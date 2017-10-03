---
title: "Suite algorithmique de sécurité non pris en charge | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11696fed-c3a8-4b11-8249-9f99f7abc8f2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43cce7cd315c3bdfa3835014c2cf1f6a8c7077f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unsupported-security-algorithm-suite"></a><span data-ttu-id="2d433-102">Valeur de suite d'algorithmes de sécurité non prise en charge</span><span class="sxs-lookup"><span data-stu-id="2d433-102">Unsupported security algorithm suite</span></span>
## <a name="details"></a><span data-ttu-id="2d433-103">Détails</span><span class="sxs-lookup"><span data-stu-id="2d433-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2d433-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="2d433-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="2d433-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="2d433-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="2d433-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="2d433-106">Event ID</span></span>|<span data-ttu-id="2d433-107">0</span><span class="sxs-lookup"><span data-stu-id="2d433-107">0</span></span>|  
|<span data-ttu-id="2d433-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="2d433-108">Event Source</span></span>|<span data-ttu-id="2d433-109">0</span><span class="sxs-lookup"><span data-stu-id="2d433-109">0</span></span>|  
|<span data-ttu-id="2d433-110">Composant</span><span class="sxs-lookup"><span data-stu-id="2d433-110">Component</span></span>|<span data-ttu-id="2d433-111">0</span><span class="sxs-lookup"><span data-stu-id="2d433-111">0</span></span>|  
|<span data-ttu-id="2d433-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="2d433-112">Symbolic Name</span></span>|<span data-ttu-id="2d433-113">0</span><span class="sxs-lookup"><span data-stu-id="2d433-113">0</span></span>|  
|<span data-ttu-id="2d433-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="2d433-114">Message Text</span></span>|<span data-ttu-id="2d433-115">Suite algorithmique de sécurité non pris en charge : {0}</span><span class="sxs-lookup"><span data-stu-id="2d433-115">Unsupported security algorithm suite: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2d433-116">Explication</span><span class="sxs-lookup"><span data-stu-id="2d433-116">Explanation</span></span>  
 <span data-ttu-id="2d433-117">Cette erreur se produit lorsque la propriété de la suite d'algorithmes de sécurité d'un emplacement de réception ou d'un port d'envoi est définie sur une valeur erronée.</span><span class="sxs-lookup"><span data-stu-id="2d433-117">This error occurs when the security algorithm suite property of a receive location or send port is set to an incorrect value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2d433-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="2d433-118">User Action</span></span>  
 <span data-ttu-id="2d433-119">Vérifiez que la propriété de protocole de transaction est définie sur une valeur valide.</span><span class="sxs-lookup"><span data-stu-id="2d433-119">Ensure that transaction protocol property is set to a valid value.</span></span>  
  
1.  <span data-ttu-id="2d433-120">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="2d433-120">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="2d433-121">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="2d433-121">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="2d433-122">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="2d433-122">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="2d433-123">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="2d433-123">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="2d433-124">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="2d433-124">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="2d433-125">Dans le port **Type** liste, sélectionnez **WCF-NetTcp**.</span><span class="sxs-lookup"><span data-stu-id="2d433-125">In the port **Type** list, select **WCF-NetTcp**.</span></span>  
  
7.  <span data-ttu-id="2d433-126">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="2d433-126">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="2d433-127">Dans le **propriétés du Transport WCF-NetTcp** boîte de dialogue, cliquez sur le **sécurité** onglet.</span><span class="sxs-lookup"><span data-stu-id="2d433-127">In the **WCF-NetTcp Transport Properties** dialog box, click the **Security** tab.</span></span>  
  
9. <span data-ttu-id="2d433-128">Dans le **la sécurité de Message** section, vérifiez que les valeurs de **suite d’algorithmes** sont corrects.</span><span class="sxs-lookup"><span data-stu-id="2d433-128">In the **Message security** section, ensure that the values for **Algorithm suite** are correct.</span></span>