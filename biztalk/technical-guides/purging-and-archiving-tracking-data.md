---
title: "Archivage des données de suivi et la purge | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14094fda-3fd9-4d45-9bbb-cd9377c2cbad
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94a2560bc8a57a8f60bf2d1ebcddf68b62fd178a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="purging-and-archiving-tracking-data"></a>Purge et archivage des données de suivi
Il est important de configurer et activer le travail de Purge et archivage SQL Agent. Ce travail Archive et purge les anciennes données à partir de la base de données de suivi BizTalk (DTA). Ceci est essentiel pour une intégrité [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] système. Une base de données de suivi volumineux commence à affecter les performances de l’hôte de suivi et de tous les autres processus qui interrogent la base de données de suivi. Si les données de suivi ne sont pas purgées à partir de la base de données de suivi, la base de données continue de croître.  
  
## <a name="guidelines-for-using-the-dta-purge-and-archive-job"></a>Instructions pour l’utilisation de DTA Purge et d’archiver le travail  
  
-   **Assurez-vous que le travail de Purge et archivage SQL Agent est correctement configuré, activé et exécution.**  
  
     Ce travail n’est pas activé par défaut, car vous devez tout d’abord le configurer pour inclure un répertoire où les fichiers d’archive peuvent être écrite.  
  
-   **Si vous devez uniquement purger les anciennes données et ne le faites pas archiver tout d’abord, puis modifier l’instruction SQL Agent de la fonction pour appeler la procédure stockée « dtasp_PurgeTrackingDatabase ».**  
  
     Ignore l’étape d’archivage et effectue simplement la purge. Pour plus d’informations sur cette procédure stockée et en modifiant le travail de l’Agent SQL pour l’utiliser, consultez [« Comment purger les données à partir de la BizTalk suivi base de données »](http://go.microsoft.com/fwlink/?LinkId=153817) (http://go.microsoft.com/fwlink/?LinkId=153817).  
  
-   **Assurez-vous que le travail est en mesure de purger les données de suivi aussi vite que les données de suivi entrantes sont générées.**  
  
     Il est acceptable pour le travail se trouve derrière pendant les pics de charge, mais il doit toujours être en mesure de rattraper son retard. Si le travail de purge prend du retard et n’est jamais en mesure de rattraper son retard, la base de données de suivi continueront à croître et performances sera finalement être affectées.  
  
-   **Passez en revue la purge normale et purge les paramètres pour s’assurer que vous conservez les données pendant la durée optimale.**  
  
     Pour plus d’informations sur ces paramètres, consultez [« D’archivage et purge du suivi des base de données BizTalk »](http://go.microsoft.com/fwlink/?LinkId=153816) (http://go.microsoft.com/fwlink/?LinkId=153816).  
  
-   **Si vous devez conserver le suivi des fichiers d’archive, assurez-vous d’avoir un processus en place pour restaurer et de les utiliser avec succès.**  
  
## <a name="see-also"></a>Voir aussi  
 [Liste de vérification : Configuration de SQL Server](~/technical-guides/checklist-configuring-sql-server.md)