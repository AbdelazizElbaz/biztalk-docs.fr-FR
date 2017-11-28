---
title: "Détermination du schéma dans l’assembleur 2.X HL7 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, assembler
- MSH5
- assembler, schemas
ms.assetid: 464c006e-4fae-4e2a-99ea-157301c0179e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50a430750846ae2567f063f9aa77221bad9c97e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schema-determination-in-the-hl7-2x-assembler"></a><span data-ttu-id="85dfc-102">Détermination du schéma dans l’assembleur 2.X HL7</span><span class="sxs-lookup"><span data-stu-id="85dfc-102">Schema Determination in the HL7 2.X Assembler</span></span>
<span data-ttu-id="85dfc-103">Lorsqu’un message transite du sérialiseur, le sérialiseur dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) utilise MSH5 (tiers de destination) du message pour déterminer les opérations à effectuer sur le message.</span><span class="sxs-lookup"><span data-stu-id="85dfc-103">When a message flows to the serializer, the serializer in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) uses MSH5 (destination party) of the message to determine the operations to be performed on the message.</span></span> <span data-ttu-id="85dfc-104">Ces opérations sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="85dfc-104">Such operations include:</span></span>  
  
-   <span data-ttu-id="85dfc-105">Si vous souhaitez effectuer la validation XML pour les segments de corps</span><span class="sxs-lookup"><span data-stu-id="85dfc-105">Whether to perform XML validation for body segments</span></span>  
  
-   <span data-ttu-id="85dfc-106">Si vous souhaitez valider les types de données personnalisés pour les segments de corps</span><span class="sxs-lookup"><span data-stu-id="85dfc-106">Whether to validate custom data types for body segments</span></span>  
  
-   <span data-ttu-id="85dfc-107">S’il faut autoriser les délimiteurs dans le corps de fin</span><span class="sxs-lookup"><span data-stu-id="85dfc-107">Whether to allow trailing delimiters in the body</span></span>  
  
-   <span data-ttu-id="85dfc-108">L’espace de noms cible schéma utilise le sérialiseur</span><span class="sxs-lookup"><span data-stu-id="85dfc-108">Which schema target namespace the serializer will use</span></span>  
  
-   <span data-ttu-id="85dfc-109">Indique si le sérialiseur doit mapper l’en-tête</span><span class="sxs-lookup"><span data-stu-id="85dfc-109">Whether the serializer needs to map the header</span></span>  
  
 <span data-ttu-id="85dfc-110">Pour déterminer le schéma, le sérialiseur effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="85dfc-110">To determine the schema, the serializer does the following:</span></span>  
  
-   <span data-ttu-id="85dfc-111">Définit l’espace de noms cible (**TargetNS**) à la même valeur que l’espace de noms configuré pour le tiers de destination</span><span class="sxs-lookup"><span data-stu-id="85dfc-111">Sets the target namespace (**TargetNS**) to the same value as the namespace configured for the destination party</span></span>  
  
-   <span data-ttu-id="85dfc-112">Extrait **Rootnode** à partir de la **BTS. MessageType** propriété promue</span><span class="sxs-lookup"><span data-stu-id="85dfc-112">Extracts **Rootnode** from the **BTS.MessageType** promoted property</span></span>  
  
 <span data-ttu-id="85dfc-113">Le **doctype** devient **TargetNS + « # » + Rootnode**.</span><span class="sxs-lookup"><span data-stu-id="85dfc-113">The **doctype** becomes **TargetNS + "#" + Rootnode**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85dfc-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85dfc-114">See Also</span></span>  
 <span data-ttu-id="85dfc-115">[Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="85dfc-115">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="85dfc-116">Traitement des fichiers plats BTAHL72X</span><span class="sxs-lookup"><span data-stu-id="85dfc-116">BTAHL72X Flat File Processing</span></span>](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md)