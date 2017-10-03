---
title: "Comment configurer le suivi d’un Port de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [receive ports], configuring
- configuring [HAT tracking], receive ports
- tracking, receive ports
- receive ports, tracking
- configuring, tracking
- receive ports, configuring
- tracking, configuring
- HAT, receive ports
- configuring, receive ports
- managing [receive ports], tracking
ms.assetid: dd569e84-cb1c-4191-912a-0c2eb2781a85
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e18748a5d9ff8088d09dfe28bf23c7b729b6afc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-tracking-for-a-receive-port"></a>Configuration du suivi pour un port de réception
Cette rubrique décrit l'utilisation de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour configurer le suivi d'un port de réception, telle que les options d'affichage des corps de messages et des propriétés promues. Ces options vous permettent d'analyser le fonctionnement de votre mise en œuvre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et d'identifier les engorgements éventuels. Les paramètres de suivi que vous définissez s'appliquent à l'ensemble des instances du port de réception.  
  
 Pour plus d’informations sur l’instance de message service et des événements de suivi des fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [liste de vérification : Message et le suivi des données d’Instance](../core/checklist-message-and-instance-data-tracking.md)  
  
 Les paramètres de suivi que vous définissez s'appliquent à l'ensemble des instances du port de réception.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe des administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-configure-tracking-for-a-receive-port"></a>Pour configurer le suivi pour un port de réception  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez successivement le groupe BizTalk, puis l'application BizTalk dont dépend le port de réception pour lequel vous voulez configurer un suivi.  
  
3.  Cliquez sur **Ports de réception**, cliquez sur le port de réception, cliquez sur **suivi**.  
  
    > [!NOTE]
    >  Avant d'activer le suivi des corps de message sur un port de réception, assurez-vous de vouloir suivre le port de réception proprement dit, car cela pourrait entraîner une surcharge. Par exemple, un pipeline de réception RcvPipe est utilisé au niveau de plusieurs emplacements de réception de différents ports de réception. Si vous activez le corps du message suivi option sur RcvPipe, cela entraîne le corps du message de suivi sur tous les emplacements de réception, ce qui vous pouvez faire. Par conséquent, définir le message de suivi des corps sur les ports conformément à vos besoins de réception.  
  
4.  Configurez les options de suivi, comme décrit dans le tableau suivant, puis cliquez sur **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Suivre les corps de Message - message de requête avant le traitement de port**|Cette case à cocher doit être activée pour permettre l'enregistrement et le suivi du contenu du message avant sa réception.|  
    |**Suivre les corps de Message - message de requête après le traitement de port**|Cette case à cocher doit être activée pour permettre l'enregistrement et le suivi du contenu du message après sa réception.|  
    |||  
    |||  
    |**Suivre les propriétés de Message - message de requête avant le traitement de port**|Cette case à cocher doit être activée pour le suivi des propriétés promues d'un message entrant.|  
    |**Suivre les propriétés de Message - message de requête après le traitement de port**|Cette case à cocher doit être activée pour le suivi des propriétés promues d'un message sortant.|  
    |||  
    |||  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des Ports de réception](../core/managing-receive-ports.md)