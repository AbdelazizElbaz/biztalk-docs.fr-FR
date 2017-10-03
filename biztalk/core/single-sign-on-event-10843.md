---
title: "Single Sign-On : Événement 10843 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 847e464e-5733-4703-905f-d44a4c4f5cc3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd86a39d515858e1cda09317ba6139bc67c95ed4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10843"></a>Single Sign-On : Événement 10843
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10843|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|ENTSSO_E_NO_SECRET2|  
|Texte du message|Impossible d'effectuer le chiffrement ou le déchiffrement car le secret n'est pas disponible depuis le serveur de secret principal. Recherchez les erreurs associées dans le journal des événements (sur l'ordinateur « %1 »).|  
  
## <a name="explanation"></a>Explication  
 Accès refusé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Le serveur de secret principal est hors ligne ou n'inclut pas le secret principal requis. Recherchez les erreurs associées dans le journal des événements sur l'ordinateur spécifié.