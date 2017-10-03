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
# <a name="restricted-character-ranges"></a>Plages de caractères restreintes

## <a name="overview"></a>Vue d'ensemble
Lorsque vous créez un schéma pour des messages de fichier plat, vous pouvez imposer à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] d'empêcher à un caractère particulier ou à une plage de caractères d'être inclus dans les messages sortants. Pour ce faire, dans l'Éditeur BizTalk, ouvrez un schéma qui sera utilisé en tant que schéma de destination. Sélectionnez le **schéma** nœud et l’utilisation du **caractères interdits** propriété pour ouvrir la **caractères interdits** boîte de dialogue. Entrez le caractère ou les plages que vous souhaitez exclues de tout message envoyé par BizTalk Server, puis cliquez sur **OK**. Chaque fois que BizTalk Server tente de traiter un caractère spécifié dans le **caractères interdits** boîte de dialogue d’un schéma de destination, le traitement s’arrête et un message d’erreur est générée.  
  
> [!NOTE]
>  Dans BizTalk Server, la restriction des plages de caractères est une fonction de l'Extension de fichier plat. En tant que telle, elle ne s'applique pas aux messages XML. Les extensions qui pourront être offertes à l'avenir pour différents types de messages seront susceptibles de varier dans leur manière d'implémenter la restriction des plages de caractères pour les formats de message qu'elles prennent en charge.  
  
## <a name="see-also"></a>Voir aussi  
-  [Considérations relatives à la création de plat fichier schémas de Message](../core/considerations-when-creating-flat-file-message-schemas.md)   
-  **Caractères interdits (propriété de nœud des schémas de fichier plat**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]