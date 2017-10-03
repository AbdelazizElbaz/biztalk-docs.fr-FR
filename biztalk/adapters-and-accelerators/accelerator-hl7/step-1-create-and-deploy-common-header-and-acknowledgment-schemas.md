---
title: "Étape 1 : Créer et déployer des en-tête commun et schémas d’accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: interrogative tutorial, headers
ms.assetid: e0f11f58-9a8c-4567-a537-3d182fa7dce2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a134071ee1973961e0fb4ed9b4da73ad87d8dbb1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-create-and-deploy-common-header-and-acknowledgment-schemas"></a>Étape 1 : Créer et déployer des en-tête commun et schémas d’accusé de réception
Vous utilisez le schéma d’en-tête pour valider l’en-tête (segment MSH) de l’instance de message. Le schéma d’accusé de réception vous permet de générer l’accusé de réception pour l’instance de message. Ce processus est commun à toutes les versions de schéma HL7.  
  
### <a name="to-create-the-header-and-acknowledgment-schemas"></a>Pour créer les schémas d’en-tête et d’accusé de réception  
  
1.  Démarrez **Microsoft Visual Studio 2012**.  
  
2.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
3.  Dans la boîte de dialogue Nouveau projet, dans le **Types de projets** liste, développez **projets BizTalk**, puis sélectionnez **BTAHL7Projects**.  
  
4.  Dans le **modèles** liste, sélectionnez **BTAHL7V2XCommon projet**.  
  
5.  Dans le **nom** , tapez **Interrogative_2XSchemas**, puis cliquez sur **OK**.  
  
     Dans l’Explorateur de solutions, notez que trois schémas (ACK_24_GLO_DEF.xsd, ACK_25_GLO_DEF.xsd et MSH_25_GLO_DEF.xsd) sont inclus dans le projet.  
  
     Laissez Visual Studio ouvert.  
  
## <a name="step-1a-assign-a-strong-key-to-the-assembly-and-deploy"></a>Étape 1 a : assigner une clé forte à l’Assembly et le déployer  
 Utilisez la procédure suivante pour affecter une clé forte à l’assembly, puis déployer l’assembly.  
  
#### <a name="to-assign-a-strong-key-and-deploy-the-assembly"></a>Pour affecter une clé forte et de déployer l’assembly  
  
1.  Démarrez une **invite de commandes Visual Studio 2012**.  
  
2.  À la [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] invite de commandes, remplacez votre répertoire à la \< *lecteur*> : \Program Files\Microsoft BizTalk \<version > Accelerator pour le dossier du didacticiel de HL7\SDK\Interrogative.  
  
3.  À l’invite de commandes, tapez **sn – k key.snk**, puis appuyez sur **entrée**. Vérifiez qu’un message de réussite s’affiche dans la fenêtre Sortie.  
  
    > [!NOTE]
    >  Si le message approprié n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de votre assembly.  
  
4.  Dans l’Explorateur de solutions, cliquez sur **Interrogative_2XSchemas** de projet, puis cliquez sur **propriétés**.  
  
5.  Dans la boîte de dialogue Pages de propriétés Interrogative_2XSchemas, cliquez sur **Assembly**.  
  
6.  Dans le volet droit, faites défiler jusqu'à la **nom fort** , cliquez sur le champ situé à droite de **fichier de clé d’Assembly**, puis cliquez sur le bouton de sélection (...).  
  
7.  Dans la boîte de dialogue de fichier de clé d’Assembly, accédez à \< *lecteur*> : \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\Interrogative didacticiel, cliquez sur **key.snk**, puis cliquez sur **ouvrir**.  
  
8.  Dans la boîte de dialogue Pages de propriétés Interrogative_2XSchemas, cliquez sur **OK** pour enregistrer vos modifications.  
  
9. Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans l’Explorateur de solutions, cliquez sur **Interrogative_2XSchemas** de projet, puis cliquez sur **déployer**. Assurez-vous de qu'un message de réussite s’affiche dans la fenêtre Sortie.  
  
    > [!NOTE]
    >  Si le message de déploiement approprié n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de votre déploiement.  
  
 Passez à [étape 2 : créer des schémas courants pour V2.4](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-4.md).