---
title: "Single Sign-On : Événement 10560 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8677a807-2973-4753-8816-c93c45697d92
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d630dccdd21aaade843d4aa8fd7026d05fd71da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10560"></a>Single Sign-On : Événement 10560
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10560|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_ERROR_BACKUP_SECRET_FAILED|  
|Texte du message|Échec lors de la sauvegarde des secrets principaux.%r<br /><br /> Nom du fichier : %1 %r<br /><br /> MSID actuel : %2 %r<br /><br /> MSID précédent : %3 %r<br /><br /> L’utilisateur client : %4 %r<br /><br /> Code d’erreur : %5|  
  
## <a name="explanation"></a>Explication  
 Une tentative de sauvegarde du secret principal a échoué. Il se peut que l'utilisateur à l'origine de la tentative de sauvegarde dispose d'autorisations, d'un chemin d'accès ou d'un répertoire incorrects.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour plus d’informations sur la sauvegarde du secret, consultez [gestion du Secret](../core/managing-the-master-secret.md).