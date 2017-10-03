---
title: "Pipeline d’envoi envoyer un lot conservé avec un document XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6765576a-134f-4856-911c-2f603b6479bd
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 14bd61538398bb11967cbbe750a4fadc016a5168
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sending-a-preserved-batch-with-an-xml-send-pipeline"></a><span data-ttu-id="092a6-102">Envoi d'un lot conservé à l'aide d'un pipeline d'envoi XML</span><span class="sxs-lookup"><span data-stu-id="092a6-102">Sending a Preserved Batch with an XML Send Pipeline</span></span>
<span data-ttu-id="092a6-103">Normalement, un lot conservé est envoyé via un pipeline d'envoi EDI.</span><span class="sxs-lookup"><span data-stu-id="092a6-103">Normally, a preserved batch is sent using an EDI send pipeline.</span></span> <span data-ttu-id="092a6-104">Toutefois, vous pouvez également envoyer un lot conservé au moyen d'un pipeline d'envoi XML.</span><span class="sxs-lookup"><span data-stu-id="092a6-104">However, you can also use an XML send pipeline to send a preserved batch.</span></span> <span data-ttu-id="092a6-105">Comme le lot conservé qui a été généré puis déposé dans la base de données MessageBox par le pipeline de réception EDI est au format XML, le pipeline d'envoi XML le transmet au format XML.</span><span class="sxs-lookup"><span data-stu-id="092a6-105">Since the preserved batch that is generated and dropped in the MessageBox by the EDI receive pipeline is in the XML format, the XML send pipeline would pass along the batch in XML format.</span></span>  
  
 <span data-ttu-id="092a6-106">Pour envoyer un lot conservé à l'aide du pipeline d'envoi XML, vous devez déployer un projet avec le schéma de lot applicable et les schémas de document pour chaque type de message au sein de l'échange.</span><span class="sxs-lookup"><span data-stu-id="092a6-106">To send a preserved batch using the XML send pipeline, you have to deploy a project with the applicable batch schema and the document schemas for each message type in the interchange.</span></span> <span data-ttu-id="092a6-107">Vous devez également modifier l'espace de noms du schéma de lot que vous déployez dans le projet.</span><span class="sxs-lookup"><span data-stu-id="092a6-107">In addition, you also have to change the namespace for the batch schema that you deploy in the project.</span></span> <span data-ttu-id="092a6-108">Si vous ne procédez pas de cette manière, l'espace de noms dans le fichier XML de lot conservé risque de différer de l'espace de noms dans le schéma de lot.</span><span class="sxs-lookup"><span data-stu-id="092a6-108">If you do not do so, the namespace in the preserved batch XML file would not correspond to the namespace for the batch schema.</span></span> <span data-ttu-id="092a6-109">Vous devez modifier l'espace de noms dans le schéma de lot comme indiqué dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="092a6-109">You have to change the namespace for the batch schema as shown in the following table:</span></span>  
  
|<span data-ttu-id="092a6-110">Pour ce type de codage :</span><span class="sxs-lookup"><span data-stu-id="092a6-110">For this encoding type:</span></span>|<span data-ttu-id="092a6-111">Modifiez cet espace de noms dans le schéma de lot :</span><span class="sxs-lookup"><span data-stu-id="092a6-111">Change this namespace in the batch schema:</span></span>|<span data-ttu-id="092a6-112">Sur l'espace de noms suivant :</span><span class="sxs-lookup"><span data-stu-id="092a6-112">To the following namespace:</span></span>|  
|-----------------------------|------------------------------------------------|---------------------------------|  
|<span data-ttu-id="092a6-113">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="092a6-113">EDIFACT</span></span>|`http://schemas.microsoft.com/Edi/Edifact`|`http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006/InterchangeXML`|  
|<span data-ttu-id="092a6-114">X12</span><span class="sxs-lookup"><span data-stu-id="092a6-114">X12</span></span>|`http://schemas.microsoft.com/Edi/X12_BatchSchema`|`http://schemas.microsoft.com/BizTalk/EDI/X12/2006/InterchangeXML`|  
  
 <span data-ttu-id="092a6-115">Ce problème ne concerne pas l'Assembleur EDI.</span><span class="sxs-lookup"><span data-stu-id="092a6-115">This is not an issue with the EDI Assembler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="092a6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="092a6-116">See Also</span></span>  
 [<span data-ttu-id="092a6-117">Configuration des lots EDI</span><span class="sxs-lookup"><span data-stu-id="092a6-117">Configuring EDI Batches</span></span>](../core/configuring-edi-batches.md)