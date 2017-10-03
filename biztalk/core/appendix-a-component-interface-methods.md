---
title: "Annexe a : méthodes d’Interface de composant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- component interfaces, methods
- methods, component interfaces
- component interface methods
ms.assetid: c8377589-fbdf-4287-b822-53263a00381d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61cb5b87cb063f22c889291b8eff3b2be50d64a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="appendix-a-component-interface-methods"></a><span data-ttu-id="851dd-102">Annexe a : méthodes d’Interface de composant</span><span class="sxs-lookup"><span data-stu-id="851dd-102">Appendix A: Component Interface Methods</span></span>
<span data-ttu-id="851dd-103">L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise offre des méthodes standard pour les interfaces de composant.</span><span class="sxs-lookup"><span data-stu-id="851dd-103">Microsoft BizTalk Adapter for PeopleSoft Enterprise provides standard methods for component interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="851dd-104">Le paramètre `interactiveMode`, dans la version Ex des méthodes, contribue au débogage d'un appel effectué au système principal (`Create/CreateEx`, `Update/UpdateEx` et `DeleteOnly`).</span><span class="sxs-lookup"><span data-stu-id="851dd-104">The `interactiveMode` parameter, in the Ex-version of the methods, assists in debugging a call to the back-end (`Create/CreateEx`, `Update/UpdateEx`, and `DeleteOnly`).</span></span> <span data-ttu-id="851dd-105">Chaque élément de l'appel *Ex effectué au système principal est appelé séparément, de manière à ce que vous identifiez avec précision celui qui a échoué.</span><span class="sxs-lookup"><span data-stu-id="851dd-105">Each item in the *Ex call to the back-end is called separately, so you know exactly which item failed.</span></span> <span data-ttu-id="851dd-106">Il existe une baisse des performances lorsque vous utilisez un \*Ex méthode étant donné que les éléments de chaque propriété reçoit un appel distinct.</span><span class="sxs-lookup"><span data-stu-id="851dd-106">There is a decrease in performance when you use an \*Ex method because each property's item receives a separate call.</span></span> <span data-ttu-id="851dd-107">Vous pouvez développer avec \*Ex méthode et puis que vous passez à la méthode principale (par exemple, `Create`) pour la production.</span><span class="sxs-lookup"><span data-stu-id="851dd-107">You can develop with \*Ex method and then switch to the main method (for example, `Create`) for production.</span></span> <span data-ttu-id="851dd-108">Vous pouvez également utiliser un commutateur de débogage au niveau de production pour basculer entre l’utilisation de la méthode et le \*Ex (méthode).</span><span class="sxs-lookup"><span data-stu-id="851dd-108">You can also use a debug switch at production to switch between using the method and the \*Ex method.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="851dd-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="851dd-109">In This Section</span></span>  
  
-   [<span data-ttu-id="851dd-110">Méthode CreateEx</span><span class="sxs-lookup"><span data-stu-id="851dd-110">CreateEx Method</span></span>](../core/createex-method.md)  
  
-   [<span data-ttu-id="851dd-111">Méthode DeleteOnly</span><span class="sxs-lookup"><span data-stu-id="851dd-111">DeleteOnly Method</span></span>](../core/deleteonly-method.md)  
  
-   [<span data-ttu-id="851dd-112">Find (méthode)</span><span class="sxs-lookup"><span data-stu-id="851dd-112">Find Method</span></span>](../core/find-method.md)  
  
-   [<span data-ttu-id="851dd-113">Get (méthode)</span><span class="sxs-lookup"><span data-stu-id="851dd-113">Get Method</span></span>](../core/get-method.md)  
  
-   [<span data-ttu-id="851dd-114">Méthode UpdateEx</span><span class="sxs-lookup"><span data-stu-id="851dd-114">UpdateEx Method</span></span>](../core/updateex-method.md)  
  
-   [<span data-ttu-id="851dd-115">Méthodes définies par l’utilisateur des composants Interface</span><span class="sxs-lookup"><span data-stu-id="851dd-115">Component Interface User-Defined Methods</span></span>](../core/component-interface-user-defined-methods.md)  
  
-   [<span data-ttu-id="851dd-116">Propriétés de la Date d’effet</span><span class="sxs-lookup"><span data-stu-id="851dd-116">Effective Date Properties</span></span>](../core/effective-date-properties.md)