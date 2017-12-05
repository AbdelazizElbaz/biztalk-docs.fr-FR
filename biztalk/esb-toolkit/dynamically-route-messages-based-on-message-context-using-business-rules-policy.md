---
title: "Comment : acheminer un Message basé sur le contexte du Message à l’aide d’une stratégie de règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d3b68de-6b24-46fe-ae0d-91afb630bc19
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e0d36df10b271d83b1e77f4d7f57d357f4b22033
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-dynamically-route-a-message-based-on-message-context-using-a-business-rules-policy"></a>Comment : acheminer un Message basé sur le contexte du Message à l’aide d’une stratégie de règles d’entreprise
## <a name="goal"></a>Objectif  
 Cette section montre comment créer un itinéraire qui détermine les points de terminaison de message, selon les propriétés de contexte du message, à l’aide d’une stratégie du moteur de règles entreprise (BRE) de BizTalk Server, puis achemine le message à l’aide de l’adaptateur FILE BizTalk Server.  
  
 Dans cette rubrique, vous effectuerez les étapes suivantes :  
  
-   Créer une stratégie de règles d’entreprise pour évaluer le type de message.  
  
-   Créer un bordereau d’itinéraire de routage pour acheminer dynamiquement à l’aide d’une stratégie de règles d’entreprise.  
  
-   Test de l’itinéraire à l’aide de l’exemple d’application Client de Test d’itinéraire.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
## <a name="steps"></a>Étapes  
 **Pour créer une stratégie BRE pour router un message à l’aide des propriétés de contexte de message**  
  
1.  Cliquez sur **Démarrer** dans la barre des tâches, pointez sur **tous les programmes**, pointez sur **BizTalk Server**, puis cliquez sur **Éditeur des règles d’entreprise**.  
  
2.  Dans l’Explorateur de stratégies, cliquez sur **stratégies**, puis cliquez sur **ajouter une nouvelle stratégie**. Nom de la stratégie **RouteBasedOnMessageType**.  
  
 **Pour ajouter une règle de routage pour les commandes Amérique du Nord**  
  
1.  Dans le **RouteBasedOnMessageType** stratégie, avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **ajouter une nouvelle règle**. Nommez la règle **SetNAOrderEndpoint**.  
  
2.  Dans la fenêtre de la règle, cliquez sur **Conditions**, pointez sur **prédicats**, puis cliquez sur **égal**.  
  
3.  Dans l’Explorateur de faits, développez le **ESB. ContextInfo** vocabulaire, développez **Version 1.0**, puis faites glisser le **Type de contexte de Message** fait à la **argument1** nœud sous  **Conditions**.  
  
    > [!NOTE]
    >  La [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] inclut plusieurs vocabulaires qui peuvent être utilisés pour créer des règles. Certains d'entre eux doivent être remplacé ou augmentée avec vos propres vocabulaires. Par exemple, le **DynamicRunTimeMaptypes** stratégie contient des définitions pour les cartes fournies dans le **GlobalBank** exemples.  
  
4.  Cliquez sur le **argument2** nœud, puis tapez **http://globalbank.esb.dynamicresolution.com/northamericanservices/#OrderDoc**  
  
5.  Dans l’Explorateur de faits, développez le **ESB. EndPointInfo** vocabulaire, développez **Version 1.0**, puis faites glisser le **définir l’emplacement du Transport Point de terminaison sortants** définition **Actions**.  
  
6.  Cliquez sur  **\<une chaîne vide\>**, puis tapez **C:\HowTos\Out\NorthAmerica%MessageID%.xml**  
  
7.  Dans l’Explorateur de faits, faites glisser le **définir le Type de Transport Point de terminaison sortants** définition **Actions**.  
  
8.  Dans l’Explorateur de faits, développez le **ESB. TansportTypes** vocabulaire, développez **Version 1.0**, puis faites glisser le **adaptateur fournisseurs** définition  **\<une chaîne vide\>** .  
  
9. Dans le volet Actions, développez le **adaptateur fournisseurs** liste déroulante, puis cliquez sur **fichier**.  
  
 **Pour publier et déployer la stratégie**  
  
1.  Dans l’Explorateur de stratégies, sous la **RouteBasedOnMessageType** stratégie, le bouton droit sur **Version 1.0 (non enregistrée)**, puis cliquez sur **publier**.  
  
2.  Dans l’Explorateur de stratégies, sous la **RouteBasedOnMessageType** stratégie, le bouton droit sur **Version 1.0 - publiée**, puis cliquez sur **déployer**.  
  
 **Pour créer un modèle d’itinéraire langage spécifique à un domaine (DSL) ESB**  
  
1.  Dans Visual Studio, ouvrez C:\HowTos\Patterns\Patterns.sln.  
  
2.  Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.  
  
3.  Dans le **nom** , tapez **MessageType**, puis cliquez sur **ajouter**.  
  
 **Pour configurer les propriétés de la feuille de route**  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de **MessageType.itinerary**. Dans le **MessageType** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Dans le **modèle exportateur** la liste déroulante, cliquez sur **XML itinéraire exportateur**.  
  
    2.  Dans le **extendeur paramètres** section à côté du **fichier XML de la feuille de route** propriété, cliquez sur le bouton de sélection (...).  
  
    3.  Dans le **sélectionner un fichier XML** boîte de dialogue le **nom de fichier** , tapez **C:\HowTos\Itineraries\MessageType**, puis cliquez sur **enregistrer**.  
  
        > [!NOTE]
        >  Cette étape vous permet d’exporter la feuille de route en tant que XML vers un emplacement de fichier local. Exportation d’un itinéraire vers un emplacement de fichier local, au lieu de la base de données d’itinéraire, permet de tester de l’itinéraire à l’aide de l’application cliente de Test ESB. Vous pourrez terminer cette procédure plus loin dans cette rubrique.  
  
 **Pour définir la structure de la feuille de route**  
  
1.  Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception. Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **ReceiveOrders**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **rampe d’entrée ESB extendeur**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.  
  
    4.  Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.  
  
2.  Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis placez-le à droite de la **rampe d’entrée** élément de modèle. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **BreRoute**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.  
  
        > [!NOTE]
        >  Cette propriété définit que le processus a lieu dans un pipeline (messagerie). Ou bien, si le processus a lieu dans une orchestration, définissez la **d’extension du Service itinéraire** propriété **Orchestration extendeur**.  
  
    3.  Dans le **conteneur** déroulante liste, développez **ReceiveOrders**, puis cliquez sur **gestionnaires de réception**.  
  
    4.  Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Routing**.  
  
3.  Avec le bouton droit le **résolveur** collection de la **BreRoute** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**. Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **ByMessageType**.  
  
    2.  Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension du programme de résolution Bre**.  
  
    3.  Dans le **stratégie** la liste déroulante, cliquez sur **RouteBasedOnMessageType v 1.0**.  
  
4.  Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **ReceiveOrders** élément de modèle à la **BreRoute** élément de modèle.  
  
5.  Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **BreRoute** élément de modèle. Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **SendBasedOnType**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.  
  
    4.  Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.  
  
6.  Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **BreRoute** élément de modèle et la **SendBasedOnType** modèle élément. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **SendPortFilter**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.  
  
    3.  Dans le **rampe** déroulante liste, développez **SendBasedOnType**, puis cliquez sur **gestionnaires d’envoi**.  
  
7.  Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **BreRoute** élément de modèle à la **SendPortFilter** élément de modèle.  
  
8.  Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **SendPortFilter** élément de modèle à la **SendBasedOnType** élément de modèle.  
  
 **Pour exporter le modèle pour une utilisation avec le Client de Test d’itinéraire**  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de la **MessageType** itinéraire, puis cliquez sur **exporter le modèle**.  
  
    > [!NOTE]
    >  La version XML de l’itinéraire s’ouvre dans Visual Studio.  
  
2.  Enregistrez tous les artefacts de projet.  
  
3.  Dans l’Explorateur Windows, accédez à C:\HowTos\Itineraries et notez la création de votre feuille de route XML (MessageType.xml).  
  
 **Pour tester la feuille de route**  
  
1.  Ouvrez l’exemple d’application Client de Test d’itinéraire à l’aide du raccourci créé au cours de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB. Itinerary.Test.exe - raccourci).  
  
2.  Dans le Client de Test d’itinéraire, désactivez le **utiliser le Service WCF** case à cocher, puis cliquez sur **charge itinéraire**.  
  
3.  Dans le **ouvrir le fichier de feuille de route** boîte de dialogue, accédez à C:\HowTos\Itineraries. Sélectionnez **MessageType.xml**, puis cliquez sur **ouvrir** pour charger la feuille de route.  
  
4.  Cliquez sur **OK** pour effacer le **itinéraire chargé avec succès** message.  
  
5.  Dans le Client de Test d’itinéraire, cliquez sur le bouton de sélection (...) à côté du **charge Message** boîte.  
  
6.  Dans le **sélectionner le Document XML à charger** boîte de dialogue, accédez à C:\HowTos. Sélectionnez **NAOrderDoc.xml**, puis cliquez sur **ouvrir** pour le message de test de charge.  
  
7.  Cliquez sur le **soumettre la demande** bouton. Une fois le test terminé, cliquez sur **OK** pour faire disparaître la confirmation qui s’affiche.  
  
8.  Dans l’Explorateur Windows, accédez à C:\HowTos\Out\\. Vérifiez que le message NorthAmerica%MessageID%.xml a été écrit dans le répertoire.  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
 Pour plus d'informations, consultez les rubriques connexes suivantes :  
  
-   [Guide pratique pour sélectionner un itinéraire à l’aide d’une stratégie de règles métier](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [Guide pratique pour transformer un message et router le message résultant vers un emplacement de fichier à l’aide d’un bordereau de routage d’itinéraire](../esb-toolkit/transform-message-and-route-the-message-to-a-location-using-itinerary-routing.md)  
  
-   [Guide pratique pour implémenter un routage basé sur le contenu à l’aide d’une stratégie de règles métier pour un type de message connu](../esb-toolkit/apply-content-based-routing-using-business-rules-policy-for-known-message-type.md)  
  
-   [Activités de développement](../esb-toolkit/development-activities.md)  
  
-   [Modèles de routage des messages](../esb-toolkit/message-routing-patterns.md)  
  
-   [Utilisation de la résolution et du routage dynamiques](../esb-toolkit/using-dynamic-resolution-and-routing.md)