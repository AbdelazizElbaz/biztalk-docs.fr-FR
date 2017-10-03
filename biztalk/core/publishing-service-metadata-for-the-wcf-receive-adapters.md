---
title: "Publication des métadonnées de Service WCF pour les adaptateurs de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing, WCF services
- WCF services, publishing
ms.assetid: 4df09e8f-e0c9-41c5-bd71-13bb0e96cd97
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d922c0acecf81a96b0e40cebf739e7b56c5ffd3e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="publishing-service-metadata-for-the-wcf-receive-adapters"></a>Publication des métadonnées de Service WCF pour les adaptateurs de réception
L'Assistant Publication de services WCF BizTalk permet de créer des services WCF à des fins de publication des métadonnées de service pour les emplacements de réception WCF existants. Pour générer le code de modèle de service client à partir de documents de métadonnées publiés, vous pouvez utiliser l’outil Service Model Metadata Utility (SvcUtil.exe) inclus dans le [!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] Kit de développement logiciel (SDK) pour [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] et [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] Composants d’exécution.  
  
> [!NOTE]
>  Avant de publier des métadonnées de service pour les adaptateurs WCF, vous devez créer WCF à l’aide de la console Administration de BizTalk ou l’outil de ligne de commande BTSTask inclus dans les emplacements de réception [!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur la création d’un service WCF, emplacement de réception, consultez la rubrique appropriée pour chaque adaptateur WCF dans [adaptateurs WCF](../core/wcf-adapters.md).  
  
 **Versions d’IIS**  
  
 Le service WCF qui publie les métadonnées de service peut être exécuté sur les versions suivantes d'Internet Information Services (IIS) sous les systèmes d'exploitation suivants :  
  
-   **IIS 7.0/7.5 sur Windows Vista, Windows Server 2008 SP2 et Windows Server 2008 R2.** IIS 7.0/7.5 incluent le même modèle de processus avancé qu'IIS 6.0. Les services WCF BizTalk publiés doivent être exécutés dans le mode de compatibilité ASP.NET d'IIS 7.0/7.5. Les métadonnées de service publiées par les applications Web dans IIS 7.0/7.5 pour les adaptateurs de réception WCF sont accessibles via le transport HTTP.  
  
 **Publication des métadonnées de service pour les emplacements de réception WCF**  
  
 Pour publier les métadonnées de service pour les emplacements de réception, vous devez utiliser l'Assistant Publication de services WCF BizTalk pour créer une application Web qui héberge les services WCF afin de fournir des métadonnées de service. Ceci permet à un emplacement de réception d'être appelé comme s'il était un service WCF.  L'Assistant Publication de services WCF BizTalk génère les fichiers suivants dans le dossier racine de l'application Web créée :  
  
|Fichier|Dossier| Description|  
|----------|------------|-----------------|  
|Services WCF (fichiers .svc)|\|Services WCF qui publient les métadonnées de service pour les emplacements de réception WCF. Les services WCF publient les métadonnées de service pour extraction à l'aide d'une requête HTTP/GET.|  
|Web.config|\|Fichier de configuration ASP.NET contenant les informations relatives aux comportements des applications Web ASP.NET, aux comportements des services WCF publiés, au point de terminaison des métadonnées et aux paramètres spécifiques à BizTalk. L’Assistant génère le fichier Web.config lorsque la **httpGetEnabled** attribut de la  **\<serviceMetadata >** a la valeur **true**. Vous pouvez utiliser un outil d'importation de métadonnées (tel que SvcUtil.exe) pour générer le code client requis pour appeler ce service dans l'environnement de développement. L’adresse à laquelle les métadonnées sont publiées est l’adresse de point de terminaison du service WCF plus une **? wsdl** chaîne de requête. **Remarque :** la liaison de métadonnées par défaut générée par l’Assistant Publication WCF BizTalk n’est pas sécurisée et il autorise l’accès anonyme aux métadonnées. Les métadonnées de service contiennent une description détaillée du service et peuvent, intentionnellement ou non, contenir des informations sensibles. Pour protéger les métadonnées de service contre un accès non autorisé, vous pouvez modifier le fichier Web.config pour utiliser une liaison sécurisée pour votre point de terminaison des métadonnées.|  
|ServiceDescription.xml|\|Fichier XML qui décrit les contrats de service WCF publiés, types de messages inclus.|  
|Schémas BizTalk (fichiers .xsd)|\App_Data|Schémas XML définissant la structure des messages d'instance XML, qui sont utilisés dans l'emplacement de réception WCF.|  
|SchemaIndex.xml|\App_Data|Fichier XML qui indique les fichiers de schéma XML utilisés dans l'emplacement de réception WCF.|  
|Serialization.xsd|\App_Data|Schéma XML exporté par [DataContractSerializer](http://go.microsoft.com/fwlink/?LinkId=81722) pour les types, les éléments et les attributs à partir de l’espace de noms, http://schemas.microsoft.com/2003/10/Serialization/.|  
|BindingInfo.xml|\App_Data\Temp|Fichier de liaison BizTalk qui peut être importé à l'aide d'un outil ou d'un Assistant de ligne de commande pour configurer les emplacements de réception. Les services WCF publiés n'utilisent pas ce fichier et le dossier Temp au moment de l'exécution.|  
|WcfServiceDescription.xml|\App_Data\Temp|Fichier XML qui résume les paramètres que vous avez utilisés avec l'Assistant Publication de services WCF BizTalk pour créer cette application Web. Les services WCF publiés n'utilisent pas ce fichier et le dossier Temp au moment de l'exécution.|  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment utiliser l’Assistant Publication de services WCF BizTalk pour publier des métadonnées de Service pour l’emplacement de réception d’un service WCF pour le routage basé sur le contenu](../core/publish-service-metadata-for-a-wcf-receive-location-for-content-based-routing.md)  
  
-   [Comment utiliser l’Assistant Publication de services WCF BizTalk pour publier des métadonnées de Service pour l’emplacement de réception WCF lié à un Port d’Orchestration](../core/publish-receive-location-service-metadata-biztalk-wcf-service-publishing-wizard.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Publication de Services WCF avec l’adaptateur WCF-NetMsmq](../core/walkthrough-publishing-wcf-services-with-the-wcf-netmsmq-adapter.md)