---
title: "Configurer manuellement une liaison de port physique à l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, sending messages to the SAP system
- physical port binding, manually configuring
- deploying, receiving messages from the SAP system
ms.assetid: c4f547aa-5514-4ca9-809b-d8d395de419c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 725a26eed4502e0a3d1eca8ed5f1429988590614
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manually-configure-a-physical-port-binding-to-the-sap-adapter"></a>Configurer manuellement une liaison de port physique à l’adaptateur SAP
Configurer le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] comme une liaison WCF personnalisée à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. 

## <a name="port-overview"></a>Vue d’ensemble du port
Après le déploiement de la carte, vous serez en mesure d’envoyer et recevoir des messages à partir du système SAP à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Les étapes de déploiement de l’adaptateur varient en fonction de :  
  
-   La direction de communication entre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Vous pouvez choisir de configurer un envoi, réception, envoi-réception ou un port d’envoi à la réception. Les choix que vous avez effectués sont résumés dans le tableau ci-dessous :  
  
    |Direction du port|Modèle de communication|Direction de communication sélectionnables|  
    |---|---|---|  
    |Send|Unidirectionnel|Toujours envoyer les messages sur ce port.|  
    |Recevoir|Unidirectionnel|Toujours recevoir les messages sur ce port.|  
    |Envoi-Réception|Requête-réponse|J’ai sera envoyer une requête et recevoir une réponse.|  
    |Réception-envoi|Sollicitation-réponse|Recevoir une requête et envoyer une réponse.|  
  
     Pour plus d’informations, consultez [créer un Port d’envoi](../../core/how-to-create-a-send-port2.md), ou [créer un Port de réception](../../core/how-to-create-a-receive-port.md).
  
-   Indique si l’adaptateur envoie des messages au système SAP ou reçoit des messages à partir du système SAP. Selon que vous souhaitez envoyer ou recevoir des messages, vous créez un envoi ou port de réception.  
  
    > [!NOTE]
    >  Vous pouvez également configurer l’envoi ou les ports de réception en important un fichier de configuration de liaison qui est créé par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] dans le cadre de la génération de métadonnées. Pour obtenir des instructions sur la configuration des ports à l’aide de ce fichier de liaison, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md).
  
## <a name="in-this-section"></a>Contenu de cette section  
  
-   [Configurer un port à l’aide de l’adaptateur de base de données Oracle et un adaptateur WCF-custom](../../adapters-and-accelerators/adapter-oracle-database/configure-a-port-using-the-wcf-custom-adapter-and-oracle-database-adapter.md)  
  
-   [Configurer un port à l’aide de l’adaptateur WCF-SAP](../../adapters-and-accelerators/adapter-sap/configure-a-port-using-the-wcf-sap-adapter.md)  
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour créer des applications SAP](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)