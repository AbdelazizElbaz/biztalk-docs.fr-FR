---
title: "Single Sign-On : Événement 10759 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5347f3d6-d31a-4c00-a64c-c0b0f680de88
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81ff42b71499df5848a55848b3dc1067adb830bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10759"></a>Single Sign-On : Événement 10759
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10759|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|ENTSSO_E_BACKUP_RESTORE_FAILED_MEDIA|  
|Texte du message|Le fichier spécifié pour la sauvegarde ou la restauration des secrets principaux doit figurer dans un système de fichiers NTFS ou sur un média amovible.|  
  
## <a name="explanation"></a>Explication  
 Seuls les systèmes de fichiers NTFS ou un média amovible peuvent être sécurisés.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Utilisez un système de fichiers NTFS ou un média amovible pour sauvegarder le secret principal.