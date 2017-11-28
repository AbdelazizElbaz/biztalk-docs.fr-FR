---
title: "Suppression des pièces jointes orphelins | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maintaining databases, deleting orphaned attachments
- databases, deleting orphaned attachments
- attachments
ms.assetid: 38280464-9c9d-4890-9fc5-4b8031dd3f88
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c7660182793cc82ac938f0dd25011a7c4ad7d7e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deleting-orphan-attachments"></a><span data-ttu-id="bb129-102">Suppression des pièces jointes orphelins</span><span class="sxs-lookup"><span data-stu-id="bb129-102">Deleting Orphan Attachments</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="bb129-103">[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] stocke des pièces jointes pour les messages reçus.</span><span class="sxs-lookup"><span data-stu-id="bb129-103"> [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] stores attachments for received messages.</span></span> <span data-ttu-id="bb129-104">Dans certaines circonstances, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] enregistre la pièce jointe, mais supprime le message associé à partir de la table MessagesToLOB, ce qui entraîne une pièce jointe orpheline.</span><span class="sxs-lookup"><span data-stu-id="bb129-104">In certain circumstances, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] saves the attachment, but deletes the associated message from the MessagesToLOB table, resulting in an orphan attachment.</span></span> <span data-ttu-id="bb129-105">Cela peut se produire quand vous envoyez un message qui comporte une pièce jointe et qui possède un manifeste qui n’est pas valide, par exemple, un manifeste dans les NumberOfAttachments = 0.</span><span class="sxs-lookup"><span data-stu-id="bb129-105">This can occur when you submit a message that has an attachment and has a manifest that is not valid, for example, a manifest in which NumberOfAttachments = 0.</span></span> <span data-ttu-id="bb129-106">Régulièrement, il pouvez que vous souhaitez supprimer les pièces jointes orphelins pour maintenir les performances du système.</span><span class="sxs-lookup"><span data-stu-id="bb129-106">Periodically, you may want to delete orphan attachments to maintain system performance.</span></span>  
  
## <a name="how-to-delete-orphan-attachments"></a><span data-ttu-id="bb129-107">Comment supprimer les pièces jointes orphelins</span><span class="sxs-lookup"><span data-stu-id="bb129-107">How to Delete Orphan Attachments</span></span>  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="bb129-108">stocke les pièces jointes dans la table de pièces jointes de la base de données BTARNDATA.</span><span class="sxs-lookup"><span data-stu-id="bb129-108"> stores attachments in the Attachments table of the BTARNDATA database.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="bb129-109">stocke les messages associés dans la table MessagesToLOB.</span><span class="sxs-lookup"><span data-stu-id="bb129-109"> stores the associated messages in the MessagesToLOB table.</span></span> <span data-ttu-id="bb129-110">Une pièce jointe orpheline se produit lorsque la pièce jointe a un `outMessageID` propriété qui ne correspond pas à la `MessageID` propriété d’un message dans la table MessagesToLOB.</span><span class="sxs-lookup"><span data-stu-id="bb129-110">An orphan attachment results when the attachment has an `outMessageID` property that does not correspond to the `MessageID` property of a message in the MessagesToLOB table.</span></span>  
  
 <span data-ttu-id="bb129-111">Régulièrement, il pouvez que vous souhaitez supprimer les pièces jointes de la table à l’aide d’une procédure stockée qui supprime uniquement les pièces jointes qui n’ont pas d’un message correspondant dans la table MessagesToLOB.</span><span class="sxs-lookup"><span data-stu-id="bb129-111">Periodically, you may want to delete attachments from the table by using a stored procedure that deletes only those attachments that do not have a corresponding message in the MessagesToLOB table.</span></span> <span data-ttu-id="bb129-112">Un exemple d’instruction SQL pour la procédure stockée est la suivante :</span><span class="sxs-lookup"><span data-stu-id="bb129-112">A sample SQL statement for the stored procedure is:</span></span>  
  
```  
delete from attachments where outMessageID not in (select messageid from messagestolob)  
```  
  
 <span data-ttu-id="bb129-113">En outre, il est recommandé de supprimer les pièces jointes qui sont antérieurs à une certaine période et ne nécessitent pas les investigations plus poussées.</span><span class="sxs-lookup"><span data-stu-id="bb129-113">Additionally, it is recommended that you delete attachments that are older than a certain period, and do not require any more investigation.</span></span> <span data-ttu-id="bb129-114">La table de pièces jointes contient un `TimeCreated` propriété que vous pouvez utiliser pour supprimer les anciennes pièces jointes.</span><span class="sxs-lookup"><span data-stu-id="bb129-114">The Attachments table contains a `TimeCreated` property that you can use to delete old attachments.</span></span> <span data-ttu-id="bb129-115">Ce processus est similaire au processus utilisé pour supprimer les anciens résumés.</span><span class="sxs-lookup"><span data-stu-id="bb129-115">This process is similar to the process used to delete old digests.</span></span> <span data-ttu-id="bb129-116">Pour un exemple d’instruction SQL pour une procédure stockée qui supprime les anciens résumés, consultez [suppression des résumés](../../adapters-and-accelerators/accelerator-rosettanet/deleting-digests.md).</span><span class="sxs-lookup"><span data-stu-id="bb129-116">For a sample SQL statement for a stored procedure that deletes old digests, see [Deleting Digests](../../adapters-and-accelerators/accelerator-rosettanet/deleting-digests.md).</span></span>  
  
 <span data-ttu-id="bb129-117">Il est également recommandé d’indexer les pièces jointes et MessagestoLOB tables sur les colonnes MessageID respectifs.</span><span class="sxs-lookup"><span data-stu-id="bb129-117">It is also recommended that you index the Attachments and MessagestoLOB tables on the respective MessageID columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb129-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb129-118">See Also</span></span>  
 [<span data-ttu-id="bb129-119">Maintenance des bases de données BTARN</span><span class="sxs-lookup"><span data-stu-id="bb129-119">Maintaining BTARN Databases</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/maintaining-btarn-databases.md)