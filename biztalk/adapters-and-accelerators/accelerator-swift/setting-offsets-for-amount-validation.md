---
title: "Définition des Offsets pour la Validation de la quantité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- amounts, validating
- validating, amounts
- amounts, offsets
- offsets
ms.assetid: 39d5510c-52e6-4fd9-9632-582b508f04d7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7cfae474407daa7dd3c0b95db3fed076a581cf1c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="setting-offsets-for-amount-validation"></a><span data-ttu-id="505f0-102">Définition des Offsets pour la Validation de la quantité</span><span class="sxs-lookup"><span data-stu-id="505f0-102">Setting Offsets for Amount Validation</span></span>
<span data-ttu-id="505f0-103">Les règles d’utilisation pour les champs de montant de types de messages MT102, MT103 et MT103PLUS sont validés par les règles de leurs stratégies de validation respectives.</span><span class="sxs-lookup"><span data-stu-id="505f0-103">The usage rules for Amount fields in message types MT102, MT103, and MT103PLUS are validated by rules in their respective validation policies.</span></span> <span data-ttu-id="505f0-104">Les champs de montant peuvent correspondre exactement ou peuvent être validés à l’intérieur d’une plage de quantités.</span><span class="sxs-lookup"><span data-stu-id="505f0-104">The Amount fields can be matched exactly or can be validated to be within a range of amounts.</span></span>  
  
 <span data-ttu-id="505f0-105">Pour activer la validation d’une plage, vous spécifiez un pourcentage de décalage dans l’appel de méthode dans la stratégie de validation appropriées.</span><span class="sxs-lookup"><span data-stu-id="505f0-105">To enable validation within a range, you specify an offset percentage in the method call in the relevant validation policy.</span></span> <span data-ttu-id="505f0-106">Par exemple, si le montant que vous définissez pour le champ est 100, et le décalage est 10 pour cent, un montant valide serait une valeur quelconque de 90 à 110, inclus.</span><span class="sxs-lookup"><span data-stu-id="505f0-106">For example, if the amount that you set for the field is 100, and the offset percentage is 10 percent, a valid amount would be any value from 90 to 110, inclusive.</span></span> [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="505f0-107">fournit cette prise en charge pour les types de messages MT102, MT102PLUS et MT103.</span><span class="sxs-lookup"><span data-stu-id="505f0-107"> provides this support for the MT102, MT102PLUS, and MT103 message types.</span></span>  
  
 <span data-ttu-id="505f0-108">Le pourcentage de décalage est spécifié, que ce soit le **IsValidSettlementAmount** ou **IsValidInterbankSettledAmount** méthode dans la stratégie de validation.</span><span class="sxs-lookup"><span data-stu-id="505f0-108">The offset percentage is specified in either the **IsValidSettlementAmount** or **IsValidInterbankSettledAmount** method in the validation policy.</span></span> <span data-ttu-id="505f0-109">Le **IsValidSettlementAmount** méthode implémente la règle d’utilisation pour les champs de quantité de messages MT102 et MT102PLUS.</span><span class="sxs-lookup"><span data-stu-id="505f0-109">The **IsValidSettlementAmount** method implements the usage rule for Amount fields of MT102 and MT102PLUS messages.</span></span> <span data-ttu-id="505f0-110">Le **IsValidInterbankSettledAmount** méthode implémente la règle d’utilisation pour les champs de quantité de messages de MT103.</span><span class="sxs-lookup"><span data-stu-id="505f0-110">The **IsValidInterbankSettledAmount** method implements the usage rule for Amount fields of MT103 messages.</span></span> <span data-ttu-id="505f0-111">Vous spécifiez le pourcentage de décalage de l’argument OffsetPercent, qui est le dixième argument d’un de ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="505f0-111">You specify the offset percentage in the OffsetPercent argument, which is the tenth argument of either of those methods.</span></span>  
  
 <span data-ttu-id="505f0-112">Si la valeur, le décalage de pourcentage s’applique aux champs suivants :</span><span class="sxs-lookup"><span data-stu-id="505f0-112">When set, the percentage offset applies to the following fields:</span></span>  
  
|<span data-ttu-id="505f0-113">type de message</span><span class="sxs-lookup"><span data-stu-id="505f0-113">Message type</span></span>|<span data-ttu-id="505f0-114">Validé avec décalages de champs</span><span class="sxs-lookup"><span data-stu-id="505f0-114">Fields validated with offsets</span></span>|  
|------------------|-----------------------------------|  
|<span data-ttu-id="505f0-115">MT102 ou MT102PLUS</span><span class="sxs-lookup"><span data-stu-id="505f0-115">MT102 or MT102PLUS</span></span>|<span data-ttu-id="505f0-116">32</span><span class="sxs-lookup"><span data-stu-id="505f0-116">32</span></span><br /><br /> <span data-ttu-id="505f0-117">33B</span><span class="sxs-lookup"><span data-stu-id="505f0-117">33B</span></span>|  
|<span data-ttu-id="505f0-118">MT103</span><span class="sxs-lookup"><span data-stu-id="505f0-118">MT103</span></span>|<span data-ttu-id="505f0-119">19, séquence C</span><span class="sxs-lookup"><span data-stu-id="505f0-119">19, Sequence C</span></span><br /><br /> <span data-ttu-id="505f0-120">31 a, séquence C</span><span class="sxs-lookup"><span data-stu-id="505f0-120">31A, Sequence C</span></span><br /><br /> <span data-ttu-id="505f0-121">72G</span><span class="sxs-lookup"><span data-stu-id="505f0-121">72G</span></span>|  
  
### <a name="to-set-an-offset-percentage"></a><span data-ttu-id="505f0-122">Pour définir un pourcentage de décalage</span><span class="sxs-lookup"><span data-stu-id="505f0-122">To set an offset percentage</span></span>  
  
1.  <span data-ttu-id="505f0-123">Ouvrez un éditeur de texte, tel que le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="505f0-123">Open a text editor, such as Notepad.</span></span>  
  
2.  <span data-ttu-id="505f0-124">Dans l’éditeur, accédez à l’emplacement de la stratégie de validation de message dans lequel vous souhaitez définir un pourcentage de décalage.</span><span class="sxs-lookup"><span data-stu-id="505f0-124">In the editor, browse to the location of the message validation policy in which you want to set an offset percentage.</span></span> <span data-ttu-id="505f0-125">Par exemple, vous pouvez trouver dans la stratégie de validation de message pour le type de message MT103, MT103_Validation_Policy.xml,  *\<lecteur\>*: \Program Files\ Microsoft BizTalk Accelerator pour SWIFT \< version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category 1\MT103.</span><span class="sxs-lookup"><span data-stu-id="505f0-125">For example, you can find the message validation policy for the MT103 message type, MT103_Validation_Policy.xml, in *\<drive\>*:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category 1\MT103.</span></span> <span data-ttu-id="505f0-126">Ouvrez la stratégie de validation.</span><span class="sxs-lookup"><span data-stu-id="505f0-126">Open the validation policy.</span></span>  
  
3.  <span data-ttu-id="505f0-127">Dans la stratégie, recherchez sur IsValidSettlementAmount messages MT102 et MT102PLUS ou IsValidInterbankSettledAmount pour les messages MT103.</span><span class="sxs-lookup"><span data-stu-id="505f0-127">In the policy, search on IsValidSettlementAmount for MT102 and MT102PLUS messages or IsValidInterbankSettledAmount for MT103 messages.</span></span>  
  
4.  <span data-ttu-id="505f0-128">Compte à la dixième argument.</span><span class="sxs-lookup"><span data-stu-id="505f0-128">Count down to the tenth argument.</span></span> <span data-ttu-id="505f0-129">Entrez le pourcentage de l’offset de l’argument.</span><span class="sxs-lookup"><span data-stu-id="505f0-129">Enter the percentage of the offset in the argument.</span></span>  
  
5.  <span data-ttu-id="505f0-130">Enregistrez le fichier, puis fermez l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="505f0-130">Save the file, and then close the editor.</span></span>