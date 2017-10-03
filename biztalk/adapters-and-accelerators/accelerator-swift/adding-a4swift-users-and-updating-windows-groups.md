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
# <a name="adding-a4swift-users-and-updating-windows-groups"></a><span data-ttu-id="017b9-102">Ajout d’utilisateurs d’A4SWIFT et de mise à jour de groupes Windows</span><span class="sxs-lookup"><span data-stu-id="017b9-102">Adding A4SWIFT Users and Updating Windows Groups</span></span>
<span data-ttu-id="017b9-103">Après avoir créé et installer des certificats pour Message Repair et New Submission rôles, vous devez créer [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] les utilisateurs et ajouter [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] utilisateurs aux groupes.</span><span class="sxs-lookup"><span data-stu-id="017b9-103">After you create and install certificates for Message Repair and New Submission roles, you must create [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] users and add [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] users to groups.</span></span>  
  
 <span data-ttu-id="017b9-104">**Résumé**</span><span class="sxs-lookup"><span data-stu-id="017b9-104">**Summary**</span></span>  
  
 <span data-ttu-id="017b9-105">Créer des utilisateurs de Message Repair et New Submission et ajouter des comptes locaux ou de domaine à [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] groupes d’utilisateurs, comme suit :</span><span class="sxs-lookup"><span data-stu-id="017b9-105">Create Message Repair and New Submission users and add local or domain accounts to [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] user groups, as follows:</span></span>  
  
-   <span data-ttu-id="017b9-106">Dans la [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Console de gestion, vous devez créer autant d’utilisateurs qu’il existe des rôles dans les étapes de votre processus de Message Repair et New Submission.</span><span class="sxs-lookup"><span data-stu-id="017b9-106">In the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Management Console, you need to create as many users as there are roles in the workflow stages of your Message Repair and New Submission process.</span></span> <span data-ttu-id="017b9-107">Associer un certificat distinct à chacun de ces utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="017b9-107">Associate a distinct certificate with each of these users.</span></span>  
  
-   <span data-ttu-id="017b9-108">À l’aide de la [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] utilitaire de gestion de l’ordinateur, ajoutez chaque utilisateur local qui crée, la réparation, de vérification ou de l’approbation d’un message aux utilisateurs d’A4SWIFT.</span><span class="sxs-lookup"><span data-stu-id="017b9-108">Using the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Computer Management utility, add each local user who is creating, repairing, verifying, or approving a message to the A4SWIFT Users.</span></span>  
  
-   <span data-ttu-id="017b9-109">À l’aide de la [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] utilitaire de gestion de l’ordinateur, ajoutez l’utilisateur local qui est répertorié dans le champ d’identification pour le service groupe BizTalk des services BizTalk pour le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] groupe d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="017b9-109">Using the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Computer Management utility, add the local user that is listed in the Log On As field for the BizTalk Service BizTalk Group service to the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Users group.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="017b9-110">Pour plus d’informations sur [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] utilisateurs et des rôles, consultez [des services de création et de rôles pour Message Repair et New Submission](../../adapters-and-accelerators/accelerator-swift/creating-departments-and-roles-for-message-repair-and-new-submission.md).</span><span class="sxs-lookup"><span data-stu-id="017b9-110">For more information about [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] users and roles, see [Creating Departments and Roles for Message Repair and New Submission](../../adapters-and-accelerators/accelerator-swift/creating-departments-and-roles-for-message-repair-and-new-submission.md).</span></span>  
  
### <a name="to-add-user-accounts-to-the-a4swift-users-group"></a><span data-ttu-id="017b9-111">Pour ajouter des comptes d’utilisateur au groupe d’utilisateurs A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="017b9-111">To add User Accounts to the A4SWIFT Users Group</span></span>  
  
1.  <span data-ttu-id="017b9-112">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, puis cliquez sur **gestion de l’ordinateur**.</span><span class="sxs-lookup"><span data-stu-id="017b9-112">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Computer Management**.</span></span>  
  
2.  <span data-ttu-id="017b9-113">Dans le **gestion de l’ordinateur** boîte de dialogue, dans le volet gauche, développez **utilisateurs et groupes locaux**, puis cliquez sur **groupes**.</span><span class="sxs-lookup"><span data-stu-id="017b9-113">In the **Computer Management** dialog box, in the left pane, expand **Local Users and Groups**, and then click **Groups**.</span></span>  
  
3.  <span data-ttu-id="017b9-114">Dans le **gestion de l’ordinateur** boîte de dialogue, dans le volet droit, double-cliquez sur **A4SWIFT utilisateurs**.</span><span class="sxs-lookup"><span data-stu-id="017b9-114">In the **Computer Management** dialog box, in the right pane, double-click **A4SWIFT Users**.</span></span>  
  
4.  <span data-ttu-id="017b9-115">Dans le **propriétés d’utilisateurs d’A4SWIFT** boîte de dialogue, cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="017b9-115">In the **A4SWIFT Users Properties** dialog box, click **Add**.</span></span>  
  
5.  <span data-ttu-id="017b9-116">Dans le **sélectionnez utilisateurs, ordinateurs ou groupes** boîte de dialogue le **Entrez les noms des objets à sélectionner** volet, tapez le nom d’un utilisateur local qui crée, la réparation, vérification ou l’approbation d’un message, puis Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="017b9-116">In the **Select Users, Computers, or Groups** dialog box, in the **Enter the object names to select** pane, type the name of a local user who is creating, repairing, verifying, or approving a message, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="017b9-117">Répétez l’étape 5 pour chaque utilisateur local qui crée, la réparation, vérification ou l’approbation d’un message.</span><span class="sxs-lookup"><span data-stu-id="017b9-117">Repeat step 5 for each local user who is creating, repairing, verifying, or approving a message.</span></span>  
  
7.  <span data-ttu-id="017b9-118">Dans la boîte de dialogue Propriétés d’utilisateurs A4SWIFT, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="017b9-118">In the A4SWIFT Users Properties dialog box, click **OK**.</span></span>  
  
8.  <span data-ttu-id="017b9-119">Dans la boîte de dialogue Gestion de l’ordinateur, dans le volet gauche, développez Services et Applications, puis cliquez sur Services.</span><span class="sxs-lookup"><span data-stu-id="017b9-119">In the Computer Management dialog box, in the left pane, expand Services and Applications, and then click Services.</span></span> <span data-ttu-id="017b9-120">Dans le volet droit, cliquez sur **groupe BizTalk des services BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="017b9-120">In the right pane, click **BizTalk Service BizTalk Group**.</span></span> <span data-ttu-id="017b9-121">Notez que l’utilisateur répertorié dans la colonne d’identification pour **groupe BizTalk des services BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="017b9-121">Note the user listed in the Log On As column for **BizTalk Service BizTalk Group**.</span></span>  
  
9. <span data-ttu-id="017b9-122">Dans le volet gauche de la **gestion de l’ordinateur** boîte de dialogue, développez **utilisateurs et groupes locaux**, puis cliquez sur **groupes**.</span><span class="sxs-lookup"><span data-stu-id="017b9-122">In the left pane of the **Computer Management** dialog box, expand **Local Users and Groups**, and then click **Groups**.</span></span> <span data-ttu-id="017b9-123">Double-cliquez sur **A4SWIFT utilisateurs**.</span><span class="sxs-lookup"><span data-stu-id="017b9-123">Double-click **A4SWIFT Users**.</span></span> <span data-ttu-id="017b9-124">Vérifiez que l’utilisateur figure dans la colonne d’identification pour **groupe BizTalk des services BizTalk** fait partie de la **A4SWIFT utilisateurs** groupe.</span><span class="sxs-lookup"><span data-stu-id="017b9-124">Ensure that the user listed in the Log On As column for **BizTalk Service BizTalk Group** is part of the **A4SWIFT Users** group.</span></span> <span data-ttu-id="017b9-125">Dans le cas contraire, ajoutez cet utilisateur à la **A4SWIFT utilisateurs** groupe.</span><span class="sxs-lookup"><span data-stu-id="017b9-125">If not, add that user to the **A4SWIFT Users** group.</span></span>  
  
10. <span data-ttu-id="017b9-126">Se déconnecter du serveur, puis vous reconnecter.</span><span class="sxs-lookup"><span data-stu-id="017b9-126">Log off the server, and then log back on.</span></span>