---
title: La classe Resolver | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9ebd6c2-fd86-471a-bc50-b1b89f701fab
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1359bcbb9c6c918fc0ee6d5e67bacb8e3559c84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-resolver-class"></a><span data-ttu-id="8023b-102">La classe de programme de résolution</span><span class="sxs-lookup"><span data-stu-id="8023b-102">The Resolver Class</span></span>
<span data-ttu-id="8023b-103">Le **résolveur** classe est une structure simple qui expose une paire nom/valeur.</span><span class="sxs-lookup"><span data-stu-id="8023b-103">The **Resolver** class is a simple structure that exposes a name/value pair.</span></span> <span data-ttu-id="8023b-104">Le service Web du programme de résolution retourne une collection générique d’instances de cette classe à partir de ses méthodes.</span><span class="sxs-lookup"><span data-stu-id="8023b-104">The Resolver Web service returns a generic collection of instances of this class from its methods.</span></span>  
  
 <span data-ttu-id="8023b-105">Le programme d’installation ESB Core installe et enregistre le **Microsoft.Practices.ESB.Resolver.dll** assembly avec la classe de programme de résolution dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="8023b-105">The ESB Core installer installs and registers the **Microsoft.Practices.ESB.Resolver.dll** assembly with Resolver class in the global assembly cache.</span></span>  
  
 <span data-ttu-id="8023b-106">L’utilisation d’une nom/valeur basée sur le dictionnaire approche rend plus faciles à ajouter de nouveaux éléments dans les futures mises à jour et réduit la taille du résultat de la résolution en évitant d’inclusion des propriétés non pertinentes qui dépendent de la méthode de résolution et le type de programme de résolution en cours.</span><span class="sxs-lookup"><span data-stu-id="8023b-106">The use of a dictionary-based name/value approach makes it easier to add new items in future releases and minimizes the size of the resolution result by avoiding inclusion of non-relevant properties that depend on the resolution method and the current resolver type.</span></span>  
  
 <span data-ttu-id="8023b-107">Le **résolveur** classe expose deux propriétés :</span><span class="sxs-lookup"><span data-stu-id="8023b-107">The **Resolver** class exposes two properties:</span></span>  
  
-   <span data-ttu-id="8023b-108">**Nom**.</span><span class="sxs-lookup"><span data-stu-id="8023b-108">**Name**.</span></span> <span data-ttu-id="8023b-109">Il s’agit du nom d’une paire nom/valeur qui contient des informations qui sont retournées après qu’une chaîne de connexion est résolue.</span><span class="sxs-lookup"><span data-stu-id="8023b-109">This is the name of a name/value pair that contains information that is returned after a connection string is resolved.</span></span>  
  
-   <span data-ttu-id="8023b-110">**Valeur**.</span><span class="sxs-lookup"><span data-stu-id="8023b-110">**Value**.</span></span> <span data-ttu-id="8023b-111">Il s’agit de la valeur qui correspond au nom de la paire nom/valeur.</span><span class="sxs-lookup"><span data-stu-id="8023b-111">This is the value that corresponds to the name of the name/value pair.</span></span>