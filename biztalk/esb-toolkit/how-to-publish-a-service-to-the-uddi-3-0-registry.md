---
title: "Comment : publier un Service à UDDI 3.0 Registre | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c3bd0ed-e5f1-43eb-98d1-e3247a565ba2
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da3d2dc400c031ab5febda1568cb18ce5180366b
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-publish-a-service-to-the-uddi-30-registry"></a>Comment : publier un Service à UDDI 3.0 Registre
## <a name="goal"></a>Objectif  
 Cette section montre comment utiliser le site des services UDDI pour publier un point de terminaison de service Web qui peut être résolu à partir d’un itinéraire à des fins de routage d’un message d’ESB. Vous allez dupliquer le service PurchaseOrderSubmitOrderService existant actuellement publié dans le Registre.  
  
 Dans cette rubrique, vous effectuerez les étapes suivantes :  
  
-   Publier un service sur le Universal Description, Discovery, and Integration (UDDI) 3 Registre à l’aide de l’outil de serveur de publication UDDI.  
  
-   Test de la publication de service à l’aide d’un bordereau d’itinéraire de routage qui résout le point de terminaison de service à l’aide d’un programme de résolution UDDI3.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) et l’exécution de l’outil de serveur de publication UDDI (vous pouvez l’installer à % ESB installer Folder%\Bin\ Microsoft.Practices.ESB.UDDIPublisher.exe).  
  
## <a name="steps"></a>Étapes  
  
#### <a name="to-create-the-newposervice-in-the-uddi-registry"></a>Pour créer le NewPOService dans le Registre UDDI  
  
1.  Dans Internet Explorer, accédez au site des services UDDI (par défaut, l’URL pour cette est http://localhost/uddi).  
  
2.  Sur le **les Services uddi** , cliquez sur **publier**.  
  
3.  Dans le volet de la publication, cliquez sur **Microsoft.Practices.ESB**, puis cliquez sur **ajouter un Service**.  
  
4.  Sur la page suivante, sélectionnez **spécifier la clé à utiliser**, puis cliquez sur **continuer**.  
  
5.  Dans la page suivante, cliquez sur le **esb** clé de partition. Dans le **clé suffixe** , tapez **newposervice**, puis cliquez sur **continuer**.  
  
6.  Sur la page suivante, à côté (**nouveau nom de Service**), cliquez sur **modifier**. Nom de service **NewPOService**, puis cliquez sur **mise à jour**.  
  
7.  Cliquez sur **ajouter une Description**, tapez une description pour le service (par exemple, **exemple de Service**), puis cliquez sur **mise à jour**.  
  
#### <a name="to-add-a-binding-for-the-newposervice"></a>Pour ajouter une liaison pour le NewPOService  
  
1.  Cliquez sur le **liaisons** onglet, puis cliquez sur **ajouter la liaison**.  
  
2.  Sélectionnez **spécifier la clé à utiliser**, puis cliquez sur **continuer**.  
  
3.  Dans la page suivante, cliquez sur le **esb** clé de partition. Dans le **clé suffixe** , tapez **newposervicebinding**, puis cliquez sur **continuer**.  
  
4.  Sous **le Point d’accès**, cliquez sur **modifier**et puis procédez comme suit :  
  
    1.  Dans le **le Point d’accès** , tapez **http://localhost/ESB.CanadianServices/SubmitPOService.asmx**.  
  
    2.  Dans le **Type d’utilisation** la liste déroulante, cliquez sur **point de terminaison**, puis cliquez sur **mise à jour**.  
  
#### <a name="to-configure-the-binding-instance-information"></a>Pour configurer les informations d’instance de liaison  
  
1.  Cliquez sur le **Infos sur l’Instance** onglet, puis cliquez sur **ajouter des informations d’Instance**.  
  
2.  Dans le **recherche les noms de tModel contenant** , tapez **esb %** puis cliquez sur **recherche**.  
  
3.  Recherchez et cliquez sur le **tModel** pour **transporttype**.  
  
    > [!NOTE]
    >  Pour effectuer les étapes restantes de cette procédure, vous devrez peut-être passer à la page 1 et 2.  
  
4.  Dans le **Descriptions** , cliquez sur **ajouter une Description**.  
  
5.  Dans le **Description** , tapez **Type de Transport pour une utilisation d’itinéraire ESB**, puis cliquez sur **mise à jour**.  
  
6.  Cliquez sur le **détails de l’Instance** onglet, puis cliquez sur **modifier**.  
  
7.  Dans le **paramètres de l’Instance** , tapez **WCF-BasicHttp**, puis cliquez sur **mise à jour**.  
  
8.  Dans le **Descriptions** , cliquez sur **ajouter une Description**.  
  
9. Dans le **Description** , tapez **WCF de base du Transport HTTP**, puis cliquez sur **mise à jour**.  
  
10. Dans le volet de la publication, sous **NewPOService**, cliquez sur **http://localhost/esb.canadianservices/submitposervice.asmx**.  
  
11. Sur le **Infos sur l’Instance** , cliquez sur **ajouter des informations d’Instance**.  
  
12. À l’aide de la procédure décrite précédemment, ajoutez les informations d’instance suivantes, selon les valeurs indiquées dans le tableau suivant.  
  
    |élément tModel| Description|Paramètre|Description du paramètre|  
    |------------|-----------------|---------------|---------------------------|  
    |Microsoft-com:esb:runtimeresolution:messageexchangepattern|Modèle d’échange de message|Bidirectionnel|Opération bidirectionnelle|  
    |Microsoft-com:esb:runtimeresolution:cachetimeout|Délai d’expiration du cache|-1|Actuellement désactivé|  
    |Microsoft-com:esb:runtimeresolution:jaxrpcresponse|JaxRpcResponse|false||  
    |Microsoft-com:esb:runtimeresolution:action|Action de service|submitOrder|Spécifie la méthode de service à appeler|  
    |Microsoft-com:esb:runtimeresolution:targetnamespace|Service Namespace|http://globalbank.ESB.dynamicresolution.com/canadianservices|Espace de noms cible|  
  
#### <a name="to-configure-the-binding-categorization"></a>Pour configurer la catégorisation de liaison  
  
1.  Dans le volet de la publication, sous **NewPOService**, cliquez sur **http://localhost/esb.canadianservices/submitposervice.asmx**.  
  
2.  Sur le **catégories** , cliquez sur **ajouter une catégorie personnalisée**.  
  
3.  Dans le **recherche** , tapez **esb %** puis cliquez sur **recherche**.  
  
4.  Recherchez et cliquez sur le **microsoft-com:esb:runtimeresolution:biztalkapplication** tModel.  
  
5.  Dans le **nom de la clé** , tapez **Application BizTalk**.  
  
6.  Dans le **clé valeur** , tapez **Microsoft.Practices.ESB**, puis cliquez sur **ajouter une catégorie**.  
  
7.  Les étapes décrites précédemment, ajoutez les catégories personnalisées suivantes, selon les valeurs indiquées dans le tableau suivant.  
  
    |élément tModel|Nom de clé|Valeur de clé|  
    |------------|--------------|---------------|  
    |Microsoft-com:esb:runtimeresolution:portname|Nom du port|NewPOService|  
    |Microsoft-com:esb:runtimeresolution:transporttype|Type de transport|WCF-BasicHttp|  
  
#### <a name="to-locate-the-service-in-the-uddi-registry"></a>Pour localiser le service dans le Registre UDDI  
  
1.  Dans Internet Explorer, sur le **les Services uddi** , cliquez sur **recherche**.  
  
2.  Cliquez sur le **Services** onglet.  
  
3.  Dans le **nom du Service** , tapez **% PO**, puis cliquez sur **recherche**.  
  
4.  Dans le **recherche** volet, dans le **résultats** , cliquez sur **NewPOService**.  
  
    > [!NOTE]
    >  Cela confirme que le service a été publié avec succès dans le Registre.  
  
#### <a name="to-create-an-itinerary-model-to-test-the-uddi-service-publication"></a>Pour créer un modèle d’itinéraire pour tester la publication des services UDDI  
  
1.  Dans Visual Studio, ouvrez C:\HowTos\Patterns\Patterns.sln.  
  
2.  Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue le **nom** , tapez **NewBindingKeySearch**, puis cliquez sur **ajouter**.  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a>Pour configurer les propriétés de la feuille de route  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de **NewBindingKeySearch.itinerary**. Dans le **NewBindingKeySearch** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Dans le **réponse à la demande est** la liste déroulante, cliquez sur **True**.  
  
    2.  Dans le **modèle exportateur** la liste déroulante, cliquez sur **XML itinéraire exportateur**.  
  
    3.  Dans le **extendeur paramètres** section à côté du **fichier XML de la feuille de route** propriété, cliquez sur le bouton de sélection (...).  
  
    4.  Dans le **sélectionner un fichier XML** boîte de dialogue, tapez **C:\HowTos\Itineraries\NewBindingKeySearch** dans les **nom de fichier** zone, puis cliquez sur **enregistrer**.  
  
        > [!NOTE]
        >  Cette étape vous permet d’exporter la feuille de route en tant que XML vers un emplacement de fichier local. En exportant un itinéraire vers un emplacement de fichier local, au lieu de la base de données d’itinéraire, permet de tester de l’itinéraire à l’aide de l’application cliente de Test ESB. Vous pourrez terminer cette procédure plus loin dans cette rubrique.  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>Pour définir la structure de la feuille de route  
  
1.  Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception. Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **rampe d’entrée ESB extendeur**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.  
  
    4.  Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary.Response**.  
  
2.  Dans la boîte à outils, faites glisser un **itinéraire Service** élément de modèle à l’aire de conception. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **TransformNAOrder**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.  
  
    3.  Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.  
  
    4.  Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Transform**.  
  
3.  Avec le bouton droit le **résolveur** collection de la **TransformNAOrder** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**. Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **NAOrder_to_CNOrder**.  
  
    2.  Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension résolveur statiques**.  
  
    3.  Dans le **transformer un Type** la liste déroulante, cliquez sur **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**.  
  
4.  Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **TransformNAOrder** élément de modèle.  
  
5.  Dans la boîte à outils, faites glisser un **itinéraire Service** élément de modèle à l’aire de conception. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **BindingKeyRoute**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **extendeur de messagerie**.  
  
    3.  Dans le **conteneur** déroulante liste, développez **ReceiveNAOrder**, puis cliquez sur **gestionnaires de réception**.  
  
    4.  Dans le **nom du Service** la liste déroulante, cliquez sur **Microsoft.Practices.ESB.Services.Routing**.  
  
6.  Avec le bouton droit le **résolveur** collection de la **BindingKeyRoute** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**. Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **BindingKeySearch**.  
  
    2.  Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Uddi3 programme de résolution d’Extension**.  
  
    3.  Dans le **Moniker du programme de résolution** la liste déroulante, cliquez sur **UDDI3**.  
  
    4.  Cliquez sur le **clé de liaison** propriété, puis tapez **uddi:esb:newposervicebinding**. Pour rechercher la valeur de clé, cliquez sur le service http://localhost/ESB.CanadianServices/SubmitPOService.asmx dans UDDI, puis cliquez sur plus de détails.  
  
7.  Cliquez sur le **BindingKeySearch** programme de résolution, puis cliquez sur **Configuration du programme de résolution de Test**.  
  
    > [!NOTE]
    >  Vérifiez la sortie affichée dans la fenêtre Sortie.  
  
8.  Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **TransformNAOrder** élément de modèle à la **BindingKeyRoute** élément de modèle.  
  
9. Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **BindingKeyRoute** élément de modèle. Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **SendCNOrder**.  
  
    2.  Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.  
  
    3.  Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.  
  
    4.  Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionSolicitResp**.  
  
10. Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **BindingKeyRoute** élément de modèle et la **SendCNOrder** élément de modèle. Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Cliquez sur le **nom** propriété, puis tapez **SendPortFilter**.  
  
    2.  Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.  
  
    3.  Dans le **rampe** déroulante liste, développez **SendCNOrder**, puis cliquez sur **gestionnaires d’envoi**.  
  
11. Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **BindingKeyRoute** élément de modèle à la **SendPortFilter** élément de modèle.  
  
12. Dans la boîte à outils, cliquez sur **connecteur**. Faites glisser une connexion à partir de la **SendPortFilter** élément de modèle à la **SendNAOrder** élément de modèle.  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a>Pour exporter le modèle pour une utilisation avec le Client de Test d’itinéraire  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de la **NewBindingKeySearch** itinéraire, puis cliquez sur **exporter le modèle**.  
  
    > [!NOTE]
    >  La version XML de l’itinéraire s’ouvre dans Visual Studio.  
  
2.  Enregistrez tous les artefacts de projet.  
  
3.  Dans l’Explorateur Windows, accédez à C:\HowTos\Itineraries et notez la création de votre feuille de route XML (NewBindingKeySearch.xml).  
  
#### <a name="to-test-the-itinerary"></a>Pour tester la feuille de route  
  
1.  Ouvrez l’exemple d’application Client de Test d’itinéraire à l’aide du raccourci créé au cours de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB. Itinerary.Test.exe - raccourci).  
  
2.  Dans le Client Test de la feuille de route, dans le **Options du Service Web** groupe, désactivez le **utiliser le Service WCF** zone, puis sélectionnez le **bidirectionnel Service** case à cocher.  
  
3.  Cliquez sur le **charge itinéraire** bouton.  
  
4.  Dans le **ouvrir le fichier de feuille de route** boîte de dialogue, accédez à C:\HowTos\Itineraries. Sélectionnez **NewBindingKeySearch.xml**, puis cliquez sur **ouvrir** pour charger la feuille de route.  
  
5.  Cliquez sur **OK** pour effacer le **itinéraire chargé avec succès** message.  
  
6.  Dans le Client de Test d’itinéraire, cliquez sur le bouton de sélection (...) à côté du **charge Message** boîte.  
  
7.  Dans le **sélectionner le Document XML à charger** boîte de dialogue, accédez à C:\HowTos. Sélectionnez **NAOrderDoc.xml**, puis cliquez sur **ouvrir** pour le message de test de charge.  
  
8.  Cliquez sur le **soumettre la demande** bouton. Une fois le test terminé, cliquez sur **OK** pour faire disparaître la confirmation qui s’affiche.  
  
9. Vérifiez que le message de réponse correcte s’affiche dans le **résultat** zone de texte de la **Itineray Test Client**.  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
 Pour plus d'informations, consultez les rubriques connexes suivantes :  
  
-   [Guide pratique pour résoudre un point de terminaison de service à l’aide d’une recherche de clé de liaison UDDI](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-binding-key-search.md)  
  
-   [Guide pratique pour résoudre un point de terminaison de service à l’aide d’une recherche de catégorie UDDI](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-category-search.md)  
  
-   [Activités de développement](../esb-toolkit/development-activities.md)