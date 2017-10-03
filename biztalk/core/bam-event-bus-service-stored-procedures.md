---
title: "Procédures stockées de Service Bus d’événements BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stored procedures, Even Bus Service [BAM]
- Event Bus Service [BAM], stored procedures
ms.assetid: 18a7bd40-50ce-44f2-88ae-45a2e3c8d3f4
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f44dce10113b8a3a85b7c1dd177f637933b582ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-event-bus-service-stored-procedures"></a>Procédures stockées et service Bus d'événements BAM
Utilisez les procédures stockées suivantes pour gérer le service Bus d'événements BAM :  
  
-   Pour interrompre momentanément le service Bus d'événements BAM, exécutez la procédure stockée TDDS_BlockTDDS dans le cadre d'une transaction (sans valider la transaction) dans la base de données d'analyse BAM. Pour relancer le service Bus d'événements BAM, validez la transaction TDDS_BlockTDDS.  
  
-   Pour activer le service Bus d'événements BAM sur plusieurs ordinateurs, identifiez le ou les hôtes à utiliser pour le suivi et joignez ces ordinateurs à l'hôte de suivi.  
  
-   Pour définir le délai d'attente de session et l'intervalle de pulsation, utilisez la procédure stockée TDDS_UpdateSettings. Seuls les membres du groupe BTS_ADMIN_USERS ont l'autorisation d'exécuter cette procédure stockée.  
  
     La procédure stockée TDDS_UpdateSettings peut être définie à l'aide des paramètres suivants :  
  
    -   @RefreshIntervalint. doit être supérieur à 60 secondes.  
  
    -   @SqlCommandTimeoutint. doit être inférieur à la valeur définie pour RefreshInterval.  
  
    -   @SessionTimeoutint. doit être deux fois supérieur à la valeur définie pour RefreshInterval.  
  
    -   @EventLoggingIntervalnvarchar(16). doit être supérieur à 60 secondes.  
  
    -   @RetryCountint. La valeur supérieure à 60 secondes  
  
    -   @ThreadPerSessionint. ce paramètre est obsolète.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion BAM](../core/managing-bam.md)