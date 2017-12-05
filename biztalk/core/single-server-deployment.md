---
title: "Déploiement mono-serveur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows SharePoint Services adapters, deploying
- configuring [Windows SharePoint Services adapters], customizing
- deploying, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, installing
- Windows SharePoint Services adapters, configuring
- configuring [Windows SharePoint Services adapters], single-server deployment
- Windows SharePoint Services adapters, single-server deployment
ms.assetid: 94ba8241-9a30-46ca-b962-721e2d00f420
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6796bbbad4722e959962ea88e9854bce82476be4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="single-server-deployment"></a>Déploiement monoserveur
Cette rubrique décrit les considérations relatives à la configuration et au déploiement monoserveur de l'adaptateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour Windows SharePoint Services.  
  
## <a name="installing-the-windows-sharepoint-services-adapter-in-a-single-server-deployment"></a>Installation de l'adaptateur Windows SharePoint Services dans un déploiement monoserveur  
 Le composant de service Web adaptateur Windows SharePoint Services installe le logiciel nécessaire à l’adaptateur Windows SharePoint Services traiter les documents entrants et sortants via Windows SharePoint Services. Ce service Web doit être installé sur le même serveur que Windows SharePoint Services. Le service Web de l'adaptateur peut traiter plusieurs sites SharePoint, y compris le site Web qui héberge les services BAS, quel que soit leur emplacement (sur le même site IIS ou sur des sites IIS différents).  
  
 L’adaptateur Windows SharePoint Services comprend trois composants :  
  
-   composants d'exécution ;  
  
-   composants de conception ;  
  
-   service Web de l'adaptateur.  
  
 Les composants d'exécution de l'adaptateur sont installés et configurés automatiquement par le composant d'exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Les composants de conception de l'adaptateur sont installés et configurés avec les autres fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous interagissez avec les composants de conception en créant des ports Windows SharePoint Services via les outils inclus dans les outils d'administration, les outils de développement, et les composants Kit de développement logiciel (SDK) ou d'exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous ne pouvez pas personnaliser les options de configuration des composants d'exécution et de conception. Vous pouvez seulement personnaliser les options du service Web Adaptateur Windows SharePoint Services.  
  
 Seuls les membres du groupe Hôtes avec SharePoint activé disposent des autorisations nécessaires pour appeler le service Web de l'adaptateur. Pour plus d’informations sur les autorisations Windows SharePoint Services requis par l’exécution de l’adaptateur Windows SharePoint Services, consultez la section sécurité [quel est l’adaptateur Windows SharePoint Services ?](../core/what-is-the-windows-sharepoint-services-adapter.md).  
  
> [!NOTE]
>  Le composant de service Web Adaptateur Windows SharePoint Services est automatiquement sélectionné si vous choisissez d'installer les services BAS.  
  
#### <a name="to-install-the-windows-sharepoint-services-adapter"></a>Pour installer l'adaptateur Windows SharePoint Services  
  
1.  Installation de BizTalk Server. Pour plus d’informations, consultez [vue d’ensemble de l’Installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5).  
  
2.  Sur le **Installation des composants** écran sous **composants disponibles**, sous **des logiciels supplémentaires**, sélectionnez **adaptateur Windows SharePoint Services Service Web**.  
  
## <a name="configuring-the-windows-sharepoint-services-adapter-web-service-in-a-single-server-deployment"></a>Configuration du service Web Adaptateur Windows SharePoint Services dans un déploiement monoserveur  
 L'adaptateur Windows SharePoint Services est configuré à l'aide de la configuration de base ou d'une configuration personnalisée. Pour plus d’informations sur ces outils, consultez [vue d’ensemble de la Configuration de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/aa58c43f-8f0e-4a5c-89b9-db7b8a852a72).  
  
### <a name="using-a-basic-configuration"></a>Utilisation d'une configuration de base  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de configurer le serveur à l'aide des paramètres par défaut. Ceux-ci sont configurés à l'aide du nom du serveur de base de données, du nom d'utilisateur et du mot de passe que vous entrez dans l'Assistant Configuration. Lorsque vous configurez le service Web Adaptateur Windows SharePoint Services à l'aide de la configuration de base, les événements suivants se produisent :  
  
-   Le groupe Windows Hôtes avec SharePoint activé est créé.  
  
-   Le site Web par défaut est utilisé pour héberger l'adaptateur Windows SharePoint Services.  
  
-   Le pool d’applications BTSSharePointAdapterWSAppPool est créé et configuré pour s’exécuter sous le compte qui est également utilisé pour exécuter le pool d’applications Windows SharePoint Services.  
  
-   L'application virtuelle BTSharePointAdapterWS est créée et configurée pour être exécutée dans le pool d'applications BTSSharePointAdapterWSAppPool.  
  
> [!NOTE]
>  Si ce répertoire virtuel existe déjà, la configuration ne met pas à jour les propriétés dans la métabase. Vous devez supprimer le répertoire virtuel et exécutez à nouveau la configuration.  
  
-   L'application virtuelle BTSharePointAdapterWS contient le service Web.  
  
 Pour plus d’informations sur la configuration de base, consultez [Configuration de base](http://msdn.microsoft.com/library/abdf3eb5-9779-47ff-bc97-2209eb4b12f5).  
  
### <a name="using-a-custom-configuration"></a>Utilisation d'une configuration personnalisée  
 La Configuration de BizTalk Server fournit un niveau d'analyse très détaillé sur l'état de la configuration des composants installés en local sur votre ordinateur. Il permet de configurer et d'annuler la configuration de composants, de configurer les paramètres de sécurité et d'importer et exporter des configurations d'autres ordinateurs.  
  
 Utilisez le **le Service Web adaptateur Windows SharePoint Services** page pour configurer l’adaptateur Windows SharePoint Services sur cet ordinateur. Le tableau suivant répertorie les options de configuration.  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Activer l’adaptateur Windows SharePoint Services sur cet ordinateur**|Sélectionnez **activer l’adaptateur Windows SharePoint Services sur cet ordinateur** pour activer l’adaptateur sur cet ordinateur.|  
|**Groupe Windows**|Le **groupe Windows** liste fournit une vue modifiable du groupe BizTalk adaptateur activé Windows hôtes avec SharePoint.|  
|**Site Web de l’adaptateur Windows SharePoint Services**|Sélectionner le site Web destiné à héberger le service Web Adaptateur Windows SharePoint Services.|  
  
 Lorsque vous configurez l’adaptateur Windows SharePoint Services à l’aide d’une configuration personnalisée, les événements suivants se produisent :  
  
-   Le groupe Windows Hôtes avec SharePoint activé est créé par défaut, sauf si vous spécifiez un autre groupe Windows.  
  
-   Le site Web par défaut est utilisé pour héberger l'adaptateur Windows SharePoint Services, sauf si vous spécifiez un autre site Web.  
  
-   Le pool d'applications BTSSharePointAdapterWSAppPool est créé et configuré pour être exécuté sous le compte également utilisé pour exécuter le pool d'applications Windows SharePoint Services.  
  
-   L'application virtuelle BTSharePointAdapterWS est créée et configurée pour être exécutée dans le pool d'applications BTSSharePointAdapterWSAppPool.  
  
> [!NOTE]
>  Si ce répertoire virtuel existe déjà, la configuration ne met pas à jour les propriétés dans la métabase. Vous devez supprimer le répertoire virtuel et exécutez à nouveau la configuration.  
  
-   L'application virtuelle BTSharePointAdapterWS contient le service Web.  
  
 Pour plus d’informations sur le Gestionnaire de configuration personnalisé, consultez [importer et exporter une Configuration de BizTalk Server](../install-and-config-guides/import-and-export-biztalk-server-configuration.md).  
  
##### <a name="to-configure-the-windows-sharepoint-services-adapter-by-using-a-custom-configuration"></a>Pour configurer l’adaptateur Windows SharePoint Services à l’aide d’une configuration personnalisée  
  
1.  Dans le **Configuration de BizTalk Server**, sélectionnez le **adaptateur SharePoint** nœud.  
  
2.  Sélectionnez **activer l’adaptateur Windows SharePoint Services sur cet ordinateur**.  
  
3.  Sous **groupe Windows**, sélectionnez le groupe Windows que vous utiliserez pour l’adaptateur Windows SharePoint Services. Par défaut, ce groupe est Hôtes avec SharePoint activé.  
  
4.  Dans le **le Site Web adaptateur Windows SharePoint Services** zone déroulante, sélectionnez le site Web où les composants d’adaptateur seront installés. Par défaut, il s'agit du site Web par défaut.  
  
5.  Cliquez sur **Appliquer la configuration**.  
  
## <a name="considerations-for-a-single-server-deployment"></a>Considérations relatives à un déploiement monoserveur  
 Lorsque vous configurez et déployez l'adaptateur Windows SharePoint Services dans un environnement monoserveur, prenez en compte les considérations suivantes :  
  
-   Ajoutez le compte de service BizTalk au groupe Windows Hôtes avec SharePoint activé sur ce serveur.  
  
-   Ajoutez le groupe Hôtes avec SharePoint activé au rôle Contributeurs SharePoint à l'aide de l'outil Administration centrale de SharePoint.  
  
-   Sous [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)], l'identité sous laquelle le service Web Adaptateur SharePoint est exécuté nécessite les autorisations suivantes :  
  
     **Lecture** autorisations sur le **Program Files\Microsoft BizTalk Server \<version\>\Business Activity Services\BTSharePointV3AdapterWS** dossier. Si vous utilisez une version 64 bits de Windows et BizTalk Server, les autorisations doivent être définies sur le **Program Files (x86) \Microsoft BizTalk Server \<version\>\Business Activity Services\BTSharePointV3AdapterWS**  
  
     **Lecture** autorisation sur la clé de Registre suivante : **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Shared Tools\Web Server\Extensions\12.0\Secure\ConfigDB**.  
  
     autorisations de connexion sur le serveur SQL contenant les bases de données SharePoint ;  
  
     Un membre de la **Public** et **WSS_Content_Application_Pools** rôles au sein de la base de données de configuration de SharePoint.  
  
     Un membre de la **Public** et **propriétaire de la base de données** rôles au sein de la base de données de contenu SharePoint.  
  
-   Le site Web sur lequel vous installez le service Web doit être étendu en tant que site Web SharePoint Services.  
  
-   Vous pouvez installer et configurer l’adaptateur Windows SharePoint Services à l’aide d’une installation sans assistance. Pour plus d’informations, consultez [annexe a : Installation sans assistance](../install-and-config-guides/appendix-a-silent-installation.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Adaptateur Windows SharePoint Services](../core/windows-sharepoint-services-adapter.md)   
 [Déploiement multiserveur](../core/multiserver-deployment.md)