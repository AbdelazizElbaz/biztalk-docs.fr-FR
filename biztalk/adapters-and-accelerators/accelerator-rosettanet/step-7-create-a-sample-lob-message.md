---
title: "Étape 7 : Créer un exemple de Message LOB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, LOB
- loopback tutorial, creating LOB message
- creating, LOB messages
- LOBs, creating messages
ms.assetid: 3023bbc0-5bc4-4e5a-a345-c3253874f0d3
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1246f56615381d2627db3058dc821ba85bf8b74d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-7-create-a-sample-lob-message"></a><span data-ttu-id="9068f-102">Étape 7 : Créer un exemple de Message LOB</span><span class="sxs-lookup"><span data-stu-id="9068f-102">Step 7: Create a Sample LOB Message</span></span>
<span data-ttu-id="9068f-103">Dans cette étape, vous utilisez l’utilitaire de l’Application métier pour créer un exemple de message de métier (LOB).</span><span class="sxs-lookup"><span data-stu-id="9068f-103">In this step, you use the LOB Application utility to create a sample line-of-business (LOB) message.</span></span>  
  
### <a name="to-create-a-sample-message-using-the-lob-application-utility"></a><span data-ttu-id="9068f-104">Pour créer un exemple de message à l’aide de l’utilitaire d’Application métier</span><span class="sxs-lookup"><span data-stu-id="9068f-104">To create a sample message using the LOB Application utility</span></span>  
  
1.  <span data-ttu-id="9068f-105">Dans [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, accédez à \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK dossier, puis double-cliquez sur  **LOBApplication.exe**.</span><span class="sxs-lookup"><span data-stu-id="9068f-105">In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, move to \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK folder, and then double-click **LOBApplication.exe**.</span></span>  
  
2.  <span data-ttu-id="9068f-106">Dans le **Application métier** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9068f-106">In the **LOB Application** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="9068f-107">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="9068f-107">**Use this**</span></span>|<span data-ttu-id="9068f-108">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="9068f-108">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="9068f-109">**Nom du profil de base**</span><span class="sxs-lookup"><span data-stu-id="9068f-109">**Home Profile Name**</span></span>|<span data-ttu-id="9068f-110">Type **accueil**.</span><span class="sxs-lookup"><span data-stu-id="9068f-110">Type **HOME**.</span></span>|  
    |<span data-ttu-id="9068f-111">**Nom du partenaire commercial**</span><span class="sxs-lookup"><span data-stu-id="9068f-111">**Trading Partner Name**</span></span>|<span data-ttu-id="9068f-112">Type **partenaire**.</span><span class="sxs-lookup"><span data-stu-id="9068f-112">Type **PARTNER**.</span></span>|  
    |<span data-ttu-id="9068f-113">**Nom du PIP**</span><span class="sxs-lookup"><span data-stu-id="9068f-113">**PIP Name**</span></span>|<span data-ttu-id="9068f-114">Type **0c1**.</span><span class="sxs-lookup"><span data-stu-id="9068f-114">Type **0C1**.</span></span>|  
    |<span data-ttu-id="9068f-115">**Version PIP**</span><span class="sxs-lookup"><span data-stu-id="9068f-115">**PIP Version**</span></span>|<span data-ttu-id="9068f-116">Tapez **R01.02**.</span><span class="sxs-lookup"><span data-stu-id="9068f-116">Type **R01.02**.</span></span>|  
    |<span data-ttu-id="9068f-117">**Nom de fichier**</span><span class="sxs-lookup"><span data-stu-id="9068f-117">**File Name**</span></span>|<span data-ttu-id="9068f-118">Cliquez sur le bouton de sélection (**...** ) et les déplacer vers \< *lecteur*:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances.</span><span class="sxs-lookup"><span data-stu-id="9068f-118">Click the ellipsis button (**...**), and move to \<*drive*:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances.</span></span> <span data-ttu-id="9068f-119">Sélectionnez **0C1_Request.xml** dans la liste des fichiers, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="9068f-119">Select **0C1_Request.xml** from the list of files, and then click **Open**.</span></span>|  
    |<span data-ttu-id="9068f-120">**Catégorie de message**</span><span class="sxs-lookup"><span data-stu-id="9068f-120">**Message Category**</span></span>|<span data-ttu-id="9068f-121">Sélectionnez **Action** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="9068f-121">Select **Action** from the drop-down list.</span></span>|  
  
3.  <span data-ttu-id="9068f-122">Dans le **Application métier** boîte de dialogue, cliquez sur **envoyer un Message**.</span><span class="sxs-lookup"><span data-stu-id="9068f-122">In the **LOB Application** dialog box, click **Submit Message**.</span></span>  
  
 <span data-ttu-id="9068f-123">L’application métier génère un message de Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] en simulant un message d’origine généré par une application métier.</span><span class="sxs-lookup"><span data-stu-id="9068f-123">The LOB application generates a message for Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] simulating an original message generated by an LOB application.</span></span> <span data-ttu-id="9068f-124">Vous pouvez afficher l’état du message dans la fenêtre d’état.</span><span class="sxs-lookup"><span data-stu-id="9068f-124">You can view the status of the message in the Status window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9068f-125">Les exemples de messages supposent que les identificateurs entreprise Global (GBI) pour « HOME » et « Partenaire » 123456789 et 987654321, respectivement.</span><span class="sxs-lookup"><span data-stu-id="9068f-125">The sample messages assume that the Global Business Identifiers (GBI) for "HOME" and "PARTNER" are 123456789 and 987654321, respectively.</span></span> <span data-ttu-id="9068f-126">Pour utiliser un autre GBI, vous devez modifier le contenu de ces fichiers.</span><span class="sxs-lookup"><span data-stu-id="9068f-126">To use a different GBI, you must modify the content of these files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9068f-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9068f-127">See Also</span></span>  
 [<span data-ttu-id="9068f-128">Étape 8 : Afficher les messages dans les bases de données BTARN</span><span class="sxs-lookup"><span data-stu-id="9068f-128">Step 8: View Messages in the BTARN Databases</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-8-view-messages-in-the-btarn-databases.md)