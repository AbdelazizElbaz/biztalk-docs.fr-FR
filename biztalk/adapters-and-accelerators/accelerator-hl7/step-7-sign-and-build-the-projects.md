---
title: "Étape 7 : Signer et générer des projets | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, projects
- projects, building
- projects, signing
ms.assetid: b66e4dc1-4ec6-4ec0-a69a-419b116b19c1
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70f77e536da4eb6589823529644e0c4ab7c95cfa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-sign-and-build-the-projects"></a>Étape 7 : Signer et générer des projets
Dans cette étape, vous affectez un nom fort et générez le projet pour générer un assembly qui contient les ressources (le schéma) que vous avez créé dans [étape 6 : valider les schémas](../../adapters-and-accelerators/accelerator-hl7/step-6-validate-the-schemas.md). Cela garantit également qu’il n’y a aucune erreur de compilation dans le travail que vous avez terminé jusqu'à présent.  
  
### <a name="to-sign-the-btahl7-project"></a>Pour signer le projet BTAHL7  
  
1.  Dans l’Explorateur de solutions, cliquez sur **BTAHL7 projet**, puis cliquez sur **propriétés**.  
  
2.  Dans la boîte de dialogue Pages de propriétés de projet BTAHL7, cliquez sur **Assembly**.  
  
3.  Dans le volet droit, faites défiler jusqu'à la **nom fort** , cliquez sur le champ situé à droite de **fichier de clé d’Assembly**, puis cliquez sur le bouton de sélection (...).  
  
4.  Dans la boîte de dialogue de fichier de clé d’Assembly, accédez à  **\<* lecteur*> : \Tutorial\BTAHL7V22Common\key.snk** (tel que créé dans [étape 3 : assigner un nom fort à l’Assembly](../../adapters-and-accelerators/accelerator-hl7/step-3-assign-a-strong-name-to-the-assembly.md)), puis cliquez sur **ouvrir**.  
  
5.  Cliquez sur **OK** pour enregistrer les modifications.  
  
### <a name="to-build-the-btahl7-project"></a>Pour générer le projet BTAHL7  
  
-   Dans l’Explorateur de solutions, cliquez sur **BTAHL7 projet**, puis cliquez sur **déployer**. [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]Compile l’assembly dans un fichier DLL et l’enregistre dans le \< *lecteur*> : \Tutorial\BTAHL7V22Common\Bin\Development dossier.  
  
 Passez à [étape 8 : créer une carte avec le Mappeur BizTalk](../../adapters-and-accelerators/accelerator-hl7/step-8-create-a-map-with-biztalk-mapper.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel d’enrichissement de message](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)