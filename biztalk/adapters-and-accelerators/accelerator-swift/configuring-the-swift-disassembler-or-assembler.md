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
# <a name="configuring-the-swift-disassembler-or-assembler"></a><span data-ttu-id="a7742-102">Configuration du désassembleur SWIFT ou l’assembleur</span><span class="sxs-lookup"><span data-stu-id="a7742-102">Configuring the SWIFT Disassembler or Assembler</span></span>
<span data-ttu-id="a7742-103">Après avoir ajouté le désassembleur SWIFT ou assembleur SWIFT à un pipeline personnalisé, vous devez le configurer pour fournir la fonctionnalité souhaitée pour le scénario particulier (par exemple, l’activation/désactivation de la découverte de type dynamique des messages, debatching entrant, la validation de XML Validation du moteur de règles d’entreprise (BRE) et ainsi de suite).</span><span class="sxs-lookup"><span data-stu-id="a7742-103">After you add the SWIFT disassembler or SWIFT assembler to a custom pipeline, you must configure it to provide the functionality you want for the particular scenario (such as enabling/disabling dynamic message type discovery, inbound debatching, XML validation, Business Rule Engine (BRE) validation, and so on).</span></span> <span data-ttu-id="a7742-104">Vous devez configurer le désassembleur SWIFT et assembleur au moment du développement avant de compiler et déployer les pipelines personnalisés qui appellent les.</span><span class="sxs-lookup"><span data-stu-id="a7742-104">You must configure the SWIFT disassembler and assembler during development time before you compile and deploy the custom pipelines that invoke them.</span></span> <span data-ttu-id="a7742-105">Pour configurer le désassembleur/assembleur SWIFT, sélectionnez le composant dans le Concepteur de Pipeline et modifier les propriétés de configuration dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="a7742-105">To configure the SWIFT disassembler/assembler, select the component in Pipeline Designer and edit the configuration properties in the Properties window.</span></span>  
  
 <span data-ttu-id="a7742-106">Reportez-vous à [propriétés de Configuration du désassembleur SWIFT](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md) pour obtenir des informations détaillées et des descriptions pour chaque propriété de configuration, ainsi que d’autres informations de configuration et de l’utilisation.</span><span class="sxs-lookup"><span data-stu-id="a7742-106">Refer to [SWIFT Disassembler Configuration Properties](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md) for complete details and descriptions for each configuration property, as well as other usage and configuration information.</span></span>  
  
 <span data-ttu-id="a7742-107">Reportez-vous à [propriétés de Configuration d’assembleur SWIFT](../../adapters-and-accelerators/accelerator-swift/swift-assembler-configuration-properties.md) pour obtenir des informations détaillées et les descriptions de la propriété de configuration du jeu de caractères de codage, ainsi que d’autres informations de configuration et de l’utilisation.</span><span class="sxs-lookup"><span data-stu-id="a7742-107">Refer to [SWIFT Assembler Configuration Properties](../../adapters-and-accelerators/accelerator-swift/swift-assembler-configuration-properties.md) for complete details and descriptions for the Encoding Charset configuration property, as well as other usage and configuration information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7742-108">Après avoir configuré, compiler et déployer les pipelines personnalisés, modifications de configuration nécessite de recompiler et redéploiement des pipelines personnalisés.</span><span class="sxs-lookup"><span data-stu-id="a7742-108">After you configure, compile, and deploy the custom pipelines, changes in configuration will require re-compiling and re-deployment of the custom pipelines.</span></span>  
  
 <span data-ttu-id="a7742-109">Après avoir configuré, compiler et déployer vos pipelines personnalisés pour le traitement des messages SWIFT, vous pouvez définir jusqu'à des emplacements de réception qui utilisent votre SWIFT personnalisé de pipeline de réception et d’envoyer des ports qui utilisent votre SWIFT personnalisé pipeline d’envoi.</span><span class="sxs-lookup"><span data-stu-id="a7742-109">After you configure, compile, and deploy your custom pipelines for processing SWIFT messages, you can set up receive locations that use your custom SWIFT receive pipeline, and send ports that use your custom SWIFT send pipeline.</span></span> <span data-ttu-id="a7742-110">Pour plus d’informations sur le déploiement des pipelines et configuration des ports de réception, emplacements de réception et les ports d’envoi, consultez [Module 4 : création de réception XML et les Ports d’envoi File plat](../../adapters-and-accelerators/accelerator-swift/module-4-adding-an-xml-receive-location-and-flat-file-send-port.md), [Module 5 : création de réception de fichier plat et Ports d’envoi XML](../../adapters-and-accelerators/accelerator-swift/module-5-adding-a-flat-file-receive-location-and-xml-send-port.md)et l’aide de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a7742-110">For more information about deploying pipelines and configuring receive ports, receive locations, and send ports, see [Module 4: Creating XML Receive and Flat File Send Ports](../../adapters-and-accelerators/accelerator-swift/module-4-adding-an-xml-receive-location-and-flat-file-send-port.md), [Module 5: Creating Flat File Receive and XML Send Ports](../../adapters-and-accelerators/accelerator-swift/module-5-adding-a-flat-file-receive-location-and-xml-send-port.md), and BizTalk Server Help.</span></span>  
  
 <span data-ttu-id="a7742-111">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="a7742-111">This section contains:</span></span>  
  
-   [<span data-ttu-id="a7742-112">Configuration du désassembleur SWIFT</span><span class="sxs-lookup"><span data-stu-id="a7742-112">Configuring the SWIFT Disassembler</span></span>](../../adapters-and-accelerators/accelerator-swift/configuring-the-swift-disassembler.md)  
  
-   [<span data-ttu-id="a7742-113">Configuration de l’assembleur SWIFT</span><span class="sxs-lookup"><span data-stu-id="a7742-113">Configuring the SWIFT Assembler</span></span>](../../adapters-and-accelerators/accelerator-swift/configuring-the-swift-assembler.md)  
  
## <a name="see-also"></a><span data-ttu-id="a7742-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7742-114">See Also</span></span>  
 [<span data-ttu-id="a7742-115">Utilisation du désassembleur et de l’assembleur SWIFT</span><span class="sxs-lookup"><span data-stu-id="a7742-115">Working with the SWIFT Disassembler and Assembler</span></span>](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)