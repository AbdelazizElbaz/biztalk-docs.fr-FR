---
title: "Port de réception Ajout MX | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4818d6af-df1d-481e-becf-1af633735248
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69123b876bdda4b5f999277a1710cdeb1cb61fe7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-mx-receive-port"></a><span data-ttu-id="09671-102">Ajout de MX Port de réception</span><span class="sxs-lookup"><span data-stu-id="09671-102">Adding MX Receive Port</span></span>
<span data-ttu-id="09671-103">**Pour ajouter un MX port de réception :**</span><span class="sxs-lookup"><span data-stu-id="09671-103">**To add an MX receive port:**</span></span>  
  
1.  <span data-ttu-id="09671-104">Démarrer **Administration de BizTalk Server** console.</span><span class="sxs-lookup"><span data-stu-id="09671-104">Start **BizTalk Server Administration** console.</span></span>  
  
2.  <span data-ttu-id="09671-105">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez **BizTalk Application 1**.</span><span class="sxs-lookup"><span data-stu-id="09671-105">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
3.  <span data-ttu-id="09671-106">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="09671-106">Right-click **Receive Ports**, point to **New**, and then click **One-Way Receive Port**.</span></span>  
  
4.  <span data-ttu-id="09671-107">Dans la boîte de dialogue Propriétés du Port de réception, dans la zone Nom, tapez **MX_ le Port de réception**.</span><span class="sxs-lookup"><span data-stu-id="09671-107">In the Receive Port Properties dialog box, in the Name box, type **MX_ Receive Port**.</span></span>  
  
5.  <span data-ttu-id="09671-108">Cliquez sur **appliquer** à lier le port, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="09671-108">Click **Apply** to bind the port, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="09671-109">Avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="09671-109">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
7.  <span data-ttu-id="09671-110">Dans la boîte de dialogue un Port de réception de la sélectionner, cliquez sur **le Port de réception MX_**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="09671-110">In the Select a Receive Port dialog box, click **MX_ Receive Port**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="09671-111">Dans la boîte de dialogue Propriétés de l’emplacement de réception, dans la zone Nom, tapez **MX_ un emplacement de réception**.</span><span class="sxs-lookup"><span data-stu-id="09671-111">In the Receive Location Properties dialog box, in the Name box, type **MX_ Receive Location**.</span></span>  
  
9. <span data-ttu-id="09671-112">Dans la section de Transport pour la zone de texte Type, cliquez sur la liste déroulante et sélectionnez **fichier**.</span><span class="sxs-lookup"><span data-stu-id="09671-112">In the Transport section, for the Type text box, click the drop-down list, and then select **FILE**.</span></span>  
  
10. <span data-ttu-id="09671-113">Cliquez sur le **configurer** bouton à droite de la liste déroulante Type.</span><span class="sxs-lookup"><span data-stu-id="09671-113">Click the **Configure** button to the right of the Type drop-down list.</span></span>  
  
11. <span data-ttu-id="09671-114">Dans la boîte de dialogue Propriétés du Transport FILE, cliquez sur **Parcourir**, puis sélectionnez un emplacement de fichier.</span><span class="sxs-lookup"><span data-stu-id="09671-114">In the FILE Transport Properties dialog box, click **Browse**, and then select a file location.</span></span>  
  
12. <span data-ttu-id="09671-115">Dans la boîte de dialogue Propriétés du Transport FILE, vérifiez que \*.xml est entré dans la zone de masque de fichier, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="09671-115">In the FILE Transport Properties dialog box, ensure that \*.xml is entered in the File Mask box, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="09671-116">Dans la boîte de dialogue Propriétés de l’emplacement de réception, assurez-vous que BizTalkServerApplication est entrée pour la zone d’un gestionnaire de réception.</span><span class="sxs-lookup"><span data-stu-id="09671-116">In the Receive Location Properties dialog box, ensure that BizTalkServerApplication is entered for the Receive handler box.</span></span>  
  
14. <span data-ttu-id="09671-117">Dans la boîte de Pipeline de réception, sélectionnez **Pipeline de réception** (le pipeline de réception qui a été déployé dans le projet de Pipeline) dans la liste déroulante, cliquez sur **appliquer**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="09671-117">In the Receive Pipeline box, select **Receive Pipeline** (the receive pipeline that has been deployed in the Pipeline project) from the drop-down list, click **Apply**, and then click **OK**.</span></span>  
  
15. <span data-ttu-id="09671-118">Avec le bouton droit à l’emplacement que vous venez de configurer, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="09671-118">Right-click the location you have just configured, and then click **Enable**.</span></span>