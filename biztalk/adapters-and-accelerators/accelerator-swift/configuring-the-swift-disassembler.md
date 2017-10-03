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
# <a name="configuring-the-swift-disassembler"></a><span data-ttu-id="e5e5f-102">Configurer le désassembleur SWIFT</span><span class="sxs-lookup"><span data-stu-id="e5e5f-102">Configuring the SWIFT Disassembler</span></span>
<span data-ttu-id="e5e5f-103">Le désassembleur SWIFT (DASM) effectue les tâches suivantes lorsque vous l’appelez dans un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pipeline de réception :</span><span class="sxs-lookup"><span data-stu-id="e5e5f-103">The SWIFT disassembler (DASM) performs the following tasks when you invoke it in a [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] receive pipeline:</span></span>  
  
-   <span data-ttu-id="e5e5f-104">Détecte le type de message et résout le schéma de document dynamiquement</span><span class="sxs-lookup"><span data-stu-id="e5e5f-104">Dynamically discovers the message type and resolves the document schema</span></span>  
  
-   <span data-ttu-id="e5e5f-105">Analyse des fichiers plats SWIFT dans XML</span><span class="sxs-lookup"><span data-stu-id="e5e5f-105">Parses SWIFT flat files into XML</span></span>  
  
-   <span data-ttu-id="e5e5f-106">Appelle le code XML lecteur pour effectuer la validation XML (schéma) de validation</span><span class="sxs-lookup"><span data-stu-id="e5e5f-106">Invokes the XML validating reader to perform XML (schema) validation</span></span>  
  
-   <span data-ttu-id="e5e5f-107">Appelle le moteur de règles d’entreprise (BRE) pour effectuer une validation de BRE</span><span class="sxs-lookup"><span data-stu-id="e5e5f-107">Invokes the Business Rule Engine (BRE) to perform BRE validation</span></span>  
  
-   <span data-ttu-id="e5e5f-108">Publie un message XML analysé pour la base de données MessageBox avec les propriétés de contexte promues et de la collection d’erreurs sérialisé XML</span><span class="sxs-lookup"><span data-stu-id="e5e5f-108">Publishes a parsed XML message to the MessageBox database with promoted context properties and serialized error collection XML</span></span>  
  
-   <span data-ttu-id="e5e5f-109">Processus des lots entrants</span><span class="sxs-lookup"><span data-stu-id="e5e5f-109">Processes inbound batches</span></span>  
  
 <span data-ttu-id="e5e5f-110">Vous pouvez configurer les fonctionnalités répertoriées ci-dessus pour répondre aux besoins d’un scénario d’utilisateur et [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] solution.</span><span class="sxs-lookup"><span data-stu-id="e5e5f-110">You can configure the functionality listed above to meet the specific requirements for a user scenario and [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] solution.</span></span>  
  
 <span data-ttu-id="e5e5f-111">Le Concepteur de Pipeline BizTalk configure le désassembleur SWIFT au moment du développement du pipeline de réception personnalisé.</span><span class="sxs-lookup"><span data-stu-id="e5e5f-111">BizTalk Pipeline Designer configures the SWIFT disassembler during development time of the custom receive pipeline.</span></span>  
  
 <span data-ttu-id="e5e5f-112">Pour configurer le désassembleur SWIFT après que qu’il a été ajouté à l’étape de désassemblage d’un pipeline de réception personnalisé, sélectionnez le composant désassembleur rapide sur le canevas du Concepteur de Pipeline BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e5e5f-112">To configure the SWIFT disassembler after it has been added to the disassemble stage of a custom receive pipeline, select the SWIFT disassembler component on the BizTalk Pipeline Designer canvas.</span></span> <span data-ttu-id="e5e5f-113">Le désassembleur SWIFT puis reçoit le focus et que vous pouvez définir ses propriétés de configuration à l’aide de la fenêtre Propriétés dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5e5f-113">The SWIFT disassembler then receives focus and you can set its configuration properties using the Properties window within [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)].</span></span>  
  
 <span data-ttu-id="e5e5f-114">Pour un tableau des propriétés de configuration disponibles et leurs descriptions et les détails d’utilisation, consultez [propriétés de Configuration du désassembleur SWIFT](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md).</span><span class="sxs-lookup"><span data-stu-id="e5e5f-114">For a table of available configuration properties and their descriptions and usage details, see [SWIFT Disassembler Configuration Properties](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md).</span></span>  
  
 <span data-ttu-id="e5e5f-115">Pour plus d’informations sur l’utilisation du désassembleur SWIFT pour différents scénarios et la définition des propriétés de configuration, consultez [utilisation de SWIFT désassembleur et assembleur](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md).</span><span class="sxs-lookup"><span data-stu-id="e5e5f-115">For information about using the SWIFT disassembler for different scenarios and setting the configuration properties, see [Working with the SWIFT Disassembler and Assembler](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md).</span></span>  
  
 <span data-ttu-id="e5e5f-116">Lorsque [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] compile le binaire, statique, il écrit les paramètres de configuration pour le pipeline personnalisé de pipeline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="e5e5f-116">When [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] compiles the custom pipeline binary, it statically writes the configuration settings to the custom pipeline.</span></span> <span data-ttu-id="e5e5f-117">Par conséquent, vous ne peut pas modifier les propriétés de configuration pendant le déploiement ou temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="e5e5f-117">Therefore, you cannot change configuration properties during deployment or run time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5e5f-118">Après avoir configuré, compiler et déployer un pipeline personnalisé, modifications de configuration nécessitent la recompilation et redéploiement du pipeline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="e5e5f-118">After you configure, compile, and deploy a custom pipeline, changes in the configuration require recompiling and redeployment of the custom pipeline.</span></span>  
  
 <span data-ttu-id="e5e5f-119">Pour plus d’informations sur la création, la création et le déploiement des pipelines personnalisés, consultez [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="e5e5f-119">For information about creating, building, and deploying custom pipelines, see [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
 <span data-ttu-id="e5e5f-120">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="e5e5f-120">This section contains:</span></span>  
  
-   [<span data-ttu-id="e5e5f-121">Propriétés de Configuration désassembleur SWIFT</span><span class="sxs-lookup"><span data-stu-id="e5e5f-121">SWIFT Disassembler Configuration Properties</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-configuration-properties.md)