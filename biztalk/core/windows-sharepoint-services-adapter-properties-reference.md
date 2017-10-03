---
title: "Référence des propriétés de l’adaptateur de Windows SharePoint Services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ConfigCustomTemplatesDocLib property [Windows SharePoint Services adapters]
- InFileSize property [Windows SharePoint Services adapters]
- InIconUrl property [Windows SharePoint Services adapters]
- InOfficeIntegration property [Windows SharePoint Services adapters]
- code samples, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, properties
- ConfigCustomTemplatesNamespaceCol property [Windows SharePoint Services adapters]
- configuring [Windows SharePoint Services adapters], properties
- ConfigTemplatesDocLib property [Windows SharePoint Services adapters]
- InPropertiesXml property [Windows SharePoint Services adapters]
- InItemId property [Windows SharePoint Services adapters]
- InListName property [Windows SharePoint Services adapters]
- InArchivedMsgUrl property [Windows SharePoint Services adapters]
- Filename property [Windows SharePoint Services adapters]
- InListUrl property [Windows SharePoint Services adapters]
- ConfigTemplatesNamespaceCol property [Windows SharePoint Services adapters]
- InLastModifiedBy property [Windows SharePoint Services adapters]
- ConfigOverwrite property [Windows SharePoint Services adapters]
- ConfigPropertiesXml property [Windows SharePoint Services adapters]
- TransmittedFileLocation property [Windows SharePoint Services adapters]
- InTitle property [Windows SharePoint Services adapters]
- Windows SharePoint Services adapters, code samples
- InCreated property [Windows SharePoint Services adapters]
- InCreatedBy property [Windows SharePoint Services adapters]
- InLastModified property [Windows SharePoint Services adapters]
- URL property [Windows SharePoint Services adapters]
- InEditUrl property [Windows SharePoint Services adapters]
- ConfigOfficeIntegration property [Windows SharePoint Services adapters]
- ConfigTimeout property [Windows SharePoint Services adapters]
- ConfigNamespaceAliases property [Windows SharePoint Services adapters]
- ConfigAdapterWSPort property [Windows SharePoint Services adapters]
ms.assetid: c64c43ac-05bb-427c-987a-71663ae8e43d
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 691708378d778eb0c91be73fe2b775d5bfd27cfd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="windows-sharepoint-services-adapter-properties-reference"></a>Référence aux propriétés de l'adaptateur Windows SharePoint Services
Les propriétés de l'adaptateur Windows SharePoint Services suivantes sont promues dans BizTalk Server ou sont utilisées pour spécifier les options de configuration du port d'envoi pour des messages sortants. Les propriétés peuvent être utilisées pour accéder aux informations Windows SharePoint Services relatives au message ou pour fournir des informations à l'adaptateur Windows SharePoint Services à partir d'une orchestration.  
  
## <a name="message-property-precedence"></a>Priorité des propriétés de message  
 Il existe une règle de priorité pour remplacer les propriétés de message définies dans les orchestrations et les ports d'envoi.  
  
 Les règles sont les suivantes :  
  
1.  Propriété définie dans l'orchestration à l'intérieur de PropertiesXML  
  
2.  Propriété définie dans l'orchestration  
  
3.  Propriété définie au niveau du port d'envoi dans la collection Nom/Source de la propriété.  
  
4.  Propriété définie au niveau du port d'envoi  
  
## <a name="considerations-and-known-issues"></a>Considérations diverses et problèmes connus  
 Les considérations suivantes s'appliquent aux propriétés de l'adaptateur Windows SharePoint Services :  
  
-   La liste des propriétés dans les orchestrations fusionne avec les propriétés définies par le port en fonction de la position de la propriété. S'il existe des conflits, la propriété de l'orchestration remplace la propriété du port d'envoi.  
  
## <a name="property-types"></a>Types de propriétés  
  
|Type de propriété| Description|  
|-------------------|-----------------|  
|**IN**|Les propriétés IN sont des propriétés BizTalk Server qui obtiennent leur valeur à partir de Windows SharePoint Services. **Remarque :** vous ne devez pas modifier ces propriétés à partir d’orchestrations.|  
|**CONFIGURATION**|Les propriétés CONFIG sont des propriétés qui obtiennent leur valeur à partir d'orchestrations BizTalk ou de pipelines personnalisés. Cette valeur est utilisée par l'adaptateur Windows SharePoint Services lors de la détermination de la destination des messages sortants. Les propriétés CONFIG vous permettent de spécifier la valeur de certaines propriétés dans une orchestration ou un pipeline personnalisé que vous devriez définir sur le port d'envoi. Les propriétés qui ne commencent pas par IN ou CONFIG sont IN et CONFIG, à l'exception de la propriété URL.|  
|**PROMUE**|Les propriétés PROMOTED peuvent être utilisées par le routage basé sur le contenu (CBR). Les propriétés qui ne sont pas marquées comme PROMOTED ne peuvent pas être utilisées par le routage basé sur le contenu. **Remarque :** bien que toutes les propriétés de la carte apparaissent dans l’éditeur de filtre CBR, seules les propriétés promues peuvent servir pour CBR.|  
|**SPÉCIAUX**|Néant|  
  
> [!NOTE]
>  Toutes les propriétés figurent dans l'espace de noms http://schemas.microsoft.com/BizTalk/2006/WindowsSharePointServices-properties et sont accessibles depuis un filtre de port d'envoi ou d'orchestration, à l'aide de la syntaxe `WSS.<WSS_Property_Name>`.  
  
## <a name="property-list"></a>Liste des propriétés  
  
|Colonne standard Windows SharePoint Services|Nom et type de propriété Windows SharePoint Services|Type| Description|Type de propriété|  
|-------------------------------------------------|--------------------------------------------------------|----------|-----------------|-------------------|  
|Nom|Nom du fichier|xs:string|Nom de fichier avec l'extension du fichier Windows SharePoint Services. Les noms de fichier, extensions comprises, sont uniques au sein d'une bibliothèque de documents.|IN/CONFIG/PROMOTED|  
|Néant|Url|xs:string|URL du fichier.|IN/PROMOTED|  
|Néant|TransmittedFileLocation|Néant|Cette propriété est utilisée par l'analyse BAM (Business Activity Monitoring) à des fins d'intégration et n'est pas disponible dans des orchestrations.|SPECIAL|  
|Néant|InArchivedMsgUrl|xs:string|URL du fichier dans la bibliothèque de documents d'archive. Cette propriété n'est pas disponible si l'emplacement de réception n'archive pas le message.|IN/PROMOTED|  
|Type|InIconUrl|xs:string|URL de l'icône Windows SharePoint Services utilisée pour représenter le document.|IN|  
|Title|InTitle|xs:string|Titre du fichier Windows SharePoint Services. Il diffère du nom de fichier. Les titres ne doivent pas être uniques dans une bibliothèque de documents.|IN/PROMOTED|  
|Modifié le|InLastModified|xs:dateTime|Date de dernière modification de Windows SharePoint Services.|IN/PROMOTED|  
|Modifié par|InLastModifiedBy|xs:string|Nom du dernier utilisateur ayant modifié le fichier.|IN/PROMOTED|  
|ID|InItemId|xs:int|L’ID du fichier. Il s'agit d'un entier unique dans la bibliothèque de documents pouvant être utilisé pour accéder au fichier.|IN|  
|Modifier|InEditUrl|xs:string|URL accessible pour modifier les propriétés du fichier.|IN|  
|Créé le|InCreated|xs:dateTime|Date de création du fichier Windows SharePoint Services.|IN/PROMOTED|  
|Date de création|InCreatedBy|xs:string|Utilisateur qui a créé le fichier.|IN/PROMOTED|  
|Taille du fichier|InFileSize|xs:int|Taille du fichier Windows SharePoint Services.|IN|  
|Néant|InListName|xs:string|Nom de la bibliothèque de documents où se trouve ce fichier.|IN/PROMOTED|  
|Néant|InListUrl|xs:string|URL de la bibliothèque de documents ou dossier de la bibliothèque de documents où se trouve ce fichier.|IN|  
|Néant|InPropertiesXml|xs:string|Document XML plat contenant toutes les colonnes Windows SharePoint Services standard et définies par l'utilisateur. Il permet d'accéder à toute valeur de colonne Windows SharePoint Services à partir d'une orchestration, y compris les valeurs des colonnes définies par l'utilisateur. **Remarque :** il n’a pas la limite de 16 colonnes. **Remarque :** consultez l’exemple de valeur InPropertiesXml dans la section suivante de cette rubrique.|IN|  
|Néant|InOfficeIntegration|xs:string|En fonction de la valeur de l'emplacement de réception. Cela peut être `yes`, `no` ou `optional`.|IN|  
|Néant|ConfigOverwrite|xs:string|« Yes » remplace les fichiers existants portant le même nom. « No » génère une erreur lorsqu'un fichier portant le même nom existe. « Rename » donne au fichier un nom unique en ajoutant une séquence unique au nom de fichier. **Remarque :** cela est semblable au champ « Remplacer » des ports d’envoi physiques. **Remarque :** 'Orchestration' n’est pas une valeur valide pour ce champ.|CONFIG|  
|Néant|ConfigNamespaceAliases|xs:string|Définitions d'alias des XPATH.|CONFIG|  
|Néant|ConfigOfficeIntegration|xs:string|« Yes » si OfficeImporters doit être appelé. « No » pour gérer le message en l'état. « Optional » revient à « Yes » si la solution d'IP est trouvée, sinon « No ». **Remarque :** cela est semblable au champ « Intégration de Microsoft Office » des ports d’envoi physiques. **Remarque :** 'Orchestration' n’est pas une valeur valide pour ce champ.|CONFIG|  
|Néant|ConfigTemplatesDocLib|xs:string|Nom de la bibliothèque de documents de secours. Il s'agit du second emplacement qui fait l'objet de la recherche. **Remarque :** cela est semblable au champ bibliothèque de documents modèles de secours pour les ports d’envoi physiques.|CONFIG|  
|Néant|ConfigTemplatesNamespaceCol|xs:string|Nom de colonne Espace de noms de la bibliothèque de documents de secours. **Remarque :** cela est semblable au champ « Colonne modèles de secours Namespace » pour les ports d’envoi physiques.|CONFIG|  
|Néant|ConfigCustomTemplatesDocLib|xs:string|Nom de la bibliothèque de documents principale. Il s'agit du premier emplacement qui fait l'objet de la recherche. **Remarque :** cela est semblable au champ de bibliothèque de documents modèles des ports d’envoi physiques.|CONFIG|  
|Néant|ConfigCustomTemplatesNamespaceCol|xs:string|Nom de colonne Espace de noms de la bibliothèque de documents principale. **Remarque :** cela est semblable au champ colonne Namespace de modèles pour les ports d’envoi physiques.|CONFIG|  
|Néant|ConfigPropertiesXml|xs:string|Document XML plat contenant tous les noms et valeurs des colonnes Windows SharePoint Services devant être mis à jour dans Windows SharePoint Services. Il permet à un développeur d'orchestration de définir les valeurs des colonnes SharePoint pour le message suivant à créer dans SharePoint. **Remarque :** cela est similaire à la fonctionnalité disponible via la colonne n et champs de valeur n colonnes pour physique des ports d’envoi. **Remarque :** il est limité à 16 colonnes. **Remarque :** consultez l’exemple de valeur ConfigPropertiesXml plus loin dans cette rubrique.|CONFIG|  
|Néant|ConfigTimeout|xs:int|Délai d'attente en millisecondes pour les appels de service Web.|CONFIG|  
|Néant|ConfigAdapterWSPort|xs:int|Port ou site Web IIS où l'adaptateur a été installé et configuré. **Remarque :** une valeur de configuration de port non valide dans une orchestration interrompt le message même si la valeur de port d’envoi physique remplace la valeur de l’orchestration définie.|CONFIG|  
  
## <a name="sample-inpropertiesxml"></a>Exemple d'InPropertiesXml  
 Voici un exemple de code XML pour InPropertiesXml.  
  
```  
<InPropertiesXml>  
     <Property name="InItemId">2</Property>  
     <Property name="Created">12/14/2004 1:30:31 PM</Property>  
     <Property name="Author">3;#John Doe</Property>  
     <Property name="Modified">12/14/2004 1:30:31 PM</Property>  
     <Property name="Editor">3;#John Doe</Property>  
     <Property name="_ModerationStatus">0</Property>  
     <Property name="_ModerationComments" />  
     <Property name="FileRef">/sites/BASSite/SourceLibrary/PO1.xml</Property>  
     <Property name="FileDirRef">2;#sites/BASSite/SourceLibrary</Property>  
     <Property name="InLastModified">2004-12-14 13:30:31</Property>  
     <Property name="InCreated">2004-12-14 13:30:31</Property>  
     <Property name="InFileSize">7338</Property>  
     <Property name="FSObjType">0</Property>  
     <Property name="CheckedOutUserId">2;#3</Property>  
     <Property name="Filename">PO1.xml</Property>  
     <Property name="VirusStatus">2;#7338</Property>  
     <Property name="CheckedOutTitle">2;#John Doe</Property>  
     <Property name="LinkCheckedOutTitle">John Doe</Property>  
     <Property name="InLastModifiedBy">MyDomain\jdoe</Property>  
     <Property name="InCreatedBy">MyDomain\jdoe</Property>  
     <Property name="owshiddenversion">1</Property>  
     <Property name="File_x0020_Type">xml</Property>  
     <Property name="HTML_x0020_File_x0020_Type" />  
     <Property name="_SourceUrl" />  
     <Property name="_SharedFileIndex" />  
     <Property name="LinkFilenameNoMenu">PO1.xml</Property>  
     <Property name="LinkFilename">PO1.xml</Property>  
     <Property name="SelectTitle">2</Property>  
     <Property name="SelectFilename">2</Property>  
     <Property name="Edit">xml</Property>  
     <Property name="InIconUrl">/sites/BASSite/SourceLibrary/PO1.xml</Property>  
     <Property name="Url">http://localhost:80/sites/BASSite/SourceLibrary/PO1.xml</Property>  
     <Property name="EncodedAbsUrl">PO1</Property>  
     <Property name="BaseName">7338</Property>  
     <Property name="FileSizeDisplay" />  
     <Property name="InstanceID">200</Property>  
     <Property name="Order" />  
     <Property name="InTitle" />  
     <Property name="ColumnOne" />  
     <Property name="ColumnTwo" />  
     <Property name="ColumnThree" />  
     <Property name="ColumnFour" />  
     <Property name="InListName">SourceLibrary</Property>  
     <Property name="InListUrl">http://localhost:80/sites/BASSite/SourceLibrary</Property>  
     <Property name="InEditUrl">http://localhost:80/sites/BASSite/SourceLibrary/Forms/EditForm.aspx?ID=2</Property>  
     <Property name="InOfficeIntegration">yes</Property>  
</InPropertiesXml>  
```  
  
## <a name="sample-configpropertiesxml"></a>Exemple de ConfigPropertiesXml  
 Voici un exemple de code XML pour ConfigPropertiesXml.  
  
```  
<ConfigPropertiesXml>  
     <PropertyName1>PO number</PropertyName1>  
     <PropertySource1>%XPATH=//orchns:PurchaseOrder/orchns:Header/orchns:ID%</PropertySource1>  
     <PropertyName2>Charge To</PropertyName2>  
     <PropertySource2>%XPATH=//orchns:PurchaseOrder/orchns:orderBody/orchns:chargeTo%</PropertySource2>  
     <PropertyName3>PO Priority</PropertyName3>  
     <PropertySource3>%XPATH=//orchns:PurchaseOrder/orchns:orderBody/orchns:priority%</PropertySource3>  
     <PropertyName4>Order Date</PropertyName4>  
     <PropertySource4>%XPATH=//orchns:PurchaseOrder/orchns:orderBody/orchns:dateOrdered%</PropertySource4>  
</ConfigPropertiesXml>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Pour configurer Windows SharePoint Services emplacement de réception](../core/how-to-configure-a-windows-sharepoint-services-receive-location.md)   
 [Comment configurer un gestionnaire d’envoi Windows SharePoint Services](../core/how-to-configure-a-windows-sharepoint-services-send-handler.md)   
 [Comment configurer un Port d’envoi Windows SharePoint Services](../core/how-to-configure-a-windows-sharepoint-services-send-port.md)   
 [Comment créer un Port d’envoi](../core/how-to-create-a-send-port2.md)   
 [Expressions de l’adaptateur de Windows SharePoint Services](../core/windows-sharepoint-services-adapter-expressions.md)   
 [Prise en charge des Types de colonnes Windows SharePoint Services](../core/supported-windows-sharepoint-services-column-types.md)