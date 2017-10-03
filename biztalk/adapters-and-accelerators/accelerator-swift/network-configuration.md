---
title: "Configuration du réseau | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: deploying, network configuration
ms.assetid: fb6265b8-2e6d-4344-bb44-4f4fd995382d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83a9e8ffe6b278c91429835c3ae32c96d45ef22e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="network-configuration"></a>Configuration réseau
Cette section fournit des indications pour la configuration du réseau dans votre déploiement. Pour plus d’informations, consultez [préparation au déploiement](../../adapters-and-accelerators/accelerator-swift/preparing-for-deployment.md).  
  
 Définir des réseaux locaux virtuels (VLAN) dans le commutateur et puis connectez les câbles appropriés. En définissant les réseaux locaux virtuels, vous désignez les ports sur le commutateur pour chaque segment de réseau ou de la couche. Vous devez créer un réseau local virtuel pour chacun des environnements suivants :  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]réception et envoi de couche  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]couche d’orchestration et de la base de données  
  
-   Réseau d’entreprise  
  
 Après avoir défini les réseaux locaux virtuels, vous pouvez connecter les câbles réseau à partir des serveurs pour les ports appropriés sur le commutateur.  
  
 Contenu de cette section :  
  
-   [Diagramme physique](../../adapters-and-accelerators/accelerator-swift/physical-diagram.md)  
  
-   [Équilibrage de charge réseau](../../adapters-and-accelerators/accelerator-swift/network-load-balancing.md)