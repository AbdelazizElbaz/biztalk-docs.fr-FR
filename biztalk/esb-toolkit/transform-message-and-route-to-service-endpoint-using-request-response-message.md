---
title: "Comment : transformer un Message et un itinéraire vers un point de terminaison de Service à l’aide d’un modèle d’échange de Message demande-réponse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b1e656fb-6c5f-4b2b-a1b6-4c812b78ee22
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 071227182eb9b5550b23e23463800cc7dd5a22c4
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-transform-a-message-and-route-to-a-service-endpoint-using-a-request-response-message-exchange-pattern"></a>Comment : transformer un Message et un itinéraire vers un point de terminaison de Service à l’aide d’un modèle d’échange de Message demande-réponse
## <a name="goal"></a>Objectif  
 Cette section montre comment utiliser le langage spécifique à un domaine (DSL), ESB concepteur pour créer un itinéraire de requête-réponse qui peut être utilisé avec un bidirectionnelle rampe d’entrée. Vous allez créer un bordereau de routage pour recevoir un message, transformer le message, envoyer le message à un service et renvoyer le message de réponse de service à l’émetteur du message d’origine.  
  
 Dans cette rubrique, vous effectuerez les étapes suivantes :  
  
-   Créer un bordereau d’itinéraire de routage avec un service d’itinéraire de transformation qui implémente un mappage de Microsoft BizTalk Server.  
  
-   Configurer la feuille de route pour acheminer le message transformé à un point de terminaison de service.  
  
-   Configurez l’itinéraire pour renvoyer le message de réponse de service à l’expéditeur d’origine.  
  
-   Test de l’itinéraire à l’aide de l’exemple d’application Client de Test d’itinéraire.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
## <a name="steps"></a>Étapes  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a>Pour créer un modèle DSL de la feuille de route ESB  
  
1.  Dans Visual Studio, ouvrez C:\HowTos\Patterns\Patterns.sln.  
  
2.  Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue le **nom** , tapez **requête-réponse**, puis cliquez sur **ajouter**.  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a>Pour configurer les propriétés de la feuille de route  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de **RequestResponse.itinerary**. Dans le **requête-réponse** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Dans le **réponse à la demande est** la liste déroulante, cliquez sur **True**.  
  
    2.  Dans le **modèle exportateur** la liste déroulante, cliquez sur **XML itinéraire exportateur**.  
  
    3.  Dans le **extendeur paramètres** section à côté du **fichier XML de la feuille de route** propriété, cliquez sur le bouton de sélection (...).  
  
    4.  Dans le **sélectionner un fichier XML** boîte de dialogue le **nom de fichier** , tapez **C:\HowTos\Itineraries\RequestResponse**, puis cliquez sur **enregistrer**.  
  
        > [!NOTE]
        >  Cette étape vous permet d’exporter la feuille de route en tant que XML vers un emplacement de fichier local. En exportant un itinéraire vers un emplacement de fichier local, au lieu de la base de données d’itinéraire, permet de tester de l’itinéraire à l’aide de l’application cliente de Test ESB. Vous pourrez terminer cette procédure plus loin dans cette rubrique.  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>Pour définir la structure de la feuille de route  
  
1.  Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception. Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **rampe d’entrée ESB extendeur**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.  
  
    4.  Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary.Response**.  
  
2.  Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis placez-le à droite de la **rampe d’entrée** élément de modèle. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **MapNAOrderToCNOrder**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.  
  
        > [!NOTE]
        >  Cette propriété définit que le processus a lieu dans un pipeline (messagerie). Ou bien, si le processus a lieu dans une orchestration, définissez la **d’extension du Service itinéraire** propriété **Orchestration extendeur**.  
  
    3.  Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.  
  
    4.  Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Transform**.  
  
3.  Avec le bouton droit le **résolveur** collection de la **MapNAOrderToCNOrder** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**. Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **StaticallySpecifyTheMap**.  
  
    2.  Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.  
  
    3.  Dans le **transformer un Type** la liste déroulante, cliquez sur **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**.  
  
4.  Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **MapNAOrderToCNOrder** élément de modèle.  
  
5.  Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis placez-le à droite de la **MapNAOrderToCNOrder** élément de modèle. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **RouteToCNService**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.  
  
        > [!NOTE]
        >  Cette propriété définit que le processus a lieu dans un pipeline (messagerie). Ou bien, si le processus a lieu dans une orchestration, définissez la **d’extension du Service itinéraire** propriété **Orchestration extendeur**.  
  
    3.  Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.  
  
    4.  Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Routing**.  
  
6.  Avec le bouton droit le **résolveur** collection de la **RouteToCNService** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**. Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **StaticallySpecifyTheService**.  
  
    2.  Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.  
  
    3.  Dans le **nom Transport** la liste déroulante, cliquez sur **WCF-BasicHttp**.  
  
    4.  Cliquez sur le **Transport emplacement** propriété, puis tapez **http://localhost/ESB.CanadianServices/SubmitPOService.asmx**.  
  
    5.  Cliquez sur le **cible Namespace** propriété, puis tapez **http://globalbank.esb.dynamicresolution.com/canadianservices**.  
  
    6.  Cliquez sur le **Action** propriété, puis tapez **submitOrder**.  
  
7.  Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **MapNAOrderToCNOrder** élément de modèle à la **RouteToCNService** élément de modèle.  
  
8.  Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **RouteToCNService** élément de modèle. Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **InvokeCNService**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.  
  
    4.  Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionSolicitResp**.  
  
9. Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **RouteToCNService** élément de modèle et la **InvokeCNService**élément de modèle. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **SendPortFilter**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.  
  
    3.  Dans le **rampe** déroulante liste, développez **InvokeCNService**, puis cliquez sur **gestionnaires d’envoi**.  
  
10. Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **RouteToCNService** élément de modèle à la **SendPortFilter** élément de modèle.  
  
11. Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **SendPortFilter** élément de modèle à la **InvokeCNService** élément de modèle.  
  
12. Cliquez sur l’aire de conception, puis cliquez sur **Validate**.  
  
    > [!NOTE]
    >  L’itinéraire est valide ; Il n’est pas nécessaire de se connecter la rampe à la bande afin d’envoyer le message de réponse au demandeur tiers. En utilisant un bidirectionnelle rampe d’entrée, le message final est automatiquement renvoyé à la partie.  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a>Pour exporter le modèle pour une utilisation avec le Client de Test d’itinéraire  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de la **requête-réponse** itinéraire, puis cliquez sur **exporter le modèle**.  
  
    > [!NOTE]
    >  La version XML de l’itinéraire s’ouvre dans Visual Studio.  
  
2.  Enregistrez tous les artefacts de projet.  
  
3.  Dans l’Explorateur Windows, accédez à C:\HowTos\Itineraries. Notez que la création de votre feuille de route XML (RequestResponse.xml).  
  
#### <a name="to-test-the-itinerary"></a>Pour tester la feuille de route  
  
1.  Ouvrez l’exemple d’application Client de Test d’itinéraire à l’aide du raccourci créé au cours de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB. Itinerary.Test.exe - raccourci).  
  
2.  Dans le Client de Test d’itinéraire, désactivez le **utiliser le Service WCF** case à cocher.  
  
3.  Dans le **Options du Service Web** section, sélectionnez le **deux manière Service** case à cocher, puis cliquez sur **charge itinéraire**.  
  
4.  Dans le **ouvrir le fichier de feuille de route** boîte de dialogue, accédez à C:\HowTos\Itineraries. Sélectionnez **RequestResponse.xml**, puis cliquez sur **ouvrir** pour charger la feuille de route.  
  
5.  Cliquez sur **OK** pour effacer le **itinéraire chargé avec succès** message.  
  
6.  Dans le Client de Test d’itinéraire, cliquez sur le bouton de sélection (...) à côté du **charge Message** boîte.  
  
7.  Dans le **sélectionner le Document XML à charger** boîte de dialogue, accédez à C:\HowTos. Sélectionnez **NAOrderDoc.xml**, puis cliquez sur **ouvrir** pour le message de test de charge.  
  
8.  Cliquez sur le **soumettre la demande** bouton. Une fois le test terminé, cliquez sur **OK** pour faire disparaître la confirmation qui s’affiche.  
  
9. Dans le **résultats** zone, notez le nœud racine du message est **submitOrderResponse** et l’espace de noms par défaut est en cours... **canadianservices**.  
  
    > [!NOTE]
    >  Si le message de réponse nécessite une transformation supplémentaire avant que la réponse est envoyée au demandeur tiers, vous devez utiliser un pipeline qui contient le composant redirecteur d’ESB. Pour obtenir un exemple de cette fonctionnalité, consultez le [installer et exécuter l’exemple de Services Web plusieurs](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md).  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
 Pour plus d'informations, consultez les rubriques connexes suivantes :  
  
-   [Guide pratique pour transformer un message et router le message résultant vers un emplacement de fichier à l’aide d’un bordereau de routage d’itinéraire](../esb-toolkit/transform-message-and-route-the-message-to-a-location-using-itinerary-routing.md)  
  
-   [Activités de développement](../esb-toolkit/development-activities.md)  
  
-   [Modèles de routage des messages](../esb-toolkit/message-routing-patterns.md)  
  
-   [Installation et exécution de l’exemple de services web multiples](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md)