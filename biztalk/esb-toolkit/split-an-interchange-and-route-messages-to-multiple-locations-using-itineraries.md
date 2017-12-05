---
title: "Comment : fractionner un échange et de router les Messages résultants vers plusieurs emplacements de fichier à l’aide d’itinéraires distinctes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccd46bee-e4a1-4846-8bde-b0460bda1e72
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 538432f548b1403fd9c0cd566b82eb8cb113f737
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-split-an-interchange-and-route-the-resulting-messages-to-multiple-file-locations-using-distinct-itineraries"></a>Comment : fractionner un échange et de router les Messages résultants vers plusieurs emplacements de fichier à l’aide d’itinéraires distinctes
## <a name="goal"></a>Objectif  
 Cette section montre comment créer un ESB rampe d’entrée qui utilise le **ItinerarySelectReceiveXml** bon de pipeline et comment configurer les composants du pipeline pour fractionner un échange entrant, puis sélectionnez le routage approprié pour chaque message résultant, selon le contexte du message. Sélection d’itinéraire est résolue à l’aide d’une stratégie de règles d’entreprise, et les messages sont routés différemment selon la région dans lequel réside le client.  
  
 Dans cette rubrique, vous effectuerez les étapes suivantes :  
  
-   Créer un ESB rampe d’entrée qui fractionne un échange XML.  
  
-   Configurer le composant de pipeline de sélecteur de feuille de route pour utiliser une stratégie de règles d’entreprise pour sélectionner la feuille de route approprié.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Effectuez les tâches suivantes avant d’effectuer les étapes plus loin dans cette rubrique :  
  
-   Créer les artefacts requis.  
  
-   Ajouter un projet de schémas à la solution de modèles.  
  
-   Ajouter les artefacts de projet de schémas.  
  
-   Créer une stratégie BRE pour sélectionner un itinéraire à l’aide des propriétés de message personnalisées.  
  
-   Ajouter une règle de sélection pour le client GlobalBank West.  
  
-   Ajouter une règle de sélection pour le client est de GlobalBank.  
  
-   Publier et déployer la stratégie.  
  
-   Créer un modèle d’itinéraire langage spécifique à un domaine (DSL) pour les messages GlobalBank West ESB.  
  
-   Configurez les propriétés de l’itinéraire GlobalBank West.  
  
-   Définir la structure de la feuille de route GlobalBank West.  
  
-   Exporter le modèle de GlobalBank West vers la base de données d’itinéraire.  
  
-   Créer un modèle DSL ESB d’itinéraire pour les messages de GlobalBank est.  
  
-   Configurez les propriétés de l’itinéraire GlobalBank est.  
  
-   Définir la structure de la feuille de route GlobalBank est.  
  
-   Exporter le modèle GlobalBank est à la base de données d’itinéraire.  
  
     Les procédures suivantes décrivent comment effectuer chacune d’elles.  
  
#### <a name="to-create-the-required-artifacts"></a>Pour créer les artefacts requis  
  
1.  Dans l’Explorateur Windows, accédez à C:\HowTos.  
  
2.  Créer un nouveau document texte nommé OrderDocEnvelope.xsd.  
  
3.  Ouvrez le schéma OrderDocEnvelope.xsd dans le bloc-notes.  
  
4.  Modifier le document en utilisant le code suivant.  
  
    ```  
    <?xml version="1.0" ?>  
    <xs:schema xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns="http://ESB.BizUnit.Map.Test" targetNamespace="http://ESB.BizUnit.Map.Test" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
      <xs:import schemaLocation="GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc" namespace="http://globalbank.esb.dynamicresolution.com/northamericanservices/" />  
      <xs:annotation>  
        <xs:appinfo>  
          <b:schemaInfo is_envelope="yes" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" />  
          <b:references>  
            <b:reference targetNamespace="http://globalbank.esb.dynamicresolution.com/northamericanservices/" />  
          </b:references>  
        </xs:appinfo>  
      </xs:annotation>  
      <xs:element name="OrderEnvelope">  
        <xs:annotation>  
          <xs:appinfo>  
            <b:recordInfo body_xpath="/*[local-name()='OrderEnvelope' and namespace-uri()='http://ESB.BizUnit.Map.Test']" />  
          </xs:appinfo>  
        </xs:annotation>  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element ref="ns0:OrderDoc" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:schema>  
    ```  
  
5.  Enregistrer OrderDocEnvelope.xsd en UTF-8, puis fermez le bloc-notes.  
  
6.  Dans le dossier C:\HowTos, créez un nouveau document texte nommé Batch.xml.  
  
7.  Dans le bloc-notes, ouvrez Batch.xml.  
  
8.  Modifier le document en utilisant le code suivant.  
  
    ```  
    <?xml version="1.0" ?>  
    <ns0:OrderEnvelope xmlns:ns0="http://ESB.BizUnit.Map.Test">  
      <ns0:OrderDoc xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/">  
        <ns0:customerName>GlobalBankWest</ns0:customerName>  
        <ns0:ID>ns0:ID_0</ns0:ID>  
        <ns0:requestType>10</ns0:requestType>  
      </ns0:OrderDoc>  
      <ns0:OrderDoc xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/">  
        <ns0:customerName>GlobalBankEast</ns0:customerName>  
        <ns0:ID>ns0:ID_0</ns0:ID>  
        <ns0:requestType>11</ns0:requestType>  
      </ns0:OrderDoc>  
      <ns0:OrderDoc xmlns:ns0="http://globalbank.esb.dynamicresolution.com/northamericanservices/">  
        <ns0:customerName>GlobalBankEast</ns0:customerName>  
        <ns0:ID>ns0:ID_0</ns0:ID>  
        <ns0:requestType>12</ns0:requestType>  
      </ns0:OrderDoc>  
    </ns0:OrderEnvelope>  
    ```  
  
9. Enregistrez et fermez Batch.xml.  
  
#### <a name="to-add-a-schemas-project-to-the-patterns-solution"></a>Pour ajouter un projet de schémas à la solution de modèles  
  
1.  Dans Visual Studio, ouvrez C:\HowTos\Patterns\Patterns.sln.  
  
2.  Dans l’Explorateur de solutions, cliquez sur **Solution « Modèles »**, pointez sur **ajouter**, puis cliquez sur **nouveau projet**.  
  
3.  Dans le **ajouter un nouveau projet** boîte de dialogue, dans le volet types de projet, cliquez sur **projets BizTalk**, puis procédez comme suit :  
  
    1.  Dans le volet Modèles, cliquez sur **projet BizTalk Server vide**.  
  
    2.  Dans le **nom** , tapez **Patterns.Schemas**, puis cliquez sur **OK**.  
  
4.  Dans l’Explorateur de solutions, cliquez sur **Patterns.Schemas**, puis cliquez sur **propriétés**.  
  
5.  Dans la fenêtre Propriétés, sur le **signature** onglet, sélectionnez le **signer l’assembly** case à cocher.  
  
6.  Dans le **choisir un fichier de clé de nom fort** la liste déroulante, cliquez sur  **\<nouveau... \>**.  
  
7.  Dans le **créer une clé de nom fort** boîte de dialogue zone, configurez les propriétés suivantes :  
  
    1.  Dans le **nom de fichier de clé** , tapez **fractionnement**.  
  
    2.  Désactivez le **protéger mon fichier de clé avec un mot de passe** case à cocher, puis cliquez sur **OK**.  
  
8.  Dans la fenêtre Propriétés, sur le **déploiement** sous l’onglet du **nom de l’Application** , tapez **Microsoft.Practices.ESB**.  
  
9. Fermez la fenêtre Propriétés.  
  
#### <a name="to-add-the-artifacts-to-the-schemas-project"></a>Pour ajouter les artefacts de projet de schémas  
  
1.  Dans l’Explorateur de solutions, cliquez sur **Patterns.Schemas**, puis cliquez sur **ajouter une référence**.  
  
2.  Sur le **Parcourir** onglet de la **ajouter une référence** boîte de dialogue, recherchez et sélectionnez C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB. DynamicResolution.Schemas\bin\Debug\GlobalBank.ESB.DynamicResolution.Schemas.dll, puis cliquez sur **OK**.  
  
3.  Dans l’Explorateur de solutions, cliquez sur **Patterns.Schemas**, pointez sur **ajouter**, puis cliquez sur **élément existant**.  
  
4.  Dans le **ajouter un élément existant** boîte de dialogue, recherchez et sélectionnez C:\HowTos\OrderDocEnvelope.xsd, puis cliquez sur **ajouter**.  
  
5.  Enregistrez tous les artefacts de solution.  
  
6.  Dans l’Explorateur de solutions, cliquez sur **Patterns.Schemas**, puis cliquez sur **déployer**.  
  
    > [!NOTE]
    >  Cette rubrique utilise la même stratégie de règles d’entreprise et les itinéraires comme ceux créés dans le [Comment : sélectionner un itinéraire à l’aide d’une stratégie de règles d’entreprise](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md) rubrique. Si vous n’avez pas encore effectué de cette section, effectuez les étapes supplémentaires suivantes. Si vous avez terminé cette section, passez directement à la section « Étapes ».  
  
#### <a name="to-create-a-business-rules-engine-bre-policy-to-select-an-itinerary-using-custom-message-properties"></a>Pour créer une stratégie du moteur de règles d’entreprise (BRE) pour sélectionner un itinéraire à l’aide des propriétés de message personnalisées  
  
1.  Cliquez sur **Démarrer** dans la barre des tâches, pointez sur **tous les programmes**, pointez sur **BizTalk Server**, puis cliquez sur **Éditeur des règles d’entreprise**.  
  
2.  Dans l’Explorateur de stratégies, cliquez sur **stratégies**, puis cliquez sur **ajouter une nouvelle stratégie**. Nom de la stratégie **ResolveItineraryBasedOnCustomer**.  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-west"></a>Pour ajouter une règle de sélection pour le client GlobalBank West  
  
1.  Dans le **ResolveItineraryBasedOnCustomer** stratégie, avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **ajouter une nouvelle règle**. Nommez la règle **SetGlobalBankWestItinerary**.  
  
2.  Dans l’Explorateur de faits, cliquez sur le **schémas XML** droit **schémas**, puis cliquez sur **Parcourir**.  
  
3.  Dans le **les fichiers de schéma** boîte de dialogue, accédez à C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB. DynamicResolution.Schemas, sélectionnez NAOrderDoc.xsd, puis cliquez sur **ouvrir**.  
  
    > [!NOTE]
    >  Voici le schéma qui définit le message NAOrderDoc.xml, qui a été utilisé pour créer les messages ouest / est que vous allez utiliser pour le test.  
  
4.  Dans l’Explorateur de faits, cliquez sur NAOrderDoc.xsd, cliquez sur le **Type de Document** propriété dans le volet Propriétés, puis tapez **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.  
  
    > [!NOTE]
    >  Il s’agit du nom qualifié complet du schéma.  
  
5.  Dans l’Explorateur de faits, développez **NAOrderDoc.xsd**, puis développez **OrderDoc**.  
  
6.  Dans la fenêtre de la règle, cliquez sur **Conditions**, pointez sur **prédicats**, puis cliquez sur **égal**.  
  
7.  Dans l’Explorateur de faits, faites glisser le **customerName** élément à la **argument1** nœud sous **Conditions**.  
  
8.  Cliquez sur le **argument2** nœud, puis tapez **GlobalBankWest**.  
  
9. Dans l’Explorateur de faits, cliquez sur le **vocabulaires** onglet. Développez le **ESB. Feuille de route** vocabulaire, développez **Version 1.1**, puis faites glisser le **définir un nom de feuille de route** définition **Actions**.  
  
10. Cliquez sur  **\<une chaîne vide\>**  , puis tapez **GlobalBankWestItinerary**.  
  
    > [!NOTE]
    >  Plus loin dans cette rubrique, vous allez créer cette feuille de route pour traiter les messages de GlobalBank West.  
  
#### <a name="to-add-a-selection-rule-for-customer-globalbank-east"></a>Pour ajouter une règle de sélection pour le client est de GlobalBank  
  
1.  Dans l’Explorateur de stratégies, cliquez sur le **SetGlobalBankWestItinerary** de règle, puis cliquez sur **copie**.  
  
2.  Avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **coller**.  
  
3.  Dans le **nom de la nouvelle règle** boîte de dialogue, tapez **SetGlobalBankEastItinerary**, puis cliquez sur **OK**.  
  
4.  Dans l’Explorateur de stratégies, cliquez sur le **SetGlobalBankEastItinerary** règle.  
  
5.  Dans le **Conditions** section, cliquez sur **GlobalBankWest**, puis cliquez sur **réinitialiser l’argument**.  
  
6.  Cliquez sur **argument2**, puis tapez **GlobalBankEast**.  
  
7.  Dans le **Actions** section, cliquez sur **GlobalBankWestItinerary**, puis cliquez sur **réinitialiser l’argument**.  
  
8.  Cliquez sur  **\<une chaîne vide\>**  , puis tapez **GlobalBankEastItinerary.**  
  
    > [!NOTE]
    >  Plus loin dans cette rubrique, vous allez créer cette feuille de route pour traiter les messages à partir de GlobalBank est.  
  
#### <a name="to-publish-and-deploy-the-policy"></a>Pour publier et déployer la stratégie  
  
1.  Dans l’Explorateur de stratégies, sous la **ResolveItineraryBasedOnCustomer** stratégie, cliquez sur **Version 1.0 (non enregistrée)**, puis cliquez sur **publier**.  
  
2.  Dans l’Explorateur de stratégies, sous la **ResolveItineraryBasedOnCustomer** stratégie, cliquez sur **Version 1.0 - publiée**, puis cliquez sur **déployer**.  
  
#### <a name="to-create-an-esb-itinerary-dsl-model-for-globalbank-west-messages"></a>Pour créer un modèle DSL ESB d’itinéraire pour les messages GlobalBank West  
  
1.  Dans **Visual Studio**, ouvrez C:\HowTos\Patterns\Patterns.sln.  
  
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
    >  Cette étape vous permet d’exporter l’itinéraire sur un référentiel central ; itinéraires peuvent être sélectionnés et attachés à partir de ce référentiel lorsque les messages sont reçus. Vous configurerez ultérieurement le composant de pipeline de sélecteur de feuille de route pour utiliser le programme de résolution BRI à évaluer les messages entrants, puis sélectionnez la feuille de route approprié à partir de ce référentiel.  
  
#### <a name="to-define-the-structure-of-the-globalbank-west-itinerary"></a>Pour définir la structure de la feuille de route GlobalBank West  
  
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
  
#### <a name="to-export-the-globalbank-west-model-to-the-itinerary-database"></a>Pour exporter le modèle de GlobalBank West vers la base de données d’itinéraire  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de la **GlobalBankWestItinerary** itinéraire, puis cliquez sur **exporter le modèle**.  
  
    > [!NOTE]
    >  L’itinéraire a été exporté vers la base de données d’itinéraire et peut maintenant être utilisé par le composant de sélecteur d’itinéraire.  
  
2.  Enregistrez tous les artefacts de projet.  
  
#### <a name="to-create-an-esb-itinerary-dsl-model-for-globalbank-east-message"></a>Pour créer un modèle DSL ESB d’itinéraire pour le message de GlobalBank est  
  
1.  Dans **Visual Studio**, ouvrez C:\HowTos\Patterns.sln.  
  
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
  
#### <a name="to-define-the-structure-of-the-globalbank-east-itinerary"></a>Pour définir la structure de la feuille de route GlobalBank est  
  
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
  
#### <a name="to-export-the-globalbank-east-model-to-the-itinerary-database"></a>Pour exporter le modèle GlobalBank est à la base de données d’itinéraire  
  
1.  Dans Visual Studio, cliquez sur l’aire de conception de la **GlobalBankEastItinerary** itinéraire, puis cliquez sur **exporter le modèle**.  
  
    > [!NOTE]
    >  L’itinéraire a été exporté vers la base de données d’itinéraire et peut maintenant être utilisé par le composant de sélecteur d’itinéraire.  
  
2.  Enregistrez tous les artefacts de projet.  
  
## <a name="steps"></a>Étapes  
  
#### <a name="to-create-and-configure-an-esb-on-ramp"></a>Pour créer et configurer un ESB rampe d’entrée  
  
1.  Cliquez sur **Démarrer** dans la barre des tâches, pointez sur **tous les programmes**, pointez sur **BizTalk Server**, puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la Console Administration de BizTalk Server, développez **groupe BizTalk**, développez **Applications**, puis développez **Microsoft.Practices.ESB**.  
  
3.  Avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.  
  
4.  Dans le **sélectionner un Port de réception** boîte de dialogue, cliquez sur **OnRamp.Itinerary**, puis cliquez sur **OK**.  
  
5.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , tapez **OnRamp.Itinerary.HowTo**.  
  
6.  Dans le **Type** la liste déroulante, cliquez sur **fichier** puis cliquez sur **configurer**.  
  
7.  Dans le **propriétés du Transport FILE** boîte de dialogue le **dossier de réception** , tapez **C:\HowTos\DropFolder**, puis cliquez sur **OK**.  
  
#### <a name="to-configure-the-itinerary-selector-pipeline-component"></a>Pour configurer le composant de pipeline du sélecteur de feuille de route  
  
1.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **ItinerarySelectReceiveXml** dans les **pipeline de réception** déroulante liste, puis cliquez sur le bouton de sélection (...).  
  
2.  Utilisez le **configurer le Pipeline** boîte de dialogue pour configurer les éléments suivants **itinéraire sélecteur** les propriétés du composant :  
  
    1.  Cliquez sur le **ItineraryFactKey** propriété, puis tapez **Resolver.Itinerary**.  
  
    2.  Cliquez sur le **ResolverConnectionString** propriété, puis tapez **BRI :\\\policy=ResolveItineraryBasedOnCustomer;useMsg=true;recognizeMessageFormat=true ;**  
  
    3.  Cliquez sur **OK** pour fermer la **configurer le Pipeline** boîte de dialogue.  
  
        > [!NOTE]
        >  Étant donné que cet réception emplacement est désassemblage d’un échange XML, aucune configuration de composant désassembleur XML est nécessaire.  
  
3.  Cliquez sur **OK** pour fermer la **propriétés de l’emplacement de réception** boîte de dialogue.  
  
4.  Dans la Console Administration de BizTalk Server, cliquez sur le **OnRamp.Itinerary.HowTo** emplacement de réception, puis cliquez sur **activer**.  
  
#### <a name="to-test-the-itinerary-selector-and-business-rules"></a>Pour tester le sélecteur d’itinéraire et les règles d’entreprise  
  
1.  Dans l’Explorateur Windows, accédez à C:\HowTos.  
  
2.  Copie (ne déplacez pas) Batch.xml dans le dossier Dossier_dépôt.  
  
3.  Accédez à C:\HowTos\Out. Vérifiez qu’un seul message West%MessageID%.xml et deux messages East%MessageID%.xml ont été écrits dans le répertoire.  
  
    > [!NOTE]
    >  Bien que les messages sont identiques à l’exception de la valeur de l’élément client, ils ont été traités à l’aide d’itinéraires différents, selon la résolution du composant de pipeline sélecteur d’itinéraire.  
  
4.  Dans la Console Administration de BizTalk Server, avec le bouton droit le OnRamp.Itinerary.HowTo l’emplacement de réception, puis cliquez sur Désactiver.  
  
5.  Après le **OnRamp.Itinerary.HowTo** recevoir d’emplacement est désactivée, faites un clic droit, puis cliquez sur **supprimer**. Dans le **emplacement de réception de confirmer la suppression** boîte de dialogue, cliquez sur **Oui**.  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
 Pour plus d'informations, consultez les rubriques connexes suivantes :  
  
-   [Guide pratique pour sélectionner un itinéraire à l’aide d’une stratégie de règles métier](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [Activités de développement](../esb-toolkit/development-activities.md)  
  
-   [Installation et exécution de l’exemple de résolution dynamique](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)  
  
-   [Utilisation de la résolution et du routage dynamiques](../esb-toolkit/using-dynamic-resolution-and-routing.md)  
  
-   [Modèles de routage des messages](../esb-toolkit/message-routing-patterns.md)