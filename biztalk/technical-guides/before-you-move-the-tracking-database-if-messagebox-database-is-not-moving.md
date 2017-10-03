---
title: "Considérations lors du déplacement de la base de données de suivi si la base de données MessageBox n’est pas déplacé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee4066cb-da5b-4d04-a3b8-23fbf2d0c92a
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ecb2fcb6ad9ead42bd3e09c84a8895758d82293f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-when-moving-the-tracking-database-if-the-messagebox-database-is-not-being-moved"></a>Considérations lors du déplacement de la base de données de suivi si la base de données MessageBox n’est pas déplacé
Si vous déplacez la base de données de suivi, mais pas la base de données MessageBox, lorsque vous modifiez le fichier SampleUpdateInfo.xml, assurez-vous que vous incluez une entrée pour la base de données MessageBox, même si la base de données MessageBox n’est pas déplacé. Ceci doit être fait pour vous assurer que les [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] TrackedMessages_Copy_BizTalkMsgBoxDb est mis à jour avec l’emplacement de la nouvelle base de données de suivi de travail de l’Agent.  
  
 Par exemple, dans le fichier SampleUpdateInfo.xml, uniquement la base de données de suivi est déplacé à partir de OldServer vers NewServer. La base de données MessageBox respecte le OldServer :  
  
```  
<UpdateConfiguration>  
     <MessageBoxDB oldDBName="BizTalkMgmtDb" oldDBServer="OldServer" newDBName="BizTalkMgmtDb" newDBServer="OldServer" IsMaster="1"/>  
     <TrackingDB oldDBName="BizTalkDTADB" oldDBServer="OldServer" newDBName="BizTalkDTADB" newDBServer="NewServer"/>  
     <OtherDatabases>  
     </OtherDatabases>  
</UpdateConfiguration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Déplacement de bases de données](../technical-guides/moving-databases.md)