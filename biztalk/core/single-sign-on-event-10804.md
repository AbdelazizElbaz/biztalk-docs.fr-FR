---
title: "Single Sign-On : Événement 10804 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4d98bef-fdc3-4627-bb5b-663fa502b965
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b65c59ce736804215cd7c70428905d776d8e0e4b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10804"></a>Single Sign-On : Événement 10804
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10804|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|ENTSSO_E_INCORRECT_COMPUTER|  
|Texte du message|Cet adaptateur n'est pas configuré pour cet ordinateur.|  
  
## <a name="explanation"></a>Explication  
 Chaque adaptateur est configuré pour fonctionner sur un ordinateur spécifique, qui est identifié par son nom long. Soit le nom est incorrect, soit vous tentez de faire fonctionner l'adaptateur sur un autre ordinateur.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Consultez la configuration pour cet adaptateur afin de déterminer le nom adéquat de l'ordinateur approprié.