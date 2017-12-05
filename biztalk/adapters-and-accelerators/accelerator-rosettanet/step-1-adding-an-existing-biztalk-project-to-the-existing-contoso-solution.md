---
title: "Étape 1 : Ajout d’un projet BizTalk existant à la Solution Contoso existante | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects, adding to solutions
- private process tutorial, adding projects to solutions
ms.assetid: 9e84d282-01aa-4611-8462-c1acef234042
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 343bdf83d90d38a6fc0c626a65353c0185c43f6c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-adding-an-existing-biztalk-project-to-the-existing-contoso-solution"></a>Étape 1 : Ajout d’un projet BizTalk existant à la Solution Contoso existante
Le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK contient une orchestration de processus privé qui sert d’un bon point de départ lors de la personnalisation de votre propre processus privé. Dans cette étape, vous ajoutez cette orchestration à votre solution et modifiez le nom de l’assembly pour éviter tout conflit avec l’orchestration PrivateResponder installée lors de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] installation. Avant de commencer, ouvrez la solution de Contoso que vous avez créé dans [étape 1 : création d’une BizTalk Solution pour Contoso Price les demandes de disponibilité](../../adapters-and-accelerators/accelerator-rosettanet/step-1-create-new-biztalk-solution-for-contoso-price-and-availability-request.md).  
  
### <a name="to-add-the-privateresponder-project-to-the-contoso-solution"></a>Pour ajouter le projet de PrivateResponder à la solution Contoso  
  
1.  Copiez l’exemple de PrivateResponder SDK dans votre dossier de solution de Contoso.  
  
    > [!NOTE]
    >  Par défaut, l’exemple de PrivateResponder SDK se trouve dans C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\PrivateResponder dossier.  
  
2.  Dans Visual Studio, cliquez sur **fichier**, pointez sur **ajouter**, puis cliquez sur **projet existant**.  
  
3.  Dans la boîte de dialogue Ajouter un projet existant, recherchez le dossier de votre solution, sélectionnez le **PrivateResponder.btproj** fichier de projet, puis cliquez sur **ouvrir**.  
  
### <a name="to-change-the-privateresponder-assembly-name-and-default-namespace"></a>Pour modifier le nom de l’assembly PrivateResponder et par défaut d’espace de noms  
  
1.  Dans l’Explorateur de solutions, avec le bouton droit sur le **PrivateResponder** de projet, puis cliquez sur **propriétés**.  
  
2.  Dans la boîte de dialogue Pages de propriétés de PrivateResponder, dans l’arborescence de la console, cliquez sur **général**. Dans le volet d’informations, dans le **nom de l’Assembly** , tapez **ContosoPriceAndAvailability.PrivateResponder**.  
  
3.  Dans le **par défaut de Namespace** , tapez **ContosoPriceAndAvailability**.  
  
4.  Cliquez sur **OK** pour fermer la boîte de dialogue Pages de propriétés de PrivateResponder.  
  
5.  Dans l'Explorateur de solutions, double-cliquez sur **PrivateResponder.odx**.  
  
6.  Dans le **Vue Orchestration** fenêtre, vérifiez que **propriétés d’Orchestration** (sous **PrivateResponderProcess**) est sélectionné.  
  
7.  Dans le **propriétés** fenêtre, dans le **Namespace** , tapez **ContosoPriceAndAvailability**, puis appuyez sur **entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 2 : Définition et publication du vocabulaire pour Contoso](../../adapters-and-accelerators/accelerator-rosettanet/step-2-defining-and-publishing-the-vocabulary-for-contoso.md)