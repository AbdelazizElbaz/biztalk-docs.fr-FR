---
title: "Réception d’interrogation de Messages entre plusieurs Ports de réception à partir de SQL à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21cf4875-1c04-41cf-98f5-d1307987ca55
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2be084ca9e0a90813a541563bf6f600ea277aec9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk-server"></a><span data-ttu-id="b3383-102">Réception d’interrogation de Messages entre plusieurs Ports de réception à partir de SQL à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="b3383-102">Receive Polling Messages Across Multiple Receive Ports from SQL using BizTalk Server</span></span>
<span data-ttu-id="b3383-103">Considérez un scénario dans lequel vous souhaitez créer une application BizTalk qui comprend deux opérations d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="b3383-103">Consider a scenario where you want to create a BizTalk application that includes two polling operations.</span></span> <span data-ttu-id="b3383-104">Chaque opération d’interrogation interroge les tables distinctes, employé et client, à partir de la même base de données.</span><span class="sxs-lookup"><span data-stu-id="b3383-104">Each polling operation polls separate tables, Employee and Customer, from the same database.</span></span> <span data-ttu-id="b3383-105">Lorsque vous déployez une telle application dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous devez créer deux ports de réception.</span><span class="sxs-lookup"><span data-stu-id="b3383-105">When you deploy such an application in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you will need to create two receive ports.</span></span> <span data-ttu-id="b3383-106">L’URI de connexion pour chaque port de réception sera :</span><span class="sxs-lookup"><span data-stu-id="b3383-106">The connection URI for each receive port will be:</span></span>  
  
```  
mssql://<server_name>/<database_instance_name>/<datbase_name>  
```  
  
 <span data-ttu-id="b3383-107">Étant donné que les deux recevoir des ports reçoivent des messages de l’interrogation de la même base de données sur le même serveur, l’URI de connexion pour les deux doivent être identiques.</span><span class="sxs-lookup"><span data-stu-id="b3383-107">Because both receive ports are receiving polling messages from the same database on the same server, the connection URI for both will be the same.</span></span> <span data-ttu-id="b3383-108">Toutefois, une application BizTalk ne peut pas avoir deux ports avec le même URI de connexion de réception.</span><span class="sxs-lookup"><span data-stu-id="b3383-108">However, a BizTalk application cannot have two receive ports with the same connection URI.</span></span>  
  
 <span data-ttu-id="b3383-109">Pour permettre aux clients de l’adaptateur d’avoir deux ports de réception qui interrogent la même base de données (ou même de la même table dans une base de données) dans une application BizTalk, le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] fournit une propriété de connexion, **InboundID**.</span><span class="sxs-lookup"><span data-stu-id="b3383-109">To enable adapter clients to have two receive ports that poll the same database (or even the same table in a database) in a BizTalk application, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] provides a connection property, **InboundID**.</span></span> <span data-ttu-id="b3383-110">Vous pouvez spécifier une valeur pour cette propriété de connexion.</span><span class="sxs-lookup"><span data-stu-id="b3383-110">You can specify any value for this connection property.</span></span> <span data-ttu-id="b3383-111">En ajoutant le code entrant, une connexion URI est unique.</span><span class="sxs-lookup"><span data-stu-id="b3383-111">By adding the inbound ID, a connection URI becomes unique.</span></span> <span data-ttu-id="b3383-112">Exemple :</span><span class="sxs-lookup"><span data-stu-id="b3383-112">For example:</span></span>  
  
 <span data-ttu-id="b3383-113">L’URI de connexion pour le port de réception de messages d’interrogation pour la table Employee peut être :</span><span class="sxs-lookup"><span data-stu-id="b3383-113">The connection URI for the port receiving polling messages for the Employee table can be:</span></span>  
  
```  
mssql://<server_name>/<database_instance_name>/<datbase_name>?InboundID=Employee  
```  
  
 <span data-ttu-id="b3383-114">De même, l’URI de connexion pour le port de réception de messages d’interrogation pour la table Customer peut être :</span><span class="sxs-lookup"><span data-stu-id="b3383-114">Similarly, the connection URI for the port receiving polling messages for the Customer table can be:</span></span>  
  
```  
mssql://<server_name>/<database_instance_name>/<datbase_name>?InboundID=Customer  
```  
  
 <span data-ttu-id="b3383-115">Étant donné que l’URI de connexion uniques en ajoutant le **InboundID** propriété, vous pouvez désormais avoir plusieurs ports d’interrogation de la même base de données ou de la même table dans une même application BizTalk de réception.</span><span class="sxs-lookup"><span data-stu-id="b3383-115">Because the connection URIs become unique by adding the **InboundID** property, you can now have multiple receive ports polling the same database or table in a single BizTalk application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b3383-116">Vous pouvez choisir de spécifier le **InboundID** propriété de connexion à la fois pour le **d’interrogation** et **TypedPolling** operations.</span><span class="sxs-lookup"><span data-stu-id="b3383-116">You can choose to specify the **InboundID** connection property for both the **Polling** and **TypedPolling** operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3383-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3383-117">See Also</span></span>  
 [<span data-ttu-id="b3383-118">Interrogation SQL Server à l’aide de l’adaptateur SQL avec BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="b3383-118">Poll SQL Server using the SQL Adapter with BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)