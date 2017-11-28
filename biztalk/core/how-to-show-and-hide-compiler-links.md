---
title: Comment afficher et masquer les liaisons du compilateur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66bfd9de-c4d2-46ee-854f-cf7c7cd07368
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66d9b9ee8901ea2d93a73fd227a0ac1623e25669
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-show-and-hide-compiler-links"></a><span data-ttu-id="da00b-102">Affichage et masquage des liaisons du compilateur</span><span class="sxs-lookup"><span data-stu-id="da00b-102">How to Show and Hide Compiler Links</span></span>
<span data-ttu-id="da00b-103">Lorsque vous compilez un mappage, le Mappeur BizTalk crée des liens supplémentaires, baptisés liens de compilateur et représentant l'ensemble des liaisons nécessaires dans le mappage.</span><span class="sxs-lookup"><span data-stu-id="da00b-103">When you compile a map, BizTalk Mapper creates additional links, known as compiler links to account for all linking needed in the map.</span></span> <span data-ttu-id="da00b-104">Certains de ces liens ont uniquement un caractère implicite conféré par les liens que vous avez créés.</span><span class="sxs-lookup"><span data-stu-id="da00b-104">Some of these links are only implied by the links you created.</span></span> <span data-ttu-id="da00b-105">Lorsque vous compilez, ou testez, un mappage, la dernière ligne de la fenêtre de sortie Visual Studio vous permet d'afficher ou de masquer ces liens de compilateur supplémentaires dans la fenêtre principale.</span><span class="sxs-lookup"><span data-stu-id="da00b-105">When you compile, or test, a map, the final line in the Visual Studio Output window allows you to show or hide these additional compiler links in the main window.</span></span> <span data-ttu-id="da00b-106">Par défaut, les liens de compilateur apparaissent sous forme de lignes en pointillés rouges.</span><span class="sxs-lookup"><span data-stu-id="da00b-106">By default, the compiler links appear as red dashed lines.</span></span>  
  
### <a name="to-show-or-hide-compiler-links"></a><span data-ttu-id="da00b-107">Pour afficher ou masquer des liens de compilateur</span><span class="sxs-lookup"><span data-stu-id="da00b-107">To show or hide compiler links</span></span>  
  
1.  <span data-ttu-id="da00b-108">Dans l’Explorateur de solutions, cliquez sur la carte dont vous souhaitez afficher, puis cliquez sur les liens de compilateur **Test Map**.</span><span class="sxs-lookup"><span data-stu-id="da00b-108">In Solution Explorer, right-click the map whose complier links you want to view, and then click **Test Map**.</span></span>  
  
2.  <span data-ttu-id="da00b-109">Dans la fenêtre liste d’erreurs Visual Studio, accédez à la fin et double-cliquez sur la ligne indiquant **double-cliquez ici pour afficher/masquer les liaisons du compilateur**.</span><span class="sxs-lookup"><span data-stu-id="da00b-109">In the Visual Studio Error List window, scroll to the end and double-click the line that says **Double-click here to show/Hide compiler links**.</span></span>  
  
     <span data-ttu-id="da00b-110">Pour faire passer l'état de l'affichage des liens de compilateur d'affiché à masqué, ou de masqué à affiché, il vous suffit de double-cliquer sur cette ligne à nouveau.</span><span class="sxs-lookup"><span data-stu-id="da00b-110">To change the display state of compiler links from shown to hidden, or from hidden to shown, just double-click that line again.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da00b-111">Lorsque vous génération/regénération d’un projet ou solution BizTalk contenant un ou plusieurs mappages, le message **double-cliquez ici pour afficher/masquer les liaisons du compilateur** s’affiche dans le **liste d’erreurs** fenêtre de Visual Studio pour tous les mappages dans le projet ou la solution.</span><span class="sxs-lookup"><span data-stu-id="da00b-111">When you build/rebuild a BizTalk project or solution containing one or more maps, the message **Double-click here to show/Hide compiler links** is displayed in the **Error List** window of Visual Studio for all the maps in the project or solution.</span></span>  
  
 <span data-ttu-id="da00b-112">Pour tester un mappage, vous devez configurer les propriétés des instances d'entrée et de sortie.</span><span class="sxs-lookup"><span data-stu-id="da00b-112">To test a map, you must configure the properties for the input and output instances.</span></span> <span data-ttu-id="da00b-113">Pour plus d’informations sur la façon de configurer ces propriétés, consultez [comment configurer la Validation de mappage et les paramètres de Test](../core/how-to-configure-map-validation-and-test-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="da00b-113">For more information about how to configure these properties, see [How to Configure Map Validation and Test Parameters](../core/how-to-configure-map-validation-and-test-parameters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da00b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da00b-114">See Also</span></span>  
 [<span data-ttu-id="da00b-115">À l’aide de liens pour spécifier l’enregistrement et les mappages de champs</span><span class="sxs-lookup"><span data-stu-id="da00b-115">Using Links to Specify Record and Field Mappings</span></span>](../core/using-links-to-specify-record-and-field-mappings.md)