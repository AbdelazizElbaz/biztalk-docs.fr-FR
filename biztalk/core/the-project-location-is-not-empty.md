---
title: "L’emplacement du projet n’est pas vide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db353050-3662-4ab6-8898-4e4d3bd78ac1
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2de1e1dd381a75f596b4980430ddcc5d6d8982b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-project-location-is-not-empty"></a>L'emplacement du projet n'est pas vide
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|L'emplacement du projet « {0} » n'est pas vide. Vous devez effectuer l’une des opérations suivantes : 1. Choisissez un autre emplacement pour le nouveau projet, 2. Spécifiez remplacer pour réutiliser l’emplacement existant, ou 3. Supprimez manuellement le contenu de l’emplacement du projet.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que le répertoire virtuel vers lequel vous tentez de publier le service n'est pas vide.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Utilisez l'emplacement existant en effectuant un remplacement. Vous pouvez également spécifier un nouvel emplacement.  Dans l’Assistant Publication de services WCF, sélectionnez **remplacer l’emplacement existant** et cliquez sur **suivant**. Cette opération remplace l'emplacement.