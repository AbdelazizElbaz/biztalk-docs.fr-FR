---
title: Meilleures pratiques pour la sauvegarde et de restauration | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aaf721ba-50ce-4334-b86d-e856b54d3486
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23657dcc843744741d6315b6a8c18ca3d35e1fe4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-backup-and-restore"></a>Méthodes conseillées pour la sauvegarde et la restauration
-   **Créez une sauvegarde et le plan de restauration**  
  
     Assurez-vous que votre plan de sauvegarde indique :  
  
    -   l'ordinateur sur lequel de les sauvegardes seront stockées ;  
  
    -   les programmes à utiliser pour sauvegarder votre système ;  
  
    -   les ordinateurs à sauvegarder ;  
  
    -   La planification des sauvegardes ;  
  
    -   l'emplacement hors site où archiver les sauvegardes.  
  
-   **Conserver un enregistrement écrit de toutes les modifications apportées à votre système BizTalk Server**  
  
     Veillez à noter toutes les modifications apportées à votre système, telles que les Service packs, les correctifs et QFE qui ont été appliqués. Cela est essentiel pour obtenir que votre système soit restauré dans l'état le plus proche possible de celui dans lequel il était avant la défaillance matérielle.  
  
-   **Implémentez les mesures suivantes pour aider à éviter ou minimiser l’effet d’un sinistre :**  
  
    -   Procurez-vous les mises à jour de logiciels et de microprogramme disponibles.  
  
    -   Munissez-vous de tous les disques d'installation de logiciels immédiatement disponibles. Cela inclut des logiciels système tels que des pilotes spécialisés et des applications telles que BizTalk Server.  
  
    -   Élaborez un plan pour surveiller les serveurs de façon proactive. C'est très important puisque les instances d'orchestration sur un hôte défaillant risquent de ne pas être récupérées par un deuxième hôte pendant dix minutes.  
  
    -   Tenez à jour les enregistrements de matériel.  
  
    -   Tenez à jour les enregistrements de logiciels.  
  
-   **Mettre en œuvre la tolérance de panne de votre organisation au niveau du matériel ou logiciel**  
  
     L'implémentation de clusters et de RAID (redundant array of independent disks) garantit que votre système puisse surmonter une panne matérielle.  
  
-   **Archive le support de sauvegarde sur une base régulière dans un emplacement sécurisé**  
  
     Planifiez l'archivage de votre support de sauvegarde à intervalles réguliers et conservez les archives en lieu sûr, hors site. Cela vous garantit de disposer d'une sauvegarde disponible quand vous en avez besoin.  
  
-   **Vérifier l’intégrité de vos sauvegardes et l’absence d’erreur**  
  
     Surveillez toutes vos opérations de sauvegarde et veillez à ce qu'elle s'opèrent sans erreurs.  
  
-   **Conserver le même matériel de rechange**  
  
     Le fait de disposer de pièces de rechange appropriées vous garantit de pouvoir rapidement remplacer des composants matériels défectueux pour être plus rapidement opérationnel.  
  
-   **Documentez et testez vos procédures de récupération**  
  
     Dans l'idéal, les tests de récupération d'urgence doivent être effectués avant l'exécution de votre système en production. Le fait de disposer de plans bien en place et d'effectuer des tests préliminaires garantit que votre personnel informatique puisse récupérer vos systèmes BizTalk Server. Cela signifie généralement que vous deviez tenter régulièrement de restaurer la sauvegarde du système sur le matériel que vous allez réellement utiliser.  
  
-   **Formez votre personnel informatique sur les procédures de récupération d’urgence**  
  
     Assurez-vous que votre personnel informatique est préparé pour la récupération du système en cas de besoin.  
  
-   **Exercez-vous à restaurer à partir de la sauvegarde dans un environnement de test**  
  
     Exercez-vous à restaurer le système BizTalk Server dans un environnement de test pour être certain de pouvoir le restaurer dans votre environnement de production en cas de défaillance.  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde et restauration de BizTalk Server](../core/backing-up-and-restoring-biztalk-server.md)