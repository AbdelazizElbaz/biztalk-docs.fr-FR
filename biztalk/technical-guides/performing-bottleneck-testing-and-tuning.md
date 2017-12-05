---
title: "Exécution de goulot d’étranglement de test et de réglage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95d41d95-3a76-4eb0-b07d-14c6b6dccdaa
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27d2e0ed3c8298287471b60d87b199fcfc800e61
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="performing-bottleneck-testing-and-tuning"></a>Exécution de goulot d’étranglement de test et de réglage
Vous devez effectuer les tests de performances pour déterminer les goulots d’étranglement dans le système et de régler le système en conséquence.  
  
## <a name="testing-a-subsystem"></a>Un sous-système de test  
 Il est une meilleure pratique pour identifier les goulots d’étranglement du système pour exécuter des tests de performances sur des sous-ensembles de l’ensemble du système, par exemple :  
  
-   Établir des paramètres de performances de ligne de base pour les systèmes externes pour envoient ou recevoir des message de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Inscrire les orchestrations, mais ne démarrez pas les. Supprimer les messages dans les emplacements de fichier/files d’attente entrant et permettent le trafic entrant de cartes drainage les file d’attente/fichier des emplacements de réception et de publier des messages dans la base de données MessageBox. Cela vous permet d’isoler votre réception ports afin de déterminer leur taux d’entrée soutenu maximal.  
  
-   Une fois que les messages sont extraits dans la base de données MessageBox, arrêtez les adaptateurs de réception, activer les processus d’orchestration et/ou des adaptateurs, d’envoi, puis mesurer la vitesse sur les orchestrations et/ou envoyer des adaptateurs sont le traitement des messages.  
  
## <a name="testing-the-end-to-end-system"></a>Test du système de bout en bout  
 Test des frais d’entrée et de sortie, comme décrit dans la précédente section d’est un moyen efficace pour isoler les performances du sous-système de l’application, bien qu’il ne décrit pas les performances de bout en bout. Vous devez également tester les performances de bout en bout, car certains d'entre eux ne peut pas être identifié, jusqu'à ce que plusieurs ressources en compétition pour la même ressource partagée (par exemple, la base de données MessageBox).  
  
 Pour générer une charge sur un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement, envisagez d’utiliser l’outil Microsoft BizTalk LoadGen 2007. Télécharger [LoadGen](https://www.microsoft.com/download/details.aspx?id=14925).  
  
 Pour générer et analyser un rapport de performances pour un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement, envisagez d’utiliser l’outil performances analyse des journaux (PAL). Pour plus d’informations sur l’outil de publication, consultez [à l’aide de l’outil performances analyse des journaux (PAL)](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md).  
  
## <a name="what-developers-operators-and-administrators-should-know"></a>Les développeurs, les opérateurs et les administrateurs doivent connaître.  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]les développeurs doivent être familiarisés avec sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des caractéristiques de performances et de paramétrage. Opérateurs et les administrateurs doivent être bien informés sur les aspects de montée en puissance parallèle de la base de données MessageBox, SAN de paramétrage, le paramétrage de réseau et de paramétrage de base de données SQL Server (par exemple, consultez [SQL Server paramètres que ne doivent pas être modifiés](../technical-guides/sql-server-settings-that-should-not-be-changed.md)). Les développeurs, des opérateurs et administrateurs Sachez comment régler [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour haut débit et à faible latence.