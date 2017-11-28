---
title: "Onglet Définition du lot | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: btahl7.configurationexplorer.tab.batchdefinition
helpviewer_keywords:
- Batch Definition tab [Configuration Explorer]
- batching, configuring
- configuring, batching
ms.assetid: fe8685ef-5de5-4337-8691-8e4094056ace
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2270625a6e4512f2a99bea7a06812b601b48d44c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="batch-definition-tab"></a><span data-ttu-id="6d366-102">Onglet de définition de lot</span><span class="sxs-lookup"><span data-stu-id="6d366-102">Batch Definition Tab</span></span>
<span data-ttu-id="6d366-103">Vous utilisez la **définition de lot** onglet pour activer le traitement par lots de traitement par lot, entrant dans / de sortie de traitement par lot du lot, puis sélectionnez les schémas disponibles pour le traitement par lot sortant.</span><span class="sxs-lookup"><span data-stu-id="6d366-103">You use the **Batch Definition** tab to enable inbound batching, batch in/batch out batching, and select available schemas for outbound batching.</span></span>  
  
 <span data-ttu-id="6d366-104">Dans le **BTAHL7 Configuration Explorer** boîte de dialogue le **définition de lot** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="6d366-104">In the **BTAHL7 Configuration Explorer** dialog box, on the **Batch Definition** tab, do the following:</span></span>  
  
|<span data-ttu-id="6d366-105">Utiliser</span><span class="sxs-lookup"><span data-stu-id="6d366-105">Use this</span></span>|<span data-ttu-id="6d366-106">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="6d366-106">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="6d366-107">**Fragmentation requise**</span><span class="sxs-lookup"><span data-stu-id="6d366-107">**Fragmentation required**</span></span>|<span data-ttu-id="6d366-108">Sélectionnez l'une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="6d366-108">Select one of the following options:</span></span><br /><br /> <span data-ttu-id="6d366-109">-   **Oui**.</span><span class="sxs-lookup"><span data-stu-id="6d366-109">-   **Yes**.</span></span> <span data-ttu-id="6d366-110">Pour activer la fragmentation.</span><span class="sxs-lookup"><span data-stu-id="6d366-110">To enable fragmentation.</span></span><br /><span data-ttu-id="6d366-111">-   **Ne**.</span><span class="sxs-lookup"><span data-stu-id="6d366-111">-   **No**.</span></span> <span data-ttu-id="6d366-112">Pour désactiver la fragmentation.</span><span class="sxs-lookup"><span data-stu-id="6d366-112">To disable fragmentation.</span></span> <span data-ttu-id="6d366-113">**Remarque :** pour un tiers, **Fragmentation requise** par défaut est **non**.</span><span class="sxs-lookup"><span data-stu-id="6d366-113">**Note:**  For a new party, **Fragmentation Required** defaults to **No**.</span></span>|  
|<span data-ttu-id="6d366-114">**Prise en charge des échanges récupérables requise**</span><span class="sxs-lookup"><span data-stu-id="6d366-114">**Recoverable interchange support required**</span></span>|<span data-ttu-id="6d366-115">Sélectionnez l'une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="6d366-115">Select one of the following options:</span></span><br /><br /> <span data-ttu-id="6d366-116">-   **True**.</span><span class="sxs-lookup"><span data-stu-id="6d366-116">-   **True**.</span></span> <span data-ttu-id="6d366-117">Pour activer la prise en charge des échanges récupérables.</span><span class="sxs-lookup"><span data-stu-id="6d366-117">To enable recoverable interchange support.</span></span><br /><span data-ttu-id="6d366-118">-   **FALSE**.</span><span class="sxs-lookup"><span data-stu-id="6d366-118">-   **FALSE**.</span></span> <span data-ttu-id="6d366-119">Pour désactiver la prise en charge des échanges récupérables.</span><span class="sxs-lookup"><span data-stu-id="6d366-119">To disable recoverable interchange support.</span></span> <span data-ttu-id="6d366-120">**Remarque :** pour un tiers, **Fragmentation requise** par défaut est **FALSE** et est activée uniquement si la valeur de **Fragmentation requise** est **Non**.</span><span class="sxs-lookup"><span data-stu-id="6d366-120">**Note:**  For a new party, **Fragmentation Required** defaults to **FALSE** and is enabled only if the value of **Fragmentation Required** is **No**.</span></span>|  
|<span data-ttu-id="6d366-121">**Sélectionner les Messages**</span><span class="sxs-lookup"><span data-stu-id="6d366-121">**Select Messages**</span></span>|<span data-ttu-id="6d366-122">Sélectionnez les types de messages que vous souhaitez envoyer en tant que lot à partir de la fenêtre de Messages disponibles, puis cliquez sur le déplacement de la flèche vers la droite (**>>**).</span><span class="sxs-lookup"><span data-stu-id="6d366-122">Select the message types you want to send as a batch from the Available Messages window and then click the Move to right arrow (**>>**).</span></span><br /><br /> <span data-ttu-id="6d366-123">Pour les messages entrants de l’accusé de réception du lot, vous devez ajouter le type de message d’accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="6d366-123">To batch incoming ACK messages, you must add the ACK message type.</span></span> <span data-ttu-id="6d366-124">Pour faire en déployant le schéma de message d’accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="6d366-124">You do so by deploying the ACK message schema.</span></span>|  
|<span data-ttu-id="6d366-125">**Sélectionnez les accusés de réception de Message**</span><span class="sxs-lookup"><span data-stu-id="6d366-125">**Select Message Acknowledgments**</span></span>|<span data-ttu-id="6d366-126">Sélectionnez les types de messages pour lesquels vous souhaitez [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] pour envoyer les accusés de réception en tant que lot à partir de la fenêtre d’accusés de réception de Message disponibles, puis cliquez sur le déplacement de la flèche vers la droite (**>>**).</span><span class="sxs-lookup"><span data-stu-id="6d366-126">Select the message types for which you want [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] to send the acknowledgments as a batch from the Available Message Acks window, and then click the Move to right arrow (**>>**).</span></span>|