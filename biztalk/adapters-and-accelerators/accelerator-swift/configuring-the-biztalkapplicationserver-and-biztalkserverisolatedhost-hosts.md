---
title: "Configuration du BizTalkApplicationServer et des hôtes de BizTalkServerIsolatedHost | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, hosts
- BizTalkApplicationServer host
- hosts
- BizTalkServerIsolatedHost host
ms.assetid: 17bc9f01-ff87-427d-8411-6a065814ba1e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8459debcd52ce990bc98adf3a2a2372206bae336
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-the-biztalkapplicationserver-and-biztalkserverisolatedhost-hosts"></a>Configuration BizTalkApplicationServer et BizTalkServerIsolatedHost hôtes
Pour limiter la messagerie (envoi et réception de messages) sur les serveurs de messagerie BizTalk, vous devez configurer les ordinateurs hôtes par défaut, qui sont en cours d’exécution envoi MSMQT et gestionnaires de réception, pour exécuter uniquement sur les serveurs de messagerie.  
  
### <a name="to-configure-the-default-hosts"></a>Pour configurer les ordinateurs hôtes par défaut  
  
1.  À l’aide de la Console Administration de BizTalk, de supprimer les instances d’orchestration serveurs hôte de l’hôte BizTalkApplicationServer :  
  
    -   Cliquez sur chaque instance d’hôte, sur **arrêter**.  
  
    -   Cliquez sur chaque instance d’hôte, sur **supprimer**.  
  
2.  À l’aide de la Console Administration de BizTalk, de supprimer les instances d’orchestration serveurs hôte de l’hôte BizTalkServerIsolatedHost :  
  
    -   Cliquez sur chaque instance d’hôte, puis cliquez sur Supprimer.  
  
3.  Après avoir configuré les ordinateurs hôtes, redémarrez toutes les instances d’hôte sur tous les serveurs.