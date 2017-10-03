---
title: Configuration de la programmation carte | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e5fef6c-6928-42e7-9a1f-42b5bd769937
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e908b3ac79970b917e1e7964868b3b9d5bd852d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-programming-configuration"></a>Configuration de programmation de carte
Chaque type d'adaptateur de synchronisation de mot de passe exige une configuration différente, selon le système non-Windows pour lequel vous concevez l'adaptateur. À l'instar des applications associées, vous pouvez utiliser le magasin de configuration du service d'authentification unique de l’entreprise pour stocker les propriétés de configuration de manière centralisée et plus sécurisée.  
  
 Comme il le ferait avec d'autres applications de stockage de configuration, un administrateur peut utiliser l'interface utilisateur de gestion de l'authentification unique de l'entreprise pour localiser et lire un fichier XML décrivant les propriétés de configuration de votre adaptateur. Les outils de gestion utilisent le fichier XML pour obtenir une page de propriétés réunissant les valeurs de propriété nécessaires, pour l’adaptateur spécifié. Vous pouvez également utiliser ISSOConfigStore pour charger et lire des combinaisons valeur/nom XML depuis et vers le magasin de configuration, ou encore l'outil SSOPS.  
  
 Vous pouvez enfin utiliser les outils d’authentification unique de l’entreprise pour activer et désactiver un adaptateur. Lors de la création initiale, un adaptateur est désactivé.  
  
## <a name="see-also"></a>Voir aussi  
 [Adaptateurs de synchronisation de mot de passe](../core/password-sync-adapters.md)