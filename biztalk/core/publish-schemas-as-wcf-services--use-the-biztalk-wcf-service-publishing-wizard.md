---
title: "Comment utiliser l’Assistant Publication de services WCF BizTalk pour publier des schémas en tant que Services WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, WCF services
- tools, WCF Service Publishing Wizard
- publishing, schemas [WCF services]
- WCF services, schemas
- WCF Service Publishing Wizard
ms.assetid: 3b770fd5-5b7b-493f-9016-d7d58854c5ff
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e1acb31455bfcf81ab9d4cb3e983f2614fce1c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-biztalk-wcf-service-publishing-wizard-to-publish-schemas-as-wcf-services"></a>Comment utiliser l'Assistant Publication de services WCF BizTalk pour publier des schémas en tant que services WCF
Vous utilisez l'Assistant Publication de services WCF BizTalk pour publier des schémas en tant que services WCF.  
  
> [!NOTE]
>  Vous devez créer vos projets BizTalk avant d'exécuter l'Assistant Publication de services WCF BizTalk. Les projets BizTalk doivent inclure des schémas à des fins de publication en tant que services WCF.  
  
### <a name="to-publish-schemas-as-wcf-servicees"></a>Pour publier des schémas en tant que services WCF  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Assistant Publication du Service WCF BizTalk**.  
  
    > [!NOTE]
    >  Pour créer et publier des orchestrations et schémas BizTalk en tant que services WCF à l'aide des adaptateurs WCF, vous utilisez l'Assistant Publication de services WCF BizTalk. Pour publier les orchestrations et les schémas en tant que services Web à l'aide de l'adaptateur SOAP, vous utilisez l'Assistant Publication de services Web BizTalk.  
  
2.  Sur le **Bienvenue dans l’Assistant de publication des services WCF BizTalk** , cliquez sur **suivant**.  
  
3.  Sur le **Type de Service WCF** page, sélectionnez le **point de terminaison de Service** option pour publier les services WCF sur les orchestrations BizTalk sélectionnées dans un assembly BizTalk.  
  
     ![Page Type de Service WCF](../core/media/959900fd-44c9-4f3a-8836-9786a2f5e707.gif "959900fd-44c9-4f3a-8836-9786a2f5e707")  
  
4.  Sur le **Type de Service WCF** page, activez ou désactivez le **activer le point de terminaison de métadonnées** case à cocher pour indiquer si WCF isolé et l’emplacement de réception hébergé par Internet Information Services (IIS) publiera métadonnées de service de récupération à l’aide d’une requête HTTP/GET.  
  
     Lorsque cette case à cocher est activée, l’Assistant génère un fichier Web.config dans lequel le **httpGetEnabled** attribut de la  **\<serviceMetadata >** a la valeur **true** . Vous pouvez utiliser un outil d'importation de métadonnées (tel que SvcUtil.exe) pour générer le code client requis pour appeler ce service dans l'environnement de développement. L’adresse à laquelle les métadonnées sont publiées est l’adresse de point de terminaison plus une **? wsdl** chaîne de requête.  
  
    > [!NOTE]
    >  Pour éviter la publication accidentelle de métadonnées de service éventuellement personnelles, nous vous conseillons de désactiver ce comportement dans l'environnement de production. Pour ce faire, définissez httpgetenabled sur False ou supprimez le répertoire virtuel MEX.  
  
5.  Sur le **Type de Service WCF** page, dans le **nom de l’adaptateur (type de Transport)** liste déroulante, sélectionnez l’adaptateur WCF isolé avec lequel les services WCF sont publiés. Vous pouvez sélectionner l'un des adaptateurs suivants :  
  
    -   **WCF-BasicHttp.** L'adaptateur WCF-BasicHttp peut communiquer avec les services Web conformes à WS-I Basic Profile 1.1 tels que les services basés sur des fichiers ASMX.  
  
    -   **WCF-WSHttp.** L'adaptateur WCF-WSHttp peut communiquer avec un service grâce aux normes WS-* via HTTP et HTTPS.  
  
    -   **WCF-CustomIsolated.** L'adaptateur WCF-CustomIsolated permet l'utilisation des fonctionnalités d'extensibilité de Windows Communication Foundation (WCF) via le transport HTTP.  
  
6.  Sur le **Type de Service WCF** page, sélectionnez le **BizTalk de créer des emplacements de réception dans l’application suivante** case à cocher pour créer des emplacements correspondant à chaque fichier .svc généré pour les ports de réception l’adaptateur WCF que vous avez sélectionné dans le **nom de l’adaptateur** liste déroulante. Si un emplacement de réception existe déjà, il n'est pas remplacé. Après avoir sélectionné cette option, choisissez l’application où les ports de réception et les emplacements sont générés dans le **nom de l’application BizTalk** liste déroulante, puis cliquez sur **suivant**.  
  
7.  Sur le **créer un Service WCF** page, sélectionnez **publier des schémas en tant que service WCF**, puis cliquez sur **suivant**.  
  
     ![Créer une page de Service WCF](../core/media/717db27a-2843-4950-899d-0946460f5c1f.gif "717db27a-2843-4950-899d-0946460f5c1f")  
  
8.  Sur le **Service WCF** page, définissez l’ou les services WCF à publier. Utilisez l’arborescence dans le **description du service Web** boîte de dialogue pour ajouter, supprimer, renommer et modifier les nœuds de description du service Web pour les services WCF à publier. Le **informations** boîte de dialogue fournit des informations sur le nœud sélectionné et affiche toutes les erreurs dans le nœud actuel ou les sous-nœuds :  
  
    -   Le nœud racine de l'arborescence (Description du service Web) décrit les services WCF à publier. Le nom du répertoire virtuel utilise le nœud racine comme nom par défaut. Vous pouvez modifier la description du service Web pour les services WCF à publier en sélectionnant **renommer la description du service web**.  
  
         ![Page Service WCF](../core/media/35131a58-dae7-45fe-ac6a-928c8570f27d.gif "35131a58-dae7-45fe-ac6a-928c8570f27d")  
  
    -   Le nœud de méthode Web, **Operation1**, du nœud de service par défaut, **Service1**, affiché par défaut dans le **description du service Web** boîte de dialogue peut être utilisée pour un emplacement de réception requête-réponse. Si vous projetez de publier un service WCF unidirectionnel emplacement de réception pour cette description de service, cliquez sur le nœud de méthode Web par défaut, cliquez sur **supprimer la méthode web**, puis créez une méthode Web unidirectionnelle comme suit : cliquez sur le service par défaut nœud **ajouter la méthode web**, puis cliquez sur **unidirectionnel**.  
  
    -   Pour ajouter un service WCF, cliquez sur le nom de description du service Web, puis cliquez sur **ajouter un service web**. Ceci crée un service WCF sans aucune opération WCF. Pour modifier le nom du service WCF, cliquez sur le noeud de service WCF, cliquez sur **renommer le service web**, puis appuyez sur ENTRÉE pour accepter le nouveau nom.  
  
    -   Pour ajouter une nouvelle opération WCF, cliquez sur le noeud de service WCF, pointez sur **ajouter une méthode Web**, puis cliquez sur **unidirectionnel** (pour une opération WCF de requête) ou **demande-réponse** (pour un opération de WCF de requête-réponse).  
  
    -   Pour définir des types de schémas de demande et réponse, cliquez sur le **demande** ou **réponse** nœud, puis cliquez sur **sélectionner le type de schéma**. Dans le **le Type de Message de demande** boîte de dialogue, tapez le nom de l’assembly contenant le schéma de document dans le **fichier d’assembly BizTalk**zone de texte ou cliquez sur **Parcourir** à rechercher pour l’assembly. Le **types de schémas disponibles** liste affiche chaque élément racine du schéma. Sélectionnez un nœud racine à ajouter en tant que type du schéma de requête ou de réponse.  
  
        > [!NOTE]
        >  Si vous avez installé le fichier d’assembly BizTalk dans le global assembly cache (GAC), assurez-vous que l’assembly dans le GAC a été mis à jour avec l’assembly que vous sélectionnez dans la **le Type de Message de demande** boîte de dialogue. Si le GAC possède le même nom complet, l'Assistant Publication de services WCF BizTalk utilise le fichier de l'assembly du GAC plutôt que celui que vous avez sélectionné.  
  
         ![Page Type de Message de demande](../core/media/6bb4cc17-b108-4692-a5ca-548c7ef46045.gif "6bb4cc17-b108-4692-a5ca-548c7ef46045")  
  
    -   Vous pouvez renommer la **demande** et **réponse** nœuds sans affecter le code généré. Après avoir défini vos schémas, vous pouvez renommer les éléments, ce qui modifie le nom de paramètre de l'opération WCF. Vous pouvez voir les modifications en visualisant les métadonnées de service pour les services WCF à publier.  
  
        > [!NOTE]
        >  Vous ne pouvez pas utiliser d'espaces lors du changement de nom d'un nœud de description de service Web.  
  
9. Cliquez sur **suivant** pour continuer l’Assistant.  
  
10. Sur le **propriétés du Service WCF** page, dans le **Targetnamespace du service WCF** zone de texte, tapez un espace de noms cible pour les services WCF, puis cliquez sur **suivant**.  
  
     ![Page de propriétés du Service WCF](../core/media/07518c78-bcae-4274-bb14-aeef107ee4c6.gif "07518c78-bcae-4274-bb14-aeef107ee4c6")  
  
11. Sur le **l’emplacement du Service WCF** page, dans le **emplacement** texte, tapez le nom du répertoire Web où les services WCF sont générés. Vous pouvez accepter l’emplacement par défaut (http://localhost/\<*description du service Web*>), tapez un emplacement pour les services WCF dans le **emplacement** zone de texte, ou cliquez sur  **Parcourir** et sélectionnez un répertoire Web. Sélectionnez une des options suivantes :  
  
    -   **Remplacer le projet existant.** Cette option est disponible uniquement si le répertoire Web existe déjà. Vous pourrez publier dans le même emplacement uniquement si vous sélectionnez cette option. Sinon, vous devez indiquer un emplacement de projet différent.  
  
    -   **Autoriser l’accès anonyme au service WCF.** Cette option permet d'ajouter un accès anonyme au répertoire virtuel créé. Par défaut, celui-ci hérite des privilèges d'accès de son répertoire virtuel parent ou du site Web (s'il s'agit d'un répertoire virtuel de niveau supérieur).  
  
     Lorsque vous avez terminé cette page, cliquez sur **suivant**.  
  
     ![Page emplacement de Service WCF](../core/media/76285470-1520-4d77-a5b6-c58cbe8fc575.gif "76285470-1520-4d77-a5b6-c58cbe8fc575")  
  
    > [!NOTE]
    >  L'emplacement du projet peut se trouver sur un serveur différent. Pour publier les services WCF sur un autre serveur, tapez le nom du projet en tant que http://\<*nom_serveur*>/\<*l’emplacement du service WCF*>.  
  
    > [!NOTE]
    >  L'emplacement du projet peut se trouver sur un site Web personnalisé. Lors de la publication sur un site Web personnalisé, ajoutez le numéro du port du site Web dans l'URL. Par exemple, http://\<*nom_serveur*> : 8080 /\<*l’emplacement du service WCF*>.  
  
    > [!NOTE]
    >  Quand vous utilisez l'Assistant pour créer des emplacements de réception, il les crée avec les valeurs par défaut. La valeur par défaut pour le pipeline de réception est le **Microsoft.BizTalk.DefaultPipelines.PassThruReceive** pipeline. Si les messages reçus via les services WCF publiés demandent un traitement spécial (par exemple, validation, corrélation/promotion de propriétés ou mappages entrant/sortant), vous devez définir le pipeline de réception sur  **Microsoft.BizTalk.DefaultPipelines.XMLReceive**, ou à un pipeline personnalisé à l’aide de la console Administration de BizTalk.  
  
12. Sur le **récapitulatif du Service WCF** page, vérifiez vos paramètres pour les services WCF.  
  
13. Cliquez sur **créer** pour créer les services WCF.  
  
14. Cliquez sur **Terminer** pour terminer l’Assistant de publication des services WCF BizTalk.  
  
15. Après la publication de services WCF avec l'Assistant Publication de services WCF BizTalk, vous devez les configurer correctement. Pour plus d’informations sur la configuration WCF isolé, l’adaptateur de réception, consultez [comment configurer WCF Services publié avec l’Assistant de publication des services WCF BizTalk](../core/configure-wcf-services-published-with-the-biztalk-wcf-service-publishing-wizard.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer des Services WCF publiés à l’Assistant Publication de services WCF BizTalk](../core/configure-wcf-services-published-with-the-biztalk-wcf-service-publishing-wizard.md)   
 [Procédure pas à pas : Publication de Services WCF avec l’adaptateur WCF-BasicHttp](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)   
 [Comment utiliser l’Assistant Publication de services WCF BizTalk pour publier des Orchestrations en tant que Services WCF](../core/publish-orchestrations-as-wcf-services--biztalk-wcf-service-publishing-wizard.md)