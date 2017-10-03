---
title: "Définir le délai de connexion pour une Page ASPX | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ASPX pages, connection time-out
- connections, time-out
ms.assetid: 61d9c996-caf4-48bd-bda7-52f2797a941b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83e083b9f2f0262095e58b4ed9842627888773dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-the-connection-time-out-for-an-aspx-page"></a>Définir le délai de connexion pour une Page ASPX
Lorsque vous utilisez une page ASPX pour des messages synchrones, vous devez augmenter le délai d’expiration de connexion de la page ASPX afin qu’il peut attendre le message attendu.  
  
 Augmenter le délai de connexion pour la page ASPX peut avoir des conséquences inattendues. Tout d’abord, il augmente le risque d’une attaque par déni de service et de la menace d’épuiser la réserve de threads. En second lieu, s’il y a trop de connexions synchrones sur la page ASPX, le système risque de se bloquer. Pendant que vous devez augmenter le délai de connexion, donc veiller à ne pas augmenter de trop.  
  
 Définir le délai de connexion à la valeur minimale autorisée par l’organisation RosettaNet. Pour plus d’informations sur les paramètres de synchronisation pour un processus PIP (Partner Interface), reportez-vous au tableau 4-3 : contrôles Exchange de Message, dans la spécification PIP RosettaNet.  
  
### <a name="to-set-the-connection-time-out-for-the-aspx-page"></a>Pour définir le délai de connexion de la page ASPX  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Outils d'administration**, puis cliquez sur **Gestionnaire des services Internet (IIS)**.  
  
2.  Dans le Gestionnaire IIS, développez le nœud pour l’ordinateur local, puis **Sites Web**.  
  
3.  Cliquez avec le bouton droit sur **Site Web par défaut**, puis cliquez sur **Propriétés**.  
  
4.  Dans la boîte de dialogue Propriétés du Site Web par défaut sur le **Site Web** sous l’onglet du **délai de connexion** zone, tapez une valeur appropriée, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)