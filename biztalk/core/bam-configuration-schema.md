---
title: "Schéma de Configuration BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM], scaling
- scaling, BAM
- BAM, scaling
- configuration schema [BAM]
ms.assetid: 7eeeb07f-012e-44eb-a8b5-06e374946e2d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b0d73435dc0245c3c3ce2b1574aa5a70b468c60
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-configuration-schema"></a>Schéma de configuration BAM
Le schéma de configuration BAM définit un document XML qui contient des informations à propos de votre infrastructure, informations que l'utilitaire de gestion BAM utilise pour le développement. Vous pouvez déployer vos bases de données sur plusieurs serveurs à des fins d'évolutivité. Dans l'optique de cette évolutivité, assurez-vous que le document XML de configuration BAM contient les différents noms de serveur et paramètres de configuration des bases de données suivantes :  
  
-   BAMPrimaryImport  
  
-   BAMStarSchema  
  
-   BAMAnalysis  
  
-   BAMArchive  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Lots DTS BAM](../core/bam-dts-packages.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Modification des paramètres d’exécution BAM](../core/changing-bam-runtime-settings.md)