---
title: "Comment configurer le suivi d’un Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [pipelines], tracking warning
- tracking, pipelines
- tracking, warnings
- configuring, pipelines
- pipelines, tracking
- managing [pipelines], configuring
- tracking, configuring
- pipelines, configuring
- configuring [HAT tracking], pipelines
- HAT, pipelines
- managing [pipelines], tracking
ms.assetid: 4f7f3c4a-4464-4170-a580-b4ce9296a097
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f34abe4d9d8b97b1c61bfc6201c3d36b977d0697
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-tracking-for-a-pipeline"></a>Configuration du suivi pour un pipeline
La présente rubrique explique comment configurer le suivi d'un pipeline à l'aide de la console Administration de BizTalk Server. Vous pouvez configurer le suivi à des fins de dépannage et d'audit. Vous pouvez afficher des propriétés de message, des événements de port et des événements de message. Vous pouvez également suivre des événements de message et des événements de port pour des messages.  
  
 Vous pouvez configurer le suivi pour un des pipelines par défaut inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ou pour un pipeline personnalisé déployé dans une application BizTalk. Les paramètres de suivi que vous définissez s'appliquent à l'ensemble des instances du pipeline.  
  
> [!IMPORTANT]
>  Bien que vous ayez la possibilité de configurer le suivi pour un pipeline, cette configuration génère d'importants volumes de données, car les données sont collectées de manière globale pour tous les ports utilisant ce pipeline. Nous vous recommandons plutôt configurer le suivi sur votre envoi et de réception des ports, comme décrit dans [comment configurer le suivi pour un Port d’envoi](../core/how-to-configure-tracking-for-a-send-port.md) et [comment configurer le suivi pour un Port de réception](../core/how-to-configure-tracking-for-a-receive-port.md).  
  
 Pour plus d’informations sur l’instance de message service et des événements de suivi des fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [afficher un Message de suivi et les données d’Instance](../core/viewing-tracked-message-and-instance-data.md)  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-configure-tracking-for-a-pipeline"></a>Pour configurer le suivi pour un pipeline  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server** et développez le groupe BizTalk contenant le pipeline pour lequel vous configurez le suivi.  
  
3.  Procédez de l'une des manières suivantes :  
  
    -   Pour configurer le suivi pour l’une de la valeur par défaut de pipelines BizTalk, développez \<tous les artefacts\>.  
  
    -   Pour configurer le suivi pour un pipeline personnalisé déployé dans une application BizTalk, développez l'application contenant le pipeline.  
  
4.  Cliquez sur le **Pipelines** dossier, cliquez sur le pipeline, puis cliquez sur **suivi**.  
  
    > [!NOTE]
    >  Pour configurer le suivi de plusieurs pipelines, maintenez enfoncée la touche MAJ enfoncée, cliquez sur chaque pipeline, cliquez sur un des pipelines, puis cliquez sur **suivi**.  
  
5.  Configurer les options de suivi, comme décrit dans le tableau suivant, puis cliquez sur **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Événements de début et de fin ports**|Cette case à cocher doit être activée pour effectuer un suivi uniquement au début et à la fin de l'exécution d'une instance. Détails incluent le nom de l’élément, assembly et d’autres métadonnées.|  
    |**Message d’envoyer et recevoir des événements**|Cette case à cocher doit être activée pour effectuer le suivi des événements d'envoi et de réception des messages. Cette case à cocher est disponible uniquement si **les événements de début et de fin de Port** est sélectionnée.|  
    |**Messages avant le traitement du pipeline**|Activer cette case à cocher pour enregistrer et effectuer le suivi des corps de messages reçus par le pipeline, qui contient des métadonnées telles que les URL ou les propriétés promues. S'il s'agit d'un pipeline de réception, le corps du message constitue le message brut que le composant de transport transmet au pipeline. Il peut être chiffré, signé ou codé, selon l'application. Dans le cas de l'utilisation d'un mappage BizTalk et s'il s'agit d'un pipeline de réception, le suivi a lieu après le traitement du mappage entrant.<br /><br /> Cette case à cocher est disponible uniquement si **Message envoyer et recevoir des événements** est sélectionnée.|  
    |**Messages d’après le traitement de pipeline**|Activer cette case à cocher pour enregistrer et effectuer le suivi des corps de messages envoyés par le pipeline, qui contient des métadonnées telles que les URL ou les propriétés promues. S'il s'agit d'un pipeline de réception, le corps du message correspond au message traité devant être transmis à la base de données MessageBox. Il peut s'agit d'un message XML, selon l'application. Dans le cas de l'utilisation d'un mappage BizTalk et s'il s'agit d'un pipeline d'envoi, le suivi a lieu avant le traitement du mappage sortant.<br /><br /> Cette case à cocher est disponible uniquement si **Message envoyer et recevoir des événements** est sélectionnée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des pipelines](../core/managing-pipelines.md)