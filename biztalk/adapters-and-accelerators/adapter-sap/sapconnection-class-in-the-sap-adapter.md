---
title: "Classe SAPConnection dans l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SAPConnection, supported methods, classes, and constructors
ms.assetid: a700602d-8135-4f67-a38b-770357d4e28b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b27bb8f88686fe1726aed16113ce227347151996
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sapconnection-class-in-the-sap-adapter"></a>Classe SAPConnection dans l’adaptateur SAP
La section suivante répertorie les méthodes et propriétés pour le **SAPConnection** classe. Représente une connexion ADO.NET pour le serveur d’applications SAP.  
  
 Elle est dérivée de **System.Data.Common.DbConnection**.  
  
## <a name="supported-properties"></a>Propriétés prises en charge  
  
|Nom|Get/Set.| Description|  
|----------|--------------|-----------------|  
|**ConnectionString**|Get et Set|Consultez [en savoir plus sur les types de fournisseur de données pour la chaîne de connexion SAP](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).|  
|**ConnectionTimeout**|Obtenir|Non pris en charge. Retourne 0.|  
|**Base de données**|Obtenir|ID du système SAP.|  
|**DataSource**|Obtenir|Cela retourne le nom de l’hôte de serveur d’applications SAP.|  
|**ServerVersion**|Obtenir|Cela affiche le numéro de version de l’instance SAP et non la version du serveur SAP. Par exemple, si le client ADO.NET se connecte au serveur de SAP version 4.6 avec le numéro de version de l’instance 620, cette propriété affiche 620.|  
|**État**|Obtenir|État de la connexion. Les états pris en charge sont :<br /><br /> -[System.Data.ConnectionState]<br /><br /> -Fermé<br /><br /> -Permet d’ouvrir<br /><br /> -Connexion|  
  
## <a name="supported-methods"></a>Méthodes prises en charge  
  
|Nom| Description|  
|----------|-----------------|  
|**ChangeDatabase(string)**|Non pris en charge.|  
|**Close()**|Ferme la connexion au système SAP.|  
|**CreateCommand()**|Retourne un nouveau SAPCommand associé à cette connexion.|  
|**GetSchema()**|Obtient la liste des tables SAP détectés. Toutes les découvertes de tables sont disponibles dans un fichier XML SAPDiscoveredObjects.xml. Le fichier se trouve dans \<lecteur d’installation > : \Program Files\Microsoft Shared\Adapters\SAP.|  
|**GetSchema (String)**|Obtient le schéma basé sur le nom de la collection. Prend en charge le nom de la collection « Tables ».|  
  
|Nom| Description|  
|----------|-----------------|  
|**GetSchema (string, qu'**|Obtient le schéma basé sur les restrictions et le nom de la collection. Le tableau suivant représente les noms de collection et les restrictions prises en charge :|  
  
|Nom|Nom de la collection|Restrictions| Description|  
|----------|---------------------|------------------|-----------------|  
|**GetSchema (string, qu'**|Tables|-|Liste des Tables de SAP détectés|  
|**GetSchema (string, qu'**|Procédures|-|Liste de RFC détectés|  
|**GetSchema (string, qu'**|SearchRFCs|arr [0] : recherche expr|Liste de mise en correspondance les RFC|  
|**GetSchema (string, qu'**|ImportParameters|arr [1] : nom de la RFC|Paramètres d’importation de RFC|  
|**GetSchema (string, qu'**|ImportParameterColumn|arr [1] : nom de la RFC<br /><br /> arr [2] : nom de paramètre|Importer le schéma de paramètre|  
|**GetSchema (string, qu'**|ExportParameters|arr [1] : nom de la RFC|Paramètres d’exportation de RFC|  
|**GetSchema (string, qu'**|ExportParameterColumn|arr [1] : nom de la RFC<br /><br /> arr [2] : nom de paramètre|Exporter le schéma de paramètres|  
|**GetSchema (string, qu'**|TableParameters|arr [1] : nom de la RFC|Paramètres de la table de RFC|  
|**GetSchema (string, qu'**|TableParameterColumn|arr [1] : nom de la RFC<br /><br /> arr [2] : nom de paramètre|Schéma de paramètres table|  
|**GetSchema (string, qu'**|ChangingParameters|arr [1] : nom de la RFC|Modification des paramètres de RFC|  
|**GetSchema (string, qu'**|ChangingParameterColumn|arr [1] : nom de la RFC<br /><br /> arr [2] : nom de paramètre|La modification du schéma de paramètres|  
|**GetSchema (string, qu'**|colonnes|arr [1] : nom de la Table|Schéma de colonne de Table SAP|  
  
|Nom| Description|  
|----------|-----------------|  
|**Open()**|Ouvre une connexion SAP en fonction de la chaîne de connexion.|  
  
> [!NOTE]
>  À l’exception des entrées de la collection de Table, procédure et SearchRFCs, pour toutes les autres entrées de la collection, vous devez spécifier une valeur factice pour arr [0].  
  
## <a name="supported-constructors"></a>Constructeur pris en charge  
  
|Nom| Description|  
|----------|-----------------|  
|**SAPConnection()**|Crée une instance d’objet SAPConnection.|  
|**SAPConnection(string)**|Accepte une chaîne de connexion SAP. Lève une exception si la chaîne de connexion n’est pas valide.|  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre des Interfaces ADO.NET avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)