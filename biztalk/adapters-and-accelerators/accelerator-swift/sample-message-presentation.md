---
title: "Exemple de Message présentation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, SWIFT message block
- SWIFT messages, message block example
ms.assetid: 3136a7da-658d-4100-bbe5-2186ee8bafd1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a14fe8cf93d0c657f2cebbdca3b2f9058f909982
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-message-presentation"></a><span data-ttu-id="a74d6-102">Exemple de présentation de Message</span><span class="sxs-lookup"><span data-stu-id="a74d6-102">Sample Message Presentation</span></span>
<span data-ttu-id="a74d6-103">Le tableau suivant montre un exemple de disposition de bloc d’un message SWIFT.</span><span class="sxs-lookup"><span data-stu-id="a74d6-103">The following table shows an example of the block layout of a SWIFT message.</span></span>  
  
|<span data-ttu-id="a74d6-104">Block</span><span class="sxs-lookup"><span data-stu-id="a74d6-104">Block</span></span>|<span data-ttu-id="a74d6-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="a74d6-105">Example</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="a74d6-106">**Bloc 1** en-tête de base</span><span class="sxs-lookup"><span data-stu-id="a74d6-106">**Block 1** Basic Header</span></span>|<span data-ttu-id="a74d6-107">{1:F01BCITITMMAXXX0012000123}</span><span class="sxs-lookup"><span data-stu-id="a74d6-107">{1:F01BCITITMMAXXX0012000123}</span></span>|  
|<span data-ttu-id="a74d6-108">**Bloc 2** (I) Application en-tête entrée (SWIFT)</span><span class="sxs-lookup"><span data-stu-id="a74d6-108">**Block 2** (I) Application Header Input (to SWIFT)</span></span><br /><br /> <span data-ttu-id="a74d6-109">Ou</span><span class="sxs-lookup"><span data-stu-id="a74d6-109">Or</span></span><br /><br /> <span data-ttu-id="a74d6-110">**Bloc 2** en-tête sortie de l’Application (O) (à partir de SWIFT)</span><span class="sxs-lookup"><span data-stu-id="a74d6-110">**Block 2** (O) Application Header Output (from SWIFT)</span></span>|<span data-ttu-id="a74d6-111">{2:I103VBOEATWWXXXXN} Ou {2:O1030840010605BNPAFRPPAXXX00120078960106051051U3</span><span class="sxs-lookup"><span data-stu-id="a74d6-111">{2:I103VBOEATWWXXXXN} Or {2:O1030840010605BNPAFRPPAXXX00120078960106051051U3</span></span>|  
|<span data-ttu-id="a74d6-112">**Bloc 3** en-tête de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="a74d6-112">**Block 3** User Header</span></span>|<span data-ttu-id="a74d6-113">{3 : {108:BCITITMMA950906}}</span><span class="sxs-lookup"><span data-stu-id="a74d6-113">{3:{108:BCITITMMA950906}}</span></span>|  
|<span data-ttu-id="a74d6-114">**Bloquer les 4** texte</span><span class="sxs-lookup"><span data-stu-id="a74d6-114">**Block 4** Text</span></span>|<span data-ttu-id="a74d6-115">{4 :\<CRLF > : 20:1234567890\<CRLF > : 23B:CRED\<CRLF > : 32A:010605GBP45000,\<CRLF > : 33B:GBP45000,\<CRLF > : 50K:MASTERS IMPORTATION\<CRLF > RUE DES ARBRES 119\<CRLF > CAMBRAI\<CRLF > : 52A:BNPAFRPPCAM\<CRLF > : 53A:POCIITMM680\<CRLF > : 57A:BCITITMM680\<CRLF > : 59 : / P03452032022819 30\< CRLF > IMPORTATION GÉNÉRAL\<CRLF > PESCARA\<CRLF > : 70 : RFB/INVENTAIRE 5591\<CRLF > : 71A:SHA\<CRLF >-}</span><span class="sxs-lookup"><span data-stu-id="a74d6-115">{4:\<CRLF> :20:1234567890\<CRLF> :23B:CRED\<CRLF> :32A:010605GBP45000,\<CRLF> :33B:GBP45000,\<CRLF> :50K:MASTERS IMPORT\<CRLF> RUE DES ARBRES 119\<CRLF> CAMBRAI\<CRLF> :52A:BNPAFRPPCAM\<CRLF> :53A:POCIITMM680\<CRLF> :57A:BCITITMM680\<CRLF> :59:/P03452032022819 30\<CRLF> GRAND IMPORT\<CRLF> PESCARA\<CRLF> :70:/RFB/INV 5591\<CRLF> :71A:SHA\<CRLF> -}</span></span>|  
|<span data-ttu-id="a74d6-116">**Bloquer 5** codes de fin</span><span class="sxs-lookup"><span data-stu-id="a74d6-116">**Block 5** Trailers</span></span>|<span data-ttu-id="a74d6-117">{5 : {MAC : 12345678} {CHK:123456789ABC}}</span><span class="sxs-lookup"><span data-stu-id="a74d6-117">{5:{MAC:12345678}{CHK:123456789ABC}}</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a74d6-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a74d6-118">See Also</span></span>  
 [<span data-ttu-id="a74d6-119">Schémas SWIFT</span><span class="sxs-lookup"><span data-stu-id="a74d6-119">SWIFT Schemas</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-schemas.md)