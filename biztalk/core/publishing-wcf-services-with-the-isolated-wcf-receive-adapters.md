---
title: "Publication des Services WCF avec WCF isolé des adaptateurs de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive adapters, WCF services
- publishing, WCF services
- WCF services, receive adapters
- WCF services, publishing
ms.assetid: 62ebf373-075c-4c98-8130-ac2cf06e4a70
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c5305560713771e7279eb013d26ff267aa21a74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="publishing-wcf-services-with-the-isolated-wcf-receive-adapters"></a>Publication des services WCF avec les adaptateurs de réception WCF isolés
Les adaptateurs BizTalk Windows Communication Foundation (WCF) permettent [!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour communiquer avec les applications WCF. Les adaptateurs WCF BizTalk incluent sept adaptateurs physiques. Tous (à l'exception de l'adaptateur WCF-CustomIsolated) sont constitués d'adaptateurs d'envoi et de réception.  
  
 Adaptateurs de réception WCF sont fournies dans les deux types de cartes : isolé des adaptateurs WCF et les adaptateurs WCF in-process. Tandis que les adaptateurs In-process sont gérés par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les adaptateurs isolés ne sont pas instanciés par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Au lieu de cela, ils sont instanciés et hébergés dans un autre processus. Les adaptateurs WCF isolés sont hébergés dans les applications Web exécutées sous IIS (Internet Information Services).  
  
> [!NOTE]
>  Avant de publier un service WCF avec les adaptateurs WCF isolés, vous devez être familiarisé avec l'hébergement des services WCF dans IIS (Internet Information Services). Pour plus d’informations sur les services WCF hébergés dans IIS, consultez « Hosting in IIS » à [http://go.microsoft.com/fwlink/?LinkID=75700](http://go.microsoft.com/fwlink/?LinkID=75700).  
  
 **Versions d’IIS**  
  
 Les trois adaptateurs WCF isolés (WCF-CustomIsolated, WCF-BasicHttp et WCF-WSHttp) peuvent être hébergés dans les versions suivantes d'IIS sous les systèmes d'exploitation suivants :  
  
-   **IIS 7.0/7.5 sur Windows Vista et Windows Server 2008.** IIS 7.0/7.5 inclut le même modèle de processus avancé qu'IIS 6.0. Les services WCF BizTalk publiés doivent être exécutés dans le mode de compatibilité ASP.NET d'IIS 7.0/7.5.  
  
> [!NOTE]
>  Si le service d'activation des processus Windows dans IIS 7.0/7.5 permet l'activation et la communication réseau via des protocoles autres que HTTP, les adaptateurs WCF isolés prennent uniquement en charge le transport HTTP.  
  
 **Adaptateurs WCF isolés**  
  
 Voici la liste des adaptateurs WCF isolés :  
  
-   **Adaptateur WCF-WSHttp**. assure la prise en charge des normes WS-* sur le transport HTTP. L'adaptateur WCF-WSHttp met en œuvre les spécifications suivantes : WS-Transaction pour les interactions transactionnelles entre des applications externes et la base de données MessageBox, et WS-Security pour la sécurité et l'authentification des messages. Le transport est de type HTTP ou HTTPS, et le codage des messages est de type texte ou MTOM (Message Transmission Optimization Mechanism).  
  
-   **Adaptateur WCF-BasicHttp**. communique avec des clients et services Web basés sur des fichiers ASMX, ainsi que d'autres services conformes à la norme WS-I Basic Profile 1.1. Le transport est de type HTTP ou HTTPS, et le codage des messages de type texte ou MTOM.  
  
-   **Adaptateur WCF-CustomIsolated**. permet d'utiliser des fonctionnalités d'extensibilité WCF sur le transport HTTP. L'adaptateur vous permet de sélectionner et configurer une liaison WCF et les informations de comportement pour l'emplacement de réception exécuté dans un hôte isolé.  
  
 **Publication de services WCF avec les adaptateurs WCF isolés**  
  
 Pour publier les services WCF avec les adaptateurs de réception WCF isolés, vous devez utiliser l'Assistant Publication de services WCF BizTalk pour créer une application Web qui héberge les adaptateurs WCF isolés. En outre, l'Assistant Publication de services WCF BizTalk génère les fichiers suivants dans le dossier racine de l'application Web créée :  
  
|Fichier|Dossier| Description|  
|----------|------------|-----------------|  
|Services WCF (fichiers .svc)|\|Services WCF pour les emplacements de réception WCF publiés avec les adaptateurs WCF isolés.|  
|Web.config|\|Fichier de configuration ASP.NET contenant les informations relatives aux comportements des applications Web ASP.NET, aux comportements des services WCF publiés, au point de terminaison des métadonnées et aux paramètres spécifiques à BizTalk. La liaison de métadonnées par défaut générée par l'Assistant Publication WCF BizTalk n'est pas sécurisée et permet l'accès anonyme aux métadonnées. Les métadonnées de service contiennent une description détaillée du service et peuvent, intentionnellement ou non, contenir des informations sensibles. Pour protéger les métadonnées de service contre un accès non autorisé, vous pouvez modifier le fichier Web.config pour utiliser une liaison sécurisée pour votre point de terminaison des métadonnées. **Remarque :** pas toutes les combinaisons de liaisons de point de terminaison de métadonnées et les liaisons de point de terminaison de service sont valides. Dans certains cas, les configurations de liaison d'un point de terminaison des métadonnées doivent être conformes aux configurations de liaison de son point de terminaison de service. Par exemple, le point de terminaison des métadonnées ne peut pas être configuré avec un mode de sécurité impliquant le transport HTTP alors que le mode de sécurité de son point de terminaison de service est basé sur HTTPS.|  
|ServiceDescription.xml|\|Fichier XML qui décrit les contrats de service WCF publiés, types de messages inclus.|  
|Schémas BizTalk (fichiers .xsd)|\App_Data|Schémas XML définissant la structure des messages d'instance XML, qui sont publiés avec les adaptateurs WCF isolés.|  
|SchemaIndex.xml|\App_Data|Fichier XML qui indique les fichiers de schéma XML utilisés dans les services WCF publiés.|  
|Serialization.xsd|\App_Data|Schéma XML exporté par [DataContractSerializer](http://go.microsoft.com/fwlink/?LinkId=81722) pour les types, les éléments et les attributs à partir de l’espace de noms, http://schemas.microsoft.com/2003/10/Serialization/.|  
|BindingInfo.xml|\App_Data\Temp|Fichier de liaison BizTalk qui permet de créer les emplacements de réception WCF correspondant aux services WCF publiés. Le fichier BindingInfo.xml peut être importé à l'aide d'un outil ou d'un Assistant de ligne de commande pour créer les emplacements de réception nécessaires. Les services WCF publiés n'utilisent pas ce fichier et le dossier Temp au moment de l'exécution.|  
|WcfServiceDescription.xml|\App_Data\Temp|Fichier XML qui résume les paramètres que vous avez utilisés avec l'Assistant Publication de services WCF BizTalk pour créer cette application Web. Les services WCF publiés n'utilisent pas ce fichier et le dossier Temp au moment de l'exécution.|  
  
 L'Assistant Publication de services WCF BizTalk permet également de créer des emplacements de réception WCF et des métadonnées de service pour les emplacements de réception exécutant les adaptateurs WCF isolés.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment utiliser l’Assistant Publication de services WCF BizTalk pour publier des Orchestrations en tant que Services WCF](../core/publish-orchestrations-as-wcf-services--biztalk-wcf-service-publishing-wizard.md)  
  
-   [Comment utiliser l’Assistant Publication de services WCF BizTalk pour publier des schémas en tant que Services WCF](../core/publish-schemas-as-wcf-services--use-the-biztalk-wcf-service-publishing-wizard.md)  
  
-   [Configuration d’IIS pour WCF isolé des adaptateurs de réception](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md)  
  
-   [Comment configurer des Services WCF publiés à l’Assistant Publication de services WCF BizTalk](../core/configure-wcf-services-published-with-the-biztalk-wcf-service-publishing-wizard.md)  
  
-   [Comment créer une Application .NET pour tester un Service WCF publié avec l’Assistant Publication de services WCF BizTalk](../core/use-net-application-to-test-wcf-service-published-with-wcf-service-publishing.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Publication de Services WCF avec l’adaptateur WCF-BasicHttp](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)