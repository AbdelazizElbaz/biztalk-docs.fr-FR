---
title: "Opérations sur IDOC dans SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDOC, operations to receive an
- IDOCs
- IDOCs, operations on
- tRFC server
- IDOC, operations to send an
- RFC server
ms.assetid: 6abcc646-c7a3-48cf-a09e-01f516dcef97
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6a70e6bc4062a6c2865c9adb8f76d68a078e965
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-idocs-in-sap"></a>Opérations sur IDOC dans SAP
IDOC sont des documents de type EDI standardisés qui prend en charge par SAP pour la communication asynchrone avec SAP et les systèmes non-SAP. IDOC sont utilisés pour envoyer et recevoir des documents telles que les commandes, par exemple, « business » ou un système SAP d’un partenaire commercial ou un programme externe.  
  
 Bien que le système SAP prend en charge un nombre de types de port pour envoyer et recevoir des IDOC (tel que le port de fichier, port de communications CPIC), le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge d’envoyer et recevoir des IDOC via le port tRFC.  
  
## <a name="operations-to-send-an-idoc"></a>Opérations à envoyer un IDOC  
 Tous les appels IDOC à SAP sont traitées en interne comme tRFC appelle laquelle l’adaptateur se comporte comme un client tRFC et appelle une commande RFC dans SAP pour envoyer un IDOC. Tout comme n’importe quel autre appel de client tRFC, le client de l’adaptateur transmet éventuellement un GUID à l’adaptateur, qui à son tour l’associe à la transaction ID (TID) qu’il utilise pour l’appel sur le système SAP. (Si le client de l’adaptateur ne transmet pas un GUID, l’adaptateur génère son propre GUID.) Le GUID est renvoyé au client de carte dans le message de réponse. Le client de l’adaptateur peut utiliser ce GUID pour confirmer le TID sur le système SAP. Le TID SAP réel utilisé par l’adaptateur pour l’appel de tRFC peut être obtenu en appelant une méthode statique spéciale dans la liaison de SAP, **ConvertGuidToTid**. Ayant le TID réel peut être utile pour résoudre les problèmes sur le système SAP.  
  
 Après l’appel pour envoyer que l’IDOC est terminée, le TID doit être confirmé sur le système SAP. Ainsi, le système SAP afin de supprimer le TID sa base de données. Le client de carte puisse confirmer le TID sur le système SAP.  
  
-   Explicitement, en appelant le **RfcConfirmTransID** opération sur la carte. Cette opération accepte un GUID (retourné dans le message de réponse ci-dessus) et la carte confirmer le TID associé sur le système SAP.  
  
-   Implicitement, en définissant le **AutoConfirmSentIdocs** propriété de liaison. Si cette propriété de liaison a la valeur true, l’adaptateur valide automatiquement le TID après avoir envoyé l’IDOC au système SAP. Consultez [en savoir plus sur l’adaptateur BizTalk pour mySAP Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md) pour plus d’informations.  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise les normes RFC suivantes pour envoyer un IDOC :  
  
-   INBOUND_IDOC_PROCESS. Ce module de fonction est utilisé pour les versions de SAP avant 4.0.  
  
-   IDOC_INBOUND_ASYNCHRONOUS. Ce module de fonction est utilisée pour SAP version 4.0 et versions ultérieures.  
  
### <a name="sending-idocs-with-segment-data-across-multiple-lines"></a>Envoyer des IDOC avec segmenter les données sur plusieurs lignes  
 IDOC sont constitués de segments. Chaque entrée de segment dans un fichier plat IDOC contient les informations d’en-tête de segment (qui contient le champ DOCNUM) et les données du segment. Dans certains IDOC, les données du segment peuvent être réparties entre plusieurs lignes. Exemple :  
  
```  
Segment header (DOCNUM is one of the fields here)  |  Segment data  
Segment header (DOCNUM is one of the fields here)  |  Segment data  
Segment data wrapped from the previous line  
Segment header (DOCNUM is one of the fields here)  |  Segment data  
```  
  
 La station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge l’envoi de ce type IDOC au système SAP. Pour prendre en charge l’envoi de ce type IDOC, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] détermine si les données de chaque segment sont une continuation de la précédente, ou s’il s’agit d’une nouveau segmenter les données. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] il décide par l’analyse de chaque en-tête de segment et recherchez le champ DOCNUM. Si les données du segment sont divisées en deux lignes, la deuxième ligne n’a pas un en-tête de segment et par conséquent le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ne trouve pas le champ DOCNUM. Par conséquent, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] peut déterminer qu’il s’agit d’une continuation des données du segment précédent.  
  
 Par exemple, dans la représentation sous forme d’un IDOC illustrée ci-dessus, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ne trouve pas de n’importe quel champ DOCNUM dans «`Segment data wrapped from the previous line`» et est en mesure de déterminer que la ligne est la suite des données du segment précédent. Compte tenu de la taille des IDOC fichiers plats dans les environnements de production, l’exécution de ce type de contrôle pour chaque segment peuvent entraîner des temps de traitement.  
  
> [!NOTE]
>  L’adaptateur utilise le champ DOCNUM au lieu d’une ligne de retour chariot (CRLF) de flux pour identifier et extraire chaque enregistrement du segment à partir des données d’IDOC. Si les champs DOCNUM dans les enregistrements de contrôle et les données sont non valides ou partiellement vide, l’adaptateur ne peut pas analyser l’IDOC. Par conséquent, l’IDOC n’est pas envoyée au système SAP.  
  
### <a name="operations-to-send-an-idoc"></a>Opérations à envoyer un IDOC  
 Les opérations suivantes sont prises en charge pour l’envoi des IDOC à un système SAP :  
  
-   **Envoyer**. Cette opération permet d’envoyer un IDOC au système SAP à l’aide d’un schéma fortement typé. Le schéma pour cette opération expose les champs d’enregistrement contrôle et les champs d’enregistrement de données, y compris les en-têtes de segment et les champs du segment. L’opération d’envoi est spécifique à un IDocType CimType + ReleaseNumber + Version combinaison.  
  
     Cette opération est visible pour chaque IDOC et est disponible sous un nœud IDOC spécifique dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
    > [!NOTE]
    >  Pour pouvoir exécuter correctement un **envoyer** opération, vous devez disposer d’autorisations appropriées dans le système SAP. Pour plus d’informations, consultez  
  
-   **SendIdoc**. Cette opération permet d’envoyer un IDOC au système SAP à l’aide d’un schéma faiblement typée. Le schéma pour cette opération expose IDOC sous la forme d’un champ de chaîne unique composé de l’enregistrement de contrôle et l’enregistrement de données. L’opération SendIdoc prend une chaîne IDOC et un GUID en tant que paramètre.  
  
     Cela indique une opération visible pour tous les IDOC exposées par le système SAP et est disponible sous la racine **IDOC** nœud dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
 Pour plus d’informations sur :  
  
-   Envoyer un IDOC à un système SAP à l’aide de BizTalk Server, consultez [envoyer des IDOC à SAP par à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-biztalk-server.md).  
  
-   Envoyer un IDOC à un système SAP à l’aide du modèle de service WCF, consultez [envoyer des IDOC à SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-the-wcf-service-model.md).  
  
-   Structures et action SOAP pour envoyer un IDOC des messages, consultez [des schémas de Message pour des opérations IDOC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md).  
  
## <a name="operations-to-receive-an-idoc"></a>Opérations pour recevoir un IDOC  
 Pour recevoir un IDOC, les [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] peuvent se comporter comme un serveur tRFC ou un serveur RFC :  
  
-   À l’adaptateur pour se comporter comme un serveur tRFC, la propriété de liaison **TidDatabaseConnectionString** doit être définie sur la chaîne de connexion pour la base de données TID sur votre ordinateur. Pour un scénario de serveur tRFC, l’adaptateur accepte un appel du client tRFC à partir du système SAP pour recevoir l’IDOC.  
  
-   À l’adaptateur pour se comporter comme un serveur RFC, le **TidDatabaseConnectionString** doit avoir la valeur null (valeur par défaut). Pour un scénario de serveur RFC, l’adaptateur accepte un appel du client à partir du système SAP RFC pour recevoir l’IDOC.  
  
 Les documents RFC suivants sont utilisés pour envoyer et recevoir des IDOC ; lors de l’envoi IDOC, l’adaptateur utilise ces RFC, tandis que lors de la réception IDOC, le système SAP les utilise.  
  
-   INBOUND_IDOC_PROCESS. Ce module de fonction est utilisé pour les versions de SAP avant 4.0.  
  
-   IDOC_INBOUND_ASYNCHRONOUS. Ce module de fonction est utilisée pour SAP version 4.0 et versions ultérieures.  
  
 Les opérations suivantes sont prises en charge pour la réception des IDOC à partir d’un système SAP :  
  
-   **Réception**. Cette opération permet de recevoir un IDOC à partir du système SAP à l’aide d’un schéma fortement typé. Le schéma pour cette opération expose les champs d’enregistrement contrôle et les champs d’enregistrement données y compris les en-têtes de segment et les champs du segment.  
  
     Cette opération est visible pour chaque IDOC et est disponible sous un nœud IDOC spécifique dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
    > [!NOTE]
    >  Pour pouvoir exécuter correctement un **réception** opération, vous devez disposer d’autorisations appropriées dans le système SAP. Pour plus d’informations, consultez  
  
    > [!NOTE]
    >  À l’aide de la **réception** opération, vous pouvez également recevoir des IDOC plusieurs.  
  
-   **ReceiveIdoc**. Cette opération permet de recevoir un IDOC à partir du système SAP à l’aide d’un schéma faiblement typée. Le schéma pour cette opération expose IDOC sous la forme d’un champ de chaîne unique composé de l’enregistrement de contrôle et l’enregistrement de données. Cette opération reçoit IDOC sous forme de chaîne dans un message XML sous la \<idocData > balise.  
  
     Cela indique une opération visible pour tous les IDOC exposées par le système SAP et est disponible sous la racine **IDOC** nœud dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
 Lors de la réception IDOC, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge différents formats de message, qui peuvent être spécifiés en tant que valeur pour la propriété de liaison, **ReceiveIDocFormat** exposées par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
-   Si la valeur « Typé », le schéma XML est fortement typé pour l’IDOC spécifique en cours de réception. (Le schéma pour ce message peut être consulté dans les opérations de réception. Notez que le schéma est différent des IDOC différents). Il en résulte un IDOC XML.  
  
-   Si la valeur « Chaîne », les données IDOC entrantes sont retournées en tant que valeur de chaîne. (Le schéma pour ce message peut être consulté à partir de l’opération ReceiveIdoc). Il en résulte un message XML avec le \<idocData > balise.  
  
-   Si la valeur « Rfc », le schéma de message correspond au schéma RFC (ou tRFC) pour les opérations de RFC IDOC_INBOUND_ASYNCHRONOUS ou INBOUND_IDOC_PROCESS, selon la version IDOC entrante. Si vous spécifiez cette propriété de liaison, vous devez utiliser le IDOC_INBOUND_ASYNCHRONOUS ou INBOUND_IDOC_PROCESS RFC pour recevoir l’IDOC. Dans les deux premières options, l’adaptateur utilise en interne cette RFC. Dans cette option, vous utilisez explicitement cette RFC pour recevoir un IDOC.  
  
 L’opération que vous utilisez pour recevoir un IDOC doit correspondre au format des données IDOC émis par l’adaptateur. Le tableau suivant fournit un résumé des différentes combinaisons dans lequel vous pouvez recevoir un IDOC de SAP.  
  
|Pour recevoir un IDOC à l’aide|Définissez la propriété binding ReceiveIDOCFormat à|  
|------------------------------|---------------------------------------------------|  
|**Réception** opération|Typé|  
|**ReciveIdoc** opération|Chaîne|  
|IDOC_INBOUND_ASYNCHRONOUS RFC|RFC|  
|INBOUND_IDOC_PROCESS RFC|RFC|  
  
 Une autre propriété de liaison **PadReceivedIdocsWithSpaces** remplit l’IDOC reçu avec des espaces blancs pour des champs facultatifs lors de réception format attendu est « String ». Cela permet d’assurer la compatibilité avec le format de données IDOC reçu à l’aide de la version précédente de l’adaptateur.  
  
 Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour mySAP Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
 Pour plus d’informations sur :  
  
-   Réception d’un IDOC à partir d’un système SAP à l’aide de BizTalk Server, consultez [recevoir des IDOC de SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-using-biztalk-server.md).  
  
-   Réception d’un IDOC à partir d’un système SAP dans un contexte transactionnel à l’aide de BizTalk Server, consultez [recevoir des IDOC de SAP dans un contexte transactionnel à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-in-a-transactional-context-using-biztalk-server.md).  
  
-   Structures et action SOAP pour recevoir un IDOC des messages, consultez [des schémas de Message pour des opérations IDOC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md).  
  
##  <a name="BKMK_Authorize"></a>SAP d’autorisation pour l’utilisation d’envoi ou d’opérations de réception  
 Lorsque vous utilisez la **envoyer** ou **réception** operations pour envoyer ou recevoir des IDOC à l’aide d’un schéma fortement typé, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] appelle en interne la RFC IDOCTYPE_READ_COMPLETE pour récupérer les métadonnées pour l’IDOC. Appel de ce document RFC nécessite l’autorisation suivante dans SAP :  
  
```  
Authorisation object S_IDOCDEFT, Fields:  
EDI_TCD, value 'WE30'  
ACTVT, value - 03 (display)  
EDI_DOC, value  *  
EDI_CIM, value *  
```  
  
 Vous pouvez utiliser la transaction SU01 dans SAP pour ajouter un objet d’autorisation. Pour plus d’informations sur la transaction, contactez votre administrateur SAP ou consultez la documentation de SAP.  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)