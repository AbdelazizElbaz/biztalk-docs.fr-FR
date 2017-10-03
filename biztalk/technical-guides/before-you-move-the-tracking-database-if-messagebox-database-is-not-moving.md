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
# <a name="considerations-when-moving-the-tracking-database-if-the-messagebox-database-is-not-being-moved"></a><span data-ttu-id="e1d48-102">Considérations lors du déplacement de la base de données de suivi si la base de données MessageBox n’est pas déplacé</span><span class="sxs-lookup"><span data-stu-id="e1d48-102">Considerations When Moving the Tracking Database if the MessageBox Database Is Not Being Moved</span></span>
<span data-ttu-id="e1d48-103">Si vous déplacez la base de données de suivi, mais pas la base de données MessageBox, lorsque vous modifiez le fichier SampleUpdateInfo.xml, assurez-vous que vous incluez une entrée pour la base de données MessageBox, même si la base de données MessageBox n’est pas déplacé.</span><span class="sxs-lookup"><span data-stu-id="e1d48-103">If you are moving the Tracking database but not the MessageBox database, when you edit the SampleUpdateInfo.xml file, make sure that you include an entry for the MessageBox database as well, even though the MessageBox database is not being moved.</span></span> <span data-ttu-id="e1d48-104">Ceci doit être fait pour vous assurer que les [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] TrackedMessages_Copy_BizTalkMsgBoxDb est mis à jour avec l’emplacement de la nouvelle base de données de suivi de travail de l’Agent.</span><span class="sxs-lookup"><span data-stu-id="e1d48-104">This must be done to ensure that the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Agent job TrackedMessages_Copy_BizTalkMsgBoxDb is updated with the location of the new Tracking database.</span></span>  
  
 <span data-ttu-id="e1d48-105">Par exemple, dans le fichier SampleUpdateInfo.xml, uniquement la base de données de suivi est déplacé à partir de OldServer vers NewServer.</span><span class="sxs-lookup"><span data-stu-id="e1d48-105">For example, in the following SampleUpdateInfo.xml file, only the Tracking database is being moved from OldServer to NewServer.</span></span> <span data-ttu-id="e1d48-106">La base de données MessageBox respecte le OldServer :</span><span class="sxs-lookup"><span data-stu-id="e1d48-106">The MessageBox database is staying on OldServer:</span></span>  
  
```  
<UpdateConfiguration>  
     <MessageBoxDB oldDBName="BizTalkMgmtDb" oldDBServer="OldServer" newDBName="BizTalkMgmtDb" newDBServer="OldServer" IsMaster="1"/>  
     <TrackingDB oldDBName="BizTalkDTADB" oldDBServer="OldServer" newDBName="BizTalkDTADB" newDBServer="NewServer"/>  
     <OtherDatabases>  
     </OtherDatabases>  
</UpdateConfiguration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1d48-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1d48-107">See Also</span></span>  
 [<span data-ttu-id="e1d48-108">Déplacement de bases de données</span><span class="sxs-lookup"><span data-stu-id="e1d48-108">Moving Databases</span></span>](../technical-guides/moving-databases.md)