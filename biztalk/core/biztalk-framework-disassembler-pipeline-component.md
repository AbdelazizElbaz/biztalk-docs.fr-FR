---
title: "Composant de Pipeline Désassembleur BizTalk Framework | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, BizTalk Framework Disassembler
- BizTalk Framework Disassembler [pipeline component]
ms.assetid: 48d6c530-5c02-4c70-ad11-0ea6c3c808f8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1ab54ddb9ef0b5fa389e6716fc4426978dcbd7a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-framework-disassembler-pipeline-component"></a><span data-ttu-id="09274-102">Composant de Pipeline Désassembleur BizTalk Framework</span><span class="sxs-lookup"><span data-stu-id="09274-102">BizTalk Framework Disassembler Pipeline Component</span></span>
<span data-ttu-id="09274-103">Le composant de pipeline Désassembleur BizTalk Framework analyse les données XML et détermine si elles contiennent une charge de message basée sur BizTalk Framework.</span><span class="sxs-lookup"><span data-stu-id="09274-103">The BizTalk Framework Disassembler pipeline component parses XML data and determines whether it contains a BizTalk Framework-based messaging payload.</span></span> <span data-ttu-id="09274-104">Le composant de pipeline enregistre le contexte du message et en crée un nouveau avec la propriété BizTalk Framework qui doit être générée.</span><span class="sxs-lookup"><span data-stu-id="09274-104">The pipeline component saves the message context, and a new message context is created with the BizTalk Framework property that needs to be generated.</span></span> <span data-ttu-id="09274-105">La propriété est utilisée pour acheminer le message au gestionnaire d’entrée BizTalk Framework, lui permettant de recevoir le message à traiter.</span><span class="sxs-lookup"><span data-stu-id="09274-105">This property is used to route the message to the BizTalk Framework inbound handler, so it can receive the message to process.</span></span>  
  
 <span data-ttu-id="09274-106">Le composant de pipeline Désassembleur BizTalk Framework génère un accusé de réception pour le message généré si l'expéditeur en a fait la demande avec l'en-tête deliverReceiptRequest dans l’enveloppe BizTalk Framework.</span><span class="sxs-lookup"><span data-stu-id="09274-106">The BizTalk Framework Disassembler pipeline component generates an acknowledgment for the generated message if the sender requested one using the deliverReceiptRequest header within the BizTalk Framework envelope.</span></span> <span data-ttu-id="09274-107">Cette opération est contrôlée par la propriété de génération d’accusé de réception dans le composant de pipeline Assembleur BizTalk Framework.</span><span class="sxs-lookup"><span data-stu-id="09274-107">This is controlled by the generate delivery receipt property in the BizTalk Framework Assembler pipeline component.</span></span> <span data-ttu-id="09274-108">Pour plus d’informations sur BizTalk Framework, consultez [composant de Pipeline assembleur BizTalk Framework](../core/biztalk-framework-assembler-pipeline-component.md).</span><span class="sxs-lookup"><span data-stu-id="09274-108">For more information about the BizTalk Framework, see [BizTalk Framework Assembler Pipeline Component](../core/biztalk-framework-assembler-pipeline-component.md).</span></span>  
  
 <span data-ttu-id="09274-109">Pour plus d’informations sur la configuration du composant de pipeline Désassembleur BizTalk Framework et la création de l’orchestration, consultez [comment configurer le composant de Pipeline Désassembleur BizTalk Framework](../core/how-to-configure-the-biztalk-framework-disassembler-pipeline-component.md).</span><span class="sxs-lookup"><span data-stu-id="09274-109">For information about configuring the BizTalk Framework Disassembler pipeline component and creating the orchestration, see [How to Configure the BizTalk Framework Disassembler Pipeline Component](../core/how-to-configure-the-biztalk-framework-disassembler-pipeline-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09274-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09274-110">See Also</span></span>  
 <span data-ttu-id="09274-111">[Comment configurer le composant de Pipeline Désassembleur BizTalk Framework](../core/how-to-configure-the-biztalk-framework-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="09274-111">[How to Configure the BizTalk Framework Disassembler Pipeline Component](../core/how-to-configure-the-biztalk-framework-disassembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="09274-112">Composants de pipeline</span><span class="sxs-lookup"><span data-stu-id="09274-112">Pipeline Components</span></span>](../core/pipeline-components.md)