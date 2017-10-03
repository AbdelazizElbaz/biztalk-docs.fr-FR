---
title: "Restreint les plages de caractères | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e12213bf-750e-43a2-998a-949fa4255b73
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74f1399aaa828d5c23c2600ebabeb7063a982447
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="restricted-character-ranges"></a><span data-ttu-id="e4514-102">Plages de caractères restreintes</span><span class="sxs-lookup"><span data-stu-id="e4514-102">Restricted Character Ranges</span></span>

## <a name="overview"></a><span data-ttu-id="e4514-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="e4514-103">Overview</span></span>
<span data-ttu-id="e4514-104">Lorsque vous créez un schéma pour des messages de fichier plat, vous pouvez imposer à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] d'empêcher à un caractère particulier ou à une plage de caractères d'être inclus dans les messages sortants.</span><span class="sxs-lookup"><span data-stu-id="e4514-104">When creating a schema for flat file messages, you can direct [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to block a particular character or a range of characters from being included in any outgoing message.</span></span> <span data-ttu-id="e4514-105">Pour ce faire, dans l'Éditeur BizTalk, ouvrez un schéma qui sera utilisé en tant que schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="e4514-105">To do this, in BizTalk Editor, open a schema that is to be used as a destination schema.</span></span> <span data-ttu-id="e4514-106">Sélectionnez le **schéma** nœud et l’utilisation du **caractères interdits** propriété pour ouvrir la **caractères interdits** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="e4514-106">Select the **Schema** node and the use the **Restricted Characters** property to open the **Restricted Characters** dialog box.</span></span> <span data-ttu-id="e4514-107">Entrez le caractère ou les plages que vous souhaitez exclues de tout message envoyé par BizTalk Server, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e4514-107">Enter the character range(s) that you want to prevent being included in any message sent by BizTalk Server, and then click **OK**.</span></span> <span data-ttu-id="e4514-108">Chaque fois que BizTalk Server tente de traiter un caractère spécifié dans le **caractères interdits** boîte de dialogue d’un schéma de destination, le traitement s’arrête et un message d’erreur est générée.</span><span class="sxs-lookup"><span data-stu-id="e4514-108">Whenever BizTalk Server attempts to process a character specified in the **Restricted Characters** dialog box of a destination schema, processing stops and an error message is generated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4514-109">Dans BizTalk Server, la restriction des plages de caractères est une fonction de l'Extension de fichier plat. En tant que telle, elle ne s'applique pas aux messages XML.</span><span class="sxs-lookup"><span data-stu-id="e4514-109">In BizTalk Server, character range restriction is a function of the Flat File Extension, and as such, does not apply to XML messages.</span></span> <span data-ttu-id="e4514-110">Les extensions qui pourront être offertes à l'avenir pour différents types de messages seront susceptibles de varier dans leur manière d'implémenter la restriction des plages de caractères pour les formats de message qu'elles prennent en charge.</span><span class="sxs-lookup"><span data-stu-id="e4514-110">Extensions that might be offered in the future for different types of messages might differ in how they implement character range restriction for their supported message formats.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4514-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4514-111">See Also</span></span>  
-  [<span data-ttu-id="e4514-112">Considérations relatives à la création de plat fichier schémas de Message</span><span class="sxs-lookup"><span data-stu-id="e4514-112">Considerations When Creating Flat File Message Schemas</span></span>](../core/considerations-when-creating-flat-file-message-schemas.md)   
-  <span data-ttu-id="e4514-113">**Caractères interdits (propriété de nœud des schémas de fichier plat**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="e4514-113">**Restricted Characters (Node Property of Flat File Schemas** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>