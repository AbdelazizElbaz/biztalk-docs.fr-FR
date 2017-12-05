---
title: "Modification des champs à être régénérée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rekeyed fields
- Message Repair and New Submission, modifying fields
- Message Repair and New Submission, rekeyed fields
ms.assetid: aaf353f7-0e43-403e-b72a-88e5dd07f4ac
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04693bf4c4d441487a3ce38f886bc680b1db368b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="changing-fields-to-be-rekeyed"></a><span data-ttu-id="89c57-102">Modification des champs à être régénérée</span><span class="sxs-lookup"><span data-stu-id="89c57-102">Changing Fields to Be Rekeyed</span></span>
<span data-ttu-id="89c57-103">Dans l’étape de vérification d’un flux de travail de réparation message, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] supprime les données à partir d’un nombre de champs afin que le vérificateur d’entrer à nouveau ou recomposition, ces données.</span><span class="sxs-lookup"><span data-stu-id="89c57-103">In the verification step of a message repair workflow, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] removes the data from a number of fields so that the verifier must re-enter, or rekey, that data.</span></span> <span data-ttu-id="89c57-104">Vous pouvez personnaliser les champs dans le RekeyVerify [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire doit être régénérée.</span><span class="sxs-lookup"><span data-stu-id="89c57-104">You can customize which fields in the RekeyVerify [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form need to be rekeyed.</span></span> <span data-ttu-id="89c57-105">Faire dans le fichier MrsrXpathConfig.xml, qui se trouve dans le \< *lecteur*\>: \Program Files\Microsoft BizTalk Accelerator pour le dossier SWIFT\MRSR.</span><span class="sxs-lookup"><span data-stu-id="89c57-105">You do so in the MrsrXpathConfig.xml file, which is located in the \<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\MRSR folder.</span></span>  
  
 <span data-ttu-id="89c57-106">Le fichier MrsrXpathConfig.xml contient une série de nœuds pour le type de message traité.</span><span class="sxs-lookup"><span data-stu-id="89c57-106">The MrsrXpathConfig.xml file contains a series of nodes for the message type processed.</span></span> <span data-ttu-id="89c57-107">Chaque nœud de type de message contient une série de nœuds de champ, un pour chaque champ.</span><span class="sxs-lookup"><span data-stu-id="89c57-107">Each message-type node contains a series of field nodes, one for each field.</span></span> <span data-ttu-id="89c57-108">Vous pouvez modifier les champs à être régénérée en ouvrant MrsrXpathConfig.xml dans un éditeur de texte, tel que le bloc-notes et en ajoutant ou en supprimant un \<chemin d’accès\> nœud pour le champ.</span><span class="sxs-lookup"><span data-stu-id="89c57-108">You can change the fields to be rekeyed by opening MrsrXpathConfig.xml in a text editor, such as Notepad, and adding or removing a \<path\> node for the field.</span></span>  
  
 <span data-ttu-id="89c57-109">Le \<chemin d’accès\> nœud contient les chemins d’accès pour le type de message et le champ.</span><span class="sxs-lookup"><span data-stu-id="89c57-109">The \<path\> node contains paths for the message type and the field.</span></span> <span data-ttu-id="89c57-110">Par exemple, l’entrée pour le chemin d’accès de Destination dans le bloc d’en-tête Application d’entrée d’un message MT103 est le suivant :</span><span class="sxs-lookup"><span data-stu-id="89c57-110">For example, the entry for the Destination Path in the Input Application Header Block of an MT103 message is the following:</span></span>  
  
```  
<path>/*[local-name()='SWIFT_CATEGORY1_MT103_Interchange' and namespace-uri()'http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/Category1/MT103']/*[local-name()='SWIFTHeader' and namespace-uri=']'']/*[local-name()='ApplicationHeaderBlock_Input' and namespace-uri90='']/*[local-name()='DestinationAddress' and namespace-uri()='']</path>  
```  
  
 <span data-ttu-id="89c57-111">Il est plus facile d’ajouter un nouveau champ à être régénérée en copiant et en collant ensuite d’une entrée existante, puis en remplaçant les chemins d’accès appropriés.</span><span class="sxs-lookup"><span data-stu-id="89c57-111">It is easiest to add a new field to be rekeyed by copying and then pasting an existing entry, and then changing the relevant paths.</span></span> <span data-ttu-id="89c57-112">Par exemple, pour forcer la régénération du champ de Date dans la section de 32 a valeur Date Interbank réglée montant en devise d’un message MT103, effectuez les remplacements de trois suivants pour le code précédent.</span><span class="sxs-lookup"><span data-stu-id="89c57-112">For example, to force rekey of the Date field in the Value Date Currency Interbank Settled Amount 32A section of an MT103 message, make the following three replacements to the preceding code.</span></span> <span data-ttu-id="89c57-113">Le reste du code reste le même.</span><span class="sxs-lookup"><span data-stu-id="89c57-113">The rest of the code remains the same.</span></span>  
  
|<span data-ttu-id="89c57-114">Remplacez ceci</span><span class="sxs-lookup"><span data-stu-id="89c57-114">Replace this</span></span>|<span data-ttu-id="89c57-115">Avec cette</span><span class="sxs-lookup"><span data-stu-id="89c57-115">With this</span></span>|  
|------------------|---------------|  
|`SWIFTHeader`|`SWIFT_CATEGORY1_MT103`|  
|`ApplicationHeaderBlock_Input`|`ValueDateCurrencyInterbankSettledAmount_32A`|  
|`DestinationAddress`|`Date`|  
  
 <span data-ttu-id="89c57-116">Pour plus d’informations sur la régénération des champs, consultez [un traitement spécial dans le Message Repair et New Submission](../../adapters-and-accelerators/accelerator-swift/special-processing-in-message-repair-and-new-submission.md).</span><span class="sxs-lookup"><span data-stu-id="89c57-116">For more information about rekeying fields, see [Special Processing in Message Repair and New Submission](../../adapters-and-accelerators/accelerator-swift/special-processing-in-message-repair-and-new-submission.md).</span></span>