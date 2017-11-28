---
title: "Emplacement de réception requête-réponse transactionnelles n’est pas prise en charge | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c89b619-280c-4ab5-b6aa-06b14a075f8e
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34de32b338a78b598941d4e828c1a0b736dde4e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transactional-request-response-receive-location-is-not-supported"></a><span data-ttu-id="77ae4-102">L'emplacement de réception requête-réponse transactionnelles n'est pas pris en charge</span><span class="sxs-lookup"><span data-stu-id="77ae4-102">Transactional request-response receive location is not supported</span></span>
## <a name="details"></a><span data-ttu-id="77ae4-103">Détails</span><span class="sxs-lookup"><span data-stu-id="77ae4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="77ae4-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="77ae4-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="77ae4-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="77ae4-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="77ae4-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="77ae4-106">Event ID</span></span>|<span data-ttu-id="77ae4-107">0</span><span class="sxs-lookup"><span data-stu-id="77ae4-107">0</span></span>|  
|<span data-ttu-id="77ae4-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="77ae4-108">Event Source</span></span>|<span data-ttu-id="77ae4-109">0</span><span class="sxs-lookup"><span data-stu-id="77ae4-109">0</span></span>|  
|<span data-ttu-id="77ae4-110">Composant</span><span class="sxs-lookup"><span data-stu-id="77ae4-110">Component</span></span>|<span data-ttu-id="77ae4-111">0</span><span class="sxs-lookup"><span data-stu-id="77ae4-111">0</span></span>|  
|<span data-ttu-id="77ae4-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="77ae4-112">Symbolic Name</span></span>|<span data-ttu-id="77ae4-113">0</span><span class="sxs-lookup"><span data-stu-id="77ae4-113">0</span></span>|  
|<span data-ttu-id="77ae4-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="77ae4-114">Message Text</span></span>|<span data-ttu-id="77ae4-115">L'emplacement de réception requête-réponse transactionnelles n'est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="77ae4-115">Transactional request-response receive location is not supported.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="77ae4-116">Explication</span><span class="sxs-lookup"><span data-stu-id="77ae4-116">Explanation</span></span>  
 <span data-ttu-id="77ae4-117">Cette erreur indique que la transaction a été activée pour un emplacement de réception de requête-réponse WCF.</span><span class="sxs-lookup"><span data-stu-id="77ae4-117">This error indicates that the transaction was set to be enabled for a WCF request-response receive location.</span></span> <span data-ttu-id="77ae4-118">Les transactions ne sont pas prises en charge dans BizTalk pour un emplacement de réception de requête-réponse en raison de la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="77ae4-118">Transactions are not supported in BizTalk for a request-response receive location due to the message box database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="77ae4-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="77ae4-119">User Action</span></span>  
 <span data-ttu-id="77ae4-120">Pour les adaptateurs WCF standard, accédez au code de configuration de l'emplacement de réception de requête-réponse.</span><span class="sxs-lookup"><span data-stu-id="77ae4-120">For the standard WCF adapters, go to the code configuring the request-response receive location.</span></span> <span data-ttu-id="77ae4-121">Vérifiez que le **EnableTransaction** élément dans les données XML pour le **TransportTypeData** propriété de la **ITransportInfo** interface est définie sur **False** .</span><span class="sxs-lookup"><span data-stu-id="77ae4-121">Ensure that the **EnableTransaction** element in the XML data for the **TransportTypeData** property of the **ITransportInfo** interface is set to **False**.</span></span>  
  
 <span data-ttu-id="77ae4-122">Pour les adaptateurs WCF-Custom :</span><span class="sxs-lookup"><span data-stu-id="77ae4-122">For the WCF-Custom adapters:</span></span>  
  
1.  <span data-ttu-id="77ae4-123">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="77ae4-123">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="77ae4-124">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="77ae4-124">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="77ae4-125">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="77ae4-125">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="77ae4-126">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="77ae4-126">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="77ae4-127">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="77ae4-127">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="77ae4-128">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="77ae4-128">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="77ae4-129">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="77ae4-129">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="77ae4-130">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **liaison** onglet.</span><span class="sxs-lookup"><span data-stu-id="77ae4-130">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="77ae4-131">Assurez-vous que la propriété transactionFlow est définie sur **False**.</span><span class="sxs-lookup"><span data-stu-id="77ae4-131">Ensure that the transactionFlow property is set to **False**.</span></span>