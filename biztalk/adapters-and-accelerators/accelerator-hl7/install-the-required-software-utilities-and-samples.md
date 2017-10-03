---
title: Installer les logiciels requis, les utilitaires et les exemples | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de0cb89d-08bd-48ec-a149-8929e2608df8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 678037cd050ae8375b3c9ec465860d939d48cccc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="install-the-required-software-utilities-and-samples"></a>Installer les logiciels requis, les utilitaires et les exemples
Ce didacticiel nécessite [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Windows Server et personnalisé [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] installation qui inclut les outils de Test MLLP. En outre, vous devez être familiarisé avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] développement dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)] et [Découvrez l’accélérateur HL7 et les outils BizTalk disponibles](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md).
  
 Vous devez les utilitaires et les exemples installés sur votre ordinateur suivants :  
  
-   **Outil de MllpSend**  
  
     Cet utilitaire de ligne de commande envoie un message via le protocole de couche inférieure (MLLP) minimale emplacement de réception du protocole à un MLLP. Il permet de tester vos résultats de didacticiel. Pour plus d’informations, consultez [MllpSend outil](../../adapters-and-accelerators/accelerator-hl7/mllpsend-tool.md).  
  
-   **Outil de MllpPReceive**  
  
     Cet utilitaire de ligne de commande reçoit des messages via le protocole MLLP, agissant comme un écouteur de l’emplacement de réception. Il permet de tester vos résultats du didacticiels, l’affichage des messages et les accusés de réception reçus. Pour plus d’informations, consultez [MllpReceive outil](../../adapters-and-accelerators/accelerator-hl7/mllpreceive-tool.md).  
  
-   **Exemple d’Application accepter ACK.txt**  
  
     Cet exemple de fichier contient le texte d’une application-accepter le message d’accusé de réception. L’exemple fonctionne avec l’outil MllpReceive, qui reçoit et affiche des messages, puis envoie l’acknowledgment(s) dans l’exemple de fichier.  
  
 Vous devez installer les outils et l’exemple de fichier à l’aide du processus d’installation personnalisée de BTAHL7. Le processus d’installation par défaut n’installe pas ces outils. Pour installer ces outils, exécutez l’installation personnalisée de BTAHL7, à la **le programme d’installation personnalisé** écran, sélectionnez **outil de Test MLLP** à partir de la **adaptateur** dossier, puis sélectionnez **Instances test** à partir de la **artefacts** dossier. Pour plus d’informations, consultez [installer BizTalk Accelerator pour HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Préparation à l’utilisation du didacticiel de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-batching-tutorial.md)