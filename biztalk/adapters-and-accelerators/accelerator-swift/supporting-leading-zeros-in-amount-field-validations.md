---
title: "Prise en charge des zéros non significatifs dans les Validations de champ Quantité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- amounts, amount fields
- amounts, leading zeros
- validating, amount fields
ms.assetid: 7c202422-019f-43da-9c2a-4b9fdf0b2859
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1de45b5acbc780fad0847ab207d0d5c72ca2a652
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="supporting-leading-zeros-in-amount-field-validations"></a><span data-ttu-id="3510b-102">Des zéros non significatifs dans les Validations de champ de montant de la prise en charge</span><span class="sxs-lookup"><span data-stu-id="3510b-102">Supporting Leading Zeros in Amount Field Validations</span></span>
<span data-ttu-id="3510b-103">Les stratégies de validation de certains types de message effectue les validations sur les champs de montant.</span><span class="sxs-lookup"><span data-stu-id="3510b-103">The validation policies of some message types perform validations on Amount fields.</span></span> <span data-ttu-id="3510b-104">Pour activer les zéros non significatifs dans les champs de montant, vous devez modifier la stratégie de validation pour le type de message.</span><span class="sxs-lookup"><span data-stu-id="3510b-104">To enable leading zeros in Amount fields, you must edit the validation policy for the message type.</span></span> <span data-ttu-id="3510b-105">Vous pouvez créer une nouvelle version de la stratégie de validation par défaut et modifier l’argument dans l’éditeur des règles d’entreprise, ou vous pouvez modifier la stratégie par défaut manuellement dans un éditeur de texte avant la stratégie est déployée.</span><span class="sxs-lookup"><span data-stu-id="3510b-105">You can create a new version of the default validation policy, and edit the argument in the Business Rule Composer, or you can edit the default policy manually in a text editor before the policy is deployed.</span></span>  
  
 <span data-ttu-id="3510b-106">Le tableau suivant répertorie les méthodes qui activent ou désactivent les zéros non significatifs.</span><span class="sxs-lookup"><span data-stu-id="3510b-106">The following table lists the methods that enable or disable leading zeros.</span></span> <span data-ttu-id="3510b-107">Le tableau indique également le nombre ordinal de l’argument que vous devez définir dans la méthode.</span><span class="sxs-lookup"><span data-stu-id="3510b-107">The table also indicates the ordinal number of the argument that you need to set in the method.</span></span> <span data-ttu-id="3510b-108">Définissez la propriété à True pour activer des zéros non significatifs, ou False pour les désactiver.</span><span class="sxs-lookup"><span data-stu-id="3510b-108">Set it to True to enable leading zeros, or to False to disable them.</span></span>  
  
|<span data-ttu-id="3510b-109">Méthode</span><span class="sxs-lookup"><span data-stu-id="3510b-109">Method</span></span>|<span data-ttu-id="3510b-110">Nombre d’arguments</span><span class="sxs-lookup"><span data-stu-id="3510b-110">Argument number</span></span>|  
|------------|---------------------|  
|<span data-ttu-id="3510b-111">**CheckValidAmount**</span><span class="sxs-lookup"><span data-stu-id="3510b-111">**CheckValidAmount**</span></span>|<span data-ttu-id="3510b-112">6</span><span class="sxs-lookup"><span data-stu-id="3510b-112">6</span></span>|  
|<span data-ttu-id="3510b-113">**CheckCurrencyAmount**</span><span class="sxs-lookup"><span data-stu-id="3510b-113">**CheckCurrencyAmount**</span></span>|<span data-ttu-id="3510b-114">4</span><span class="sxs-lookup"><span data-stu-id="3510b-114">4</span></span>|  
|<span data-ttu-id="3510b-115">**CheckValidSignCurrencyAmount**</span><span class="sxs-lookup"><span data-stu-id="3510b-115">**CheckValidSignCurrencyAmount**</span></span>|<span data-ttu-id="3510b-116">3</span><span class="sxs-lookup"><span data-stu-id="3510b-116">3</span></span>|  
|<span data-ttu-id="3510b-117">**CheckValidSignDateCurrencyAmount**</span><span class="sxs-lookup"><span data-stu-id="3510b-117">**CheckValidSignDateCurrencyAmount**</span></span>|<span data-ttu-id="3510b-118">4</span><span class="sxs-lookup"><span data-stu-id="3510b-118">4</span></span>|  
|<span data-ttu-id="3510b-119">**IsValidTransactionDetailsCurrencyAmount**</span><span class="sxs-lookup"><span data-stu-id="3510b-119">**IsValidTransactionDetailsCurrencyAmount**</span></span>|<span data-ttu-id="3510b-120">4</span><span class="sxs-lookup"><span data-stu-id="3510b-120">4</span></span>|  
  
 <span data-ttu-id="3510b-121">Chaque méthode dans le tableau précédent est contenue dans une ou plusieurs stratégies de validation de message.</span><span class="sxs-lookup"><span data-stu-id="3510b-121">Each method in the preceding table is contained in one or more message validation policies.</span></span> <span data-ttu-id="3510b-122">Pour définir l’argument dans une stratégie, vous devez rechercher sur le nom de la méthode pour vérifier si la stratégie contient.</span><span class="sxs-lookup"><span data-stu-id="3510b-122">To set the argument in a policy, you must search on the method name to verify whether the policy contains it.</span></span> <span data-ttu-id="3510b-123">Une méthode peut apparaître plusieurs fois dans la stratégie d’un message.</span><span class="sxs-lookup"><span data-stu-id="3510b-123">A method may appear multiple times in a message's policy.</span></span>  
  
### <a name="to-enable-or-disable-leading-zeros"></a><span data-ttu-id="3510b-124">Pour activer ou désactiver les zéros non significatifs</span><span class="sxs-lookup"><span data-stu-id="3510b-124">To enable or disable leading zeros</span></span>  
  
1.  <span data-ttu-id="3510b-125">Ouvrez un éditeur de texte, tel que le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="3510b-125">Open a text editor, such as Notepad.</span></span>  
  
2.  <span data-ttu-id="3510b-126">Dans l’éditeur, accédez à l’emplacement de la stratégie de validation de message dans lequel vous souhaitez activer ou désactiver les zéros non significatifs.</span><span class="sxs-lookup"><span data-stu-id="3510b-126">In the editor, browse to the location of the message validation policy in which you want to enable or disable leading zeros.</span></span> <span data-ttu-id="3510b-127">Par exemple, vous pouvez trouver dans la stratégie de validation de message pour le type de message MT103, MT103_Validation_Policy.xml,  *\<lecteur >*: / programme ou de fichiers Microsoft BizTalk Accelerator pour SWIFT/SWIFT Messages/catégorie 1 / MT103.</span><span class="sxs-lookup"><span data-stu-id="3510b-127">For example, you can find the message validation policy for the MT103 message type, MT103_Validation_Policy.xml, in *\<drive>*:/Program Files/Microsoft BizTalk Accelerator for SWIFT/SWIFT Messages/Category 1/MT103.</span></span> <span data-ttu-id="3510b-128">Ouvrez la stratégie de validation.</span><span class="sxs-lookup"><span data-stu-id="3510b-128">Open the validation policy.</span></span>  
  
3.  <span data-ttu-id="3510b-129">Dans la stratégie, effectuez une recherche sur le **CheckValidAmount** (méthode).</span><span class="sxs-lookup"><span data-stu-id="3510b-129">In the policy, search on the **CheckValidAmount** method.</span></span>  
  
4.  <span data-ttu-id="3510b-130">Si vous trouvez la méthode, compte à l’argument approprié.</span><span class="sxs-lookup"><span data-stu-id="3510b-130">If you find the method, count down to the appropriate argument.</span></span> <span data-ttu-id="3510b-131">Par exemple, pour le **CheckValidAmount** décompte sixième argument de la méthode.</span><span class="sxs-lookup"><span data-stu-id="3510b-131">For example, for the **CheckValidAmount** method, count down to the sixth argument.</span></span> <span data-ttu-id="3510b-132">L’argument de la valeur **True** pour activer les zéros de début ou de False pour les désactiver.</span><span class="sxs-lookup"><span data-stu-id="3510b-132">Set the argument to **True** to enable leading zeros or False to disable them.</span></span>  
  
5.  <span data-ttu-id="3510b-133">Répétez les étapes 3 et 4 pour chaque méthode dans le tableau précédent.</span><span class="sxs-lookup"><span data-stu-id="3510b-133">Repeat steps 3 and 4 for each method in the preceding table.</span></span>  
  
6.  <span data-ttu-id="3510b-134">Enregistrez le fichier, puis fermez l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="3510b-134">Save the file, and then close the editor.</span></span>