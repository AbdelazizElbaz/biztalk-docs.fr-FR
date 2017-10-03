---
title: "Single Sign-On : Événement 10848 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61888420-29a6-4c64-a884-1b074b586f21
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9511d46a43180626a31f36c9f887b0ac532e088a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10848"></a>Single Sign-On : Événement 10848
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10848|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|ENTSSO_E_DIRECT_SYNC_NOT_ALLOWED_AMBIGUOUS|  
|Texte du message|La synchronisation des mots de passe n'est pas autorisée pour cette application car ses champs sont ambigus.|  
  
## <a name="explanation"></a>Explication  
 S'il y a plus de deux champs, un seul doit être marqué pour la synchronisation des mots de passe.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour remédier à cette situation, vous devez supprimer l'application et la recréer afin qu'elle soit conforme à ces instructions.