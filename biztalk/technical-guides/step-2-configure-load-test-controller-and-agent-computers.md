---
title: "Étape 2 : Configurer le contrôleur de Test de charge et les ordinateurs agents | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9d937ac-55d8-48fa-bba2-3efe151587b8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f931a05796856816e19b53ff5cba9f53b48c3e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-configure-load-test-controller-and-agent-computers"></a>Étape 2 : Configurer le contrôleur de Test de charge et les ordinateurs de l’Agent
Édition de Visual Studio 2010 Ultimate peut générer une charge simulant jusqu'à 250 utilisateurs virtuels sur une série de tests de charge locale. Pour simuler plus de 250 utilisateurs virtuels et/ou pour lancer le test à une distance ordinateur nécessite Visual Studio Load Test Virtual User Pack 2010.  
  
 Tous les tests de charge effectuées dans ce guide a été lancé à partir de deux ordinateurs :  
  
-   Un ordinateur exécutant en tant qu’un contrôleur de Test de charge et un Agent de Test de charge.  
  
-   Un autre ordinateur en cours d’exécution en tant qu’un Agent de Test de charge uniquement.  
  
 Résultats des tests ont été stockés dans un référentiel de résultats des tests de charge à distance dans une base de données SQL Server 2008 R2.  
  
 Pour plus d’informations sur l’utilisation de contrôleurs de test et agents de test pour distribuer des tests de charge sur plusieurs ordinateurs de test, consultez [distribution charger les Tests sur plusieurs Test Machines à l’aide de contrôleurs de Test et Agents de Test](http://go.microsoft.com/fwlink/?LinkId=208406) (http:// go.Microsoft.com/fwlink/ ? LinkId = 208406).  
  
## <a name="install-and-configure-the-load-test-controller-and-load-test-agents"></a>Installer et configurer la charge de contrôleur de Test et de la charge des Agents de Test  
 Pour installer et configurer le contrôleur de test de charge et des agents de test de charge, consultez les sections suivantes dans la rubrique [installation et configuration des Agents Visual Studio et de Test et les contrôleurs de Build](http://go.microsoft.com/fwlink/?LinkId=208455) (http://go.microsoft.com/fwlink/?LinkId=208455) :  
  
-   Pour configurer un contrôleur de test, suivez les procédures décrites dans le [installer un contrôleur de Test](http://go.microsoft.com/fwlink/?LinkId=208454) (http://go.microsoft.com/fwlink/?LinkId=208454) section.  
  
-   Pour configurer les agents de test, suivez les procédures décrites dans le [installer un Agent de Test](http://go.microsoft.com/fwlink/?LinkId=208456) (http://go.microsoft.com/fwlink/?LinkId=208456) section.