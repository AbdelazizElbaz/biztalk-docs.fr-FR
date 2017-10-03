---
title: "Étiquette d’un lien à | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5fb81763-8b50-4334-88a8-efad1c5d82d9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c0e47a776fdbc8eccbc1037b3c73b069d810eee0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-label-a-link"></a><span data-ttu-id="4e303-102">Attribution d'une étiquette à un lien</span><span class="sxs-lookup"><span data-stu-id="4e303-102">How to Label a Link</span></span>
<span data-ttu-id="4e303-103">Les étiquettes permettent de spécifier le but d'un fonctoid ou d'une liaison dans un mappage.</span><span class="sxs-lookup"><span data-stu-id="4e303-103">Labels are helpful to document the purpose of a functoid or a link in a map.</span></span> <span data-ttu-id="4e303-104">Vous pouvez utiliser la **étiquette** propriété pour nommer une liaison.</span><span class="sxs-lookup"><span data-stu-id="4e303-104">You can use the **Label** property to name a link.</span></span> <span data-ttu-id="4e303-105">Ceci est utile lorsque votre mappage contient de grandes structures de schéma et que l'identification des entrées et liaisons de sortie vers un fonctoid devient difficile.</span><span class="sxs-lookup"><span data-stu-id="4e303-105">This is useful when your map contains big schema structures and identifying the inputs and output links to a functoid becomes difficult.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e303-106">Pour plus d’informations sur l’étiquette et commentaire fonctoids, consultez [étiquette et commentaires à un fonctoid](../core/how-to-label-and-comment-a-functoid.md).</span><span class="sxs-lookup"><span data-stu-id="4e303-106">For information on how to label and comment functoids, see [How to Label and Comment a Functoid](../core/how-to-label-and-comment-a-functoid.md).</span></span>  
  
 <span data-ttu-id="4e303-107">La figure suivante illustre une étiquette de liaison.</span><span class="sxs-lookup"><span data-stu-id="4e303-107">The following figure shows a link label.</span></span>  
  
 <span data-ttu-id="4e303-108">![Étiquetage d’un lien](../core/media/new-labelling-link.gif "New_Labelling_link")</span><span class="sxs-lookup"><span data-stu-id="4e303-108">![Labelling a link](../core/media/new-labelling-link.gif "New_Labelling_link")</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4e303-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="4e303-109">Prerequisites</span></span>  
 <span data-ttu-id="4e303-110">Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="4e303-110">These instructions require that BizTalk Mapper is running.</span></span>  
  
### <a name="to-add-a-label-to-a-link"></a><span data-ttu-id="4e303-111">Pour ajouter une étiquette à une liaison</span><span class="sxs-lookup"><span data-stu-id="4e303-111">To add a label to a link</span></span>  
  
1.  <span data-ttu-id="4e303-112">Sélectionnez la liaison à laquelle ajouter une étiquette.</span><span class="sxs-lookup"><span data-stu-id="4e303-112">Select the link you want to label.</span></span>  
  
2.  <span data-ttu-id="4e303-113">Dans le **propriétés** fenêtre, indiquez le nouveau nom dans la **étiquette** champ.</span><span class="sxs-lookup"><span data-stu-id="4e303-113">In the **Properties** window, provide the new name in the **Label** field.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="4e303-114">Le nombre maximal de caractères autorisé est de 256.</span><span class="sxs-lookup"><span data-stu-id="4e303-114">The maximum number of characters allowed is 256.</span></span> <span data-ttu-id="4e303-115">Si une chaîne comportant plus de 256 caractères est spécifiée, les 256 premiers caractères sont acceptés et le reste est ignoré.</span><span class="sxs-lookup"><span data-stu-id="4e303-115">If a string with more than 256 characters is specified, the first 256 characters are accepted and the rest are discarded.</span></span>  
  
     <span data-ttu-id="4e303-116">![Lier les propriétés de l’étiquette](../core/media/new-to-label-link.gif "New_To_Label_Link")</span><span class="sxs-lookup"><span data-stu-id="4e303-116">![Link label properties](../core/media/new-to-label-link.gif "New_To_Label_Link")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e303-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e303-117">See Also</span></span>  
 [<span data-ttu-id="4e303-118">À l’aide de liens pour spécifier l’enregistrement et les mappages de champs</span><span class="sxs-lookup"><span data-stu-id="4e303-118">Using Links to Specify Record and Field Mappings</span></span>](../core/using-links-to-specify-record-and-field-mappings.md)