---
title: "Étape 1 : Ajouter des schémas d’en-tête et d’accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 808132bf-02e7-4ff4-b914-9fae5d27e5fd
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b5fb871bed9f6a4f54261db7e54587c65244344
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-add-header-and-acknowledgment-schemas"></a>Étape 1 : Ajouter des schémas d’en-tête et d’accusé de réception
Dans cette étape, vous créez un projet basé sur le modèle de projet de BTAHL72XCommon. Ce modèle contient les trois schémas courants pour les en-têtes de message (MSH_25_GLO_DEF.xsd) et les accusés de réception (ACK_24_GLO_DEF.xsd) et (ACK_25_GLO_DEF.xsd). Vous devez inclure ces schémas dans un projet, ainsi que de BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) génère et/ou valide correctement les en-têtes de message et les accusés de réception. Ce processus est commun à toutes les versions de schéma de [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 2.X.  
  
 Vous également créez une clé forte, affectez à l’assembly, puis déployez l’assembly. La clé forte fournit la sécurité et l’identité à l’assembly et n’est nécessaire pour le déploiement. Lorsque vous déployez l’assembly, il est stocké dans la base de données de Configuration (également appelée la base de données BizTalk Management) et le global assembly cache (GAC).  
  
### <a name="to-create-the-project-and-add-header-and-acknowledgment-schemas"></a>Pour créer le projet et ajouter des schémas d’en-tête et d’accusé de réception  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
2.  Dans la boîte de dialogue Nouveau projet, dans le **Types de projets** liste, développez **projets BizTalk**, puis cliquez sur **BTAHL7Projects**.  
  
3.  Dans le **modèles** , cliquez sur **BTAHL7V2XCommon projet**.  
  
4.  Dans le **nom** , tapez **BTAHL7V2XCommon** comme nom du projet.  
  
5.  Dans le **emplacement** , naviguez jusqu’au  **\<**  *lecteur***: > \Batching didacticiel**.  
  
6.  Cliquez sur **OK**.  
  
> [!NOTE]
>  Dans l’Explorateur de solutions, les trois schémas (MSH_25_GLO_DEF.xsd, ACK_24_GLO_DEF.xsd et ACK_25_GLO_DEF.xsd) sont inclus dans le projet.  
  
### <a name="to-assign-a-strong-key-to-the-assembly-and-deploy"></a>Pour attribuer une clé forte à l’assembly et le déployer  
  
1.  Ouvrez  **[!INCLUDE[vs2012](../../includes/vs2012-md.md)] invite de commandes**.  
  
2.  Sur le [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] invite de commandes, accédez à la  **\<**  *lecteur***> : \Batching didacticiel** dossier.  
  
3.  À l’invite de commandes, tapez **sn – k key.snk**, puis appuyez sur ENTRÉE. Vérifiez qu’un message de réussite s’affiche dans la fenêtre Sortie.  
  
    > [!NOTE]
    >  Si le message approprié n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de votre assembly.  
  
4.  Dans l’Explorateur de solutions, cliquez sur **BTAHL7V2Xcommon projet**, puis cliquez sur **propriétés**.  
  
5.  Dans le **Page de propriétés du projet BTAHL7V2XCommon** boîte de dialogue, cliquez sur **signature**.  
  
6.  Vérifiez **signer l’assembly** case à cocher.  
  
7.  Dans **choisir un nom fort** déroulante de fichier de clé de liste, sélectionnez  **\<Parcourir... >**.  
  
8.  Accédez à \< *lecteur*> : \Batching Tutorial, sélectionnez **key.snk**, puis cliquez sur **ouvrir**.  
  
9. Dans la fenêtre de Pages de propriétés du projet BTAHL7V2XCommon, cliquez sur **OK** pour enregistrer vos modifications.  
  
10. Dans l’Explorateur de solutions, cliquez sur **BTAHL7V2Xcommon projet**, puis cliquez sur **déployer**. Assurez-vous de qu'un message de réussite s’affiche dans la fenêtre Sortie.  
  
    > [!NOTE]
    >  Si le message de déploiement approprié n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de votre déploiement.  
  
 Passez à [étape 2 : ajouter des schémas courants pour v2.3.1](../../adapters-and-accelerators/accelerator-hl7/step-2-add-common-schemas-for-v2-3-1.md).