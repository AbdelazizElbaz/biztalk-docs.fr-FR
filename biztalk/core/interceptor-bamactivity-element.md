---
title: "Élément BamActivity de l’intercepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6dee61b4-83cd-4a22-b8a6-1c1a7ea3648b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd43869922e46187c8b2e06155d525e428edd905
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interceptor-bamactivity-element"></a><span data-ttu-id="ae0b8-102">Élément BamActivity de l'intercepteur</span><span class="sxs-lookup"><span data-stu-id="ae0b8-102">Interceptor BamActivity Element</span></span>
<span data-ttu-id="ae0b8-103">Le **BamActivity** élément définit une activité BAM unique.</span><span class="sxs-lookup"><span data-stu-id="ae0b8-103">The **BamActivity** element defines a single BAM activity.</span></span>  
  
## <a name="format"></a><span data-ttu-id="ae0b8-104">Format</span><span class="sxs-lookup"><span data-stu-id="ae0b8-104">Format</span></span>  
 <span data-ttu-id="ae0b8-105">Le `BamActivity` élément inclut un **nom** d’attribut et contient un ou plusieurs `OnEvent` éléments.</span><span class="sxs-lookup"><span data-stu-id="ae0b8-105">The `BamActivity` element includes a **Name** attribute and contains one or more `OnEvent` elements.</span></span>  
  
```  
<ic:BamActivity Name="PurchaseOrder">  
  <!-- One or more OnEvent elements -->  
</ic:BamActivity>   
```  
  
### <a name="attributes"></a><span data-ttu-id="ae0b8-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="ae0b8-106">Attributes</span></span>  
  
|<span data-ttu-id="ae0b8-107">Nom de l'attribut</span><span class="sxs-lookup"><span data-stu-id="ae0b8-107">Attribute name</span></span>|<span data-ttu-id="ae0b8-108"> Description</span><span class="sxs-lookup"><span data-stu-id="ae0b8-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ae0b8-109">Nom</span><span class="sxs-lookup"><span data-stu-id="ae0b8-109">Name</span></span>|<span data-ttu-id="ae0b8-110">Nom de l'activité BAM défini par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ae0b8-110">User-defined name of the BAM activity.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ae0b8-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="ae0b8-111">Example</span></span>  
 <span data-ttu-id="ae0b8-112">Le code suivant contient un exemple de BamActivity pour « MyOrderWorkflow » avec un OnEvent unique.</span><span class="sxs-lookup"><span data-stu-id="ae0b8-112">The following example contains a sample BamActivity for "MyOrderWorkflow" with a single OnEvent.</span></span>  
  
```  
<ic:BamActivity Name="MyOrderWorkflow">  
  <ic:OnEvent Name="MyActivityEvent"  Source="OrderWorkflow">  
    …  
  </ic:OnEvent>  
</ic:BamActivity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae0b8-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae0b8-113">See Also</span></span>  
 <span data-ttu-id="ae0b8-114">[Élément EventSource de l’intercepteur](../core/interceptor-eventsource-element.md) </span><span class="sxs-lookup"><span data-stu-id="ae0b8-114">[Interceptor EventSource Element](../core/interceptor-eventsource-element.md) </span></span>  
 [<span data-ttu-id="ae0b8-115">Élément OnEvent de l’intercepteur</span><span class="sxs-lookup"><span data-stu-id="ae0b8-115">Interceptor OnEvent Element</span></span>](../core/interceptor-onevent-element.md)