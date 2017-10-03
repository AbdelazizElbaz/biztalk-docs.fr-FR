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
ms.openlocfilehash: 57380a36759d9cf0139f295779b8e1f2628c554f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-the-qryq01txt-file"></a>Créer le fichier QRY^Q01.txt
Utilisez la procédure suivante pour créer le fichier de message de requête patient QRY^Q01.txt. Vous utiliserez ce fichier ultérieurement pour vérifier le scénario du didacticiel.  
  
### <a name="to-create-the-qryq01txt-file"></a>Pour créer le fichier QRY^Q01.txt  
  
1.  Ouvrez un éditeur, tel que le bloc-notes et copiez le texte suivant dans l’éditeur :  
  
    ```  
    MSH|^~\&|ADT||HIS||19990303||QRY^Q01|MSG00001|P|2.4  
    QRD|200307231012|D|I|4387|||20^LI|12233|RES|ALL  
    ```  
  
2.  Enregistrez le fichier sous **QRY^Q01.txt** dans les \< *lecteur*: > \Program Files\Microsoft BizTalk \<version > Accelerator pour le dossier du didacticiel de HL7\SDK\Interrogative, puis Fermez l’éditeur.  
  
 Passez à [créer le fichier DSR.txt](../../adapters-and-accelerators/accelerator-hl7/create-the-dsr-txt-file.md).