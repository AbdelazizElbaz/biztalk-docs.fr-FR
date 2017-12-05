---
title: "Comment : valider un Message à l’aide d’une architecture ESB rampe d’entrée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43dfc791-7cb6-45a4-898f-f53def199c08
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e14fd3f433609da7748197a8b67112d815da153
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-validate-a-message-using-an-esb-on-ramp"></a>Comment : valider un Message à l’aide d’une architecture ESB rampe d’entrée
## <a name="goal"></a>Objectif  
 Cette section montre comment configurer le composant de pipeline de désassemblage de répartiteur ESB pour effectuer une validation de message pour les messages XML soumis à une architecture ESB rampe d’entrée.  
  
 Dans cette rubrique, vous effectuerez les étapes suivantes :  
  
-   Créer un ESB rampe d’entrée qui utilise le **ItinerarySelectReceiveXml** pipeline.  
  
-   Configurer le composant de pipeline de désassemblage de répartiteur ESB pour valider le contenu du message.  
  
-   Configurer le composant de pipeline de sélecteur de feuille de route pour résoudre l’itinéraire approprié.  
  
-   Validation de message de test à l’aide d’un message valide et un message non valide.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Effectuez les tâches suivantes avant d’effectuer les étapes plus loin dans cette rubrique :  
  
-   Créer un message de test non valide.  
  
-   Créer un modèle d’itinéraire langage spécifique à un domaine (DSL) ESB.  
  
-   Configurez les propriétés de l’itinéraire.  
  
-   Définir la structure de l’itinéraire.  
  
-   Exporter le modèle vers la base de données d’itinéraire.  
  
 Les procédures suivantes décrivent comment effectuer chacune d’elles.  
  
#### <a name="to-create-an-invalid-test-message"></a>Pour créer un message de test non valide  
  
1.  Dans l’Explorateur Windows, accédez à C:\HowTos.  
  
2.  Créer une copie de NAOrderDoc.xml et renommez la copie Invalid.xml.  
  
3.  Dans le bloc-notes, ouvrez Invalid.xml.  
  
4.  Modification  **\<ns0:requestType\>10\</ns0:requestType\> à \<ns0:requestType\>dix\</ns0:requestType\>** .  
  
5.  Enregistrer Invalid.xml en UTF-8, puis fermez le bloc-notes.  
  
    > [!NOTE]
    >  En modifiant la valeur numérique de cet élément de texte, le message ne seront plus valide selon le schéma.  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a>Pour créer un modèle DSL de la feuille de route ESB  
  
1.  Dans Visual Studio, ouvrez C:\HowTos\Patterns\Patterns.sln.  
  
2.  Dans l’Explorateur de solutions, cliquez sur **ItineraryLibrary**, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue, tapez **Validation** dans les **nom** zone, puis cliquez sur **ajouter**.  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a>Pour configurer les propriétés de la feuille de route  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de **Validation.itinerary**. Dans le **Validation** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Dans le **modèle exportateur** la liste déroulante, cliquez sur **exportateur de feuille de route de base de données**.  
  
    2.  Cliquez sur le bouton de sélection (...) à côté du **base de données de la feuille de route** propriété.  
  
    3.  Dans le **propriétés de connexion** boîte de dialogue, choisissez le serveur SQL qui héberge la base de données de référentiel d’itinéraire, puis spécifiez le nom de la base de données (le nom par défaut est **EsbItineraryDb**).  
  
2.  Dans le **état de la feuille de route** la liste déroulante, cliquez sur **déployées**.  
  
    > [!NOTE]
    >  Cette étape vous permet d’exporter l’itinéraire sur un référentiel central ; itinéraires peuvent être sélectionnés et attachés à partir de ce référentiel lorsque le message est reçu. Vous configurerez ultérieurement le composant de pipeline de sélecteur de feuille de route pour utiliser un programme de résolution statique pour sélectionner l’itinéraire approprié à partir de ce référentiel.  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>Pour définir la structure de la feuille de route  
  
1.  Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception. Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **rampe d’entrée ESB extendeur**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.  
  
    4.  Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.  
  
2.  Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de l’élément de modèle existant. Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **SendNAOrder**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.  
  
    4.  Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.  
  
3.  Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **ReceiveNAOrder** élément de modèle et la **SendNAOrder** élément de modèle. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **SendPortFilter**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.  
  
    3.  Dans le **rampe** déroulante liste, développez **SendNAOrder**, puis cliquez sur **gestionnaires d’envoi**.  
  
4.  Avec le bouton droit le **résolveur** collection de la **SendPortFilter** élément, puis cliquez sur **ajouter le nouveau programme de résolution**. Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **ConfigureOffRamp**.  
  
    2.  Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.  
  
    3.  Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.  
  
    4.  Cliquez sur le **Transport emplacement** propriété, puis tapez **C:\HowTos\Out\Validated%MessageID%.xml**.  
  
5.  Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **SendPortFilter** élément de modèle.  
  
6.  Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **SendPortFilter** élément de modèle à la **SendNAOrder** élément de modèle.  
  
#### <a name="to-export-the-model-to-the-itinerary-database"></a>Pour exporter le modèle vers la base de données d’itinéraire  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de la **Validation** itinéraire, puis cliquez sur **exporter le modèle**.  
  
    > [!NOTE]
    >  L’itinéraire a été exporté vers la base de données d’itinéraire et peut maintenant être utilisé par le composant de pipeline du sélecteur d’itinéraire.  
  
2.  Enregistrez tous les artefacts de projet.  
  
## <a name="steps"></a>Étapes  
  
#### <a name="to-create-and-configure-an-esb-on-ramp"></a>Pour créer et configurer un ESB rampe d’entrée  
  
1.  Cliquez sur **Démarrer** dans la barre des tâches, pointez sur **tous les programmes**, pointez sur **BizTalk Server**, puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la Console Administration de BizTalk Server, développez **groupe BizTalk**, développez **Applications**, puis développez **Microsoft.Practices.ESB**.  
  
3.  Avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.  
  
4.  Dans le **sélectionner un Port de réception** boîte de dialogue, cliquez sur **OnRamp.Itinerary**, puis cliquez sur **OK**.  
  
5.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue, tapez **OnRamp.Itinerary.HowTo** dans les **nom** boîte.  
  
6.  Dans le **Type** la liste déroulante, cliquez sur **fichier**, puis cliquez sur **configurer**.  
  
7.  Dans le **propriétés du Transport FILE** boîte de dialogue, tapez **C:\HowTos\DropFolder** dans les **dossier de réception** zone, puis cliquez sur **OK**.  
  
#### <a name="to-configure-the-on-ramp-to-perform-message-validation"></a>Pour configurer la rampe d’entrée pour effectuer une validation de message  
  
1.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **pipeline de réception** la liste déroulante, cliquez sur **ItinerarySelectReceiveXml**, puis cliquez sur le bouton de sélection (...) ).  
  
2.  Utilisez le **configurer le Pipeline** boîte de dialogue pour configurer les éléments suivants **désassembleur XML** les propriétés du composant :  
  
    1.  Développez l’application GlobalBank.Esb, puis cliquez sur **schémas**. Avec le bouton droit **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**, puis cliquez sur **propriétés**. Copie le **nom** et **Assembly** propriétés et les coller dans un fichier texte.  
  
    2.  Dans le **désassembler** composant, cliquez sur **True** dans les **ValidateDocument** liste déroulante.  
  
    3.  Cliquez sur le **DocumentSpecNames** propriété, puis tapez le nom qualifié complet du schéma. Le nom qualifié complet commence par le nom et est suivi par une virgule et les informations d’assembly extrait à l’étape un. Par exemple :  
  
         GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc, GlobalBank.ESB.DynamicResolution.Schemas, Version = 2.0.0.0, Culture = neutral, PublicKeyToken = c2c8b2b87f54180a  
  
        > [!NOTE]
        >  Il s’agit du nom qualifié complet du schéma à valider ; Il est composé du nom de schéma et les quatre propriétés de l’assembly : nom de l’assembly, version, culture et jeton de clé publique. Plusieurs valeurs sont autorisées ; Séparez plusieurs schémas avec une barre verticale (&#124;) symbole.  
  
#### <a name="to-configure-the-itinerary-selector-pipeline-component"></a>Pour configurer le composant de Pipeline de sélecteur de feuille de route  
  
1.  Dans le **configurer le Pipeline** boîte de dialogue zone, configurez les éléments suivants **itinéraire sélecteur** les propriétés du composant :  
  
    1.  Cliquez sur le **ItineraryFactKey** propriété, puis tapez **Resolver.Itinerary**.  
  
    2.  Cliquez sur le **ResolverConnectionString** propriété, puis tapez **itinéraire :\\\name=Validation ;**.  
  
    3.  Cliquez sur **OK** pour fermer la **configurer le Pipeline** boîte de dialogue.  
  
2.  Cliquez sur **OK** pour fermer la **propriétés de l’emplacement de réception** boîte de dialogue.  
  
3.  Dans la Console Administration de BizTalk Server, cliquez sur le **OnRamp.Itinerary.HowTo** emplacement de réception, puis cliquez sur **activer**.  
  
#### <a name="to-test-the-message-validation-and-itinerary-selection"></a>Pour tester la sélection de validation et de la feuille de route des messages  
  
1.  Dans l’Explorateur Windows, accédez à C:\HowTos.  
  
2.  Copie (ne déplacez pas) NAOrderDoc.xml dans le dossier Dossier_dépôt.  
  
3.  Accédez à C:\HowTos\Out. Vérifiez que Validated%MessageID%.xml a été écrit dans le répertoire.  
  
    > [!NOTE]
    >  Le message valid terminé son routage basé sur l’itinéraire, comme prévu.  
  
4.  Supprimez Validated%MessageID%.xml dans le dossier de sortie.  
  
5.  Dans l’Explorateur Windows, accédez à C:\HowTos.  
  
6.  Copie (ne déplacez pas) Invalid.xml dans le dossier Dossier_dépôt.  
  
7.  Accédez à C:\HowTos\Out. Vérifiez qu’aucun message n’a été remis.  
  
    > [!NOTE]
    >  Le message n’a pas pu être validé ; Par conséquent, le routage basé sur la feuille de route pas pu être effectué.  
  
8.  Cliquez sur **Démarrer** dans la barre des tâches, pointez sur **outils d’administration**, puis cliquez sur **Observateur d’événements**.  
  
9. Dans l’Observateur d’événements, développez **journaux Windows**, puis cliquez sur **Application**.  
  
10. Recherchez un événement récent où le **Source** est **BizTalk Server**et le **ID d’événement** est **5719**.  
  
    > [!NOTE]
    >  La présentation et l’échec du message non valide a entraîné une entrée d’exception dans le journal des événements.  
  
11. Dans la Console Administration de BizTalk Server, cliquez sur le **OnRamp.Itinerary.HowTo** emplacement de réception, puis cliquez sur **désactiver**.  
  
12. Après le **OnRamp.Itinerary.HowTo** recevoir d’emplacement est désactivée, faites un clic droit, puis cliquez sur **supprimer**. Dans le **emplacement de réception de confirmer la suppression** boîte de dialogue, cliquez sur **Oui**.  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
 Pour plus d'informations, consultez les rubriques connexes suivantes :  
  
-   [Guide pratique pour sélectionner un itinéraire à l’aide d’une stratégie de règles métier](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [Activités de développement](../esb-toolkit/development-activities.md)  
  
-   [Installation et exécution de l’exemple de résolution dynamique](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)