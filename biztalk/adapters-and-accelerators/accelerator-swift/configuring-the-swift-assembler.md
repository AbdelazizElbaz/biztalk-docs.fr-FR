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
ms.openlocfilehash: f77d47b2b3ab687f2fd72242f4ddbbc68ae8530c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="configuring-the-swift-assembler"></a><span data-ttu-id="5723d-102">Configuration de l’assembleur SWIFT</span><span class="sxs-lookup"><span data-stu-id="5723d-102">Configuring the SWIFT Assembler</span></span>
<span data-ttu-id="5723d-103">L’assembleur SWIFT exécute les tâches suivantes lorsque vous l’appelez dans un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pipeline d’envoi :</span><span class="sxs-lookup"><span data-stu-id="5723d-103">The SWIFT assembler performs the following tasks when you invoke it in a [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] send pipeline:</span></span>  
  
-   <span data-ttu-id="5723d-104">Détecte le type de message et résout le schéma de document dynamiquement</span><span class="sxs-lookup"><span data-stu-id="5723d-104">Dynamically discovers the message type and resolves the document schema</span></span>  
  
-   <span data-ttu-id="5723d-105">Sérialise le code XML analysé dans des fichiers plats SWIFT</span><span class="sxs-lookup"><span data-stu-id="5723d-105">Serializes parsed XML into SWIFT flat files</span></span>  
  
 <span data-ttu-id="5723d-106">Vous pouvez configurer l’encodage jeu de caractères utilisé pour l’encodage de la sortie sérialisée (par exemple, pour utiliser l’encodage ASCII ou Unicode).</span><span class="sxs-lookup"><span data-stu-id="5723d-106">You can configure the encoding character set used for encoding the serialized output (for example, to use ASCII or Unicode encoding).</span></span>  
  
 <span data-ttu-id="5723d-107">Vous configurez l’assembleur SWIFT au moment du développement de pipeline d’envoi personnalisé qui utilise l’assembleur SWIFT.</span><span class="sxs-lookup"><span data-stu-id="5723d-107">You configure the SWIFT assembler during development time of the custom send pipeline that uses the SWIFT assembler.</span></span>  
  
 <span data-ttu-id="5723d-108">Le Concepteur de Pipeline BizTalk configure l’assembleur SWIFT au moment du développement du pipeline d’envoi personnalisé.</span><span class="sxs-lookup"><span data-stu-id="5723d-108">BizTalk Pipeline Designer configures the SWIFT assembler during development time of the custom send pipeline.</span></span>  
  
 <span data-ttu-id="5723d-109">Pour configurer l’assembleur SWIFT après que qu’elle a été ajouté à l’étape d’assemblage d’un pipeline d’envoi personnalisé, sélectionnez le composant assembleur SWIFT dans la zone de dessin du Concepteur de Pipeline.</span><span class="sxs-lookup"><span data-stu-id="5723d-109">To configure the SWIFT assembler after it has been added to the assemble stage of a custom send pipeline, select the SWIFT assembler component on the Pipeline Designer canvas.</span></span> <span data-ttu-id="5723d-110">L’assembleur SWIFT puis reçoit le focus, et vous pouvez définir ses propriétés de configuration à l’aide de la fenêtre Propriétés dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5723d-110">The SWIFT assembler then receives focus, and you can set its configuration properties using the Properties window within [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)].</span></span>  
  
 <span data-ttu-id="5723d-111">Pour un tableau des propriétés de configuration disponibles et leurs descriptions et les détails d’utilisation, consultez [propriétés de Configuration SWIFT assembleur](../../adapters-and-accelerators/accelerator-swift/swift-assembler-configuration-properties.md).</span><span class="sxs-lookup"><span data-stu-id="5723d-111">For a table of available configuration properties and their descriptions and usage details, see [SWIFT Assembler Configuration Properties](../../adapters-and-accelerators/accelerator-swift/swift-assembler-configuration-properties.md).</span></span>  
  
 <span data-ttu-id="5723d-112">Pour plus d’informations sur l’utilisation de l’assembleur SWIFT pour différents scénarios et la définition des propriétés de configuration, consultez [utilisation de SWIFT désassembleur et assembleur](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md).</span><span class="sxs-lookup"><span data-stu-id="5723d-112">For information about using the SWIFT assembler for different scenarios and setting the configuration properties, see [Working with the SWIFT Disassembler and Assembler](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md).</span></span>  
  
 <span data-ttu-id="5723d-113">Lorsque le fichier binaire de pipeline personnalisé est compilé, il écrit statiquement les paramètres de configuration pour le pipeline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="5723d-113">When the custom pipeline binary is compiled, it statically writes the configuration settings to the custom pipeline.</span></span> <span data-ttu-id="5723d-114">Par conséquent, vous ne peut pas modifier les propriétés de configuration pendant le déploiement ou temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5723d-114">Therefore, you cannot change configuration properties during deployment or run time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5723d-115">Après avoir configuré, compiler et déployer un pipeline personnalisé, modifications de configuration nécessitent la recompilation et redéploiement du pipeline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="5723d-115">After you configure, compile, and deploy a custom pipeline, changes in the configuration require recompiling and redeployment of the custom pipeline.</span></span>  
  
 <span data-ttu-id="5723d-116">Pour plus d’informations sur la création, créer et déployer des pipelines personnalisés, consultez l’aide de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="5723d-116">For information about creating, building, and deploying custom pipelines, see BizTalk Server Help.</span></span>  
  
 <span data-ttu-id="5723d-117">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="5723d-117">This section contains:</span></span>  
  
-   [<span data-ttu-id="5723d-118">Propriétés de la configuration de l’assembleur SWIFT</span><span class="sxs-lookup"><span data-stu-id="5723d-118">SWIFT Assembler Configuration Properties</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-assembler-configuration-properties.md)