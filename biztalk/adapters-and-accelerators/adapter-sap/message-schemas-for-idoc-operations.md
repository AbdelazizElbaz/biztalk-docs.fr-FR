---
title: "Schémas de message pour des opérations IDOC dans le mon adaptateur SAP dans BizTalk | Documents Microsoft"
description: "Les opérations de message, des structures et des actions pour envoyer et recevoir des IDOC à l’aide de l’adaptateur mySAP - Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 601aa9f9-e42f-47aa-b020-7a1eed4f0780
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76d6cc5a7c8c651bcd9fcc6198b7069180c511bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-idoc-operations"></a>Schémas de message pour des opérations IDOC
Documents intermédiaires (IDoc) sont des documents EDI de type standardisés pris en charge par SAP pour la communication asynchrone avec SAP et les systèmes non-SAP. IDOC sont utilisés pour envoyer et recevoir des documents professionnels tels que les commandes vers ou depuis le système SAP d’un partenaire commercial ou un programme externe.  
  
 Bien que le système SAP prend en charge un nombre de types de port pour envoyer et recevoir des IDOC (par exemple, un port de fichier ou un port de communications CPIC), le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] prend en charge d’envoyer et recevoir des IDOC à l’aide d’un port tRFC.  
  
-   Pour un IDOC sortant, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] se comporte comme un client tRFC et appelle une commande RFC pour envoyer l’IDOC à SAP.  
  
-   Pour un IDOC entrant, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] se comporte comme un serveur tRFC et accepte un appel du client tRFC à partir de SAP pour recevoir l’IDOC.  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] met en évidence des quatre opérations sous le nœud IDOC que vous pouvez utiliser pour envoyer et recevoir des IDOC avec un système SAP.  
  
-   **SendIdoc**. Envoie un IDOC à la carte en tant que données de type chaîne. Cette opération apparaissent directement sous le nœud racine IDOC. La même opération est utilisée pour tous les IDOC.  
  
-   **Envoyer**. Envoie un IDOC à la carte en tant que données fortement typées. Cette opération est visible sous un nœud spécifique dans chaque IDOC.  
  
-   **ReceiveIdoc**. Reçoit un IDOC à partir de la carte en tant que données de type chaîne. Cette opération apparaissent directement sous le nœud racine IDOC. La même opération est utilisée pour tous les IDOC.  
  
-   **Réception**. Reçoit un IDOC à partir de la carte en tant que données fortement typées. Cette opération est visible sous un nœud spécifique dans chaque IDOC.  
  
> [!NOTE]
>  Ces quatre opérations fournissent différentes façons d’échange IDOC entre votre programme et le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. L’adaptateur utilise toujours une commande RFC (comme indiqué dans la section suivante) pour envoyer ou recevoir des IDOC avec le système SAP.  
  
 Outre l’utilisation d’une des quatre opérations IDOC, vous pouvez également envoyer ou recevoir un IDOC en utilisant l’une des RFC qui sont utilisées en interne par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] pour échanger des IDOC avec le système SAP. Pour une vue d’ensemble de la façon dont [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge les IDOC, consultez [opérations sur IDOC dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md).  
  
 Cette rubrique contient des informations sur les schémas de message et les actions de message utilisées pour des opérations IDOC.  
  
## <a name="rfcs-used-by-the-sap-adapter-to-send-and-receive-idocs"></a>RFC utilisés par l’adaptateur SAP pour envoyer et recevoir des IDOC  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise les appels de fonction distants suivant (RFC) en interne pour échanger des IDOC avec le système SAP. Du côté sortant (adaptateur au système SAP), l’adaptateur fait Office de client tRFC pour appeler la RFC. Sur le côté entrant (adaptateur SAP), SAP appelle le RFC sur la carte, qui agit comme un serveur tRFC.  
  
|RFC| Description|  
|---------|-----------------|  
|IDOC_INBOUND_ASYNCHRONOUS|Ce module de fonction est utilisé à partir de la version 4.0 et versions ultérieure. Il traite les IDOC dans des types d’enregistrements qui sont valides pour les versions 4.x. Cela garantit que les noms de segment IDOC plus longs sont pris en charge.<br /><br /> Les paramètres de ce document RFC sont les suivantes :<br /><br /> -idoc_control_rec_40 (structure SAP est EDI_DC40)<br /><br /> -idoc_data_rec_40 (structure SAP est EDI_DD40)<br /><br /> L’enregistrement de contrôle IDOC comprend les champs suivants :<br /><br /> - **Mestyp**. Type de message logique. Donne la signification de l’activité du message. Il s’agit d’un champ obligatoire.<br /><br /> - **Idoctyp**. La structure de base de l’IDOC. Ce champ identifie le jeu de mise en page qui utilise ce message. Il s’agit d’un champ obligatoire.<br /><br /> -                      **Cimtyp**. La structure d’extension du client. Si une structure de base SAP est étendue, le client doit nommer la structure de l’extension. Ce champ est obligatoire si un client a effectué une amélioration ; dans le cas contraire initiale.<br /><br /> - **Champs de partenaires**. Ces côté envoi et recevoir des paramètres de partenaire côté comme type de partenaire, nombre de partenaires, fonction de partenaire.<br /><br /> L’enregistrement de données IDOC comprend les champs suivants :<br /><br /> - **Champs d’en-tête**. Champs d’en-tête comme nom de la table, numéro de segment, le type de segment du segment. Ces champs sont obligatoires.<br /><br /> -                      **Sdata**. champ de 1000 caractères pour les données utilisées par l’IDOC. Il s’agit d’un champ obligatoire.|  
|INBOUND_IDOC_PROCESS|Ce module de fonction est utilisé pour les versions jusqu'à 4.0. Il traite les IDOC dans des types d’enregistrements qui sont valides pour les versions 3.x. Il est également possible d’utiliser ce module de fonction dans 4.x.<br /><br /> Les paramètres de ce document RFC sont les suivantes :<br /><br /> -idoc_control (structure SAP est EDI_DC)<br /><br /> -idoc_data (structure SAP est EDI_DD)|  
  
## <a name="operations-to-send-idocs"></a>Opérations à envoyer des IDOC  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] expose les opérations d’envoi et SendIdoc pour les clients envoyer des IDOC à un système SAP. Pour l’opération d’envoi, l’IDOC est représentée sous forme de données fortement typées ; pour l’opération SendIdoc, l’IDOC est représenté en tant que données de type chaîne. Ces opérations déterminent comment les données IDOC sont représentées entre l’adaptateur et de votre application. L’adaptateur envoie toujours IDOC à SAP en utilisant le IDOC_INBOUND_ASYNCHRONOUS ou le IDOC_INBOUND_PROCESS (t) RFC. Pour envoyer un IDOC à votre système SAP, vous pouvez utiliser l’opération d’envoi ou SendIdoc, ou vous pouvez appeler directement la RFC appropriée.  
  
### <a name="message-structures-for-idoc-client-operations"></a>Structures de message pour les opérations du Client IDOC  
 Le tableau suivant présente les structures de message pour les opérations d’envoi et SendIdoc.  
  
|Opération|Structure XML| Description|  
|---------------|-------------------|-----------------|  
|Send|`<Send xmlns="[MSG_VERSION]/Idoc/[VERSION]/[IDOCTYP]/                    [CIMTYP]/[RELNO]/Send">   <idocData>     <[EDI_DC40/EDI_DC] xmlns="/Types/Idoc/      [VERSION]/[IDOCTYP]/[CIMTYP]/[RELNO]">       <EDIDC_FIELD1>value1</ EDIDC_FIELD1>       <EDIDC_FIELD2>value2</ EDIDC_FIELD2>       …     </EDI_DC40>     <[SEGMENT_DEFN]_1>       <[DATAHEADERCOLUMN_[SEGHDR_FLD1]>         header_value_1       </[DATAHEADERCOLUMN_[SEGHDR_FLD1]>       <[DATAHEADERCOLUMN_[SEGHDR_FLD2]>         header_value_2       </[DATAHEADERCOLUMN_[SEGHDR_FLD2]>       …       <SEG_FIELD1>value1</SEG_FIELD1>       <SEG_FIELD2>value2</SEG_FIELD2>       …     </[SEGMENT_DEFN]_1>     <[SEGMENT_DEFN]_2>       <[DATAHEADERCOLUMN_[SEGHDR_FLD1]>         header_value_1       </[DATAHEADERCOLUMN_[SEGHDR_FLD1]>       <[DATAHEADERCOLUMN_[SEGHDR_FLD2]>         header_value_2       </[DATAHEADERCOLUMN_[SEGHDR_FLD2]>       …       <SEG_FIELD1>value1</SEG_FIELD1>       <SEG_FIELD2>value2</SEG_FIELD2>       …     </[SEGMENT_DEFN]_2>     …     </[EDI_DC40/EDI_DC]>   </idocData>   <guid>guid</guid> </Send>`|Envoie un IDOC fortement typée à SAP<br /><br /> -Schéma de IDOC est fortement typée.<br /><br /> -Champs d’enregistrement de contrôle expose.<br /><br /> -Expose les champs d’enregistrement données y compris les en-têtes de segment et les champs du segment.<br /><br /> Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] associe un GUID de la transaction SAP ID (TID) qu’il utilise pour envoyer l’IDOC. Vous pouvez choisir s’il faut spécifier un GUID dans le message de demande. Si un GUID n’est pas inclus dans le message de demande, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] en génère un. Le GUID est renvoyé dans le message de réponse.|  
|Envoyer une réponse|`<SendResponse xmlns="[MSG_VERSION]/Idoc/[VERSION]/         [IDOCTYP]/[CIMTYP]/[RELNO]/Send">   <guid>guid</guid> </SendResponse>`|Indique que l’IDOC a été envoyé au système SAP.<br /><br /> Si le **AutoConfirmSentIdocs** la liaison de propriété est **true**, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] automatiquement confirme la transaction sur le système SAP, vous pouvez ignorer le GUID retourné dans la réponse. Si le **AutoConfirmSentIdocs** la liaison de propriété est **false**, vous devez appeler la **RfcConfirmTransID** opération avec le GUID retourné par la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] à terminer la transaction sur le système SAP.<br /><br /> Vous pouvez appeler la **SapAdapterUtilities.ConvertGuidToTid** méthode pour obtenir le TID associé à l’unité logique de travail (LUW).|  
|SendIdoc|`<SendIdoc xmlns="[MSG_VERSION]/Idoc">   <idocData>docDataString</idocData>   <guid>guid</guid> </SendIdoc>`|Envoie un IDOC faiblement typée à SAP.<br /><br /> -Schéma de IDOC est faiblement typé.<br /><br /> -Expose l’IDOC comme un champ de chaîne unique qui se compose de l’enregistrement de contrôle et l’enregistrement de données.<br /><br /> Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] associe un GUID le TID SAP qu’elle utilise pour envoyer l’IDOC. Vous pouvez choisir s’il faut spécifier un GUID dans le message de demande. Si un GUID n’est pas inclus dans le message de demande, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] génère une. Le GUID est renvoyé dans le message de réponse|  
|Réponse de SendIdoc|`<SendIdocResponse xmlns="[MSG_VERSION]/Idoc">   <guid>guid</guid> </SendIdocResponse>`|Indique que l’IDOC a été envoyé au système SAP.<br /><br /> Si le **AutoConfirmSentIdocs** la liaison de propriété est **true**, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] automatiquement confirme la transaction sur le système SAP, vous pouvez ignorer le GUID retourné dans la réponse. Si le **AutoConfirmSentIdocs** la liaison de propriété est **false**, vous devez appeler la **RfcConfirmTransID** opération avec le GUID retourné par la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]à terminer la transaction sur le système SAP.<br /><br /> Vous pouvez appeler la **SapAdapterUtilities.ConvertGuidToTid** méthode pour obtenir le TID associé à le LUW.|  
  
 [MSG_VERSION] = la chaîne de version de message ; par exemple, http://Microsoft.LobServices.Sap/2007/03.  
  
 [VERSION] = version IDOC (2 ou 3).  
  
 [IDOCTYP] = type IDOC ; par exemple, ORDERS05.  
  
 [CIMTYP] = Cimtype de l’IDOC personnalisé.  
  
 [RELNO] = numéro de version ; par exemple, 620.  
  
 [EDI_DC40/EDI_DC] = EDI_DC40 pour version IDOC de version 3 et EDI_DC pour libérer les IDOC version2.  
  
 [EDIDC_FIELD] = constituant la structure d’enregistrement EDI_DC40/EDI_DC contrôle de champ.  
  
 [SEGMENT_DEFN] = nom de définition de Segment (pas nom de type segment) ; par exemple, E2EDK01005. Notez que le nœud de définition du segment peut également apparaître sous un nœud de groupe de segment, en fonction de la structure de l’IDOC.  
  
 [DATAHEADERCOLUMN_(SEGHDR_FLD)] = chaque segment possède un en-tête de segment qui se compose d’un ensemble standard de champs d’en-tête suivi par les données du segment. Les données du segment se comprennent de toutes les données et les champs du segment. Ce nœud représente les champs d’en-tête segment ; par exemple, DATAHEADERCOLUMN_SEGNAM.  
  
 [SEG_FIELD] = nom du champ Segment constituant une définition de segment particulière [SEGMENT_DEFN].  
  
 [guid] = paramètre GUID.  
  
### <a name="message-actions-for-idoc-client-operations"></a>Actions de message pour les opérations du Client IDOC  
 Le tableau suivant répertorie les actions de message pour les opérations d’envoi et SendIdoc.  
  
|Opération|Action|Exemple|  
|---------------|------------|-------------|  
|Send|[MESSAGE_VERSION] /Idoc/ [VERSION] / [IDOCTYP] / [CIMTYP] / [RELNO] / envoi|http://Microsoft.LobServices.SAP/2007/03/IDOC/3/ORDERS05//620/Send|  
|Envoyer une réponse|[MESSAGE_VERSION] /Idoc/ [VERSION] / [IDOCTYP] / [CIMTYP] / / envoi/réponse de [RELNO]|http://Microsoft.LobServices.SAP/2007/03/IDOC/3/ORDERS05//620/Send/Response|  
|SendIdoc|[MESSAGE_VERSION] / Idoc/SendIdoc|http://Microsoft.LobServices.SAP/2007/03/IDOC/SendIdoc|  
|Réponse de SendIdoc|[MESSAGE_VERSION] / Idoc/SendIdoc/réponse|http://Microsoft.LobServices.SAP/2007/03/IDOC/SendIdoc/Response|  
  
 [MESSAGE_VERSION] = la chaîne de version de message ; par exemple, http://Microsoft.LobServices.Sap/2007/03.  
  
 [VERSION] = version IDOC (2 ou 3).  
  
 [IDOCTYP] = type IDOC ; par exemple, ORDERS05.  
  
 [CIMTYP] = Cimtype de l’IDOC personnalisé.  
  
 [RELNO] = numéro de version ; par exemple, 620.  
  
## <a name="operations-to-receive-idocs"></a>Opérations pour recevoir des IDOC  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] expose les opérations de réception et ReceiveIdoc pour les applications à recevoir des IDOC à partir d’un système SAP. Pour l’opération de réception, l’IDOC est représentée sous forme de données fortement typées ; pour l’opération ReceiveIdoc, l’IDOC est représenté en tant que données de type chaîne.  
  
 Ces opérations déterminent la façon dont les données IDOC sont émises par la carte à votre application. L’adaptateur reçoit toujours IDOC à partir du système SAP comme un IDOC_INBOUND_ASYNCHRONOUS ou IDOC_INBOUND_PROCESS tRFC. Vous pouvez utiliser l’opération de réception ou ReceiveIdoc, ou vous pouvez recevoir des données IDOC au format de la RFC. Vous définissez la **ReceiveIdocFormat** liaison de propriété pour spécifier le format dans lequel la carte émet les données IDOC à votre application. Pour plus d’informations sur la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
### <a name="message-structures-for-idoc-receive-operations"></a>Opérations de réception des Structures de message pour IDOC  
 Le tableau suivant présente les structures de message pour les opérations de réception et ReceiveIdoc.  
  
|Opération|Structure XML| Description|  
|---------------|-------------------|-----------------|  
|Recevoir|`<Receive xmlns="[MSG_VERSION]/Idoc/[VERSION]/[IDOCTYP]/                 [CIMTYP]/[RELNO]/Receive">   <idocData>     <[EDI_DC40/EDI_DC] xmlns="/Types/Idoc/      [VERSION]/[IDOCTYP]/[CIMTYP]/[RELNO]">       <EDIDC_FIELD1>value1</ EDIDC_FIELD1>       <EDIDC_FIELD2>value2</ EDIDC_FIELD2>       …     </EDI_DC40>     <[SEGMENT_DEFN]_1>       <[DATAHEADERCOLUMN_[SEGHDR_FLD1]>         header_value_1       </[DATAHEADERCOLUMN_[SEGHDR_FLD1]>       <[DATAHEADERCOLUMN_[SEGHDR_FLD2]>         header_value_2       </[DATAHEADERCOLUMN_[SEGHDR_FLD2]>       …       <SEG_FIELD1>value1</SEG_FIELD1>       <SEG_FIELD2>value2</SEG_FIELD2>       …     </[SEGMENT_DEFN]_1>     <[SEGMENT_DEFN]_2>       <[DATAHEADERCOLUMN_[SEGHDR_FLD1]>         header_value_1       </[DATAHEADERCOLUMN_[SEGHDR_FLD1]>       <[DATAHEADERCOLUMN_[SEGHDR_FLD2]>         header_value_2       </[DATAHEADERCOLUMN_[SEGHDR_FLD2]>       …       <SEG_FIELD1>value1</SEG_FIELD1>       <SEG_FIELD2>value2</SEG_FIELD2>       …     </[SEGMENT_DEFN]_2>     …     </[EDI_DC40/EDI_DC]>   </idocData> </Receive>`|Reçoit un IDOC fortement typé à partir de SAP<br /><br /> -Schéma de IDOC est fortement typée.<br /><br /> -Champs d’enregistrement de contrôle expose.<br /><br /> -Expose les champs d’enregistrement données y compris les en-têtes de segment et les champs du segment.|  
|Recevoir la réponse|`<ReceiveResponse xmlns="[MSG_VERSION]/Idoc/[VERSION]/[IDOCTYP]/         [CIMTYP]/[RELNO]/Receive"> </ReceiveResponse>`|Indique que l’IDOC a été reçu à partir du système SAP.|  
|ReceiveIdoc|`<ReceiveIdoc xmlns="[MSG_VERSION]/Idoc">   <idocData>docDataString</idocData> </ReceiveIdoc>`|Reçoit un IDOC faiblement typée à partir de SAP.<br /><br /> -Schéma de IDOC est faiblement typé.<br /><br /> -Expose l’IDOC comme un champ de chaîne unique qui se compose de l’enregistrement de contrôle et l’enregistrement de données.|  
|Réponse de ReceiveIdoc|`<ReceiveIdocResponse xmlns="[MSG_VERSION]/Idoc"> </ReceiveIdocResponse>`|Indique que l’IDOC a été reçu à partir du système SAP.|  
  
 [MSG_VERSION] = la chaîne de version de message ; par exemple, http://Microsoft.LobServices.Sap/2007/03.  
  
 [VERSION] = version IDOC (2 ou 3).  
  
 [IDOCTYP] = type IDOC ; par exemple, ORDERS05.  
  
 [CIMTYP] = Cimtype de l’IDOC personnalisé.  
  
 [RELNO] = numéro de version ; par exemple, 620.  
  
 [EDI_DC40/EDI_DC] = EDI_DC40 pour version IDOC de version 3 et EDI_DC pour libérer les IDOC version 2.  
  
 [EDIDC_FIELD] = constituant la structure d’enregistrement EDI_DC40/EDI_DC contrôle de champ.  
  
 [SEGMENT_DEFN] = nom de définition de Segment (pas nom de type segment) ; par exemple, E2EDK01005. Le nœud de définition du segment peut également apparaître sous un nœud de groupe de segment, en fonction de la structure de l’IDOC.  
  
 [DATAHEADERCOLUMN_(SEGHDR_FLD)] = chaque segment possède un en-tête de segment qui se compose d’un ensemble standard de champs d’en-tête suivi par les données du segment. Les données du segment se comprennent de toutes les données et les champs du segment. Ce nœud représente les champs d’en-tête segment ; par exemple, DATAHEADERCOLUMN_SEGNAM.  
  
 [SEG_FIELD] = nom du champ Segment constituant une définition de segment particulière [SEGMENT_DEFN].  
  
#### <a name="receiving-an-idoc-in-rfc-format"></a>Réception d’un IDOC au Format de la RFC  
 Vous pouvez également recevoir des IDOC au format de la RFC. Les documents RFC utilisés pour recevoir des IDOC de SAP sont :  
  
-   IDOC_INBOUND_ASYNCHRONOUS des IDOC de version 3.  
  
-   INBOUND_IDOC_PROCESS des IDOC de version 2.  
  
 Le code suivant montre la structure d’un IDOC reçu en tant qu’une opération IDOC_INBOUND_ASYNCHRONOUS.  
  
```  
<IDOC_INBOUND_ASYNCHRONOUS xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/">  
  <IDOC_CONTROL_REC_40>  
    <EDI_DC40 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
      <EDIDC_FIELD1>field1</EDIDC_FIELD1>  
      <EDIDC_FIELD2>field2</EDIDC_FIELD2>  
      …  
    </EDI_DC40>  
  <IDOC_DATA_REC_40>  
    <EDI_DD40 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
      \<[SEG_HEADER_FIELD1]>value1\</[SEG_HEADER_FIELD1]>  
      \<[SEG_HEADER_FIELD2]>value2\</[SEG_HEADER_FIELD2]>  
      …  
      <SDATA>segment value</SDATA>  
    </EDI_DD40>  
    …  
  </IDOC_DATA_REC_40>  
</IDOC_INBOUND_ASYNCHRONOUS>  
```  
  
 [EDIDC_FIELD] = champ constituant la structure de fichier de contrôle EDI_DC40/EDI_DC  
  
 [SEG_HEADER_FIELD] = chaque segment possède un en-tête de segment qui se compose d’un ensemble standard de champs d’en-tête suivi par les données du segment. Les données du segment se comprennent de toutes les données et les champs du segment. Ce nœud représente les champs d’en-tête segment ; par exemple, SEGNAM situation et DOCNUM.  
  
 Pour plus d’informations sur le format des opérations de tRFC, consultez [des schémas de Message pour des opérations tRFC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md).  
  
### <a name="message-actions-for-idoc-receive-operations"></a>Opérations de réception des Actions de message pour IDOC  
 Le tableau suivant répertorie les actions de message pour les opérations de réception et ReceiveIdoc.  
  
|Opération|Action|Exemple|  
|---------------|------------|-------------|  
|Recevoir|[MESSAGE_VERSION] /Idoc/ [VERSION] / [IDOCTYP] / [CIMTYP] / [RELNO] / de réception|http://Microsoft.LobServices.SAP/2007/03/IDOC/3/ORDERS05//620/Receive|  
|Recevoir la réponse|[MESSAGE_VERSION] /Idoc/ [VERSION] / [IDOCTYP] / [CIMTYP] / / réception/réponse de [RELNO]|http://Microsoft.LobServices.SAP/2007/03/IDOC/3/ORDERS05//620/Receive/Response|  
|ReceiveIdoc|[MESSAGE_VERSION] / Idoc/ReceiveIdoc|http://Microsoft.LobServices.SAP/2007/03/IDOC/ReceiveIdoc|  
|Réponse de ReceiveIdoc|[MESSAGE_VERSION] / Idoc/ReceiveIdoc/réponse|http://Microsoft.LobServices.SAP/2007/03/IDOC/ReceiveIdoc/Response|  
  
