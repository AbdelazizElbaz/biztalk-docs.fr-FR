---
title: "Configurer manuellement une liaison de port physique à l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, sending to an Oracle database
- messages, receiving from an Oracle database
- physical port binding, manually configuring
ms.assetid: 6b118236-e9eb-494e-96b2-969c7064943d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2a64223485cf83fb214055cb1e11b44fb6bc7c4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manually-configure-a-physical-port-binding-to-the-oracle-database-adapter"></a>Configurer manuellement une liaison de port physique à l’adaptateur de base de données Oracle
Cette section fournit des informations sur la configuration de la [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] en tant que liaison de WCF-Custom ou liaison WCF-OracleDB à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Après le déploiement de la carte, vous serez en mesure d’envoyer et recevoir des messages à partir de la base de données Oracle à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Les étapes de déploiement de l’adaptateur varient en fonction de :  
  
-   La direction de communication entre BizTalk Server et [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Vous pouvez choisir de configurer un envoi, réception, envoi-réception ou un port d’envoi à la réception. Les choix disponibles sont résumées dans le tableau suivant.  
  
    |Direction du port|Modèle de communication|Direction de communication sélectionnables|  
    |--------------------|---------------------------|-----------------------------------------------|  
    |Send|Unidirectionnel|Toujours envoyer les messages sur ce port.|  
    |Recevoir|Unidirectionnel|Toujours recevoir les messages sur ce port.|  
    |Envoi / réception|Requête-réponse|J’ai sera envoyer une requête et recevoir une réponse.|  
    |Envoi de réception|Sollicitation-réponse|Recevoir une requête et envoyer une réponse.|  
  
     Pour plus d’informations, consultez [créer un Port d’envoi](../../core/how-to-create-a-send-port2.md), ou [créer un Port de réception](../../core/how-to-create-a-receive-port.md). 
  
-   Indique si l’adaptateur envoie des messages à la base de données Oracle ou reçoit des messages à partir de la base de données Oracle. Selon que vous souhaitez envoyer ou recevoir des messages, vous créez un envoi ou port de réception, respectivement.  
  
    > [!NOTE]
    >  Vous pouvez également configurer l’envoi ou les ports de réception en important un fichier de configuration de liaison qui est créé par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] dans le cadre de la génération de métadonnées. Pour obtenir des instructions sur la configuration des ports à l’aide de ce fichier de liaison, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).  
  
 
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications BizTalk](../../core/develop-your-biztalk-applications.md)