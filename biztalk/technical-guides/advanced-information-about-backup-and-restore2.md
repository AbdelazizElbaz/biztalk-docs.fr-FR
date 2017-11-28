---
title: "Informations sur la sauvegarde et Restore2 avancées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa6a3527-4889-40ae-aacb-b8ea75be0329
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6991e417afaee807d999f7123f7a853dbd955eb3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="advanced-information-about-backup-and-restore"></a><span data-ttu-id="33bbf-102">Informations avancées sur la sauvegarde et la restauration</span><span class="sxs-lookup"><span data-stu-id="33bbf-102">Advanced Information About Backup and Restore</span></span>
<span data-ttu-id="33bbf-103">Les rubriques suivantes décrivent la sauvegarde et le processus de restauration plus décrit en détail et sont destinées à être utilisées par les utilisateurs expérimentés qui ont une connaissance approfondie de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="33bbf-103">The topics listed here describe the backup and restore processes in more detail and are intended to be used by advanced users with a thorough understanding of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="33bbf-104">Pour plus d’informations sur la transaction marquée, des sauvegardes complètes et des journaux, consultez [les Transactions marquées, sauvegardes complètes et sauvegardes de journaux](http://go.microsoft.com/fwlink/?LinkId=151565) (http://go.microsoft.com/fwlink/?LinkId=151565).</span><span class="sxs-lookup"><span data-stu-id="33bbf-104">For information about marked transaction, full backups, and logs, see [Marked Transactions, Full Backups, and Log Backups](http://go.microsoft.com/fwlink/?LinkId=151565) (http://go.microsoft.com/fwlink/?LinkId=151565).</span></span>  
  
-   <span data-ttu-id="33bbf-105">Pour plus d’informations sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoi de journaux, consultez [l’envoi de journaux BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=151566) (http://go.microsoft.com/fwlink/?LinkId=151566).</span><span class="sxs-lookup"><span data-stu-id="33bbf-105">For information about [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping, see [BizTalk Server Log Shipping](http://go.microsoft.com/fwlink/?LinkId=151566) (http://go.microsoft.com/fwlink/?LinkId=151566).</span></span>  
  
-   <span data-ttu-id="33bbf-106">Pour plus d’informations sur la planification de sauvegarde [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de la tâche, consultez [comment planifier le travail de sauvegarde BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=151568) (http://go.microsoft.com/fwlink/?LinkId=151568).</span><span class="sxs-lookup"><span data-stu-id="33bbf-106">For information about scheduling backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job, see [How to Schedule the Backup BizTalk Server Job](http://go.microsoft.com/fwlink/?LinkId=151568) (http://go.microsoft.com/fwlink/?LinkId=151568).</span></span>  
  
-   <span data-ttu-id="33bbf-107">Pour plus d’informations sur la sauvegarde des bases de données personnalisées, consultez [comment dans des bases de données personnalisées](http://go.microsoft.com/fwlink/?LinkId=151569) (http://go.microsoft.com/fwlink/?LinkId=151569).</span><span class="sxs-lookup"><span data-stu-id="33bbf-107">For information about backing up custom databases, see [How to Back Up Custom Databases](http://go.microsoft.com/fwlink/?LinkId=151569) (http://go.microsoft.com/fwlink/?LinkId=151569).</span></span>  
  
-   <span data-ttu-id="33bbf-108">Pour plus d’informations sur la création d’un serveur lié, consultez [la création d’un serveur lié](http://go.microsoft.com/fwlink/?LinkId=151570) (http://go.microsoft.com/fwlink/?LinkId=151570).</span><span class="sxs-lookup"><span data-stu-id="33bbf-108">For information about creating a linked server, see [How to Create a Linked Server](http://go.microsoft.com/fwlink/?LinkId=151570) (http://go.microsoft.com/fwlink/?LinkId=151570).</span></span>  
  
-   <span data-ttu-id="33bbf-109">Pour plus d’informations sur l’affichage de l’historique des sauvegardes restaurées, consultez [affichage de l’historique de sauvegardes restaurées](http://go.microsoft.com/fwlink/?LinkId=151572) (http://go.microsoft.com/fwlink/?LinkId=151572).</span><span class="sxs-lookup"><span data-stu-id="33bbf-109">For information about viewing the history of restored backups, see [Viewing the History of Restored Backups](http://go.microsoft.com/fwlink/?LinkId=151572) (http://go.microsoft.com/fwlink/?LinkId=151572).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="33bbf-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="33bbf-110">In This Section</span></span>  
  
-   [<span data-ttu-id="33bbf-111">BizTalk Server journaux de transaction à l’aide de l’adresse IP et un nom de Cluster Windows</span><span class="sxs-lookup"><span data-stu-id="33bbf-111">BizTalk Server Log Shipping Using a Windows Cluster Name and IP Address</span></span>](../technical-guides/biztalk-server-log-shipping-using-a-windows-cluster-name-and-ip-address.md)  
  
-   [<span data-ttu-id="33bbf-112">Restauration de Production à partir d’une sauvegarde à chaud</span><span class="sxs-lookup"><span data-stu-id="33bbf-112">Restoring Production from a Warm Backup</span></span>](../technical-guides/restoring-production-from-a-warm-backup.md)