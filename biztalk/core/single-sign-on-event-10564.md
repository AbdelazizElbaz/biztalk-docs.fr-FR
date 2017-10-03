---
title: "Single Sign-On : Événement 10564 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e523c97a-608e-4bf4-8747-cfa0cce10acf
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7268b877a59fcd4e993a2c9009d48d73e5db9ac8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10564"></a>Single Sign-On : Événement 10564
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10564|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_ERROR_BACKUP_FILE_INCORRECT_FORMAT|  
|Texte du message|Le format du fichier de sauvegarde est incorrect.|  
  
## <a name="explanation"></a>Explication  
 Le format du fichier de sauvegarde est incorrect.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez qu'il s'agit du bon fichier et qu'il figure au bon emplacement. Vous devez également confirmer qu'aucun autre fichier de ce dossier ne comporte l'extension .BAK, car le système ENTSSO risquerait de les confondre avec le fichier de sauvegarde actuel.