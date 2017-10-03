---
title: "Étape 1 : Créer et déployer des schémas d’en-tête et d’accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, header schemas
- header schemas
ms.assetid: 3ff013a4-6c67-4bac-be97-81b2dc5b6119
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bfab230d919c2cb7f8c05d58b87cdeea6033423
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-create-and-deploy-header-and-acknowledgment-schemas"></a>Étape 1 : Créer et déployer des schémas d’en-tête et d’accusé de réception
Vous utilisez le schéma d’en-tête pour valider l’en-tête (segment MSH) de l’instance de message. Le schéma d’accusé de réception vous permet de générer l’accusé de réception pour l’instance de message. Ce processus est commun à toutes les versions de schémas de [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 2.X.  
  
### <a name="to-create-the-header-and-acknowledgment-schemas"></a>Pour créer les schémas d’en-tête et d’accusé de réception  
  
1.  Démarrez **Microsoft Visual Studio 2012**.  
  
2.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
3.  Dans la boîte de dialogue Nouveau projet, dans le **Types de projets** , développez **projets BizTalk**, puis sélectionnez **BTAHL7Projects**.  
  
4.  Dans la section modèles, sélectionnez **BTAHL7V2XCommon projet**, puis cliquez sur **OK**.  
  
     Dans l’Explorateur de solutions, notez que les trois schémas (ACK_24_GLO_DEF.xsd ACK_25_GLO_DEF.xsd et MSH_25_GLO_DEF.xsd) sont inclus dans le projet.  
  
## <a name="step-1a-assign-a-strong-key-to-the-assembly-and-deploy"></a>Étape 1 a : assigner une clé forte à l’Assembly et le déployer  
 Utilisez la procédure suivante pour affecter une clé forte à l’assembly, puis déployer l’assembly.  
  
#### <a name="to-assign-a-strong-key-and-deploy-the-assembly"></a>Pour affecter une clé forte et de déployer l’assembly  
  
1.  Démarrez une **invite de commandes Visual Studio 2012**.  
  
2.  À la [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] invite de commandes, accédez à la \< *lecteur*> : \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version > Accelerator pour le dossier de didacticiel \SDK\End-to-End HL7.  
  
3.  À l’invite de commandes, tapez **sn – k key.snk**, puis appuyez sur ENTRÉE. Vérifiez que le message suivant s’affiche dans la fenêtre Sortie, puis fermez la fenêtre de commande.  
  
     **« Paire de clés écrite dans key.snk. »**  
  
    > [!NOTE]
    >  Si le message approprié n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de votre assembly.  
  
4.  Dans l’Explorateur de solutions, cliquez sur **BTAHL7V2XCommon Projet1**, puis cliquez sur **propriétés**.  
  
5.  Dans la page des Pages de propriétés Projet1 BTAHL7V2XCommon, cliquez sur **Assembly**.  
  
6.  Dans le volet droit, faites défiler jusqu'à la **nom fort** , cliquez sur le champ situé à droite de **fichier de clé d’Assembly**, puis cliquez sur le bouton de sélection (**...** ) bouton.  
  
7.  Dans la boîte de dialogue de fichier de clé d’Assembly, accédez à \< *lecteur*> : \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version > Accelerator for HL7\SDK\End en bout didacticiel, sélectionnez **key.snk**, puis cliquez sur **ouvrir**.  
  
8.  Dans la page de propriété du projet BTAHL7V2XCommon, cliquez sur **OK** pour enregistrer vos modifications.  
  
9. Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans **l’Explorateur de solutions**, avec le bouton droit **BTAHL7V2XCommon projet**, puis cliquez sur **déployer**. Assurez-vous de qu'un message de réussite s’affiche dans la fenêtre Sortie.  
  
    > [!NOTE]
    >  Si le message de déploiement approprié n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de votre déploiement.  
  
 Passez à [étape 2 : créer des schémas courants pour V2.3.1](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-3-1.md).