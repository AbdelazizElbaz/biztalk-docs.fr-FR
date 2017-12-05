---
title: "Comment : router un Message unique à plusieurs destinataires à l’aide d’un bon d’itinéraire de routage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42c30493-4fe1-4fd5-8bc7-af091535b091
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c493b33081e540a4e18d6d20e4813cdddad894a
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-route-a-single-message-to-multiple-recipients-using-an-itinerary-routing-slip"></a>Comment : router un Message unique à plusieurs destinataires à l’aide d’un bon d’itinéraire de routage
## <a name="goal"></a>Objectif  
 Cette section montre comment utiliser le langage spécifique à un domaine (DSL), concepteur pour créer un itinéraire qui route un message à trois destinataires distinctes à l’aide d’un programme de résolution statique et l’adaptateur FILE BizTalk Server.  
  
 Dans cette rubrique, vous effectuerez les étapes suivantes :  
  
-   Créer un itinéraire avec trois programmes de résolution statiques pour router les messages à plusieurs destinataires.  
  
-   Test de l’itinéraire à l’aide de l’exemple d’application Client de Test d’itinéraire.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
## <a name="steps"></a>Étapes  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a>Pour créer un modèle DSL de la feuille de route ESB  
  
1.  Dans Visual Studio, ouvrez C:\HowTos\Patterns\Patterns.sln.  
  
2.  Dans l’Explorateur de solutions, cliquez sur **ItineraryLibrary**, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **ItineraryDsl** dans le volet Modèles.  
  
4.  Dans le **nom** , tapez **RecipientList**, puis cliquez sur **ajouter**.  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a>Pour configurer les propriétés de la feuille de route  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de RecipientList.itinerary. Dans la fenêtre Propriétés de RecipientList, configurez les propriétés suivantes :  
  
    1.  Dans le **modèle exportateur** la liste déroulante, cliquez sur **XML itinéraire exportateur**.  
  
    2.  Dans le **extendeur paramètres** section à côté du **fichier XML de la feuille de route** propriété, cliquez sur le bouton de sélection (...).  
  
    3.  Dans le **sélectionner un fichier XML** boîte de dialogue le **nom de fichier** , tapez **C:\HowTos\Itineraries\RecipientList**, puis cliquez sur **enregistrer**.  
  
        > [!NOTE]
        >  Cette étape vous permet d’exporter la feuille de route en tant que XML vers un emplacement de fichier local. En exportant un itinéraire vers un emplacement de fichier local, au lieu de la base de données d’itinéraire, permet de tester de l’itinéraire à l’aide de l’application cliente de Test ESB. Vous pourrez terminer cette procédure plus loin dans cette rubrique.  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>Pour définir la structure de la feuille de route  
  
1.  Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception. Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **extendeur de rampe d’entrée**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.  
  
    4.  Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.  
  
2.  Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis placez-le à droite de la **rampe d’entrée** élément de modèle. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **RouteToThreeRecipients**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.  
  
        > [!NOTE]
        >  Cette propriété définit que le processus a lieu dans un pipeline (messagerie). Ou bien, si le processus a lieu dans une orchestration, définissez la **d’extension du Service itinéraire** propriété **Orchestration extendeur**.  
  
    3.  Dans le **conteneur** déroulante liste, développez **ReceiveNaOrderDoc**, puis cliquez sur **gestionnaires de réception**.  
  
    4.  Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Routing**.  
  
3.  Avec le bouton droit le **résolveur** collection de la **RouteToThreeRecipients** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**. Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **FirstResolver**.  
  
    2.  Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.  
  
    3.  Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.  
  
    4.  Cliquez sur le **Transport emplacement** propriété, puis tapez **C:\HowTos\Out\First%MessageID%.xml**.  
  
        > [!NOTE]
        >  Vous avez ajouté la première des trois programmes de résolution de ce service d’itinéraire. Vous allez maintenant ajouter les deux programmes de résolution plus pour acheminer le message à des destinataires supplémentaires.  
  
4.  Avec le bouton droit le **résolveur** collection de la **RouteToThreeRecipients** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**. Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **SecondResolver**.  
  
    2.  Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.  
  
    3.  Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.  
  
    4.  Cliquez sur le **Transport emplacement** propriété, puis tapez **C:\HowTos\Out\Second%MessageID%.xml**.  
  
5.  Avec le bouton droit le **résolveur** collection de la **RouteToThreeRecipients** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**. Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **ThirdResolver**.  
  
    2.  Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.  
  
    3.  Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.  
  
    4.  Cliquez sur le **Transport emplacement** propriété, puis tapez **C:\HowTos\Out\Third%MessageID%.xml**.  
  
6.  Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **RouteToThreeRecipients** élément de modèle.  
  
7.  Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **RouteToThreeRecipients** élément de modèle. Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **SendThreeMessages**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.  
  
    4.  Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.  
  
8.  Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **RouteToThreeRecipients** élément de modèle et la **SendThreeMessages** élément de modèle. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **SendPortFilter**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.  
  
    3.  Dans le **rampe** déroulante liste, développez **SendThreeMessages**, puis cliquez sur **gestionnaires d’envoi**.  
  
9. Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **RouteToThreeRecipients** élément de modèle à la **SendPortFilter** élément de modèle.  
  
10. Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **SendPortFilter** élément de modèle à la **SendThreeMessages** élément de modèle.  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a>Pour exporter le modèle pour une utilisation avec le Client de Test d’itinéraire  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de la **RecipientList** itinéraire, puis cliquez sur **exporter le modèle**.  
  
    > [!NOTE]
    >  La version XML de l’itinéraire s’ouvre dans Visual Studio.  
  
2.  Enregistrez tous les artefacts de projet.  
  
3.  Dans l’Explorateur Windows, accédez à C:\HowTos\Itineraries et notez la création de votre feuille de route XML (RecipientList.xml).  
  
#### <a name="to-test-the-itinerary"></a>Pour tester la feuille de route  
  
1.  Ouvrez l’exemple d’application Client de Test d’itinéraire à l’aide du raccourci créé au cours de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB. Itinerary.Test.exe - raccourci).  
  
2.  Dans le Client de Test d’itinéraire, désactivez le **utiliser le Service WCF** case à cocher, puis cliquez sur **charge itinéraire**.  
  
3.  Dans le **ouvrir le fichier de feuille de route** boîte de dialogue, accédez à C:\HowTos\Itineraries. Sélectionnez **RecipientList.xml**, puis cliquez sur **ouvrir** pour charger la feuille de route.  
  
4.  Cliquez sur **OK** pour effacer le « itinéraire a été chargé avec succès : message.  
  
5.  Dans le Client de Test d’itinéraire, cliquez sur le bouton de sélection (...) à côté du **charge Message** boîte.  
  
6.  Dans le **sélectionner le Document XML à charger** boîte de dialogue, accédez à C:\Patterns. Sélectionnez NAOrderDoc.xml, puis cliquez sur **ouvrir** pour le message de test de charge.  
  
7.  Cliquez sur le **soumettre la demande** bouton. Une fois le test terminé, cliquez sur **OK** pour faire disparaître la confirmation qui s’affiche.  
  
8.  Dans l’Explorateur Windows, accédez à C:\HowTos\Out\\. Vérifiez que les messages suivants ont été écrits dans le répertoire :  
  
    -   First%MessageID%.Xml  
  
    -   Second%MessageID%.Xml  
  
    -   Third%MessageID%.Xml  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
 Pour plus d'informations, consultez les rubriques connexes suivantes :  
  
-   [Activités de développement](../esb-toolkit/development-activities.md)  
  
-   [Modèles de routage des messages](../esb-toolkit/message-routing-patterns.md)  
  
-   [Utilisation de la résolution et du routage dynamiques](../esb-toolkit/using-dynamic-resolution-and-routing.md)