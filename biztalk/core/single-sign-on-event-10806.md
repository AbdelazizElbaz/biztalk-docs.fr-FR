---
title: "Single Sign-On : Événement 10806 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23650d6b-b6a4-4c41-96cd-476e5b0f7f63
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd3f432a408cffcbd1ccd27508550fd0888c5213
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10806"></a>Single Sign-On : Événement 10806
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10806|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|ENTSSO_E_APP_ASSIGNED_TO_ADAPTER|  
|Texte du message|L'application ne peut pas être supprimée car elle est actuellement affectée à un adaptateur.|  
  
## <a name="explanation"></a>Explication  
 Une application ne peut pas être supprimée lorsqu'elle est affectée à un adaptateur.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Supprimez l'affectation de l'application à l'adaptateur, puis supprimez l'adaptateur.