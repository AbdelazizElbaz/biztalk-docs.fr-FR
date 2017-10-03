---
title: "Longueur d’adresse non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8e16eb6-e77e-4361-ac91-0730004c4433
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2df1666fbbd399ef71852b9b9049959830749e99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-address-length"></a><span data-ttu-id="6ec9e-102">Longueur d'adresse non valide</span><span class="sxs-lookup"><span data-stu-id="6ec9e-102">Invalid address length</span></span>
## <a name="details"></a><span data-ttu-id="6ec9e-103">Détails</span><span class="sxs-lookup"><span data-stu-id="6ec9e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6ec9e-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="6ec9e-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="6ec9e-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="6ec9e-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="6ec9e-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="6ec9e-106">Event ID</span></span>|<span data-ttu-id="6ec9e-107">0</span><span class="sxs-lookup"><span data-stu-id="6ec9e-107">0</span></span>|  
|<span data-ttu-id="6ec9e-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="6ec9e-108">Event Source</span></span>|<span data-ttu-id="6ec9e-109">0</span><span class="sxs-lookup"><span data-stu-id="6ec9e-109">0</span></span>|  
|<span data-ttu-id="6ec9e-110">Composant</span><span class="sxs-lookup"><span data-stu-id="6ec9e-110">Component</span></span>|<span data-ttu-id="6ec9e-111">0</span><span class="sxs-lookup"><span data-stu-id="6ec9e-111">0</span></span>|  
|<span data-ttu-id="6ec9e-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="6ec9e-112">Symbolic Name</span></span>|<span data-ttu-id="6ec9e-113">0</span><span class="sxs-lookup"><span data-stu-id="6ec9e-113">0</span></span>|  
|<span data-ttu-id="6ec9e-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="6ec9e-114">Message Text</span></span>|<span data-ttu-id="6ec9e-115">Longueur d’adresse non valide ; longueur de l’adresse spécifiée est {0} caractères, la limite est de {{1} caractères</span><span class="sxs-lookup"><span data-stu-id="6ec9e-115">Invalid address length; specified address length is {0} characters, limit is {1} characters</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6ec9e-116">Explication</span><span class="sxs-lookup"><span data-stu-id="6ec9e-116">Explanation</span></span>  
 <span data-ttu-id="6ec9e-117">Vous avez fourni une adresse qui dépasse la longueur maximale de 255 caractères pour un transport WCF.</span><span class="sxs-lookup"><span data-stu-id="6ec9e-117">You provided an address that exceeds the maximum length of 255 characters for a WCF transport.</span></span> <span data-ttu-id="6ec9e-118">Cette limitation est imposée par BizTalk Server, et non par WCF.</span><span class="sxs-lookup"><span data-stu-id="6ec9e-118">This is a limitation imposed by BizTalk Server, not by WCF.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6ec9e-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="6ec9e-119">User Action</span></span>  
 <span data-ttu-id="6ec9e-120">La procédure suivante permet de configurer une adresse valide.</span><span class="sxs-lookup"><span data-stu-id="6ec9e-120">Use the following procedure to configure a valid address.</span></span>  
  
#### <a name="to-configure-a-valid-address"></a><span data-ttu-id="6ec9e-121">Pour configurer une adresse valide</span><span class="sxs-lookup"><span data-stu-id="6ec9e-121">To configure a valid address</span></span>  
  
1.  <span data-ttu-id="6ec9e-122">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** , puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="6ec9e-122">Click **Start**, click **All Programs**, click **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**, and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="6ec9e-123">Dans la racine de la Console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="6ec9e-123">In the Console Root, expand  **BizTalk Server Administration**, expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="6ec9e-124">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="6ec9e-124">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="6ec9e-125">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="6ec9e-125">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="6ec9e-126">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="6ec9e-126">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="6ec9e-127">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="6ec9e-127">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="6ec9e-128">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="6ec9e-128">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="6ec9e-129">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="6ec9e-129">In the **WCF [***transport type***] Transport Properties** dialog box, click the **General** tab.</span></span>  
  
9. <span data-ttu-id="6ec9e-130">Dans le **adresse (URI)** texte zone, vérifiez que l’adresse ne dépasse pas la longueur maximale de 255 caractères.</span><span class="sxs-lookup"><span data-stu-id="6ec9e-130">In the **Address (URI)** text box, ensure the address does not exceed the maximum length of 255 characters.</span></span>