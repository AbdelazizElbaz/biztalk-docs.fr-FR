---
title: "Composants d’envoi EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fce270db-a573-48b3-be15-0178a5b7785b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5520a0c1dd0a6ef7e42818314a9f87733aebcb8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-send-components"></a><span data-ttu-id="ba5f4-102">Composants d'envoi EDI</span><span class="sxs-lookup"><span data-stu-id="ba5f4-102">EDI Send Components</span></span>
<span data-ttu-id="ba5f4-103">Le pipeline et les composants de pipeline décrits dans cette rubrique traitent les messages EDI de type autre que EDI/AS2.</span><span class="sxs-lookup"><span data-stu-id="ba5f4-103">The pipeline and pipeline components described in this topic process EDI messages that are not EDI/AS2 messages.</span></span> <span data-ttu-id="ba5f4-104">Pour plus d’informations sur l’envoi d’EDI/AS2 ou les messages EDI/AS2, consultez [composants d’envoi AS2](../core/as2-send-components.md).</span><span class="sxs-lookup"><span data-stu-id="ba5f4-104">For information about the sending of EDI/AS2 or non-EDI/AS2 messages, see [AS2 Send Components](../core/as2-send-components.md).</span></span> <span data-ttu-id="ba5f4-105">Notez que les composants d'envoi AS2 exécutent le traitement EDI en plus du traitement AS2.</span><span class="sxs-lookup"><span data-stu-id="ba5f4-105">Note that AS2 send components perform EDI processing in addition to AS2 processing.</span></span>  
  
## <a name="edi-send-pipeline"></a><span data-ttu-id="ba5f4-106">Pipeline d'envoi EDI</span><span class="sxs-lookup"><span data-stu-id="ba5f4-106">EDI Send Pipeline</span></span>  
 <span data-ttu-id="ba5f4-107">Le traitement d'envoi EDI est effectué dans le pipeline EDISend suivant.</span><span class="sxs-lookup"><span data-stu-id="ba5f4-107">EDI send processing is performed in the following EDISend pipeline.</span></span> <span data-ttu-id="ba5f4-108">Ce pipeline est installé dans `Microsoft.BizTalk.Edi.EdiPipelines.dll` dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ba5f4-108">This pipeline is installed in `Microsoft.BizTalk.Edi.EdiPipelines.dll` in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span></span>  
  
 <span data-ttu-id="ba5f4-109">**Pipeline EDISend**</span><span class="sxs-lookup"><span data-stu-id="ba5f4-109">**EDISend Pipeline**</span></span>  
  
 <span data-ttu-id="ba5f4-110">Ce pipeline génère et envoie des messages EDI.</span><span class="sxs-lookup"><span data-stu-id="ba5f4-110">This pipeline generates and sends EDI messages.</span></span> <span data-ttu-id="ba5f4-111">En revanche, il ne traite pas les messages EDI de type AS2 reçus via HTTP</span><span class="sxs-lookup"><span data-stu-id="ba5f4-111">It does not process AS2-encoded EDI messages received over HTTP.</span></span> <span data-ttu-id="ba5f4-112">Le traitement des messages EDI codés AS2 est effectué par un pipeline AS2.</span><span class="sxs-lookup"><span data-stu-id="ba5f4-112">Processing of AS2-encoded EDI messages is performed by an AS2 pipeline.</span></span> <span data-ttu-id="ba5f4-113">Les pipelines d'envoi AS2 utilisent les mêmes composants que le pipeline EDI pour traiter les messages EDI.</span><span class="sxs-lookup"><span data-stu-id="ba5f4-113">The AS2 send pipelines use the same components to process EDI messages as the EDI pipeline uses.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba5f4-114">L'exécution du pipeline EDISend à partir d'une orchestration n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="ba5f4-114">Running the EDISend pipeline from an orchestration is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba5f4-115">Le pipeline AS2EDISend génère et envoie des messages EDI, via le transport AS2.</span><span class="sxs-lookup"><span data-stu-id="ba5f4-115">The AS2EDISend pipeline generates and sends EDI messages over AS2 transport.</span></span> <span data-ttu-id="ba5f4-116">Pour plus d’informations, consultez [composants d’envoi AS2](../core/as2-send-components.md).</span><span class="sxs-lookup"><span data-stu-id="ba5f4-116">For more information, see [AS2 Send Components](../core/as2-send-components.md).</span></span>  
  
 <span data-ttu-id="ba5f4-117">Ce pipeline est formé du composant de pipeline Assembleur EDI :</span><span class="sxs-lookup"><span data-stu-id="ba5f4-117">The pipeline consists of the EDI Assembler pipeline component:</span></span>  
  
## <a name="edi-send-pipeline-component"></a><span data-ttu-id="ba5f4-118">Composant de pipeline d'envoi EDI</span><span class="sxs-lookup"><span data-stu-id="ba5f4-118">EDI Send Pipeline Component</span></span>  
 <span data-ttu-id="ba5f4-119">Le pipeline EDISend utilise le composant de pipeline Assembleur EDI.</span><span class="sxs-lookup"><span data-stu-id="ba5f4-119">The EDISend pipeline uses the EDI Assembler pipeline component.</span></span> <span data-ttu-id="ba5f4-120">Ce composant est installé dans `Microsoft.BizTalk.Edi.PipelineComponents.dll` dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]composants de Pipeline\\.</span><span class="sxs-lookup"><span data-stu-id="ba5f4-120">This component is installed in `Microsoft.BizTalk.Edi.PipelineComponents.dll` in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Pipeline Components\\.</span></span>  
  
 <span data-ttu-id="ba5f4-121">Le plus souvent, l'assembleur EDI traite les échanges EDI codés dans le pipeline EDISend.</span><span class="sxs-lookup"><span data-stu-id="ba5f4-121">The EDI Assembler performs most processing of EDI-encoded interchanges in the EDISend Pipeline.</span></span> <span data-ttu-id="ba5f4-122">Pour plus d’informations sur la façon dont l’assembleur EDI traite les messages EDI, consultez [EDI assembleur fonctionnement](../core/how-the-edi-assembler-works.md).</span><span class="sxs-lookup"><span data-stu-id="ba5f4-122">For information about how the EDI Assembler processes EDI messages, see [How the EDI Assembler Works](../core/how-the-edi-assembler-works.md).</span></span>