---
title: "Comment désactiver le suivi des | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4b1e6cdd-8266-494d-b6e7-260ac5a4f2fb
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae1e7ad95aa8be661e283f5671d3443615c7033a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-disable-tracking"></a>Comment désactiver le suivi de
Cette rubrique décrit comment désactiver le suivi à l’aide du [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Vous pouvez configurer diverses options de suivi pendant l’exécution des orchestrations, ports d’envoi, ports de réception et pipelines à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Vous pouvez modifier ces options à tout moment, sans interrompre le processus d'entreprise.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations permettant de gérer une Application](../technical-guides/permissions-for-managing-an-application.md).  
  
> [!NOTE]  
>  Si vous souhaitez uniquement afficher les options de suivi, vous pouvez ouvrir une session en tant que membre de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Opérateurs.  
  
##  <a name="BKMK_DisableOrchTracking"></a>Pour désactiver le suivi d’une orchestration  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant l’orchestration pour laquelle vous souhaitez configurer le suivi.  
  
3.  Cliquez sur **Orchestrations**, dans le volet droit, cliquez sur l’orchestration pour laquelle vous souhaitez configurer le suivi, puis cliquez sur **propriétés**.  
  
4.  Cliquez sur le **suivi** onglet, désactivez les options de suivi comme décrit dans le tableau suivant, puis cliquez sur **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Suivre les événements - début de l’Orchestration et de fin**|Désactivez cette case à cocher pour désactiver le suivi de l’instance d’orchestration avant et après le traitement du processus d’entreprise entière.|  
    |**Suivre les événements - envoi et réception de messages**|Désactivez cette case à cocher pour désactiver le suivi de l’envoi du message et de recevoir des événements. Cette case à cocher est disponible uniquement si vous sélectionnez le **Orchestration début et fin** case à cocher.|  
    |**Suivre les événements - début de la forme et de fin**|Désactivez cette case à cocher lorsque vous n’avez pas besoin de déboguer des instances d’orchestration dans le débogueur d’Orchestration. Quand cette case est activée, la liste des événements du débogueur de l'orchestration contient des données. Cette case à cocher est disponible uniquement si vous sélectionnez le **Orchestration début et fin** case à cocher.|  
    |**Suivre les corps de Message - avant le traitement de l’orchestration**|Désactivez cette case à cocher pour désactiver l’enregistrement et le suivi du contenu réel du message avant le traitement, l’instance d’orchestration. Cette case à cocher est disponible uniquement si vous sélectionnez le **le Message d’envoi et réception** case à cocher.|  
    |**Suivre les corps de Message - après le traitement de l’orchestration**|Désactivez cette case à cocher pour désactiver l’enregistrement et le suivi du contenu réel du message après le traitement par l’instance d’orchestration. Cette case à cocher est disponible uniquement si vous sélectionnez le **le Message d’envoi et réception** case à cocher.|  
    |**Suivre les propriétés de Message - messages entrants**|Désactivez cette case à cocher pour désactiver le suivi des propriétés promues d’un message entrant. Cette case à cocher est disponible uniquement si vous sélectionnez le **le Message d’envoi et réception** case à cocher.|  
    |**Suivre les propriétés de Message - messages sortants**|Désactivez cette case à cocher pour désactiver le suivi des propriétés promues d’un message sortant.  Cette case à cocher est disponible uniquement si vous sélectionnez le **le Message d’envoi et réception** case à cocher.|  
  
### <a name="to-disable-tracking-for-a-send-port"></a>Pour désactiver le suivi pour un port d’envoi  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant le port d’envoi pour lequel vous souhaitez configurer suivi.  
  
3.  Cliquez sur **Ports d’envoi**, cliquez sur le port d’envoi, cliquez sur **propriétés**, puis cliquez sur **suivi**.  
  
4.  Désactiver les options de suivi comme décrit dans le tableau suivant, puis cliquez sur **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Suivre les corps de Message - message de requête avant le traitement de port**|Désactivez cette case à cocher pour désactiver l’enregistrement et le suivi du contenu du message avant que le message est reçu. **Remarque :** vous devez activer le corps du pipeline le suivi des messages suivre le message de réponse avant le traitement de port.|  
    |**Suivre les corps de Message - message de requête après le traitement de port**|Désactivez cette case à cocher pour désactiver l’enregistrement et le suivi du contenu du message une fois que le message est reçu.|  
    |**Suivre les corps de Message - message de réponse avant le traitement de port**|Désactivez cette case à cocher pour désactiver l’enregistrement et le suivi du contenu du message avant que le message est envoyé. Elle est disponible uniquement pour les ports d'envoi avec sollicitation-réponse.|  
    |**Suivre les corps de Message - message de réponse après le traitement de port**|Désactivez cette case à cocher pour désactiver l’enregistrement et le suivi du contenu du message une fois que le message est envoyé. Elle est disponible uniquement pour les ports d'envoi avec sollicitation-réponse.|  
    |**Suivre les propriétés de Message - message de requête avant le traitement de port**|Désactivez cette case à cocher pour désactiver le suivi des propriétés promues d’un message entrant.|  
    |**Suivre les propriétés de Message - message de requête après le traitement de port**|Désactivez cette case à cocher si vous ne souhaitez pas suivre les propriétés promues d’un message sortant.|  
    |**Suivre les propriétés de Message - message de réponse avant le traitement de port**|Désactivez cette case à cocher pour désactiver l’enregistrement et le suivi des propriétés du message avant que le message est envoyé. Elle est disponible uniquement pour les ports d'envoi avec sollicitation-réponse.|  
    |**Suivre les propriétés de Message - message de réponse après le traitement de port**|Désactivez cette case à cocher pour désactiver l’enregistrement et le suivi des propriétés une fois que le message est envoyé. Elle est disponible uniquement pour les ports d'envoi avec sollicitation-réponse.|  
  
### <a name="to-disable-tracking-for-a-receive-port"></a>Pour désactiver le suivi pour un port de réception  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant le port de réception pour lequel vous souhaitez configurer le suivi.  
  
3.  Cliquez sur **Ports de réception**, cliquez sur le port de réception, puis cliquez sur **suivi**.  
  
4.  Désactiver les options de suivi comme décrit dans le tableau suivant, puis cliquez sur **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Suivre les corps de Message - message de requête avant le traitement de port**|Désactivez cette case à cocher pour désactiver l’enregistrement et le suivi du contenu du message avant que le message est reçu.|  
    |**Suivre les corps de Message - message de requête après le traitement de port**|Désactivez cette case à cocher pour désactiver l’enregistrement et le suivi du contenu du message une fois que le message est reçu.|  
    |**Suivre les corps de Message - message de réponse avant le traitement de port**|Désactivez cette case à cocher pour désactiver l’enregistrement et le suivi du contenu du message avant que le message est envoyé. Cette case à cocher est disponible uniquement pour les ports de réception requête-réponse. **Remarque :** vous devez activer le corps du pipeline le suivi des messages suivre le message de réponse avant le traitement de port.|  
    |**Suivre les corps de Message - message de réponse après le traitement de port**|Désactivez cette case à cocher pour désactiver l’enregistrement et le suivi du contenu du message une fois que le message est envoyé. Cette case à cocher est disponible uniquement pour les ports de réception requête-réponse.|  
    |**Suivre les propriétés de Message - message de requête avant le traitement de port**|Désactivez cette case à cocher pour désactiver le suivi des propriétés promues d’un message entrant.|  
    |**Suivre les propriétés de Message - message de requête après le traitement de port**|Désactivez cette case à cocher si vous ne souhaitez pas suivre les propriétés promues d’un message sortant.|  
    |**Suivre les propriétés de Message - message de réponse avant le traitement de port**|Désactivez cette case à cocher pour désactiver l’enregistrement et le suivi des propriétés du message avant que le message est envoyé. Cette case à cocher est disponible uniquement pour les ports de réception requête-réponse.|  
    |**Suivre les propriétés de Message - message de réponse après le traitement de port**|Désactivez cette case à cocher pour désactiver l’enregistrement et le suivi des propriétés une fois que le message est envoyé. Cette case à cocher est disponible uniquement pour les ports de réception requête-réponse.|  
  
### <a name="to-disable-tracking-for-a-policy"></a>Pour désactiver le suivi d’une stratégie  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant la stratégie pour laquelle vous souhaitez configurer suivi.  
  
3.  Cliquez sur **stratégies**, avec le bouton droit de la stratégie, cliquez sur **propriétés**, puis cliquez sur **suivi**.  
  
4.  Désactiver les options de suivi comme décrit dans le tableau suivant, puis cliquez sur **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Activité rapide**|Désactivez cette case à cocher pour désactiver le suivi des données d’instance sur laquelle s’applique la stratégie.|  
    |**Évaluation de condition**|Désactivez cette case à cocher pour désactiver le suivi des résultats true/false des conditions de la stratégie sélectionnée.|  
    |**Déclenchements de règles**|Désactivez cette case à cocher pour désactiver le suivi des actions déclenchées par la stratégie.|  
    |**Mises à jour de l’agenda**|Désactivez cette case à cocher pour désactiver le suivi des mises à jour à l’agenda. Celui-ci contient la liste des actions « True » qui doivent être déclenchées.|  
  
### <a name="to-disable-tracking-for-a-schema"></a>Pour désactiver le suivi d’un schéma  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant le schéma pour lequel vous souhaitez configurer suivi.  
  
3.  Cliquez sur **schémas**, cliquez sur le schéma, puis cliquez sur **propriétés**.  
  
4.  Dans le volet gauche, cliquez sur **suivi**.  
  
5.  Effectuez l’une des options suivantes pour spécifier les propriétés que vous souhaitez désactiver le suivi des messages, puis cliquez sur **OK**:  
  
    -   Désactivez le **toujours suivre toutes les propriétés** case à cocher si vous ne souhaitez pas utiliser toutes les propriétés de message, quelle que soit la version du schéma. Cette case à cocher est disponible seulement pour des schémas de document.  
  
    -   Désactivez le **sélectionner toutes les propriétés de message** case à cocher si vous ne souhaitez pas utiliser toutes les propriétés répertoriées.  
  
    -   Sous **liste des propriétés**, désactivez la case à cocher de chaque propriété que vous ne souhaitez pas utiliser.  
  
    > [!NOTE]  
    >  Vous devez sélectionner uniquement les options dont vous avez besoin, car le suivi des messages crée des performances et le stockage de système de traitement pour votre système.  
  
### <a name="to-disable-tracking-for-a-pipeline"></a>Pour désactiver le suivi d’un pipeline  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
    > [!NOTE]  
    >  Si vous définissez des options de suivi sur les pipelines, vous allez également définir les options de suivi global pour tous les ports qui utilise le pipeline. Cette opération, à son tour, peut entraîner des données beaucoup plus que prévu, en cours de suivi qui ralentit les performances du système. Au lieu de cela, vous pouvez définir les options de suivi de l’envoi de ports et les ports de réception.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant le pipeline pour lequel vous souhaitez configurer suivi.  
  
3.  Procédez de l'une des manières suivantes :  
  
    -   Pour désactiver le suivi pour l’une de la valeur par défaut des pipelines BizTalk, développez \<tous les artefacts\>.  
  
    -   Pour désactiver le suivi d’un pipeline personnalisé qui a été déployé dans une application BizTalk, développez l’application contenant le pipeline.  
  
4.  Cliquez sur le **Pipelines** dossier, cliquez sur le pipeline, puis cliquez sur **suivi**.  
  
    > [!NOTE]  
    >  Pour désactiver le suivi de plusieurs pipelines, maintenez enfoncée la touche MAJ enfoncée, cliquez sur chaque pipeline, cliquez sur un des pipelines, puis cliquez sur **suivi**.  
  
5.  Désactiver les options de suivi comme décrit dans le tableau suivant, puis cliquez sur **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Événements de début et de fin ports**|Désactivez cette case à cocher pour désactiver le suivi uniquement quand une instance commence et se termine. Détails incluent le nom de l’élément, assembly et d’autres métadonnées.|  
    |**Message d’envoyer et recevoir des événements**|Désactivez cette case à cocher pour désactiver le suivi de message envoyer et recevoir des événements. Cette case à cocher est disponible uniquement si **les événements de début et de fin de Port** est sélectionnée.|  
    |**Message avant le traitement de pipeline**|Désactivez cette case à cocher pour désactiver l’enregistrement et le suivi des corps de messages reçus par le pipeline, qui contient des métadonnées telles que les URL ou les propriétés promues. S'il s'agit d'un pipeline de réception, le corps du message constitue le message brut que le composant de transport transmet au pipeline. Il peut être chiffré, signé ou codé, selon l'application. Lorsque vous utilisez un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] mappage, s’il s’agit d’un pipeline de réception, le suivi a lieu après le traitement du mappage entrant.<br /><br /> Cette case à cocher est disponible uniquement si **Message envoyer et recevoir des événements** est sélectionnée.|  
    |**Message après le traitement de pipeline**|Désactivez cette case à cocher pour désactiver l’enregistrement et de suivi des corps des messages envoyés par le pipeline, qui contient des métadonnées telles que les URL ou les propriétés promues. S'il s'agit d'un pipeline de réception, le corps du message correspond au message traité devant être transmis à la base de données MessageBox. Il peut s'agit d'un message XML, selon l'application. Lorsque vous utilisez un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] mappage, s’il s’agit d’un pipeline d’envoi, le suivi a lieu avant le traitement du mappage sortant.<br /><br /> Cette case à cocher est disponible uniquement si **Message envoyer et recevoir des événements** est sélectionnée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Conservation des performances](../technical-guides/maintaining-performance.md)