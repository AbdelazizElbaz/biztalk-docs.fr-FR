---
title: "Comment les caractères de nom de nœud codés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6462856b-7a52-40c9-9aff-c0579130eec9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d2c9410e56b2b50a32ec73ce5f49ae59909f59a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-node-name-characters-get-encoded"></a><span data-ttu-id="7506d-102">Codage des caractères des noms de nœud</span><span class="sxs-lookup"><span data-stu-id="7506d-102">How Node Name Characters Get Encoded</span></span>
<span data-ttu-id="7506d-103">Si vous utilisez un caractère qui n’est pas autorisé dans un nom de nœud, l’Éditeur BizTalk vous invite à entrer vous demande si vous voulez poursuivre l’ou les caractères encodés non autorisée (**OK** ou **Annuler**).</span><span class="sxs-lookup"><span data-stu-id="7506d-103">If you use a character that is not allowed in a node name, BizTalk Editor prompts you, asking if you want to proceed with the disallowed character or characters encoded (**OK** or **Cancel**).</span></span> <span data-ttu-id="7506d-104">Si vous en décidez ainsi, chaque caractère non autorisé est codé comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="7506d-104">If you proceed, each disallowed character is encoded as follows:</span></span>  
  
-   <span data-ttu-id="7506d-105">Caractères non autorisés sont codés en tant que « _xDDDD\_» où « DDDD » est la représentation Unicode hexadécimale de 4 chiffres du caractère.</span><span class="sxs-lookup"><span data-stu-id="7506d-105">Disallowed characters are encoded as "_xDDDD\_" where "DDDD" is the 4-digit hexadecimal Unicode representation of the character.</span></span> <span data-ttu-id="7506d-106">Par exemple, le caractère espace (0 x 0020) est encodé comme « _x0020\_».</span><span class="sxs-lookup"><span data-stu-id="7506d-106">For example, the space character (0x0020) is encoded as "_x0020\_".</span></span>  
  
-   <span data-ttu-id="7506d-107">Si au moins deux caractères adjacents non autorisés sont codés, un seul caractère de soulignement est placé entre eux.</span><span class="sxs-lookup"><span data-stu-id="7506d-107">If two or more adjacent disallowed characters are encoded, only a single underscore character is used between them.</span></span> <span data-ttu-id="7506d-108">Par exemple, trois espaces sont encodés en tant que « _x0020_x0020_x0020\_» plutôt que « _x0020\__x0020\__x0020\_».</span><span class="sxs-lookup"><span data-stu-id="7506d-108">For example, three spaces are encoded as "_x0020_x0020_x0020\_" rather than "_x0020\__x0020\__x0020\_".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7506d-109">Vous pouvez désactiver les invites pour le codage d’un nom de nœud en définissant le **afficher Encoder boîte de dialogue Avertissement** propriété **False** dans le dossier de l’Éditeur BizTalk de la **Options** boîte de dialogue disponible sur le **outils** menu, ou en sélectionnant le **ne plus afficher cette boîte de dialogue** case à cocher dans la boîte de dialogue de codage le nom du nœud.</span><span class="sxs-lookup"><span data-stu-id="7506d-109">You can disable prompting for node name encoding by setting the **Show Encode Warning Dialog** property to **False** in the BizTalk Editor folder of the **Options** dialog box, available on the **Tools** menu, or by selecting the **Do not show this dialog in the future** check box in the node name encoding dialog box.</span></span> <span data-ttu-id="7506d-110">Pour plus d’informations sur les options de cette boîte de dialogue, consultez [la gestion de l’arborescence du schéma](../core/how-to-manage-the-schema-tree-view.md).</span><span class="sxs-lookup"><span data-stu-id="7506d-110">For more information about the options in this dialog box, see [Managing the Schema Tree View](../core/how-to-manage-the-schema-tree-view.md).</span></span>  
  
 <span data-ttu-id="7506d-111">Dans l'Éditeur BizTalk, l'arborescence des schémas affiche les noms de nœud en utilisant les caractères que vous tapez.</span><span class="sxs-lookup"><span data-stu-id="7506d-111">The schema tree view in BizTalk Editor displays node names by using the characters you type.</span></span> <span data-ttu-id="7506d-112">Le Mappeur BizTalk affiche également les caractères tapés plutôt que la version codée.</span><span class="sxs-lookup"><span data-stu-id="7506d-112">BizTalk Mapper also displays the characters you have typed rather than the encoded version.</span></span> <span data-ttu-id="7506d-113">Dans la vue XSD de l'Éditeur BizTalk et dans le fichier XSD lui-même, le nom de nœud codé est utilisé.</span><span class="sxs-lookup"><span data-stu-id="7506d-113">In the XSD view of BizTalk Editor, and in the XSD file itself, the encoded node name is used.</span></span> <span data-ttu-id="7506d-114">Par exemple, si vous donnez à un nœud le nom Bon de commande, il s'affichera tel quel dans les arborescences de schéma de l'Éditeur BizTalk et du Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7506d-114">For example, if you name a node Purchase Order, it will be displayed as Purchase Order in the schema trees in both BizTalk Editor and BizTalk Mapper.</span></span> <span data-ttu-id="7506d-115">Dans la vue XSD de l'Éditeur BizTalk, le nœud d'élément correspondant prendra la forme suivante lorsqu'il sera inséré pour la première fois :</span><span class="sxs-lookup"><span data-stu-id="7506d-115">In the XSD view of BizTalk Editor, the corresponding element node, when first inserted, will be as follows.</span></span>  
  
```  
<element name="Purchase_x0020_Order" type="xs:string />  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="7506d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7506d-116">See Also</span></span>  
 <span data-ttu-id="7506d-117">[Propriété de nom de nœud](../core/node-name-property.md) </span><span class="sxs-lookup"><span data-stu-id="7506d-117">[Node Name Property](../core/node-name-property.md) </span></span>  
 [<span data-ttu-id="7506d-118">Les caractères de nom de nœud codés</span><span class="sxs-lookup"><span data-stu-id="7506d-118">Which Node Name Characters Get Encoded</span></span>](../core/which-node-name-characters-get-encoded.md)