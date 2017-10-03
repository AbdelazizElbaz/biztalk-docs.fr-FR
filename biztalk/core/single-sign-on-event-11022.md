---
title: "Single Sign-On : Événement 11022 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c65ca12b-dda8-408b-9512-39df6f8e035b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ccae36e9beef672e6c5fb7917c88341ce4bb3c08
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11022"></a>Single Sign-On : Événement 11022
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11022|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_EXTERNAL_TO_EXTERNAL_MAPPING_CONFLICT_NOT_ALLOWED|  
|Texte du message|Un changement de mot de passe externe aurait entraîné la modification d'un compte externe différent.%r<br /><br /> Cela ne s'est pas produit, car la carte pour ce système externe est configurée de sorte à ne pas autoriser les conflits de mappage.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Carte : %2 %r<br /><br /> Compte Windows : %3 %r<br /><br /> Compte externe 1 : %4 %r<br /><br /> Compte externe 2 : %5|  
  
## <a name="explanation"></a>Explication  
 Il s'agit d'un message informatif indiquant l'échec du changement de mot de passe externe qui aurait entraîné la modification d'un compte externe différent.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Bien qu'aucun changement n'ait été effectué (car ce système est configuré afin de ne pas autoriser les conflits de mappage), vous devez confirmer immédiatement que cette tentative a été effectuée, sachant que vous en étiez informé et que vous l'avez autorisée. Dans ce cas, aucune action n'est requise. Sinon, déterminez où le changement a été initié et confirmez qu'il s'agissait d'un emplacement sûr au sein du système. 