---
title: "Comment utiliser l’Assistant Publication de services WCF BizTalk pour publier des métadonnées de Service pour l’emplacement de réception WCF lié à un Port d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Service Publishing Wizard, publishing metadata
- WCF services, orchestration ports
- WCF services, metadata
- orchestrations, WCF services
ms.assetid: 04ccce9f-8d18-433a-8299-d06fa155db06
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93f739620b16514df26c836d645af41b8be0e8eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-biztalk-wcf-service-publishing-wizard-to-publish-service-metadata-for-a-wcf-receive-location-bound-to-an-orchestration-port"></a>Procédure d'utilisation de l'Assistant Publication de services WCF BizTalk pour publier des métadonnées de service pour un emplacement de réception WCF lié à un port d'orchestration
L'Assistant Publication de services WCF BizTalk permet de créer un service WCF à des fins de publication des métadonnées de service pour les emplacements de réception WCF existants liés aux ports d'orchestration.  
  
> [!NOTE]
>  Vous devez créer vos projets BizTalk avant d'exécuter l'Assistant Publication de services WCF BizTalk. Ceux-ci doivent inclure des orchestrations disposant au moins d'un port de réception dont le modificateur de type est public. Avant de publier les métadonnées de service pour les adaptateurs WCF, vous devez également créer les emplacements de réception WCF à l'aide de la console Administration de BizTalk ou de l'outil de ligne de commande BTSTask inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur la création d’un service WCF, emplacement de réception, consultez la rubrique appropriée pour chaque adaptateur WCF dans [adaptateurs WCF](../core/wcf-adapters.md).  
  
### <a name="to-publish-service-metadata-for-an-existing-wcf-receive-location-bound-to-an-orchestration-port"></a>Pour publier des métadonnées de service pour un emplacement de réception WCF existant lié à un port d'orchestration  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Assistant Publication du Service WCF BizTalk**.  
  
    > [!NOTE]
    >  Pour créer et publier des métadonnées de service WCF pour les orchestrations et les schémas BizTalk, vous utilisez l'Assistant Publication de services WCF BizTalk. Pour publier les orchestrations et les schémas en tant que services Web à l'aide de l'adaptateur SOAP, vous utilisez l'Assistant Publication de services Web BizTalk.  
  
2.  Sur le **Bienvenue dans l’Assistant de publication des services WCF BizTalk** , cliquez sur **suivant**.  
  
3.  Sur le **Type de Service WCF** page, sélectionnez le **point de terminaison métadonnées uniquement (MEX)** option pour publier les services WCF pour fournir des métadonnées de service pour WCF emplacement de réception que vous sélectionnez dans l’étape suivante.  
  
     ![Page Type de Service WCF](../core/media/794a85b5-6454-4cce-8c15-382b5583b0f2.gif "794a85b5-6454-4cce-8c15-382b5583b0f2")  
  
4.  Sur le **Type de Service WCF** page, dans le **emplacement de réception de publier les métadonnées pour** la liste déroulante, sélectionnez un service WCF emplacement de réception pour publier des métadonnées de service, puis cliquez sur **suivant**.  
  
5.  Sur le **créer un Service WCF** page, sélectionnez **publier des orchestrations BizTalk en tant que service WCF**, puis cliquez sur **suivant**.  
  
     ![Créer une page de Service WCF](../core/media/86cb66b5-6842-4330-8942-20afa68ec5fa.gif "86cb66b5-6842-4330-8942-20afa68ec5fa")  
  
6.  Sur le **BizTalk Assembly** page, dans le **fichier d’assembly BizTalk (\*.dll)** zone de texte, tapez le nom du fichier d’assembly BizTalk ou cliquez sur **Parcourir** pour accéder à l’assembly contenant l’ou les orchestrations à publier des métadonnées de service, puis cliquez sur **suivant**.  
  
    > [!NOTE]
    >  Avant de sélectionner un fichier d’assembly BizTalk, copiez tous les assemblys dépendants dans le même dossier avec l’assembly BizTalk ou installer les assemblys dépendants dans le global assembly cache (GAC).  
  
    > [!NOTE]
    >  Si vous avez installé le fichier d’assembly BizTalk dans le GAC, assurez-vous que l’assembly dans le GAC a été mis à jour avec l’assembly que vous sélectionnez dans la **BizTalk Assembly** boîte de dialogue. Toutefois, si l'assembly du GAC possède le même nom complet, l'Assistant Publication de services WCF BizTalk utilise le fichier de l'assembly du GAC plutôt que celui sélectionné par vos soins.  
  
    > [!NOTE]
    >  Les chemins d'accès de plus de 260 caractères risquent d'entraîner un message d'erreur indiquant que le chemin d'accès est trop long.  
  
     ![Page BizTalk Assembly](../core/media/d34a027e-ea82-4048-8b15-d97df795b0d4.gif "d34a027e-ea82-4048-8b15-d97df795b0d4")  
  
7.  Sur le **Orchestrations et Ports** page, développez les nœuds d’arborescence pour chaque assembly et l’orchestration en cliquant sur le signe plus (+). Sélectionnez les ports et orchestrations pour lesquels publier les métadonnées en activant les cases à cocher correspondantes dans les nœuds de l'arborescence. Si vous souhaitez créer un service WCF (fichier .svc) pour tous les ports de réception sélectionnés au lieu d’un service WCF pour chaque port de réception, sélectionnez le **fusionner les ports sélectionnés en un seul service WCF** option, puis cliquez sur  **Suivant**.  
  
    > [!NOTE]
    >  Lorsque vous fusionnez tous les ports sélectionnés en un seul service WCF, ceux-ci disposent du même type de port, mais les noms des opérations demeurent uniques.  
  
     ![Page opérations et Ports](../core/media/97112744-ddd4-4512-ac56-41317ba9412b.gif "97112744-ddd4-4512-ac56-41317ba9412b")  
  
8.  Sur le **propriétés du Service WCF** page, dans le **Targetnamespace du service WCF** zone de texte, tapez un espace de noms cible pour les services WCF, puis cliquez sur **suivant**.  
  
     ![Page de propriétés du Service WCF](../core/media/07518c78-bcae-4274-bb14-aeef107ee4c6.gif "07518c78-bcae-4274-bb14-aeef107ee4c6")  
  
9. Sur le **l’emplacement du Service WCF** page, dans le **emplacement** texte, tapez le nom du répertoire Web où les services WCF sont générés. Vous pouvez accepter l’emplacement par défaut (http://localhost/\<*nom de l’Assembly BizTalk*>), tapez un emplacement pour les services WCF dans le **emplacement** zone de texte, ou cliquez sur **Parcourir**  et sélectionnez un répertoire Web. Sélectionnez une des options suivantes :  
  
    -   **Remplacer le projet existant.** Cette option est disponible uniquement si le répertoire Web existe déjà. Vous pourrez publier dans le même emplacement uniquement si vous sélectionnez cette option. Sinon, vous devez indiquer un emplacement de projet différent.  
  
    -   **Autoriser l’accès anonyme au service WCF.** Cette option permet d'ajouter un accès anonyme au répertoire virtuel créé. Par défaut, celui-ci hérite des privilèges d'accès de son répertoire virtuel parent ou du site Web (s'il s'agit d'un répertoire virtuel de niveau supérieur).  
  
     Lorsque vous avez terminé cette page, cliquez sur **suivant**.  
  
     ![Page emplacement de Service WCF](../core/media/76285470-1520-4d77-a5b6-c58cbe8fc575.gif "76285470-1520-4d77-a5b6-c58cbe8fc575")  
  
    > [!NOTE]
    >  L'emplacement du projet peut se trouver sur un serveur différent. Pour publier les services WCF sur un autre serveur, tapez le nom du projet en tant que http://\<*nom_serveur*>/\<*l’emplacement du service WCF*>.  
  
    > [!NOTE]
    >  L'emplacement du projet peut se trouver sur un site Web personnalisé. Lors de la publication sur un site Web personnalisé, ajoutez le numéro du port du site Web dans l'URL. Par exemple, http://\<*nom_serveur*> : 8080 /\<*l’emplacement du service WCF*>.  
  
    > [!NOTE]
    >  Le fichier BindingInfo.xml créé par l’Assistant dans le dossier App_DataTemp de l’application Web utilise les valeurs par défaut pour les pipelines. La valeur par défaut pour le pipeline de réception est le **Microsoft.BizTalk.DefaultPipelines.XMLReceive** valeur de pipeline et la valeur par défaut pour le pipeline d’envoi est le  **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit** pipeline.  
  
10. Sur le **récapitulatif du Service WCF** page, vérifiez vos paramètres pour les services WCF.  
  
11. Cliquez sur **créer** pour créer les services WCF.  
  
12. Cliquez sur **Terminer** pour terminer l’Assistant de publication des services WCF BizTalk.  
  
### <a name="to-configure-the-web-application-for-publishing-service-metadata"></a>Pour configurer l'application Web à des fins de publication des métadonnées de service  
  
1.  Activez ASP.NET pour l'application Web créée par l'Assistant Publication de services WCF BizTalk. Pour plus d’informations, consultez [activation des Services Web](../core/enabling-web-services.md).  
  
    > [!NOTE]
    >  Si vous utilisez Windows Server 2008 ou Windows Vista, vous devez ajouter le compte d'identité du pool d'applications au groupe Administrateurs de BizTalk Server. Une fois le compte approprié ajouté au groupe Administrateurs de BizTalk Server, vous devez redémarrer le service IIS pour que les paramètres soient pris en compte.  
  
2.  Ouvrez une invite de commandes, accédez au dossier où l’Assistant de publication des services WCF BizTalk a créé les services WCF dans %SystemDrive%\InetPub\\, puis ouvrez le fichier Web.config dans le bloc-notes.  
  
3.  Dans le bloc-notes, ajoutez la ligne suivante à l’intérieur de la  **\<system.web >** élément :  
  
    ```  
    <trust level="Full" originUrl="" />  
    ```  
  
    > [!NOTE]
    >  Ce paramètre est facultatif. Il autorise l'accès de l'application ASP.NET hébergeant le service WCF publié à n'importe quelle ressource exposée à la sécurité du système d'exploitation. Il s'agit du niveau de confiance requis par les services WCF publiés lorsque Windows SharePoint Services est installé et exécuté sur l'ordinateur sur lequel ceux-ci sont hébergés.  
  
4.  Dans Internet Explorer, dans le **adresse** zone, tapez l’URL pour le service WCF au format http://*hôte [ : port]*/*apppath* / *nomservicewcf.svc* pour tester le service WCF publié. Ces paramètres sont décrits dans le tableau suivant.  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |*hôte [ : port]*|Nom de l'ordinateur sur lequel vous avez déployé votre service WCF. Le nom du serveur peut être suivi de deux points et du numéro du port.|  
    |*chemin d’application*|Nom du répertoire virtuel et chemin d'accès à l'application Web|  
    |*nomservicewcf.svc*|Nom du fichier .svc du service WCF.|  
  
5.  Pour empêcher la divulgation involontaire de métadonnées de service potentiellement sensibles, nous vous conseillons de désactiver ce comportement dans l’environnement de production en effectuant les tâches suivantes :  
  
    1.  Dans le bloc-notes, ouvrez le fichier Web.config dans le dossier dans lequel l’Assistant de publication des services WCF BizTalk a créé le service WCF dans %SystemDrive%\InetPub\\.  
  
    2.  Dans le bloc-notes, définissez le le **httpGetEnabled** d’attribut dans le  **\<serviceMetadata >** élément False comme dans la ligne suivante :  
  
        ```  
        <serviceMetadata httpGetEnabled="false" httpsGetEnabled="false" />  
        ```  
  
## <a name="see-also"></a>Voir aussi  
 [Comment utiliser l’Assistant Publication de services WCF BizTalk pour publier des métadonnées de Service pour l’emplacement de réception d’un service WCF pour le routage basé sur le contenu](../core/publish-service-metadata-for-a-wcf-receive-location-for-content-based-routing.md)   
 [Procédure pas à pas : Publication de Services WCF avec l’adaptateur WCF-NetMsmq](../core/walkthrough-publishing-wcf-services-with-the-wcf-netmsmq-adapter.md)