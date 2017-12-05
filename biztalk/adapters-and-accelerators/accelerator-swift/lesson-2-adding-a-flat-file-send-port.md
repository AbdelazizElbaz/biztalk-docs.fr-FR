---
title: "Leçon 2 : Ajout d’un Port d’envoi de fichier plat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, flat files
- flat files, send ports
- creating, send ports
- send ports, creating
ms.assetid: 33dceb0d-85f5-4e19-820f-cd33b60cd32a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d438a6fa68136b05b358a81f4b026350d92a6af4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="lesson-2-adding-a-flat-file-send-port"></a><span data-ttu-id="22c95-102">Leçon 2 : Ajout d’un Port d’envoi de fichier plat</span><span class="sxs-lookup"><span data-stu-id="22c95-102">Lesson 2: Adding a Flat File Send Port</span></span>
<span data-ttu-id="22c95-103">Dans cette leçon, vous configurez le port d’envoi et de l’emplacement d’envoi.</span><span class="sxs-lookup"><span data-stu-id="22c95-103">In this lesson, you configure the send port and the send location.</span></span> <span data-ttu-id="22c95-104">Le port d’envoi vous permet de définir comment vous souhaitez que les messages envoyés.</span><span class="sxs-lookup"><span data-stu-id="22c95-104">You use the send port to define how you want messages sent.</span></span> <span data-ttu-id="22c95-105">Vous créez également un emplacement de dossier de fichiers pour les messages envoyés.</span><span class="sxs-lookup"><span data-stu-id="22c95-105">You also create a file folder location for sent messages.</span></span>  
  
### <a name="to-add-a-flat-file-send-port"></a><span data-ttu-id="22c95-106">Pour ajouter un port d’envoi de fichier plat</span><span class="sxs-lookup"><span data-stu-id="22c95-106">To add a flat file send port</span></span>  
  
1.  <span data-ttu-id="22c95-107">Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="22c95-107">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="22c95-108">Dans la boîte de dialogue Propriétés de Port d’envoi dans le **nom** , tapez **MT103_FlatFile_SendPort**.</span><span class="sxs-lookup"><span data-stu-id="22c95-108">In the Send Port Properties dialog box, in the **Name** box, type **MT103_FlatFile_SendPort**.</span></span>  
  
3.  <span data-ttu-id="22c95-109">Dans le **Transport** section, pour le **Type** zone, cliquez sur la liste déroulante, puis sélectionnez **fichier**.</span><span class="sxs-lookup"><span data-stu-id="22c95-109">In the **Transport** section, for the **Type** box, click the drop-down list, and then select **FILE**.</span></span>  
  
4.  <span data-ttu-id="22c95-110">Cliquez sur le **configurer** bouton à droite de la liste déroulante Type.</span><span class="sxs-lookup"><span data-stu-id="22c95-110">Click the **Configure** button to the right of the Type drop-down list.</span></span>  
  
5.  <span data-ttu-id="22c95-111">Dans la boîte de dialogue Propriétés du Transport FILE, cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="22c95-111">In the FILE Transport Properties dialog box, click **Browse**.</span></span>  
  
6.  <span data-ttu-id="22c95-112">Dans la boîte de dialogue Rechercher un dossier, déplacer vers le  **\<lecteur\>: \Labs** dossier, puis cliquez sur **créer un nouveau dossier**.</span><span class="sxs-lookup"><span data-stu-id="22c95-112">In the Browse For Folder dialog box, move to the **\<drive\>:\Labs** folder, and then click **Make New Folder**.</span></span>  
  
7.  <span data-ttu-id="22c95-113">Créer un **sortant** dossier  **\<lecteur\>: \Labs**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="22c95-113">Create an **Outbound** folder in **\<drive\>:\Labs**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="22c95-114">Dans le **nom de fichier** , tapez **%MessageID%.txt**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="22c95-114">In the **File name** box, type **%MessageID%.txt**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="22c95-115">Dans la boîte de dialogue Propriétés de Port d’envoi, cliquez sur la liste déroulante pour le **pipeline d’envoi** zone, puis sélectionnez **MT103SendPipeline**.</span><span class="sxs-lookup"><span data-stu-id="22c95-115">In the Send Port Properties dialog box, click the drop-down list for the **Send pipeline** box, and then select **MT103SendPipeline**.</span></span>  
  
10. <span data-ttu-id="22c95-116">Dans le volet gauche, cliquez sur **filtres**, puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="22c95-116">In the left pane, click **Filters**, and then do the following:</span></span>  
  
    |<span data-ttu-id="22c95-117">Utiliser</span><span class="sxs-lookup"><span data-stu-id="22c95-117">Use this</span></span>|<span data-ttu-id="22c95-118">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="22c95-118">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="22c95-119">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="22c95-119">**Property**</span></span>|<span data-ttu-id="22c95-120">Sélectionnez **BTS. ReceivePortName**.</span><span class="sxs-lookup"><span data-stu-id="22c95-120">Select **BTS.ReceivePortName**.</span></span>|  
    |<span data-ttu-id="22c95-121">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="22c95-121">**Operator**</span></span>|<span data-ttu-id="22c95-122">Sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="22c95-122">Select **==**.</span></span>|  
    |<span data-ttu-id="22c95-123">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="22c95-123">**Value**</span></span>|<span data-ttu-id="22c95-124">Type **MT103_XML_ReceivePort**.</span><span class="sxs-lookup"><span data-stu-id="22c95-124">Type **MT103_XML_ReceivePort**.</span></span>|  
  
11. <span data-ttu-id="22c95-125">Cliquez sur **appliquer**, puis cliquez sur **OK.**</span><span class="sxs-lookup"><span data-stu-id="22c95-125">Click **Apply**, and then click **OK.**</span></span>  
  
12. <span data-ttu-id="22c95-126">Dans le **Ports d’envoi** volet, avec le bouton droit **MT103_FlatFile_SendPort**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="22c95-126">In the **Send Ports** pane, right-click **MT103_FlatFile_SendPort**, and then click **Start**.</span></span>  
  
 <span data-ttu-id="22c95-127">Passez à [Module 5 : ajout d’un fichier plat emplacement de réception et Port d’envoi XML](../../adapters-and-accelerators/accelerator-swift/module-5-adding-a-flat-file-receive-location-and-xml-send-port.md).</span><span class="sxs-lookup"><span data-stu-id="22c95-127">Proceed to [Module 5: Adding a Flat File Receive Location and XML Send Port](../../adapters-and-accelerators/accelerator-swift/module-5-adding-a-flat-file-receive-location-and-xml-send-port.md).</span></span>