---
title: "Créer le fichier QRY^Q01.txt | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ac96587-264f-4743-a90b-4763d330e320
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b3bc9de81259ba71547e3fb887e91872e9e549c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="create-the-qryq01txt-file"></a>Créer le fichier QRY^Q01.txt
Utilisez la procédure suivante pour créer le fichier de message de requête patient QRY^Q01.txt. Vous utiliserez ce fichier ultérieurement pour vérifier le scénario du didacticiel.  
  
### <a name="to-create-the-qryq01txt-file"></a>Pour créer le fichier QRY^Q01.txt  
  
1.  Ouvrez un éditeur, tel que le bloc-notes et copiez le texte suivant dans l’éditeur :  
  
    ```  
    MSH|^~\&|ADT||HIS||19990303||QRY^Q01|MSG00001|P|2.4  
    QRD|200307231012|D|I|4387|||20^LI|12233|RES|ALL  
    ```  
  
2.  Enregistrez le fichier sous **QRY^Q01.txt** dans les \< *lecteur*:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\ Dossier Tutorial interrogative et fermez l’éditeur.  
  
 Passez à [créer le fichier DSR.txt](../../adapters-and-accelerators/accelerator-hl7/create-the-dsr-txt-file.md).