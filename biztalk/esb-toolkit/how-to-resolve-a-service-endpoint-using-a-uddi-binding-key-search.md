---
title: "Comment : résoudre un point de terminaison de Service à l’aide d’une recherche de clé de liaison de UDDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a685641-2beb-4153-a9ba-c766679ce48e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d286f3dd48daa7cc0ddd16f4abda601cf9e8a5f7
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-resolve-a-service-endpoint-using-a-uddi-binding-key-search"></a>Comment : résoudre un point de terminaison de Service à l’aide d’une recherche de clé de liaison de UDDI
## <a name="goal"></a>Objectif  
 Cette section montre comment utiliser le langage spécifique à un domaine (DSL), ESB concepteur pour créer une basée sur un itinéraire de routage qui utilise le Universal Description, Discovery, et résolveur Integration (UDDI) 3 pour localiser un point de terminaison de service à l’aide d’une clé de liaison recherche. Dans ce scénario, le point de terminaison de service sera un point de terminaison de fichiers publié dans UDDI.  
  
 Dans cette rubrique, vous effectuerez les étapes suivantes :  
  
-   Créer un bordereau d’itinéraire de routage pour résoudre un point de terminaison de service.  
  
-   Configurer la feuille de route pour acheminer le message vers un point de terminaison de service à l’aide d’un programme de résolution UDDI 3.  
  
-   Test de l’itinéraire à l’aide de l’exemple d’application Client de Test d’itinéraire.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
## <a name="steps"></a>Étapes  
  
#### <a name="to-create-an-itinerary-model"></a>Pour créer un modèle d’itinéraire  
  
1.  Dans Visual Studio, ouvrez C:\HowTos\Patterns\Patterns.sln.  
  
2.  Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue le **nom** , tapez **UDDI3BindingKeySearch**, puis cliquez sur **ajouter**.  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a>Pour configurer les propriétés de la feuille de route  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de **UDDI3BindingKeySearch.itinerary**. Dans le **UDDI3BindingKeySearch** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Dans le **modèle exportateur** la liste déroulante, cliquez sur **XML itinéraire exportateur**.  
  
    2.  Sous le **extendeur paramètres** section à côté du **fichier XML de la feuille de route** propriété, cliquez sur le bouton de sélection (...).  
  
    3.  Dans le **sélectionner un fichier XML** boîte de dialogue, tapez **C:\HowTos\Itineraries\UDDI3BindingKeySearch** dans les **nom de fichier** zone, puis cliquez sur **enregistrer**.  
  
        > [!NOTE]
        >  Cette étape vous permet d’exporter la feuille de route en tant que XML vers un emplacement de fichier local. En exportant un itinéraire vers un emplacement de fichier local, au lieu de la base de données d’itinéraire, permet de tester de l’itinéraire à l’aide de l’application cliente de Test ESB. Vous pourrez terminer cette procédure plus loin dans cette rubrique.  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>Pour définir la structure de la feuille de route  
  
1.  Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception. Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **rampe d’entrée ESB extendeur**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.  
  
    4.  Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.  
  
2.  Dans la boîte à outils, faites glisser un **itinéraire Service** élément de modèle à l’aire de conception. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **BindingKeyRoute**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.  
  
    3.  Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.  
  
    4.  Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Routing**.  
  
3.  Avec le bouton droit le **résolveur** collection de la **BindingKeyRoute** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**. Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **BindingKeySearch**.  
  
    2.  Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Uddi3 programme de résolution d’Extension**.  
  
    3.  Dans le **Moniker du programme de résolution** la liste déroulante, cliquez sur **UDDI3**.  
  
    4.  Cliquez sur le **clé de liaison** propriété, puis tapez **uddi:esb:orderfileservicev3.1**.  
  
4.  Cliquez sur le **BindingKeySearch** programme de résolution, puis cliquez sur **Configuration du programme de résolution de Test**.  
  
    > [!NOTE]
    >  Vérifiez la sortie affichée dans la fenêtre Sortie.  
  
5.  Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **BindingKeyRoute** élément de modèle.  
  
6.  Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **BindingKeyRoute** élément de modèle. Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **SendNAOrder**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.  
  
    4.  Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.  
  
7.  Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **BindingKeyRoute** élément de modèle et la **SendNAOrder** élément de modèle. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **SendPortFilter**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.  
  
    3.  Dans le **rampe** déroulante liste, développez **SendNAOrder**, puis cliquez sur **gestionnaires d’envoi**.  
  
8.  Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **BindingKeyRoute** élément de modèle à la **SendPortFilter** élément de modèle.  
  
9. Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **SendPortFilter** élément de modèle à la **SendNAOrder** élément de modèle.  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a>Pour exporter le modèle pour une utilisation avec le Client de Test d’itinéraire  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de la **UDDI3BindingKeySearch** itinéraire, puis cliquez sur **exporter le modèle**.  
  
    > [!NOTE]
    >  La version XML de l’itinéraire s’ouvre dans Visual Studio.  
  
2.  Enregistrez tous les artefacts de projet.  
  
3.  Dans l’Explorateur Windows, accédez à C:\HowTos\Itineraries et notez la création de votre feuille de route XML (UDDI3BindingKeySearch.xml).  
  
#### <a name="to-test-the-itinerary"></a>Pour tester la feuille de route  
  
1.  Ouvrez l’exemple d’application Client de Test d’itinéraire à l’aide du raccourci créé au cours de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB. Itinerary.Test.exe - raccourci).  
  
2.  Dans le Client de Test d’itinéraire, désactivez le **utiliser le Service WCF** case à cocher, puis cliquez sur **charge itinéraire**.  
  
3.  Dans la boîte de dialogue Ouvrir un fichier itinéraire, accédez à C:\HowTos\Itineraries. Sélectionnez UDDI3BindingKeySearch.xml, puis cliquez sur Ouvrir pour charger la feuille de route.  
  
4.  Cliquez sur **OK** pour effacer le **itinéraire chargé avec succès** message.  
  
5.  Dans le Client de Test d’itinéraire, cliquez sur le bouton de sélection (...) à côté du **charge Message** boîte.  
  
6.  Dans le **sélectionner le Document XML à charger** boîte de dialogue, accédez à C:\HowTos. Sélectionnez **NAOrderDoc.xml**, puis cliquez sur **ouvrir** pour le message de test de charge.  
  
7.  Cliquez sur le **soumettre la demande** bouton. Une fois le test terminé, cliquez sur **OK** pour faire disparaître la confirmation qui s’affiche.  
  
8.  Dans l’Explorateur Windows, accédez à C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out. Vérifiez que le message %MessageID%.xml a été écrit dans le répertoire.  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
 Pour plus d'informations, consultez les rubriques connexes suivantes :  
  
-   [Guide pratique pour résoudre un point de terminaison de service à l’aide d’une recherche de catégorie UDDI](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-category-search.md)  
  
-   [Activités de développement](../esb-toolkit/development-activities.md)  
  
-   [Utilisation de la résolution et du routage dynamiques](../esb-toolkit/using-dynamic-resolution-and-routing.md)