---
title: "Résolution des problèmes de latence de MessageBox | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9eb5789-80bd-40d4-8c27-7ae117fd9232
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e37fc970230bf218bcfd820611fb6b87322e535
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-messagebox-latency-issues"></a>Résolution des problèmes de latence de MessageBox
Dans un monde parfait, tous les messages seraient traités et remis dès qu'ils seraient publiés dans la base de données MessageBox. Par ailleurs, cette dernière ne deviendrait jamais trop volumineuse. Tous les messages de la MessageBox n'étant plus référencés seraient immédiatement supprimés par les travaux de l'agent SQL qui nettoient régulièrement les tables de cette base de données.  
  
 Dans la réalité, cependant, les messages ne sont généralement pas reçus de façon prévisible et linéaire, et les travaux de l'agent SQL ont besoin de temps pour nettoyer les tables de la base de données MessageBox.  
  
 Par conséquent, dans certains cas, la MessageBox peut grossir très rapidement.  
  
 Les éléments ci-dessous peuvent entraîner un accroissement excessif de la MessageBox et détériorer les performances générales :  
  
-   **Arrêt de l’instance d’hôte Biztalk qui a la valeur d’option « Autoriser le suivi de l’hôte »**. C'est l'hôte qui est chargé de déplacer les données de suivi de la base de données MessageBox vers la base de données des suivis BizTalk (BizTalkDTADb).  
  
-   **L’Agent SQL Server n’est pas en cours d’exécution** cela peut se produire si les travaux SQL chargés de déplacement des données à partir de la base de données MessageBox vers la base de données BizTalkDTADb [puis de purger les données déplacées dans la MessageBox] ne sont pas en cours d’exécution. Pour éviter ce problème, le service de l'Agent SQL doit impérativement fonctionner tout le temps.  
  
-   **Travaux de SQL Server sont désactivés** même si l’Agent SQL Server est en cours d’exécution, il est impératif qu’aucun des travaux de SQL Server par défaut désactivé.  
  
-   **Base de données BizTalkDTADb augmente excessivement** cela peut se produire si la base de données BizTalkDTADb devient très volumineuse, à l’origine des insertions dans la base de données BizTalkDTADb prend plus de temps. Dans ce cas, le déplacement des données par le service TDDS (Tracking Data Delivery Service) ralentit, ce qui génère une accumulation des travaux en retard dans la base de données MessageBox. Pour éviter ce problème, il est essentiel d'exécuter régulièrement les travaux de purge et d'archivage du serveur SQL sur les bases de données BizTalkDTADb.  
  
-   **Une latence d’e/s disque excessive** si la vitesse d’entrée de données dans la base de données MessageBox est plus rapide que le système peut traiter et déplacer les données vers la base de données BizTalkDTADb, file d’attente peut s’accumuler dans la base de données MessageBox. Si cette accumulation se poursuit, le problème s'aggrave et les performances du système se dégradent peu à peu. Pour résoudre ce problème, vous pouvez installer des disques plus rapides et/ou mettre à niveau le matériel afin que le système puisse se remettre des éventuels messages accumulés avec le temps.  
  
## <a name="plan-for-the-future"></a>Prévoir l'avenir  
 Même si toutes les recommandations ci-dessus sont respectées, avec le temps, le volume des données de suivi déplacées vers la base de données BizTalkDTADb devient très important. Il est donc indispensable d'implémenter un plan de maintenance de cette base de données de façon à archiver régulièrement les données de suivi afin que le système présente toujours des performances optimales.  
  
 La quantité de données historiques pouvant être conservées dans la base de données BizTalkDTADb dépend du volume des messages transmis au sein du système. Dans les systèmes non soumis à un débit et un stress élevés, cette base de données grossit à un rythme plus lent et peut contenir plus de données historiques.  
  
 Il est recommandé de conserver un nombre de données minimal dans la base de données BizTalkDTADb afin de ne pas nuire aux performances du moteur d'exécution.