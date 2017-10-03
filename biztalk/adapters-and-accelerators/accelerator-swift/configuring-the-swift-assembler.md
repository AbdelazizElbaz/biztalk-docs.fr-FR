---
title: "Configuration de l’assembleur SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembler, configuring
- configuring, assembler
ms.assetid: 76944226-e29b-4a7f-a4ab-3c3d5f13ec51
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76e1309012abbaac27e2e0ae6ec9b35f37d88884
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-the-swift-assembler"></a>Configuration de l’assembleur SWIFT
L’assembleur SWIFT exécute les tâches suivantes lorsque vous l’appelez dans un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pipeline d’envoi :  
  
-   Détecte le type de message et résout le schéma de document dynamiquement  
  
-   Sérialise le code XML analysé dans des fichiers plats SWIFT  
  
 Vous pouvez configurer l’encodage jeu de caractères utilisé pour l’encodage de la sortie sérialisée (par exemple, pour utiliser l’encodage ASCII ou Unicode).  
  
 Vous configurez l’assembleur SWIFT au moment du développement de pipeline d’envoi personnalisé qui utilise l’assembleur SWIFT.  
  
 Le Concepteur de Pipeline BizTalk configure l’assembleur SWIFT au moment du développement du pipeline d’envoi personnalisé.  
  
 Pour configurer l’assembleur SWIFT après que qu’elle a été ajouté à l’étape d’assemblage d’un pipeline d’envoi personnalisé, sélectionnez le composant assembleur SWIFT dans la zone de dessin du Concepteur de Pipeline. L’assembleur SWIFT puis reçoit le focus, et vous pouvez définir ses propriétés de configuration à l’aide de la fenêtre Propriétés dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)].  
  
 Pour un tableau des propriétés de configuration disponibles et leurs descriptions et les détails d’utilisation, consultez [propriétés de Configuration SWIFT assembleur](../../adapters-and-accelerators/accelerator-swift/swift-assembler-configuration-properties.md).  
  
 Pour plus d’informations sur l’utilisation de l’assembleur SWIFT pour différents scénarios et la définition des propriétés de configuration, consultez [utilisation de SWIFT désassembleur et assembleur](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md).  
  
 Lorsque le fichier binaire de pipeline personnalisé est compilé, il écrit statiquement les paramètres de configuration pour le pipeline personnalisé. Par conséquent, vous ne peut pas modifier les propriétés de configuration pendant le déploiement ou temps d’exécution.  
  
> [!NOTE]
>  Après avoir configuré, compiler et déployer un pipeline personnalisé, modifications de configuration nécessitent la recompilation et redéploiement du pipeline personnalisé.  
  
 Pour plus d’informations sur la création, la création et le déploiement des pipelines personnalisés, consultez [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
 Contenu de cette section :  
  
-   [Propriétés de Configuration assembleur SWIFT](../../adapters-and-accelerators/accelerator-swift/swift-assembler-configuration-properties.md)