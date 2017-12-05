---
title: "Un fichier introuvable exception s’est produite durant la réflexion d’un assembly BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 223147eb-785f-4dfc-b2a6-7d50dfaf8092
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00000896eb4cb97e44ed51602675fc65495552be
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="a-file-not-found-exception-occurred-while-reflecting-a-biztalk-assembly"></a>Une exception de fichier introuvable a été générée lors de la mise en correspondance de l'assembly BizTalk
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Une exception de fichier introuvable a été générée lors de la mise en correspondance de l'assembly BizTalk « {0} ». Ce problème peut survenir si une ou plusieurs dépendances ne sont pas disponibles. Pour corriger ce problème, essayez l’une des opérations suivantes : 1. Copiez les dépendances de l'assembly dans le même dossier. 2. Installez les dépendances manquantes dans le Global Assembly Cache.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que l'assembly BizTalk publie des références à un autre assembly qui ne se trouve ni dans le Global Assembly Cache (GAC) ni dans le même répertoire.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Outre les actions spécifiées dans le message d'erreur, déplacez l'assembly de référence dans le Global Assembly Cache ou copiez-le dans le même emplacement que l'assembly BizTalk  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Visual Studio**, puis cliquez sur **Visual Studio**.  
  
2.  Ouvrez une invite de commandes.  
  
3.  Accédez à l’emplacement de l’assembly, puis entrez **gacutil /I /\<***nom de l’assembly***\>.dll**