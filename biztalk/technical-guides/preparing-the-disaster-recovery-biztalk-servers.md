---
title: "Préparer les serveurs BizTalk de récupération d’urgence | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14c2c25d-30c5-4e90-a744-f084befa2c1d
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9379136f0845c7c4c987170747a28bd3c50206c4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="preparing-the-disaster-recovery-biztalk-servers"></a>Préparer les serveurs BizTalk de récupération d’urgence
Installer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] serveurs d’exécution sur le site de récupération d’urgence suivant les recommandations de [BizTalk Server 2010 Installation and Upgrade Guides](http://go.microsoft.com/fwlink/?LinkID=194815) (http://go.microsoft.com/fwlink/?LinkID=194815). Configurer ces [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] serveurs d’exécution à l’aide de l’Assistant Configuration de BizTalk pour les joindre au groupe BizTalk de production. Lorsque vous configurez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] serveurs d’exécution sur le site de récupération d’urgence (y compris le serveur de Enterprise seule l’authentification sur le Secret de récupération d’urgence) veillez à :  
  
-   Sélectionnez **non** à la question « Est-ce serveur de secret principal ? »  
  
-   Sélectionnez **jointure** à la question « Voulez-vous créer ou joindre un groupe BizTalk Server ? »  
  
 Après avoir configuré le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] serveurs de récupération d’urgence du moment de l’exécution, créer des instances d’hôte BizTalk sur le site de récupération d’urgence qui correspondent aux instances de l’hôte site de production, mais ne démarrez pas ces instances de l’hôte. Par exemple, si le site de production a trois hôtes **envoyer**, **réception**, et **Orchestration** avec des instances sur server1 et server2 server3, créez trois correspondant instances d’hôte sur DRserver1, DRserver2, DRserver3.  
  
> [!NOTE]  
>  Tous les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-associées telles que l’Instance d’hôte BizTalk et le Service de moteur de règles sur le site de récupération d’urgence doivent indiquer « désactivé » dans le Gestionnaire des Services pour le site de récupération d’urgence empêcher d’effectuer de traitement des services Windows.  
  
 Vous pouvez installer et configurer un nombre différent de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] moment de l’exécution des serveurs dans le site de récupération d’urgence qu’en cours d’exécution en production. Soyez prudent lors de cette approche Toutefois, afin d’éviter de surcharger les serveurs dans le site de récupération d’urgence si un événement de récupération d’urgence se produit. Une fois le groupe BizTalk, comme représenté par l’ensemble des bases de données est entièrement restauré et toutes les modifications système requises sont effectuées pour le groupe BizTalk, les scripts peuvent être exécutés pour joindre le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] serveurs d’exécution pour le groupe BizTalk.