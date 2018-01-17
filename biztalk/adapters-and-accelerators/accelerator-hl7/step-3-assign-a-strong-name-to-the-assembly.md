---
title: "Étape 3 : Assigner un nom fort à l’Assembly | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies
- message enrichment tutorial, strong name assemblies
- strong name assemblies
ms.assetid: 8709e4e1-b428-42af-ba3c-08225c17a9eb
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57368dbbb2d8ecaa6621707ea7b989bf7f5b005d
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="step-3-assign-a-strong-name-to-the-assembly"></a>Étape 3 : Assigner un nom fort à l’Assembly
Dans cette étape, vous créez et attribuez un nom fort pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] assembly. Un assembly avec nom fort présente plusieurs avantages de sécurité et est nécessaire pour déployer votre projet dans le global assembly cache (GAC). Un nom fort garantit l’unicité de l’assembly en assignant une signature numérique et une paire de clés unique. Cela protège également l’enregistrement en ligne de l’assembly en veillant à ce que personne ne peut générer une version ultérieure de l’assembly. Enfin, un nom fort fournit un contrôle d’intégrité fort pour garantir que le contenu de l’assembly n’a pas modifié, car vous les avez générées.  
  
### <a name="to-assign-a-strong-name-to-the-assembly"></a>Pour attribuer un nom fort à l’assembly  
  
1.  Démarrer **invite de commandes Visual Studio**.  
  
    > [!NOTE]
    >  Si vous avez déjà créé une clé de nom fort, vous pouvez la réutiliser.  
  
2.  À l’invite de commandes, accédez au**\<*lecteur*\>: \Tutorial\BTAHL7V22Common** (où \< *lecteur* \> est lettre de lecteur de votre installation), puis appuyez sur **entrée**.  
  
3.  À l’invite de commandes, tapez **sn – k key.snk**, puis appuyez sur **entrée**. Un message s’affiche indiquant que [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] écriture de la paire de clés dans le fichier de clé key.snk.  
  
4.  Dans l’Explorateur de solutions, cliquez sur le **BTAHL7V22Common** de projet, puis cliquez sur **propriétés**.  
  
5.  Dans la boîte de dialogue Pages de propriétés BTAHL7V22Common, cliquez sur **Assembly**.  
  
6.  Dans le volet droit, faites défiler jusqu'à la **nom fort** , cliquez sur le champ situé à droite de **fichier de clé d’Assembly**, puis cliquez sur le bouton de sélection (...).  
  
7.  Dans la boîte de dialogue de fichier de clé d’Assembly, accédez à  **\< *lecteur*\>: \Tutorial\BTAHL7V22Common\key.snk**, cliquez sur **ouvrez**, puis cliquez sur **OK**.  
  
8.  Dans l’Explorateur de solutions, cliquez sur **BTAHL7V22Common**, puis cliquez sur **déployer**. [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]Crée un assembly que vous pouvez référencer à partir de votre prochain projet.  
  
9. Répétez les étapes 4 à 8 pour le projet BTAHL7V2XCommon.  
  
 Passez à [étape 4 : créer les schémas](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-schemas.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel sur l’enrichissement des messages](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)