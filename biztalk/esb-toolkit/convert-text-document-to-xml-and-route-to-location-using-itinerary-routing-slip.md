---
title: "Comment : convertir un Document texte XML et d’itinéraire vers un emplacement de fichier à l’aide d’une feuille de route bordereau | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01597a5f-5ca3-440e-ad97-70332233f319
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ba308473568c222559ccc799faf3233478ee490
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-convert-a-text-document-to-xml-and-route-to-a-file-location-using-an-itinerary-routing-slip"></a>Comment : convertir un Document texte XML et d’itinéraire vers un emplacement de fichier à l’aide d’un bon d’itinéraire de routage
## <a name="goal"></a>Objectif  
 La section explique comment créer un pipeline qui sera convertir un document texte XML puis sélectionnez la feuille de route appropriée et acheminer le message vers un emplacement de fichier.  
  
 Dans cette rubrique, vous effectuerez les étapes suivantes :  
  
-   Utilisez un pipeline pour recevoir un document de fichier plat et la convertir en XML.  
  
-   Configurer le composant de pipeline de sélecteur de feuille de route pour résoudre le bordereau de routage approprié.  
  
-   Créer une rampe d’entrée qui utilise le pipeline personnalisé.  
  
-   Testez le routage basé sur l’itinéraire d’un message de fichier plat.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Effectuez les tâches suivantes avant d’effectuer les étapes plus loin dans cette rubrique :  
  
-   Déployer le **DataFormatTransformation** itinéraire.  
  
-   Créer le message de test.  
  
 Les procédures suivantes décrivent comment effectuer chacune d’elles.  
  
#### <a name="to-deploy-the-dataformattransformation-itinerary"></a>Pour déployer l’itinéraire DataFormatTransformation  
  
1.  Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation\DataFormatTransformation.sln.  
  
2.  Dans l’Explorateur de solutions, dans le **Itinerary.Library** de projet, double-cliquez sur **DataFormatTransformation.itinerary** pour l’ouvrir dans le Concepteur d’itinéraire.  
  
3.  Dans Visual Studio, cliquez sur l’aire de conception de **DataFormatTransformation.itinerary**. Dans le **DataFormatTransformation.itinerary** fenêtre Propriétés, configurez les propriétés suivantes :  
  
    1.  Dans le **état de la feuille de route** la liste déroulante, cliquez sur **déployées**.  
  
    2.  Dans le **modèle exportateur** la liste déroulante, cliquez sur **exportateur de feuille de route de base de données**.  
  
    3.  Cliquez sur le bouton de sélection (...) à côté du **base de données de la feuille de route** propriété.  
  
    4.  Dans le **propriétés de connexion** boîte de dialogue, choisissez le serveur SQL qui héberge la base de données de référentiel d’itinéraire, puis spécifiez le nom de la base de données (le nom par défaut est **EsbItineraryDb**).  
  
4.  Enregistrez tous les artefacts de projet.  
  
5.  Dans Visual Studio, cliquez sur l’aire de conception de la **DataModelTransformation** itinéraire, puis cliquez sur **exporter le modèle**.  
  
#### <a name="to-create-the-receive-pipeline"></a>Pour créer le pipeline de réception  
  
1.  Dans Visual Studio, cliquez sur **DataFormatTransformation.Schemas**, puis cliquez sur **propriétés**. Cliquez sur **Application**, puis tapez **GlobalBank.ESB.DataFormatTransformation.Schemas** dans les **nom de l’Assembly** boîte.  
  
2.  Avec le bouton droit **DataFormatTransformation.Schemas**, puis cliquez sur **propriétés**. Cliquez sur **signature**, puis vérifiez que le **signer l’assembly** case à cocher est activée et que l’emplacement de l’assembly pointe vers **.\\... \\.. \\.. \\.. \\.. \keys\Microsoft.Practices.ESB.snk**.  
  
3.  Avec le bouton droit **DataFormatTransformation.Pipelines**, puis cliquez sur **supprimer**.  
  
4.  Avec le bouton droit **DataFormatTransformation**, pointez sur **ajouter**, puis cliquez sur **nouveau projet**. Cliquez sur **projets Biztalk**, puis cliquez sur **projet Biztalk Server vide**. Dans le **nom** , tapez **DataFormatTransformationReceive.Pipeline**.  
  
5.  Avec le bouton droit **DataFormatTransformationReceive.Pipeline**, puis cliquez sur **propriétés**. Cliquez sur **signature**, puis vérifiez que le **signer l’assembly** case à cocher est activée et que l’emplacement de l’assembly pointe vers **C:\projects\Microsoft.Practices.ESB\keys\ Microsoft.Practices.ESB.snk**.  
  
6.  Avec le bouton droit **DataFormatTransformationReceive.Pipeline**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
7.  Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **Pipeline de réception** dans le volet Modèles. Dans le **nom** , tapez **ItinerarySelectReceiveFF**, puis cliquez sur **ajouter**.  
  
8.  Avec le bouton droit **références** pour le projet de DataFormatTransformationReceive.Pipeline, puis cliquez sur **ajouter une référence**. Cliquez sur le **projets** onglet, puis cliquez sur **DataFormatTransformation.Schemas**. Cliquez sur **OK** pour ajouter la référence.  
  
9. Dans la boîte à outils, faites glisser un **désassembleur de fichier plat** composant de pipeline pour le **désassembler** étape du pipeline.  
  
10. Dans la fenêtre Propriétés pour le fichier plat désassembler, cliquez sur **DataModelTransformation.Schemas.NAOrderDocFF** dans les **schéma de Document** liste déroulante.  
  
11. Dans la boîte à outils, faites glisser un **ESB itinéraire sélecteur** composant de pipeline pour le **résoudre le tiers** étape du pipeline.  
  
12. À partir de la boîte à outils, faites glisser un **ESB répartiteur** composant de pipeline le **résoudre le tiers** étape du pipeline, puis placez-le sous le **ESB itinéraire sélecteur** pipeline composant.  
  
13. Enregistrez tous les artefacts de projet.  
  
## <a name="to-create-the-test-message"></a>Pour créer le message de test  
  
1.  Cliquez une fois dans le fichier de schéma NAOrderDocFF.xsd du projet DataFormatTransformation.Schemas. Dans le volet Propriétés de Visual Studio, modifiez les deux propriétés suivantes :  
  
    -   **Générer le Type d’Instance de sortie**. Cliquez sur la liste déroulante de cette propriété pour la remplacer par **natif**.  
  
    -   **Nom du fichier de l’Instance de sortie**. Cliquez sur le bouton de sélection (...) pour cette propriété et acceptez le chemin d’accès par défaut de C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation. Dans le **nom de fichier** , tapez **NAOrderDocFF**, puis cliquez sur **enregistrer**.  
  
2.  Avec le bouton droit **NAOrderDocFF.xsd** sous **DataFormatTransformation.Schemas**, puis cliquez sur **générer l’Instance**. À ce stade, vous devez générer un nouveau fichier dans le répertoire C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation.  
  
3.  Copie (ne déplacez pas) le fichier NAOrderDocFF.txt à partir de C:\Projects\Microsoft.Practices.ESB\Source\Samples\DataFormatTransformation à C:\HowTos.  
  
    > [!NOTE]
    >  Voici le message sera reçu et convertir au format XML. Ce document représente une version de fichier plat de la commande en Amérique du Nord.  
  
## <a name="steps"></a>Étapes  
  
#### <a name="to-deploy-the-receive-pipeline-and-the-schema"></a>Pour déployer le pipeline de réception et le schéma  
  
1.  Avec le bouton droit **DataFormatTransformationReceive.Pipeline**, puis cliquez sur **propriétés**. Cliquez sur **déploiement**, puis tapez **Microsoft.Practices.ESB** dans les **nom de l’Application** boîte.  
  
2.  Cliquez sur le **DataFormatTransformation.Schemas** de projet, puis cliquez sur **propriétés**. Cliquez sur **déploiement**, puis tapez **Microsoft.Practices.ESB** dans les **nom de l’Application** boîte.  
  
3.  Fermer les volets de propriétés pour les deux **DataFormatTransformationReceive.Pipeline** et **DataFormatTransformation.Schemas**.  
  
4.  Dans l’Explorateur de solutions, cliquez sur le **DataFormatTransformation** de projet, puis cliquez sur **déployer la Solution**.  
  
#### <a name="to-create-and-configure-an-esb-on-ramp"></a>Pour créer et configurer un ESB rampe d’entrée  
  
1.  Cliquez sur **Démarrer** dans la barre des tâches, pointez sur **tous les programmes**, pointez sur  **[!INCLUDE[prague](../includes/prague-md.md)]** , puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans le [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration, développez **groupe BizTalk**, développez **Applications**, puis cliquez sur **Microsoft.Practices.ESB**.  
  
3.  Avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.  
  
4.  Dans le **sélectionner un Port de réception** boîte de dialogue, cliquez sur **OnRamp.Itinerary**, puis cliquez sur **OK**.  
  
5.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , tapez **OnRamp.Itinerary.FlatFile.FILE**.  
  
6.  Dans le **Type** la liste déroulante, cliquez sur **fichier**, puis cliquez sur **configurer**.  
  
7.  Dans le **propriétés du Transport FILE** boîte de dialogue le **dossier de réception** , tapez **C:\HowTos\DropFolder**.  
  
8.  Dans le **propriétés du Transport FILE** boîte de dialogue le **masque de fichier** , tapez  **\*.txt**, puis cliquez sur **OK**.  
  
#### <a name="to-configure-the-itinerary-selector-pipeline-component"></a>Pour configurer le composant de pipeline du sélecteur de feuille de route  
  
1.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **ItinerarySelectReceiveFF** dans les **pipeline de réception** zone de liste déroulante, puis cliquez sur le bouton de sélection (...).  
  
2.  Utilisez le **configurer le Pipeline** boîte de dialogue pour configurer les éléments suivants **itinéraire sélecteur** les propriétés du composant :  
  
    1.  Cliquez sur le **ItineraryFactKey** propriété, puis tapez **Resolver.Itinerary**.  
  
    2.  Cliquez sur le **ResolverConnectionString** , tapez **itinéraire :\\\name=DataFormatTransformation ;** puis cliquez sur **OK**.  
  
3.  Cliquez sur **OK** pour fermer la **propriétés de l’emplacement de réception** boîte de dialogue.  
  
4.  Dans le [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration, avec le bouton droit le **OnRamp.Itinerary.FlatFile.FILE** emplacement de réception, puis cliquez sur **activer**.  
  
#### <a name="to-test-itinerary-based-routing-of-a-flat-file-message"></a>Pour tester le routage basé sur l’itinéraire d’un message de fichier plat  
  
1.  Dans l’Explorateur Windows, accédez à C:\HowTos.  
  
2.  Copie (ne déplacez pas) NAOrderDocFF.txt à C:\HowTos\DropFolder.  
  
3.  Accédez à C:\HowTos\Out. Vérifiez que le message DFT%MessageID%.xml a été écrit dans le répertoire.  
  
4.  Dans le [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration, avec le bouton droit le **OnRamp.Itinerary.FlatFile.FILE** emplacement de réception, puis cliquez sur **désactiver**.  
  
5.  Après le **OnRamp.Itinerary.FlatFile.FILE** recevoir d’emplacement est désactivée, faites un clic droit, puis cliquez sur **supprimer**. Dans le **emplacement de réception de confirmer la suppression** boîte de dialogue, cliquez sur **Oui**.  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
 Pour plus d'informations, consultez les rubriques connexes suivantes :  
  
-   [Comment : transformer un Message et router le Message résultant à un emplacement de fichier à l’aide d’un bon d’itinéraire de routage](../esb-toolkit/transform-message-and-route-the-message-to-a-location-using-itinerary-routing.md)  
  
-   [Comment : router un Message unique à plusieurs destinataires à l’aide d’un bon d’itinéraire de routage](../esb-toolkit/route-a-single-message-to-multiple-recipients-using-an-itinerary-routing-slip.md)  
  
-   [Activités de développement](../esb-toolkit/development-activities.md)  
  
-   [Modèles de Transformation de messages](../esb-toolkit/message-transformation-patterns.md)