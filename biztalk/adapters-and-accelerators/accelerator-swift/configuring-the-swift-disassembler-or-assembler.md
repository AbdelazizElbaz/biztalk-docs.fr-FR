---
title: "Configuration du désassembleur SWIFT ou l’assembleur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembler, configuring
- configuring, disassembler
- disassembler, configuring
- configuring, assembler
ms.assetid: 56e421f2-0292-40af-b878-0cba1b034e19
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8920a8b74da14eeb8186d153444ced7c54d57724
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="configuring-the-swift-disassembler-or-assembler"></a>Configuration du désassembleur SWIFT ou l’assembleur
Après avoir ajouté le désassembleur SWIFT ou assembleur SWIFT à un pipeline personnalisé, vous devez le configurer pour fournir la fonctionnalité souhaitée pour le scénario particulier (par exemple, l’activation/désactivation de la découverte de type dynamique des messages, debatching entrant, la validation de XML Validation du moteur de règles d’entreprise (BRE) et ainsi de suite). Vous devez configurer le désassembleur SWIFT et assembleur au moment du développement avant de compiler et déployer les pipelines personnalisés qui appellent les. Pour configurer le désassembleur/assembleur SWIFT, sélectionnez le composant dans le Concepteur de Pipeline et modifier les propriétés de configuration dans la fenêtre Propriétés.  
  
 Reportez-vous à [propriétés de Configuration du désassembleur SWIFT](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md) pour obtenir des informations détaillées et des descriptions pour chaque propriété de configuration, ainsi que d’autres informations de configuration et de l’utilisation.  
  
 Reportez-vous à [propriétés de Configuration d’assembleur SWIFT](../../adapters-and-accelerators/accelerator-swift/swift-assembler-configuration-properties.md) pour obtenir des informations détaillées et les descriptions de la propriété de configuration du jeu de caractères de codage, ainsi que d’autres informations de configuration et de l’utilisation.  
  
> [!NOTE]
>  Après avoir configuré, compiler et déployer les pipelines personnalisés, modifications de configuration nécessite de recompiler et redéploiement des pipelines personnalisés.  
  
 Après avoir configuré, compiler et déployer vos pipelines personnalisés pour le traitement des messages SWIFT, vous pouvez définir jusqu'à des emplacements de réception qui utilisent votre SWIFT personnalisé de pipeline de réception et d’envoyer des ports qui utilisent votre SWIFT personnalisé pipeline d’envoi. Pour plus d’informations sur le déploiement des pipelines et configuration des ports de réception, emplacements de réception et les ports d’envoi, consultez [Module 4 : création de réception XML et les Ports d’envoi File plat](../../adapters-and-accelerators/accelerator-swift/module-4-adding-an-xml-receive-location-and-flat-file-send-port.md), [Module 5 : création de réception de fichier plat et Ports d’envoi XML](../../adapters-and-accelerators/accelerator-swift/module-5-adding-a-flat-file-receive-location-and-xml-send-port.md)et l’aide de BizTalk Server.  
  
 Contenu de cette section :  
  
-   [Configuration du désassembleur SWIFT](../../adapters-and-accelerators/accelerator-swift/configuring-the-swift-disassembler.md)  
  
-   [Configuration de l’assembleur SWIFT](../../adapters-and-accelerators/accelerator-swift/configuring-the-swift-assembler.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du désassembleur et de l’assembleur SWIFT](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)