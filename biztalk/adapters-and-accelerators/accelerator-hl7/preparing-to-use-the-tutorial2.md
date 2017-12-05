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
# <a name="preparing-to-use-the-tutorial"></a>Préparation à l’utilisation du didacticiel
Avant d’utiliser le didacticiel, vous devez créer un fichier ADT^A03.txt.  
  
### <a name="to-create-the-adta03txt-file"></a>Pour créer le fichier ADT^A03.txt  
  
1.  Ouvrir un éditeur tel que le bloc-notes et copiez le texte suivant dans l’éditeur :  
  
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
    >  Il doit y avoir cinq lignes dans le .txt un fichier, chacune commençant par « MSH », « EVN », « Ci », « PD1 » et « PV1 ». Vous devez supprimer les espaces dans la ligne « Ci » et la ligne « PD1 ». Si nécessaire, désactivez le retour automatique à la ligne dans le bloc-notes.  
  
2.  Enregistrez le fichier sous **ADT^A03.txt** dans les \< *lecteur*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator pour le dossier Tutorial de bout en HL7\SDK\End, puis fermez le bloc-notes.  
  
 Passez à [étape 1 : créer et déployer des schémas d’en-tête et d’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/step-1-create-and-deploy-header-and-acknowledgment-schemas.md).