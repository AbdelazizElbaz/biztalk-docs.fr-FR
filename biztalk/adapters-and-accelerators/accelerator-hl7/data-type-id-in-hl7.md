---
title: "ID de Type de données dans HL7 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types, data type ID
- data types, messages
- messages, data types
ms.assetid: d1412886-ff0b-4333-b01e-1c3ae45240e2
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c5778e772d21cb5f9c6759c127c92ebe74b6f5c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-type-id-in-hl7"></a><span data-ttu-id="f24fb-102">ID de Type de données dans HL7</span><span class="sxs-lookup"><span data-stu-id="f24fb-102">Data Type ID in HL7</span></span>
<span data-ttu-id="f24fb-103">Dans le cas de HL7 V2.1, l’ID de type de données est un espace réservé pour les types de données non défini.</span><span class="sxs-lookup"><span data-stu-id="f24fb-103">In the case of HL7 V2.1, the data type ID is a placeholder for undefined data types.</span></span> <span data-ttu-id="f24fb-104">Voici quelques exemples de son utilisation :</span><span class="sxs-lookup"><span data-stu-id="f24fb-104">The following are examples of its usage:</span></span>  
  
-   <span data-ttu-id="f24fb-105">Le type de données sous la forme d’un champ ST est SI (ID de séquence).</span><span class="sxs-lookup"><span data-stu-id="f24fb-105">The data type in the form of an ST field is SI (Sequence ID).</span></span>  
  
-   <span data-ttu-id="f24fb-106">Le type de données sous la forme d’un champ NM est champs composites.</span><span class="sxs-lookup"><span data-stu-id="f24fb-106">The data type in the form of an NM field is composite fields.</span></span>  
  
 <span data-ttu-id="f24fb-107">Voici quelques exemples de spécifiquement les types de données composites définis :</span><span class="sxs-lookup"><span data-stu-id="f24fb-107">The following are examples of specifically defined composite data types:</span></span>  
  
-   <span data-ttu-id="f24fb-108">CK : ID Composite avec chiffre de vérification.</span><span class="sxs-lookup"><span data-stu-id="f24fb-108">CK: Composite ID with check digit.</span></span> <span data-ttu-id="f24fb-109">Exemple :</span><span class="sxs-lookup"><span data-stu-id="f24fb-109">For example:</span></span>  
  
    ```  
    |128952^6^M11|  
    ```  
  
-   <span data-ttu-id="f24fb-110">NC : Composite ID et nom.</span><span class="sxs-lookup"><span data-stu-id="f24fb-110">CN: Composite ID number and name.</span></span> <span data-ttu-id="f24fb-111">Exemple :</span><span class="sxs-lookup"><span data-stu-id="f24fb-111">For example:</span></span>  
  
    ```  
    |12372^RIGGINS^JOHN^""^MD|  
    |12372|  
    |^RIGGINS^JOHN^""^MD|  
    ```  
  
-   <span data-ttu-id="f24fb-112">CQ : Quantité Composite avec des unités.</span><span class="sxs-lookup"><span data-stu-id="f24fb-112">CQ: Composite quantity with units.</span></span> <span data-ttu-id="f24fb-113">Exemple :</span><span class="sxs-lookup"><span data-stu-id="f24fb-113">For example:</span></span>  
  
    ```  
    |123.7^ML|  
    ```  
  
-   <span data-ttu-id="f24fb-114">CE : Codé de l’élément.</span><span class="sxs-lookup"><span data-stu-id="f24fb-114">CE: Coded element.</span></span> <span data-ttu-id="f24fb-115">Exemple :</span><span class="sxs-lookup"><span data-stu-id="f24fb-115">For example:</span></span>  
  
    ```  
    |54.21^Laparoscopy^I9C^42112^^AS4|  
    ```  
  
 <span data-ttu-id="f24fb-116">Ce type de données est localisé et définie sur le site.</span><span class="sxs-lookup"><span data-stu-id="f24fb-116">This data type is localized and site-defined.</span></span> <span data-ttu-id="f24fb-117">En outre, HL7 V2.1 ne fournit pas de la couverture de ce type de données dans la base de données HL7 accès.</span><span class="sxs-lookup"><span data-stu-id="f24fb-117">Additionally, HL7 V2.1 does not provide the coverage for this data type in the HL7 Access database.</span></span> <span data-ttu-id="f24fb-118">Pour la génération de vos schémas, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) suppose que les types de données de version 2.2 du HL7 sont valides et utilise ces informations pour générer les schémas.</span><span class="sxs-lookup"><span data-stu-id="f24fb-118">For generating your schemas, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) assumes that the HL7 V2.2 data types are valid, and uses this information to build the schemas.</span></span> <span data-ttu-id="f24fb-119">Selon l’utilisation dans le schéma, un type de données approprié doit être utilisé, ce qui signifie que que le type de données doit être remplacé par CK, CQ, CE, ST ^ SI et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="f24fb-119">Depending on the usage in the schema, an appropriate data type must be used, meaning that the data type must be replaced with CK, CQ, CE, ST^SI, and so on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f24fb-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f24fb-120">See Also</span></span>  
 <span data-ttu-id="f24fb-121">[Types de données](../../adapters-and-accelerators/accelerator-hl7/data-types.md) </span><span class="sxs-lookup"><span data-stu-id="f24fb-121">[Data Types](../../adapters-and-accelerators/accelerator-hl7/data-types.md) </span></span>  
 <span data-ttu-id="f24fb-122">[Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="f24fb-122">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="f24fb-123">[Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="f24fb-123">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="f24fb-124">L’utilisation des schémas 2.X HL7</span><span class="sxs-lookup"><span data-stu-id="f24fb-124">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)