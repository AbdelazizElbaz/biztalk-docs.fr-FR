---
title: "Configurer manuellement une liaison de port physique à l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- physical port binding, manually configuring
- how to, manually configure adapters for sending messages to a Siebel system
ms.assetid: a1445b8a-440f-45e8-96e9-a13142ca87c6
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed94ca9f6a44919684d36a1be931cbb33f746377
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manually-configure-a-physical-port-binding-to-the-siebel-adapter"></a>Configurer manuellement une liaison de port physique à l’adaptateur Siebel
Cette section fournit des informations sur la configuration de la [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] comme une liaison WCF personnalisée à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Après le déploiement de la carte, vous serez en mesure d’envoyer et recevoir des messages à partir du système Siebel à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Console d’Administration. Les étapes de déploiement de l’adaptateur varient en fonction de la direction de communication entre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. Vous pouvez choisir de configurer un envoi ou un port d’envoi / réception. Les choix que vous avez effectués sont résumés dans le tableau ci-dessous :  
  
|Direction du port|Modèle de communication|Direction de communication sélectionnables|  
|---|---|---|  
|Send|Unidirectionnel|Toujours envoyer les messages sur ce port.|  
|Envoi-Réception|Requête-réponse|J’ai sera envoyer une requête et recevoir une réponse.|  
  
 Pour plus d’informations, consultez [création et configuration des Ports d’envoi](../../core/creating-and-configuring-send-ports.md).
  
> [!NOTE]
>  Recevoir des ports ne sont pas pris en charge, car le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] n’active pas les opérations entrantes à partir du système Siebel.  
  
> [!NOTE]
>  Vous pouvez également configurer les ports d’envoi WCF-Custom en important un fichier de configuration de liaison qui est créé par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] dans le cadre de la génération de métadonnées. Pour obtenir des instructions sur la configuration des ports à l’aide de ce fichier de liaison, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-physical-port-binding-using-a-port-binding-file-to-siebel.md).
  
 
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour créer des applications BizTalk avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)