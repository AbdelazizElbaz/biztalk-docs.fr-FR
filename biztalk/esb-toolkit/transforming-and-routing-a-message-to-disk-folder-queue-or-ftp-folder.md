---
title: "Transformer et acheminer les messages vers le dossier de disque, de file d’attente ou de dossier FTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5bfdbc38-6663-4d95-a0ed-57fec0245b9f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dcbc9d42fbed5dfd73aee910ba2e1a40da595658
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="transforming-and-routing-a-message-to-disk-folder-queue-or-ftp-folder"></a>Transformer et acheminer les messages vers le dossier de disque, de file d’attente ou de dossier FTP
Dans ce cas de figure, l’architecture ESB transforme un message envoyé via le service Web de la feuille de route ou toute rampe d’entrée. Une recherche de résolution dynamique de type FILE, FTP ni d’emplacement de la file d’attente détermine le nom de mappage (pour la transformation) et le point de terminaison cible pour le message, comme illustré dans la Figure 1.  
  
 ![Transformation de dossier de disque](../esb-toolkit/media/ch3-transformingdiskfolder.gif "Ch3-TransformingDiskFolder")  
  
 **Figure 1**  
  
 **Transformer et acheminer les messages vers un dossier de disque**  
  
 L’exemple de résolution dynamique fourni avec [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure. Il montre comment utiliser les composants de dynamiquement résoudre l’emplacement du point de terminaison, définir des propriétés de routage et résoudre et exécuter des mappages BizTalk Server au niveau de la messagerie, sans l’aide d’une orchestration. Il montre également les modèles de messagerie unidirectionnels ou bidirectionnels.  
  
 Une extension de ce cas de figure est une solution de routage simple qui achemine un message entrant à un fichier, FTP ou emplacement de la file d’attente sans cette étape supplémentaire de transformation.  
  
 Pour plus d’informations, consultez [l’installation et l’exécution de l’exemple de résolution dynamique](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md).