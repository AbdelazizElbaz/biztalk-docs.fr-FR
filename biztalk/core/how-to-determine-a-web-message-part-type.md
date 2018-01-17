---
title: "Comment déterminer un Type de partie de Message Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web messages, message types
- Web services, Web messages
- Web messages, parts
ms.assetid: bdd1f604-ec35-41e3-b5a8-1e0ad0193eff
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6102e39eb38e919c68405ae18bebde0b46c0b053
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-determine-a-web-message-part-type"></a><span data-ttu-id="5feb0-102">Choix d'un type de partie de message web</span><span class="sxs-lookup"><span data-stu-id="5feb0-102">How to Determine a Web Message Part Type</span></span>
<span data-ttu-id="5feb0-103">Vous pouvez déterminer si un type de partie de message Web est un type .NET primitif ou un type de schéma à l'aide de la fenêtre Propriétés pour un type de message Web donné.</span><span class="sxs-lookup"><span data-stu-id="5feb0-103">You can determine if a Web message part type is a primitive .NET type or a schema type by using the Properties window for a given Web message type.</span></span>  
  
### <a name="to-determine-a-web-message-part-type"></a><span data-ttu-id="5feb0-104">Pour déterminer un type de partie de message Web</span><span class="sxs-lookup"><span data-stu-id="5feb0-104">To determine a Web message part type</span></span>  
  
1.  <span data-ttu-id="5feb0-105">Avec une orchestration ouverte, dans le **vue** menu, cliquez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.</span><span class="sxs-lookup"><span data-stu-id="5feb0-105">With an orchestration open, on the **View** menu, click **Other Windows**,and then click **Orchestration View**.</span></span>  
  
2.  <span data-ttu-id="5feb0-106">Développez le **Types Message à parties multiples** nœud, puis développez un type de message Web.</span><span class="sxs-lookup"><span data-stu-id="5feb0-106">Expand the **Multi-part Message Types** node, and then expand a Web message type.</span></span>  
  
3.  <span data-ttu-id="5feb0-107">Sélectionnez une partie de message.</span><span class="sxs-lookup"><span data-stu-id="5feb0-107">Select a message part.</span></span>  
  
     <span data-ttu-id="5feb0-108">Une signature de partie de message Web qui commence par  **\< *espace de noms par défaut du projet*\>.\< *Nom de référence web*\>. Référence. \< *racine du schéma* \>**  est un type de schéma.</span><span class="sxs-lookup"><span data-stu-id="5feb0-108">A Web message part signature that begins as **\<*project default namespace*\>.\<*Web reference name*\>.Reference.\<*schema root*\>** is a schema type.</span></span> <span data-ttu-id="5feb0-109">Le  **\< *racine du schéma* \>**  partie du type est l’élément racine du schéma de référence Web qui construit la partie de message Web.</span><span class="sxs-lookup"><span data-stu-id="5feb0-109">The **\<*schema root*\>** part of the type is the root element of the Web reference schema that constructs the Web message part.</span></span> <span data-ttu-id="5feb0-110">Sinon, la signature de partie de message est un type .NET primitif tel que **System.String** ou **System.Int32**.</span><span class="sxs-lookup"><span data-stu-id="5feb0-110">Otherwise, the message part signature is a primitive .NET type such as **System.String** or **System.Int32**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5feb0-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5feb0-111">See Also</span></span>  
 [<span data-ttu-id="5feb0-112">Construction de messages web</span><span class="sxs-lookup"><span data-stu-id="5feb0-112">Constructing Web Messages</span></span>](../core/constructing-web-messages.md)