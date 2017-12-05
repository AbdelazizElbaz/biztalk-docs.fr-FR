---
title: Utilitaire BatchTerminator | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 771241fa-7df5-4882-8430-c2f36200cc9d
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 080f82993fc3c8c62b3764d496f03589bd06364e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="batchterminator-utility"></a>Utilitaire BatchTerminator
L'utilitaire BatchTerminator permet d'arrêter toutes les orchestrations de traitement par lot actives utilisées pour le traitement par lot des échanges EDI. Cet outil peut s'avérer utile si un grand nombre d'instances d'orchestration de traitement par lot est en cours d'exécution et vous devez arrêter tous les traitements par lot afin de procéder à la maintenance du système BizTalk Server.  
  
 L'utilitaire BatchTerminator se trouve dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Utilities\MicrosoftEDI\BatchTerminator. Lorsque vous exécutez l’utilitaire pour arrêter les instances d’orchestration de traitement par lot, l’utilitaire enregistrera les résultats dans le fichier batchterminator.log situé dans le \< *lecteur*\>: \Documents and Settings\\ < *nom d’utilisateur*\>dossier \Application Data.  
  
> [!NOTE]
>  L'utilitaire BatchTerminator est seulement pris en charge sur les systèmes 32 bits.  Il utilise les composants dans l'espace de noms Microsoft.BizTalk.ExplorerOM (uniquement pris en charge s'il est utilisé à partir d'un processus 32 bits).  
  
 **Redémarrer les Instances d’Orchestration arrêtées**  
  
 Après l'arrêt d'un groupe d'orchestrations de traitement par lot, vous pouvez effectuer un redémarrage en bloc de ces instances. Pour ce faire, utilisez le commutateur /activate et indiquez les noms et chemin d'accès du fichier répertoriant les lots arrêtés. Ce fichier est créé lorsque vous exécutez l'utilitaire pour arrêter un groupe d'instances d'orchestration. Le fichier est batchSettings -\<GUID\>.xml dans le \< *lecteur*\>: \Documents and Settings\\<*nom d’utilisateur*  \>Dossier \Application data. Les chemin d'accès et nom du fichier répertoriant les lots arrêtés sont également enregistrés dans le fichier journal. Lorsque l'utilitaire est exécuté avec le commutateur /activate, il valide le fichier d'entrée par rapport à un schéma.  
  
 **Syntaxe**  
  
 Exécutez l'utilitaire BatchTerminator dans une fenêtre de ligne de commande à l'aide de la syntaxe suivante :  
  
```  
BatchTerminator /<switch>  
```  
  
 Vous pouvez exécuter l'utilitaire BatchTerminator avec les commutateurs suivants. Si aucun commutateur n'est indiqué, l'option /terminate est utilisée. Comme mentionné ci-après, vous pouvez entrer le nom complet du commutateur (par exemple, /terminate) ou sa forme abrégée (dans ce cas, /t).  
  
|||  
|-|-|  
|Commutateur|Fonction|  
|/?|Affiche l'aide|  
|/ arrêter - journal :\<*fichier journal*\><br /><br /> ou /t-journal :\<*fichier journal*\>|Envoie des messages de contrôle d'arrêt pour toutes les instances d'orchestration de traitement par lot X12 ou EDIFACT actives. Affiche les résultats de l'opération (liste des instances d'orchestration de traitement par lot actives arrêtées, nombre d'orchestrations de traitement par lot actives détectées et nombre de messages de contrôle d'arrêt envoyés). Il enregistre les résultats dans le fichier batchterminator.log situé dans le \< *lecteur*\>: \Documents and Settings\\<*nom d’utilisateur*\>\ Dossier Application Data.<br /><br /> Le paramètre -log: (facultatif) permet de spécifier le nom du fichier journal et/ou le chemin d'accès au dossier dans lequel enregistrer le fichier journal. Un exemple d’utilisation du paramètre pour spécifier le chemin d’accès et nom de fichier est le suivant : `BatchTerminator.exe /terminate -log:"C:\logs\log.txt"`. Un exemple d’utilisation du paramètre pour spécifier le nom de fichier est uniquement les éléments suivants : `BatchTerminator.exe /terminate -log:log.txt`. Si le chemin d’accès spécifié n’est pas valide, l’utilitaire utilisera le chemin d’accès par défaut : \< *lecteur*\>: \Documents and Settings\\<*nom d’utilisateur* \>\Application data. Le paramètre -log: peut être utilisé avec ou sans le commutateur /terminate.|  
|/print<br /><br /> ou /p|Affiche la liste des instances d'orchestration de traitement par lot actives sans envoyer de messages de contrôle d'arrêt|  
|/ Activer :\<*chemin d’accès*\>\\<br />batchSettings -\<*GUID*\>.xml-journal :\<*fichier journal*\><br /><br /> ou/a:\<*chemin d’accès*\>\\<br />batchSettings -\<*GUID*\>.xml-journal :\<*fichier journal*\>|Réactive les instances d’orchestration précédemment arrêtées qui sont répertoriées dans le batchSettings -\<GUID\>fichier .xml. L'utilitaire valide le fichier d'entrée par rapport à un schéma incorporé dans le code. Si le fichier d'entrée ne correspond pas au schéma, un message d'erreur est affiché à l'écran et le programme est fermé.<br /><br /> Si vous incluez le commutateur -log:, cette opération consigne des informations relatives à l'action de redémarrage dans le fichier journal.|  
  
 **Format du fichier de commandes d’Activation**  
  
 Pour réactiver précédemment interrompue instances d’orchestration de traitement par lots à l’aide du commutateur / activate, vous devez fournir un fichier d’activation de lot (batchSettings -\<GUID\>.xml). au format suivant :  
  
```  
<?xml version="1.0"?>  
<xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" elementFormDefault="qualified" id="BatchInfo" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="BatchTerminator">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element minOccurs="1" maxOccurs="unbounded" name="Batch">  
          <xs:complexType>  
            <xs:attribute name="PartyName" type="xs:string" />  
            <xs:attribute name="PartyID" type="xs:int" use="required" />  
            <xs:attribute name=”BatchName” type=”xs:string” />  
            <xs:attribute name=”BatchID” type=”xs:int” use=”required” />  
            <xs:attribute name="EdiMessageType" type="xs:string" use="required" />  
          </xs:complexType>  
        </xs:element>  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## <a name="prerequisites"></a>Conditions préalables  
 La configuration suivante est requise pour exécuter les procédures décrites dans cette rubrique :  
  
-   Vous devez ouvrir une session en tant que membre du groupe Administrateurs BizTalk Server.  
  
### <a name="to-run-the-batchterminator-utility"></a>Pour exécuter l'utilitaire BatchTerminator  
  
1.  Dans l'Explorateur Windows, accédez au dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Utilities\MicrosoftEDI\BatchTerminator.  
  
2.  Entrée **BatchTerminator**, y compris les commutateurs souhaités, puis cliquez sur **entrée**.  
  
3.  Dans l’Explorateur Windows, accédez à \< *lecteur*\>: \Documents and Settings\\<*nom d’utilisateur*\>dossier \Application Data, et Ouvrez le fichier batchterminator.log situé pour consulter les résultats.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaires du SDK](../core/utilities-in-the-sdk.md)