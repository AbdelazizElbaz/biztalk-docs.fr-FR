---
title: "Avant d’importer le Pack d’administration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e3c13dd-613a-4885-a5d2-ad3ee492ff25
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c11849c379a4654bed78a8e86ba263e6da428c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="before-you-import-the-management-pack"></a><span data-ttu-id="cac7b-102">Avant d’importer le Pack d’administration</span><span class="sxs-lookup"><span data-stu-id="cac7b-102">Before You Import the Management Pack</span></span>
<span data-ttu-id="cac7b-103">Comme meilleure pratique, vous devez importer le Pack d’administration de Windows Server pour le système d’exploitation que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="cac7b-103">As a best practice, you should import the Windows Server Management Pack for the operating system that you are using.</span></span> <span data-ttu-id="cac7b-104">Avant d’importer le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration, effectuez les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="cac7b-104">Before you import the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack, take the following actions:</span></span>  
  
-   <span data-ttu-id="cac7b-105">Assurez-vous qu’Operations Manager 2007 R2/2012 est installé.</span><span class="sxs-lookup"><span data-stu-id="cac7b-105">Ensure that Operations Manager 2007 R2/2012 is installed.</span></span>  
  
-   <span data-ttu-id="cac7b-106">Vous devez être membre du groupe Administrateurs de SCOM ou sur le groupe auteurs de SCOM.</span><span class="sxs-lookup"><span data-stu-id="cac7b-106">You must be a member of either the SCOM Administrators group or the SCOM Authors group.</span></span> <span data-ttu-id="cac7b-107">Les administrateurs locaux sur le serveur d’administration SCOM ont tous les droits et les autorisations sont accordées au groupe Administrateurs de SCOM.</span><span class="sxs-lookup"><span data-stu-id="cac7b-107">Local administrators on the SCOM Management Server have all the rights and permissions that are granted to the SCOM Administrators group.</span></span>  
  
-   <span data-ttu-id="cac7b-108">Configurer vos serveurs BizTalk Server en tant qu’ordinateurs gérés dans Operations Manager en déployant des agents SCOM sur chaque serveur BizTalk Server que vous souhaitez gérer.</span><span class="sxs-lookup"><span data-stu-id="cac7b-108">Set up your BizTalk Servers as managed computers in Operations Manager by deploying the SCOM agents on each BizTalk Server that you want to manage.</span></span> <span data-ttu-id="cac7b-109">Le déploiement de l’agent SCOM implique les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="cac7b-109">The SCOM agent deployment involves the following tasks:</span></span>  
  
    -   <span data-ttu-id="cac7b-110">Installez l’agent SCOM.</span><span class="sxs-lookup"><span data-stu-id="cac7b-110">Install the SCOM agent.</span></span>  
  
    -   <span data-ttu-id="cac7b-111">Créer un compte d’agent BizTalk SCOM.</span><span class="sxs-lookup"><span data-stu-id="cac7b-111">Create a BizTalk SCOM agent account.</span></span>  
  
    -   <span data-ttu-id="cac7b-112">Configurer un **exécuter en tant que** compte.</span><span class="sxs-lookup"><span data-stu-id="cac7b-112">Configure a **Run As** account.</span></span> <span data-ttu-id="cac7b-113">Ajoutez le compte d’identification aux groupes suivants :</span><span class="sxs-lookup"><span data-stu-id="cac7b-113">Add the Run As account to the following groups:</span></span>  
  
        -   <span data-ttu-id="cac7b-114">Groupes BizTalk.</span><span class="sxs-lookup"><span data-stu-id="cac7b-114">BizTalk Groups.</span></span>  
  
        -   <span data-ttu-id="cac7b-115">Administrateurs de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="cac7b-115">BizTalk Administrators.</span></span>  
  
        -   <span data-ttu-id="cac7b-116">Administrateurs de l’authentification unique.</span><span class="sxs-lookup"><span data-stu-id="cac7b-116">SSO Administrators.</span></span>  
  
        -   <span data-ttu-id="cac7b-117">Administrateurs d’applications associées SSO.</span><span class="sxs-lookup"><span data-stu-id="cac7b-117">SSO Affiliate Administrators.</span></span>  
  
    -   <span data-ttu-id="cac7b-118">Lancement de l’analyse.</span><span class="sxs-lookup"><span data-stu-id="cac7b-118">Initiate monitoring.</span></span>  
  
-   <span data-ttu-id="cac7b-119">Dans la Console Operations Manager, les ordinateurs gérés sont dans un état sain.</span><span class="sxs-lookup"><span data-stu-id="cac7b-119">In Operation Manager Console, managed computers are in a healthy state.</span></span>  
  
-   <span data-ttu-id="cac7b-120">Configurer des comptes d’utilisateur qui doivent être définies, comme les comptes d’identification requises ou des profils.</span><span class="sxs-lookup"><span data-stu-id="cac7b-120">Configure any user accounts that have to be set up, such as any required Run As accounts or profiles.</span></span> <span data-ttu-id="cac7b-121">Ce pack d’administration inclut les profils d’identification nommées « Compte d’analyse de BizTalk Server » et « Compte de découverte de BizTalk Server » pour définir les informations d’identification spécifiques sur une base par l’agent.</span><span class="sxs-lookup"><span data-stu-id="cac7b-121">This management pack includes Run As profiles named “BizTalk Server Monitoring Account” and “BizTalk Server Discovery Account” to define specific credentials on a per-agent basis.</span></span> <span data-ttu-id="cac7b-122">Vous devrez peut-être utiliser ce profil exécuter en tant que certains agents après avoir importé le Pack d’administration.</span><span class="sxs-lookup"><span data-stu-id="cac7b-122">You may have to use this Run As profile for some agents after you import the management pack.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cac7b-123">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="cac7b-123">In this section</span></span>  
  
-   [<span data-ttu-id="cac7b-124">Fichiers dans ce pack d’administration</span><span class="sxs-lookup"><span data-stu-id="cac7b-124">Files in This Management Pack</span></span>](../technical-guides/files-in-this-management-pack.md)  
  
-   [<span data-ttu-id="cac7b-125">Packs d’administration supplémentaires recommandés</span><span class="sxs-lookup"><span data-stu-id="cac7b-125">Recommended Additional Management Packs</span></span>](../technical-guides/recommended-additional-management-packs.md)