---
title: Exemple de FileTransport | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a32c8cbf-0c17-4237-b2a3-9d21faa13496
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 495e4cfe4c9c9b9d7ae16ee58f7831ad5447d37b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="filetransport-sample"></a>Exemple de FileTransport
L’exemple FileTransport montre comment configurer [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] d’utiliser des ports de fichier, au lieu des ports SQL. L’exemple FileTransport utilise le Transport FTP (File Protocol) pour envoyer et recevoir des messages, au lieu de HTTP.  
  
> [!NOTE]
>  Ce document suppose que vous installez [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] test ou démonstration à usage interne uniquement. Il ne pas prescrire n’importe quel compte de sécurité minimale ou configuration. Vous devez utiliser un compte qui dispose des autorisations d’administrateur local dans les procédures décrites dans cette rubrique.  
  
> [!NOTE]
>  Cet exemple ne prend pas en charge les pièces jointes de message.  
  
## <a name="filetransport-binding-files"></a>Fichiers de liaison FileTransport  
 L’exemple de FileTransport inclut deux fichiers de liaison. Vous pouvez utiliser chacun de ces fichiers de liaison à configurer des ports de fichier pour une utilisation avec une orchestration BTARN. Ces fichiers de liaison se trouvent dans  *\<lecteur >*: \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet \SDK\FileTransport. Ouvrez chaque fichier de liaison dans un éditeur tel que le bloc-notes pour afficher les paramètres de l’orchestration, port d’envoi, port de réception et emplacement de réception, comme indiqué ci-dessous.  
  
-   PrivateInitiatorusingFileDrops.xml  
  
    -   Orchestration : Microsoft.Solutions.BTARN.PrivateInitiator.PrivateInitiatorProcess  
  
    -   Port d’envoi : PrivateInitiator_To_File  
  
    -   Port de réception : File_To_PrivateInitiator  
  
    -   Emplacement de réception : File_To_PrivateInitiator  
  
-   PrivateResponderusingFileDrops.xml  
  
    -   Orchestration : Microsoft.Solutions.BTARN.PrivateResponder.PrivateResponderProcess  
  
    -   Port d’envoi : PrivateResponder_To_File  
  
    -   Port de réception : File_To_PrivateResponder  
  
    -   Emplacement de réception : File_To_PrivateResponder  
  
 La procédure suivante décrit comment importer les liaisons à partir des fichiers de liaison à l’aide de la commande BTSTask. Pour plus d’informations, consultez la rubrique « Commande ImportBindings » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-set-up-btarn-by-using-file-drop-folders"></a>Pour configurer BTARN à l’aide de dossiers de dépôt de fichiers  
  
1.  Ouvrez l’Explorateur BizTalk.  
  
2.  Arrêtez les deux ports d’envoi SQL de LOB, PrivateInitiator_To_LOB et PrivateResponder_To_LOB.  
  
3.  Désactivez les deux Lob SQL Receive ports, LOB_To_PrivateInitiator et LOB_To_PrivateResponder.  
  
4.  Désinscrire Microsoft.Solutions.BTARN.PrivateResponder.PrivateResponderProcess.  
  
5.  Désinscrire Microsoft.Solutions.BTARN.PrivateInitiator.PrivateInitiatatorProcess.  
  
6.  Créez un dossier \FileDrops sous le dossier BTARN de C:\Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet, puis créer la structure de dossiers suivante sous \FileDrops :  
  
    -   \PrivateInitiator  
  
         \FromLOB  
  
         \ToLOB  
  
    -   \PrivateResponder  
  
         \FromLOB  
  
         \ToLOB  
  
7.  Exécutez la commande suivante (en supposant que BTARN est installé sur le lecteur C:) :  
  
    ```  
    BTSTask ImportBindings /Source:C:\Program Files\Microsoft BizTalk <version> Accelerator for RosettaNet\SDK\FileTransport\PrivateInitiatorusingFileDrops.xml  
    ```  
  
8.  Exécutez la commande suivante (en supposant que BTARN est installé sur le lecteur C:) :  
  
    ```  
    BTSTask ImportBindings /Source:C:\Program Files\Microsoft BizTalk <version> Accelerator for RosettaNet\SDK\FileTransport\PrivateResponderusingFileDrops.xml  
    ```  
  
9. Démarrer les ports d’envoi : PrivateInitiator_To_File et PrivateResponder_To_File.  
  
10. Activer les ports de réception : LOB_To_PrivateInitiator et LOB_To_PrivateResponder.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de messagerie](../../adapters-and-accelerators/accelerator-rosettanet/messaging-samples.md)