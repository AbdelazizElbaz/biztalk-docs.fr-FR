---
title: "Configurer manuellement une liaison de port physique à l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3f0bb78-c85f-4629-9e2d-cce180ff78ae
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac72d914539eabc9b129985c2b9335270e561d18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manually-configure-a-physical-port-binding-to-the-sql-adapter"></a>Configurer manuellement une liaison de port physique à l’adaptateur SQL
Cette section fournit des informations sur la configuration de la [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] sous la forme d’une liaison WCF personnalisée ou un port WCF-SQL à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Après le déploiement de la carte, vous serez en mesure d’envoyer et recevoir des messages à partir de SQL Server à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Les étapes de déploiement de l’adaptateur varient en fonction de :  
  
-   La direction de communication entre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Vous pouvez choisir de configurer un envoi, réception, ou un port d’envoi / réception. Les choix disponibles sont résumées dans le tableau suivant.  
  
    |Direction du port|Modèle de communication|Direction de communication sélectionnables|  
    |--------------------|---------------------------|-----------------------------------------------|  
    |Send|Unidirectionnel|Toujours envoyer les messages sur ce port.|  
    |Recevoir|Unidirectionnel|Toujours recevoir les messages sur ce port.|  
    |Envoi / réception|Requête-réponse|J’ai sera envoyer une requête et recevoir une réponse.|  
  
    > [!NOTE]
    >  Bidirectionnel recevoir des ports ne sont pas pris en charge par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
     Pour plus d’informations, consultez [la création d’un Port d’envoi](../../core/how-to-create-a-send-port2.md), ou [la création d’un Port de réception](../../core/how-to-create-a-receive-port.md). 
  
-   Indique si l’adaptateur envoie des messages vers le serveur SQL Server (opérations sortantes) ou reçoit des messages à partir de SQL Server (opérations entrantes). Selon que vous souhaitez envoyer ou recevoir des messages, vous créez un envoi ou port de réception, respectivement.  
  
    > [!NOTE]
    >  Vous pouvez également configurer l’envoi ou les ports de réception en important un fichier de configuration de liaison qui est créé par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] dans le cadre de la génération de métadonnées. Pour obtenir des instructions sur la configuration des ports à l’aide de ce fichier de liaison, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à utiliser l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Configurer un port à l’aide de l’adaptateur WCF-custom et l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-port-using-the-wcf-custom-adapter-and-sql-adapter.md)  
  
-   [Configurer un port à l’aide de l’adaptateur WCF-SQL](../../adapters-and-accelerators/adapter-sql/configure-a-port-using-the-wcf-sql-adapter.md)  
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour développer des applications BizTalk à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)