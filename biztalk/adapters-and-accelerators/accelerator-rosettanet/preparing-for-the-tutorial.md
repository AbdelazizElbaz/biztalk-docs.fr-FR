---
title: "Conditions préalables pour le didacticiel RosettaNet Loopback dans BizTalk Server | Documents Microsoft"
description: "Conditions préalables pour parcourir le didacticiel de bouclage de l’accélérateur RosettaNet (BTARN) dans BizTalk Server"
caps.latest.revision: "9"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 08/09/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e26696c-86c5-448b-9cd6-bfd4a279151a
ms.author: mandia
ms.openlocfilehash: 9767f7823e80d4de67345ba0fbf59c1435adb8e1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="prepare-for-the-tutorial"></a><span data-ttu-id="2bdff-103">Préparer pour le didacticiel</span><span class="sxs-lookup"><span data-stu-id="2bdff-103">Prepare for the tutorial</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2bdff-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="2bdff-104">Prerequisites</span></span>
<span data-ttu-id="2bdff-105">Avant de commencer le didacticiel de bouclage :</span><span class="sxs-lookup"><span data-stu-id="2bdff-105">Before starting the Loopback tutorial:</span></span>
  
-   <span data-ttu-id="2bdff-106">[Installer et configurer](install-configure-biztalk-accelerator-for-rosettanet.md) l’accélérateur.</span><span class="sxs-lookup"><span data-stu-id="2bdff-106">[Install and configure](install-configure-biztalk-accelerator-for-rosettanet.md) the accelerator.</span></span> <span data-ttu-id="2bdff-107">Vous devrez peut-être ajouter le répertoire virtuel btarnhttpreceive à la liste d’exclusion de chemin d’accès géré Windows SharePoint dans l’Administration centrale de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="2bdff-107">You may have to add the btarnhttpreceive virtual directory to the Windows SharePoint managed path exclusion list in SharePoint Central Administration.</span></span>  
  
-   <span data-ttu-id="2bdff-108">Vérifiez que l’hôte BizTalkServerIsolatedHost l’hôte BizTalkServerApplication ont le **approuvé par authentification** option est activée.</span><span class="sxs-lookup"><span data-stu-id="2bdff-108">Be sure the BizTalkServerIsolatedHost and BizTalkServerApplication hosts have the **Authentication trusted** option enabled.</span></span> <span data-ttu-id="2bdff-109">Pour vérifier, ouvrez la console Administration de BizTalk Server, développez **hôtes**.</span><span class="sxs-lookup"><span data-stu-id="2bdff-109">To verify, open the BizTalk Server Administration console, and expand **Hosts**.</span></span> <span data-ttu-id="2bdff-110">Cliquez sur l’ordinateur hôte, sélectionnez **propriétés**et vérifiez **approuvé par authentification** s’il n’est pas activé.</span><span class="sxs-lookup"><span data-stu-id="2bdff-110">Right-click the host, select **Properties**, and check **Authentication Trusted** if it's not enabled.</span></span>  

    <span data-ttu-id="2bdff-111">Si vous avez plusieurs instances d’hôte, puis supprimez tous les mais une instance de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="2bdff-111">If you have more than one host instance, then delete all but one host instance.</span></span> <span data-ttu-id="2bdff-112">Par exemple, supprimez l’instance d’hôte isolé BizTalk Server et conserver l’instance de l’hôte BizTalkServerApplication).</span><span class="sxs-lookup"><span data-stu-id="2bdff-112">For example, delete the BizTalk Server Isolated Host instance, and keep the BizTalkServerApplication host instance).</span></span> <span data-ttu-id="2bdff-113">Permet de sélectionner **approuvé par authentification** sur l’hôte associé à cette instance et puis recréer les instances d’hôte supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="2bdff-113">This lets you select **Authentication Trusted** on the host associated with that instance, and then re-create the additional host instances.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="2bdff-114">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="2bdff-114">Next step</span></span>
 [<span data-ttu-id="2bdff-115">Étape 1 : Créer l’organisation d’origine</span><span class="sxs-lookup"><span data-stu-id="2bdff-115">Step 1: Create the Home Organization</span></span>](step-1-create-the-home-organization.md)