---
title: "Importation de schémas dans BizTalk Server Projects1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing schemas
- orchestration variables, messages
- schemas, importing into BizTalk Server
- orchestration types, port types
ms.assetid: fa640195-a735-4201-a893-48f3405ddcb5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c0e67ef4e47b62e0381d882739b2fdc012ba621
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importing-schemas-into-biztalk-server-projects"></a><span data-ttu-id="bf919-102">Importation de schémas dans des projets BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="bf919-102">Importing Schemas into BizTalk Server Projects</span></span>
<span data-ttu-id="bf919-103">Les informations suivantes décrivent l'importation des schémas dans un projet BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="bf919-103">The following information describes how to import schemas into a BizTalk Server project.</span></span>  
  
## <a name="importing-schemas"></a><span data-ttu-id="bf919-104">Importation des schémas</span><span class="sxs-lookup"><span data-stu-id="bf919-104">Importing Schemas</span></span>  
  
#### <a name="to-import-schemas"></a><span data-ttu-id="bf919-105">Pour importer des schémas</span><span class="sxs-lookup"><span data-stu-id="bf919-105">To import schemas</span></span>  
  
1.  <span data-ttu-id="bf919-106">Dans l’Explorateur de solutions, cliquez sur le projet, pointez sur **ajouter**, puis sélectionnez **ajouter les éléments générés**.</span><span class="sxs-lookup"><span data-stu-id="bf919-106">In Solution Explorer, right-click the project, point to **Add**, and select **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="bf919-107">Cliquez sur **ajouter un adaptateur**, puis sélectionnez **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="bf919-107">Click **Add adapter**, and then select **Open**.</span></span>  
  
3.  <span data-ttu-id="bf919-108">Sélectionnez l’adaptateur**, J.D. Edwards OneWorld XE**.</span><span class="sxs-lookup"><span data-stu-id="bf919-108">Select the adapter**, J.D. Edwards OneWorld XE**.</span></span>  
  
4.  <span data-ttu-id="bf919-109">Dans la liste déroulante, sélectionnez le port **SSOSendToJD Edwards OneWorld XE**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="bf919-109">In the drop-down list, select the port **SSOSendToJD Edwards OneWorld XE**, and then click **Next**.</span></span>  
  
     <span data-ttu-id="bf919-110">Le myJ.D.</span><span class="sxs-lookup"><span data-stu-id="bf919-110">The myJ.D.</span></span> <span data-ttu-id="bf919-111">Edwards OneWorld système logique apparaît dans le navigateur (ce système logique a été créé avec le SSOSendToJ.D.</span><span class="sxs-lookup"><span data-stu-id="bf919-111">Edwards OneWorld XESSO logical system appears in the browser (this logical system was created with the SSOSendToJ.D.</span></span> <span data-ttu-id="bf919-112">Port OneWorld XE Edwards).</span><span class="sxs-lookup"><span data-stu-id="bf919-112">Edwards OneWorld XE port).</span></span>  
  
5.  <span data-ttu-id="bf919-113">Développez **myJ.D. Edwards OneWorld XESSO**.</span><span class="sxs-lookup"><span data-stu-id="bf919-113">Expand **myJ.D. Edwards OneWorld XESSO**.</span></span>  
  
6.  <span data-ttu-id="bf919-114">Cliquez sur l’icône de flèche pour déplacer l’élément (ou faites simplement glisser) dans le **transmission** fenêtre, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bf919-114">Click the arrow icon to move the item (or simply drag it) into the **Transmit** window, and then click **OK**.</span></span>  
  
     <span data-ttu-id="bf919-115">Les schémas sont ajoutés au projet SSOSchedule.</span><span class="sxs-lookup"><span data-stu-id="bf919-115">The schemas are added to the SSOSchedule project.</span></span>  
  
7.  <span data-ttu-id="bf919-116">Dans l’Explorateur de solutions, développez **projet SSOSchedule**.</span><span class="sxs-lookup"><span data-stu-id="bf919-116">In Solution Explorer, expand **SSOSchedule project**.</span></span>  
  
8.  <span data-ttu-id="bf919-117">Avec le bouton droit **biztalkorchestration.odx**, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="bf919-117">Right-click **BizTalk orchestration.odx**, and then click **Delete**.</span></span>  
  
9. <span data-ttu-id="bf919-118">Dans l’Explorateur de solutions, double-cliquez sur **GetList.odx** pour examiner l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="bf919-118">In Solution Explorer, double-click **GetList.odx** to inspect the orchestration.</span></span>  
  
## <a name="orchestration-types---port-types"></a><span data-ttu-id="bf919-119">Types d'orchestration - Types de ports</span><span class="sxs-lookup"><span data-stu-id="bf919-119">Orchestration Types - Port Types</span></span>  
  
-   <span data-ttu-id="bf919-120">**PortTypeIn / / demande :** SSOSchedule.myJ.D.</span><span class="sxs-lookup"><span data-stu-id="bf919-120">**PortTypeIn/In/Request:** SSOSchedule.myJ.D.</span></span> <span data-ttu-id="bf919-121">Edwards OneWorld XEsso_transmitService_3.method</span><span class="sxs-lookup"><span data-stu-id="bf919-121">Edwards OneWorld XEsso_transmitService_3.method</span></span>  
  
-   <span data-ttu-id="bf919-122">**PortTypeOut/Out/réponse :** SSOSchedule.myJ.D.</span><span class="sxs-lookup"><span data-stu-id="bf919-122">**PortTypeOut/Out/response:** SSOSchedule.myJ.D.</span></span> <span data-ttu-id="bf919-123">Edwards OneWorld XE sso_transmitService_3.methodResponse</span><span class="sxs-lookup"><span data-stu-id="bf919-123">Edwards OneWorld XE sso_transmitService_3.methodResponse</span></span>  
  
-   <span data-ttu-id="bf919-124">**PortTypeInOut/InOut/demande :** SSOSchedule.myJ.D.</span><span class="sxs-lookup"><span data-stu-id="bf919-124">**PortTypeInOut/InOut/Request:** SSOSchedule.myJ.D.</span></span> <span data-ttu-id="bf919-125">Edwards OneWorld XEsso_transmitService_3.method</span><span class="sxs-lookup"><span data-stu-id="bf919-125">Edwards OneWorld XEsso_transmitService_3.method</span></span>  
  
-   <span data-ttu-id="bf919-126">**PortTypeInOut/InOut/réponse :** SSOSchedule.myJ.D.</span><span class="sxs-lookup"><span data-stu-id="bf919-126">**PortTypeInOut/InOut/Response:** SSOSchedule.myJ.D.</span></span> <span data-ttu-id="bf919-127">Edwards OneWorld XE sso_transmitService_3.methodResponse</span><span class="sxs-lookup"><span data-stu-id="bf919-127">Edwards OneWorld XE sso_transmitService_3.methodResponse</span></span>  
  
## <a name="orchestration-variables---messages"></a><span data-ttu-id="bf919-128">Variables d'orchestration - Messages</span><span class="sxs-lookup"><span data-stu-id="bf919-128">Orchestration Variables - Messages</span></span>  
  
-   <span data-ttu-id="bf919-129">**(Messagein) :** SSOSchedule.myJ.D.</span><span class="sxs-lookup"><span data-stu-id="bf919-129">**MessageIn:** SSOSchedule.myJ.D.</span></span> <span data-ttu-id="bf919-130">Edwards OneWorld XEsso_transmitService_3.method</span><span class="sxs-lookup"><span data-stu-id="bf919-130">Edwards OneWorld XEsso_transmitService_3.method</span></span>  
  
-   <span data-ttu-id="bf919-131">**(Messageout) :** SSOSchedule.myJ.D.</span><span class="sxs-lookup"><span data-stu-id="bf919-131">**MessageOut:** SSOSchedule.myJ.D.</span></span> <span data-ttu-id="bf919-132">Edwards OneWorld XE sso_transmitService_3.methodResponse</span><span class="sxs-lookup"><span data-stu-id="bf919-132">Edwards OneWorld XE sso_transmitService_3.methodResponse</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf919-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf919-133">See Also</span></span>  
 [<span data-ttu-id="bf919-134">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="bf919-134">Using Single Sign-On</span></span>](../core/using-single-sign-on3.md)