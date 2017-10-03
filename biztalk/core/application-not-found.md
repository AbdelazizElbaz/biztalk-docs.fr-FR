---
title: Application introuvable | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c37680b2-b38a-40f3-bb27-7b7281299ec3
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2a2b42a74001cfdc374d20052a8369ae535347d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="application-not-found"></a><span data-ttu-id="39f49-102">Application introuvable</span><span class="sxs-lookup"><span data-stu-id="39f49-102">Application not found</span></span>
## <a name="details"></a><span data-ttu-id="39f49-103">Détails</span><span class="sxs-lookup"><span data-stu-id="39f49-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="39f49-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="39f49-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="39f49-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="39f49-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="39f49-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="39f49-106">Event ID</span></span>|<span data-ttu-id="39f49-107">0</span><span class="sxs-lookup"><span data-stu-id="39f49-107">0</span></span>|  
|<span data-ttu-id="39f49-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="39f49-108">Event Source</span></span>|<span data-ttu-id="39f49-109">0</span><span class="sxs-lookup"><span data-stu-id="39f49-109">0</span></span>|  
|<span data-ttu-id="39f49-110">Composant</span><span class="sxs-lookup"><span data-stu-id="39f49-110">Component</span></span>|<span data-ttu-id="39f49-111">0</span><span class="sxs-lookup"><span data-stu-id="39f49-111">0</span></span>|  
|<span data-ttu-id="39f49-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="39f49-112">Symbolic Name</span></span>|<span data-ttu-id="39f49-113">0</span><span class="sxs-lookup"><span data-stu-id="39f49-113">0</span></span>|  
|<span data-ttu-id="39f49-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="39f49-114">Message Text</span></span>|<span data-ttu-id="39f49-115">Application « {0} » introuvable. Vérifiez que l'application existe dans la base de données de configuration BizTalk par défaut</span><span class="sxs-lookup"><span data-stu-id="39f49-115">Application "{0}" not found.Verify the application exists in the default BizTalk configuration database</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="39f49-116">Explication</span><span class="sxs-lookup"><span data-stu-id="39f49-116">Explanation</span></span>  
 <span data-ttu-id="39f49-117">Cette erreur indique que BizTalk utilise une application qui n'existe pas dans les bases de données BizTalk.</span><span class="sxs-lookup"><span data-stu-id="39f49-117">This error indicates BizTalk is using an application that does not exist in the BizTalk databases.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="39f49-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="39f49-118">User Action</span></span>  
 <span data-ttu-id="39f49-119">La procédure suivante permet de configurer une application valide.</span><span class="sxs-lookup"><span data-stu-id="39f49-119">Use the following procedure to configure a valid application.</span></span>  
  
#### <a name="to-configure-a-valid-application"></a><span data-ttu-id="39f49-120">Pour configurer une application valide</span><span class="sxs-lookup"><span data-stu-id="39f49-120">To configure a valid application</span></span>  
  
1.  <span data-ttu-id="39f49-121">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="39f49-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="39f49-122">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="39f49-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="39f49-123">Assurez-vous que l'application existe.</span><span class="sxs-lookup"><span data-stu-id="39f49-123">Ensure that the application exists there.</span></span> <span data-ttu-id="39f49-124">Sinon, sélectionnez-en une valide.</span><span class="sxs-lookup"><span data-stu-id="39f49-124">If not, select a different valid application.</span></span>