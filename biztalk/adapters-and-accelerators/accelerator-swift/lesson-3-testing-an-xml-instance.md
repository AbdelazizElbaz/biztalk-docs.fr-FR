---
title: "Leçon 3 : Test d’une Instance XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing, XML instances
- XML instances
ms.assetid: 19d7dd18-17dc-4355-a4f1-5c5e6750faf3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 948ea484b5cc3138a73a67b384705ed73d9478b2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="lesson-3-testing-an-xml-instance"></a><span data-ttu-id="252ef-102">Leçon 3 : Test d’une Instance XML</span><span class="sxs-lookup"><span data-stu-id="252ef-102">Lesson 3: Testing an XML Instance</span></span>
<span data-ttu-id="252ef-103">Dans cette leçon, vous envoyez un MT103 valide créés dans les leçons précédentes de ports de réception de message au format XML dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="252ef-103">In this lesson, you submit a valid MT103 message in XML format to the file receive ports created in the previous lessons.</span></span> <span data-ttu-id="252ef-104">Cette action teste les pipelines d’envoi que vous avez créé dans les modules précédentes.</span><span class="sxs-lookup"><span data-stu-id="252ef-104">This action tests the send pipelines that you created in previous modules.</span></span> [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="252ef-105">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]écrit la sortie sous forme de fichier plat dans le dossier de sortie que vous avez sélectionnés pour le port d’envoi dans le module précédent.</span><span class="sxs-lookup"><span data-stu-id="252ef-105">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] writes the output as a flat file to the output folder that you selected for the send port in the previous module.</span></span>  
  
 <span data-ttu-id="252ef-106">Vous lancez le fichier de l’adaptateur de réception en copiant un fichier au format XML de SWIFT dans le dossier entrant.</span><span class="sxs-lookup"><span data-stu-id="252ef-106">You initiate the file receive adapter by copying a SWIFT XML-formatted file to the inbound folder.</span></span> <span data-ttu-id="252ef-107">Cette action entraîne le système copie un fichier plat SWIFT valid dans le dossier sortant.</span><span class="sxs-lookup"><span data-stu-id="252ef-107">This action results in the system copying a valid SWIFT flat file to the outbound folder.</span></span>  
  
### <a name="to-test-an-xml-instance"></a><span data-ttu-id="252ef-108">Pour tester une Instance XML</span><span class="sxs-lookup"><span data-stu-id="252ef-108">To test an XML Instance</span></span>  
  
1.  <span data-ttu-id="252ef-109">Dans l’Explorateur Windows, ouvrez \< *lecteur*\>: \Labs\Outbound.</span><span class="sxs-lookup"><span data-stu-id="252ef-109">In Windows Explorer, open \<*drive*\>:\Labs\Outbound.</span></span> <span data-ttu-id="252ef-110">Vérifiez que ce dossier contient le fichier {GUID} .xml que vous avez envoyé à ce dossier dans [leçon 1 : envoi d’un exemple de fichier plat](../../adapters-and-accelerators/accelerator-swift/lesson-1-submitting-a-sample-flat-file.md) de ce module.</span><span class="sxs-lookup"><span data-stu-id="252ef-110">Verify that this folder contains the {GUID}.xml file that you sent to this folder in [Lesson 1: Submitting a Sample Flat File](../../adapters-and-accelerators/accelerator-swift/lesson-1-submitting-a-sample-flat-file.md) of this module.</span></span>  
  
2.  <span data-ttu-id="252ef-111">Copiez le fichier XML et collez-le dans \< *lecteur*\>: \Labs\Inbound\XMLFile.</span><span class="sxs-lookup"><span data-stu-id="252ef-111">Copy the XML file, and paste it into \<*drive*\>:\Labs\Inbound\XMLFile.</span></span> <span data-ttu-id="252ef-112">Notez l’heure que vous avez collé à ce fichier.</span><span class="sxs-lookup"><span data-stu-id="252ef-112">Note the time that you pasted this file.</span></span>  
  
3.  <span data-ttu-id="252ef-113">Déplacer vers \< *lecteur*\>: \Labs\Outbound.</span><span class="sxs-lookup"><span data-stu-id="252ef-113">Move to \<*drive*\>:\Labs\Outbound.</span></span> <span data-ttu-id="252ef-114">Vérifiez qu’il existe un fichier appelé {GUID} .txt dans ce dossier, et que l’heure dans la colonne de Date de modification pour ce fichier correspond à l’heure que vous avez collé dans le fichier de \< *lecteur*\>: \Labs\Inbound\ XMLFile.</span><span class="sxs-lookup"><span data-stu-id="252ef-114">Verify that there is a file called {GUID}.txt in this folder, and that the time in the Date Modified column for this file corresponds to the time that you pasted the file into \<*drive*\>:\Labs\Inbound\XMLFile.</span></span>  
  
4.  <span data-ttu-id="252ef-115">Dans le bloc-notes, ouvrez MT103_Sample.txt dans \< *lecteur*\>: \Program Files\Microsoft BizTalk Accelerator pour SWIFT\SDK\Tutorial.</span><span class="sxs-lookup"><span data-stu-id="252ef-115">In Notepad, open MT103_Sample.txt in \<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial.</span></span>  
  
5.  <span data-ttu-id="252ef-116">Dans une autre instance du bloc-notes, ouvrez .txt {GUID} dans \< *lecteur*\>: \Labs\Inbound\XMLFile.</span><span class="sxs-lookup"><span data-stu-id="252ef-116">In another instance of Notepad, open {GUID}.txt in \<*drive*\>:\Labs\Inbound\XMLFile.</span></span>  
  
6.  <span data-ttu-id="252ef-117">Vérifiez que les deux fichiers dans le bloc-notes contiennent le même contenu.</span><span class="sxs-lookup"><span data-stu-id="252ef-117">Verify that the two files in Notepad contain the same content.</span></span>  
  
 <span data-ttu-id="252ef-118">Passez à [Module 8 : la réparation d’un Message non valide](http://msdn.microsoft.com/en-us/fb531b22-ac7a-4620-b395-87aebf56077d).</span><span class="sxs-lookup"><span data-stu-id="252ef-118">Proceed to [Module 8: Repairing an Invalid Message](http://msdn.microsoft.com/en-us/fb531b22-ac7a-4620-b395-87aebf56077d).</span></span>