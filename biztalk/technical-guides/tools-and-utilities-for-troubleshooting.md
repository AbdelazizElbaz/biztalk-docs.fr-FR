---
title: "Outils et utilitaires de dépannage | Documents Microsoft"
ms.custom: 
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56b0946a-56de-47cd-95d9-365722cdbaed
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 086c7144d39b459a342e3c4f6c5c87f669fffedc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tools-and-utilities-for-troubleshooting"></a>Outils et utilitaires de résolution des problèmes
Cette rubrique décrit les divers outils et utilitaires qui peuvent être utiles pour diagnostiquer la cause d’un problème dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] composant ou une dépendance.  
  
|Dépannage|Outil|Utiliser|  
|---------------------|----------|---------|  
|**Dépannage de SQL Server**|Moniteur d’activité SQL|Moniteur d’activité SQL Server 2008 fournit des informations sur les processus SQL Server et la façon dont ces processus affectent l’instance actuelle de SQL Server. Pour plus d’informations sur le moniteur d’activité SQL Server 2008, consultez [moniteur d’activité](http://go.microsoft.com/fwlink/?LinkId=146355) (http://go.microsoft.com/fwlink/?LinkId=146355) dans la documentation de SQL Server. Pour plus d’informations sur la façon d’ouvrir le moniteur d’activité à partir de SQL Server Management Studio, consultez [Comment : ouvrir le moniteur d’activité (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=135094) (http://go.microsoft.com/fwlink/?LinkId=135094) dans la documentation de SQL Server.|  
||Collecte de données SQL Server 2008|SQL Server 2008 fournit un collecteur de données que vous pouvez utiliser pour obtenir et enregistrer les données collectées à partir de plusieurs sources. Le collecteur de données vous permet d’utiliser des conteneurs de collecte de données, qui vous permettent de déterminer l’étendue et la fréquence de collecte de données sur un ordinateur qui exécute SQL Server 2008. Pour plus d’informations sur l’implémentation de collecte de données SQL Server 2008, consultez [collecte des données](http://go.microsoft.com/fwlink/?LinkId=146356) (http://go.microsoft.com/fwlink/?LinkId=146356) dans la documentation de SQL Server.|  
||**Résolution des problèmes liés à la performance**|L’utilitaire Rejournaliser est utilisé pour extraire les compteurs de performances à partir des journaux créés par l’Analyseur de performances et de convertir les données d’autres formats, tels que les fichiers de texte délimité (texte-TSV), les fichiers texte délimité par des virgules (CSV de texte), des fichiers binaires et les bases de données SQL. Ces données peuvent ensuite être analysées et interrogés à l’aide d’autres outils, tels que de l’Analyseur de journal, pour générer des statistiques pour les indicateurs de performance clés (KPI). L’utilitaire Rejournaliser est fourni avec Windows Server 2003 et versions ultérieures.|  
|Outils d’analyse de performances Windows||Outils de performances de Windows sont conçus pour l’analyse d’un large éventail de problèmes de performances, y compris les heures de démarrage d’application, les problèmes de démarrage différé des appels de procédure et d’interruption d’activité (DPC et ISR), la réactivité du système émet, la ressource d’application l’utilisation et les vagues d’interruption. Pour plus d’informations, consultez [centre de développement Windows Performance Analysis](http://go.microsoft.com/fwlink/?LinkId=139763) (http://go.microsoft.com/fwlink/?LinkId=139763).|  
|Pathping||PathPing fournit des informations sur la perte de données à un ou plusieurs sauts de routeur sur le chemin d’un ordinateur hôte cible. Pour ce faire, pathping envoie des paquets de contrôle Message ICMP (Internet Protocol) à chaque routeur situé dans le chemin d’accès. Pathping.exe est disponible avec toutes les versions de Windows depuis Windows 2000 Server.|  
|IOMeter||IOMeter est un outil open source utilisé pour le disque mesure les performances d’e/s. Pour plus d’informations, consultez [IOMeter](http://go.microsoft.com/fwlink/?LinkId=122412) (http://go.microsoft.com/fwlink/?LinkId=122412). **Important :** utilisation de cet outil n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ce programme. L'utilisation de ce programme relève de votre seule responsabilité.|  
|**Résolution des problèmes généraux**|-Observateur d’événements<br />-Moniteur réseau<br />-SQL Server Profiler<br />-Éditeur de requête SQL Server<br />-DTCTester<br />-DTCPing<br />-Console de performances<br />-RegMon<br />-FileMon<br />-Debug outil Diagnostics de la boîte à outils de diagnostic IIS|Consultez [outils et utilitaires à utiliser pour la résolution des problèmes](http://go.microsoft.com/fwlink/?LinkId=154416) (http://go.microsoft.com/fwlink/?LinkId=154416).|  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de test](../technical-guides/tools-for-testing.md)   
 [Liste de vérification : Configuration de BizTalk Server](~/technical-guides/checklist-configuring-biztalk-server.md)