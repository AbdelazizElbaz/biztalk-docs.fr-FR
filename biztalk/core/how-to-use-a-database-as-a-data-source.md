---
title: L’utilisation d’une base de données comme Source de données | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Business Rule Composer, data sources
ms.assetid: a68057ed-836f-499f-bb80-f644d81bcfc5
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3a9201ee729288a819a3d527a6ecb4fefd32797
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-a-database-as-a-data-source"></a><span data-ttu-id="da718-102">Utilisation d'une base de données en tant que source de données</span><span class="sxs-lookup"><span data-stu-id="da718-102">How to Use a Database as a Data Source</span></span>
<span data-ttu-id="da718-103">Vous pouvez spécifier une base de données en tant que source de données.</span><span class="sxs-lookup"><span data-stu-id="da718-103">You can specify a database as a data source.</span></span> <span data-ttu-id="da718-104">Vous pouvez ensuite sélectionner une table ou une colonne d'une table dans la base de données et la faire glisser vers une règle ou une définition de vocabulaire pour l'utiliser en tant que fait.</span><span class="sxs-lookup"><span data-stu-id="da718-104">You can subsequently select a table or table column from the database, and drag it onto a vocabulary definition or rule to use as a fact.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da718-105">Vous pouvez choisir de lier à la base de données/table de lignes à l’aide **DataConnection** ou **TypedDataTable** en sélectionnant « Connexion de données » ou « Ligne de la table de base de données » dans le **type de liaison de base de données**  zone de liste déroulante dans la fenêtre Propriétés pour le **bases de données** onglet de l’Explorateur de faits.</span><span class="sxs-lookup"><span data-stu-id="da718-105">You can choose to bind to the database row/table using either **DataConnection** or **TypedDataTable** by selecting "Data connection" or "Database table/row" from the **Database binding type** drop-down box in the Property Window for the **Databases** tab of Fact Explorer.</span></span> <span data-ttu-id="da718-106">**DataConnection** liaison est utilisée par défaut.</span><span class="sxs-lookup"><span data-stu-id="da718-106">**DataConnection** binding is used by default.</span></span>  
  
### <a name="to-specify-a-sql-database-as-a-data-source"></a><span data-ttu-id="da718-107">Pour spécifier une base de données SQL en tant que source de données</span><span class="sxs-lookup"><span data-stu-id="da718-107">To specify a SQL database as a data source</span></span>  
  
1.  <span data-ttu-id="da718-108">Dans la fenêtre Explorateur de faits, cliquez sur le **bases de données** onglet.</span><span class="sxs-lookup"><span data-stu-id="da718-108">In the Facts Explorer window, click the **Databases** tab.</span></span>  
  
2.  <span data-ttu-id="da718-109">Cliquez sur le **serveurs** nœud, puis cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="da718-109">Right-click the **Servers** node, and then click **Browse**.</span></span>  
  
3.  <span data-ttu-id="da718-110">Dans la liste déroulante, sélectionnez un serveur de base de données disponible.</span><span class="sxs-lookup"><span data-stu-id="da718-110">In the drop-down list, select an available database server.</span></span>  
  
4.  <span data-ttu-id="da718-111">Sélectionnez un type d'authentification.</span><span class="sxs-lookup"><span data-stu-id="da718-111">Select an authentication type.</span></span> <span data-ttu-id="da718-112">Si vous sélectionnez l'authentification SQL, entrez un nom de connexion et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="da718-112">If you select SQL authentication, enter a logon name and password.</span></span> <span data-ttu-id="da718-113">Lorsque vous avez entré vos informations d’authentification, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="da718-113">When you have entered your authentication information, click **OK**.</span></span>  
  
     <span data-ttu-id="da718-114">![Capture d’écran de bases de données du navigateur de l’arborescence. ] (../core/media/ebiz-dbbrows.gif "ebiz_dbbrows")</span><span class="sxs-lookup"><span data-stu-id="da718-114">![Screenshot of databases of tree brower.](../core/media/ebiz-dbbrows.gif "ebiz_dbbrows")</span></span>  
<span data-ttu-id="da718-115">Navigation dans une base de données</span><span class="sxs-lookup"><span data-stu-id="da718-115">Browsing a database</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da718-116">Les vues de base de données SQL Server ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="da718-116">SQL Server database views are not supported.</span></span>