---
title: "Comment créer un mappage sans mappages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 520ec44f-5aca-4271-8835-b8e784214061
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81be2591c1d8f20f5b8dd01cf01c03e8daed9c9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-map-without-maps"></a><span data-ttu-id="3e38e-102">Création d'un mappage sans mappages</span><span class="sxs-lookup"><span data-stu-id="3e38e-102">How to Create a Map without Maps</span></span>
<span data-ttu-id="3e38e-103">Si vous disposez du code XSLT que vous avez utilisé pour convertir les messages d'instance, vous pouvez vous en servir directement au lieu de créer un mappage.</span><span class="sxs-lookup"><span data-stu-id="3e38e-103">If you have XSLT code you have been using to convert instance messages, you can use that code directly instead of creating a map.</span></span>  
  
 <span data-ttu-id="3e38e-104">À l’aide de votre code XSLT implique la création d’un mappage vide et en définissant son **chemin du XSLT personnalisé** propriété de grille.</span><span class="sxs-lookup"><span data-stu-id="3e38e-104">Using your XSLT code involves creating an empty map and setting its **Custom XSLT Path** grid property.</span></span> <span data-ttu-id="3e38e-105">Si votre code XSLT utilise des assemblys .NET externes, vous devez également créer un fichier XML avec extensions personnalisées.</span><span class="sxs-lookup"><span data-stu-id="3e38e-105">If your XSLT code uses external .NET assemblies, you also need to create a custom extension XML file.</span></span> <span data-ttu-id="3e38e-106">Pour plus d’informations sur la structure d’un fichier XML avec extensions personnalisées, consultez la **XML avec extensions personnalisées (propriété de grille)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="3e38e-106">For information about the structure of a custom extension XML file, see the **Custom Extension XML (Grid Property)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="use-custom-xslt-code-in-place-of-a-map"></a><span data-ttu-id="3e38e-107">Utiliser du code XSLT personnalisé à la place d’une carte</span><span class="sxs-lookup"><span data-stu-id="3e38e-107">Use custom XSLT code in place of a map</span></span>  
  
1.  <span data-ttu-id="3e38e-108">Créez un mappage BizTalk vide dans votre projet et configurez les schémas source et de destination.</span><span class="sxs-lookup"><span data-stu-id="3e38e-108">Create an empty BizTalk map in your project and set the source and destination schemas.</span></span>  
  
     <span data-ttu-id="3e38e-109">Pour plus d’informations sur la création de la carte et de configuration de schémas, consultez [création de mappages](../core/creating-maps.md).</span><span class="sxs-lookup"><span data-stu-id="3e38e-109">For information about creating the map and setting the schemas, see [Creating Maps](../core/creating-maps.md).</span></span>  
  
2.  <span data-ttu-id="3e38e-110">Dans la vue Grille, cliquez sur la grille du Mappeur.</span><span class="sxs-lookup"><span data-stu-id="3e38e-110">In the Grid view, click the mapper grid.</span></span>  
  
     <span data-ttu-id="3e38e-111">La fenêtre Propriétés affiche les **grille** propriétés.</span><span class="sxs-lookup"><span data-stu-id="3e38e-111">The Properties window shows the **Grid** properties.</span></span>  
  
3.  <span data-ttu-id="3e38e-112">Dans la fenêtre Propriétés, sélectionnez **chemin du XSLT personnalisé** et cliquez sur le bouton de sélection (**...** ) bouton.</span><span class="sxs-lookup"><span data-stu-id="3e38e-112">In the Properties window, select **Custom XSLT Path** and click the ellipsis (**…**) button.</span></span>  
  
4.  <span data-ttu-id="3e38e-113">Dans le **ouvrir** boîte de dialogue zone, accédez au fichier, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="3e38e-113">In the **Open** dialog box, navigate to the file and click **Open**.</span></span>  
  
     <span data-ttu-id="3e38e-114">Le **chemin du XSLT personnalisé** est définie.</span><span class="sxs-lookup"><span data-stu-id="3e38e-114">The **Custom XSLT Path** property is set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e38e-115">Le Mappeur BizTalk ne prend en charge que XSLT 1.0.</span><span class="sxs-lookup"><span data-stu-id="3e38e-115">BizTalk Mapper supports XSLT 1.0 only.</span></span> <span data-ttu-id="3e38e-116">Il ne prend pas en charge XSLT 2.0.</span><span class="sxs-lookup"><span data-stu-id="3e38e-116">Using XSLT 2.0 in BizTalk Mapper is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e38e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e38e-117">See Also</span></span>  
 <span data-ttu-id="3e38e-118">[À propos des mappages](../core/about-maps.md) </span><span class="sxs-lookup"><span data-stu-id="3e38e-118">[About Maps](../core/about-maps.md) </span></span>  
 <span data-ttu-id="3e38e-119">[Écriture de scripts utilisant Inline XSLT et modèles d’appel XSLT](../core/scripting-using-inline-xslt-and-xslt-call-templates.md) </span><span class="sxs-lookup"><span data-stu-id="3e38e-119">[Scripting Using Inline XSLT and XSLT Call Templates](../core/scripting-using-inline-xslt-and-xslt-call-templates.md) </span></span>  
 [<span data-ttu-id="3e38e-120">XSLT personnalisé</span><span class="sxs-lookup"><span data-stu-id="3e38e-120">Custom XSLT</span></span>](../core/custom-xslt.md)   