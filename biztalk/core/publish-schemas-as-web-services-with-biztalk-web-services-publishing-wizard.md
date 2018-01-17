---
title: "Comment utiliser le site Web de BizTalk Services Assistant pour publier des schémas sous la forme d’un Service Web de publication | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Web Services Publishing Wizard, publishing
- BizTalk Web Services Publishing Wizard, schemas
ms.assetid: b22de720-1416-486a-988f-e52527ad9ab1
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba7f93eae8866212546f5daa3b9ed1a5b653c983
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-use-the-biztalk-web-services-publishing-wizard-to-publish-schemas-as-a-web-service"></a>Comment utiliser l’Assistant Publication de Services Web BizTalk pour publier des schémas en tant qu’un Service Web
Vous utilisez l'Assistant Publication de services Web BizTalk pour publier des schémas en tant que services Web.  
  
### <a name="to-publish-schemas-as-a-web-service"></a>Pour publier des schémas en tant que services Web  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Assistant Publication des Services Web BizTalk**.  
  
    > [!IMPORTANT]
    >  Vous devez créer des projets BizTalk avant d'exécuter l'Assistant Publication de services Web BizTalk.  
  
2.  Sur le **Bienvenue** , cliquez sur **suivant**.  
  
3.  Sur le **créer un Service Web** page, sélectionnez **publier des schémas en tant que services web** puis cliquez sur **suivant**.  
  
4.  Sur le **Service Web** page, définissez l’ou les services Web à publier. Vous utilisez l’arborescence dans le **description du service Web** boîte de dialogue pour ajouter, supprimer, renommer et modifier les nœuds de description du service Web. Le **informations** boîte de dialogue fournit des informations sur le nœud sélectionné et affiche toutes les erreurs dans le nœud actuel ou tout sous-nœud :  
  
    -   Le nœud racine de l'arborescence (Description du service Web) décrit le nom de projet de service Web. Le nom du répertoire virtuel utilise le nœud racine comme nom par défaut. Vous pouvez modifier la description du service Web en sélectionnant **renommer la description du service web**.  
  
    -   Pour ajouter un nouveau service Web, cliquez sur le **description du service Web** nœud, puis cliquez sur **ajouter un service web**. Cela crée un service Web sans méthode Web. Pour modifier le nom du service Web, cliquez sur le nœud du service Web, puis sélectionnez **renommer le service web**, puis appuyez sur ENTRÉE pour accepter le nouveau nom.  
  
    -   Pour ajouter une nouvelle méthode Web, cliquez sur le nœud du service Web, pointez sur **ajouter une méthode Web**, puis cliquez sur **unidirectionnel** (pour une requête de méthode Web) ou **demande-réponse** (pour un méthode de requête-réponse Web) dans le menu contextuel.  
  
    -   Pour définir des types de schémas de demande et réponse, cliquez sur le **demande** ou **réponse** nœud, puis cliquez sur **sélectionner le type de schéma**. Dans le **le Type de Message de demande** boîte de dialogue, tapez le nom de l’assembly contenant le schéma de document dans le **fichier d’assembly BizTalk** zone de texte ou cliquez sur **Parcourir** à rechercher pour l’assembly. Le **types de schémas disponibles** liste affiche chaque élément racine du schéma. Sélectionnez un nœud racine à ajouter en tant que type du schéma de requête ou de réponse.  
  
        > [!NOTE]
        >  Si vous avez installé le fichier d’assembly BizTalk dans le Global Assembly Cache (GAC), assurez-vous que l’assembly dans le GAC a été mis à jour avec l’assembly que vous sélectionnez dans la **le Type de Message de demande** boîte de dialogue. Toutefois, si le GAC possède le même nom complet, l'Assistant Publication de services Web BizTalk utilise le fichier de l'assembly du GAC plutôt que celui sélectionné par vos soins.  
  
    -   Vous pouvez renommer la **demande** et **réponse** nœuds sans affecter le code généré. Après avoir défini vos schémas, vous pouvez renommer les éléments part, ce qui modifie le nom du paramètre de la méthode Web. Vous pouvez voir les modifications en affichant le code du service Web généré.  
  
    > [!NOTE]
    >  Vous ne pouvez pas utiliser d'espaces lors du changement de nom d'un nœud de description de service Web.  
  
5.  Cliquez sur **suivant** pour continuer l’Assistant.  
  
6.  Sur le **propriétés du Service Web** page, dans le **espace de noms cible du service web** boîte de dialogue, tapez un espace de noms cible pour le service Web, activez les cases appropriées pour spécifier la façon dont l’Assistant doit en-têtes SOAP de handle et Single Sign-On prend en charge pour le service Web. Si vous souhaitez personnaliser davantage l’implémentation du service Web, cliquez sur **avancé** bouton. Il affiche plus d'options disponibles :  
  
    |Option|Valeur| Description|  
    |------------|-----------|-----------------|  
    |Style de paramètre SOAP|Par défaut|Cette option spécifie la façon dont les paramètres sont formatés dans un message SOAP. Pour plus d’informations, consultez SoapParameterStyle, énumération au [http://go.microsoft.com/fwlink/?LinkId=62259](http://go.microsoft.com/fwlink/?LinkId=62259).|  
    |Style de paramètre SOAP|Bare|Cette option spécifie la façon dont les paramètres sont formatés dans un message SOAP. Pour plus d’informations, consultez SoapParameterStyle, énumération au [http://go.microsoft.com/fwlink/?LinkId=62259](http://go.microsoft.com/fwlink/?LinkId=62259).|  
    |Style de paramètre SOAP|Wrapped|Cette option spécifie la façon dont les paramètres sont formatés dans un message SOAP. Pour plus d’informations, consultez SoapParameterStyle, énumération au [http://go.microsoft.com/fwlink/?LinkId=62259](http://go.microsoft.com/fwlink/?LinkId=62259).|  
    |Demandes de conformité|Aucun|Cette option indique la spécification d'interopérabilité des services Web (WSI) à laquelle les demandes de liaison doivent se conformer. Pour plus d’informations, consultez la propriété WebServiceBindingAttribute.ConformsTo à [http://go.microsoft.com/fwlink/?LinkId=193064](http://go.microsoft.com/fwlink/?LinkId=193064).|  
    |Demandes de conformité|WS-I Basic Profile 1.1|Cette option indique la spécification d'interopérabilité des services Web (WSI) à laquelle les demandes de liaison doivent se conformer. Pour plus d’informations, consultez la propriété WebServiceBindingAttribute.ConformsTo à [http://go.microsoft.com/fwlink/?LinkId=193064](http://go.microsoft.com/fwlink/?LinkId=193064).|  
    |Forcer requête-réponse|[Par défaut]|Cette option indique si des opérations BizTalk unidirectionnelles doivent être exposées en tant que méthodes Web de requête-réponse. La valeur par défaut est de ne pas forcer l'indicateur unidirectionnel.|  
  
    > [!NOTE]
    >  Les options de sélection d'un en-tête SOAP sont appliquées globalement à tous les services Web et méthodes Web créés lors de l'exécution de cette instance de l'Assistant.  
  
7.  Sur le **propriétés du Service Web** , cliquez sur **suivant**.  
  
8.  Si vous avez sélectionné **ajouter des en-têtes SOAP supplémentaires**, le **en-têtes SOAP de requête** et **en-têtes SOAP de réponse** pages s’affichent. Vous pouvez ajouter et supprimer la demande et réponse des en-têtes SOAP à l’aide de la **ajouter** et **supprimer** boutons dans les boîtes de dialogue suivantes :  
  
    -   Pour ajouter un en-tête SOAP, cliquez sur **ajouter**. Dans le **nom de l’assembly BizTalk (\*.dll)** zone de texte, tapez le nom de l’assembly ou recherchez l’assembly contenant le schéma d’en-tête SOAP dans le **fichier d’assembly BizTalk** zone de texte. Le **types de schémas disponibles** liste affiche chaque élément racine du schéma. Sélectionnez un nœud racine à ajouter comme en-tête SOAP de requête ou de réponse. Pour sélectionner plusieurs éléments, maintenez la touche CTRL ENFONCÉE et cliquez sur **OK**.  
  
    -   Pour supprimer un en-tête SOAP de la liste, sélectionnez-le dans la liste des en-têtes SOAP ajoutés, puis cliquez sur **supprimer**.  
  
    -   Cliquez sur **suivant** sur chaque page d’en-tête SOAP pour continuer l’Assistant.  
  
    > [!NOTE]
    >  L'espace de noms cible et le nom de l'élément racine définissent l'en-tête SOAP.  
  
    > [!NOTE]
    >  Si la même combinaison espace de noms cible / nom de l'élément racine est ajoutée en tant qu'en-tête SOAP de requête et de réponse, il ne sera pas traité en tant qu'en-tête d'entrée/sortie. Vous devez copier manuellement l'en-tête entrant dans l'en-tête sortant à l'intérieur d'une orchestration.  
  
    > [!NOTE]
    >  La même combinaison espace de noms cible / nom de l'élément racine ne peut être ajoutée qu'une seule fois en tant qu'en-tête SOAP de requête et qu'une seule fois en tant qu'en-tête SOAP de réponse.  
  
9. Sur le **projet de Service Web** page, dans le **emplacement du projet** texte, tapez l’emplacement du projet. Vous pouvez accepter l’emplacement par défaut (http://localhost/ <*project_name*>), tapez un emplacement pour le projet, ou cliquez sur **Parcourir** et sélectionnez un répertoire Web. Sélectionnez une des options suivantes :  
  
    -   **Remplacer le projet existant.** cette option n'est disponible que si l'emplacement du projet existe déjà. Vous serez uniquement en mesure de publier vers le même emplacement si vous sélectionnez cette option. Sinon, vous devez indiquer un emplacement de projet différent.  
  
    -   **Autoriser l’accès anonyme au service web.** Cette option permet d'ajouter un accès anonyme au répertoire virtuel créé. Par défaut, celui-ci hérite des privilèges d'accès de son répertoire virtuel parent ou du site Web (s'il s'agit d'un répertoire virtuel de niveau supérieur).  
  
    -   **BizTalk de créer des emplacements de réception.** cette option crée automatiquement les ports et emplacements de réception de l'adaptateur SOAP qui correspondent à chaque fichier .asmx généré. Si un autre emplacement de réception existe déjà, l'emplacement de réception n'est pas remplacé. Emplacements de réception de l’adaptateur SOAP sont résolus en utilisant le format « /\<*nom de répertoire virtuel*\>/\<*namespace_typename_portname d’orchestration*  \>.asmx ». Après avoir sélectionné cette option, choisissez l'application où les ports et emplacements de réception sont générés.  
  
        > [!NOTE]
        >  L'emplacement du projet peut se trouver sur un serveur différent. Pour publier un service Web sur un autre serveur, tapez le nom du projet en tant que **http://&lt*nom_serveur*>/<*project_name*>**.  
  
        > [!NOTE]
        >  L'emplacement du projet peut se trouver sur un site Web personnalisé. Lorsque vous publiez sur un site Web de celle par défaut, incluez le numéro de port du site Web dans l’URL : http://localhost : 8080 / <*project_name*>.  
  
        > [!NOTE]
        >  Lors de l'utilisation de l'Assistant pour créer des emplacements de réception, celui-ci crée des emplacements de réception à l'aide de nombreuses valeurs par défaut. Les valeurs par défaut pour les pipelines de réception et d’envoi sont **Microsoft.BizTalk.DefaultPipelines.PassThruReceive** et **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**. Si les messages reçus par le service Web publié requièrent un traitement spécial (par exemple, validation, corrélation ou mappages entrant/sortant), vous devez définir l’envoi et réception de pipelines pour  **Microsoft.BizTalk.DefaultPipelines.XMLReceive**, **Microsoft.BizTalk.DefaultPipelines.XMLSend**, ou à un pipeline personnalisé.  
  
10. Cliquez sur **suivant** pour passer en revue vos paramètres pour le projet de service Web ASP.NET.  
  
11. Cliquez sur **créer** pour créer le service Web ASP.NET.  
  
12. Cliquez sur **Terminer** pour terminer l’Assistant de publication des Services Web BizTalk.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication de schémas en tant que service web](../core/publishing-schemas-as-a-web-service.md)