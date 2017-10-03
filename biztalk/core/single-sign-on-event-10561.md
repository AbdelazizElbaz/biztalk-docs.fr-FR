---
title: "Single Sign-On : Événement 10561 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 770e6fc1-0854-4555-8f2a-5f199e3aaca7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5148633c7fffabe0ef4bb4789fe4ded58336c10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10561"></a>Single Sign-On : Événement 10561
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10561|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_ERROR_BACKUP_FAILED_MEDIA|  
|Texte du message|Le fichier spécifié pour la sauvegarde des secrets principaux doit figurer dans un système de fichiers NTFS ou sur un média amovible.%r<br /><br /> Nom du fichier : %1 %r<br /><br /> L’utilisateur client : %2 %r<br /><br /> Ordinateur client : %3 %r<br /><br /> Code d’erreur : %4|  
  
## <a name="explanation"></a>Explication  
 Une tentative de sauvegarde a été effectuée à l'aide d'un média non valide, tel qu'un fichier FAT. Le fichier spécifié pour la sauvegarde des secrets principaux doit figurer dans un système de fichiers NTFS ou sur un média amovible.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez le format du média et assurez-vous qu'il s'agit d'un système de fichiers NTFS ou d'un média amovible.