---
title: "Optimisation des performances de la base de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a95caf60-f1f5-458f-8a81-0aead88f07be
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe9148c5b14c5c915de9a8d16699856922e051a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-database-performance"></a><span data-ttu-id="86f5f-102">Optimisation des performances de la base de données</span><span class="sxs-lookup"><span data-stu-id="86f5f-102">Optimizing Database Performance</span></span>
<span data-ttu-id="86f5f-103">BizTalk Server est une application de beaucoup de ressources de base de données qui peut nécessiter la création de bases de données jusqu'à 13 dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="86f5f-103">BizTalk Server is an extremely database-intensive application that may require the creation of up to 13 databases in SQL Server.</span></span> <span data-ttu-id="86f5f-104">Étant un des principaux objectifs de création de BizTalk Server pour vous assurer qu’aucun message n’est perdu, BizTalk Server conserve les données sur le disque avec une fréquence élevée et en outre, le fait dans le contexte d’une transaction MSDTC.</span><span class="sxs-lookup"><span data-stu-id="86f5f-104">Because one of the primary design goals of BizTalk Server is to ensure that no messages are lost, BizTalk Server persists data to disk with great frequency and furthermore, does so within the context of an MSDTC transaction.</span></span> <span data-ttu-id="86f5f-105">Par conséquent, les performances de la base de données est primordiale pour les performances globales d’une solution BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="86f5f-105">Therefore, database performance is paramount to the overall performance of any BizTalk Server solution.</span></span>  
  
 <span data-ttu-id="86f5f-106">Cette section décrit les méthodes générales pour optimiser les performances de SQL Server, ainsi que des méthodes pour optimiser les performances de la base de données qui sont spécifiques à un environnement BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="86f5f-106">This section describes general methods for maximizing SQL Server performance as well as methods for maximizing database performance that are specific to a BizTalk Server environment.</span></span> <span data-ttu-id="86f5f-107">Pour plus d’informations sur l’optimisation des performances de base de données BizTalk, consultez le [livre blanc sur l’optimisation de base de données BizTalk](http://go.microsoft.com/fwlink/?LinkId=101578) (http://go.microsoft.com/fwlink/?LinkId=101578).</span><span class="sxs-lookup"><span data-stu-id="86f5f-107">For additional information about optimizing BizTalk database performance, see the [BizTalk Database Optimization whitepaper](http://go.microsoft.com/fwlink/?LinkId=101578) (http://go.microsoft.com/fwlink/?LinkId=101578).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="86f5f-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="86f5f-108">In This Section</span></span>  
  
-   [<span data-ttu-id="86f5f-109">Base de données de la Configuration préalable Optimizations2</span><span class="sxs-lookup"><span data-stu-id="86f5f-109">Pre-Configuration Database Optimizations2</span></span>](../technical-guides/pre-configuration-database-optimizations2.md)  
  
-   [<span data-ttu-id="86f5f-110">À la Configuration de base de données Optimizations2</span><span class="sxs-lookup"><span data-stu-id="86f5f-110">Post-Configuration Database Optimizations2</span></span>](../technical-guides/post-configuration-database-optimizations2.md)  
  
-   [<span data-ttu-id="86f5f-111">Optimisation des groupes de fichiers pour le Databases2</span><span class="sxs-lookup"><span data-stu-id="86f5f-111">Optimizing Filegroups for the Databases2</span></span>](../technical-guides/optimizing-filegroups-for-the-databases2.md)  
  
-   [<span data-ttu-id="86f5f-112">Script de groupes de fichiers SQL de base de données MessageBox de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="86f5f-112">BizTalk Server MessageBox Database Filegroups SQL Script</span></span>](../technical-guides/biztalk-server-messagebox-database-filegroups-sql-script.md)  
  
-   [<span data-ttu-id="86f5f-113">Analyse des performances de SQL Server</span><span class="sxs-lookup"><span data-stu-id="86f5f-113">Monitoring SQL Server Performance</span></span>](../technical-guides/monitoring-sql-server-performance.md)