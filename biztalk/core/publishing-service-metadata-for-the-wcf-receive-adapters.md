---
title: "Publier les métadonnées de Service pour les adaptateurs de réception WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4df09e8f-e0c9-41c5-bd71-13bb0e96cd97
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f6962ec3068694223bd6ca214d2d7500e0d5316
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="publishing-service-metadata-for-the-wcf-receive-adapters"></a>Publication des métadonnées de Service WCF pour les adaptateurs de réception
L'Assistant Publication de services WCF BizTalk permet de créer des services WCF à des fins de publication des métadonnées de service pour les emplacements de réception WCF existants. Pour générer le code de modèle de service client à partir de documents de métadonnées publiés, vous pouvez utiliser l’outil Service Model Metadata Utility (SvcUtil.exe) inclus dans le Kit de développement logiciel (SDK) Windows et les composants d’exécution .NET Framework.  
  
> [!NOTE]
>  Avant de publier des métadonnées de service pour les adaptateurs WCF, vous devez créer WCF des emplacements de réception à l’aide de la console Administration de BizTalk ou l’outil de ligne de commande BTSTask inclus dans BizTalk Server. Pour plus d’informations sur la création d’un service WCF, emplacement de réception, consultez la rubrique appropriée pour chaque adaptateur WCF dans [adaptateurs WCF](../core/wcf-adapters.md).  
  
## <a name="iis-versions"></a>Versions d’IIS
  
 Le service WCF qui publie les métadonnées de service peut être en cours d’exécution la version d’IIS incluse avec le système d’exploitation.
  
-   **IIS** fournit le modèle de processus avancé. Les services WCF BizTalk publiés doivent s’exécuter en Mode de compatibilité ASP.NET. Les métadonnées de service publiées par les applications Web dans IIS pour les adaptateurs de réception WCF sont accessibles via le transport HTTP.  
  
## <a name="publish-service-metadata-for-the-wcf-receive-locations"></a>Publier les métadonnées de service pour les emplacements de réception WCF
  
 Pour publier les métadonnées de service pour les emplacements de réception, vous devez utiliser l'Assistant Publication de services WCF BizTalk pour créer une application Web qui héberge les services WCF afin de fournir des métadonnées de service. Ceci permet à un emplacement de réception d'être appelé comme s'il était un service WCF.  L'Assistant Publication de services WCF BizTalk génère les fichiers suivants dans le dossier racine de l'application Web créée :  
  
|Fichier|Dossier| Description|  
|----------|------------|-----------------|  
|Services WCF (fichiers .svc)|\|Services WCF qui publient les métadonnées de service WCF pour les emplacements de réception. Les services WCF publient les métadonnées de service pour extraction à l'aide d'une requête HTTP/GET.|  
|Web.config|\|Fichier de configuration d’ASP.NET qui contient des informations pour les comportements d’application Web ASP.NET, les comportements de service WCF publiés, le point de terminaison de métadonnées et les paramètres spécifiques à BizTalk. L’Assistant génère le fichier Web.config lorsque la **httpGetEnabled** attribut de la  **\<serviceMetadata\>**  a la valeur **true**. Vous pouvez utiliser un outil d'importation de métadonnées (tel que SvcUtil.exe) pour générer le code client requis pour appeler ce service dans l'environnement de développement. L’adresse à laquelle les métadonnées sont publiées est l’adresse de point de terminaison du service WCF plus une **? wsdl** chaîne de requête. **Remarque :** la liaison de métadonnées par défaut générée par l’Assistant Publication WCF BizTalk n’est pas sécurisée et il autorise l’accès anonyme aux métadonnées. Les métadonnées de service contiennent une description détaillée du service et peuvent, intentionnellement ou non, contenir des informations sensibles. Pour protéger les métadonnées de service contre un accès non autorisé, vous pouvez modifier le fichier Web.config pour utiliser une liaison sécurisée pour votre point de terminaison des métadonnées.|  
|ServiceDescription.xml|\|Fichier XML qui décrit le service WCF publié contrats y compris les types de messages.|  
|Schémas BizTalk (fichiers .xsd)|\App_Data|Schémas XML définissant la structure des messages d'instance XML, qui sont utilisés dans l'emplacement de réception WCF.|  
|SchemaIndex.xml|\App_Data|Fichier XML qui indique les fichiers de schéma XML utilisés dans l'emplacement de réception WCF.|  
|Serialization.xsd|\App_Data|Schéma XML exporté par [DataContractSerializer](https://msdn.microsoft.com/library/system.runtime.serialization.datacontractserializer.aspx) pour les types, les éléments et les attributs à partir de l’espace de noms, http://schemas.microsoft.com/2003/10/Serialization/.|  
|BindingInfo.xml|\App_Data\Temp|Fichier de liaison BizTalk qui peut être importé à l'aide d'un outil ou d'un Assistant de ligne de commande pour configurer les emplacements de réception. Les services WCF publiés n'utilisent pas ce fichier et le dossier Temp au moment de l'exécution.|  
|WcfServiceDescription.xml|\App_Data\Temp|Fichier XML qui résume les paramètres que vous avez utilisés avec l'Assistant Publication de services WCF BizTalk pour créer cette application Web. Les services WCF publiés n'utilisent pas ce fichier et le dossier Temp au moment de l'exécution.|  
  
## <a name="next-steps"></a>Étapes suivantes
  
-   [Utiliser l’Assistant Publication de services WCF BizTalk afin de publier des métadonnées de service pour un emplacement de réception WCF pour le routage basé sur le contenu](../core/publish-service-metadata-for-a-wcf-receive-location-for-content-based-routing.md)  
  
-   [Utiliser l’Assistant Publication de services WCF BizTalk afin de publier des métadonnées de service pour un emplacement de réception WCF lié à un port d’orchestration](../core/publish-receive-location-service-metadata-biztalk-wcf-service-publishing-wizard.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Publication des services WCF avec l’adaptateur WCF-NetMsmq](../core/walkthrough-publishing-wcf-services-with-the-wcf-netmsmq-adapter.md)