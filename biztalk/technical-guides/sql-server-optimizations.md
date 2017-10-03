---
title: Optimisations de SQL Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb735b54-595e-4dd0-9e4d-9a5e7a007a78
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3783c09b1155202ac8fe5a964d16c24d33082c26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sql-server-optimizations"></a><span data-ttu-id="64307-102">Optimisations de SQL Server</span><span class="sxs-lookup"><span data-stu-id="64307-102">SQL Server Optimizations</span></span>
<span data-ttu-id="64307-103">BizTalk Server est extrêmement de base de données applications exigeantes qui peuvent nécessiter la création de bases de données jusqu'à 13 dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="64307-103">BizTalk Server is an extremely database intensive application that may require the creation of up to 13 databases in SQL Server.</span></span> <span data-ttu-id="64307-104">Étant un des principaux objectifs de création de BizTalk Server pour vous assurer qu’aucun message n’est perdu, BizTalk Server conserve les données sur le disque avec une fréquence élevée et en outre, le fait dans le contexte d’une transaction MSDTC.</span><span class="sxs-lookup"><span data-stu-id="64307-104">Because one of the primary design goals of BizTalk Server is to ensure that no messages are lost, BizTalk Server persists data to disk with great frequency and furthermore, does so within the context of an MSDTC transaction.</span></span> <span data-ttu-id="64307-105">Par conséquent, les performances de la base de données est primordiale pour les performances globales d’une solution BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="64307-105">Therefore, database performance is paramount to the overall performance of any BizTalk Server solution.</span></span>  
  
 <span data-ttu-id="64307-106">Cette section décrit les méthodes générales pour optimiser les performances de SQL Server, ainsi que des méthodes pour optimiser les performances de la base de données qui sont spécifiques à un environnement BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="64307-106">This section describes general methods for maximizing SQL Server performance as well as methods for maximizing database performance that are specific to a BizTalk Server environment.</span></span> <span data-ttu-id="64307-107">Pour plus d’informations sur l’optimisation de BizTalk les performances de base de données, consultez l’article TechNet de l’optimisation de base de données BizTalk à [http://go.microsoft.com/fwlink/?LinkId=118001](http://go.microsoft.com/fwlink/?LinkId=118001).</span><span class="sxs-lookup"><span data-stu-id="64307-107">For additional information on optimizing BizTalk database performance, see the BizTalk Database Optimization TechNet article at [http://go.microsoft.com/fwlink/?LinkId=118001](http://go.microsoft.com/fwlink/?LinkId=118001).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="64307-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="64307-108">In This Section</span></span>  
  
-   [<span data-ttu-id="64307-109">Base de données de la Configuration préalable Optimizations1</span><span class="sxs-lookup"><span data-stu-id="64307-109">Pre-Configuration Database Optimizations1</span></span>](../technical-guides/pre-configuration-database-optimizations1.md)  
  
-   [<span data-ttu-id="64307-110">À la Configuration de base de données Optimizations1</span><span class="sxs-lookup"><span data-stu-id="64307-110">Post-Configuration Database Optimizations1</span></span>](../technical-guides/post-configuration-database-optimizations1.md)  
  
-   [<span data-ttu-id="64307-111">Optimisation des groupes de fichiers pour le Databases1</span><span class="sxs-lookup"><span data-stu-id="64307-111">Optimizing Filegroups for the Databases1</span></span>](../technical-guides/optimizing-filegroups-for-the-databases1.md)