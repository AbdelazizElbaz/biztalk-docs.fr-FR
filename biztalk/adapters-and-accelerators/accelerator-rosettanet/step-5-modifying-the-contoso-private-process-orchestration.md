---
title: "Étape 5 : Modification de l’Orchestration de processus de privé Contoso | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private processes, orchestrations
- private process tutorial, modifying private process orchestration
ms.assetid: a5430db8-e5f0-48a6-abb9-e268d8ec2ec4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42c93a10fd4751f32aadf2cbfa0a0bbbafc6c7bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-modifying-the-contoso-private-process-orchestration"></a>Étape 5 : Modification de l’Orchestration de processus de privé de Contoso
Dans cette étape, vous modifiez l’orchestration de processus privé à intégrer avec le système de planification ERP (Enterprise Resource) pour Contoso. Le système ERP de Contoso utilise les schémas définies en interne pour la disponibilité et le prix du produit. En personnalisant le processus privé pour le 3A2 - prix et la disponibilité des processus PIP (Partner Interface), vous serez en mesure d’intégrer le système ERP à l’aide des informations de mappage de schéma.  
  
### <a name="to-add-a-reference-to-the-contoso-priceandavailability-and-rnpips-assemblies"></a>Pour ajouter une référence aux assemblys Contoso PriceAndAvailability et RNPIPs  
  
1.  Avec la solution Contoso est affichée dans l’Explorateur de solutions, cliquez sur le **PrivateResponder** de projet, puis cliquez sur **ajouter une référence**.  
  
2.  Dans la boîte de dialogue Ajouter une référence, cliquez sur **Parcourir**. Déplacer vers  *\<lecteur >*: \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\Bin dossier et sélectionnez les assemblys suivants**:**  
  
    -   Microsoft.Solutions.BTARN.CommonTypes.dll  
  
    -   Microsoft.Solutions.BTARN.ConfigurationManager.dll  
  
    -   Microsoft.Solutions.BTARN.GlobalSchemas.dll  
  
    -   Microsoft.Solutions.BTARN.PublicResponder.dll  
  
    -   Microsoft.Solutions.BTARN.Schemas.RNPIPs.dll  
  
    -   Microsoft.Solutions.BTARN.Shared.dll  
  
    -   Microsoft.Solutions.BTARN.XSDClasses.GlobalSchemas.dll  
  
3.  Cliquez sur **Ajouter**.  
  
4.  Dans la boîte de dialogue Ajouter une référence, cliquez sur le **projets** onglet, sélectionnez le **ContosoPriceAndAvailability** et **HeaderHelper** projets, puis cliquez sur  **Ajouter**.  
  
5.  Cliquez sur **OK**.  
  
6.  Dans la boîte de dialogue environnement de développement Microsoft, cliquez sur **OK**.  
  
### <a name="to-create-new-message-types"></a>Pour créer des types de message  
  
1.  Dans l’Explorateur de solutions, double-cliquez sur le **PrivateResponder** orchestration pour l’ouvrir.  
  
2.  Dans l’Explorateur de solutions, cliquez sur **Vue Orchestration**.  
  
3.  Dans la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.  
  
4.  Dans la fenêtre Propriétés, dans le **identificateur** , tapez **PIP3A2RequestMessage**.  
  
5.  Dans le **Type de Message** , cliquez sur la flèche déroulante, développez **schémas**, puis sélectionnez  **\<sélectionner dans l’assembly référencé >**.  
  
6.  Dans la zone Sélectionner le Typedialog artefact, sélectionnez **Microsoft.Solutions.BTARN.Schemas.RNPIPs** dans le volet gauche, sélectionnez **_3A2PriceAndAvailabilityQueryMessageGuideline_v1_3** dans le volet droit, et puis cliquez sur **OK**.  
  
7.  Répétez les étapes 3 à 6 pour créer tous les types de message pour la solution en utilisant les informations suivantes :  
  
    |Identificateur|Assembly|Type de message|  
    |----------------|--------------|------------------|  
    |PIP3A2ResponseMessage|Microsoft.Solutions.BTARN.<br />Schemas.RNPips|_3A2PriceAndAvailability<br />ResponseMessageGuideline_v1_3|  
    |Contoso3A2ResponseMessage|ContosoPriceAndAvailability|rootPriceResponse|  
    |Contoso3A2RequestMessage|ContosoPriceAndAvailability|rootPriceRequest|  
  
8.  Vous avez terminé la création des types de message pour la solution.  
  
### <a name="to-create-new-variables"></a>Pour créer de nouvelles variables  
  
1.  Dans la vue Orchestration, cliquez sur **Variables,** puis cliquez sur **nouvelle Variable**.  
  
2.  Dans la fenêtre Propriétés, dans le **identificateur** , tapez **contosoResponseXML**.  
  
3.  Dans le **Type** boîte, sélectionnez  **\<classe .NET >** dans la liste déroulante.  
  
4.  Dans l’artefact sélectionnez Tapez boîte de dialogue, dans le volet gauche, sous la **projet actuel** et **références** nœuds, sélectionnez **System.Xml**, sélectionnez  **XmlDocument** à partir de la liste dans le volet droit, puis cliquez sur **OK**.  
  
5.  Dans **Vue Orchestration**, cliquez sur **Variables**, puis cliquez sur **nouvelle Variable**.  
  
6.  Dans la fenêtre Propriétés, dans le **identificateur** , tapez **submitMessage**.  
  
7.  Dans le **Type** boîte, sélectionnez  **\<classe .NET >** dans la liste déroulante.  
  
8.  Dans la boîte de dialogue Sélectionner le Type d’artefact dans le volet gauche, développez **projet actuel** et **références** nœuds, sélectionnez **Microsoft.Solutions.BTARN.Shared**, sélectionnez  **SubmitRNIF** à partir de la liste dans le volet droit, puis cliquez sur **OK**.  
  
### <a name="to-change-the-orchestration-filter-expression"></a>Pour modifier l’expression de filtre d’orchestration  
  
1.  Dans le Concepteur d’Orchestration, sélectionnez la **ReceiveFromPublicProcessResponder** forme.  
  
2.  Dans la fenêtre Propriétés, dans le **Expression de filtre** zone, cliquez sur la zone de valeur, puis cliquez sur le bouton de sélection (**...** ) pour ouvrir la boîte de dialogue Expression de filtre.  
  
3.  Dans la boîte de dialogue Expression de filtre dans le **Group By** , cliquez sur le **ou** valeur sur la première ligne, puis sélectionnez **et** dans la liste déroulante.  
  
4.  Dans la boîte de dialogue Expression de filtre, cliquez sur **cliquez ici pour ajouter une nouvelle ligne**, puis sélectionnez **Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode** dans la liste déroulante.  
  
5.  Dans la même ligne, cliquez sur **valeur**, puis tapez dans **« 3A2 »**.  
  
6.  Dans la même ligne, cliquez sur **AND** dans les **Group By** zone, puis sélectionnez **ou** dans la liste déroulante.  
  
7.  Dans la boîte de dialogue Expression de filtre, sélectionnez la ligne que vous venez de créer, puis cliquez sur une fois le bouton de flèche haut pour déplacer la ligne qu’une seule fois.  
  
8.  Cliquez sur **cliquez ici pour ajouter une nouvelle ligne**, puis sélectionnez **Microsoft.Solutions.BTARN.GlobalSchemas.SCPIPCode** dans la liste déroulante.  
  
9. Dans la même ligne, cliquez sur **valeur**, puis tapez dans **« 3A2 »**.  
  
10. Cliquez sur OK.  
  
### <a name="to-modify-the-business-process-workflow"></a>Pour modifier le workflow de processus d’entreprise  
  
1.  Faites glisser un **assignation du Message** mettre en forme à partir de la boîte à outils vers l’aire de conception et déposez-le sous le **ReceiveFromPublicProcessResponder** forme. Sélectionnez le **ConstructMessage_1** forme qui a été créé et dans le **propriétés** fenêtre, dans le **nom** , tapez **ConstructPIP3A2RequestMessage** .  
  
2.  Faites glisser un **transformer** forme sur l’aire de conception et déposez-le sous le **ConstructPIP3A2RequestMessage** forme. Sélectionnez le **ConstructMessage_1** forme qui a été créé et dans le **propriétés** fenêtre, dans le **nom** , tapez **ConstructContoso3A2RequestMessage** .  
  
3.  Faites glisser un **envoyer** forme sur l’aire de conception et déposez-le sous le **ConstructContoso3A2RequestMessage** forme.  
  
4.  Faites glisser un **réception** forme sur l’aire de conception et déposez-le sous le **Send_1** forme.  
  
5.  Dans l’aire de conception d’orchestration, cliquez sur une zone vide.  
  
6.  Dans la fenêtre Propriétés, sélectionnez le **Type de Transaction** propriété, puis cliquez sur **Long terme**.  
  
7.  Faites glisser un **étendue** forme sur l’aire de conception et déposez-le sous le **Receive_1** forme.  
  
8.  Dans la fenêtre Propriétés, à partir de la **Type de Transaction** liste déroulante de propriétés, sélectionnez **atomique** pour le **étendue** forme.  
  
9. Faites glisser un **appeler règles** forme sur l’aire de conception et déposez-la sur l’étiquette indiquant que **déposez une forme à partir de la boîte à outils ici** à l’intérieur de la **étendue** forme. Dans la fenêtre Propriétés pour le **appeler règles** mettre en forme, dans le **nom** , tapez **Execute3A2Vocabulary**.  
  
10. Faites glisser un **transformer** forme sur l’aire de conception et déposez-le sous le **Scope_1** forme. Cliquez sur le **ConstructMessage_1** forme. Dans la fenêtre Propriétés, dans le **nom** , tapez **Construct3A2ResponseMessage**.  
  
11. Faites glisser un **Expression** forme sur l’aire de conception et déposez-le sous le **Construct3A2ResponseMessageTransform** forme.  
  
12. Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier**, cliquez sur **Enregistrer tout** pour enregistrer le projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 6 : Configuration des formes d’Orchestration (Contoso)](../../adapters-and-accelerators/accelerator-rosettanet/step-6-configuring-orchestration-shapes-contoso.md)