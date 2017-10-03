---
title: "Développer des applications SQL à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11df5cc2-b532-45a8-9055-d05f4704a6e5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b503b0766a4848e05c9361fb151196ee43afd81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-sql-applications-using-the-wcf-channel-model"></a><span data-ttu-id="4c57d-102">Développer des applications SQL à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="4c57d-102">Develop SQL applications using the WCF Channel Model</span></span>
<span data-ttu-id="4c57d-103">Vous pouvez utiliser la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de canal pour consommer le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] en envoyant des messages XML directement sur une instance de canal créée avec la liaison de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4c57d-103">You can use the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] channel model to consume the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] by sending XML messages directly over a channel instance created with the SQL Server Binding.</span></span>  
  
 <span data-ttu-id="4c57d-104">Un avantage de l’utilisation du modèle de canal WCF en utilisant les classes fortement typées et les méthodes que le modèle de service WCF expose est que le modèle de canal fournit un contrôle plus précis sur les opérations que vous effectuez sur la base de données SQL.</span><span class="sxs-lookup"><span data-stu-id="4c57d-104">One advantage of using the WCF channel model over using the strongly-typed classes and methods that the WCF service model exposes is that the channel model provides more fine-grained control over the operations that you perform on the SQL database.</span></span> <span data-ttu-id="4c57d-105">Ce contrôle vient du fait que dans le modèle de canal WCF, vous contrôlez directement le contenu des messages que vous envoyez sur le canal.</span><span class="sxs-lookup"><span data-stu-id="4c57d-105">This control comes from the fact that in the WCF channel model, you directly control the contents of the messages that you send over the channel.</span></span>  
  
 <span data-ttu-id="4c57d-106">Dans certains scénarios, ce niveau supplémentaire de contrôle peut être utile.</span><span class="sxs-lookup"><span data-stu-id="4c57d-106">In certain scenarios, this extra level of control can be beneficial.</span></span> <span data-ttu-id="4c57d-107">Par exemple, lorsque vous utilisez le modèle de canal WCF pour effectuer une opération de mise à jour sur une table, vous pouvez sélectivement mettre à jour colonnes dans les lignes de la cible en omettant les colonnes à partir du modèle de mise à jour que vous passez dans le message.</span><span class="sxs-lookup"><span data-stu-id="4c57d-107">For example, when you use the WCF channel model to perform an Update operation on a table, you can selectively update columns in the target rows by omitting columns from the update template that you pass in the message.</span></span> <span data-ttu-id="4c57d-108">Seules les colonnes qui sont nécessaires sont celles avec « nillable = false » dans le WSDL.</span><span class="sxs-lookup"><span data-stu-id="4c57d-108">The only columns that are required are those with “nillable=false” in the WSDL.</span></span> <span data-ttu-id="4c57d-109">La méthode de mise à jour exposée par un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client utilise un paramètre d’enregistrement de fortement typé pour le modèle qui inclut toutes les colonnes dans le schéma de table.</span><span class="sxs-lookup"><span data-stu-id="4c57d-109">The update method exposed by a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client uses a strongly-typed record parameter for the template that includes every column in the table schema.</span></span>  
  
 <span data-ttu-id="4c57d-110">Les sections de cette rubrique expliquent comment effectuer les opérations sur les [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] en utilisant le modèle de canal WCF.</span><span class="sxs-lookup"><span data-stu-id="4c57d-110">The sections in this topic explain how to perform operations on the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] by using the WCF channel model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4c57d-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4c57d-111">In This Section</span></span>  
  
-   [<span data-ttu-id="4c57d-112">Vue d’ensemble du modèle de canal WCF avec l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="4c57d-112">Overview of the WCF channel model with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-channel-model-with-the-sql-adapter.md)  
  
-   [<span data-ttu-id="4c57d-113">Créer un canal à l’aide de l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="4c57d-113">Create a channel using the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/create-a-channel-using-the-sql-adapter.md)  
  
-   [<span data-ttu-id="4c57d-114">Exécuter une opération Insert sur une Table dans SQL à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="4c57d-114">Run an Insert Operation on a Table in SQL using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sql/run-an-insert-operation-on-a-table-in-sql-using-the-wcf-channel-model.md)  
  
-   [<span data-ttu-id="4c57d-115">Recevoir des Messages d’interrogation de données modifiées à partir de SQL Server à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="4c57d-115">Receive Polling-based Data-changed Messages from SQL Server by Using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-channel.md)  
  
## <a name="see-also"></a><span data-ttu-id="4c57d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c57d-116">See Also</span></span>  
[<span data-ttu-id="4c57d-117">Développer vos applications SQL</span><span class="sxs-lookup"><span data-stu-id="4c57d-117">Develop your SQL applications</span></span>](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)