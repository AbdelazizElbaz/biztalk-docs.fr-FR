---
title: "Ne peut pas obtenir la base de données ou les noms de serveur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0590f43b-0aec-491f-bca5-c50ab12552a5
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16c694acdc78b704eb6f2578df99239442fd897e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="could-not-get-the-database-or-the-server-names"></a><span data-ttu-id="da0b1-102">Impossible d'obtenir les noms de la base de données ou du serveur</span><span class="sxs-lookup"><span data-stu-id="da0b1-102">Could not get the database or the server names</span></span>
## <a name="details"></a><span data-ttu-id="da0b1-103">Détails</span><span class="sxs-lookup"><span data-stu-id="da0b1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="da0b1-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="da0b1-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="da0b1-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="da0b1-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="da0b1-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="da0b1-106">Event ID</span></span>|-|  
|<span data-ttu-id="da0b1-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="da0b1-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="da0b1-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="da0b1-108"> EDI</span></span>|  
|<span data-ttu-id="da0b1-109">Composant</span><span class="sxs-lookup"><span data-stu-id="da0b1-109">Component</span></span>|<span data-ttu-id="da0b1-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="da0b1-110">EDI Engine</span></span>|  
|<span data-ttu-id="da0b1-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="da0b1-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="da0b1-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="da0b1-112">Message Text</span></span>|<span data-ttu-id="da0b1-113">Impossible d'obtenir les noms de la base de données ou du serveur</span><span class="sxs-lookup"><span data-stu-id="da0b1-113">Could not get the database or the server names</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="da0b1-114">Explication</span><span class="sxs-lookup"><span data-stu-id="da0b1-114">Explanation</span></span>  
 <span data-ttu-id="da0b1-115">Cette erreur indique que BizTalk n'a pas pu lire le nom BizTalkMgmtDb et le nom du serveur depuis le registre.</span><span class="sxs-lookup"><span data-stu-id="da0b1-115">This error indicates BizTalk could not read the BizTalkMgmtDb name and Server name from registry.</span></span> <span data-ttu-id="da0b1-116">Une raison possible de cette erreur est que le groupe BizTalk n'est pas configuré.</span><span class="sxs-lookup"><span data-stu-id="da0b1-116">One possible reason for this error is the BizTalk Group is not configured.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="da0b1-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="da0b1-117">User Action</span></span>  
 <span data-ttu-id="da0b1-118">Pour résoudre cette erreur, configurez le groupe BizTalk :</span><span class="sxs-lookup"><span data-stu-id="da0b1-118">To resolve this error, configure the BizTalk Group:</span></span>  
  
1.  <span data-ttu-id="da0b1-119">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="da0b1-119">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="da0b1-120">À la racine de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="da0b1-120">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  
  
3.  <span data-ttu-id="da0b1-121">Avec le bouton droit **groupe BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="da0b1-121">Right-click **BizTalk Group**.</span></span>  
  
4.  <span data-ttu-id="da0b1-122">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="da0b1-122">Click **Properties**.</span></span>  
  
5.  <span data-ttu-id="da0b1-123">Dans le volet gauche, cliquez sur **général**.</span><span class="sxs-lookup"><span data-stu-id="da0b1-123">In the left pane, click **General**.</span></span>  
  
6.  <span data-ttu-id="da0b1-124">Vérifiez le **Server** nom et **base de données** nom sont corrects.</span><span class="sxs-lookup"><span data-stu-id="da0b1-124">Verify the **Server** name and **Database** name are correct.</span></span>