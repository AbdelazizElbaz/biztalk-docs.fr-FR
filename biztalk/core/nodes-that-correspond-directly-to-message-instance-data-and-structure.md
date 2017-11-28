---
title: "Les nœuds qui correspondent directement à un Message d’Instance Structure et les données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18cf721c-2972-43c6-8ae4-f2f8f83ba2c5
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d5ed1aae517bb81e5a6cfb888300015e99ec017
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="nodes-that-correspond-directly-to-message-instance-data-and-structure"></a><span data-ttu-id="03cb4-102">Nœuds correspondant directement à une structure et à des données d’instance de message</span><span class="sxs-lookup"><span data-stu-id="03cb4-102">Nodes That Correspond Directly to Message Instance Data and Structure</span></span>
<span data-ttu-id="03cb4-103">Certains types de nœuds que vous utilisez pour créer des schémas dans l’Éditeur BizTalk correspondent directement à des éléments et à des attributs de représentation XML de messages d'instance gérés par le schéma (pour les autres formats de message d’instance, tels que les formats de fichier plat, cette correspondance n’existe qu’après conversion depuis un autre format ou avant conversion vers un autre format).</span><span class="sxs-lookup"><span data-stu-id="03cb4-103">Some of the node types that you use to create schemas in BizTalk Editor correspond directly to elements and attributes in XML representation of instance messages governed by the schema (for other instance message formats, such as flat file formats, this correspondence only exists after translation from the other format and before translation to the other format).</span></span> <span data-ttu-id="03cb4-104">Ces types de nœuds sont **enregistrement** nœuds (y compris racine **enregistrement** nœuds), **élément de champ** nœuds, et **attribut de champ** nœuds.</span><span class="sxs-lookup"><span data-stu-id="03cb4-104">These node types are **Record** nodes (including root **Record** nodes), **Field Element** nodes, and **Field Attribute** nodes.</span></span>  
  
 <span data-ttu-id="03cb4-105">Les valeurs que vous donnez à la **nom de nœud** propriété du **enregistrement** et **élément de champ** nœuds spécifient le nom de l’élément correspondant dans les messages d’instance XML gérés par le schéma.</span><span class="sxs-lookup"><span data-stu-id="03cb4-105">The values you give to the **Node Name** property of **Record** and **Field Element** nodes specify the name of the corresponding element in XML instance messages governed by the schema.</span></span> <span data-ttu-id="03cb4-106">De même, les valeurs que vous donnez à la **nom de nœud** propriété du **attribut de champ** nœuds spécifient le nom de l’attribut correspondant dans les messages d’instance XML gérés par le schéma.</span><span class="sxs-lookup"><span data-stu-id="03cb4-106">Likewise, the values you give to the **Node Name** property of **Field Attribute** nodes specify the name of the corresponding attribute in XML instance messages governed by the schema.</span></span> <span data-ttu-id="03cb4-107">Plus de détails sur cette propriété [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="03cb4-107">More details on this property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
 <span data-ttu-id="03cb4-108">Le reste de cette section fournit des informations sur cette classe de nœuds, avec racine **enregistrement** nœuds reçoit un traitement distinct en raison de leur rôle spécial dans les schémas.</span><span class="sxs-lookup"><span data-stu-id="03cb4-108">The remainder of this section provides more information about this class of nodes, with root **Record** nodes receiving separate treatment due to their special role in schemas.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="03cb4-109">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="03cb4-109">Next steps</span></span> 
  
-   [<span data-ttu-id="03cb4-110">Nœuds racine</span><span class="sxs-lookup"><span data-stu-id="03cb4-110">Root Nodes</span></span>](../core/root-nodes.md)  
  
-   [<span data-ttu-id="03cb4-111">Nœuds d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="03cb4-111">Record Nodes</span></span>](../core/record-nodes.md)  
  
-   [<span data-ttu-id="03cb4-112">Nœuds élément de champ</span><span class="sxs-lookup"><span data-stu-id="03cb4-112">Field Element Nodes</span></span>](../core/field-element-nodes.md)  
  
-   [<span data-ttu-id="03cb4-113">Nœuds attribut de champ</span><span class="sxs-lookup"><span data-stu-id="03cb4-113">Field Attribute Nodes</span></span>](../core/field-attribute-nodes.md)