---
title: "Liste de vérification : Effectuer des vérifications de performances mensuel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa103777-af4d-480d-abc7-3c4718f493c1
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3c1c84248fc3f5a7efdcc7e4df3f62b23bfcc82
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-performing-monthly-performance-checks"></a>Liste de vérification : Effectuer des vérifications de performances mensuel
Cette rubrique répertorie les meilleures pratiques à suivre sur une base mensuelle afin d’éviter les problèmes de performances avec un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] système.  
  
|Étapes|Référence|  
|-----------|---------------|  
|Déterminer les informations que vous devez suivre lors de la planification|Vous devriez décider au cours des étapes de planification de quelles informations doivent faire l'objet d'un suivi, de sorte qu'après avoir déployé le projet, vous puissiez définir les options de suivi et limiter le volume de données suivies afin de n'obtenir que les informations dont vous avez besoin. **Remarque :** pour plus d’informations sur les meilleures pratiques relatives au suivi, consultez [planification pour le suivi](../technical-guides/planning-for-tracking.md) dans ce guide et [suivi des activités et](http://go.microsoft.com/fwlink/?LinkId=154187) (http://go.microsoft.com/fwlink/ ? LinkId = 154187) dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.|  
|Ne suivez pas tous les messages|Nous vous recommandons de pas suivre tous les messages, car chaque fois qu’un message est couvertes, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] effectue une autre copie. Vous pouvez limiter à la place de la portée en effectuant le suivi d’un port spécifique uniquement. Cela permet d’optimiser les performances de votre système et de conserver les bases de données ne soit pas encombré.|  
|Ne suivez pas tous les événements pour les orchestrations|Le suivi de tous les événements d’une orchestration peut augmenter la taille des tables dta_DebugTrace et dta_MessageInoutEvents. Pour obtenir des instructions sur la manière de désactiver le suivi d’une orchestration, consultez [pour désactiver le suivi d’une orchestration](../technical-guides/how-to-disable-tracking.md#BKMK_DisableOrchTracking).|  
|Définition du suivi sur les ports d’envoi et ports au lieu d’un pipeline de réception|Si vous définissez des options de suivi sur les pipelines, vous allez également définir les options de suivi global pour tous les ports qui utilise le pipeline. Cela peut à son tour entraîner beaucoup plus de données en cours de suivi que vous avez l’intention, qui ralentit les performances du système. Au lieu de cela, vous pouvez définir les options de suivi de l’envoi de ports et les ports de réception.|  
|Ajuster la limitation basée sur l’utilisation des ressources|La limitation dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est configuré par défaut pour fournir une protection intégrée satisfaisante du système. Surveiller les compteurs de performances pour la limitation des États pour voir si la limitation est en cours, puis évaluez si la ressource sur laquelle la limitation est basée (par exemple, la base de données d’utilisation de taille ou de la mémoire) est sous ou surutilisées et ensuite ajuster la limitation seuils au-dessus ou au-dessous. Pour plus d’informations, consultez [ajuster les seuils de limitation : quand et pourquoi](http://go.microsoft.com/fwlink/?LinkId=154188) (http://go.microsoft.com/fwlink/?LinkId=154188).|  
|Utilisez le pipeline PassThruTransmit si possible|Si aucun traitement de document n’est requis avant d’envoyer un message vers sa destination, utilisez le pipeline PassThruTransmit au lieu du pipeline d’envoi XML.|  
|Prendre en compte différents facteurs dès que la taille de la base de données des suivis BizTalk|-Lors du redimensionnement de la base de données des suivis BizTalk, compte des facteurs de SQL Server, tels que la taille de l’index, en ajoutant un multiplicateur d’urgence pour vos calculs.<br />-Lors de la détermination de la taille des messages dans la base de données des suivis BizTalk, ajoutez la taille moyenne du contexte de message à la taille de message s’il est important par rapport à la taille du message.<br />-Pour limiter la taille des messages dans la base de données des suivis BizTalk, limitez le nombre de propriétés que vous promouvez.<br />-Si l’option du débogueur d’orchestration est activée, prendre en compte l’état de chaque forme de l’orchestration est enregistré dans la base de données des suivis BizTalk.|  
|Appliquez les solutions matérielles pour éviter la contention de disque|Pour éviter la contention de disque dans la base de données MessageBox, procédez comme suit :<br /><br /> -Utilisez les disques à grande vitesse<br />-Déployer les bases de données sur un réseau SAN à grande vitesse<br />-Séparer la base de données MessageBox sur un serveur dédié qui est distinct des bases de données de suivi<br />-Mise à l’échelle des unités centrales et ajouter plus de processeurs sur le serveur de base de données MessageBox dédié<br />-Permet de déplacer le journal du fichier d’échange et/ou de MSDTC sur un lecteur distinct<br /><br /> Pour plus d’informations sur la prévention des conflits de base de données, consultez [comment éviter la Contention de disque](http://go.microsoft.com/fwlink/?LinkId=158809) (http://go.microsoft.com/fwlink/?LinkId=158809).|  
  
## <a name="see-also"></a>Voir aussi  
 [Listes de contrôle de routine de performances](../technical-guides/routine-performance-checklists.md)   
 [Liste de vérification : Effectuer des vérifications de performances hebdomadaire](../technical-guides/checklist-performing-weekly-performance-checks.md)