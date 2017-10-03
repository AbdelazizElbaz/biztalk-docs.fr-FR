---
title: "Configurer le désassembleur SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, disassembler
- disassembler, configuring
ms.assetid: f3773781-7412-421c-943c-18cc665da8d9
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7aa71ce6ba1d2a910626446ed45439b8c7132e75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-the-swift-disassembler"></a>Configurer le désassembleur SWIFT
Le désassembleur SWIFT (DASM) effectue les tâches suivantes lorsque vous l’appelez dans un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pipeline de réception :  
  
-   Détecte le type de message et résout le schéma de document dynamiquement  
  
-   Analyse des fichiers plats SWIFT dans XML  
  
-   Appelle le code XML lecteur pour effectuer la validation XML (schéma) de validation  
  
-   Appelle le moteur de règles d’entreprise (BRE) pour effectuer une validation de BRE  
  
-   Publie un message XML analysé pour la base de données MessageBox avec les propriétés de contexte promues et de la collection d’erreurs sérialisé XML  
  
-   Processus des lots entrants  
  
 Vous pouvez configurer les fonctionnalités répertoriées ci-dessus pour répondre aux besoins d’un scénario d’utilisateur et [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] solution.  
  
 Le Concepteur de Pipeline BizTalk configure le désassembleur SWIFT au moment du développement du pipeline de réception personnalisé.  
  
 Pour configurer le désassembleur SWIFT après que qu’il a été ajouté à l’étape de désassemblage d’un pipeline de réception personnalisé, sélectionnez le composant désassembleur rapide sur le canevas du Concepteur de Pipeline BizTalk. Le désassembleur SWIFT puis reçoit le focus et que vous pouvez définir ses propriétés de configuration à l’aide de la fenêtre Propriétés dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)].  
  
 Pour un tableau des propriétés de configuration disponibles et leurs descriptions et les détails d’utilisation, consultez [propriétés de Configuration du désassembleur SWIFT](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md).  
  
 Pour plus d’informations sur l’utilisation du désassembleur SWIFT pour différents scénarios et la définition des propriétés de configuration, consultez [utilisation de SWIFT désassembleur et assembleur](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md).  
  
 Lorsque [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] compile le binaire, statique, il écrit les paramètres de configuration pour le pipeline personnalisé de pipeline personnalisé. Par conséquent, vous ne peut pas modifier les propriétés de configuration pendant le déploiement ou temps d’exécution.  
  
> [!NOTE]
>  Après avoir configuré, compiler et déployer un pipeline personnalisé, modifications de configuration nécessitent la recompilation et redéploiement du pipeline personnalisé.  
  
 Pour plus d’informations sur la création, la création et le déploiement des pipelines personnalisés, consultez [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
 Contenu de cette section :  
  
-   [Propriétés de Configuration désassembleur SWIFT](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md)