---
title: "Sauvegarde d’un ordinateur exécutant BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70f53b41-8083-4b56-8698-e75a13b21a69
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 537ea40b39ecd35127b62f8d96f0175e98a1f3b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="backing-up-a-computer-running-biztalk-server"></a>Sauvegarde d'un ordinateur exécutant BizTalk Server
Si un ordinateur BizTalk Server rencontre une défaillance matérielle irrécupérable, vous devez le remplacer par un ordinateur identique. Vous devez configurer l'ordinateur de remplacement avec la plateforme logicielle de base, les composants logiciels requis, les composants BizTalk Server et des paramètres de configuration identiques. Ces derniers sont constitués des entrées de Registre, fichiers, dossiers et services Windows associés appropriés, nécessaires au fonctionnement correct de vos applications BizTalk.  
  
 Outre la sauvegarde des bases de données BizTalk Server, vous devez sauvegarder les composants BizTalk Server suivants pour permettre la récupération de BizTalk Server suite à une défaillance matérielle :  
  
-   configuration de BizTalk Server ;  
  
-   secret principal de l'authentification unique de l'entreprise (SSO) ;  
  
-   portail BAM (Business Activity Monitoring) (non requis, sauf si vous utilisez l'analyse BAM) ;  
  
-   applications BizTalk.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment faire pour sauvegarder la Configuration de BizTalk Server](../core/how-to-back-up-the-biztalk-server-configuration.md)  
  
-   [Comment sauvegarder le Secret principal](../core/how-to-back-up-the-master-secret.md)  
  
-   [Comment sauvegarder le portail BAM](../core/how-to-back-up-the-bam-portal.md)  
  
-   [Sauvegarde des Applications BizTalk Server](../core/backing-up-biztalk-server-applications.md)