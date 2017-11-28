---
title: "Personnalisations non déclarées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- undeclared customizations
- Z objects, undeclared customizations
- customizing, Z objects
- customizing, undeclared customizations
ms.assetid: f062dbb7-2c78-47ea-a927-99e1fba4854b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77f688e4cf6a4bbb55243d9f5f6f60e144bad862
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="undeclared-customizations"></a><span data-ttu-id="4fa2c-102">Personnalisations non déclarées</span><span class="sxs-lookup"><span data-stu-id="4fa2c-102">Undeclared Customizations</span></span>
<span data-ttu-id="4fa2c-103">Vous pouvez ajouter des données à un message sans définir le format ou la nature des données.</span><span class="sxs-lookup"><span data-stu-id="4fa2c-103">You can add data to a message without defining the format or nature of the data.</span></span> <span data-ttu-id="4fa2c-104">Pour cela, à l’aide de segments de Z non déclarés.</span><span class="sxs-lookup"><span data-stu-id="4fa2c-104">You do so by using undeclared Z segments.</span></span> <span data-ttu-id="4fa2c-105">Les segments Z non déclarés sont des instances inattendues à la fin d’un message.</span><span class="sxs-lookup"><span data-stu-id="4fa2c-105">Undeclared Z segments are unexpected instances at the end of a message.</span></span> <span data-ttu-id="4fa2c-106">Le programme de validation d’analyseur/XML ne valide pas le segment.</span><span class="sxs-lookup"><span data-stu-id="4fa2c-106">The parser/XML validator does not validate the segment.</span></span> <span data-ttu-id="4fa2c-107">Il n’est pas défini par n’importe quel schéma.</span><span class="sxs-lookup"><span data-stu-id="4fa2c-107">It is not defined by any schema.</span></span> [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="4fa2c-108">BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) traite le segment en tant qu’un objet binaire volumineux (BLOB).</span><span class="sxs-lookup"><span data-stu-id="4fa2c-108"> BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) treats the segment as a binary large object (BLOB).</span></span>  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="4fa2c-109">transmet des données de segment Z non déclarées par le biais comme la troisième partie d’un message en trois parties.</span><span class="sxs-lookup"><span data-stu-id="4fa2c-109"> passes undeclared Z segment data through as the third part of a three-part message.</span></span> <span data-ttu-id="4fa2c-110">Les trois parties sont l’en-tête, le corps et le segment Z non déclaré, également appelée la partie Z.</span><span class="sxs-lookup"><span data-stu-id="4fa2c-110">The three parts are the header, the body, and the undeclared Z segment, also called the Z part.</span></span> <span data-ttu-id="4fa2c-111">Un segment ID à compter de la lettre « Z », par exemple, « ZPD » pour plus d’informations personnalisé données démographiques patient, identifie la partie Z.</span><span class="sxs-lookup"><span data-stu-id="4fa2c-111">A segment ID beginning with the letter "Z", for instance, "ZPD" for custom patient demographics information, identifies the Z part.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fa2c-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fa2c-112">See Also</span></span>  
 <span data-ttu-id="4fa2c-113">[Personnalisations déclarées](../../adapters-and-accelerators/accelerator-hl7/declared-customizations.md) </span><span class="sxs-lookup"><span data-stu-id="4fa2c-113">[Declared Customizations](../../adapters-and-accelerators/accelerator-hl7/declared-customizations.md) </span></span>  
 <span data-ttu-id="4fa2c-114">[Extension des schémas 2.X HL7 avec des objets Z](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span><span class="sxs-lookup"><span data-stu-id="4fa2c-114">[Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span></span>  
 <span data-ttu-id="4fa2c-115">[Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="4fa2c-115">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="4fa2c-116">[Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="4fa2c-116">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="4fa2c-117">L’utilisation des schémas 2.X HL7</span><span class="sxs-lookup"><span data-stu-id="4fa2c-117">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)