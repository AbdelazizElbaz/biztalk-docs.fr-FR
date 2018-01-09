---
title: "Pipeline d’activer le suivi des | Documents Microsoft"
description: "Suivre les corps de message et des événements lorsque le pipeline traite les messages dans BizTalk Server"
ms.custom: 
ms.date: 12/13/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f7f3c4a-4464-4170-a580-b4ce9296a097
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ed836947ff47e21eeeb3bc306e94ea08f5464f0
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2017
---
# <a name="configure-pipeline-tracking-in-biztalk-server"></a>Configurer le pipeline de suivi des modifications dans BizTalk Server
L’Administration de BizTalk Server permet de configurer le suivi d’un pipeline. Vous pouvez configurer le suivi à des fins de dépannage et d'audit. Vous pouvez afficher des propriétés de message, des événements de port et des événements de message. Vous pouvez également suivre des événements de message et des événements de port pour des messages.  
  
 Vous pouvez configurer le suivi pour un des pipelines par défaut inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ou pour un pipeline personnalisé déployé dans une application BizTalk. Les paramètres de suivi que vous définissez s'appliquent à l'ensemble des instances du pipeline.  
  
> [!IMPORTANT]
>  Vous pouvez configurer le suivi d’un pipeline, cela génère une grande quantité de données, car les données sont rassemblées globalement pour tous les ports qui utilisent le pipeline. Au lieu de cela, nous vous recommandons de configurer le suivi sur votre envoi et de réception des ports, comme décrit dans [configurer le suivi pour un Port d’envoi](../core/how-to-configure-tracking-for-a-send-port.md) et [configurer le suivi pour un Port de réception](../core/how-to-configure-tracking-for-a-receive-port.md).  
  
 Pour plus d’informations sur l’instance de message service et des événements de suivi des fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [afficher un Message de suivi et les données d’Instance](../core/viewing-tracked-message-and-instance-data.md)  
  
## <a name="prerequisites"></a>Prerequisites  
Connectez-vous avec un compte qui est membre du groupe Administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="enable-pipeline-tracking"></a>Activer le suivi de pipeline
  
1.  Dans **Administration de BizTalk Server**, développez le groupe BizTalk contenant le pipeline. 
  
2.  Procédez de l'une des manières suivantes :  
  
    -   Pour configurer le suivi pour l’une de la valeur par défaut de pipelines BizTalk, développez \<tous les artefacts\>.  
  
    -   Pour configurer le suivi pour un pipeline personnalisé déployé dans une application BizTalk, développez l'application contenant le pipeline.  
  
3.  Sélectionnez le **Pipelines** dossier, cliquez sur le pipeline, puis **suivi**.  
  
    > [!NOTE]
    >  Pour configurer le suivi pour plusieurs pipelines, maintenez enfoncée la touche MAJ enfoncée, sélectionnez chaque pipeline, cliquez sur un des pipelines, puis **suivi**.  
  
4.  Utilisez les informations suivantes pour configurer les options de suivi de votre choix, puis sélectionnez **OK** pour enregistrer vos modifications.  
  
    |Propriété|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Suivre les événements - Port commencent et se terminent les événements**|Surveille uniquement une instance commence et se termine. Détails incluent le nom de l’élément, assembly et d’autres métadonnées.|  
    |**Suivre les événements - Message envoyer et recevoir des événements**|Message de pistes envoyer et recevoir des événements. Disponible uniquement si **les événements de début et de fin de Port** est sélectionnée.|  
    |**Suivre les corps de Message - Messages avant le traitement de pipeline**|Enregistre et effectue le suivi des corps de messages reçus par le pipeline, qui conserve des métadonnées telles que les URL ou les propriétés promues. S'il s'agit d'un pipeline de réception, le corps du message constitue le message brut que le composant de transport transmet au pipeline. Il peut être chiffré, signé ou codé, selon l'application. Dans le cas de l'utilisation d'un mappage BizTalk et s'il s'agit d'un pipeline de réception, le suivi a lieu après le traitement du mappage entrant.<br /><br /> Disponible uniquement si **Message envoyer et recevoir des événements** est sélectionnée.|  
    |**Suivre les corps de Message - message après le traitement de pipeline**|Enregistre et effectue le suivi des corps de messages envoyés par le pipeline, qui conserve des métadonnées telles que les URL ou les propriétés promues. S'il s'agit d'un pipeline de réception, le corps du message correspond au message traité devant être transmis à la base de données MessageBox. Il peut s'agit d'un message XML, selon l'application. Dans le cas de l'utilisation d'un mappage BizTalk et s'il s'agit d'un pipeline d'envoi, le suivi a lieu avant le traitement du mappage sortant.<br /><br /> Disponible uniquement si **Message envoyer et recevoir des événements** est sélectionnée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des pipelines](../core/managing-pipelines.md)
