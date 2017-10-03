---
title: "Leçon 1 : Ajout de fichier plat Port de réception et emplacement | Documents Microsoft"
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
- receive ports, creating
- creating, receive ports
ms.assetid: 881f58d8-f541-4a85-b534-cb1ca627c002
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6fcd41cd38074377fa179e3a414b278521c31f26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-1-adding-flat-file-receive-port-and-location"></a><span data-ttu-id="cf934-102">Leçon 1 : Ajout d’un fichier plat Port de réception et emplacement</span><span class="sxs-lookup"><span data-stu-id="cf934-102">Lesson 1: Adding Flat File Receive Port and Location</span></span>
<span data-ttu-id="cf934-103">Le port de réception a toujours un emplacement de réception associés que vous devez configurer lorsque vous ajoutez le port de réception.</span><span class="sxs-lookup"><span data-stu-id="cf934-103">The receive port always has an associated receive location that you must configure when you add the receive port.</span></span> <span data-ttu-id="cf934-104">Un emplacement de réception définit une adresse spécifique pour un message entrant et le pipeline que vous utilisez pour traiter le message.</span><span class="sxs-lookup"><span data-stu-id="cf934-104">A receive location defines a specific address for an incoming message and the pipeline that you use to process the message.</span></span>  
  
### <a name="to-add-a-receive-port"></a><span data-ttu-id="cf934-105">Pour ajouter un port de réception</span><span class="sxs-lookup"><span data-stu-id="cf934-105">To add a receive port</span></span>  
  
1.  <span data-ttu-id="cf934-106">Dans la Console Administration de BizTalk Server, cliquez sur **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="cf934-106">In the BizTalk Server Administration Console, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
2.  <span data-ttu-id="cf934-107">Dans la boîte de dialogue Propriétés du Port de réception, dans le **nom** , tapez **MT103_FlatFile_ReceivePort**.</span><span class="sxs-lookup"><span data-stu-id="cf934-107">In the Receive Port Properties dialog box, in the **Name** box, type **MT103_FlatFile_ReceivePort**.</span></span>  
  
3.  <span data-ttu-id="cf934-108">Cliquez sur **appliquer** à lier le port, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="cf934-108">Click **Apply** to bind the port, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="cf934-109">Dans la Console Administration de BizTalk Server, cliquez sur **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="cf934-109">In the BizTalk Server Administration Console, right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
5.  <span data-ttu-id="cf934-110">Dans la boîte de dialogue un Port de réception de la sélectionner, cliquez sur **MT103_FlatFile_ReceivePort**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="cf934-110">In the Select a Receive Port dialog box, click **MT103_FlatFile_ReceivePort**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="cf934-111">Dans la boîte de dialogue Propriétés de l’emplacement de réception, dans le **nom** , tapez **MT103_FlatFile_ReceiveLocation**.</span><span class="sxs-lookup"><span data-stu-id="cf934-111">In the Receive Location Properties dialog box, in the **Name** box, type **MT103_FlatFile_ReceiveLocation**.</span></span>  
  
7.  <span data-ttu-id="cf934-112">Dans le **Transport** section, pour le **Type** zone de texte, cliquez sur la liste déroulante et sélectionnez **fichier**.</span><span class="sxs-lookup"><span data-stu-id="cf934-112">In the **Transport** section, for the **Type** text box, click the drop-down list, and then select **FILE**.</span></span>  
  
8.  <span data-ttu-id="cf934-113">Cliquez sur le **configurer** bouton à droite de la liste déroulante Type.</span><span class="sxs-lookup"><span data-stu-id="cf934-113">Click the **Configure** button to the right of the Type drop-down list.</span></span>  
  
9. <span data-ttu-id="cf934-114">Dans la boîte de dialogue Propriétés du Transport FILE, cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="cf934-114">In the FILE Transport Properties dialog box, click **Browse**.</span></span>  
  
10. <span data-ttu-id="cf934-115">Dans la boîte de dialogue Rechercher un dossier, déplacer vers le  **\<lecteur > : \Labs\Inbound** dossier, puis cliquez sur **créer un nouveau dossier**.</span><span class="sxs-lookup"><span data-stu-id="cf934-115">In the Browse For Folder dialog box, move to the **\<drive>:\Labs\Inbound** folder, and then click **Make New Folder**.</span></span>  
  
11. <span data-ttu-id="cf934-116">Créer un **FlatFile** dossier  **\<lecteur > : \Labs\Inbound**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="cf934-116">Create a **FlatFile** folder in **\<drive>:\Labs\Inbound**, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="cf934-117">Dans le **masque de fichier** , tapez  **\*.txt**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="cf934-117">In the **File mask** box, type **\*.txt**, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="cf934-118">Dans la boîte de dialogue Propriétés de l’emplacement de réception, vérifiez que **BizTalkServerApplication** est entré pour le **Gestionnaire de réception** boîte.</span><span class="sxs-lookup"><span data-stu-id="cf934-118">In the Receive Location Properties dialog box, ensure that **BizTalkServerApplication** is entered for the **Receive handler** box.</span></span>  
  
14. <span data-ttu-id="cf934-119">Pour le **Pipeline de réception** boîte, sélectionnez **MT103ReceivePipeline** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="cf934-119">For the **Receive Pipeline** box, select **MT103ReceivePipeline** from the drop-down list.</span></span>  
  
15. <span data-ttu-id="cf934-120">Cliquez sur **appliquer**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="cf934-120">Click **Apply**, and then click **OK**.</span></span>  
  
16. <span data-ttu-id="cf934-121">Dans la Console Administration de BizTalk Server, cliquez sur **emplacements de réception**, avec le bouton droit **MT103_FlatFile_ReceiveLocation**, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="cf934-121">In the BizTalk Server Administration Console, click **Receive Locations**, right-click **MT103_FlatFile_ReceiveLocation**, and then click **Enable**.</span></span>  
  
 <span data-ttu-id="cf934-122">Passez à [leçon 2 : ajout d’un Port d’envoi XML](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-an-xml-send-port.md).</span><span class="sxs-lookup"><span data-stu-id="cf934-122">Proceed to [Lesson 2: Adding an XML Send Port](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-an-xml-send-port.md).</span></span>