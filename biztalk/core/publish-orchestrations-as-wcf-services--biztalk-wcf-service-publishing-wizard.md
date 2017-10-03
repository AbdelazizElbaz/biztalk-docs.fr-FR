---
title: "Comment utiliser l’Assistant Publication de services WCF BizTalk pour publier des Orchestrations en tant que Services WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tools, WCF Service Publishing Wizard
- WCF services, WCF Service Publishing Wizard
- WCF services, orchestrations
- publishing, orchestrations [WCF services]
- orchestrations, WCF services
- WCF Service Publishing Wizard
ms.assetid: db352132-2fe8-4d53-b239-45e5c3525b6c
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88c3ce33f413a55fbf756aecfb054e66e5d3599c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-biztalk-wcf-service-publishing-wizard-to-publish-orchestrations-as-wcf-services"></a>Utilisation de l'Assistant Publication de services WCF BizTalk pour publier les orchestrations sous forme de services WCF
Utilisez l'Assistant Publication de services WCF BizTalk pour publier les orchestrations sous forme de services WCF.  
  
> [!NOTE]
>  Vous devez créer vos projets BizTalk avant d'exécuter l'Assistant Publication de services WCF BizTalk. Ceux-ci doivent inclure des orchestrations disposant au moins d'un port de réception dont le modificateur de type est public. Ce modificateur de type existe dans les propriétés de l'orchestration lorsque le port est créé.  
  
### <a name="to-publish-an-orchestration-as-a-wcf-service"></a>Pour publier une orchestration en tant que service WCF  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], puis cliquez sur **Assistant Publication du Service WCF BizTalk**.  
  
    > [!NOTE]
    >  Pour créer et publier des orchestrations et schémas BizTalk en tant que services WCF à l'aide des adaptateurs WCF, vous utilisez l'Assistant Publication de services WCF BizTalk. Pour publier les orchestrations et les schémas en tant que services Web à l'aide de l'adaptateur SOAP, vous utilisez l'Assistant Publication de services Web BizTalk.  
  
2.  Sur le **Bienvenue dans l’Assistant de publication des services WCF BizTalk** , cliquez sur **suivant**.  
  
3.  Sur le **Type de Service WCF** page, sélectionnez **point de terminaison de Service** option pour publier les services WCF sur les orchestrations BizTalk sélectionnées dans un assembly BizTalk.  
  
     ![Page Type de Service WCF](../core/media/959900fd-44c9-4f3a-8836-9786a2f5e707.gif "959900fd-44c9-4f3a-8836-9786a2f5e707")  
  
4.  Sur le **Type de Service WCF** page, sélectionnez **activer le point de terminaison de métadonnées** la case à cocher pour indiquer si WCF isolé et l’emplacement de réception hébergé par Internet Information Services (IIS) publier des métadonnées de service pour la récupération à l’aide d’une requête HTTP/GET. En activant cette case à cocher, l’Assistant génère le fichier Web.config dans lequel le **httpGetEnabled** attribut de la  **\<serviceMetadata >** a la valeur **true**. Vous pouvez utiliser un outil d'importation de métadonnées (tel que SvcUtil.exe) pour générer le code client requis pour appeler ce service dans l'environnement de développement. L’adresse à laquelle les métadonnées sont publiées est l’adresse de point de terminaison plus une **? wsdl** chaîne de requête.  
  
    > [!NOTE]
    >  Pour empêcher toute divulgation non intentionnelle de métadonnées de service potentiellement sensibles, il est recommandé de désactiver ce comportement dans l'environnement de production. Pour ce faire, définissez httpgetenabled sur False ou supprimez le répertoire virtuel MEX.  
  
5.  Sur le **Type de Service WCF** page, dans le **nom de l’adaptateur (type de Transport)** liste déroulante, sélectionnez l’adaptateur WCF isolé avec lequel les services WCF sont publiés. Vous pouvez sélectionner l'un des adaptateurs suivants :  
  
    -   **WCF-BasicHttp.** L'adaptateur WCF-BasicHttp peut communiquer avec les services Web conformes à WS-I Basic Profile 1.1 tels que les services basés sur des fichiers ASMX.  
  
    -   **WCF-WSHttp.** L'adaptateur WCF-WSHttp peut communiquer avec un service grâce aux normes WS-* via HTTP et HTTPS.  
  
    -   **WCF-CustomIsolated.** L'adaptateur WCF-CustomIsolated permet l'utilisation des fonctionnalités d'extensibilité de Windows Communication Foundation (WCF) via le transport HTTP.  
  
6.  Sur le **Type de Service WCF** page, sélectionnez le **BizTalk de créer des emplacements de réception dans l’application suivante** la case à cocher pour créer les ports de réception et les emplacements correspondant à chaque fichier .svc généré pour l’adaptateur WCF que vous avez sélectionné dans le **nom de l’adaptateur** liste déroulante. Si un emplacement de réception existe déjà, il n'est pas remplacé. Après avoir sélectionné cette option, choisissez l’application où les ports de réception et les emplacements sont générés dans le **nom de l’application BizTalk** liste déroulante, puis cliquez sur **suivant**.  
  
7.  Sur le **créer un Service WCF** page, sélectionnez **publier des orchestrations BizTalk en tant que service WCF**, puis cliquez sur **suivant**.  
  
     ![Créer une page de Service WCF](../core/media/86cb66b5-6842-4330-8942-20afa68ec5fa.gif "86cb66b5-6842-4330-8942-20afa68ec5fa")  
  
8.  Sur le **BizTalk Assembly** page, dans le **fichier d’assembly BizTalk (\*.dll)** zone de texte, tapez le nom du fichier d’assembly BizTalk ou cliquez sur **Parcourir** pour accéder à l’assembly contenant l’ou les orchestrations à publier, puis cliquez sur **suivant**.  
  
    > [!NOTE]
    >  Avant de choisir un fichier d’assembly BizTalk, copiez tous les assemblys dépendants dans le même dossier avec l’assembly BizTalk ou installer les assemblys dépendants dans le global assembly cache (GAC).  
  
    > [!NOTE]
    >  Si vous avez installé le fichier d’assembly BizTalk dans le GAC, assurez-vous que l’assembly dans le GAC a été mis à jour avec l’assembly que vous sélectionnez dans la **BizTalk Assembly** boîte de dialogue. Toutefois, si l'assembly du GAC possède le même nom complet, l'Assistant Publication de services WCF BizTalk utilise le fichier de l'assembly du GAC plutôt que celui sélectionné par vos soins.  
  
    > [!NOTE]
    >  Les chemins d'accès de plus de 260 caractères risquent d'entraîner un message d'erreur indiquant que le chemin d'accès est trop long.  
  
     ![Page BizTalk Assembly](../core/media/d34a027e-ea82-4048-8b15-d97df795b0d4.gif "d34a027e-ea82-4048-8b15-d97df795b0d4")  
  
9. Sur le **Orchestrations et Ports** page, développez les nœuds d’arborescence pour chaque assembly et l’orchestration en cliquant sur le signe plus (+). Sélectionner les orchestrations et les ports à publier en sélectionnant les cases à cocher arborescence nœud correspondant. Si vous souhaitez créer un service WCF (fichier .svc) pour tous les ports de réception sélectionnés au lieu d’un service WCF pour chaque port de réception, sélectionnez le **fusionner les ports sélectionnés en un seul service WCF** option, puis cliquez sur  **Suivant**.  
  
    > [!NOTE]
    >  Lorsque vous fusionnez tous les ports sélectionnés en un seul service WCF, ceux-ci disposent du même type de port, mais les noms des opérations demeurent uniques.  
  
     ![Page opérations et Ports](../core/media/97112744-ddd4-4512-ac56-41317ba9412b.gif "97112744-ddd4-4512-ac56-41317ba9412b")  
  
10. Sur le **propriétés du Service WCF** page, dans le **Targetnamespace du service WCF** zone de texte, tapez un espace de noms cible pour les services WCF, puis cliquez sur **suivant**.  
  
     ![Page de propriétés du Service WCF](../core/media/07518c78-bcae-4274-bb14-aeef107ee4c6.gif "07518c78-bcae-4274-bb14-aeef107ee4c6")  
  
11. Sur le **l’emplacement du Service WCF** page, dans le **emplacement** texte, tapez le nom du répertoire Web où les services WCF sont générés. Vous pouvez accepter l’emplacement par défaut (http://localhost/\<*nom de l’Assembly BizTalk*>), tapez un emplacement pour les services WCF dans le **emplacement** zone de texte, ou cliquez sur **Parcourir**  et sélectionnez un répertoire Web. Sélectionnez une des options suivantes :  
  
    -   **Remplacer le projet existant.** cette option est disponible uniquement si le répertoire Web existe déjà. Vous pourrez publier dans le même emplacement uniquement si vous sélectionnez cette option. Sinon, vous devez indiquer un emplacement de projet différent.  
  
    -   **Autoriser l’accès anonyme au service WCF.** Cette option permet d'ajouter un accès anonyme au répertoire virtuel créé. Par défaut, celui-ci hérite des privilèges d'accès de son répertoire virtuel parent ou du site Web (s'il s'agit d'un répertoire virtuel de niveau supérieur).  
  
     Lorsque vous avez terminé cette page, cliquez sur **suivant**.  
  
     ![Page emplacement de Service WCF](../core/media/76285470-1520-4d77-a5b6-c58cbe8fc575.gif "76285470-1520-4d77-a5b6-c58cbe8fc575")  
  
    > [!NOTE]
    >  L'emplacement du projet peut se trouver sur un serveur différent. Pour publier les services WCF sur un autre serveur, tapez le nom du projet en tant que http://\<*nom_serveur*>/\<*l’emplacement du service WCF*>.  
  
    > [!NOTE]
    >  L'emplacement du projet peut se trouver sur un site Web personnalisé. Lors de la publication sur un site Web personnalisé, ajoutez le numéro du port du site Web dans l'URL. Par exemple, http://\<*nom_serveur*> : 8080 /\<*l’emplacement du service WCF*>.  
  
    > [!NOTE]
    >  Quand vous utilisez l'Assistant pour créer des emplacements de réception, il les crée avec les valeurs par défaut. La valeur par défaut pour le pipeline de réception est le **Microsoft.BizTalk.DefaultPipelines.PassThruReceive** pipeline. Si les messages reçus via les services WCF publiés demandent un traitement spécial (par exemple, validation, corrélation/promotion de propriétés ou mappages entrant/sortant), vous devez définir le pipeline de réception sur  **Microsoft.BizTalk.DefaultPipelines.XMLReceive**, ou à un pipeline personnalisé, à l’aide de la console Administration de BizTalk Server.  
  
    > [!NOTE]
    >  Si vous décidez de ne pas utiliser le **publication d’orchestration en tant que service WCF** option une fois que vous atteignez cette page, sur le **créer un Service WCF** page, vous pouvez voir qui le **descriptionduserviceWeb** affiche des noms à partir de l’assembly BizTalk que vous avez sélectionné avant le service et la méthode modifiée de l’option de publication. La description du service Web en mémoire n'est en effet pas supprimée lorsque la méthode de publication est modifiée.  
  
12. Sur le **récapitulatif du Service WCF** page, vérifiez vos paramètres pour les services WCF.  
  
13. Cliquez sur **créer** pour créer les services WCF.  
  
14. Cliquez sur **Terminer** pour terminer l’Assistant de publication des services WCF BizTalk.  
  
15. Après la publication de services WCF avec l'Assistant Publication de services WCF BizTalk, vous devez les configurer correctement. Pour plus d’informations sur la configuration WCF isolé, l’adaptateur de réception, consultez [comment configurer WCF Services publié avec l’Assistant de publication des services WCF BizTalk](../core/configure-wcf-services-published-with-the-biztalk-wcf-service-publishing-wizard.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer des Services WCF publiés à l’Assistant Publication de services WCF BizTalk](../core/configure-wcf-services-published-with-the-biztalk-wcf-service-publishing-wizard.md)   
 [Procédure pas à pas : Publication de Services WCF avec l’adaptateur WCF-BasicHttp](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)   
 [Comment utiliser l’Assistant Publication de services WCF BizTalk pour publier des schémas en tant que Services WCF](../core/publish-schemas-as-wcf-services--use-the-biztalk-wcf-service-publishing-wizard.md)