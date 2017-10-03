---
title: "Single Sign-On : Événement 11026 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e39b252d-2ed0-4006-aac2-4dce6504afb2
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ecee6d3c3e6dcf01b8489c4041f4aab717eba585
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11026"></a>Single Sign-On : Événement 11026
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11026|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_EXISTING_GROUP_MAPPING|  
|Texte du message|Le nouveau mappage de groupe n'a pas pu être créé en raison d'un conflit avec un nom existant. Supprimez le mappage existant, puis réessayez.%r<br /><br /> Mappage existant : %1 %r<br /><br /> Nouveau mappage : %2 %r<br /><br /> Compte externe : %3 %r<br /><br /> Nom de l’application : %4|  
  
## <a name="explanation"></a>Explication  
 Ceci est probablement dû au fait que votre système utilise une ancienne version de l'authentification unique de l'entreprise, ainsi que des applications de groupe anciennes.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Supprimez puis recréez le mappage, comme indiqué dans l'avertissement. En cas d'échec, vous devrez peut-être mettre à niveau vers une version plus récente de l'authentification unique de l'entreprise.