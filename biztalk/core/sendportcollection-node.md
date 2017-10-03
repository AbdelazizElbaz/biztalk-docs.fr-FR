---
title: "Nœud SendPortCollection | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SendPortCollection node [binding file]
ms.assetid: 2084507e-ef70-4828-a15f-51d676b14333
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2cf0a968ef995bfdb5a551d16b204743d507b25
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sendportcollection-node"></a><span data-ttu-id="2cf65-102">Nœud SendPortCollection</span><span class="sxs-lookup"><span data-stu-id="2cf65-102">SendPortCollection Node</span></span>
<span data-ttu-id="2cf65-103">Le nœud SendPortCollection d'un fichier de liaison est le nœud parent de tous les nœuds SendPort qui contiennent des informations spécifiques sur un port d'envoi exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="2cf65-103">The SendPortCollection node of a binding file is the parent node for all of the SendPort nodes which contain specific information about a send port that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-sendportcollection-node"></a><span data-ttu-id="2cf65-104">Nœuds du nœud SendPortCollection</span><span class="sxs-lookup"><span data-stu-id="2cf65-104">Nodes in the SendPortCollection node</span></span>  
 <span data-ttu-id="2cf65-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="2cf65-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="2cf65-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="2cf65-106">**Name**</span></span>|<span data-ttu-id="2cf65-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="2cf65-107">**Node Type**</span></span>|<span data-ttu-id="2cf65-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="2cf65-108">**Data Type**</span></span>|<span data-ttu-id="2cf65-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="2cf65-109">**Description**</span></span>|<span data-ttu-id="2cf65-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="2cf65-110">**Restrictions**</span></span>|<span data-ttu-id="2cf65-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="2cf65-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="2cf65-112">Le port d’envoi</span><span class="sxs-lookup"><span data-stu-id="2cf65-112">SendPort</span></span>](../core/sendport-sendportcollection-node.md)|<span data-ttu-id="2cf65-113">Record</span><span class="sxs-lookup"><span data-stu-id="2cf65-113">Record</span></span>|<span data-ttu-id="2cf65-114">SendPort (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="2cf65-114">SendPort (ComplexType)</span></span>|<span data-ttu-id="2cf65-115">Spécifie les informations relatives à un port d'envoi exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="2cf65-115">Specifies information about a send port that is exported with the binding file.</span></span>|<span data-ttu-id="2cf65-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="2cf65-116">Not required</span></span>|<span data-ttu-id="2cf65-117">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="2cf65-117">Default value: none</span></span>|