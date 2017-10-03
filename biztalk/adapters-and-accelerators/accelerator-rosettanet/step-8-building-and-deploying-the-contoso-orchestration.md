---
title: "Étape 8 : Création et déploiement de l’Orchestration Contoso | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private process tutorial, building solutions
- private process tutorial, deploying solutions
ms.assetid: d350b87a-0e4e-4837-ad39-fb5b1fdc1532
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 706c5ab2b52d30aeedfba7b3e002dc637fcece93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-8-building-and-deploying-the-contoso-orchestration"></a>Étape 8 : Création et déploiement de l’Orchestration Contoso
Au cours de cette étape, vous allez générer le projet Orchestration et le déployer à l'aide de l'Assistant Déploiement BizTalk. Ces opérations ajoutent l'assembly à la base de données de configuration et l'installent dans le GAC (Global Assembly Cache).  
  
### <a name="to-assign-a-strong-name-to-your-assembly"></a>Pour affecter un nom fort à votre assembly  
  
1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet **PrivateResponder** , puis cliquez sur **Propriétés**.  
  
2.  Dans la boîte de dialogue Pages de propriétés de PrivateResponder, sélectionnez **Assembly** dans le volet gauche.  
  
3.  Dans le volet droit, faites défiler l'affichage jusqu'à la section **Nom fort** , cliquez sur le champ situé à droite de **Fichier de clé de l'assembly**, puis cliquez sur le bouton de sélection (**...**).  
  
4.  Recherchez votre dossier de projet, sélectionnez le fichier **FabConPriceAvail.snk** , puis cliquez sur **Ouvrir**.  
  
5.  Dans le volet droit, sélectionnez **Faux** dans la liste déroulante **Temporisation de la signature de l'assembly** .  
  
6.  Cliquez sur **OK** pour enregistrer les modifications.  
  
### <a name="to-build-and-deploy-the-orchestration-project"></a>Pour créer et déployer le projet d'orchestration  
  
1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet **PrivateResponder** , puis cliquez sur **Générer**.  
  
    > [!NOTE]
    >  Vous pouvez ignorer sans risque les avertissements qui se produisent pendant le processus de génération.  
  
2.  Une fois la génération réussie, cliquez à nouveau avec le bouton droit sur le projet, puis cliquez sur **Déployer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 9 : Démarrer l’Orchestration Contoso](../../adapters-and-accelerators/accelerator-rosettanet/step-9-starting-the-contoso-orchestration.md)