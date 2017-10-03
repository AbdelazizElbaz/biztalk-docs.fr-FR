---
title: "XSLT personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functoid types, Scripting
- maps, customizing
- functoid types, Looping
- maps, extending
- XSLT, maps
- Scripting functoids
- maps, XSLT
- customizing, maps
- maps, replacing
ms.assetid: e254d16d-4d16-4c23-a3ed-cc98eea9939a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4adf2abe438b3972419184b1297eaff5578c5bde
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="custom-xslt"></a><span data-ttu-id="ccf0e-102">XSLT personnalisé</span><span class="sxs-lookup"><span data-stu-id="ccf0e-102">Custom XSLT</span></span>
<span data-ttu-id="ccf0e-103">Si le code XSLT (Extensible Stylesheet Language Transformations) n’a plus de secret pour vous, vous pouvez l’utiliser pour personnaliser, étendre ou remplacer des mappages BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ccf0e-103">If you are familiar with Extensible Stylesheet Language Transformations (XSLT) code, you can use it to customize, extend, or replace BizTalk maps.</span></span> <span data-ttu-id="ccf0e-104">La façon la plus simple à utiliser XSLT est avec le **script** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="ccf0e-104">The simplest way to use XSLT is with the **Scripting** functoid.</span></span> <span data-ttu-id="ccf0e-105">Le **script** fonctoid accepte les scripts dans de nombreux. NET-langues activées, y compris les XSLT.</span><span class="sxs-lookup"><span data-stu-id="ccf0e-105">The **Scripting** functoid accepts scripts in many .NET-enabled languages, including XSLT.</span></span> <span data-ttu-id="ccf0e-106">Pour plus d’informations sur l’utilisation de XSLT avec le **script** fonctoid, consultez [scripts utilisant Inline XSLT et modèles d’appel XSLT](../core/scripting-using-inline-xslt-and-xslt-call-templates.md).</span><span class="sxs-lookup"><span data-stu-id="ccf0e-106">For more information about using XSLT with the **Scripting** functoid, see [Scripting Using Inline XSLT and XSLT Call Templates](../core/scripting-using-inline-xslt-and-xslt-call-templates.md).</span></span>  
  
 <span data-ttu-id="ccf0e-107">Si vous disposez du code XSLT que vous avez utilisé pour convertir un message d'instance en un autre, vous pouvez l’utiliser directement au lieu d’un mappage BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ccf0e-107">If you have XSLT code that you have been using to convert one instance message into another, you can use that code directly in place of a BizTalk map.</span></span> <span data-ttu-id="ccf0e-108">Pour plus d’informations sur le remplacement BizTalk mappe avec votre code XSLT, voir [la création d’un mappage sans mappages](../core/how-to-create-a-map-without-maps.md).</span><span class="sxs-lookup"><span data-stu-id="ccf0e-108">For information about replacing BizTalk maps with your XSLT code, see [How to Create a Map without Maps](../core/how-to-create-a-map-without-maps.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccf0e-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccf0e-109">See Also</span></span>  
 <span data-ttu-id="ccf0e-110">[Mappages](../core/maps.md) </span><span class="sxs-lookup"><span data-stu-id="ccf0e-110">[Maps](../core/maps.md) </span></span>  
 [<span data-ttu-id="ccf0e-111">Création de mappages à l’aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="ccf0e-111">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)