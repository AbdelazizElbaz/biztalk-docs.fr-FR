---
title: "Étape 3 : Création d’une Application métier Contoso est mappé pour le prix et la disponibilité du projet à l’aide du mappeur de BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: private process tutorial, creating LOB maps
ms.assetid: a947e0ac-f0cb-4be9-85a8-09daf3675b1a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3478997abd4e5bb15bfeb977e05ca3edc7348e0a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-creating-the-contoso-lob-application-maps-for-the-price-and-availability-project-using-biztalk-mapper"></a>Étape 3 : Créer les mappages d’applications métier Contoso pour le prix et le projet de disponibilité à l’aide du Mappeur BizTalk
Dans cette étape, vous créez deux mappages qui définissent la transformation nécessaire pour échanger les messages entre les deux partenaires commerciaux. Pour ce scénario, le système ERP de Contoso a déjà standardisé en un format de message pour une demande de prix et de disponibilité. Les deux cartes mappera les messages de demande et de réponse du partenaire commercial, Fabrikam, vers et depuis ces messages définies par l’utilisateur de Contoso, respectivement.  
  
### <a name="to-add-a-reference-for-the-3a2-priceandavailability-request-schema"></a>Pour ajouter une référence pour le schéma de demande de PriceAndAvailability 3A2  
  
1.  Dans l’Explorateur de solutions, cliquez sur le projet ContosoPriceAndAvailability, puis cliquez sur **ajouter une référence**.  
  
2.  Dans la boîte de dialogue Ajouter une référence, cliquez sur **Parcourir**.  
  
3.  Déplacer vers le dossier  *\<lecteur >*: \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\Bin, puis sélectionnez le **Microsoft.Solutions.BTARN.Schemas.RNPIPs.dll**  assembly.  
  
4.  Cliquez sur **ajouter**, puis cliquez sur **OK**.  
  
### <a name="to-create-the-3a2-priceandavailability-request-to-contoso-priceandavailability-request-map"></a>Pour créer la demande de PriceAndAvailability 3A2 au mappage de demande de Contoso PriceAndAvailability  
  
1.  Dans l’Explorateur de solutions, cliquez sur le projet ContosoPriceAndAvailability, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans l’ajouter un nouvel élément - ContosoPriceAndAvailability boîte de dialogue, sélectionnez **les fichiers de mappage** dans le volet des catégories, puis sélectionnez **carte** dans les **modèles** volet. Dans le **nom** , tapez **PIP3A2RequestToContosoPriceRequest**, puis cliquez sur **ajouter**.  
  
### <a name="to-associate-the-schemas-for-the-pip3a2requesttocontosopricerequest-map"></a>Pour associer les schémas de la carte PIP3A2RequestToContosoPriceRequest  
  
1.  Dans le Mappeur BizTalk (avec PIP3A2RequestToContosoPriceRequest.btm affiché), dans le volet Schéma Source, cliquez sur **ouvrir le schéma Source**.  
  
2.  Dans la boîte de dialogue Sélecteur de Type BizTalk, développez **ContosoPriceAndAvailability**, développez **références**, développez **Microsoft.Solutions.BTARN.Schemas.RNPIPs**, puis Développez **schémas.**  
  
3.  Sélectionnez **Microsoft.Solutions.BTARN.Schemas.RNPIPs.**  
  
     **_3A2PriceAndAvailabilityQueryMessageGuideline_v1_3**, puis cliquez sur **OK**.  
  
4.  Dans le volet Schéma de Destination, cliquez sur **ouvrir le schéma de Destination**.  
  
5.  Dans la boîte de dialogue Sélecteur de Type BizTalk, développez **ContosoPriceAndAvailability**, puis développez **schémas**.  
  
6.  Sélectionnez le **ContosoPriceAndAvailability.ContosoPriceSchema** schéma, puis cliquez sur **OK**.  
  
7.  Dans le nœud racine de la boîte de dialogue de schéma cible, sélectionnez le **rootPriceRequest** schéma, puis cliquez sur **OK**.  
  
### <a name="to-link-schema-fields-in-the-pip3a2requesttocontosopricerequest-map"></a>Pour lier des champs de schéma dans le mappage de PIP3A2RequestToContosoPriceRequest  
  
1.  Dans le volet Schéma de Destination, cliquez sur le  **\<schéma >** nœud, puis cliquez sur **développer le nœud d’arborescence**.  
  
2.  Dans le volet Schéma Source, cliquez sur le  **\<schéma >** nœud, puis cliquez sur **développer le nœud d’arborescence**.  
  
3.  Faites glisser le **GlobalProductIdentifier** au champ la **ProductID** champ dans le volet Schéma de Destination.  
  
    > [!NOTE]
    >  Vous pouvez trouver la **GlobalProductIdentifier** champ dans le nœud Pip3A2PriceAndAvailabilityQuery/ProductPriceAndAvailabilityQuery /  
    >   
    >  ProductPriceAndAvailability/ProductLineItem/productUnit /  
    >   
    >  ProductPackageDescription/ProductIdentification.  
  
4.  Sur le **fichier** menu, cliquez sur **Enregistrer tout** pour enregistrer vos modifications.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et configuration des Ports BizTalk pour Contoso](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-biztalk-ports-for-contoso.md)