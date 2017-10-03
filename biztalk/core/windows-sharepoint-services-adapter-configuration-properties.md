---
title: "Propriétés de Configuration de l’adaptateur Windows Sharepoint Services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code samples, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, properties
- receive locations, adapters
- Windows SharePoint Services adapters, code sample
- Windows SharePoint Services adapters, send ports
- Windows SharePoint Services adapters, receive locations
- Windows SharePoint Services adapters
- send ports, adapters
ms.assetid: 20b08959-75d3-4613-9cea-582ac2813415
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e6e26d51914211c5c51dfa232be4383d54f5e3c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="windows-sharepoint-services-adapter-configuration-properties"></a>Propriétés de configuration de l'adaptateur Windows SharePoint Services
Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir pour l'emplacement de réception de l'adaptateur Windows Sharepoint Services :  
  
|Nom de la propriété|Type| Description|Restrictions|Commentaires|  
|-------------------|----------|-----------------|------------------|--------------|  
|SiteUrl|VT_BSTR|Spécifier l'URL complète du site Web Windows SharePoint Services.|L'URI d'un port d'envoi ou d'un emplacement de réception ne peut pas comporter plus de 256 caractères.|Aucune|  
|WssLocation|VT_BSTR|Spécifier l'URL de la bibliothèque de documents Windows SharePoint Services, relative au site SharePoint, où les documents sont extraits.|Vous ne pouvez pas recevoir de messages d'une liste ou d'un dossier SharePoint.|L'URL de bibliothèque de documents SharePoint est parfois différente du nom de cet élément. Consultez la barre d'adresse d'Internet Explorer pour connaître l'URL correcte.|  
|NomVue|VT_BSTR|Spécifier la vue Windows SharePoint Services utilisée pour filtrer les documents traités par l'adaptateur.|Aucune|Tous les messages dans un affichage en 2D sont traités.|  
|ArchiveLocation|VT_BSTR|Spécifier l'URL de dossier de Windows SharePoint Services, relative au site SharePoint, dans laquelle sont archivés les fichiers traités.|Aucune|L'URL de bibliothèque de documents ou de dossier SharePoint est parfois différente du nom de cet élément. Consultez la barre d'adresse d'Internet Explorer pour connaître l'URL correcte.|  
|NamespaceAliases|VT_BSTR|Spécifier une liste, séparée par des virgules ou des points-virgules, des définitions des alias d'espaces de noms.|Aucune|Aucune|  
|ArchiveFileName|VT_BSTR|Spécifier le nom de fichier Windows SharePoint Services du fichier archivé.|Les macros « %SendingOrchestrationID% » et « %SendingOrchestrationType% » ne sont pas prises en charge par ce champ.|Aucune|  
|Remplacer|VT_BSTR|Spécifier si les fichiers existants de l'archive sont remplacés.|Les valeurs valides sont :<br /><br /> -Oui<br />-Aucun|La valeur par défaut est no.|  
|ErrorThreshold|VT_BSTR|Spécifier le nombre maximal d'échecs d'interrogation consécutifs rencontrés par l'adaptateur avant que l'emplacement de réception ne soit désactivé.|Les valeurs valides sont comprises entre 0 et 2147483647.|Définissez cette propriété sur 0 afin de ne jamais désactiver l'emplacement de réception.<br /><br /> La valeur par défaut est 10.|  
|PollingInterval|VT_BSTR|Spécifier l'intervalle de temps, en secondes, entre deux requêtes consécutives exécutées par l'adaptateur pour vérifier si de nouveaux messages sont disponibles pour le traitement.|Les valeurs valides sont compris entre 1 et 2147483647.|La spécification d'une valeur inférieure améliore le débit et le temps de réponse de l'adaptateur.<br /><br /> La valeur par défaut est 60.|  
|BatchSize|VT_BSTR|Spécifier le nombre maximal de documents que le service Web de l'adaptateur de messagerie Windows SharePoint Services va traiter en un seul lot.|Les valeurs valides sont compris entre 1 et 2147483647.|Un lot traité peut contenir un nombre de messages inférieur à la taille du lot définie ; toutefois, il ne peut pas contenir un nombre de messages supérieur à cette taille.<br /><br /> La valeur par défaut est 20.|  
|OfficeIntegration|VT_BSTR|Spécifier le niveau d'intégration de Microsoft Office.|Les valeurs valides sont :<br /><br /> -   **facultatif** - essayez de supprimer les instructions de traitement InfoPath si possible ou à traiter comme s’il n’est pas possible.<br />-   **ne** -traiter le document « tel quel ».<br />-   **Oui** - supprimer les instructions de traitement InfoPath ou ignorer le message en cas d’erreur.|La valeur par défaut est « facultatif ».|  
|Délai d'expiration|VT_BSTR|Spécifiez le délai d’attente, en millisecondes, pour les appels de service Web adaptateur runtime apportées à l’adaptateur Windows SharePoint Services service Web.|Les valeurs valides sont de 1000 et 2147483647.|La valeur par défaut est 100 000.|  
|AdapterWSPort|VT_BSTR|Spécifier le port HTTP du site Web IIS sur lequel est installé le service Web de l'adaptateur Windows SharePoint Services.|Aucune|La valeur par défaut est 80.|  
|uri|VT_BSTR|Spécifier le chemin d'accès complet à la bibliothèque de documents Windows SharePoint Services.|L'URI d'un port d'envoi ou d'un emplacement de réception ne peut pas comporter plus de 256 caractères.|Aucune|  
  
 Le code suivant présente le format de la chaîne que vous devez utiliser pour définir les propriétés :  
  
```  
<CustomProps><AdapterConfig vt="8"><ReceiveLocation xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><SiteUrl>http://BTS2006/sites/BASSite/</SiteUrl><WssLocation>Shared Docs</WssLocation><ViewName>Approved</ViewName><ArchiveLocation>Archive</ArchiveLocation><NamespaceAliases>po='http://POProcess/POrder'</NamespaceAliases><ArchiveFileName>PurchaseOrder0001.xml</ArchiveFileName><Overwrite>no</Overwrite><ErrorThreshold>10</ErrorThreshold><PollingInterval>60</PollingInterval><BatchSize>20</BatchSize><OfficeIntegration>optional</OfficeIntegration><Timeout>100000</Timeout><AdapterWSPort>80</AdapterWSPort><uri>wss://bts2006:80/sites/BASSite/Shared+Docs?ViewName=Approved</uri></ReceiveLocation></AdapterConfig></CustomProps>  
```  
  
 Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir pour le port d'envoi de l'adaptateur Windows Sharepoint Services :  
  
|Nom de la propriété|Type| Description|Restrictions|Commentaires|  
|-------------------|----------|-----------------|------------------|--------------|  
|SiteUrl|VT_BSTR|Spécifier l'URL complète du site Web Windows SharePoint Services|L'URI d'un port d'envoi ou d'un emplacement de réception ne peut pas comporter plus de 256 caractères.|Aucune|  
|WssLocation|VT_BSTR|Spécifier l'URL du dossier de destination de Windows SharePoint Services, relative au site SharePoint.|Aucune|Il arrive que l'URL de la bibliothèque de documents, de la liste ou du dossier SharePoint soit différente du nom de cet élément. Consultez la barre d'adresses d'Internet Explorer pour connaître l'URL correcte.|  
|Remplacer|VT_BSTR|Spécifier si les fichiers existants doivent être remplacés.|Les valeurs valides sont :<br /><br /> -Aucun<br />-orchestration<br />-renommer<br />-Oui|La valeur par défaut est no.|  
|NamespaceAliases|VT_BSTR|Spécifier une liste, séparée par des virgules ou des points-virgules, des définitions des alias d'espaces de noms.|Aucune|Utilisez ce champ pour définir les alias d'espaces de noms utilisés par les requêtes XPATH introduites dans les champs.<br /><br /> Cette propriété ne remplace pas la propriété de contexte de message WSS.ConfigNamespacesAliases définie par l'orchestration. Les deux valeurs sont fusionnées.|  
|FileName|VT_BSTR|Spécifier le nom de fichier Windows SharePoint Services du fichier archivé|Aucune|Lors de l'envoi de messages à une liste, la valeur spécifiée dans la propriété Nom de fichier est ignorée et ne sera pas enregistrée dans une colonne SharePoint. Les listes SharePoint n’ont pas de colonne Nom de fichier. Vous devez donc mettre à jour la colonne Titre en utilisant l'une des 16 colonnes disponibles.|  
|OfficeIntegration|VT_BSTR|Spécifier la modification du document de sorte qu'il s'ouvre automatiquement dans une application Office comme InfoPath ou pour l'enregistrer en l'état si aucune solution InfoPath n'est trouvée.|Les valeurs valides sont :<br /><br /> -Aucun<br />-facultatif<br />-orchestration<br />-Oui<br />-yesformlibrary|La valeur par défaut est « facultatif ».|  
|TemplatesDocLib|VT_BSTR|Spécifier le nom d'une bibliothèque de documents SharePoint où sont stockées les solutions InfoPath.|Cette propriété doit contenir une valeur si la propriété TemplatesNamespaceCol contient une valeur.|La bibliothèque de documents doit comporter au moins une colonne SharePoint de type Une seule ligne de texte renseignée avec l'espace de noms et le nœud racine des documents XML pouvant être ouverts avec cette solution InfoPath, ou avec le nœud racine uniquement.|  
|TemplatesNamespaceCol|VT_BSTR|Spécifier le nom de la colonne SharePoint de la bibliothèque de documents Modèles de secours qui contient l'espace de noms de la solution InfoPath,|Cette propriété doit contenir une valeur si la propriété TemplatesDocLib contient une valeur.<br /><br /> Ce champ respecte la casse.|Aucune|  
|CustomTemplatesDocLib|VT_BSTR|Spécifier le nom d'une bibliothèque de documents SharePoint où sont stockées les solutions InfoPath.|Cette propriété doit contenir une valeur si la propriété CustomTemplatesNamespaceCol contient une valeur.<br /><br /> Ce champ respecte la casse.|Aucune|  
|CustomTemplatesNamespaceCol|VT_BSTR|Spécifier le nom de la colonne SharePoint de la bibliothèque de documents Modèles qui contient l'espace de noms de la solution InfoPath.|Cette propriété doit contenir une valeur si la propriété CustomTemplatesDocLib contient une valeur.<br /><br /> Ce champ respecte la casse.|Aucune|  
|PropertyName(n)|VT_BSTR|Spécifier le nom de la colonne Windows SharePoint Services qui existe dans la bibliothèque des documents de destination.|Ce champ respecte la casse.|Vous pouvez indiquer jusqu'à 16 colonnes.|  
|PropertySource(n)|VT_BSTR|Spécifier la valeur de colonne à définir pour ce message.|Aucune|Vous pouvez indiquer jusqu'à 16 valeurs de colonne.|  
|Délai d'expiration|VT_BSTR|Spécifier le délai d'expiration, en millisecondes, des appels du service Web d'exécution de l'adaptateur adressés au service Web de l'adaptateur Windows SharePoint Services.|Les valeurs valides sont de 1000 et 2147483647.|La valeur par défaut est 100 000.|  
|AdapterWSPort|VT_BSTR|Spécifier le port HTTP du site Web IIS sur lequel est installé le service Web de l'adaptateur Windows SharePoint Services.|Aucune|La valeur par défaut est 80.|  
|uri|VT_BSTR|Spécifier le chemin d'accès complet à l'URL du dossier de destination de Windows SharePoint Services.|L'URI d'un port d'envoi ou d'un emplacement de réception ne peut pas comporter plus de 256 caractères.|Aucune|  
  
 Le code suivant présente le format de la chaîne que vous devez utiliser pour définir les propriétés :  
  
> [!NOTE]
>  Les définitions de la propriété PropertyName2, des propriétés PropertySource2 à PropertyName16 et de la propriété PropertySource16 ont été omises dans cette chaîne.  
  
```  
<CustomProps><AdapterConfig vt="8"><SendPort xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><SiteUrl>http://BizTalkServer/sites/BASSite/</SiteUrl><WssLocation>Shared Documents/Purchase Orders</WssLocation><Overwrite>yes</Overwrite><NamespaceAliases>po='http://OrderProcess/POrder'</NamespaceAliases><FileName>PurchaseOrder0001.xml</FileName><OfficeIntegration>yesformlibrary</OfficeIntegration><TemplatesDocLib>Templates</TemplatesDocLib><TemplatesNamespaceCol>NamespaceFallback</TemplatesNamespaceCol><CustomTemplatesDocLib>Shared Documents</CustomTemplatesDocLib><CustomTemplatesNamespaceCol>Namespace</CustomTemplatesNamespaceCol><PropertyName1>Column1</PropertyName1><PropertySource1>Column1 Value</PropertySource1><Timeout>100000</Timeout><AdapterWSPort>80</AdapterWSPort><uri>wss://biztalkserver:80/sites/BASSite/Shared%20Documents/Purchase%20Orders</uri></SendPort></AdapterConfig></CustomProps>  
```  
  
> [!NOTE]
>  Lorsque vous spécifiez les données de configuration TransportTypeData pour un adaptateur qui est construit à l’aide de l’infrastructure d’adaptateurs, les paires nom/valeur utilisées doivent toutes être stockées dans le \<AdapterConfig > élément. Étant donné que le \<AdapterConfig > élément spécifie le VT_BSTR (vt = « 8 ») type de données, puis le \< > caractères dans les données doivent être échappés.