---
title: "Comment régler l’intervalle d’actualisation du Cache Configuration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63c6c998-e9c0-48f1-a36a-f1fcb916321b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad9459fadd65af220982ab31ae0e464cb7f1986e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-adjust-the-configuration-cache-refresh-interval"></a>Comment régler l’intervalle d’actualisation du Cache Configuration
L’intervalle d’actualisation du cache configuration définit la période de temps dans laquelle BizTalk Server met à jour la configuration des points de terminaison. Lorsque vous démarrez BizTalk Server, tous les éléments dans l’administration de BizTalk Server, telles que les bases de données MessageBox, les propriétés du serveur, les cartes et les connexions à la base de données de suivi, sont stockés dans le cache de configuration. Tous les éléments dans le cache sont actualisés à l’intervalle d’actualisation de configuration. Par défaut, cela est toutes les 60 secondes, à l’exception des connexions du serveur de base de données et propriétés du serveur. Cela signifie que si vous modifiez les propriétés générales d’un groupe BizTalk, telles que l’hôte SMTP, les modifications sont récupérées pendant 60 secondes. Modifications du système effectuées à l’extérieur de l’instance ouverte de la console Administration de BizTalk Server ne sont pas répercutées jusqu'à ce que vous actualisiez.  
  
 L’intervalle d’actualisation du cache configuration fait partie des propriétés de groupe BizTalk.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté en tant que membre du groupe des administrateurs de BizTalk Server.  
  
### <a name="to-adjust-the-cache-refresh-interval"></a>Pour régler l’intervalle d’actualisation du cache  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, avec le bouton droit **groupe BizTalk**, puis cliquez sur **paramètres**.  
  
3.  Dans le **Panneau de configuration BizTalk** boîte de dialogue, sélectionnez le **général** onglet. Pour le **intervalle d’actualisation de Configuration** propriété, tapez ou sélectionnez l’heure (en secondes) que tous les éléments de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cache d’administration doit attendre entre les actualisations du cache de configuration, puis cliquez sur **OK** .  
  
    > [!NOTE]  
    >  Les éléments concernés par cette actualisation sont les bases de données MessageBox, les propriétés du serveur, les adaptateurs et les connexions à la base de données des suivis.  
  
    > [!NOTE]  
    >  Par défaut, tous les objets dans le cache de configuration sont actualisés toutes les 60 secondes, à l’exception des connexions du serveur de base de données et propriétés du serveur.