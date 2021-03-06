---
title: "Étape 2 : Configuration d’équilibrage de charge réseau sur les serveurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Network Load Balancing
- configuring, NLB
- NLB
ms.assetid: 30b2f645-b495-49a5-852b-cf89d25fd2b7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6d174ba336a94d44aaffdb2605542035304d9ff
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="step-2-configuring-nlb-on-the-servers"></a>Étape 2 : Configuration d’équilibrage de charge réseau sur les serveurs
Après avoir installé la plate-forme de base et les serveurs configurés avec les paramètres de réseau approprié (voir [étape 1 : installation de la plate-forme de Base](../../adapters-and-accelerators/accelerator-swift/step-1-installing-the-base-platform.md)), vous devrez peut-être activer l’équilibrage de charge sur les serveurs frontaux HTTP BizTalk et BizTalk Serveurs de messagerie. Cette étape est nécessaire uniquement si vous avez une ou plusieurs BizTalk serveurs frontaux HTTP installés sur un ordinateur distinct à partir d’un ou plusieurs serveurs de messagerie BizTalk.  
  
 L’équilibrage de charge garantit la haute disponibilité des communications entre les ordinateurs clients (utilisateurs accédant au site MRSR pour Internet Explorer) et les serveurs MRSR et entre les serveurs MRSR et les serveurs de messagerie.  
  
 Équilibrage de charge sur le **Public** interfaces des serveurs frontaux HTTP est requis pour activer les utilisateurs Intranet pour se connecter aux serveurs Web IIS sur ces ordinateurs. Équilibrage de charge sur le **privé** interfaces des serveurs frontaux HTTP est requis pour activer les serveurs de messagerie contacter les services web sur ces ordinateurs.  
  
 Sur les serveurs de messagerie, en supposant que les deux serveurs, sont configurer l’équilibrage de charge sur le **privé** cartes réseau.  
  
 Pour plus d’informations, consultez le Guide de déploiement de BizTalk Server.