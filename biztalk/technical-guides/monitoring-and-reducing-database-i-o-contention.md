---
title: "Analyse et de réduire les contentions d’e/s de base de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd6d3343-3fa3-469a-9772-e94f22fdf558
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 446a4b512b4f38869637cb3968305fad1e869dae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-and-reducing-database-io-contention"></a>Surveillance et réduire la Contention d’e/s de la base de données
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]performances sont souvent basée sur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] performances, ce qui à son tour, sont souvent basée sur les performances d’e/s disque. Par conséquent, vous devez surveiller et régler les performances d’e/s de disque sur les ordinateurs exécutant [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cette maison le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données.  
  
## <a name="monitoring-disk-io"></a>Surveillance des e/s disque  
 En raison de la base de données intensif de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], e/s disque peut facilement devenir un goulot d’étranglement sur la MessageBox et BizTalk, le suivi des bases de données ; cela est vrai même si les e/s disque n’a pas été précédemment un goulot d’étranglement pour les fichiers de base de données dans votre [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] environnement. Par conséquent, nous vous recommandons de proactive mesurer les performances d’e/s disque pour les disques qui hébergent les fichiers journaux de transaction et de données. Pour plus d’informations sur l’analyse des performances d’e/s disque à l’aide du Moniteur système, consultez le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] article [« Prédéploiement d’e/s meilleures pratiques »](http://go.microsoft.com/fwlink/?LinkId=104829) (http://go.microsoft.com/fwlink/?LinkId=104829). Si vous utilisez un réseau SAN, vous devrez peut-être également des outils spécifiques du fabricant du matériel de réseau SAN pour mesurer les performances d’e/s disque.  
  
## <a name="separating-the-messagebox-and-biztalk-tracking-dta-databases-and-log-files"></a>Séparation de la MessageBox et les bases de données (DTA) et les fichiers journaux de suivi de BizTalk  
 Étant donné que les bases de données MessageBox et des suivis BizTalk sont les plus actifs, nous vous recommandons de placer les fichiers de données et les fichiers journaux des transactions pour chacun d’eux sur des lecteurs dédiés pour réduire le risque de problèmes de contention d’e/s de disque. Par exemple, vous avez besoin des quatre disques pour les fichiers de base de données MessageBox et des suivis BizTalk ; un lecteur pour chacun des éléments suivants :  
  
-   Fichiers de données MessageBox  
  
-   Fichiers journaux des transactions MessageBox  
  
-   Fichiers de données des suivis BizTalk  
  
-   Fichiers journaux des transactions des suivis BizTalk  
  
 Séparer les bases de données MessageBox et des suivis BizTalk et en séparant les fichiers de base de données et les fichiers journaux des transactions sur des disques différents sont considérés comme des meilleures pratiques pour réduire la contention d’e/s disque. Essayez afin de répartir l’e/s disque piles de disques physiques autant que possible. Pour plus d’informations sur la prévention de contention de disque, consultez [comment éviter la Contention de disque](http://go.microsoft.com/fwlink/?LinkId=158809) (http://go.microsoft.com/fwlink/?LinkId=158809) dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Guide d’optimisation des performances.  
  
 Vous devez séparer les fichiers manuellement après la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez la [livre blanc de l’optimisation de base de données BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=101578) (http://go.microsoft.com/fwlink/?LinkId=101578).  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’analyse des performances de l’outil de journaux (PAL)](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)