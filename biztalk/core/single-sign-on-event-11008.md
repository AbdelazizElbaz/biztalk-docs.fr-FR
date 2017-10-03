---
title: "Single Sign-On : Événement 11008 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7e11dbc-7596-45fa-ae54-a6e79498e60e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88d2dfa2cfb71d66b43cfaa77b24b1dfce70fd7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11008"></a>Single Sign-On : Événement 11008
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11008|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_CHECK_GROUP|  
|Texte du message|Échec de la vérification de l'appartenance à un groupe.%r<br /><br /> Nom du groupe : %1 %r<br /><br /> Nom du compte : %2 %r<br /><br /> Données supplémentaires : %3 %r<br /><br /> Code d’erreur : %4|  
  
## <a name="explanation"></a>Explication  
 Cette erreur est généralement causée par des problèmes réseau, une utilisation entre domaines ou un niveau mixte de contrôleurs de domaine (par exemple, si votre système utilise des contrôleurs de domaine à partir de [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] et [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez avec votre administrateur réseau la présence éventuelle de problèmes réseau, si une utilisation entre domaines est effectuée sur votre système ou s'il existe un niveau mixte de contrôleurs de domaine.