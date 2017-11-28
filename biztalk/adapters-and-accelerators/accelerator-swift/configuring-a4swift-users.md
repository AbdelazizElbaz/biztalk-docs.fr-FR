---
title: "Configuration d’A4SWIFT utilisateurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, user accounts
- creating, user accounts
- user accounts, creating
ms.assetid: 45dcbece-ec8d-410a-8320-79bfbc4c779d
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79c3b63cd77bb34545f4c4093796310aa7720563
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-a4swift-users"></a><span data-ttu-id="5cad1-102">Configuration d’A4SWIFT utilisateurs</span><span class="sxs-lookup"><span data-stu-id="5cad1-102">Configuring A4SWIFT Users</span></span>
<span data-ttu-id="5cad1-103">Lors de l’installation de [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)], le programme de configuration d’A4SWIFT crée des profils de partenaire commercial par défaut et des accords et inscrit le serveur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5cad1-103">During installation of [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)], the A4SWIFT configuration program creates default trading partner profiles and agreements, and registers the BizTalk Server.</span></span> <span data-ttu-id="5cad1-104">A4SWIFT crée également des bibliothèques de documents utilisées par le composant de Message Repair et New Submission.</span><span class="sxs-lookup"><span data-stu-id="5cad1-104">A4SWIFT also creates document libraries used by the Message Repair and New Submission component.</span></span>  
  
 <span data-ttu-id="5cad1-105">A4SWIFT crée les dossiers de document suivants lors de l’installation :</span><span class="sxs-lookup"><span data-stu-id="5cad1-105">A4SWIFT creates the following document folders during installation:</span></span>  
  
-   <span data-ttu-id="5cad1-106">Bibliothèque de documents boîte d’envoi</span><span class="sxs-lookup"><span data-stu-id="5cad1-106">Outbox document library</span></span>  
  
-   <span data-ttu-id="5cad1-107">Bibliothèque de documents modèles</span><span class="sxs-lookup"><span data-stu-id="5cad1-107">Templates document library</span></span>  
  
-   <span data-ttu-id="5cad1-108">Bibliothèque de documents non analysée</span><span class="sxs-lookup"><span data-stu-id="5cad1-108">Unparsed document library</span></span>  
  
-   <span data-ttu-id="5cad1-109">Nouvelle bibliothèque de documents SWIFT MT Message</span><span class="sxs-lookup"><span data-stu-id="5cad1-109">New SWIFT MT Message document library</span></span>  
  
-   <span data-ttu-id="5cad1-110">Nouvelle bibliothèque de documents Messages de MX SWIFT</span><span class="sxs-lookup"><span data-stu-id="5cad1-110">New SWIFT MX Messages document library</span></span>  
  
 <span data-ttu-id="5cad1-111">Pour chaque service créé, l’administrateur A4SWIFT doivent configurer manuellement les groupes de sites pour les services correspondants et rôles définis par l’A4SWIFT.</span><span class="sxs-lookup"><span data-stu-id="5cad1-111">For each department created, the A4SWIFT Administrator must manually set up site groups for the corresponding departments and A4SWIFT defined roles.</span></span> <span data-ttu-id="5cad1-112">Chaque département/rôle dispose d’une boîte de réception créé automatiquement par le Client(PWC) Web de profil.</span><span class="sxs-lookup"><span data-stu-id="5cad1-112">Each department/role has an inbox created automatically by the Profile Web Client(PWC).</span></span>  
  
 <span data-ttu-id="5cad1-113">Une fois le programme de configuration d’A4SWIFT le programme d’installation est terminé, l’administrateur de A4SWIFT configure les flux de travail pour chaque service de l’organisation.</span><span class="sxs-lookup"><span data-stu-id="5cad1-113">After the A4SWIFT setup configuration program is completed, the A4SWIFT Administrator configures workflows for each department in the organization.</span></span> <span data-ttu-id="5cad1-114">Lors de la configuration de Message Repair et New Submission, via le Client Web du profil, les boîtes de réception correspondants sont créés pour chaque combinaison de département/rôle.</span><span class="sxs-lookup"><span data-stu-id="5cad1-114">During Message Repair and New Submission configuration, through the Profile Web Client, corresponding inboxes are created for each department/role combination.</span></span> <span data-ttu-id="5cad1-115">Par exemple, lors de la configuration de PWC A4SWIFT administrateur crée un service nommé paiements et attribue ensuite les rôles des créateurs, réparateurs et les approbateurs à un service appelé paiements.</span><span class="sxs-lookup"><span data-stu-id="5cad1-115">For example, during PWC configuration an A4SWIFT Administrator creates a department named Payments and then assigns the roles of Creators, Repairers, and Approvers to a department called Payments.</span></span> <span data-ttu-id="5cad1-116">Bibliothèques de documents sur le site MRSR sont créés avec les noms de la boîte de réception, comme indiqué dans les exemples dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="5cad1-116">Document libraries on the MRSR site are created with the inbox names as shown in the examples in the following table:</span></span>  
  
|<span data-ttu-id="5cad1-117">Nom du service</span><span class="sxs-lookup"><span data-stu-id="5cad1-117">Department name</span></span>|<span data-ttu-id="5cad1-118">Nom du rôle</span><span class="sxs-lookup"><span data-stu-id="5cad1-118">Role name</span></span>|<span data-ttu-id="5cad1-119">Nom de la boîte de réception</span><span class="sxs-lookup"><span data-stu-id="5cad1-119">Inbox name</span></span>|  
|---------------------|---------------|----------------|  
|<span data-ttu-id="5cad1-120">Paiements</span><span class="sxs-lookup"><span data-stu-id="5cad1-120">Payments</span></span>|<span data-ttu-id="5cad1-121">Créateurs</span><span class="sxs-lookup"><span data-stu-id="5cad1-121">Creators</span></span>|<span data-ttu-id="5cad1-122">Payments_Creator</span><span class="sxs-lookup"><span data-stu-id="5cad1-122">Payments_Creator</span></span>|  
|<span data-ttu-id="5cad1-123">Paiements</span><span class="sxs-lookup"><span data-stu-id="5cad1-123">Payments</span></span>|<span data-ttu-id="5cad1-124">Réparateurs</span><span class="sxs-lookup"><span data-stu-id="5cad1-124">Repairers</span></span>|<span data-ttu-id="5cad1-125">Payments_Repairers</span><span class="sxs-lookup"><span data-stu-id="5cad1-125">Payments_Repairers</span></span>|  
|<span data-ttu-id="5cad1-126">Paiements</span><span class="sxs-lookup"><span data-stu-id="5cad1-126">Payments</span></span>|<span data-ttu-id="5cad1-127">Approbateurs</span><span class="sxs-lookup"><span data-stu-id="5cad1-127">Approvers</span></span>|<span data-ttu-id="5cad1-128">Payments_Approvers</span><span class="sxs-lookup"><span data-stu-id="5cad1-128">Payments_Approvers</span></span>|