---
title: "Scénario de faible latence Optimizations2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19cd78ce-ad7d-4e4b-8188-a63d707905d5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 009b1298e90b586830f062c8e884b88995f9e33f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="low-latency-scenario-optimizations"></a>Optimisations de scénario de faible latence
Par défaut, BizTalk Server est optimisé pour un débit plutôt que de faible latence. Les optimisations suivantes peuvent être appliquées à BizTalk Server dans les scénarios où la latence réduite est requise.  
  
> [!NOTE]  
>  Ces optimisations améliorent les temps de latence, mais peuvent le faire à un coût pour le débit global.  
  
## <a name="increase-the-biztalk-server-host-internal-message-queue-size"></a>Augmenter la taille de file d’attente de messages interne hôte BizTalk Server  
 Chaque hôte de BizTalk possède sa propre file d’attente en mémoire interne. Augmenter la taille de cette file d’attente à partir de la valeur par défaut de 100 à 10 000 pour améliorer les performances d’un scénario à faible latence. Pour plus d’informations sur la modification de la valeur de la taille de file d’attente de messages interne, consultez [comment modifier les ressources de limitation paramètres](http://go.microsoft.com/fwlink/?LinkID=208366) (http://go.microsoft.com/fwlink/?LinkID=208366) dans la documentation de BizTalk Server.  
  
> [!NOTE]  
>  Augmentation de la valeur de taille de file d’attente de messages interne augmentera la mémoire utilisée par l’instance d’hôte.  
  
## <a name="increase-the-biztalk-server-host-in-process-messages"></a>Augmenter les messages de dans le processus hôte BizTalk Server  
 Augmentez les messages in-process à partir de la valeur par défaut de 1000 à 10 000 pour améliorer les performances. Pour plus d’informations sur la modification de la valeur des messages dans le processus, consultez [comment modifier les paramètres de limitation d’hôte par défaut](http://go.microsoft.com/fwlink/?LinkID=208366) (http://go.microsoft.com/fwlink/?LinkID=208366) dans la documentation de BizTalk Server.  
  
> [!NOTE]  
>  Augmentation de la valeur de taille de file d’attente de messages interne augmentera la mémoire utilisée par l’instance d’hôte.  
  
## <a name="optimize-orchestrations-for-low-latency"></a>Optimiser les orchestrations pour une latence faible  
 Suivez les recommandations de la section « Recommandations pour l’optimisation des orchestrations pour les scénarios de faible latence » de [optimisation des performances d’Orchestration](../technical-guides/optimizing-orchestration-performance.md).  
  
## <a name="configure-polling-intervals"></a>Configurer les intervalles d’interrogation  
 Utilisez le panneau de configuration pour configurer les intervalles d’interrogation d’un hôte donné, dans le groupe BizTalk. Pour modifier les intervalles d’interrogation :  
  
1.  Dans le **Console d’Administration de BizTalk Server**, développez **Administration de BizTalk Server**, avec le bouton droit **groupe BizTalk**, puis cliquez sur **paramètres** .  
  
2.  Dans le **Panneau de configuration BizTalk** boîte de dialogue le **hôtes** page, sur le **général** sous l’onglet sous **intervalles d’interrogation**, vous trouverez le **messagerie** et **Orchestration** valeurs. Par défaut, ces deux valeurs sont définies à 500 millisecondes.  
  
 Le tableau suivant répertorie les valeurs d’interrogation que nous avons utilisés pour le test sur les hôtes BizTalk dans le processus 64 bits (RxHost, TxHost et PxHost). Pour désactiver l’interrogation, vous pouvez définir l’intervalle d’interrogation d’un très grand nombre figurant dans la table.  
  
|Hôtes de serveur|Messagerie|Orchestration|  
|------------------|---------------|-------------------|  
|**RxHost**<br /><br /> Étant donné que nous publions uniquement l’emplacement de réception des messages entrants dans la boîte de message BizTalk via unidirectionnel, l’interrogation n’est pas requis sur le RxHost (hôte de réception).|200000|200000|  
|**TxHost**<br /><br /> Étant donné que nous recevons uniquement des instances de messagerie à partir de la boîte de message BizTalk, interrogation de l’orchestration n’est pas requis sur le TxHost (hôte d’envoi).|50|200000|  
|**PxHost**<br /><br /> Étant donné que nous recevons uniquement des instances d’orchestration à partir de la boîte de message BizTalk, la messagerie d’interrogation n’est pas requis sur le PxHost (hôte de traitement).|200000|50|  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances de BizTalk Server](../technical-guides/optimizing-biztalk-server-performance.md)