---
title: "Optimisation des performances réseau | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6c3985a-48b3-489b-8fe3-3b7bfd0515f9
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8225bd082140ac1347bc99a91ea209f9d79a8bab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-network-performance"></a>Optimisation des performances réseau
Dans un environnement BizTalk Server sur lequel l’ordinateur BizTalk Server est distinct de l’ordinateur SQL Server, chaque message traité par BizTalk Server requiert la communication sur le réseau. Cette communication comprend un trafic considérable entre l’ordinateur BizTalk Server et la base de données BizTalk MessageBox, la base de données de gestion BizTalk, les bases de données BAM et autres bases de données. Dans les scénarios de charge élevée, cette communication peut entraîner un trafic réseau considérable et peut devenir un goulot d’étranglement, en particulier lorsque les paramètres réseau n’ont pas été optimisées, n’est pas suffisant cartes d’interface réseau sont installés ou de bande passante réseau insuffisantes disponible.  
  
 Cette section fournit des recommandations générales pour l’amélioration des performances réseau et décrit plusieurs entrées de Registre qui peuvent être modifiées pour optimiser la pile réseau pour atténuer l’occurrence des goulots d’étranglement sur le réseau.  
  
> [!IMPORTANT]  
>  Certaines recommandations de cette section nécessitent des modifications au Registre Windows. Une utilisation incorrecte de l'Éditeur du Registre peut causer des problèmes vous obligeant à réinstaller votre système d'exploitation. Son utilisation est sous votre entière responsabilité. Pour plus d’informations sur la façon de sauvegarder, restaurer et modifier le Registre, consultez l’article de la Base de connaissances Microsoft [256896, « informations du Registre Windows pour les utilisateurs expérimentés »](http://go.microsoft.com/fwlink/?LinkId=62729) (http://go.microsoft.com/fwlink/?LinkId=62729).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Instructions générales pour améliorer les performances du réseau](../technical-guides/general-guidelines-for-improving-network-performance.md)  
  
-   [Paramètres qui peuvent être modifiées pour améliorer les performances réseau](../technical-guides/settings-that-can-be-modified-to-improve-network-performance.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances](../technical-guides/optimizing-performance.md)