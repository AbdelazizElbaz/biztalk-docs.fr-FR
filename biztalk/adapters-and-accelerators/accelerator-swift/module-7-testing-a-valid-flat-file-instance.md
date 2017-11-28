---
title: "Module 7 : Test d’une Instance de fichier plat valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing, flat file instance
- tutorial, testing flat file instance
- flat files, testing
ms.assetid: ba8a5d81-41b0-4da7-8c2e-02cf29953af7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 572df71fe479bc26e6b803cdbb95ff7a409c394a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="module-7-testing-a-valid-flat-file-instance"></a><span data-ttu-id="5f2e2-102">Module 7 : Tester une Instance valide de fichier plat</span><span class="sxs-lookup"><span data-stu-id="5f2e2-102">Module 7: Testing a Valid Flat File Instance</span></span>
<span data-ttu-id="5f2e2-103">Dans ce module, vous envoyez un exemple valid MT103 créés dans les laboratoires précédentes des ports de réception de fichier plat dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="5f2e2-103">In this module, you submit a valid sample MT103 flat file to the file receive ports created in the previous labs.</span></span> <span data-ttu-id="5f2e2-104">Cette tâche teste les pipelines de réception que vous avez créé dans les laboratoires précédentes.</span><span class="sxs-lookup"><span data-stu-id="5f2e2-104">This task tests the receive pipelines you created in previous labs.</span></span> [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="5f2e2-105">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]écrit la sortie au format XML dans le dossier de sortie dans le port d’envoi que vous avez sélectionné dans la leçon précédente, [leçon 2 : ajout d’un Port d’envoi XML](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-an-xml-send-port.md).</span><span class="sxs-lookup"><span data-stu-id="5f2e2-105">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] writes the output in XML format to the output folder in the send port you selected in the previous lesson, [Lesson 2: Adding an XML Send Port](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-an-xml-send-port.md).</span></span>  
  
 <span data-ttu-id="5f2e2-106">Vous lancez le fichier de l’adaptateur de réception en copiant un fichier plat au format SWIFT dans le dossier entrant.</span><span class="sxs-lookup"><span data-stu-id="5f2e2-106">You initiate the file receive adapter by copying a SWIFT flat-formatted file to the inbound folder.</span></span> <span data-ttu-id="5f2e2-107">Cette action entraîne [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] routage d’un fichier XML de SWIFT valide dans le dossier sortant.</span><span class="sxs-lookup"><span data-stu-id="5f2e2-107">This action results in [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] routing a valid SWIFT XML file to the outbound folder.</span></span>  
  
 <span data-ttu-id="5f2e2-108">Dans cette tâche, vous permet également d’envoyer un message MT103 qui n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="5f2e2-108">In this task, you also submit an MT103 message that is not valid.</span></span> <span data-ttu-id="5f2e2-109">Vous utilisez l’événement pour résoudre l’erreur.</span><span class="sxs-lookup"><span data-stu-id="5f2e2-109">You use the Event to resolve the error.</span></span>  
  
 <span data-ttu-id="5f2e2-110">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="5f2e2-110">This section contains:</span></span>  
  
-   [<span data-ttu-id="5f2e2-111">Leçon 1 : Envoi d’un exemple de fichier plat</span><span class="sxs-lookup"><span data-stu-id="5f2e2-111">Lesson 1: Submitting a Sample Flat File</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-1-submitting-a-sample-flat-file.md)  
  
-   [<span data-ttu-id="5f2e2-112">Leçon 2 : Envoi d’un Message MT103 qui n’est pas valide</span><span class="sxs-lookup"><span data-stu-id="5f2e2-112">Lesson 2: Submitting an MT103 Message That Is Not Valid</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-2-submitting-an-mt103-message-that-is-not-valid.md)  
  
-   [<span data-ttu-id="5f2e2-113">Leçon 3 : Test d’une Instance XML</span><span class="sxs-lookup"><span data-stu-id="5f2e2-113">Lesson 3: Testing an XML Instance</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-3-testing-an-xml-instance.md)