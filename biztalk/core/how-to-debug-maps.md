---
title: "Comment déboguer des mappages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1ee1e26-fced-4126-b48a-71007043424d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e40964b267ad0788308a92490a106f940a6cb33e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-debug-maps"></a>Comment déboguer des mappages
Le **déboguer le mappage** fonctionnalité est utile pour identifier et résoudre les problèmes de mappage complexes. Cette rubrique fournit des instructions pas à pas pour déboguer des mappages à l'aide du débogueur inline XSLT.  
  
> [!NOTE]
>  Lors du débogage de la carte, le **déboguer le mappage** fonctionnalité utilise les propriétés de fichier de mappage **Instance d’entrée TestMap** et **Instance de sortie TestMap**. Par conséquent, avant de déboguer le mappage, nous vous recommandons de configurer les propriétés d'instance d'entrée et de sortie dans le fichier de mappage.  
  
### <a name="to-debug-a-biztalk-map"></a>Pour déboguer un mappage BizTalk  
  
1.  Dans l’Explorateur de solutions, cliquez sur la carte que vous souhaitez tester, puis cliquez sur **déboguer le mappage**. [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]Affiche la carte au format XSLT dans son éditeur.  
  
2.  Appuyez sur F10 ou F11 pour déboguer le code XSL. Lorsque vous appuyez sur F11 suite à un appel de fonctoid, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] passe dans le code C# pour le fonctoid. Vous pouvez visualiser les valeurs des variables utilisées dans le code source du fonctoid dans le Débogueur local de Windows.