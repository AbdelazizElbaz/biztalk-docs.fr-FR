---
title: "Désassembleur SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disassembler
- messages, receive pipelines
- receive pipelines, messages
ms.assetid: 42641550-0c88-4535-b5d5-b90acb30a6d3
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac0024abe862f777e7ee798991d97845ec5098a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-disassembler"></a><span data-ttu-id="46b67-102">Désassembleur SWIFT</span><span class="sxs-lookup"><span data-stu-id="46b67-102">SWIFT Disassembler</span></span>
<span data-ttu-id="46b67-103">Un pipeline de réception entrant traite tous les messages soumis à une [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] application (reçue à un emplacement de réception).</span><span class="sxs-lookup"><span data-stu-id="46b67-103">An inbound receive pipeline processes all messages submitted to an [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] application (received at a receive location).</span></span>  
  
 <span data-ttu-id="46b67-104">Les étapes logiques d’exécution associées pour le traitement entrant composent BizTalk les pipelines de réception.</span><span class="sxs-lookup"><span data-stu-id="46b67-104">Logical execution stages related to inbound processing make up the BizTalk receive pipelines.</span></span> <span data-ttu-id="46b67-105">Un composant de pipeline services ou implémente chaque étape.</span><span class="sxs-lookup"><span data-stu-id="46b67-105">A pipeline component services or implements each stage.</span></span> <span data-ttu-id="46b67-106">En particulier, le désassembleur de services à l’étape de désassemblage du pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="46b67-106">In particular, the disassembler services the disassemble stage in the receive pipeline.</span></span> <span data-ttu-id="46b67-107">A4SWIFT fournit des fonctionnalités dans un composant désassembleur personnalisé de traitement des messages SWIFT spécifiques.</span><span class="sxs-lookup"><span data-stu-id="46b67-107">A4SWIFT provides SWIFT-specific message processing functionality in a custom disassembler component.</span></span>  
  
 <span data-ttu-id="46b67-108">Le désassembleur SWIFT, un désassembleur de fichier plat personnalisé, fournit les fonctionnalités pour le traitement des lots et les messages entrants SWIFT et exécute les fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="46b67-108">The SWIFT disassembler, a custom flat file disassembler, provides functionality for processing inbound SWIFT messages and batches, and performs the following functions:</span></span>  
  
-   <span data-ttu-id="46b67-109">Détecte le type de message et résout le schéma de document dynamiquement</span><span class="sxs-lookup"><span data-stu-id="46b67-109">Dynamically discovers the message type and resolves the document schema</span></span>  
  
-   <span data-ttu-id="46b67-110">Analyse des fichiers plats SWIFT dans XML</span><span class="sxs-lookup"><span data-stu-id="46b67-110">Parses SWIFT flat files into XML</span></span>  
  
-   <span data-ttu-id="46b67-111">Appelle le code XML lecteur pour effectuer la validation XML (schéma) de validation</span><span class="sxs-lookup"><span data-stu-id="46b67-111">Invokes the XML validating reader to perform XML (schema) validation</span></span>  
  
-   <span data-ttu-id="46b67-112">Appelle le moteur de règles d’entreprise (BRE) pour effectuer une validation de BRE</span><span class="sxs-lookup"><span data-stu-id="46b67-112">Invokes the Business Rule Engine (BRE) to perform BRE validation</span></span>  
  
-   <span data-ttu-id="46b67-113">Publie un message XML analysé pour la base de données MessageBox avec les propriétés de contexte promues et de la collection d’erreurs sérialisé XML</span><span class="sxs-lookup"><span data-stu-id="46b67-113">Publishes a parsed XML message to the MessageBox database with promoted context properties and serialized error collection XML</span></span>  
  
-   <span data-ttu-id="46b67-114">Traite et Désassemble les lots entrants</span><span class="sxs-lookup"><span data-stu-id="46b67-114">Processes and disassembles inbound batches</span></span>  
  
 <span data-ttu-id="46b67-115">L’illustration suivante montre les données désassembleur SWIFT flux.</span><span class="sxs-lookup"><span data-stu-id="46b67-115">The following figure shows the SWIFT disassembler data flow.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/fsa-intro2.gif "FSA_Intro2")  
  
 <span data-ttu-id="46b67-116">Pour plus d’informations sur le désassembleur SWIFT, consultez [utilisation de SWIFT désassembleur et assembleur](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md).</span><span class="sxs-lookup"><span data-stu-id="46b67-116">For more information about the SWIFT disassembler, see [Working with the SWIFT Disassembler and Assembler](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46b67-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46b67-117">See Also</span></span>  
 [<span data-ttu-id="46b67-118">BizTalk Accelerator pour SWIFT Runtime</span><span class="sxs-lookup"><span data-stu-id="46b67-118">BizTalk Accelerator for SWIFT Runtime</span></span>](../../adapters-and-accelerators/accelerator-swift/biztalk-accelerator-for-swift-runtime.md)