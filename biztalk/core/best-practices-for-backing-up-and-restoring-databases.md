---
title: "Meilleures pratiques pour la sauvegarde et restauration des bases de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices, maintaining
- restoring, best practices
- best practices, backing up
- backing up, restoring
- backing up, best practices
- maintaining, best practices
- best practices, restoring
ms.assetid: 649ca56b-3cc1-49ad-9f74-ba1521e65ee1
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2543f09c5118e58bd18ea2add113811fb733d884
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-backing-up-and-restoring-databases"></a>Méthodes conseillées pour la sauvegarde et la restauration des bases de données
Consultez les meilleures pratiques suivantes relatives à la sauvegarde et à la restauration des bases de données BizTalk Server.  
  
-   **Développer la sauvegarde et de restauration des stratégies et de les tester.**  
  
     Une stratégie appropriée permet de restaurer rapidement des données perdues suite à une défaillance matérielle.  
  
-   **Gérer l’espace disque et archivez les fichiers de sauvegarde précédentes.**  
  
     Le travail de sauvegarde de BizTalk Server ne supprime pas les fichiers de sauvegarde obsolètes. Vous devez donc gérer ceux-ci afin de conserver de l'espace libre sur le disque. Une fois que vous avez créé une sauvegarde complète de vos bases de données, vous devez déplacer les fichiers de sauvegarde obsolètes vers un périphérique de stockage d'archives pour libérer de l'espace sur le disque principal.  
  
-   **Ne stockez pas de sauvegardes sur le même ordinateur ou le même disque que vous sauvegardez.**  
  
     Vous devez spécifier un ordinateur ou un disque pour la sauvegarde différent de celui contenant les données d'origine. Sinon, vous risquez de perdre toutes vos données en cas de défaillance matérielle.  
  
-   **Conserver des copies.**  
  
     Conservez au moins trois copies du support, dont une copie hors site au sein d'un environnement maîtrisé.  
  
-   **Effectuer des tests de restauration.**  
  
     Une fois par mois, réalisez une opération de restauration d'essai pour vérifier que vos fichiers ont été correctement sauvegardés. Cette opération permet de détecter des problèmes matériels cachés qui ne sont pas mis au jour lors de la vérification du bon fonctionnement de votre logiciel. N'attendez pas une défaillance de votre disque dur pour découvrir si vous êtes en mesure de restaurer votre système et vos bases de données.  
  
-   **Sécurisation des appareils et des supports.**  
  
     Sécurisez à la fois le périphérique de stockage et le support de sauvegarde. Une personne peut très bien accéder à vos données à partir d'un support volé en les restaurant sur un autre serveur pour lequel il dispose des droits d'administrateur.  
  
-   **Surveiller la sauvegarde et le processus de restauration.**  
  
     Pour garantir la réussite de ce processus, vous devez surveiller les travaux de l'Agent SQL Server qui permettent de sauvegarder et de restaurer BizTalk Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde et restauration des bases de données BizTalk Server](../core/backing-up-and-restoring-the-biztalk-server-databases.md)