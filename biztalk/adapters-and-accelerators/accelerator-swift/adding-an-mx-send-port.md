---
title: "Ajout d’un Port d’envoi MX | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3ad5d2f-1fcb-49d4-9974-664733308f45
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3cd4c16658ad0ff6b85976fbc6a97c4f397acbdb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-an-mx-send-port"></a><span data-ttu-id="95e67-102">Ajout d’un Port d’envoi de MX</span><span class="sxs-lookup"><span data-stu-id="95e67-102">Adding an MX Send Port</span></span>
<span data-ttu-id="95e67-103">**Pour ajouter un port d’envoi MX :**</span><span class="sxs-lookup"><span data-stu-id="95e67-103">**To add an MX send port:**</span></span>  
  
1.  <span data-ttu-id="95e67-104">Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="95e67-104">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-Way Send Port**.</span></span>  
  
2.  <span data-ttu-id="95e67-105">Dans la boîte de dialogue Propriétés de Port d’envoi dans la zone Nom du type **MX_SendPort**.</span><span class="sxs-lookup"><span data-stu-id="95e67-105">In the Send Port Properties dialog box, in the Name box type **MX_SendPort**.</span></span>  
  
3.  <span data-ttu-id="95e67-106">Dans la section de Transport, dans la zone Type, cliquez sur la liste déroulante et sélectionnez **fichier**.</span><span class="sxs-lookup"><span data-stu-id="95e67-106">In the Transport section, for the Type box, click the drop-down list, and then select **FILE**.</span></span>  
  
4.  <span data-ttu-id="95e67-107">Cliquez sur le **configurer** bouton à droite de la liste déroulante Type.</span><span class="sxs-lookup"><span data-stu-id="95e67-107">Click the **Configure** button to the right of the Type drop-down list.</span></span>  
  
5.  <span data-ttu-id="95e67-108">Dans la boîte de dialogue Propriétés du Transport FILE, cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="95e67-108">In the FILE Transport Properties dialog box, click **Browse**.</span></span>  
  
6.  <span data-ttu-id="95e67-109">Dans le dossier boîte de dialogue Rechercher, sélectionnez un emplacement de fichier.</span><span class="sxs-lookup"><span data-stu-id="95e67-109">In the Browse for Folder dialog box, select a file location.</span></span>  
  
7.  <span data-ttu-id="95e67-110">Dans la zone Nom de fichier, tapez **%MessageID%.xml**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="95e67-110">In the File name box, type **%MessageID%.xml**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="95e67-111">Dans la boîte de dialogue Propriétés de Port d’envoi, cliquez sur la liste déroulante de la zone de pipeline d’envoi, puis sélectionnez le pipeline d’envoi que vous avez déployé dans le projet de pipeline.</span><span class="sxs-lookup"><span data-stu-id="95e67-111">In the Send Port Properties dialog box, click the drop-down list for the send pipeline box, and then select the send pipeline you have deployed in the pipeline project.</span></span>  
  
9. <span data-ttu-id="95e67-112">Dans le volet gauche, cliquez sur **filtres**, puis spécifiez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="95e67-112">In the left pane, click **Filters**, and then specify the following:</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="95e67-113">Propriété</span><span class="sxs-lookup"><span data-stu-id="95e67-113">Property</span></span>|<span data-ttu-id="95e67-114">Microsoft.Solutions.MX_A4SWIFT. Property.MX_A4SWIFT_Failed</span><span class="sxs-lookup"><span data-stu-id="95e67-114">Microsoft.Solutions.MX_A4SWIFT.Property.MX_A4SWIFT_Failed</span></span>|  
    |<span data-ttu-id="95e67-115">Opérateur</span><span class="sxs-lookup"><span data-stu-id="95e67-115">Operator</span></span>|<span data-ttu-id="95e67-116">Sélectionnez ==</span><span class="sxs-lookup"><span data-stu-id="95e67-116">Select ==</span></span>|  
    |<span data-ttu-id="95e67-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="95e67-117">Value</span></span>|<span data-ttu-id="95e67-118">False</span><span class="sxs-lookup"><span data-stu-id="95e67-118">False</span></span>|  
  
10. <span data-ttu-id="95e67-119">Cliquez sur **appliquer**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="95e67-119">Click **Apply**, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="95e67-120">Dans le volet Ports d’envoi, cliquez sur **MX_SendPort**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="95e67-120">In the Send Ports pane, right-click **MX_SendPort**, and then click **Start**.</span></span>