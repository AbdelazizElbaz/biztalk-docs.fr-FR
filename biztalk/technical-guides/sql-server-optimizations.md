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
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36317d99387fde1d7b5e1c56b45255129daedb25
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="sql-server-optimizations"></a><span data-ttu-id="acb5e-102">Optimisations de SQL Server</span><span class="sxs-lookup"><span data-stu-id="acb5e-102">SQL Server Optimizations</span></span>
<span data-ttu-id="acb5e-103">BizTalk Server est extrêmement de base de données applications exigeantes qui peuvent nécessiter la création de bases de données jusqu'à 13 dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="acb5e-103">BizTalk Server is an extremely database intensive application that may require the creation of up to 13 databases in SQL Server.</span></span> <span data-ttu-id="acb5e-104">Étant un des principaux objectifs de création de BizTalk Server pour vous assurer qu’aucun message n’est perdu, BizTalk Server conserve les données sur le disque avec une fréquence élevée et en outre, le fait dans le contexte d’une transaction MSDTC.</span><span class="sxs-lookup"><span data-stu-id="acb5e-104">Because one of the primary design goals of BizTalk Server is to ensure that no messages are lost, BizTalk Server persists data to disk with great frequency and furthermore, does so within the context of an MSDTC transaction.</span></span> <span data-ttu-id="acb5e-105">Par conséquent, les performances de la base de données est primordiale pour les performances globales d’une solution BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="acb5e-105">Therefore, database performance is paramount to the overall performance of any BizTalk Server solution.</span></span>  
  
<span data-ttu-id="acb5e-106">Cette section décrit les méthodes générales pour optimiser les performances de SQL Server, ainsi que des méthodes pour optimiser les performances de la base de données qui sont spécifiques à un environnement BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="acb5e-106">This section describes general methods for maximizing SQL Server performance as well as methods for maximizing database performance that are specific to a BizTalk Server environment.</span></span> <span data-ttu-id="acb5e-107">Les liens suivants sont aussi bonnes ressources :</span><span class="sxs-lookup"><span data-stu-id="acb5e-107">The following links are also good resources:</span></span> 

- [<span data-ttu-id="acb5e-108">BizTalk Server : Recommandations pour l’installation, le dimensionnement, déploiement et maintenance d’une Solution</span><span class="sxs-lookup"><span data-stu-id="acb5e-108">BizTalk Server: Recommendations for Installing, Sizing, Deploying, and Maintaining a Solution</span></span>](https://social.technet.microsoft.com/wiki/contents/articles/666.biztalk-server-recommendations-for-installing-sizing-deploying-and-maintaining-a-solution.aspx)

- [<span data-ttu-id="acb5e-109">Guide d’optimisation des performances BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="acb5e-109">BizTalk Server Performance Optimization Guide</span></span>](biztalk-server-2013-performance-optimization-guide.md)

  
## <a name="next-steps"></a><span data-ttu-id="acb5e-110">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="acb5e-110">Next steps</span></span>
  
-   [<span data-ttu-id="acb5e-111">Préconfiguration des optimisations des bases de données</span><span class="sxs-lookup"><span data-stu-id="acb5e-111">Pre-Configuration Database Optimizations</span></span>](../technical-guides/pre-configuration-database-optimizations1.md)  
  
-   [<span data-ttu-id="acb5e-112">Postconfiguration des optimisations des bases de données</span><span class="sxs-lookup"><span data-stu-id="acb5e-112">Post-Configuration Database Optimizations</span></span>](../technical-guides/post-configuration-database-optimizations1.md)  
  
-   [<span data-ttu-id="acb5e-113">Optimisation des groupes de fichiers pour les bases de données</span><span class="sxs-lookup"><span data-stu-id="acb5e-113">Optimizing Filegroups for the Databases</span></span>](../technical-guides/optimizing-filegroups-for-the-databases1.md)