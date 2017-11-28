---
title: "Emplacement de réception pour la réception de l’Application Back-End-création de la FRR | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, creating
- creating, receive locations
- FRR, creating receive locations
ms.assetid: 78bd8084-ddec-4066-a474-ab5b1a0a849f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46895ff64e6585c8b80979c09874dffb510cf049
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-the-frr-receive-location-for-receiving-from-the-back-end-application"></a><span data-ttu-id="aa8db-102">Création de la FRR emplacement de réception pour la réception de l’Application Back-End</span><span class="sxs-lookup"><span data-stu-id="aa8db-102">Creating the FRR Receive Location for Receiving from the Back-End Application</span></span>
<span data-ttu-id="aa8db-103">Pour effectuer le rapprochement de réponse de FIN, vous devez créer un emplacement de réception qui reçoit un message à partir de l’application principale dans [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aa8db-103">To perform FIN Response Reconciliation, you need to create a receive location that receives a message from the back-end application into [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span></span>  
  
 <span data-ttu-id="aa8db-104">**Résumé**</span><span class="sxs-lookup"><span data-stu-id="aa8db-104">**Summary**</span></span>  
  
 <span data-ttu-id="aa8db-105">Créer un emplacement de réception avec les propriétés suivantes et les composants :</span><span class="sxs-lookup"><span data-stu-id="aa8db-105">Create a receive location with the following properties and components:</span></span>  
  
|<span data-ttu-id="aa8db-106">Propriété/composant</span><span class="sxs-lookup"><span data-stu-id="aa8db-106">Property/Component</span></span>|<span data-ttu-id="aa8db-107">Paramètre</span><span class="sxs-lookup"><span data-stu-id="aa8db-107">Setting</span></span>|  
|-------------------------|-------------|  
|<span data-ttu-id="aa8db-108">Port de réception</span><span class="sxs-lookup"><span data-stu-id="aa8db-108">Receive port</span></span>|<span data-ttu-id="aa8db-109">Port unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="aa8db-109">One-way port</span></span>|  
|<span data-ttu-id="aa8db-110">Type de transport </span><span class="sxs-lookup"><span data-stu-id="aa8db-110">Transport type</span></span>|<span data-ttu-id="aa8db-111">Le type de transport utilisé par l’application principale</span><span class="sxs-lookup"><span data-stu-id="aa8db-111">The transport type used by the back-end application</span></span>|  
|<span data-ttu-id="aa8db-112">Adresse URI</span><span class="sxs-lookup"><span data-stu-id="aa8db-112">Address URI</span></span>|<span data-ttu-id="aa8db-113">Selon les besoins pour le type de transport</span><span class="sxs-lookup"><span data-stu-id="aa8db-113">As required for the transport type</span></span>|  
|<span data-ttu-id="aa8db-114">Gestionnaire de réception</span><span class="sxs-lookup"><span data-stu-id="aa8db-114">Receive handler</span></span>|<span data-ttu-id="aa8db-115">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="aa8db-115">BizTalkServerApplication</span></span>|  
|<span data-ttu-id="aa8db-116">Pipeline de réception</span><span class="sxs-lookup"><span data-stu-id="aa8db-116">Receive pipeline</span></span>|<span data-ttu-id="aa8db-117">Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pipeline que vous avez créé pour FRR de réception</span><span class="sxs-lookup"><span data-stu-id="aa8db-117">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receive pipeline that you created for FRR</span></span>|  
  
### <a name="to-add-an-frr-receive-location-for-receiving-from-the-back-end-application"></a><span data-ttu-id="aa8db-118">Pour ajouter un FRR emplacement de réception pour la réception de l’application principale</span><span class="sxs-lookup"><span data-stu-id="aa8db-118">To add an FRR receive location for receiving from the back-end application</span></span>  
  
1.  <span data-ttu-id="aa8db-119">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, **groupe BizTalk**, **Applications**, et **Application BizTalk 1** nœuds.</span><span class="sxs-lookup"><span data-stu-id="aa8db-119">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and **BizTalk Application 1** nodes.</span></span>  
  
2.  <span data-ttu-id="aa8db-120">Avec le bouton droit **Pipelines**, puis cliquez sur **Actualiser**.</span><span class="sxs-lookup"><span data-stu-id="aa8db-120">Right-click **Pipelines**, and then click **Refresh**.</span></span>  
  
3.  <span data-ttu-id="aa8db-121">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="aa8db-121">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
4.  <span data-ttu-id="aa8db-122">Dans la boîte de dialogue Propriétés du Port de réception, dans le **nom** , tapez un nom pour le port de réception, par exemple FRRBackEndReceivePort.</span><span class="sxs-lookup"><span data-stu-id="aa8db-122">In the Receive Port Properties dialog box, in the **Name** box, type a name for the receive port, such as FRRBackEndReceivePort.</span></span>  
  
5.  <span data-ttu-id="aa8db-123">Cliquez sur **appliquer** à lier le port, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="aa8db-123">Click **Apply** to bind the port, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="aa8db-124">Dans la Console d’Administration, cliquez sur **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="aa8db-124">In the Administration Console, right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
7.  <span data-ttu-id="aa8db-125">Dans la boîte de dialogue un Port de réception, sélectionnez, sélectionnez le port de réception que vous venez créé, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="aa8db-125">In the Select a Receive Port dialog box, select the receive port that you just created, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="aa8db-126">Dans la boîte de dialogue Propriétés de l’emplacement de réception, dans le **nom** , tapez un nom pour l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="aa8db-126">In the Receive Location Properties dialog box, in the **Name** box, type a name for the receive location.</span></span>  
  
9. <span data-ttu-id="aa8db-127">Dans le **Transport** section, pour le **Type** zone de texte, sélectionnez le type de transport utilisé par l’application principale.</span><span class="sxs-lookup"><span data-stu-id="aa8db-127">In the **Transport** section, for the **Type** text box, select the transport type used by the back-end application.</span></span>  
  
10. <span data-ttu-id="aa8db-128">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="aa8db-128">Click **Configure**.</span></span>  
  
11. <span data-ttu-id="aa8db-129">Dans la boîte de dialogue Propriétés du Transport FILE, renseignez les propriétés requises pour le type de transport, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="aa8db-129">In the FILE Transport Properties dialog box, fill in the properties required for the transport type, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="aa8db-130">Dans la boîte de dialogue Propriétés de l’emplacement de réception pour **Gestionnaire de réception**, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="aa8db-130">In the Receive Location Properties dialog box, for **Receive Handler**, select **BizTalkServerApplication**.</span></span>  
  
13. <span data-ttu-id="aa8db-131">Dans la boîte de dialogue Propriétés de l’emplacement de réception pour **Pipeline de réception**, sélectionnez le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pipeline que vous avez créé pour FRR de réception.</span><span class="sxs-lookup"><span data-stu-id="aa8db-131">In the Receive Location Properties dialog box, for **Receive Pipeline**, select the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receive pipeline that you created for FRR.</span></span>  
  
14. <span data-ttu-id="aa8db-132">Cliquez sur **appliquer**, puis cliquez sur **OK** pour fermer la **propriétés de l’emplacement de réception** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="aa8db-132">Click **Apply**, and then click **OK** to close the **Receive Location Properties** dialog box.</span></span>  
  
15. <span data-ttu-id="aa8db-133">Dans l’Explorateur BizTalk, cliquez sur l’emplacement de réception que vous venez créé, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="aa8db-133">In BizTalk Explorer, right-click the receive location that you just created, and then click **Enable**.</span></span>