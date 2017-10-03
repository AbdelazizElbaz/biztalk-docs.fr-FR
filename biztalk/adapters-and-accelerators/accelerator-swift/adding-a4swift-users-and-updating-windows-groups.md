---
title: "Ajout d’utilisateurs d’A4SWIFT et de mise à jour de groupes Windows | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user accounts, Windows groups
- Windows groups, user accounts
- user accounts, creating
- Windows groups, updating
- updating Windows groups
- A4SWIFT, creating user accounts
ms.assetid: ddc54457-6499-402c-9cc2-f7b17bbc255f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce3fbf2f3b78b13205b43989c2b0c03909dec392
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-a4swift-users-and-updating-windows-groups"></a>Ajout d’utilisateurs d’A4SWIFT et de mise à jour de groupes Windows
Après avoir créé et installer des certificats pour Message Repair et New Submission rôles, vous devez créer [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] les utilisateurs et ajouter [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] utilisateurs aux groupes.  
  
 **Résumé**  
  
 Créer des utilisateurs de Message Repair et New Submission et ajouter des comptes locaux ou de domaine à [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] groupes d’utilisateurs, comme suit :  
  
-   Dans la [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Console de gestion, vous devez créer autant d’utilisateurs qu’il existe des rôles dans les étapes de votre processus de Message Repair et New Submission. Associer un certificat distinct à chacun de ces utilisateurs.  
  
-   À l’aide de la [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] utilitaire de gestion de l’ordinateur, ajoutez chaque utilisateur local qui crée, la réparation, de vérification ou de l’approbation d’un message aux utilisateurs d’A4SWIFT.  
  
-   À l’aide de la [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] utilitaire de gestion de l’ordinateur, ajoutez l’utilisateur local qui est répertorié dans le champ d’identification pour le service groupe BizTalk des services BizTalk pour le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] groupe d’utilisateurs.  
  
    > [!NOTE]
    >  Pour plus d’informations sur [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] utilisateurs et des rôles, consultez [des services de création et de rôles pour Message Repair et New Submission](../../adapters-and-accelerators/accelerator-swift/creating-departments-and-roles-for-message-repair-and-new-submission.md).  
  
### <a name="to-add-user-accounts-to-the-a4swift-users-group"></a>Pour ajouter des comptes d’utilisateur au groupe d’utilisateurs A4SWIFT  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, puis cliquez sur **gestion de l’ordinateur**.  
  
2.  Dans le **gestion de l’ordinateur** boîte de dialogue, dans le volet gauche, développez **utilisateurs et groupes locaux**, puis cliquez sur **groupes**.  
  
3.  Dans le **gestion de l’ordinateur** boîte de dialogue, dans le volet droit, double-cliquez sur **A4SWIFT utilisateurs**.  
  
4.  Dans le **propriétés d’utilisateurs d’A4SWIFT** boîte de dialogue, cliquez sur **ajouter**.  
  
5.  Dans le **sélectionnez utilisateurs, ordinateurs ou groupes** boîte de dialogue le **Entrez les noms des objets à sélectionner** volet, tapez le nom d’un utilisateur local qui crée, la réparation, vérification ou l’approbation d’un message, puis Cliquez sur **OK**.  
  
6.  Répétez l’étape 5 pour chaque utilisateur local qui crée, la réparation, vérification ou l’approbation d’un message.  
  
7.  Dans la boîte de dialogue Propriétés d’utilisateurs A4SWIFT, cliquez sur **OK**.  
  
8.  Dans la boîte de dialogue Gestion de l’ordinateur, dans le volet gauche, développez Services et Applications, puis cliquez sur Services. Dans le volet droit, cliquez sur **groupe BizTalk des services BizTalk**. Notez que l’utilisateur répertorié dans la colonne d’identification pour **groupe BizTalk des services BizTalk**.  
  
9. Dans le volet gauche de la **gestion de l’ordinateur** boîte de dialogue, développez **utilisateurs et groupes locaux**, puis cliquez sur **groupes**. Double-cliquez sur **A4SWIFT utilisateurs**. Vérifiez que l’utilisateur figure dans la colonne d’identification pour **groupe BizTalk des services BizTalk** fait partie de la **A4SWIFT utilisateurs** groupe. Dans le cas contraire, ajoutez cet utilisateur à la **A4SWIFT utilisateurs** groupe.  
  
10. Se déconnecter du serveur, puis vous reconnecter.