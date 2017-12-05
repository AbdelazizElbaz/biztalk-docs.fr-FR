---
title: "Préparation à l’utilisation de la Tutorial2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: end-to-end tutorial, pre-requisites
ms.assetid: 88e6c0b5-5f7d-4fee-a4de-7922cfba917f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8688e84f7913dbc32a0629d21f29ed2578c43b1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="preparing-to-use-the-tutorial"></a><span data-ttu-id="bc5b8-102">Préparation à l’utilisation du didacticiel</span><span class="sxs-lookup"><span data-stu-id="bc5b8-102">Preparing to Use the Tutorial</span></span>
<span data-ttu-id="bc5b8-103">Avant d’utiliser le didacticiel, vous devez créer un fichier ADT^A03.txt.</span><span class="sxs-lookup"><span data-stu-id="bc5b8-103">Before you use the tutorial, you need to create an ADT^A03.txt file.</span></span>  
  
### <a name="to-create-the-adta03txt-file"></a><span data-ttu-id="bc5b8-104">Pour créer le fichier ADT^A03.txt</span><span class="sxs-lookup"><span data-stu-id="bc5b8-104">To create the ADT^A03.txt file</span></span>  
  
1.  <span data-ttu-id="bc5b8-105">Ouvrir un éditeur tel que le bloc-notes et copiez le texte suivant dans l’éditeur :</span><span class="sxs-lookup"><span data-stu-id="bc5b8-105">Open an editor such as Notepad and copy the following text into the editor:</span></span>  
  
    ```  
    MSH|^~\&|Tutorial_ADTSystem|MCM|BTAHL7InterfaceEngine||199601121005||ADT^A03|000001|P|2.3.1  
    EVN|A03|199601121005||01||199601121000  
    PID|||191919^^^MYHOS^MR~123-45-6789^^^USSSA^SS|253763|SMITH^JOHN^Q||19560129|M|||  
        123MAIN^^BUFFALO^NY^98052^""||(123)555-0100||S|M|10199925^^^MYHOS^AN|123-45-6789  
    PD1|S|F|NormalString^A^+1^-1^ISO^simpletext&Test&HCD^GI^simpletext&NormalString&ISO^I|  
       NormalString^Test&Test^Test^Test^Test^Test^AE^simpletext^simpletext&Test&ISO^P  
       ^NormalString^M10^MC^simpletext&NormalString&HCD^A|N|simpletext|I|I|N|NormalString  
       ^+1^M11^simpletext&NormalString&L,M,N^RRI^simpletext&NormalString&HCD|NOVALUE^NormalString  
       ^Test^Test^NormalString^Test|N  
    PV1|1|I|2000^2012^01^hey&test&DNS^test^test^test^test^test||||004777^MILLER^CONNIE^A.|||SUR||||2|A0  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="bc5b8-106">Il doit y avoir cinq lignes dans le .txt un fichier, chacune commençant par « MSH », « EVN », « Ci », « PD1 » et « PV1 ».</span><span class="sxs-lookup"><span data-stu-id="bc5b8-106">There should be five lines in the .txt file, one each starting with "MSH", "EVN", "PID", "PD1", and "PV1".</span></span> <span data-ttu-id="bc5b8-107">Vous devez supprimer les espaces dans la ligne « Ci » et la ligne « PD1 ».</span><span class="sxs-lookup"><span data-stu-id="bc5b8-107">You will need to remove the spaces within the "PID" line and the "PD1" line.</span></span> <span data-ttu-id="bc5b8-108">Si nécessaire, désactivez le retour automatique à la ligne dans le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="bc5b8-108">If necessary, turn off word wrap in Notepad.</span></span>  
  
2.  <span data-ttu-id="bc5b8-109">Enregistrez le fichier sous **ADT^A03.txt** dans les \< *lecteur*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator pour le dossier Tutorial de bout en HL7\SDK\End, puis fermez le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="bc5b8-109">Save the file as **ADT^A03.txt** in the \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial folder, and then close Notepad.</span></span>  
  
 <span data-ttu-id="bc5b8-110">Passez à [étape 1 : créer et déployer des schémas d’en-tête et d’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/step-1-create-and-deploy-header-and-acknowledgment-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="bc5b8-110">Proceed to [Step 1: Create and Deploy Header and Acknowledgment Schemas](../../adapters-and-accelerators/accelerator-hl7/step-1-create-and-deploy-header-and-acknowledgment-schemas.md).</span></span>