---
title: "Meilleures pratiques pour la récupération d’urgence | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afbb0a57-0d31-4a2f-847c-02b40361c0ed
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e988055205203c5c4bc7a4d9d6e84706414967c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-disaster-recovery"></a>Meilleures pratiques pour la récupération d’urgence
Pour plus d’informations sur les meilleures pratiques pour la récupération d’urgence [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], consultez [meilleures pratiques pour la sauvegarde et restauration](http://go.microsoft.com/fwlink/?LinkId=151391) (http://go.microsoft.com/fwlink/?LinkId=151391) dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
 **Créez une sauvegarde et le plan de restauration**  
  
-   Assurez-vous que votre plan de sauvegarde indique :  
  
    -   l'ordinateur sur lequel de les sauvegardes seront stockées ;  
  
    -   les programmes à utiliser pour sauvegarder votre système ;  
  
    -   les ordinateurs à sauvegarder ;  
  
    -   La planification des sauvegardes ;  
  
    -   l'emplacement hors site où archiver les sauvegardes.  
  
 **Conserver un enregistrement écrit de toutes les modifications apportées à votre système BizTalk Server**  
  
-   Veillez à noter toutes les modifications apportées à votre système, telles que les Service packs, les correctifs et QFE qui ont été appliqués. Cela est essentiel pour obtenir que votre système soit restauré dans l'état le plus proche possible de celui dans lequel il était avant la défaillance matérielle.  
  
 **Implémentez les mesures suivantes pour aider à éviter ou minimiser l’effet d’un incident**  
  
-   Procurez-vous les mises à jour de logiciels et de microprogramme disponibles.  
  
-   Avoir tous les disques de logiciels disponibles.  
  
-   Élaborez un plan pour surveiller les serveurs de façon proactive. Ceci est très important, car les instances d’orchestration sur un hôte défaillant ne peuvent pas être récupérés par un deuxième hôte pendant 10 minutes.  
  
-   Tenez à jour les enregistrements de matériel.  
  
-   Tenez à jour les enregistrements de logiciels.  
  
 **Mettre en œuvre la tolérance de panne de votre organisation au niveau du matériel ou logiciel**  
  
-   L'implémentation de clusters et de RAID (redundant array of independent disks) garantit que votre système puisse surmonter une panne matérielle.  
  
 **Archive le support de sauvegarde sur une base régulière dans un emplacement sécurisé**  
  
-   Planifiez l'archivage de votre support de sauvegarde à intervalles réguliers et conservez les archives en lieu sûr, hors site. Cela vous garantit de disposer d'une sauvegarde disponible quand vous en avez besoin.  
  
 **Vérifier l’intégrité de vos sauvegardes et l’absence d’erreur**  
  
-   Surveillez toutes vos opérations de sauvegarde et veillez à ce qu'elle s'opèrent sans erreurs.  
  
 **Conserver le même matériel de rechange**  
  
-   Matériel identique de rechange disponible permet de garantir que vous pouvez remplacer rapidement matériel défectueux pour être opérationnel et en cours d’exécution plus rapidement.  
  
 **Documentez et testez vos procédures de récupération**  
  
-   Test de la récupération d’urgence doit être effectuée avant d’exécuter jamais votre système de production. Le fait de disposer de plans bien en place et d'effectuer des tests préliminaires garantit que votre personnel informatique puisse récupérer vos systèmes BizTalk Server.  
  
 **Formez votre personnel informatique sur les procédures de récupération d’urgence**  
  
-   Assurez-vous que votre personnel informatique est préparé pour la récupération du système en cas de besoin.  
  
 **Exercez-vous à restaurer à partir d’une sauvegarde dans un environnement de test**  
  
-   Exercez-vous à restaurer le système BizTalk Server dans un environnement de test pour être certain de pouvoir le restaurer dans votre environnement de production en cas de défaillance.  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération d’urgence](../technical-guides/disaster-recovery.md)