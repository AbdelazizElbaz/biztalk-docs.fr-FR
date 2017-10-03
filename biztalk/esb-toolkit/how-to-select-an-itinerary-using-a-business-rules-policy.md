---
title: "Comment : sélectionner un itinéraire à l’aide d’une stratégie de règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f6373a8-d9d6-46c6-95e3-f62dd33c342a
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d06bdea233c88fb740c728a414472d01a8fdc34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-select-an-itinerary-using-a-business-rules-policy"></a>Comment : sélectionner un itinéraire à l’aide d’une stratégie de règles d’entreprise
## <a name="goal"></a>Objectif  
 Cette section montre comment créer des règles d’entreprise qui peuvent être utilisés pour sélectionner un itinéraire en fonction du contenu d’un message reçu et comment configurer le composant de pipeline de sélecteur de feuille de route au sein d’un générique d’itinéraire rampe d’entrée à appeler ces règles. Cette section décrit un scénario d’entreprise dans laquelle messages sont routés différemment, selon la région dans lequel réside le client.  
  
 Dans cette rubrique, vous effectuerez les étapes suivantes :  
  
-   Itinéraires de modèle pour les divisions de l’ouest et orientale de client Global Bank.  
  
-   Créer des stratégies de règles d’entreprise qui permet de sélectionner une feuille de route pour le traitement de la demande.  
  
-   Configurer le composant de pipeline de sélecteur de feuille de route pour utiliser une stratégie de règles d’entreprise pour sélectionner la feuille de route approprié.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Effectuez les tâches suivantes avant d’effectuer les étapes plus loin dans cette rubrique :  
  
-   Créer le message de test GlobalBank West.  
  
-   Créer le message de test est de GlobalBank.  
  
 Les procédures suivantes décrivent comment effectuer chacune d’elles.  
  
#### <a name="to-create-the-globalbank-west-test-message"></a>Pour créer le message de test GlobalBank West  
  
1.  Dans l’Explorateur Windows, accédez à C:\HowTos.  
  
2.  Créer une copie de NAOrderDoc.xml et nommez la copie West.xml.  
  
3.  Dans le bloc-notes, ouvrez West.xml et modifiez la valeur de la **customerName** élément **GlobalBankWest**.  
  
4.  Enregistrer West.xml en UTF-8, puis fermez le bloc-notes.  
  
#### <a name="to-create-the-globalbank-east-test-message"></a>Pour créer le message de test est de GlobalBank  
  
1.  Dans l’Explorateur Windows, accédez à C:\HowTos.  
  
2.  Créer une copie de NAOrderDoc.xml et nommez la copie East.xml.  
  
3.  Dans le bloc-notes, ouvrez East.xml et modifiez la valeur de la **customerName** élément **GlobalBankEast**.  
  
4.  Enregistrer East.xml en UTF-8, puis fermez le bloc-notes.  
  
## <a name="steps"></a>Étapes  
  
#### <a name="to-create-a-business-rules-engine-bre-policy-to-select-an-itinerary-using-custom-message-properties"></a>Pour créer une stratégie du moteur de règles d’entreprise (BRE) pour sélectionner un itinéraire à l’aide des propriétés de message personnalisées  
  
1.  Cliquez sur **Démarrer** dans la barre des tâches, pointez sur **tous les programmes**, pointez sur  **[!INCLUDE[prague](../includes/prague-md.md)]** , puis cliquez sur **Éditeur des règles d’entreprise**.  
  
2.  Dans l’Explorateur de stratégies, cliquez sur **stratégies**, puis cliquez sur **ajouter une nouvelle stratégie**. Nom de la stratégie **ResolveItineraryBasedOnCustomer**.  
  
    > [!NOTE]
    >  Cette rubrique utilise la même stratégie de règles d’entreprise et les itinéraires comme ceux créés dans la rubrique [Comment : fractionner un échange et de router les Messages résultant vers plusieurs fichiers emplacements à l’aide de Distinct itinéraires](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md). Si vous avez déjà effectué cette section, vous pouvez ignorer la procédure, « pour créer et configurer un ESB rampe d’entrée » plus loin dans cette rubrique.  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-west"></a>Pour ajouter une règle de sélection pour le client GlobalBank West  
  
1.  Dans le **ResolveItineraryBasedOnCustomer** stratégie, avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **ajouter une nouvelle règle**. Nommez la règle **SetGlobalBankWestItinerary**.  
  
2.  Dans l’Explorateur de faits, cliquez sur le **schémas XML** droit **schémas**, puis cliquez sur **Parcourir**.  
  
3.  Dans le **les fichiers de schéma** boîte de dialogue, accédez à C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB. DynamicResolution.Schemas, sélectionnez **NAOrderDoc.xsd**, puis cliquez sur **ouvrir**.  
  
    > [!NOTE]
    >  Voici le schéma qui définit le message NAOrderDoc.xml, qui a été utilisé pour créer les messages ouest / est que vous allez utiliser pour le test.  
  
4.  Dans l’Explorateur de faits, cliquez sur **NAOrderDoc.xsd**, cliquez sur le **Type de Document** propriété dans le volet Propriétés, puis tapez **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.  
  
    > [!NOTE]
    >  Il s’agit du nom qualifié complet du schéma.  
  
5.  Dans l’Explorateur de faits, développez **NAOrderDoc.xsd**, puis développez **OrderDoc**.  
  
6.  Dans la fenêtre de la règle, cliquez sur **Conditions**, pointez sur **prédicats**, puis cliquez sur **égal**.  
  
7.  Dans l’Explorateur de faits, faites glisser le **customerName** élément à la **argument1** nœud sous **Conditions**.  
  
8.  Cliquez sur le **argument2** nœud, puis tapez **GlobalBankWest**.  
  
9. Dans l’Explorateur de faits, cliquez sur le **vocabulaires** onglet. Développez le **ESB. Feuille de route** vocabulaire, développez **Version 1.1**, puis faites glisser le **définir un nom de feuille de route** définition **Actions**.  
  
10. Cliquez sur  **\<une chaîne vide >**, puis tapez **GlobalBankWestItinerary**.  
  
    > [!NOTE]
    >  Plus loin dans cette rubrique, vous allez créer cette feuille de route pour traiter les messages de GlobalBank West.  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-east"></a>Pour ajouter une règle de sélection pour le client GlobalBank est  
  
1.  Dans l’Explorateur de stratégies, cliquez sur le **SetGlobalBankWestItinerary** de règle, puis cliquez sur **copie**.  
  
2.  Avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **coller**.  
  
3.  Dans le **nom de la nouvelle règle** boîte de dialogue, tapez **SetGlobalBankEastItinerary**, puis cliquez sur **OK**.  
  
4.  Dans l’Explorateur de stratégies, cliquez sur le **SetGlobalBankEastItinerary** règle.  
  
5.  Dans le **Conditions** section, cliquez sur **GlobalBankWest**, puis cliquez sur **réinitialiser l’argument**.  
  
6.  Cliquez sur **argument2**, puis tapez **GlobalBankEast**.  
  
7.  Dans le **Actions** section, cliquez sur **GlobalBankWestItinerary**, puis cliquez sur **réinitialiser l’argument**.  
  
8.  Cliquez sur  **\<une chaîne vide >** , puis tapez **GlobalBankEastItinerary**.  
  
    > [!NOTE]
    >  Plus loin dans la rubrique de procédure, vous allez créer cette feuille de route pour traiter les messages à partir de GlobalBank est.  
  
#### <a name="to-publish-and-deploy-the-policy"></a>Pour publier et déployer la stratégie  
  
1.  Dans l’Explorateur de stratégies, sous la **ResolveItineraryBasedOnCustomer** stratégie, le bouton droit sur **Version 1.0 (non enregistrée)**, puis cliquez sur **publier**.  
  
2.  Dans l’Explorateur de stratégies, sous la **ResolveItineraryBasedOnCustomer** stratégie, le bouton droit sur **Version 1.0 - publiée**, puis cliquez sur **déployer**.  
  
#### <a name="to-create-an-esb-itinerary-domain-specific-language-dsl-model-for-globalbank-west-messages"></a>Pour créer un modèle d’itinéraire langage spécifique à un domaine (DSL) ESB pour les messages GlobalBank West  
  
1.  Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez C:\HowTos\Patterns\Patterns.sln.  
  
2.  Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue, dans le volet Modèles, cliquez sur **ItineraryDsl**.  
  
4.  Dans le **nom** , tapez **GlobalBankWestItinerary**, puis cliquez sur **ajouter**.  
  
#### <a name="to-configure-the-properties-of-the-globalbank-west-itinerary"></a>Pour configurer les propriétés de l’itinéraire GlobalBank West  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de **GlobalBankWestItinerary.itinerary**. Dans le **GlobalBankWestItinerary** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Dans le **modèle exportateur** la liste déroulante, cliquez sur **exportateur de feuille de route de base de données**.  
  
    2.  Cliquez sur le bouton de sélection (...) à côté du **base de données de la feuille de route** propriété.  
  
    3.  Dans le **propriétés de connexion** boîte de dialogue, choisissez le serveur SQL qui héberge la base de données de référentiel d’itinéraire, puis spécifiez le nom de la base de données (le nom par défaut est **EsbItineraryDb**).  
  
2.  Dans le **état de la feuille de route** la liste déroulante, cliquez sur **déployées**.  
  
    > [!NOTE]
    >  Cette étape vous permet d’exporter l’itinéraire sur un référentiel central ; itinéraires peuvent être sélectionnés et attachés à partir de ce référentiel lors de la réception du message. Vous configurerez ultérieurement le composant de pipeline de sélecteur de feuille de route pour utiliser le programme de résolution du moteur des règles d’entreprise (BRI) à évaluer les messages entrants, puis sélectionnez la feuille de route approprié à partir de ce référentiel.  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>Pour définir la structure de la feuille de route  
  
1.  Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception. Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **Extension du Service ESB rampe d’entrée**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.  
  
    4.  Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.  
  
2.  Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **ReceiveNAOrder** élément de modèle. Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **SendNAOrder**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB Service Extension**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.  
  
    4.  Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.  
  
3.  Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **ReceiveNAOrder** élément de modèle et la **SendNAOrder** élément de modèle. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **RouteMessage**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe itinéraire Service Extension**.  
  
    3.  Dans le **rampe** déroulante liste, développez **SendNAOrder**, puis cliquez sur **gestionnaires d’envoi**.  
  
4.  Avec le bouton droit le **résolveur** collection de la **RouteMessage** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**. Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **StaticResolver**.  
  
    2.  Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.  
  
    3.  Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.  
  
    4.  Cliquez sur le **Transport emplacement** propriété, puis tapez **C:\HowTos\Out\West%MessageID%.xml**.  
  
5.  Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **RouteMessage** élément de modèle.  
  
6.  Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **RouteMessage** élément de modèle à la **SendNAOrder** élément de modèle.  
  
#### <a name="to-export-the-model-to-the-itinerary-database"></a>Pour exporter le modèle vers la base de données d’itinéraire  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de la **GlobalBankWestItinerary** itinéraire, puis cliquez sur **exporter le modèle**.  
  
    > [!NOTE]
    >  L’itinéraire a été exporté vers la base de données d’itinéraire et peut maintenant être utilisé par le composant de sélecteur d’itinéraire.  
  
2.  Enregistrez tous les artefacts de projet.  
  
#### <a name="to-create-an-esb-itinerary-dsl-model-for-globalbank-east-message"></a>Pour créer un modèle DSL ESB d’itinéraire pour le message de GlobalBank est  
  
1.  Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez C:\HowTos\Patterns.sln.  
  
2.  Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue, dans le volet Modèles, cliquez sur **ItineraryDsl**.  
  
4.  Dans le **nom** , tapez **GlobalBankEastItinerary**, puis cliquez sur **ajouter**.  
  
#### <a name="to-configure-the-properties-of-the-globalbank-east-itinerary"></a>Pour configurer les propriétés de l’itinéraire GlobalBank est  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de **GlobalBankEastItinerary.itinerary**. Dans le **GlobalBankEastItinerary** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Dans le **modèle exportateur** la liste déroulante, cliquez sur **exportateur de feuille de route de base de données**.  
  
    2.  Cliquez sur le bouton de sélection (...) à côté du **base de données de la feuille de route** propriété.  
  
    3.  Dans le **propriétés de connexion** boîte de dialogue, choisissez le serveur SQL qui héberge la base de données de référentiel d’itinéraire, puis spécifiez le nom de la base de données (le nom par défaut est **EsbItineraryDb**).  
  
2.  Dans le **état de la feuille de route** la liste déroulante, cliquez sur **déployées**.  
  
    > [!NOTE]
    >  Cette étape vous permet d’exporter l’itinéraire sur un référentiel central ; itinéraires peuvent être sélectionnés et attachés à partir de ce référentiel lorsque les messages sont reçus. Vous configurerez ultérieurement le composant de pipeline de sélecteur de feuille de route pour utiliser le programme de résolution BRI à évaluer les messages entrants, puis sélectionnez la feuille de route approprié à partir de ce référentiel.  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>Pour définir la structure de la feuille de route  
  
1.  Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception. Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **Extension du Service ESB rampe d’entrée**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.  
  
    4.  Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.  
  
2.  Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **ReceiveNAOrder** élément de modèle. Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **SendNAOrder**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB Service Extension**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.  
  
    4.  Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.  
  
3.  Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **ReceiveNAOrder** élément de modèle et la **SendNAOrder** élément de modèle. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **RouteMessage**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe itinéraire Service Extension**.  
  
    3.  Dans le **rampe** déroulante liste, développez **SendNAOrder**, puis cliquez sur **gestionnaires d’envoi**.  
  
4.  Avec le bouton droit le **résolveur** collection de la **RouteMessage** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**. Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **StaticResolver**.  
  
    2.  Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.  
  
    3.  Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.  
  
    4.  Cliquez sur le **Transport emplacement** propriété, puis tapez **C:\HowTos\Out\East%MessageID%.xml**.  
  
5.  Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **RouteMessage** élément de modèle.  
  
6.  Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **RouteMessage** élément de modèle à la **SendNAOrder** élément de modèle.  
  
#### <a name="to-export-the-model-to-the-itinerary-database"></a>Pour exporter le modèle vers la base de données d’itinéraire  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de la **GlobalBankEastItinerary** itinéraire, puis cliquez sur **exporter le modèle**.  
  
    > [!NOTE]
    >  L’itinéraire a été exporté vers la base de données d’itinéraire et peut maintenant être utilisé par le composant de sélecteur d’itinéraire.  
  
2.  Enregistrez tous les artefacts de projet.  
  
#### <a name="to-create-and-configure-an-esb-on-ramp"></a>Pour créer et configurer un ESB rampe d’entrée  
  
1.  Cliquez sur **Démarrer** dans la barre des tâches, pointez sur **tous les programmes**, pointez sur  **[!INCLUDE[prague](../includes/prague-md.md)]** , puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans le [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration, développez **groupe BizTalk**, développez **Applications**, puis développez **Microsoft.Practices.ESB**.  
  
3.  Avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.  
  
4.  Dans le **sélectionner un Port de réception** boîte de dialogue, cliquez sur **OnRamp.Itinerary**, puis cliquez sur **OK**.  
  
5.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , tapez **OnRamp.Itinerary.HowTo**.  
  
6.  Dans le **Type** la liste déroulante, cliquez sur **fichier**, puis cliquez sur **configurer**.  
  
7.  Dans le **propriétés du Transport FILE** boîte de dialogue le **dossier de réception** , tapez **C:\HowTos\DropFolder**, puis cliquez sur **OK**.  
  
#### <a name="to-configure-the-itinerary-selector-pipeline-component"></a>Pour configurer le composant de pipeline du sélecteur de feuille de route  
  
1.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **pipeline de réception** la liste déroulante, cliquez sur **ItinerarySelectReceiveXml**, puis cliquez sur le bouton de sélection (...) ).  
  
2.  Utilisez le **configurer le Pipeline** boîte de dialogue pour configurer les éléments suivants **itinéraire sélecteur** les propriétés du composant :  
  
    1.  Cliquez sur le **ItineraryFactKey** propriété, puis tapez **Resolver.Itinerary**.  
  
    2.  Cliquez sur le **ResolverConnectionString** propriété, puis tapez **BRI :\\\policy=ResolveItineraryBasedOnCustomer;useMsg=true;recognizeMessageFormat=true ;**  
  
    3.  Cliquez sur **OK** pour fermer la **configurer le Pipeline** boîte de dialogue.  
  
3.  Cliquez sur **OK** pour fermer la **propriétés de l’emplacement de réception** boîte de dialogue.  
  
4.  Dans le [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration, avec le bouton droit le **OnRamp.Itinerary.HowTo** emplacement de réception, puis cliquez sur **activer**.  
  
#### <a name="to-test-the-itinerary-selector-and-business-rules"></a>Pour tester le sélecteur d’itinéraire et les règles d’entreprise  
  
1.  Dans l’Explorateur Windows, accédez à C:\HowTos.  
  
2.  Copie (ne déplacez pas) les fichiers East.xml et West.xml dans le dossier Dossier_dépôt.  
  
3.  Accédez à C:\HowTos\Out. Vérifiez que les messages East%MessageID%.xml et West%MessageID%.xml ont été écrits dans le répertoire.  
  
    > [!NOTE]
    >  Si elle est identique à l’exception de la valeur de l’élément client, les messages ont été traités à l’aide d’itinéraires différents, selon la résolution du composant de pipeline sélecteur d’itinéraire.  
  
4.  Dans le [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration, avec le bouton droit le **OnRamp.Itinerary.HowTo** emplacement de réception, puis cliquez sur **désactiver**.  
  
5.  Après le **OnRamp.Itinerary.HowTo** recevoir d’emplacement est désactivée, faites un clic droit, puis cliquez sur **supprimer**. Dans le **emplacement de réception de confirmer la suppression** boîte de dialogue, cliquez sur **Oui**.  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
 Pour plus d'informations, consultez les rubriques connexes suivantes :  
  
-   [Comment : fractionner un échange et de router les Messages résultants vers plusieurs emplacements de fichier à l’aide d’itinéraires distinctes](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md)  
  
-   [Activités de développement](../esb-toolkit/development-activities.md)  
  
-   [Installer et exécuter l’exemple de résolution dynamique](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)  
  
-   [À l’aide de la résolution dynamique et le routage](../esb-toolkit/using-dynamic-resolution-and-routing.md)  
  
-   [Modèles de routage de messages](../esb-toolkit/message-routing-patterns.md)