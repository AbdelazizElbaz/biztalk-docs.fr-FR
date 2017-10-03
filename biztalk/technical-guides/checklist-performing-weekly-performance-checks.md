---
title: "Liste de vérification : Effectuer des vérifications de performances hebdomadaire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c36fe78d-1be8-49f2-97ce-b6d0cadffab8
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7898702e42253ab1155b0a6e32af3008800db1f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-performing-weekly-performance-checks"></a>Liste de vérification : Effectuer des vérifications de performances hebdomadaire
Cette rubrique répertorie les meilleures pratiques à suivre sur une base hebdomadaire lorsque afin d’éviter les performances des problèmes avec un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] système.  
  
|Étapes|Référence|  
|-----------|---------------|  
|Définir la croissance automatique de la base de données à un nombre fixe|-Base de données de la croissance automatique doit être définie sur un nombre fixe de mégaoctets et non un pourcentage, en particulier pour les bases de données MessageBox et de suivi (DTA). Selon votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application et de débit, de la MessageBox et de bases de données de suivi peuvent devenir très volumineux. Si la croissance automatique est définie sur un pourcentage, la croissance automatique peut également être substantielle.<br />-Si le système est nouveau et les tailles statiques n’ont pas été établies définitivement, puis configurez les fichiers avec l’option Activer la croissance automatique et spécifier la croissance des fichiers en mégaoctets. L’incrément de croissance doit généralement pas être supérieur à 100 Mo (pour les fichiers volumineux), 10 Mo (pour les fichiers de taille moyenne) ou 1 Mo (pour les petits fichiers). Consultez le **annexe B : Configuration de base de données recommandé de BizTalk Server** section de la [livre blanc de l’optimisation de base de données BizTalk Server](http://go.microsoft.com/fwlink/p/?LinkID=153594) (http://go.microsoft.com/fwlink/p/? LinkID = 153594) pour une table avec des tailles de fichiers suggérée pour chacun de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données.|  
|Limiter les événements que vous surveillez avec SQL Server Profiler|Utiliser SQL Server Profiler pour surveiller uniquement les événements qui vous intéressent. Si les traces deviennent trop volumineux, vous pouvez filtrer en fonction des informations que vous le souhaitez, afin que seul un sous-ensemble des données d’événement est collecté. La surveillance d'un trop grand nombre d'événements s'ajoute à la charge du serveur et du processus de surveillance, et peut considérablement accroître la taille du fichier ou de la table de trace, en particulier si le processus de surveillance se prolonge sur une période importante.|  
|Configurer le traitement par lots du message pour augmenter les performances de l’adaptateur|-Réduire le nombre de transactions effectuées par un adaptateur en combinant plusieurs opérations dans un lot unique.<br />-Limiter la taille de lot en fonction du nombre total d’octets dans le lot, en plus du nombre de messages. Pour plus d’informations sur la limitation de la taille de lot, consultez [configurer le traitement par lot pour améliorer les performances de l’adaptateur](../technical-guides/configuring-batching-to-improve-adapter-performance.md).|  
|Ajustez le seuil de messages volumineux|Pour améliorer le débit, augmentez le seuil de messages volumineux, ce qui réduit le nombre de messages volumineux qui sont en mémoire tampon sur le disque lors du mappage.|  
|Examiner les fuites de mémoire ou des exceptions de mémoire insuffisante dans le processus de BizTalk Server|Fuites de mémoire dans les processus BizTalk peuvent se produire en raison d’une raisons diverses. Consultez 918643 de l’Article de Base de connaissances Microsoft, [comment résoudre les problèmes d’une fuite de mémoire ou une exception de mémoire insuffisante dans le processus de BizTalk Server](http://go.microsoft.com/fwlink/p/?LinkId=157212) (http://go.microsoft.com/fwlink/p/? LinkId = 157212) pour plus d’informations sur les scénarios dans lesquels une fuite de mémoire peut se produire et comment la corriger.|  
  
## <a name="see-also"></a>Voir aussi  
 [Listes de contrôle de routine de performances](../technical-guides/routine-performance-checklists.md)   
 [Liste de vérification : Effectuer des vérifications de performances mensuel](../technical-guides/checklist-performing-monthly-performance-checks.md)