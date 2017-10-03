---
title: "Single Sign-On : Événement 10855 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba244f8e-bc61-475f-913c-475ebf1c69ee
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89bbdb3c004dc7533be9b7f6371ec69b67bde532
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10855"></a>Single Sign-On : Événement 10855
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10855|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|ENTSSO_E_PASSWORD_FILTER_FAILED|  
|Texte du message|Les informations d'identification ne peuvent pas être renvoyées car le filtre de mots de passe a échoué.|  
  
## <a name="explanation"></a>Explication  
 Le filtre de mots de passe n'est pas valide. La cause la plus probable est que le filtre a été créé manuellement, ce qui n'est pas recommandé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Recréez le filtre de mots de passe par l'intermédiaire de l'Assistant Créer un filtre.