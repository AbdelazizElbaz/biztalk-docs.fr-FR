---
title: Comment utiliser le site Web de BizTalk Services Assistant pour publier une Orchestration en tant qu’un Service Web de publication | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Web services, publishing
- BizTalk Web Services Publishing Wizard, publishing
- BizTalk Web Services Publishing Wizard
- Web services, orchestrations
- BizTalk Web Services Publishing Wizard, orchestrations
- BizTalk Web Services Publishing Wizard, about BizTalk Web Services Publishing Wizard
- orchestrations, publishing
ms.assetid: d990f8e4-88ce-4718-8a94-63796b8d92dc
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d8c86721091b9a0c9e8436b42a7489e228dbb7e0
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-use-the-biztalk-web-services-publishing-wizard-to-publish-an-orchestration-as-a-web-service"></a>Comment utiliser l’Assistant Publication de Services Web BizTalk pour publier une Orchestration en tant que Service Web
L'Assistant Publication de services Web BizTalk permet de publier une orchestration en tant que service Web.  
  
> [!NOTE]
>  Vous devez créer vos projets BizTalk avant d'exécuter l'Assistant Publication de services Web BizTalk.  
  
> [!NOTE]
>  Vous pouvez utiliser l'utilitaire de ligne de commande BTSWebSvcPub.exe pour publier une orchestration en tant que service Web. Pour plus d’informations, consultez [référence de ligne de commande BTSWebSvcPub](../core/btswebsvcpub-command-line-reference.md).  
  
### <a name="to-publish-an-orchestration-as-a-web-service"></a>Pour publier une orchestration en tant que service Web  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk Server**, puis cliquez sur **Assistant Publication de Services Web BizTalk**.  
  
2.  Sur le **Bienvenue dans l’Assistant de publication des Services Web BizTalk** , cliquez sur **suivant**.  
  
3.  Sur le **créer un Service Web** page, sélectionnez **publier des orchestrations BizTalk en tant que services web**, puis cliquez sur **suivant**.  
  
4.  Sur le **BizTalk Assembly** page, dans le fichier d’assembly BizTalk (\*.dll) zone de texte, tapez le nom du fichier d’assembly BizTalk ou cliquez sur **Parcourir** pour accéder à l’assembly contenant le l’ou les orchestrations à publier, puis cliquez sur **suivant**.  
  
    > [!NOTE]
    >  Avant de sélectionner le fichier de l'assembly BizTalk, copiez tous les assemblys dépendants dans le dossier contenant l'assembly BizTalk ou installez ceux-ci dans le Global Assembly Cache (GAC).  
  
    > [!NOTE]
    >  Si vous avez installé le fichier d’assembly BizTalk dans le GAC, assurez-vous que l’assembly dans le GAC a été mis à jour avec l’assembly que vous sélectionnez dans la **BizTalk Assembly** boîte de dialogue. Toutefois, si le GAC possède le même nom complet, l'Assistant Publication de services Web BizTalk utilise le fichier de l'assembly du GAC plutôt que celui sélectionné par vos soins.  
  
    > [!NOTE]
    >  Si vous ouvrez l'Assistant Publication de services Web BizTalk dans Visual Studio contenant une orchestration, le fichier de l'assembly BizTalk est renseigné avec l'assembly contenant l'orchestration.  
  
    > [!NOTE]
    >  Chemins d’accès plus de 260 caractères peuvent devenir un message d’erreur que le chemin d’accès est trop long.  
  
5.  Sur le **Orchestrations et Ports** page, développez les nœuds d’arborescence pour chaque assembly et l’orchestration en cliquant sur le signe plus. Sélectionnez les ports et orchestrations à publier en activant les cases à cocher correspondantes dans les nœuds de l'arborescence. Si vous souhaitez créer un service Web (.asmx) pour tous les ports de réception sélectionnés au lieu d’un service Web pour chaque port de réception, sélectionnez le **fusionner les ports sélectionnés en un seul service web** option, puis cliquez sur **suivant** .  
  
    > [!NOTE]
    >  Lorsque vous fusionnez tous les ports sélectionnés en un seul service Web, ceux-ci disposent du même type de port, mais les noms des opérations demeurent uniques.  
  
6.  Sur le **propriétés du Service Web** page, dans le **espace de noms cible du service web** , tapez un espace de noms cible pour le service Web, sélectionnez les cases appropriées pour indiquer comment l’Assistant doit gérer SOAP en-têtes et SharePoint Portal Server 2007 unique Sign-On (SSO) prend en charge pour le service Web. Si vous souhaitez personnaliser davantage l’implémentation du service Web, cliquez sur **avancé** bouton. Il affiche plus d'options disponibles :  
  
    |Option|Valeur| Description|  
    |------------|-----------|-----------------|  
    |Style de paramètre SOAP|Par défaut|Cette option spécifie la façon dont les paramètres sont formatés dans un message SOAP. Pour plus d’informations, consultez SoapParameterStyle, énumération au [ http://go.microsoft.com/fwlink/?LinkId=62259 ](http://go.microsoft.com/fwlink/?LinkId=62259).|  
    |Style de paramètre SOAP|Bare|Cette option spécifie la façon dont les paramètres sont formatés dans un message SOAP. Pour plus d’informations, consultez SoapParameterStyle, énumération au [ http://go.microsoft.com/fwlink/?LinkId=62259 ](http://go.microsoft.com/fwlink/?LinkId=62259).|  
    |Style de paramètre SOAP|Wrapped|Cette option spécifie la façon dont les paramètres sont formatés dans un message SOAP. Pour plus d’informations, consultez SoapParameterStyle, énumération au [ http://go.microsoft.com/fwlink/?LinkId=62259 ](http://go.microsoft.com/fwlink/?LinkId=62259).|  
    |Demandes de conformité|Aucun|Cette option indique la spécification d'interopérabilité des services Web (WSI) à laquelle les demandes de liaison doivent se conformer. Pour plus d’informations, consultez la propriété WebServiceBindingAttribute.ConformsTo à [ http://go.microsoft.com/fwlink/?LinkId=193064 ](http://go.microsoft.com/fwlink/?LinkId=193064).|  
    |Demandes de conformité|WS-I Basic Profile 1.1|Cette option indique la spécification d'interopérabilité des services Web (WSI) à laquelle les demandes de liaison doivent se conformer. Pour plus d’informations, consultez la propriété WebServiceBindingAttribute.ConformsTo à [ http://go.microsoft.com/fwlink/?LinkId=193064 ](http://go.microsoft.com/fwlink/?LinkId=193064).|  
    |Forcer requête-réponse|[Par défaut]|Cette option indique si des opérations BizTalk unidirectionnelles doivent être exposées en tant que méthodes Web de requête-réponse. La valeur par défaut est de ne pas forcer l'indicateur unidirectionnel.|  
    |Forcer requête-réponse|non|Cette option indique si des opérations BizTalk unidirectionnelles doivent être exposées en tant que méthodes Web de requête-réponse. La valeur par défaut est de ne pas forcer l'indicateur unidirectionnel.|  
    |Forcer requête-réponse|Oui|Cette option indique si des opérations BizTalk unidirectionnelles doivent être exposées en tant que méthodes Web de requête-réponse. La valeur par défaut est de ne pas forcer l'indicateur unidirectionnel.|  
  
7.  Sur le **propriétés du Service Web** , cliquez sur **suivant**.  
  
    > [!NOTE]
    >  La sélection que des options des en-têtes SOAP sont appliquées globalement à tous les services Web et les méthodes Web qui sont créés lors de l’exécution de cette instance de l’Assistant.  
  
8.  Si vous avez sélectionné **ajouter des en-têtes SOAP supplémentaires** option, le **en-têtes SOAP de requête** et **en-têtes SOAP de réponse** pages s’affichent. Vous pouvez ajouter et supprimer la demande et réponse des en-têtes SOAP à l’aide de la **ajouter** et **supprimer** boutons dans les boîtes de dialogue suivantes :  
  
    -   Pour ajouter un en-tête SOAP, cliquez sur **ajouter**. Dans le **fichier d’assembly BizTalk (\*.dll)** zone de texte, tapez ou recherchez l’assembly contenant le schéma d’en-tête SOAP. Le **types de schémas disponibles** liste affiche chaque élément racine du schéma. Sélectionnez un nœud racine à ajouter comme en-tête SOAP de requête ou de réponse. Pour sélectionner plusieurs éléments, maintenez la touche CTRL ENFONCÉE et cliquez sur **OK**.  
  
    -   Pour supprimer un en-tête SOAP de la liste, sélectionnez-le dans la liste des en-têtes SOAP ajoutés, puis cliquez sur **supprimer**.  
  
    -   Cliquez sur **suivant** sur chaque **en-tête SOAP** page pour continuer l’Assistant.  
  
    > [!NOTE]
    >  Un en-tête SOAP est définit par un espace de noms cible et un nom d'élément racine.  
  
    > [!NOTE]
    >  Si la même combinaison espace de noms cible / nom de l'élément racine est ajoutée en tant qu'en-tête SOAP de requête et de réponse, il ne sera pas traité en tant qu'en-tête d'entrée/sortie. Vous devez copier manuellement l'en-tête entrant dans l'en-tête sortant à l'intérieur d'une orchestration.  
  
    > [!NOTE]
    >  La même combinaison espace de noms cible / nom de l'élément racine ne peut être ajoutée qu'une seule fois en tant qu'en-tête SOAP de requête et qu'une seule fois en tant qu'en-tête SOAP de réponse.  
  
9. Sur le **projet de Service Web** page, dans le **nom du projet** texte, tapez le nom du projet. Vous pouvez accepter l’emplacement par défaut (http://localhost/<*project_name*>), tapez un emplacement pour le projet dans le **emplacement du projet** zone de texte, ou cliquez sur **Parcourir** et Sélectionnez un répertoire Web. Sélectionnez une des options suivantes :  
  
    -   **Remplacer le projet existant.** cette option n'est disponible que si l'emplacement du projet existe déjà. Vous serez uniquement en mesure de publier vers le même emplacement si vous sélectionnez cette option. Sinon, vous devez indiquer un emplacement de projet différent.  
  
    -   **Autoriser l’accès anonyme au service web.** Cette option permet d'ajouter un accès anonyme au répertoire virtuel créé. Par défaut, celui-ci hérite des privilèges d'accès de son répertoire virtuel parent ou du site Web (s'il s'agit d'un répertoire virtuel de niveau supérieur).  
  
    -   **BizTalk de créer des emplacements de réception.** cette option crée automatiquement les ports et emplacements de réception de l'adaptateur SOAP qui correspondent à chaque fichier .asmx généré. Si un emplacement de réception existe déjà, il n'est pas remplacé. Emplacements de réception de l’adaptateur SOAP sont résolus en utilisant le format /\<*nom de répertoire virtuel*\>/\<*namespace_typename_portname d’orchestration*  \>.asmx. Après avoir sélectionné cette option, choisissez l'application où les ports et emplacements de réception sont générés.  
  
        > [!NOTE]
        >  L'emplacement du projet peut se trouver sur un serveur différent. Pour publier un service Web sur un autre serveur, tapez le nom du projet en tant que **http://&lt*nom_serveur*>/<*project_name*>**.  
  
        > [!NOTE]
        >  L'emplacement du projet peut se trouver sur un site Web personnalisé. Lors de la publication sur un site Web personnalisé, ajoutez le numéro du port du site Web dans l'URL. Par exemple, http://localhost:8080/< *project_name*>.  
  
        > [!NOTE]
        >  Quand vous utilisez l'Assistant pour créer des emplacements de réception, il les crée avec les valeurs par défaut. La valeur par défaut pour le pipeline de réception est le **Microsoft.BizTalk.DefaultPipelines.PassThruReceive** pipeline. Si les messages reçus par le service Web publié requièrent un traitement spécial (par exemple, validation, corrélation / promotion de propriétés ou mappages entrant/sortant), vous devez définir le pipeline de réception sur  **Microsoft.BizTalk.DefaultPipelines.XMLReceive**, ou à un pipeline personnalisé.  
  
        > [!NOTE]
        >  Lorsque vous consommez (appelez) des services Web à partir d’une orchestration, l’adaptateur SOAP prend uniquement en charge les pipelines d’envoi direct de style. Vous pouvez utiliser un pipeline d’envoi personnalisé, mais il ne peut pas contenir des composants qui modifie les parties du corps du message. Ces composants incluent l’assembleur XML et les composants de codage.  
  
        > [!NOTE]
        >  Lorsque vous atteignez cette page et si vous choisissez Annuler de choisir **publication de schémas en tant que services web** option, dans le **Services Web** page, vous pouvez voir les **descriptionduserviceWeb** affiche les noms de service et de méthode à partir de l’assembly BizTalk précédemment sélectionné avant de restauration à partir de **publier des orchestrations BizTalk en tant que services web** option. Cela est dû au fait que la description du service Web stockée en mémoire n'est pas effacée lorsque la méthode de publication est modifiée.  
  
10. Cliquez sur **suivant** pour passer en revue vos paramètres pour le projet de service Web ASP.NET.  
  
11. Cliquez sur **créer** pour créer le service Web ASP.NET.  
  
12. Cliquez sur **Terminer** pour terminer l’Assistant de publication des Services Web BizTalk.  
  
> [!NOTE]
>  Si vous souhaitez publier une orchestration en tant que service Web sous Windows Vista, vous devez mettre à jour le répertoire virtuel hébergeant le service. Pour ce faire, exécutez la commande suivante à partir de l’invite de commandes, en remplaçant \<vdir\> avec le nom du répertoire virtuel : **% systemroot%\system32\inetsrv\APPCMD. EXE migrer la configuration « Site Web par défaut /\<nom de répertoire virtuel\>»**.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’une Orchestration en tant que Service Web](../core/publishing-an-orchestration-as-a-web-service.md)   
 [Comment mapper des Orchestrations aux Services Web](../core/how-to-map-orchestrations-to-web-services.md)