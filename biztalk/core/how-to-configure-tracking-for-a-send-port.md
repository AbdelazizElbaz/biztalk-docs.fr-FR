---
title: "Comment configurer le suivi d’un Port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, send ports
- configuring, tracking
- tracking, send ports
- configuring [HAT tracking], send ports
- send ports, tracking
- managing [send ports], configuring
- tracking, configuring
- send ports, configuring
- managing [send ports], tracking
- HAT, send ports
ms.assetid: f32e97b0-244c-4acc-8f3f-b18cdb9ec0da
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60ba83b7d3451599a0422ec370fed41eeba94407
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-tracking-for-a-send-port"></a>Configuration du suivi pour un port d'envoi
Cette rubrique décrit l'utilisation de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour configurer le suivi d'un port d'envoi, comme les options d'affichage des corps de messages et des propriétés promues. Ces options vous permettent d'analyser le fonctionnement de votre mise en œuvre BizTalk et d'identifier les engorgements éventuels. Les paramètres de suivi que vous définissez s'appliquent à l'ensemble des instances du port d'envoi.  
  
 Pour plus d’informations sur l’instance de message service et des événements de suivi des fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [afficher un Message de suivi et les données d’Instance](../core/viewing-tracked-message-and-instance-data.md)  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe des administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-configure-tracking-for-a-send-port"></a>Pour configurer le suivi d'un port d'envoi  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez successivement le groupe BizTalk, puis l'application BizTalk dont dépend le port d'envoi pour lequel vous voulez configurer un suivi.  
  
3.  Cliquez sur **Ports d’envoi**, cliquez sur le port d’envoi, cliquez sur **propriétés**, puis cliquez sur **suivi**.  
  
    > [!NOTE]
    >  Un port d'envoi ne peut être associé qu'à un seul pipeline d'envoi Si le suivi des corps de message est désactivé sur le pipeline d'envoi, rien ne peut être suivi sur le port d'envoi. Dans un tel scénario, vous pouvez désactiver les options « Suivi » sur ce port d'envoi.  
  
4.  Configurez les options de suivi, comme décrit dans le tableau suivant, puis cliquez sur **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Suivre les corps de Message - message de requête avant le traitement de port**|Cette case à cocher doit être activée pour permettre l'enregistrement et le suivi du contenu d'un message avant sa réception. **Remarque :** vous devez activer le corps du pipeline le suivi des messages suivre le message de réponse avant le traitement de port.|  
    |**Suivre les corps de Message - message de requête après le traitement de port**|Cette case à cocher doit être activée pour permettre l'enregistrement et le suivi du contenu d'un message après sa réception.|  
    |||  
    |||  
    |**Suivre les propriétés de Message - message de requête avant le traitement de port**|Cette case à cocher doit être activée pour le suivi des propriétés promues d'un message entrant.|  
    |**Suivre les propriétés de Message - message de requête après le traitement de port**|Cette case à cocher doit être activée pour le suivi des propriétés promues d'un message sortant.|  
    |||  
    |||  
  
## <a name="see-also"></a>Voir aussi  
 [Création et configuration des Ports d’envoi](../core/creating-and-configuring-send-ports.md)