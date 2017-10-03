---
title: "Déploiement multiserveur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [Windows SharePoint Services adapters], multi-server deployment
- planning, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, deploying
- Windows SharePoint Services adapters, multi-server deployment
- deploying, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, installing
ms.assetid: 0c6e2aa0-e873-461b-8101-9b0988019597
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d9770a2d9e4977ec23c8ff4013d5415c75087d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="multiserver-deployment"></a>Déploiement multiserveur
Cette rubrique décrit les considérations relatives à la configuration et au déploiement multiserveur de l'adaptateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour Windows SharePoint Services.  
  
## <a name="installing-the-windows-sharepoint-services-adapter-in-a-multiserver-deployment"></a>Installation de l'adaptateur Windows SharePoint Services dans un déploiement multiserveur  
 Sélectionner le composant Service Web Adaptateur Windows SharePoint Services installe le logiciel nécessaire à l'adaptateur Windows SharePoint Services pour traiter les documents entrants et sortants via Windows SharePoint Services. Ce service Web doit être installé sur le même serveur que Windows SharePoint Services.  
  
 Le service Web adaptateur peut gérer plusieurs sites SharePoint qu’il s’agisse de sur le même site IIS ou sur des sites IIS différents.  
  
 L'adaptateur Windows SharePoint Services inclut trois types de composants :  
  
-   composants d'exécution ;  
  
-   composants de conception ;  
  
-   service Web de l'adaptateur.  
  
 Les composants d'exécution de l'adaptateur sont installés et configurés automatiquement par le composant d'exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Les composants de conception de l'adaptateur sont installés et configurés avec d'autres fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous interagissez avec les composants de conception en créant des ports Windows SharePoint Services via les outils inclus dans les outils d'administration, les outils de développement, et les composants Kit de développement logiciel (SDK) ou d'exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous ne pouvez pas personnaliser les options de configuration des composants d'exécution et de conception. Vous pouvez personnaliser uniquement les options de Service Web adaptateur Windows SharePoint Services.  
  
 Seuls les membres du groupe hôtes avec SharePoint activé disposera d’autorisations pour appeler le service Web adaptateur. Pour plus d’informations sur les autorisations Windows SharePoint Services requis par l’exécution de l’adaptateur Windows SharePoint Services, consultez la section sécurité [quel est l’adaptateur Windows SharePoint Services ?](../core/what-is-the-windows-sharepoint-services-adapter.md).  
  
> [!NOTE]
>  Le composant de service Web Adaptateur Windows SharePoint Services est automatiquement sélectionné si vous choisissez d'installer les services BAS.  
  
#### <a name="to-install-the-windows-sharepoint-services-adapter"></a>Pour installer l'adaptateur Windows SharePoint Services  
  
1.  Installer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [vue d’ensemble de l’Installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5).  
  
2.  Sur le **Installation des composants** écran sous **composants disponibles**, sous **des logiciels supplémentaires**, sélectionnez **adaptateur Windows SharePoint Services Service Web**.  
  
> [!NOTE]
>  Vous devez exécuter l'installation et la configuration sur l'ordinateur hébergeant les composants d'exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et l'ordinateur exécutant Windows SharePoint Services.  
  
## <a name="configuring-the-windows-sharepoint-services-adapter-web-service-in-a-multiserver-deployment"></a>Configuration du service Web Adaptateur Windows SharePoint Services dans un déploiement multiserveur  
 L'adaptateur Windows SharePoint Services est configuré à l'aide de la configuration de BizTalk Server. Pour plus d’informations sur ces outils, consultez [vue d’ensemble de la Configuration de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/aa58c43f-8f0e-4a5c-89b9-db7b8a852a72).  
  
### <a name="using-a-custom-configuration"></a>Utilisation d'une configuration personnalisée  
 La Configuration de BizTalk Server fournit un niveau d'analyse très détaillé sur l'état de la configuration des composants installés en local sur votre ordinateur. Il permet de configurer et d'annuler la configuration de composants, de configurer les paramètres de sécurité et d'importer et exporter des configurations d'autres ordinateurs.  
  
 Utilisez le **Windows SharePoint Services** page pour configurer l’adaptateur Windows SharePoint Services sur cet ordinateur. Le tableau suivant répertorie les options de configuration.  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Activer l’adaptateur Windows SharePoint Services sur cet ordinateur**|Sélectionnez **activer l’adaptateur Windows SharePoint Services sur cet ordinateur** pour activer l’adaptateur sur cet ordinateur.|  
|**Groupe Windows**|Le **groupe Windows** liste fournit une vue modifiable du groupe BizTalk adaptateur activé Windows hôtes avec SharePoint.|  
|**Site Web de l’adaptateur Windows SharePoint Services**|Sélectionner le site Web destiné à héberger le service Web de l'adaptateur Windows SharePoint Services.|  
  
 Lorsque vous configurez l'adaptateur Windows SharePoint Services à l'aide de la configuration personnalisée, les événements suivants se produisent :  
  
-   Le groupe Windows Hôtes avec SharePoint activé est créé par défaut, sauf si vous spécifiez un autre groupe Windows.  
  
-   Le site Web par défaut est utilisé pour héberger l'adaptateur Windows SharePoint Services, sauf si vous spécifiez un autre site Web.  
  
-   Le pool d'applications BTSSharePointAdapterWSAppPool est créé et configuré pour être exécuté sous le compte également utilisé pour exécuter le pool d'applications Windows SharePoint Services.  
  
-   L'application virtuelle BTSharePointAdapterWS est créée et configurée pour être exécutée dans le pool d'applications BTSSharePointAdapterWSAppPool.  
  
> [!NOTE]
>  Si ce répertoire virtuel existe déjà, la configuration ne met pas à jour les propriétés dans la métabase. Vous devez supprimer le répertoire virtuel et exécuter à nouveau la configuration.  
  
-   L'application virtuelle BTSharePointAdapterWS contient le service Web.  
  
 Pour plus d’informations sur la Configuration de BizTalk Server, consultez [importer et exporter une Configuration de BizTalk Server](../install-and-config-guides/import-and-export-biztalk-server-configuration.md).  
  
##### <a name="to-configure-the-windows-sharepoint-services-adapter-by-using-custom-configuration"></a>Pour configurer l'adaptateur Windows SharePoint Services à l'aide de la configuration personnalisée  
  
1.  Dans le **Configuration de BizTalk Server**, sélectionnez le **adaptateur SharePoint** nœud.  
  
2.  Sélectionnez **activer l’adaptateur Windows SharePoint Services sur cet ordinateur**.  
  
3.  Sous **groupe Windows**, sélectionnez le groupe Windows que vous utiliserez pour l’adaptateur Windows SharePoint Services. Par défaut, ce groupe est Hôtes avec SharePoint activé.  
  
4.  Dans le **le Site Web adaptateur Windows SharePoint Services** zone déroulante, sélectionnez le site Web où les composants d’adaptateur seront installés. Par défaut, il s'agit du site Web par défaut.  
  
    > [!NOTE]
    >  L'installation du site Web de l'adaptateur Windows SharePoint Services sur un ordinateur SharePoint Server distant, sans autres composants [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installés, est une configuration entièrement prise en charge.  
  
5.  Cliquez sur **Appliquer la configuration**.  
  
## <a name="considerations-for-a-multiserver-deployment"></a>Considérations relatives à un déploiement multiserveur  
 ![](../core/media/adapters-wss-multiserver-screenshot01.gif "Adapters_WSS_Multiserver_Screenshot01")  
  
### <a name="general-considerations"></a>Observations générales  
 Lorsque vous configurez et déployez l'adaptateur Windows SharePoint Services dans un environnement multiserveur, prenez en compte les considérations suivantes :  
  
-   Ajoutez le compte de service BizTalk au groupe Windows Hôtes avec SharePoint activé sur chaque serveur.  
  
-   Ajoutez le groupe Hôtes avec SharePoint activé au rôle Contributeurs SharePoint à l'aide de l'outil Administration centrale de SharePoint.  
  
-   Sous [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)], l'identité sous laquelle le service Web Adaptateur SharePoint est exécuté nécessite les autorisations suivantes :  
  
     **Lecture** autorisations sur le **Program Files\Microsoft BizTalk Server \<version > \Business Activity Services\BTSharePointV3AdapterWS** dossier. Si vous utilisez une version 64 bits de Windows et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les autorisations doivent être définies sur le **Program Files (x86) \Microsoft BizTalk Server \<version > \Business Activity Services\BTSharePointV3AdapterWS**  
  
     **Lecture** autorisation sur la clé de Registre suivante : **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Shared Tools\Web Server\Extensions\12.0\Secure\ConfigDB**.  
  
     autorisations de connexion sur le serveur SQL contenant les bases de données SharePoint ;  
  
     Un membre de la **Public** et **WSS_Content_Application_Pools** rôles au sein de la base de données de configuration de SharePoint.  
  
     Un membre de la **Public** et **propriétaire de la base de données** rôles au sein de la base de données de contenu SharePoint.  
  
-   Le site Web sur lequel vous installez le service Web doit être étendu en tant que site Web SharePoint Services.  
  
-   Vous pouvez installer et configurer l'adaptateur Windows SharePoint Services dans le cadre d'une installation sans assistance. Pour plus d’informations, consultez [annexe a : Installation sans assistance](../install-and-config-guides/appendix-a-silent-installation.md).  
  
### <a name="considerations-for-network-load-balancing-nlb"></a>Considérations relatives à l'équilibrage de la charge réseau  
 L'adaptateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour Windows SharePoint Services prend en charge le clustering d'équilibrage de la charge réseau des serveurs Windows SharePoint Services avec plusieurs serveurs BizTalk configurés dans le même groupe. Pour cela, Windows SharePoint Services doit être installé sur le cluster d'équilibrage de la charge réseau, comme recommandé dans la documentation SharePoint.  
  
 Lorsque vous configurez et déployez l'adaptateur Windows SharePoint Services dans un environnement multiserveur avec équilibrage de la charge réseau, prenez en compte les considérations suivantes :  
  
-   Configurez Windows SharePoint Services en sélectionnant l'option permettant de pointer vers une base de données de gestion BizTalk existante. Pointez vers la base de données de gestion BizTalk créée sur le premier ordinateur. Cela indique à Windows SharePoint Services que vous avez l'intention d'utiliser un environnement de serveur Web. Étendez le site Web en pointant vers la base de données de contenu existante.  
  
-   Vous devez étendre le même site Web (par exemple, site Web par défaut sur le port 80) sur chaque ordinateur Windows SharePoint Services dans l'environnement de serveur Web.  
  
-   BTSharePointAdapterWS doit être installé et configuré de la même façon sur chacun des hôtes d'équilibrage de la charge réseau. Vous devez configurer les paramètres d'équilibrage de la charge réseau suivants :  
  
    -   Protocole : TCP  
  
    -   Ports : 80 (port HTTP du site Web IIS sur lequel le service Web Adaptateur Windows SharePoint Services est installé et configuré)  
  
    -   Mode de filtrage : Hôte multiple  
  
    -   Affinité : Aucune  
  
> [!NOTE]
>  Ce paramètre ne peut être utilisé que si le site n'est pas configuré pour le protocole HTTPS. Si le service Web BTSharePointAdapterWS est installé sur un site avec le protocole HTTPS, vous devez utiliser l'affinité Client unique.  
  
## <a name="see-also"></a>Voir aussi  
 [Adaptateur Windows SharePoint Services](../core/windows-sharepoint-services-adapter.md)   
 [Déploiement de serveur unique](../core/single-server-deployment.md)