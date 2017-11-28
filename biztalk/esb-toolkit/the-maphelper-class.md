---
title: La classe MapHelper | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c552c066-835f-4515-939f-dd465a7a5ed0
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de74610c40b37560abcbce040d80320525f0a21c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-maphelper-class"></a><span data-ttu-id="df674-102">La classe MapHelper</span><span class="sxs-lookup"><span data-stu-id="df674-102">The MapHelper Class</span></span>
<span data-ttu-id="df674-103">Utilisez le **MapHelper** classe pour effectuer des transformations directement sans utiliser la transformation de service Web.</span><span class="sxs-lookup"><span data-stu-id="df674-103">Use the **MapHelper** class to perform transformations directly without using the transformation Web service.</span></span>  
  
 <span data-ttu-id="df674-104">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] programme d’installation installe et inscrit l’assembly **Microsof.Practices.ESB.Transform.dll** avec la **MapHelper** classe dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="df674-104">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] installer installs and registers the assembly **Microsof.Practices.ESB.Transform.dll** with the **MapHelper** class in the global assembly cache.</span></span>  
  
 <span data-ttu-id="df674-105">Le **MapHelper** classe expose deux méthodes publiques :</span><span class="sxs-lookup"><span data-stu-id="df674-105">The **MapHelper** class exposes two public methods:</span></span>  
  
-   <span data-ttu-id="df674-106">**TransformMessage**.</span><span class="sxs-lookup"><span data-stu-id="df674-106">**TransformMessage**.</span></span> <span data-ttu-id="df674-107">Cette méthode prend comme paramètres une chaîne qui contient le message à transformer et une chaîne qui contient le nom qualifié complet d’un mappage déployé dans BizTalk.</span><span class="sxs-lookup"><span data-stu-id="df674-107">This method takes as parameters a string that contains the message to transform and a string that contains the fully qualified name of a map deployed in BizTalk.</span></span> <span data-ttu-id="df674-108">La méthode retourne une chaîne qui contient le document transformé.</span><span class="sxs-lookup"><span data-stu-id="df674-108">The method returns a string containing the transformed document.</span></span>  
  
-   <span data-ttu-id="df674-109">**TransformMessageStream**.</span><span class="sxs-lookup"><span data-stu-id="df674-109">**TransformMessageStream**.</span></span> <span data-ttu-id="df674-110">Cette méthode prend comme paramètres un flux qui contient le message à transformer et une chaîne qui contient le nom qualifié complet d’un mappage déployé dans BizTalk.</span><span class="sxs-lookup"><span data-stu-id="df674-110">This method takes as parameters a stream that contains the message to transform and a string that contains the fully qualified name of a map deployed in BizTalk.</span></span> <span data-ttu-id="df674-111">La méthode retourne une chaîne qui contient le document transformé.</span><span class="sxs-lookup"><span data-stu-id="df674-111">The method returns a string that contains the transformed document.</span></span>