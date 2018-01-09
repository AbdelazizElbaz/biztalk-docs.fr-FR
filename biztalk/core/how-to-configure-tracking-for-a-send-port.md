---
title: "Activer le suivi des modifications sur un Port d’envoi | Documents Microsoft"
description: "Activer le suivi des corps de message et de suivre les propriétés de message sur un port d’envoi dans BizTalk Server"
ms.custom: 
ms.date: 12/13/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f32e97b0-244c-4acc-8f3f-b18cdb9ec0da
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 223c417769086cc71f501b044410bf2d3e4cbc74
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2017
---
# <a name="configure-send-port-tracking-in-biztalk-server"></a>Configurer le suivi de port d’envoi dans BizTalk Server
Utilisez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour configurer le suivi d’un port d’envoi, telles que les options d’affichage du corps des messages et les propriétés promues. Ces options vous permettent d'analyser le fonctionnement de votre mise en œuvre BizTalk et d'identifier les engorgements éventuels. Les paramètres de suivi que vous définissez s'appliquent à l'ensemble des instances du port d'envoi.  
  
 Pour plus d’informations sur l’instance de message service et des événements de suivi des fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [afficher un Message de suivi et les données d’Instance](../core/viewing-tracked-message-and-instance-data.md)  
  
## <a name="prerequisites"></a>Prerequisites  
Connectez-vous avec un compte qui est membre de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="enable-tracking-on-a-send-port"></a>Activer le suivi des modifications sur un port d’envoi  
  
1.  Dans **Administration de BizTalk Server**, développez le groupe BizTalk, puis développez votre application BizTalk qui a le port d’envoi.  
  
2.  Sélectionnez **Ports d’envoi**, cliquez sur le port d’envoi, sélectionnez **propriétés**, puis sélectionnez **suivi**.  
  
    > [!NOTE]
    >  Un port d'envoi ne peut être associé qu'à un seul pipeline d'envoi Si le suivi des corps de message est désactivé sur le pipeline d’envoi, rien n’est suivi sur le port d’envoi. Dans un tel scénario, vous pouvez désactiver les options « Suivi » sur ce port d'envoi.  
  
3.  Utilisez les informations suivantes pour activer les options de suivi de votre choix, puis sélectionnez **OK** pour enregistrer vos modifications.  
  
    |Propriété|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Suivre les corps de Message - message de requête avant le traitement de port**|Enregistre et effectue le suivi de contenu du message avant que le message est reçu. <br/><br/> **Remarque**: veillez à activer le suivi de pipeline message corps suivre le message de réponse avant le traitement de port.|  
    |**Suivre les corps de Message - message de requête après le traitement de port**|Enregistre et effectue le suivi de contenu du message une fois que le message est reçu.|  
    |**Suivre les corps de Message-message de réponse avant le traitement de port**|Enregistre et effectue le suivi de contenu du message avant que le message est envoyé. Disponible uniquement pour les ports d’envoi de sollicitation-réponse.|    
    |**Suivre les corps de Message-message de réponse après le traitement de port**|Enregistre et effectue le suivi de contenu du message une fois que le message est envoyé. Disponible uniquement pour les ports d’envoi de sollicitation-réponse.|  
    |**Suivre les corps de Message-message de réponse après le traitement de port**|Effectue le suivi des propriétés promues d’un message entrant.|  
    |**Suivre les propriétés de Message - message de requête après le traitement de port**|Effectue le suivi des propriétés promues d’un message sortant.|  
    |**Suivre les propriétés de Message-message de réponse avant le traitement de port**|Enregistre et effectue le suivi des propriétés de message avant que le message est envoyé. Disponible uniquement pour les ports d’envoi de sollicitation-réponse.|   
    |**Suivre les propriétés de Message-message de réponse après le traitement de port**|Enregistre et effectue le suivi des propriétés une fois que le message est envoyé. Disponible uniquement pour les ports d’envoi de sollicitation-réponse.|   
  
## <a name="see-also"></a>Voir aussi  
 [Création et configuration des ports d’envoi](../core/creating-and-configuring-send-ports.md)
