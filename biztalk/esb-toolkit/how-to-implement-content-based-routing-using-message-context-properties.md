---
title: "Comment : implémenter le routage basé sur le contenu à l’aide des propriétés de contexte de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 952af792-5762-4b04-9087-980bb3323568
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e47235978960ac89f4ea276c4c4a60c8ddf16e1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-implement-content-based-routing-using-message-context-properties"></a>Comment : implémenter le routage basé sur le contenu à l’aide des propriétés de contexte de Message
## <a name="goal"></a>Objectif  
 Cette section montre comment utiliser le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Concepteur de feuille de route pour créer un itinéraire qui sélectionne un destinataire de message en fonction de la propriété de contexte de message, puis achemine un message vers ce destinataire à l’aide de l’itinéraire Service Broker pour les service de messagerie.  
  
 Dans cette rubrique, vous effectuerez les étapes suivantes :  
  
-   Créer un itinéraire avec un broker d’itinéraire et les deux services de routage avec des programmes de résolution statiques.  
  
-   Test de l’itinéraire à l’aide de l’exemple d’application Client de Test d’itinéraire.  
  
> [!NOTE]
>  Aucun service broker basé sur l’orchestration n’est fournie dans l’implémentation actuelle.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
## <a name="steps"></a>Étapes  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a>Pour créer un modèle ESB itinéraire DSL  
  
1.  Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez C:\HowTos\Patterns\Patterns.sln.  
  
2.  Dans l’Explorateur de solutions, cliquez sur **ItineraryLibrary**, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **ItineraryDsl** dans le volet Modèles.  
  
4.  Dans le **nom** , tapez **ChoiceRouter**, puis cliquez sur **ajouter**.  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a>Pour configurer les propriétés de la feuille de route  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de la **ChoiceRouter** itinéraire. Dans le **ChoiceRouter** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Dans le **modèle exportateur** la liste déroulante, cliquez sur **XML itinéraire exportateur**.  
  
    2.  Dans le **extendeur paramètres** , cliquez sur le bouton de sélection (...) à côté du **fichier XML de la feuille de route** propriété.  
  
    3.  Dans le **exporter un Mode** liste de propriétés de liste déroulante, cliquez sur **Strict**.  
  
    4.  Dans le **sélectionner un fichier XML** boîte de dialogue, tapez **C:\HowTos\Itineraries\ChoiceRouter** dans les **nom de fichier** zone, puis cliquez sur **enregistrer**.  
  
    > [!NOTE]
    >  Cette étape vous permet d’exporter la feuille de route en tant que XML vers un emplacement de fichier local. En exportant un itinéraire vers un emplacement de fichier local, au lieu de la base de données d’itinéraire, vous pouvez tester l’itinéraire à l’aide de l’application cliente de Test ESB. Vous pourrez terminer cette procédure plus loin dans cette rubrique.  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>Pour définir la structure de la feuille de route  
  
1.  Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception. Dans la fenêtre Propriétés de OnRamp1, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **extendeur de rampe d’entrée**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.  
  
    4.  Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.  
  
2.  Dans la boîte à outils, faites glisser un **itinéraire Service Broker Service** élément à l’aire du Concepteur de modèle, puis placez-le à droite de la **rampe d’entrée** élément de modèle. Dans le **ItineraryBrokerService1**, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **RouteBrokerService**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **extendeur de service Broker de messagerie**.  
  
    3.  Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.  
  
    4.  Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Itinerary.Services.Broker.MessagingBroker**.  
  
3.  Cliquez sur le **filtre** collection, puis cliquez sur **ajouter un nouveau filtre**. Dans le **Filter1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **ASMXFilter**.  
  
    2.  Cliquez sur le **filtre** implémentation d’un menu déroulant, puis cliquez sur **filtre XPath**.  
  
    3.  Cliquez sur le **Expression** propriété, puis tapez **count (ContextProperties/propriété [@name= 'InboundTransportLocation'] [contient (., 'ProcessItinerary.asmx')]) > 0**.  
  
4.  Cliquez sur le **filtre** collection, puis cliquez sur **ajouter un nouveau filtre**. Dans le **Filter1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **WCFFilter**.  
  
    2.  Cliquez sur le **implémentation de filtre** liste déroulante, puis cliquez sur **filtre XPath**.  
  
    3.  Cliquez sur le **Expression** propriété, puis tapez **count (ContextProperties/propriété [@name= 'InboundTransportLocation'] [contient (., ' ESB. ItineraryServices.WCF')]) > 0**.  
  
5.  Avec le bouton droit le **résolveur** collection de la **RouteBrokerService** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**. Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **ResolverBrokerRoute**.  
  
    2.  Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **MessageContext programme de résolution d’Extension**.  
  
6.  Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **RouteBrokerService** élément de modèle.  
  
7.  Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle et placez-le sous le **RouteBrokerService** élément de modèle. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **RouteToFileFromASMX**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.  
  
        > [!NOTE]
        >  Cette propriété définit que le processus a lieu dans un pipeline (messagerie). Ou bien, si le processus a lieu dans une orchestration, définissez la **d’extension du Service itinéraire** propriété **Orchestration extendeur**.  
  
    3.  Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.  
  
    4.  Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Routing**.  
  
8.  Avec le bouton droit le **résolveur** collection de la **RouteToFileFromASMX** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**. Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **ResolverFromAsmx**.  
  
    2.  Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.  
  
    3.  Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.  
  
    4.  Cliquez sur le **Transport emplacement** propriété, puis tapez **c:\howtos\out\asmx%MessageId%.xml**.  
  
9. Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **RouteToFileFromASMX** élément de modèle. Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **SendASMXOrder**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.  
  
    4.  Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.  
  
10. Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **RouteToFileFromASMX** élément de modèle et la **SendASMXOrder**élément de modèle. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **SendPortFilterASMX**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.  
  
    3.  Dans le **rampe** déroulante liste, développez **SendASMXOrder**, puis cliquez sur **gestionnaires d’envoi**.  
  
11. Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **RouteToFileFromASMX** élément de modèle à la **SendPortFilterASMX** élément de modèle.  
  
12. Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **SendPortFilterASMX** élément de modèle à la **SendASMXOrder** élément de modèle.  
  
13. Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis placez-le à droite de **RouteBrokerService** élément de modèle. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **RouteToFileFromWCF**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.  
  
        > [!NOTE]
        >  Cette propriété définit que le processus a lieu dans un pipeline (messagerie). Ou bien, si le processus a lieu dans une orchestration, définissez la **d’extension du Service itinéraire** propriété **Orchestration extendeur**.  
  
    3.  Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.  
  
    4.  Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Routing**.  
  
14. Avec le bouton droit le **résolveur** collection de la **RouteToFileFromWCF** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**. Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **ResolverFromWCF**.  
  
    2.  Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.  
  
    3.  Dans le **nom Transport** la liste déroulante, cliquez sur **fichier**.  
  
    4.  Cliquez sur le **Transport emplacement** propriété, puis tapez **c:\howtos\out\wcf%MessageId%.xml**.  
  
15. Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **RouteToFileFromWCF** élément de modèle. Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **SendWCFOrder**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.  
  
    4.  Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.  
  
16. Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **RouteToFileFromWCF** élément de modèle et la **SendWCFOrder**élément de modèle. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **SendPortFilterWCF**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.  
  
    3.  Dans le **rampe** déroulante liste, développez **SendWCFOrder**, puis cliquez sur **gestionnaires d’envoi**.  
  
17. Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **RouteToFileFromWCF** élément de modèle à la **SendPortFilterWCF** élément de modèle.  
  
18. Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **SendPortFilterWCF** élément de modèle à la **SendWCFOrder** élément de modèle.  
  
19. Dans la boîte à outils, faites glisser un **itinéraire Outport** élément de modèle à la bordure droite de **RouteBrokerService**. Dans le **ItineraryBrokerOutPort1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **Port WCF**.  
  
    2.  Dans le **filtre** la liste déroulante, cliquez sur **WCFFilter**.  
  
    3.  Dans le **résolveur** la liste déroulante, cliquez sur **ResolverBrokerRoute**.  
  
20. Dans la boîte à outils, faites glisser un **itinéraire Outport** élément de modèle à la bordure inférieure de **RouteBrokerService**. Dans le **ItineraryBrokerOutPort1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **ASMX Port**.  
  
    2.  Dans le **filtre** la liste déroulante, cliquez sur **ASMXFilter**.  
  
    3.  Dans le **résolveur** la liste déroulante, cliquez sur **ResolverBrokerRoute**.  
  
21. Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **Port WCF** élément de modèle à la **RouteToFileFromWCF** élément de modèle.  
  
22. Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **ASMX Port** élément de modèle à la **RouteToFileFromASMX** élément de modèle.  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a>Pour exporter le modèle pour une utilisation avec le Client de Test d’itinéraire  
  
> [!NOTE]
>  Vous devez exporter la feuille de route à deux reprises : une fois au format XML et une heure à la base de données pour tester le routage via le service broker.  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de la **ChoiceRouter** itinéraire, puis cliquez sur **exporter le modèle**.  
  
    > [!NOTE]
    >  La version XML de l’itinéraire s’ouvre dans Visual Studio.  
  
2.  Dans l’Explorateur Windows, accédez à C:\HowTos\Itineraries et notez la création de votre feuille de route XML (ChoiceRouter.xml).  
  
3.  Dans Visual Studio, cliquez sur l’aire de conception de la **ChoiceRouter** itinéraire, puis cliquez sur **exporter le modèle**.  
  
4.  Dans la fenêtre Propriétés, cliquez sur **exportateur de feuille de route de base de données** dans les **modèle exportateur** liste déroulante.  
  
5.  Dans la fenêtre Propriétés, définissez la **base de données de la feuille de route** chaîne de connexion de propriété pour pointer vers la base de données d’itinéraire.  
  
6.  Dans le **état de la feuille de route** propriété liste déroulante, sélectionnez **déployées**.  
  
7.  Dans Visual Studio, cliquez sur l’aire de conception de la **ChoiceRouter** itinéraire, puis cliquez sur **exporter le modèle**.  
  
#### <a name="to-test-the-itinerary"></a>Pour tester la feuille de route  
  
1.  Ouvrez l’exemple d’application Client de Test d’itinéraire à l’aide du raccourci créé au cours de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB. Itinerary.Test.exe - raccourci).  
  
2.  Dans le Client de Test d’itinéraire, désactivez le **utiliser le Service WCF** case à cocher, puis cliquez sur **charge itinéraire**.  
  
3.  Dans le **ouvrir le fichier de feuille de route** boîte de dialogue, accédez à C:\HowTos\Itineraries. Sélectionnez **ChoiceRouter.xml**, puis cliquez sur **ouvrir** pour charger la feuille de route.  
  
4.  Cliquez sur **OK** pour fermer le message « Itinéraire chargé avec succès ».  
  
5.  Dans le Client de Test d’itinéraire, cliquez sur le bouton de sélection (...) à côté du **charge Message** boîte.  
  
6.  Dans le **sélectionner le Document XML à charger** boîte de dialogue, accédez à C:\Patterns\HowTos. Sélectionnez NAOrderDoc.xml, puis cliquez sur **ouvrir** pour le message de test de charge.  
  
7.  Cliquez sur le **soumettre la demande** bouton. Une fois le test terminé, cliquez sur **OK** pour fermer le message de confirmation qui s’affiche.  
  
8.  Dans l’Explorateur Windows, accédez à C:\HowTos\Out. Vérifiez que les messages ASMX%MessageID%.xml ont été écrits dans ce répertoire.  
  
9. Cliquez sur le client de Test de la feuille de route **utiliser le Service WCF** case à cocher. Dans le **nom d’itinéraire** , tapez **ChoiceRouter**, puis cliquez sur le **soumettre la demande** bouton. Une fois le test terminé, cliquez sur **OK** pour fermer le message de confirmation.  
  
10. Dans l’Explorateur Windows, accédez à C:\HowTos\Out. Vérifiez que les messages WCF%MessageID%.xml ont été écrits dans ce répertoire.  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
 Pour plus d'informations, consultez les rubriques connexes suivantes :  
  
-   [Comment : sélectionner un itinéraire à l’aide d’une stratégie de règles d’entreprise](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [Comment : acheminer un Message basé sur le contexte du Message à l’aide d’une stratégie de règles d’entreprise](../esb-toolkit/dynamically-route-messages-based-on-message-context-using-business-rules-policy.md)  
  
-   [Activités de développement](../esb-toolkit/development-activities.md)  
  
-   [Modèles de routage de messages](../esb-toolkit/message-routing-patterns.md)