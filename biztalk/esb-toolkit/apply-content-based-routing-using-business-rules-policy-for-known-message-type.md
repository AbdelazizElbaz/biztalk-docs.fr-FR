---
title: "Comment : implémenter en fonction du contenu routage à l’aide d’une entreprise règles de stratégie pour un Type connu | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44451c85-929a-4d13-b0dd-53ea600d0859
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b384c63b26f98a866390a001c7d7c2ec6f3f7cb2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-implement-content-based-routing-using-a-business-rules-policy-for-a-known-message-type"></a>Comment : implémenter en fonction du contenu routage à l’aide d’une entreprise règles de stratégie pour un Type connu
## <a name="goal"></a>Objectif  
 Cette section montre comment créer un itinéraire qui dynamiquement achemine un message basé sur le contenu d’un type connu (schéma déployé sur la base de données de Configuration de Microsoft BizTalk Server), une entreprise à l’aide de règles de stratégie.  
  
 Dans cette rubrique, vous effectuerez les étapes suivantes :  
  
-   Créer une stratégie de règles d’entreprise qui permet de router un message en fonction du contenu.  
  
-   Créez un bordereau d’itinéraire de routage avec un programme de résolution BRE d’acheminer un message.  
  
-   Test de l’itinéraire à l’aide de l’exemple d’application Client de Test d’itinéraire.  
  
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
  
#### <a name="to-create-a-bre-policy-to-route-using-custom-message-properties"></a>Pour créer une stratégie BRE pour router à l’aide des propriétés de message personnalisées  
 Cette règle utilisera le nom du client à définir dynamiquement le point de terminaison utilisé pour router le message.  
  
1.  Cliquez sur **Démarrer** dans la barre des tâches, pointez sur **tous les programmes**, pointez sur  **[!INCLUDE[prague](../includes/prague-md.md)]** , puis cliquez sur **Éditeur des règles d’entreprise**.  
  
2.  Dans l’Explorateur de stratégies, cliquez sur **stratégies**, puis cliquez sur **ajouter une nouvelle stratégie**. Nom de la stratégie **RouteBasedOnCustomerKnownType**.  
  
#### <a name="to-add-a-routing-rule-for-customer-globalbank-west"></a>Pour ajouter une règle de routage pour le client GlobalBank West  
  
1.  Dans le **RouteBasedOnCustomerKnownType** stratégie, avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **ajouter une nouvelle règle**. Nommez la règle **SetWestEndpoint**.  
  
2.  Dans l’Explorateur de faits, cliquez sur le **schémas XML** droit **schémas**, puis cliquez sur **Parcourir**.  
  
3.  Dans le **les fichiers de schéma** boîte de dialogue, accédez à C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB. DynamicResolution.Schemas, sélectionnez **NAOrderDoc.xsd**, puis cliquez sur **ouvrir**.  
  
    > [!NOTE]
    >  Voici le schéma qui définit le message NAOrderDoc.xml, qui a été utilisé pour créer les messages ouest / est que vous allez utiliser pour le test.  
  
4.  Dans l’Explorateur de faits, cliquez sur **NAOrderDoc.xsd**, puis dans le volet Propriétés, cliquez sur le **Type de Document** propriété, puis tapez **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc** .  
  
    > [!NOTE]
    >  Il s’agit du nom qualifié complet du schéma.  
  
5.  Dans l’Explorateur de faits, développez **NAOrderDoc.xsd**, puis développez **OrderDoc**.  
  
6.  Dans la fenêtre de la règle, cliquez sur **Conditions**, pointez sur **prédicats**, puis cliquez sur **égal**.  
  
7.  Dans l’Explorateur de faits, faites glisser le **customerName** élément à la **argument1** nœud sous **Conditions**.  
  
8.  Cliquez sur le **argument2** nœud, puis tapez **GlobalBankWest**.  
  
9. Dans l’Explorateur de faits, cliquez sur le **vocabulaires** onglet, développez **ESB. EndPointInfo**, puis développez **Version 1.0**.  
  
    > [!NOTE]
    >  La [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] inclut plusieurs vocabulaires qui peuvent être utilisés pour créer des règles pour l’utilisation dans l’architecture ESB. Certains d'entre eux doivent être remplacé ou augmentée avec vos propres vocabulaires. Par exemple, le **DynamicRunTimeMaptypes** a des définitions pour les cartes fournies dans le **GlobalBank** exemples.  
  
10. Dans l’Explorateur de faits, faites glisser le **définir l’emplacement du Transport Point de terminaison sortants** définition **Actions**.  
  
11. Cliquez sur  **\<une chaîne vide >** , puis tapez **C:\HowTos\Out\West%MessageID%.xml**.  
  
12. Dans l’Explorateur de faits, faites glisser le **définir le Type de Transport Point de terminaison sortants** définition **Actions**.  
  
13. Dans l’Explorateur de faits, développez **ESB. TransportTypes**, développez **Version 1.0**, puis faites glisser le **adaptateur fournisseurs** définition  **\<une chaîne vide >**.  
  
14. Dans le **Actions** volet, développez le **adaptateur fournisseurs** liste déroulante, puis cliquez sur **fichier**.  
  
#### <a name="to-add-a-routing-rule-for-customer-globalbank-east"></a>Pour ajouter une règle de routage pour le client est de GlobalBank  
  
1.  Dans l’Explorateur de stratégies, cliquez sur le **SetWestEndpoint** de règle, puis cliquez sur **copie**.  
  
2.  Avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **coller**.  
  
3.  Dans le **nom de la nouvelle règle** boîte de dialogue, tapez **SetEastEndpoint**, puis cliquez sur **OK**.  
  
4.  Dans l’Explorateur de stratégies, cliquez sur le **SetEastEndpoint** règle.  
  
5.  Dans le **Conditions** section, cliquez sur **GlobalBankWest**, puis cliquez sur **réinitialiser l’argument**.  
  
6.  Cliquez sur **argument2**, puis tapez **GlobalBankEast**.  
  
7.  Dans le **Actions** section, cliquez sur **C:\HowTos\Out\West%MessageID%.xml**, puis cliquez sur **réinitialiser l’argument**.  
  
8.  Cliquez sur  **\<une chaîne vide >**, puis tapez **C:\HowTos\Out\East%MessageID%.xml**.  
  
#### <a name="to-add-a-routing-rule-for-unknown-customers"></a>Pour ajouter une règle de routage pour les clients inconnus  
  
1.  Dans la stratégie RouteBasedOnCustomerKnownType, avec le bouton droit de la Version 1.0 (non enregistrée), puis cliquez sur Ajouter une nouvelle règle. Nom de la règle SetUnknownCustomerEndpoint.  
  
2.  Dans la fenêtre de la règle, cliquez sur les Conditions, puis cliquez sur Ajouter et logique.  
  
3.  Dans la fenêtre de la règle, avec le bouton droit et, pointez sur les prédicats, puis cliquez sur NotEqual.  
  
4.  Dans l’Explorateur de faits, cliquez sur l’onglet schémas XML, NAOrderDoc.xsd, puis OrderDoc.  
  
5.  À partir de l’Explorateur de faits, faites glisser l’élément customerName au nœud argument1 sous Conditions.  
  
6.  Cliquez sur le nœud argument2 et tapez GlobalBankWest.  
  
7.  Dans la fenêtre de la règle, avec le bouton droit et, pointez sur les prédicats, puis cliquez sur NotEqual.  
  
8.  À partir de l’Explorateur de faits, faites glisser l’élément customerName au nœud argument1 sous Conditions.  
  
9. Cliquez sur le nœud argument2 et tapez GlobalBankEast.  
  
10. Dans l’Explorateur de faits, cliquez sur l’onglet vocabulaires, ESB. EndPointInfo, puis développez la Version 1.0.  
  
11. À partir de l’Explorateur de faits, faites glisser la définition de l’emplacement de Transport sortant Point de terminaison défini pour les Actions.  
  
12. Cliquez sur \<une chaîne vide >, puis tapez C:\HowTos\Out\CustomerUnknown%MessageID%.xml.  
  
13. À partir de l’Explorateur de faits, faites glisser la définition du Type de Transport sortant Point de terminaison défini pour les Actions.  
  
14. Dans l’Explorateur de faits, développez ESB. TransportTypes, puis Version 1.0, puis faites glisser la définition de fournisseurs de carte à \<une chaîne vide >.  
  
15. Dans le volet Actions, développez la liste déroulante des fournisseurs de carte, puis cliquez sur fichier.  
  
#### <a name="to-publish-and-deploy-the-policy"></a>Pour publier et déployer la stratégie  
  
1.  Dans l’Explorateur de stratégies, sous la **RouteBasedOnCustomerKnownType** stratégie, le bouton droit sur **Version 1.0 (non enregistrée)**, puis cliquez sur **publier**.  
  
2.  Dans l’Explorateur de stratégies, sous la **RouteBasedOnCustomerKnownType** stratégie, le bouton droit sur **Version 1.0 - publiée**, puis cliquez sur **déployer**.  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a>Pour créer un modèle DSL de la feuille de route ESB  
  
1.  Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez C:\HowTos\Patterns\Patterns.sln.  
  
2.  Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue le **nom** , tapez **CbrKnownType**, puis cliquez sur **ajouter**.  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a>Pour configurer les propriétés de la feuille de route  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de **CbrKnownType.itinerary**. Dans le **CbrKnownType** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Dans le **modèle exportateur** la liste déroulante, cliquez sur **XML itinéraire exportateur**.  
  
    2.  Dans le **extendeur paramètres** section à côté du **fichier XML de la feuille de route** propriété, cliquez sur le bouton de sélection (...).  
  
    3.  Dans le **sélectionner un fichier XML** boîte de dialogue, tapez **C:\HowTos\Itineraries\CbrKnownType** dans les **nom de fichier** zone, puis cliquez sur **enregistrer**.  
  
        > [!NOTE]
        >  Cette étape vous permet d’exporter la feuille de route en tant que XML vers un emplacement de fichier local. En exportant un itinéraire vers un emplacement de fichier local, au lieu de la base de données d’itinéraire, permet de tester de l’itinéraire à l’aide de l’application cliente de Test ESB. Vous pourrez terminer cette procédure plus loin dans cette rubrique.  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>Pour définir la structure de la feuille de route  
  
1.  Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception. Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **rampe d’entrée ESB extendeur**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.  
  
    4.  Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.  
  
2.  Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **ReceiveNAOrder** élément de modèle. Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **SendRegionalOrders**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.  
  
    4.  Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.  
  
3.  Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **ReceiveNAOrder** élément de modèle et la **SendRegionalOrders**élément de modèle. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **SendPortFilter**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.  
  
    3.  Dans le **rampe** déroulante liste, développez **SendRegionalOrders**, puis cliquez sur **gestionnaires d’envoi**.  
  
4.  Avec le bouton droit le **résolveur** collection de la **SendPortFilter** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**. Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **RouteRegionalOrders**.  
  
    2.  Dans le **nom Transport** la liste déroulante, cliquez sur **BRE**.  
  
    3.  Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension du programme de résolution Bre**.  
  
    4.  Dans le **stratégie** la liste déroulante, cliquez sur **RouteBasedOnCustomerKnownType**.  
  
    5.  Dans le **reconnaît un Format de Message** cliquez sur la liste déroulante **True**.  
  
    6.  Dans le **UseMsg** la liste déroulante, cliquez sur **True**.  
  
        > [!NOTE]
        >  Si vous utilisez l’Extension du programme de résolution BRE à partir de l’orchestration, le **recognizeMessageFormat** propriété doit être définie sur **False**.  
  
5.  Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **SendPortFilter** élément de modèle.  
  
6.  Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **SendPortFilter** élément de modèle à la **SendRegionalOrders** élément de modèle.  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a>Pour exporter le modèle pour une utilisation avec le Client de Test d’itinéraire  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de la **CbrKnownType** itinéraire, puis cliquez sur **exporter le modèle**.  
  
    > [!NOTE]
    >  La version XML de l’itinéraire s’ouvre dans Visual Studio.  
  
2.  Enregistrez tous les artefacts de projet.  
  
3.  Dans l’Explorateur Windows, accédez à C:\HowTos\Itineraries et notez la création de votre feuille de route XML (CbrKnownType.xml).  
  
#### <a name="to-test-the-itinerary-and-business-rules"></a>Pour tester les règles d’itinéraire et d’entreprise  
  
1.  Ouvrez l’exemple d’application Client de Test d’itinéraire à l’aide du raccourci créé au cours de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB. Itinerary.Test.exe - raccourci).  
  
2.  Dans le Client de Test d’itinéraire, désactivez le **utiliser le Service WCF** case à cocher, puis cliquez sur **charge itinéraire**.  
  
3.  Dans le **ouvrir le fichier de feuille de route** boîte de dialogue, accédez à C:\HowTos\Itineraries. Sélectionnez **CbrKnownType.xml**, puis cliquez sur **ouvrir** pour charger la feuille de route.  
  
4.  Cliquez sur **OK** pour effacer le **itinéraire chargé avec succès** message.  
  
5.  Dans le Client de Test d’itinéraire, cliquez sur le bouton de sélection (...) à côté du **charge Message** boîte.  
  
6.  Dans le **sélectionner le Document XML à charger** boîte de dialogue, accédez à C:\HowTos. Sélectionnez **West.xml**, puis cliquez sur **ouvrir** pour le message de test de charge.  
  
7.  Cliquez sur le **soumettre la demande** bouton. Une fois le test terminé, cliquez sur **OK** pour faire disparaître la confirmation qui s’affiche.  
  
8.  Dans l’Explorateur Windows, accédez à C:\HowTos\Out. Vérifiez que le message West%MessageID%.xml a été écrit dans le répertoire.  
  
9. Répétez le processus de test en utilisant le message East.xml.  
  
10. Dans l’Explorateur Windows, accédez à C:\HowTos\Out. Vérifiez que le message East%MessageID%.xml a été écrit dans le répertoire.  
  
11. Répétez le processus de test en utilisant le message NAOrderDoc.xml.  
  
12. Dans l’Explorateur Windows, accédez à C:\HowTos\Out. Vérifiez que le message CustomerUnknown%MessageID%.xml a été écrit dans le répertoire.  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
 Pour plus d'informations, consultez les rubriques connexes suivantes :  
  
-   [Comment : sélectionner un itinéraire à l’aide d’une stratégie de règles d’entreprise](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [Comment : acheminer un Message basé sur le contexte du Message à l’aide d’une stratégie de règles d’entreprise](../esb-toolkit/dynamically-route-messages-based-on-message-context-using-business-rules-policy.md)  
  
-   [Activités de développement](../esb-toolkit/development-activities.md)  
  
-   [Modèles de routage de messages](../esb-toolkit/message-routing-patterns.md)