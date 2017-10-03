---
title: "Gérer les Ports d’envoi et groupes de ports d’envoi | Documents Microsoft"
description: "Des liens pour créer, configurer, inscrire, désinscrire et démarrer et arrêter des ports d’envoi dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db45f9f9-b32a-4b9c-a3bf-8c271d0f0cf9
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 928160ed5b67602c8fc8d9d646459bf2425d7a01
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-send-ports-and-send-port-groups"></a>Gérer les Ports d’envoi et groupes de ports d’envoi

## <a name="overview"></a>Vue d'ensemble
Cette section fournit des instructions sur l'utilisation de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour créer, configurer et gérer des ports d'envoi et des groupes de ports d'envoi dans une application BizTalk. Un port d'envoi spécifie l'emplacement vers lequel les messages sont envoyés et éventuellement, l'emplacement à partir duquel les réponses sont reçues. Lorsqu’un message est envoyé à un port d’envoi, une nouvelle instance du service de port d’envoi est créée, qui est appelé un *l’instance de service*.  
  
 Un groupe de ports d'envoi est un groupe logique de ports d'envoi. Lorsqu'un message est envoyé à un groupe de ports d'envoi, il est acheminé vers tous les ports d'envoi associés.  Pour plus d’informations générales sur les ports d’envoi et groupes de ports d’envoi, consultez [Ports d’envoi et groupes de ports d’envoi](../core/send-ports-and-send-port-groups.md).  
  
> [!NOTE]
>  Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives. Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
> [!NOTE]
>  Lorsqu'il développe une application BizTalk, le développeur peut utiliser les outils de conception BizTalk dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], tels que le Concepteur d'orchestration, pour créer et configurer des ports d'envoi et des groupes de ports d'envoi. Pour plus d’informations, consultez [à l’aide des Ports dans les Orchestrations](../core/using-ports-in-orchestrations.md).  
  
## <a name="next-steps"></a>Étapes suivantes
  
-   [Création et configuration des Ports d’envoi](../core/creating-and-configuring-send-ports.md)  
  
-   [Création et configuration des groupes de ports d’envoi](../core/creating-and-configuring-send-port-groups.md)  
  
-   [Inscrire un Port d’envoi ou un groupe de ports d’envoi](../core/how-to-enlist-a-send-port-or-send-port-group.md)  
  
-   [Désinscrire un Port d’envoi ou un groupe de ports d’envoi](../core/how-to-unenlist-a-send-port-or-send-port-group.md)  
  
-   [Démarrer un Port d’envoi ou un groupe de ports d’envoi](../core/how-to-start-a-send-port-or-send-port-group.md)  
  
-   [Arrêter un Port d’envoi ou un groupe de ports d’envoi](../core/how-to-stop-a-send-port-or-send-port-group.md)