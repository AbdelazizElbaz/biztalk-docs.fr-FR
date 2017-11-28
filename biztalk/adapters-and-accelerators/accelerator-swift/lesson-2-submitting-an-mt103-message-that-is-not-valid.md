---
title: "Leçon 2 : Envoi d’un Message MT103 qui n’est pas valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, invalid messages
- submitting, invalid messages
- submitting, MT103 messages
- MT103 messages
- messages, MT103 messages
ms.assetid: 4b070ae1-c400-421a-b2f6-b7b1f22c0e41
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1968549cb2417a180ee69dff82f233c43a40318c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-2-submitting-an-mt103-message-that-is-not-valid"></a><span data-ttu-id="111db-102">Leçon 2 : Envoi d’un Message MT103 qui n’est pas valide</span><span class="sxs-lookup"><span data-stu-id="111db-102">Lesson 2: Submitting an MT103 Message That Is Not Valid</span></span>
<span data-ttu-id="111db-103">Dans cette leçon, vous envoyez un message MT103 qui n’est pas valide, et puis vous résolvez l’erreur obtenu à l’aide des outils de votre système.</span><span class="sxs-lookup"><span data-stu-id="111db-103">In this lesson, you submit an MT103 message that is not valid and then you troubleshoot the resulting error using your System Tools.</span></span>  
  
### <a name="to-submit-an-mt103-message-that-is-not-valid"></a><span data-ttu-id="111db-104">Pour envoyer un message MT103 qui n’est pas valide</span><span class="sxs-lookup"><span data-stu-id="111db-104">To submit an MT103 message that is not valid</span></span>  
  
1.  <span data-ttu-id="111db-105">Copiez le fichier MT103_Invalid_Sample.txt à partir de \< *lecteur :*> \Program Files\Microsoft BizTalk Accelerator pour SWIFT\SDK\Tutorial à \< *lecteur*> : \Labs\Inbound\ FlatFile dossier.</span><span class="sxs-lookup"><span data-stu-id="111db-105">Copy the file MT103_Invalid_Sample.txt from \<*drive:*>\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial to \<*drive*>:\Labs\Inbound\FlatFile folder.</span></span> <span data-ttu-id="111db-106">Notez l’heure que vous déposez le fichier dans le dossier.</span><span class="sxs-lookup"><span data-stu-id="111db-106">Note the time that you drop the file into the folder.</span></span>  
  
2.  <span data-ttu-id="111db-107">Ouvrez \< *lecteur :*> \Labs\Outbound pour vérifier qu’aucun fichier XML correspondant à MT103_Invalid_Sample.txt n’est dans le dossier.</span><span class="sxs-lookup"><span data-stu-id="111db-107">Open \<*drive:*>\Labs\Outbound to verify that no XML file corresponding to MT103_Invalid_Sample.txt is in the folder.</span></span> <span data-ttu-id="111db-108">(Le fichier XML correspondant au message MT103_Sample.txt valid doit toujours figurer dans ce dossier.)</span><span class="sxs-lookup"><span data-stu-id="111db-108">(The XML file corresponding to the valid MT103_Sample.txt message should still be in that folder.)</span></span>  
  
3.  <span data-ttu-id="111db-109">Dans le bloc-notes, ouvrez le fichier MT103_Invalid_Sample.txt dans \< *lecteur :*> \Program Files\Microsoft BizTalk Accelerator pour SWIFT\SDK\Tutorial.</span><span class="sxs-lookup"><span data-stu-id="111db-109">In Notepad, open the file MT103_Invalid_Sample.txt in \<*drive:*>\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial.</span></span>  
  
4.  <span data-ttu-id="111db-110">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="111db-110">Start **BizTalk Server Administration**.</span></span>  
  
5.  <span data-ttu-id="111db-111">Dans la Console Administration de BizTalk Server, développez **l’Observateur d’événements (Local)**, puis cliquez sur **Application**.</span><span class="sxs-lookup"><span data-stu-id="111db-111">In the BizTalk Server Administration Console, expand **Event Viewer (Local)**, and then click **Application**.</span></span>  
  
6.  <span data-ttu-id="111db-112">Recherchez une entrée d’erreur qui a une source de BizTalk Accelerator pour SWIFT et une heure qui correspond à lorsque vous déposez le message non valide dans le \< *lecteur*> : \Labs\Inbound\FlatFile dossier.</span><span class="sxs-lookup"><span data-stu-id="111db-112">Look for an error entry that has a source of BizTalk Accelerator for SWIFT and a time that corresponds to when you dropped the invalid message into the \<*drive*>:\Labs\Inbound\FlatFile folder.</span></span> <span data-ttu-id="111db-113">Double-cliquez sur cette entrée de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="111db-113">Double-click that error entry.</span></span>  
  
7.  <span data-ttu-id="111db-114">Dans la boîte de dialogue Propriétés de l’événement de l’erreur, vérifiez dans le volet Description que le message ayant échoué a été publié dans la MessageBox et le désassembleur SWIFT marqué **A4SWIFT_Failed** en tant que **True**.</span><span class="sxs-lookup"><span data-stu-id="111db-114">In the Event Properties dialog box for the error, verify in the Description pane that the failed message was published to the MessageBox and that the SWIFT Disassembler marked **A4SWIFT_Failed** as **True**.</span></span> <span data-ttu-id="111db-115">Fermez la boîte de dialogue Propriétés de l’événement.</span><span class="sxs-lookup"><span data-stu-id="111db-115">Close the Event Properties dialog box.</span></span>  
  
8.  <span data-ttu-id="111db-116">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, puis développez **groupe BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="111db-116">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, and then expand **BizTalk Group**.</span></span> <span data-ttu-id="111db-117">Dans le **vue** menu, cliquez sur **Page Hub du groupe**.</span><span class="sxs-lookup"><span data-stu-id="111db-117">In the **View** menu, click **Group Hub Page**.</span></span>  
  
9. <span data-ttu-id="111db-118">Dans le **vue d’ensemble du groupe** volet, dans le **Instances de Service suspendues groupées** volet, cliquez sur **regroupés par Application**.</span><span class="sxs-lookup"><span data-stu-id="111db-118">In the **Group Overview** pane, in the **Grouped Suspended Service Instances** pane, click **Grouped by Application**.</span></span>  
  
10. <span data-ttu-id="111db-119">Dans le **Aperçu pour le résultat de la requête sélectionnée** volet, double-cliquez sur l’entrée **MT103_FlatFile_ReceivePort**.</span><span class="sxs-lookup"><span data-stu-id="111db-119">In the **Preview for the selected query result** pane, double-click the entry for **MT103_FlatFile_ReceivePort**.</span></span>  
  
11. <span data-ttu-id="111db-120">Dans la boîte de dialogue Détails du Service, cliquez sur le **Messages** onglet. Double-cliquez sur l’entrée dont le nom du Service est **MT103_FlatFile_ReceivePort**.</span><span class="sxs-lookup"><span data-stu-id="111db-120">In the Service Details dialog box, click the **Messages** tab. Double-click the entry for which the Service Name is **MT103_FlatFile_ReceivePort**.</span></span>  
  
12. <span data-ttu-id="111db-121">Dans la boîte de dialogue Détails du Message, cliquez sur **corps** dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="111db-121">In the Message Details dialog box, click **Body** in the left pane.</span></span>  
  
13. <span data-ttu-id="111db-122">Vérifiez que le message affiché dans le volet de corps de la boîte de dialogue Détails du Message correspond au MT103_Invalid_Sample.txt que vous avez ouvert dans le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="111db-122">Verify that the message displayed in the body pane of the Message Details dialog box corresponds to MT103_Invalid_Sample.txt that you opened in Notepad.</span></span>  
  
 <span data-ttu-id="111db-123">Passez à [leçon 3 : test d’une Instance XML](../../adapters-and-accelerators/accelerator-swift/lesson-3-testing-an-xml-instance.md).</span><span class="sxs-lookup"><span data-stu-id="111db-123">Proceed to [Lesson 3: Testing an XML Instance](../../adapters-and-accelerators/accelerator-swift/lesson-3-testing-an-xml-instance.md).</span></span>