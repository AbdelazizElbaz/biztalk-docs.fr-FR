---
title: Maintenance BizTalk Serveur1 | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk Server, maintaining
ms.assetid: dd1e4497-839a-4686-b213-da100b6b5226
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e56d1cb915a91136058a6c1d4a670416903e8aef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="maintaining-biztalk-server1"></a><span data-ttu-id="1d23c-102">Mise à jour BizTalk Server1</span><span class="sxs-lookup"><span data-stu-id="1d23c-102">Maintaining BizTalk Server1</span></span>
<span data-ttu-id="1d23c-103">Cette section fournit des informations sur la sauvegarde et la restauration de BizTalk Server et des bases de données de Microsoft BizTalk Server, sur l'archivage et la purge des données de la base de données des suivis BizTalk (BizTalkDTADb) et sur le déplacement des bases de données BizTalk Server les plus susceptibles de faire l'objet d'un transfert.</span><span class="sxs-lookup"><span data-stu-id="1d23c-103">This section provides information about how to back up and restore BizTalk Server and the Microsoft BizTalk Server databases, how to archive and purge data from the BizTalk Tracking (BizTalkDTADb) database, and how to move some of the more commonly moved BizTalk Server databases.</span></span> <span data-ttu-id="1d23c-104">Elle fournit également une vue d'ensemble du processus de restauration et de sauvegarde ainsi que des recommandations relatives à la gestion de la base de données des suivis BizTalk.</span><span class="sxs-lookup"><span data-stu-id="1d23c-104">It provides an overview of the backup and restoration process, as well as recommendations for maintaining the BizTalk Tracking database.</span></span> <span data-ttu-id="1d23c-105">Elle fournit des informations sur la purge manuelle des données de la base de données MessageBox BizTalk dans un environnement de test.</span><span class="sxs-lookup"><span data-stu-id="1d23c-105">It provides information on manually purging data from the BizTalk MessageBox database in a test environment.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1d23c-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1d23c-106">In This Section</span></span>  
  
-   [<span data-ttu-id="1d23c-107">Sauvegarde et restauration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="1d23c-107">Backing Up and Restoring BizTalk Server</span></span>](../core/backing-up-and-restoring-biztalk-server.md)  
  
-   [<span data-ttu-id="1d23c-108">Archivage et purge de la base de données de suivi BizTalk</span><span class="sxs-lookup"><span data-stu-id="1d23c-108">Archiving and Purging the BizTalk Tracking Database</span></span>](../core/archiving-and-purging-the-biztalk-tracking-database.md)  
  
-   [<span data-ttu-id="1d23c-109">Déplacement de bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="1d23c-109">Moving BizTalk Server Databases</span></span>](../core/moving-biztalk-server-databases.md)  
  
-   [<span data-ttu-id="1d23c-110">Purge manuelle des données à partir de la base de données MessageBox dans un environnement de Test</span><span class="sxs-lookup"><span data-stu-id="1d23c-110">How to Manually Purge Data from the MessageBox Database in a Test Environment</span></span>](../core/how-to-manually-purge-data-from-the-messagebox-database-in-a-test-environment.md)