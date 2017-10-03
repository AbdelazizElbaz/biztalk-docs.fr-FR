---
title: "Développer des applications BizTalk à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5471f28e-bce1-4295-b56d-954690e60749
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9963764a298246c5a236d10b6010feee8497278f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-biztalk-applications-using-the-sql-adapter"></a><span data-ttu-id="6b8d4-102">Développer des applications BizTalk à l’aide de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="6b8d4-102">Develop BizTalk applications using the SQL adapter</span></span>
<span data-ttu-id="6b8d4-103">Développement d’applications BizTalk implique la création d’un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et à l’aide de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer le schéma XML.</span><span class="sxs-lookup"><span data-stu-id="6b8d4-103">Developing BizTalk applications involves creating a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate XML schema.</span></span> <span data-ttu-id="6b8d4-104">Une fois que vous avez généré le schéma, vous pouvez utiliser le routage basé sur le contenu (CBR) ou créer des orchestrations BizTalk pour envoyer et recevoir des messages conformes au schéma généré.</span><span class="sxs-lookup"><span data-stu-id="6b8d4-104">Once you have generated the schema, you can either use Content-Based Routing (CBR) or create BizTalk orchestrations to send and receive messages that conform to the generated schema.</span></span>  
  
 <span data-ttu-id="6b8d4-105">CBR peut être utilisé dans les scénarios où les messages envoyés à SQL Server nécessitent un traitement intensif.</span><span class="sxs-lookup"><span data-stu-id="6b8d4-105">CBR can be used in scenarios where the messages being sent to SQL Server do not require any intensive processing.</span></span> <span data-ttu-id="6b8d4-106">Par exemple, si vous savez que le port de réception reçoit les messages uniquement d’un certain type, vous pouvez ajouter un filtre au port d’envoi pour router les messages qui correspondent à l’expression de filtre pour le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="6b8d4-106">For example, if you know that the receive port will receive messages only of a certain type, you can add a filter to the send port to route messages that match the filter expression to the send port.</span></span>  
  
 <span data-ttu-id="6b8d4-107">Dans les orchestrations BizTalk, vous créez envoi et ports de réception pour envoyer et recevoir des messages vers et depuis le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], qui à son tour envoie des messages à [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6b8d4-107">In BizTalk orchestrations, you create send and receive ports to send and receive messages to and from the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], which in turn sends the messages to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="6b8d4-108">Cette section fournit des informations sur l’utilisation des orchestrations BizTalk pour effectuer des opérations sur l’utilisation de SQL Server le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6b8d4-108">This section provides information about using BizTalk orchestrations to perform operations on SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="6b8d4-109">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] à son tour utilise le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], ce qui peut interagir avec une liaison WCF.</span><span class="sxs-lookup"><span data-stu-id="6b8d4-109">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in turn uses the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], which can interact with a WCF binding.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6b8d4-110">Pour utiliser le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous devez toujours définir la **EnableBizTalkCompatibilityMode** liaison de propriété **True**.</span><span class="sxs-lookup"><span data-stu-id="6b8d4-110">To use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you must always set the **EnableBizTalkCompatibilityMode** binding property to **True**.</span></span> <span data-ttu-id="6b8d4-111">Pour plus d’informations sur la définition des propriétés de liaison, consultez [configurer les propriétés de liaison de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="6b8d4-111">For information about how to set binding properties, see [Configure the binding properties for the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6b8d4-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6b8d4-112">In This Section</span></span>  
  
-   [<span data-ttu-id="6b8d4-113">Conditions préalables pour créer des applications SQL à l’aide de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="6b8d4-113">Prerequisites to create SQL applications using the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md) 
  
-   [<span data-ttu-id="6b8d4-114">Blocs de construction pour développer des applications BizTalk à l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="6b8d4-114">Building blocks to develop BizTalk applications with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md) 
  
-   [<span data-ttu-id="6b8d4-115">INSERT, Update, Delete et sélectionnez les opérations sur les Tables et vues à l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="6b8d4-115">Insert, Update, Delete, and Select Operations on Tables and Views with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/insert-update-delete-and-select-on-tables-and-views-with-the-sql-adapter.md)  
  
-   [<span data-ttu-id="6b8d4-116">Exécuter des opérations sur les Tables et vues avec des Types de données volumineux à l’aide de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="6b8d4-116">Run Operations on Tables and Views with Large Data Types using the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/run-operations-on-tables-and-views-with-large-data-types-using-the-sql-adapter.md)  
  
-   [<span data-ttu-id="6b8d4-117">Exécuter des procédures stockées dans SQL Server à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="6b8d4-117">Execute Stored Procedures in SQL Server by Using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-biztalk-server.md)  
  
-   [<span data-ttu-id="6b8d4-118">Exécuter des procédures stockées avec un paramètre unique</span><span class="sxs-lookup"><span data-stu-id="6b8d4-118">Execute Stored Procedures With a Single XML Parameter</span></span>](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-with-a-single-xml-parameter-in-sql-using-biztalk.md)  
  
-   [<span data-ttu-id="6b8d4-119">Exécutez ayant de procédures stockées une clause FOR XML Clause dans SQL Server à l’aide de BizTalk server</span><span class="sxs-lookup"><span data-stu-id="6b8d4-119">Execute Stored Procedures Having a FOR XML Clause in SQL Server using BizTalk server</span></span>](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-having-a-for-xml-clause-in-sql-server-using-biztalk.md)  
  
-   [<span data-ttu-id="6b8d4-120">Exécuter des opérations composites sur SQL Server à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="6b8d4-120">Run Composite Operations on SQL Server by Using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/run-composite-operations-on-sql-server-using-biztalk-server.md)  
  
-   [<span data-ttu-id="6b8d4-121">Appeler des fonctions scalaires dans SQL Server à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="6b8d4-121">Invoke Scalar Functions in SQL Server by Using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/invoke-scalar-functions-in-sql-server-using-biztalk-server.md)  
  
-   [<span data-ttu-id="6b8d4-122">Appeler des fonctions table dans SQL Server à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="6b8d4-122">Invoke Table-Valued Functions in SQL Server by Using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/invoke-table-valued-functions-in-sql-server-using-biztalk-server.md) 
  
-   [<span data-ttu-id="6b8d4-123">Réalisation d’opérations ExecuteReader, ExecuteScalar ou ExecuteNonQuery opérations à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="6b8d4-123">Performing ExecuteReader, ExecuteScalar, or ExecuteNonQuery Operations by Using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md)  
  
-   [<span data-ttu-id="6b8d4-124">Recherche de serveur SQL Server à l’aide de l’adaptateur SQL avec BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="6b8d4-124">Polling SQL Server by Using the SQL Adapter with BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)  
  
-   [<span data-ttu-id="6b8d4-125">Recevoir des Notifications de requête SQL à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="6b8d4-125">Receive SQL Query Notifications by Using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="6b8d4-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b8d4-126">See Also</span></span>  
[<span data-ttu-id="6b8d4-127">Développer vos applications SQL</span><span class="sxs-lookup"><span data-stu-id="6b8d4-127">Develop your SQL applications</span></span>](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)