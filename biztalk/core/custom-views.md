---
title: "Vues personnalisées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9084cc07-be98-4c57-afea-4fa369a38bad
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 184f49330374126f4afc0bd4bb376ea31a5ca681
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="custom-views"></a><span data-ttu-id="51042-102">Vues personnalisées</span><span class="sxs-lookup"><span data-stu-id="51042-102">Custom Views</span></span>
<span data-ttu-id="51042-103">Une vue personnalisée est généralement un objet de contrôle de fenêtre en lecture seule (dérivé de **System.Windows.Forms.Control**) et est fournie par une extension pour représenter le schéma dans un format d’affichage personnalisé pour le type de fichier ou de fichiers pris en charge par l’extension de l’Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="51042-103">A custom view is typically a read-only window control object (derived from **System.Windows.Forms.Control**), and is provided by an extension to represent the schema in a display format customized for the type of file or files supported by the BizTalk Editor extension.</span></span> <span data-ttu-id="51042-104">Une extension peut implémenter plusieurs vues personnalisées (les vues personnalisées ne lui sont cependant pas indispensables).</span><span class="sxs-lookup"><span data-stu-id="51042-104">An extension can implement multiple custom views, though it need not have any custom view.</span></span>  
  
 <span data-ttu-id="51042-105">Les vues personnalisées sont affichées en tant que vues supplémentaires dans le même volet de l'Éditeur BizTalk que la vue XSD et sont accessibles à l'aide des onglets situés dans la partie inférieure des vues.</span><span class="sxs-lookup"><span data-stu-id="51042-105">A custom view is displayed as an additional view in the same BizTalk Editor pane as the XSD view, accessible by using tabs at the bottom of the views.</span></span> <span data-ttu-id="51042-106">Par exemple, l'Extension de fichier plat ajoute une nouvelle vue avec un onglet étiqueté Fichier plat.</span><span class="sxs-lookup"><span data-stu-id="51042-106">For example, the Flat File Extension adds a new view with a tab labeled Flat File.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51042-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51042-107">See Also</span></span>  
 [<span data-ttu-id="51042-108">Extension de l’Éditeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="51042-108">Extending BizTalk Editor</span></span>](../core/extending-biztalk-editor.md)