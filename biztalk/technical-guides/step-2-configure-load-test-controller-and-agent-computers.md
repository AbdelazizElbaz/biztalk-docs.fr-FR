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
ms.openlocfilehash: 75a659d533b68cf525bcd782a2dadce72a6ebb0b
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="step-2-configure-load-test-controller-and-agent-computers"></a>Étape 2 : Configurer le contrôleur de Test de charge et les ordinateurs de l’Agent

## <a name="overview"></a>Vue d'ensemble
Visual Studio peut générer une charge simulant jusqu'à 250 utilisateurs virtuels sur une série de tests de charge locale. Pour simuler plus de 250 utilisateurs virtuels et/ou pour lancer le test à une distance ordinateur nécessite Visual Studio charge virtuel utilisateur de Test.  
  
 Tous les tests de charge effectuées dans ce guide a été lancé à partir de deux ordinateurs :  
  
-   Un ordinateur exécutant en tant qu’un contrôleur de Test de charge et un Agent de Test de charge.  
  
-   Un autre ordinateur en cours d’exécution en tant qu’un Agent de Test de charge uniquement.  
  
 Résultats des tests ont été stockés dans un référentiel de résultats des tests de charge à distance dans une base de données SQL Server.  
  
 Pour plus d’informations sur l’utilisation de contrôleurs de test et agents de test pour distribuer des tests de charge sur plusieurs ordinateurs de test, consultez [distribution charger les Tests sur plusieurs Test Machines à l’aide de contrôleurs de Test et Agents de Test](https://msdn.microsoft.com/library/dd728093.aspx).  
  
## <a name="install-and-configure-the-load-test-controller-and-load-test-agents"></a>Installer et configurer la charge de contrôleur de Test et de la charge des Agents de Test  
 Pour installer et configurer le contrôleur de test de charge et des agents de test de charge, consultez [installer et configurer les agents de test](https://docs.microsoft.com/visualstudio/test/lab-management/install-configure-test-agents).
