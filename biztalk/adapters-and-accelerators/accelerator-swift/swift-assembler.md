---
title: Assembleur SWIFT | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembler
- send pipelines, messages
- messages, send pipelines
ms.assetid: 2a95c7d4-da10-4058-bc2c-3efc35958e14
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91d9411cce90079e8a84fc6919bd6ebf8b2b4371
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-assembler"></a><span data-ttu-id="c543f-102">Assembleur SWIFT</span><span class="sxs-lookup"><span data-stu-id="c543f-102">SWIFT Assembler</span></span>
<span data-ttu-id="c543f-103">Un pipeline d’envoi sortante traite tous les messages transmis par un [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] application (envoyée via un port d’envoi).</span><span class="sxs-lookup"><span data-stu-id="c543f-103">An outbound send pipeline processes all messages transmitted by an [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] application (sent through a send port).</span></span>  
  
 <span data-ttu-id="c543f-104">Les étapes logiques d’exécution relatives au traitement sortant constituent les pipelines d’envoi BizTalk.</span><span class="sxs-lookup"><span data-stu-id="c543f-104">Logical execution stages related to outbound processing make up the BizTalk send pipelines.</span></span> <span data-ttu-id="c543f-105">Un composant de pipeline services ou implémente chaque étape.</span><span class="sxs-lookup"><span data-stu-id="c543f-105">A pipeline component services or implements each stage.</span></span> <span data-ttu-id="c543f-106">En particulier, l’assembleur de services de la phase d’assemblage du pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="c543f-106">In particular, the assembler services the assemble stage in the receive pipeline.</span></span> <span data-ttu-id="c543f-107">A4SWIFT fournit les messages sortants SWIFT spécifiques du traitement dans un composant assembleur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c543f-107">A4SWIFT provides SWIFT-specific outbound message processing functionality in a custom assembler component.</span></span>  
  
 <span data-ttu-id="c543f-108">L’assembleur SWIFT, un assembleur de fichier plat personnalisé, fournit les fonctionnalités pour le traitement des messages SWIFT sortants et exécute les fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="c543f-108">The SWIFT assembler, a custom flat file assembler, provides functionality for processing outbound SWIFT messages, and performs the following functions:</span></span>  
  
-   <span data-ttu-id="c543f-109">Détecte le type de message et résout le schéma de document dynamiquement</span><span class="sxs-lookup"><span data-stu-id="c543f-109">Dynamically discovers the message type and resolves the document schema</span></span>  
  
-   <span data-ttu-id="c543f-110">Sérialise le code XML analysé dans des fichiers plats SWIFT</span><span class="sxs-lookup"><span data-stu-id="c543f-110">Serializes parsed XML into SWIFT flat files</span></span>  
  
 <span data-ttu-id="c543f-111">L’illustration suivante montre les données de l’assembleur SWIFT flux.</span><span class="sxs-lookup"><span data-stu-id="c543f-111">The following figure shows the SWIFT assembler data flow.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/fsa-intro3.gif "FSA_Intro3")  
  
 <span data-ttu-id="c543f-112">Pour plus d’informations sur l’assembleur SWIFT, consultez [utilisation de SWIFT désassembleur et assembleur](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md).</span><span class="sxs-lookup"><span data-stu-id="c543f-112">For more information about the SWIFT assembler, see [Working with the SWIFT Disassembler and Assembler](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c543f-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c543f-113">See Also</span></span>  
 [<span data-ttu-id="c543f-114">BizTalk Accelerator pour SWIFT Runtime</span><span class="sxs-lookup"><span data-stu-id="c543f-114">BizTalk Accelerator for SWIFT Runtime</span></span>](../../adapters-and-accelerators/accelerator-swift/biztalk-accelerator-for-swift-runtime.md)