---
title: "Comment tester et déboguer un adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf6563ea-b4ea-4617-b3da-d31250d002ab
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 508f0b5a5ee7b29ed6e2fbde9a94b352d645e550
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-test-and-debug-an-adapter"></a>Test et débogage d'un adaptateur
Le débogage des problèmes d'exécution doit souvent être abordé sous plusieurs angles. Pour déterminer la cause des problèmes ou des bogues logiciels, il est nécessaire de rassembler des données de plusieurs sources telles que le suivi logiciel, les compteurs de performance, les entrées de journal d'événements, les événements WMI (Windows Management Instrumentation) et le code source de débogage.  
  
 Les adaptateurs de réception et d'envoi étant exécutés dans l'espace d'adressage du service BizTalk, le débogueur doit être associé au processus BtsNtSvc.exe pour pouvoir déboguer un adaptateur. Par contre, pour les adaptateurs de réception isolés, le débogueur doit être associé au processus qui les héberge.  
  
 Le code d'exécution de l'adaptateur doit idéalement être instrumenté avec un code de suivi pour pouvoir capturer des diagnostics d'exécution en vue du dépannage. Vous pouvez réaliser cette instrumentation à l'aide de Microsoft Enterprise Instrumentation Framework (EIF). Il est généralement utile d'ajouter des instructions de suivi à chaque niveau de gravité. Par exemple, suivi pour les conditions d'erreur uniquement, suivi pour les erreurs et les avertissements ou suivi pour les erreurs, les avertissements et les instructions d'information. Par ailleurs, les adaptateurs plus complexes comportent parfois des sous-systèmes séparés dont le suivi doit être effectué de manière isolée. Un adaptateur peut en effet avoir un sous-sous-système de réseau et un sous-système principal. L'activation du suivi pour tous les sous-systèmes est susceptible de générer une quantité excessive de « bruit » dans certains cas de figure.  
  
 Des compteurs de performance doivent être ajoutés pour capturer les taux et valeurs au moment de l'exécution et donner davantage d'informations au sujet du comportement de l'adaptateur durant l'exécution. Par exemple, un adaptateur pourra publier des compteurs de performance pour les nombres bruts des messages envoyés terminaison par terminaison ainsi que pour le nombre de messages envoyés par seconde.  
  
 Les événements WMI peuvent aussi s'avérer utiles pour certains scénarios d'erreurs critiques.  Par exemple, si un adaptateur rencontre une erreur critique qui l'amène à fermer un emplacement de réception, le déclenchement d'un événement WMI permet à un administrateur d'écouter cet événement et de prendre les mesures nécessaires.  
  
## <a name="adapter-testing"></a>Test des adaptateurs  
 Lorsque vous développez un adaptateur personnalisé pour BizTalk Server, rappelez-vous qu'il doit avoir la qualité logicielle de l'entreprise. Cela signifie que vous devez le tester de manière approfondie avant de le livrer. Cette section donne une bonne idée de ce qu'il faut faire pour tester des adaptateurs, sans entrer dans tous les détails. En règle générale le test de code d’exécution tels que des cartes doit couvrir les trois grandes catégories : test fonctionnel, test de stress et test des performances.  
  
### <a name="function-testing"></a>Test fonctionnel  
 L'adaptateur doit être testé pour toutes les permutations de sa fonctionnalité et doit être soumis à des tests aussi bien positifs que négatifs. Les tests positifs devront porter entre autres sur les cas de figure suivants :  
  
-   recevoir un ou des messages ;  
  
-   transmettre un ou des messages ;  
  
-   transmettre un message à l'aide d'un port dynamique ;  
  
-   désactiver des emplacements de réception ;  
  
-   mettre à jour la configuration ;  
  
-   garantir que les fenêtre du service fonctionnent pour les adaptateurs de réception et d'envoi ;  
  
-   garantir l'intégrité transactionnelle des adaptateurs traités.  
  
 Les tests négatifs devront porter entre autres sur les cas de figure suivants :  
  
-   recevoir un ou des messages incorrects ;  
  
-   recevoir un lot mixte de messages corrects et incorrects ;  
  
-   transmettre une erreur ;  
  
-   faire une nouvelle tentative en cas de réussite ;  
  
-   faire une nouvelle tentative en cas d'échec, passer au prochain transport réussi ;  
  
-   passer au prochain échec de transport, interrompre le message ;  
  
-   transmettre un lot mixte de messages ;  
  
-   basculement de base de données.  
  
### <a name="stress-testing"></a>Test de stress  
 En tant que composants d'exécution, les adaptateurs doivent satisfaire aux exigences rigoureuses des logiciels d'exécution. Généralement, le test de stress consiste à mettre en œuvre des scénarios en condition de charge sur une certaine durée. Entre les tests d'échec, des intervalles de stress élevé et de faible stress devront par ailleurs être testés pendant que l'adaptateur sera exécuté en condition de charge sur une durée déterminée.  
  
 Pour conduire ces tests, il sera notamment judicieux d'exécuter l'adaptateur sous un stress élevé pendant environ 72 heures, quand le nombre des messages qui transitent par l'adaptateur entraîne une utilisation de l'UC de 80 à 90 pour cent. Sous faible stress, l'utilisation de l'UC devrait être de 30 à 40 pour cent pendant 120 heures.  
  
### <a name="performance-testing"></a>Test de performances  
 Les performances sont un aspect incontournable du développement des adaptateurs. Avant de sortir un adaptateur, veillez donc à valider ses performances. Il est primordial qu'elles évoluent verticalement et horizontalement. Autrement dit, l'ajout d'UC a pour conséquence une augmentation des performances, au même titre que l'ajout d'ordinateurs. Profiler le code peut faciliter l'élimination des goulots d'étranglement liés aux performances.