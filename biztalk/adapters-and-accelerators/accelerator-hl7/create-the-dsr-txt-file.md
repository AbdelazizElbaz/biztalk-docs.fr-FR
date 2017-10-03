---
title: "Créer le fichier DSR.txt | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6947af7-c5ce-4ee6-9fe9-5c1094d0aee0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eef9f107b01c8e86d466cb1fb0a202e1aa5b0b54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-the-dsrtxt-file"></a><span data-ttu-id="74b9e-102">Créer le fichier DSR.txt</span><span class="sxs-lookup"><span data-stu-id="74b9e-102">Create the DSR.txt File</span></span>
<span data-ttu-id="74b9e-103">Utilisez la procédure suivante pour créer le fichier de message de réponse DSR.txt.</span><span class="sxs-lookup"><span data-stu-id="74b9e-103">Use the following procedure to create the response DSR.txt message file.</span></span> <span data-ttu-id="74b9e-104">Vous utiliserez ce fichier ultérieurement pour vérifier le scénario du didacticiel.</span><span class="sxs-lookup"><span data-stu-id="74b9e-104">You will use this file later to verify the tutorial scenario.</span></span>  
  
### <a name="to-create-the-dsrtxt-file"></a><span data-ttu-id="74b9e-105">Pour créer le fichier DSR.txt</span><span class="sxs-lookup"><span data-stu-id="74b9e-105">To create the DSR.txt file</span></span>  
  
1.  <span data-ttu-id="74b9e-106">Ouvrez un éditeur, tel que le bloc-notes et copiez le texte suivant dans l’éditeur :</span><span class="sxs-lookup"><span data-stu-id="74b9e-106">Open an editor, such as Notepad, and copy the following text into the editor:</span></span>  
  
    ```  
    MSH|^~\&|HIS||ADT||19990505||DSR^Q01|ZXT23469|P|2.4  
    MSA|AA|MSG00003  
    QRD|200307231012|D|I|4387|||20^LI|12233|RES|ALL  
    DSP|||RESULTS FOR PATIENT#12233 SMITH, JOHN H. 07/23/03  
    DSP|||SPECIMEN#H85 COLLECTED 07/22/03 /07/0/0  
    DSP|||ELECTROLYTES  
    DSP||| SODIUM 136 [135-148] MEQ/L STAT  
    DSP||| POTASSIUM 4.2 [3.5-5.0] MEQ/L STAT  
    DSP||| CHLORIDE 91 [95-111] MEQ/L STAT  
    DSP||| CO2 25 [20-30] MEQ/L STAT  
    DSP|||CO2 25 [20-30] MEQ/L STAT|LB  
    ```  
  
2.  <span data-ttu-id="74b9e-107">Enregistrez le fichier sous **DSR.txt** dans les \< *lecteur*: > \Program Files\Microsoft BizTalk \<version > Accelerator pour le dossier du didacticiel de HL7\SDK\Interrogative et fermez l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="74b9e-107">Save the file as **DSR.txt** in the \<*drive*:>\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\SDK\Interrogative Tutorial folder, and then close the editor.</span></span>  
  
 <span data-ttu-id="74b9e-108">Passez à [étape 1 : créer et déployer en-tête commun et schémas d’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/step-1-create-and-deploy-common-header-and-acknowledgment-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="74b9e-108">Proceed to [Step 1: Create and Deploy Common Header and Acknowledgment Schemas](../../adapters-and-accelerators/accelerator-hl7/step-1-create-and-deploy-common-header-and-acknowledgment-schemas.md).</span></span>