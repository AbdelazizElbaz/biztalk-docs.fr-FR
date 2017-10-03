---
title: "Comment utiliser l’Assistant Publication de services WCF BizTalk pour publier des métadonnées de Service pour l’emplacement de réception d’un service WCF pour le routage basé sur le contenu | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Service Publishing Wizard, publishing metadata
- WCF services, metadata
ms.assetid: e900b0a0-db17-4db9-a639-54891e02d6d7
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9c46af9724d12609f599c790a7f0a52b2d5d0b5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-biztalk-wcf-service-publishing-wizard-to-publish-service-metadata-for-a-wcf-receive-location-for-content-based-routing"></a>Procédure pour l'utilisation de l'Assistant Publication de services WCF BizTalk pour publier des métadonnées de service pour les emplacements de réception WCF pour le routage basé sur le contenu.
L'Assistant Publication de services WCF BizTalk permet de créer un service WCF à des fins de publication des métadonnées de service pour les emplacements de réception WCF existants pour le routage basé sur le contenu.  
  
> [!NOTE]
>  Vous devez créer vos projets BizTalk avant d'exécuter l'Assistant Publication de services WCF BizTalk. Les projets BizTalk doivent inclure des schémas à des fins de publication en tant que services WCF. Avant de publier les métadonnées de service pour les adaptateurs WCF, vous devez également créer les emplacements de réception WCF à l'aide de la console Administration de BizTalk Server ou de l'outil de ligne de commande BTSTask inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur la création d’un service WCF, emplacement de réception, consultez la rubrique appropriée pour chaque adaptateur WCF dans [adaptateurs WCF](../core/wcf-adapters.md).  
  
### <a name="to-publish-service-metadata-for-an-existing-wcf-receive-location-for-content-based-routing"></a>Publication des métadonnées de service pour un emplacement de réception WCF existant pour le routage basé sur le contenu  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur  **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]** , puis cliquez sur **Assistant Publication du Service WCF BizTalk**.  
  
    > [!NOTE]
    >  Pour créer et publier des métadonnées de service WCF pour les schémas et les orchestrations BizTalk, vous utilisez l’Assistant de publication des services WCF BizTalk. Pour publier les orchestrations et les schémas en tant que services Web à l'aide de l'adaptateur SOAP, vous utilisez l'Assistant Publication de services Web BizTalk.  
  
2.  Sur le **Bienvenue dans l’Assistant de publication des services WCF BizTalk** , cliquez sur **suivant**.  
  
3.  Sur le **Type de Service WCF** page, sélectionnez le **point de terminaison métadonnées uniquement (MEX)** option pour publier les services WCF pour fournir des métadonnées de service pour WCF emplacement de réception que vous sélectionnez dans l’étape suivante.  
  
     ![Page Type de Service WCF](../core/media/794a85b5-6454-4cce-8c15-382b5583b0f2.gif "794a85b5-6454-4cce-8c15-382b5583b0f2")  
  
4.  Sur le **Type de Service WCF** page, dans le **emplacement de réception de publier les métadonnées pour** la liste déroulante, sélectionnez un service WCF emplacement de réception pour publier des métadonnées de service, puis cliquez sur **suivant**.  
  
5.  Sur le **créer un Service WCF** page, sélectionnez **publier des schémas en tant que service WCF**, puis cliquez sur **suivant**.  
  
     ![Créer une page de Service WCF](../core/media/717db27a-2843-4950-899d-0946460f5c1f.gif "717db27a-2843-4950-899d-0946460f5c1f")  
  
6.  Sur le **Service WCF** page, définir les contrats de service WCF pour publier des métadonnées de service. Vous utilisez l’arborescence dans le **description du service Web** boîte de dialogue pour ajouter, supprimer, renommer et modifier les nœuds de description du service Web pour les services WCF à publier. Le **informations** boîte de dialogue fournit des informations sur le nœud sélectionné et affiche toutes les erreurs dans le nœud actuel et les sous-nœuds :  
  
    -   Le nœud racine de l'arborescence (description du service Web) décrit les contrats de service WCF à publier. Le nom du répertoire virtuel utilise le nœud racine comme nom par défaut. Vous pouvez modifier la description du service Web pour les services WCF à publier en sélectionnant **renommer la description du service web**.  
  
         ![Page Service WCF](../core/media/35131a58-dae7-45fe-ac6a-928c8570f27d.gif "35131a58-dae7-45fe-ac6a-928c8570f27d")  
  
    -   Le nœud de méthode Web, **Operation1**, du nœud de service par défaut, **Service1**, affiché par défaut dans le **description du service Web** boîte de dialogue peut être utilisée pour un emplacement de réception requête-réponse. Si vous avez sélectionné un service WCF unidirectionnel emplacement de réception pour ce contrat de service, cliquez sur le nœud de méthode Web par défaut, cliquez sur **supprimer la méthode web**, puis créez une méthode Web unidirectionnelle comme suit : le nœud de service par défaut, point de clic droit pour **ajouter la méthode web**, puis cliquez sur **unidirectionnel**.  
  
    -   Pour ajouter un service WCF, cliquez sur le nom de description du service Web, puis cliquez sur **ajouter un service web**. Ceci crée un service WCF sans aucune opération WCF. Pour modifier le nom du service WCF, cliquez sur le noeud de service WCF, cliquez sur **renommer le service web**, puis appuyez sur ENTRÉE pour accepter le nouveau nom.  
  
    -   Pour ajouter une nouvelle opération WCF, cliquez sur le noeud de service WCF, pointez sur **ajouter une méthode Web**, puis cliquez sur **unidirectionnel** (pour une opération WCF de requête) ou **demande-réponse** (pour un opération de WCF de requête-réponse).  
  
    -   Pour définir des types de schémas de demande et réponse, cliquez sur le **demande** ou **réponse** nœud, puis cliquez sur **sélectionner le type de schéma**. Dans le **le Type de Message de demande** boîte de dialogue, tapez le nom de l’assembly contenant le schéma de document dans le **fichier d’assembly BizTalk** zone de texte ou cliquez sur **Parcourir** à rechercher pour l’assembly. Le **types de schémas disponibles** liste affiche chaque élément racine du schéma. Sélectionnez un nœud racine à ajouter en tant que type du schéma de requête ou de réponse.  
  
        > [!NOTE]
        >  Si vous avez installé le fichier d’assembly BizTalk dans le global assembly cache (GAC), assurez-vous que l’assembly dans le GAC a été mis à jour avec l’assembly que vous sélectionnez dans la **le Type de Message de demande** boîte de dialogue. Si le GAC possède le même nom complet, l'Assistant Publication de services WCF BizTalk utilise le fichier de l'assembly du GAC plutôt que celui que vous avez sélectionné.  
  
         ![Page Type de Message de demande](../core/media/6bb4cc17-b108-4692-a5ca-548c7ef46045.gif "6bb4cc17-b108-4692-a5ca-548c7ef46045")  
  
    -   Vous pouvez renommer la **demande** et **réponse** nœuds sans affecter le code généré. Après avoir défini vos schémas, vous pouvez renommer les éléments, ce qui modifie le nom de paramètre de l'opération WCF. Vous pouvez voir les modifications en visualisant les métadonnées de service pour les services WCF à publier.  
  
    > [!NOTE]
    >  Vous ne pouvez pas utiliser d'espaces lors du changement de nom d'un nœud de description de service Web.  
  
7.  Cliquez sur **suivant** pour continuer l’Assistant.  
  
8.  Sur le **propriétés du Service WCF** page, dans le **Targetnamespace du service WCF** zone de texte, tapez un espace de noms cible pour les services WCF, puis cliquez sur **suivant**.  
  
     ![Page de propriétés du Service WCF](../core/media/07518c78-bcae-4274-bb14-aeef107ee4c6.gif "07518c78-bcae-4274-bb14-aeef107ee4c6")  
  
9. Sur le **l’emplacement du Service WCF** page, dans le **emplacement** texte, tapez le nom du répertoire Web où les services WCF sont générés. Vous pouvez accepter l’emplacement par défaut (http://localhost/\<*description du service Web*>), tapez un emplacement pour les services WCF dans le **emplacement** zone de texte, ou cliquez sur  **Parcourir** et sélectionnez un répertoire Web. Sélectionnez une des options suivantes :  
  
    -   **Remplacer le projet existant.** Cette option est disponible uniquement si le répertoire Web existe déjà. Vous pourrez publier dans le même emplacement uniquement si vous sélectionnez cette option. Sinon, vous devez indiquer un emplacement de projet différent.  
  
    -   **Autoriser l’accès anonyme au service WCF.** Cette option permet d'ajouter un accès anonyme au répertoire virtuel créé. Par défaut, celui-ci hérite des privilèges d'accès de son répertoire virtuel parent ou du site Web (s'il s'agit d'un répertoire virtuel de niveau supérieur).  
  
     Lorsque vous avez terminé cette page, cliquez sur **suivant**.  
  
     ![Page emplacement de Service WCF](../core/media/76285470-1520-4d77-a5b6-c58cbe8fc575.gif "76285470-1520-4d77-a5b6-c58cbe8fc575")  
  
    > [!NOTE]
    >  L'emplacement du projet peut se trouver sur un serveur différent. Pour publier les services WCF sur un autre serveur, tapez le nom du projet en tant que http://\<*nom_serveur*>/\<*l’emplacement du service WCF*>.  
  
    > [!NOTE]
    >  L'emplacement du projet peut se trouver sur un site Web personnalisé. Lors de la publication sur un site Web personnalisé, ajoutez le numéro du port du site Web dans l'URL. Par exemple, http://\<*nom_serveur*> : 8080 /\<*l’emplacement du service WCF*>.  
  
    > [!NOTE]
    >  Le fichier BindingInfo.xml créé par l'Assistant dans le répertoire \App_Data\Temp de l'application Web utilise les valeurs par défaut des pipelines. La valeur par défaut pour le pipeline de réception est le **Microsoft.BizTalk.DefaultPipelines.XMLReceive** valeur de pipeline et la valeur par défaut pour le pipeline d’envoi est le  **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit** pipeline.  
  
10. Sur le **récapitulatif du Service WCF** page, vérifiez vos paramètres pour les services WCF.  
  
11. Cliquez sur **créer** pour créer les services WCF.  
  
12. Cliquez sur **Terminer** pour terminer l’Assistant de publication des services WCF BizTalk.  
  
### <a name="to-configure-the-web-application-for-publishing-service-metadata"></a>Pour configurer l'application Web à des fins de publication des métadonnées de service  
  
1.  Activez ASP.NET pour l'application Web créée par l'Assistant Publication de services WCF BizTalk. Pour plus d’informations, consultez [activation des Services Web](../core/enabling-web-services.md).  
  
    > [!NOTE]
    >  Si vous utilisez une autre version du système d'exploitation Windows, vous devez ajouter le compte d'identité du pool d'applications au groupe Administrateurs de BizTalk Server. Après avoir ajouté le compte approprié pour le groupe d’administrateurs BizTalk Server, vous devez redémarrer le service IIS pour le paramètre prenne effet.  
  
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
  
    2.  Dans le bloc-notes, définissez le le **httpGetEnabled** d’attribut dans le  **\<serviceMetadata >** élément à la valeur false, car la ligne suivante :  
  
        ```  
        <serviceMetadata httpGetEnabled="false" httpsGetEnabled="false" />  
        ```  
  
## <a name="see-also"></a>Voir aussi  
 [Comment utiliser l’Assistant Publication de services WCF BizTalk pour publier des schémas en tant que Services WCF](../core/publish-schemas-as-wcf-services--use-the-biztalk-wcf-service-publishing-wizard.md)   
 [Procédure pas à pas : Publication de Services WCF avec l’adaptateur WCF-NetMsmq](../core/walkthrough-publishing-wcf-services-with-the-wcf-netmsmq-adapter.md)