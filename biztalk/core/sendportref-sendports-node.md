---
title: SendPortRef (nœud ports d’envoi) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SendPortRef node [binding file]
ms.assetid: 6c799b23-a9a4-4686-a04e-0450b4eef889
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9290a535ebcaf0c23097cacbd3412f64c2808f40
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sendportref-sendports-node"></a><span data-ttu-id="e6c25-102">SendPortRef (Nœud SendPorts)</span><span class="sxs-lookup"><span data-stu-id="e6c25-102">SendPortRef (SendPorts Node)</span></span>
<span data-ttu-id="e6c25-103">Le nœud SendPortRef du nœud SendPorts d'un fichier de liaison spécifie le nom d'un port d'envoi référencé par une liste de distribution.</span><span class="sxs-lookup"><span data-stu-id="e6c25-103">The SendPortRef node of the SendPorts node of a binding file specifies the name of a send port referenced by a distribution list.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6c25-104">Une liste de distribution est appelée groupe de ports d'envoi dans l'Administrateur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e6c25-104">A distribution list is referred to as a send port group in the BizTalk Administrator.</span></span>  
  
## <a name="nodes-in-the-sendportref-node"></a><span data-ttu-id="e6c25-105">Nœuds du nœud SendPortRef</span><span class="sxs-lookup"><span data-stu-id="e6c25-105">Nodes in the SendPortRef node</span></span>  
 <span data-ttu-id="e6c25-106">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="e6c25-106">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="e6c25-107">**Nom**</span><span class="sxs-lookup"><span data-stu-id="e6c25-107">**Name**</span></span>|<span data-ttu-id="e6c25-108">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="e6c25-108">**Node Type**</span></span>|<span data-ttu-id="e6c25-109">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="e6c25-109">**Data Type**</span></span>|<span data-ttu-id="e6c25-110">**Description**</span><span class="sxs-lookup"><span data-stu-id="e6c25-110">**Description**</span></span>|<span data-ttu-id="e6c25-111">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="e6c25-111">**Restrictions**</span></span>|<span data-ttu-id="e6c25-112">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="e6c25-112">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="e6c25-113">Nom</span><span class="sxs-lookup"><span data-stu-id="e6c25-113">Name</span></span>|<span data-ttu-id="e6c25-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="e6c25-114">Attribute</span></span>|<span data-ttu-id="e6c25-115">xs:string</span><span class="sxs-lookup"><span data-stu-id="e6c25-115">xs:string</span></span>|<span data-ttu-id="e6c25-116">Spécifie le nom du port d'envoi référencé par la liste de distribution.</span><span class="sxs-lookup"><span data-stu-id="e6c25-116">Specifies the name of the send port referenced by the distribution list.</span></span>|<span data-ttu-id="e6c25-117">Facultatif</span><span class="sxs-lookup"><span data-stu-id="e6c25-117">Not required</span></span>|<span data-ttu-id="e6c25-118">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="e6c25-118">Default value: empty</span></span>|