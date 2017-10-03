---
title: "Détermination du schéma dans le désassembleur 2.X HL7 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- header segments [2.X]
- 2.X messages, header segments
- messages, parsing messages
- MSH
- disassembler, parsing messages
- 2.X messages, MSH
ms.assetid: afd45c4c-2feb-44eb-b3bd-49fe114eb893
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6314f9651d09dbb041d2e8851565e904366c9efe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schema-determination-in-the-hl7-2x-disassembler"></a><span data-ttu-id="25e90-102">Détermination du schéma dans le désassembleur 2.X HL7</span><span class="sxs-lookup"><span data-stu-id="25e90-102">Schema Determination in the HL7 2.X Disassembler</span></span>
<span data-ttu-id="25e90-103">HL7 2.X messages contiennent un segment d’en-tête (MSH), suivi d’un nombre de segments de corps et un nombre facultatif de segments de Z.</span><span class="sxs-lookup"><span data-stu-id="25e90-103">HL7 2.X messages contain a header segment (MSH), followed by a number of body segments and an optional number of Z segments.</span></span> <span data-ttu-id="25e90-104">MSH contient des 21 champs.</span><span class="sxs-lookup"><span data-stu-id="25e90-104">MSH contains 21 fields.</span></span>  
  
 <span data-ttu-id="25e90-105">Lorsqu’un message arrive, le moteur 2.X lit l’en-tête pour déterminer le schéma à utiliser pour analyser le corps du message.</span><span class="sxs-lookup"><span data-stu-id="25e90-105">When a message arrives, the 2.X engine reads the header to determine the schema to use to parse the message body.</span></span> <span data-ttu-id="25e90-106">La séquence d’événements suivante se produit :</span><span class="sxs-lookup"><span data-stu-id="25e90-106">The following sequence of events occurs:</span></span>  
  
1.  <span data-ttu-id="25e90-107">Le désassembleur lit la valeur de MSH3 (tiers de la source) pour déterminer les options de validation suivantes :</span><span class="sxs-lookup"><span data-stu-id="25e90-107">The disassembler reads the value of MSH3 (source party) to determine the following validation options:</span></span>  
  
    1.  <span data-ttu-id="25e90-108">Si vous souhaitez effectuer la validation XML pour le corps</span><span class="sxs-lookup"><span data-stu-id="25e90-108">Whether to perform XML validation for the body</span></span>  
  
    2.  <span data-ttu-id="25e90-109">Si vous souhaitez valider les données personnalisées de type champs dans les données de corps</span><span class="sxs-lookup"><span data-stu-id="25e90-109">Whether to validate custom data type fields in the body data</span></span>  
  
    3.  <span data-ttu-id="25e90-110">S’il faut autoriser les délimiteurs dans le corps de fin</span><span class="sxs-lookup"><span data-stu-id="25e90-110">Whether to allow trailing delimiters in the body</span></span>  
  
    4.  <span data-ttu-id="25e90-111">Quel est l’espace de noms cible du schéma de corps (**TargetNS**)</span><span class="sxs-lookup"><span data-stu-id="25e90-111">What the target namespace of the body schema is (**TargetNS**)</span></span>  
  
2.  <span data-ttu-id="25e90-112">Le désassembleur lit ensuite MSH9 et MSH12 pour déterminer le nom du nœud racine du corps.</span><span class="sxs-lookup"><span data-stu-id="25e90-112">The disassembler then reads MSH9 and MSH12 to determine the root node name of the body.</span></span> <span data-ttu-id="25e90-113">L’algorithme est comme suit :</span><span class="sxs-lookup"><span data-stu-id="25e90-113">The algorithm is as follows:</span></span>  
  
    ```  
    Body schema type = TargetNS + "#" + MSH9.1 + MSH9.2 + MSH12.1 (with dots removed) + MSH12.2 (or GLO if the value is blank) + MSH12.3 (or DEF if the value is blank)  
    ```  
  
     [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="25e90-114">BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) permet de toujours les délimiteurs dans un en-tête de message de fin.</span><span class="sxs-lookup"><span data-stu-id="25e90-114"> BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) always allows trailing delimiters in a message header.</span></span> <span data-ttu-id="25e90-115">Le moteur examine l’identificateur de segment est les trois premiers caractères de chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="25e90-115">The engine examines the segment identifier that is the first three characters of each line.</span></span> <span data-ttu-id="25e90-116">Il conserve sur la génération de code XML pour tous les segments contenant le schéma de corps.</span><span class="sxs-lookup"><span data-stu-id="25e90-116">It keeps on generating XML for all segments that the body schema defines.</span></span> <span data-ttu-id="25e90-117">Lorsqu’il rencontre un segment non défini, ce segment est traité comme un segment de Z.</span><span class="sxs-lookup"><span data-stu-id="25e90-117">When it encounters an undefined segment, it treats that segment as a Z segment.</span></span> <span data-ttu-id="25e90-118">À ce stade, tous les segments indéfinis constituent la partie Z du message.</span><span class="sxs-lookup"><span data-stu-id="25e90-118">From that point on, all undefined segments constitute the Z part of the message.</span></span> <span data-ttu-id="25e90-119">La prochaine MSH marque la fin de ce message.</span><span class="sxs-lookup"><span data-stu-id="25e90-119">The next MSH marks the end of this message.</span></span> <span data-ttu-id="25e90-120">Pour les messages du lot, le suivant MSH ou BTS (balise segment code de fin de lot) marque la fin d’un message.</span><span class="sxs-lookup"><span data-stu-id="25e90-120">For batch messages, the next MSH or BTS (the batch trailer segment tag) marks the end of a message.</span></span> <span data-ttu-id="25e90-121">Un segment Z ne peut contenir que des segments qui sont non déclarés dans un schéma.</span><span class="sxs-lookup"><span data-stu-id="25e90-121">A Z segment can only contain segments that are undeclared in a schema.</span></span> <span data-ttu-id="25e90-122">Il s’agit d’une erreur de rencontrer un segment déclaré.</span><span class="sxs-lookup"><span data-stu-id="25e90-122">It is an error to encounter a declared segment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25e90-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25e90-123">See Also</span></span>  
 <span data-ttu-id="25e90-124">[Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="25e90-124">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="25e90-125">Traitement des fichiers plats BTAHL72X</span><span class="sxs-lookup"><span data-stu-id="25e90-125">BTAHL72X Flat File Processing</span></span>](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md)