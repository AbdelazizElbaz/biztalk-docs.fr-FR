---
title: "Administration à l’aide du portail de gestion ESB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 478d1dcc-e9b2-443b-be98-5b7545322401
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 351d06df4d6384607564778c4b86d8c509379488
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="administration-using-the-esb-management-portal"></a><span data-ttu-id="ad1dd-102">Administration à l’aide du portail de gestion ESB</span><span class="sxs-lookup"><span data-stu-id="ad1dd-102">Administration Using the ESB Management Portal</span></span>
<span data-ttu-id="ad1dd-103">Le portail de gestion ESB inclus dans le cadre de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], est un exemple de site qui illustre l’utilisation de mesures et les possibilités qui existent pour l’extension de BizTalk ESB Toolkit.</span><span class="sxs-lookup"><span data-stu-id="ad1dd-103">The ESB Management Portal, included as part of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], is a sample site that demonstrates the use of metrics and the possibilities that exist for extending the BizTalk ESB Toolkit.</span></span> <span data-ttu-id="ad1dd-104">Le portail fournit un point de départ à partir duquel vous pouvez générer votre propre portail personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ad1dd-104">The portal provides a starting point from which you can build your own customized portal.</span></span>  
  
 <span data-ttu-id="ad1dd-105">Le portail de gestion ESB est également un outil hautement compatible et utile qui peut aider à optimiser l’utilisation et l’efficacité du système de gestion d’exception ESB.</span><span class="sxs-lookup"><span data-stu-id="ad1dd-105">The ESB Management Portal is also a highly capable and useful tool that can help to maximize the use and efficiency of the ESB exception management system.</span></span> <span data-ttu-id="ad1dd-106">En outre, le portail fournit une interface utilisateur pour un serveur de Registre Universal Description, Discovery and Integration (UDDI) sous-jacent et des fonctionnalités de configuration graphique des fonctionnalités telles que l’audit, affichage des informations d’historique, configuration alertes et notifications et en permettant aux utilisateurs à s’abonner aux alertes qui indiquent des erreurs qui se produisent dans les applications d’ESB.</span><span class="sxs-lookup"><span data-stu-id="ad1dd-106">In addition, the portal provides a user interface for an underlying Universal Description, Discovery, and Integration (UDDI) registry server and graphical configuration capabilities for features such as auditing, viewing history information, configuring alerts and notifications, and allowing users to subscribe to alerts that indicate faults occurring in ESB applications.</span></span>  
  
 <span data-ttu-id="ad1dd-107">Cette section décrit les tâches courantes que vous pouvez accomplir à l’aide du portail de gestion ESB, notamment les suivantes :</span><span class="sxs-lookup"><span data-stu-id="ad1dd-107">This section describes the common tasks you can accomplish using the ESB Management Portal, including the following:</span></span>  
  
-   [<span data-ttu-id="ad1dd-108">Utilisation des Exceptions et les Messages d’erreur</span><span class="sxs-lookup"><span data-stu-id="ad1dd-108">Working with Exceptions and Fault Messages</span></span>](../esb-toolkit/working-with-exceptions-and-fault-messages.md)  
  
-   [<span data-ttu-id="ad1dd-109">Configuration des alertes, Notifications et abonnements</span><span class="sxs-lookup"><span data-stu-id="ad1dd-109">Configuring Alerts, Notifications, and Subscriptions</span></span>](../esb-toolkit/configuring-alerts-notifications-and-subscriptions.md)  
  
-   [<span data-ttu-id="ad1dd-110">Affichage et gestion de l’audit et historique</span><span class="sxs-lookup"><span data-stu-id="ad1dd-110">Viewing and Managing Auditing and History</span></span>](../esb-toolkit/viewing-and-managing-auditing-and-history.md)  
  
-   [<span data-ttu-id="ad1dd-111">Analyse de tendances de panne à l’aide de graphiques et rapports</span><span class="sxs-lookup"><span data-stu-id="ad1dd-111">Analyzing Fault Trends Using Charts and Reports</span></span>](../esb-toolkit/analyzing-fault-trends-using-charts-and-reports.md)  
  
-   [<span data-ttu-id="ad1dd-112">Affichage et la publication des inscriptions UDDI</span><span class="sxs-lookup"><span data-stu-id="ad1dd-112">Viewing and Publishing UDDI Registrations</span></span>](../esb-toolkit/viewing-and-publishing-uddi-registrations.md)  
  
> [!NOTE]
>  <span data-ttu-id="ad1dd-113">Pour obtenir une description détaillée des fonctionnalités du portail de gestion ESB individuelles, consultez [référence de fonctionnalité de portail de gestion ESB](../esb-toolkit/esb-management-portal-feature-reference.md).</span><span class="sxs-lookup"><span data-stu-id="ad1dd-113">For a detailed description of the individual features of the ESB Management Portal, see [ESB Management Portal Feature Reference](../esb-toolkit/esb-management-portal-feature-reference.md).</span></span>  
  
## <a name="esb-portal-technologies"></a><span data-ttu-id="ad1dd-114">Technologies de portail ESB</span><span class="sxs-lookup"><span data-stu-id="ad1dd-114">ESB Portal Technologies</span></span>  
 <span data-ttu-id="ad1dd-115">Le portail de gestion ESB tire parti des technologies suivantes :</span><span class="sxs-lookup"><span data-stu-id="ad1dd-115">The ESB Management Portal takes advantage of the following technologies:</span></span>  
  
-   [!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)] 
  
-   <span data-ttu-id="ad1dd-116">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ad1dd-116">ASP.NET</span></span>
  
-   <span data-ttu-id="ad1dd-117">[Enterprise Library](http://go.microsoft.com/fwlink/?LinkId=188292) ([http://go.microsoft.com/fwlink/?LinkId=188292](http://go.microsoft.com/fwlink/?LinkId=188292)).</span><span class="sxs-lookup"><span data-stu-id="ad1dd-117">[Enterprise Library](http://go.microsoft.com/fwlink/?LinkId=188292) ([http://go.microsoft.com/fwlink/?LinkId=188292](http://go.microsoft.com/fwlink/?LinkId=188292)).</span></span> <span data-ttu-id="ad1dd-118">Le portail de gestion ESB utilise les assemblys de bibliothèque d’entreprise suivants :</span><span class="sxs-lookup"><span data-stu-id="ad1dd-118">The ESB Management Portal uses the following Enterprise Library assemblies:</span></span>  
  
    -   <span data-ttu-id="ad1dd-119">**Microsoft.Practices.EnterpriseLibrary.Caching**</span><span class="sxs-lookup"><span data-stu-id="ad1dd-119">**Microsoft.Practices.EnterpriseLibrary.Caching**</span></span>  
  
    -   <span data-ttu-id="ad1dd-120">**Microsoft.Practices.EnterpriseLibrary.Common**</span><span class="sxs-lookup"><span data-stu-id="ad1dd-120">**Microsoft.Practices.EnterpriseLibrary.Common**</span></span>  
  
    -   <span data-ttu-id="ad1dd-121">**Microsoft.Practices.EnterpriseLibrary.Data**</span><span class="sxs-lookup"><span data-stu-id="ad1dd-121">**Microsoft.Practices.EnterpriseLibrary.Data**</span></span>  
  
    -   <span data-ttu-id="ad1dd-122">**Microsoft.Practices.EnterpriseLibrary.ExceptionHandling**</span><span class="sxs-lookup"><span data-stu-id="ad1dd-122">**Microsoft.Practices.EnterpriseLibrary.ExceptionHandling**</span></span>  
  
    -   <span data-ttu-id="ad1dd-123">**Microsoft.Practices.EnterpriseLibrary.ExceptionHandling.Logging**</span><span class="sxs-lookup"><span data-stu-id="ad1dd-123">**Microsoft.Practices.EnterpriseLibrary.ExceptionHandling.Logging**</span></span>  
  
    -   <span data-ttu-id="ad1dd-124">**Microsoft.Practices.EnterpriseLibrary.Logging**</span><span class="sxs-lookup"><span data-stu-id="ad1dd-124">**Microsoft.Practices.EnterpriseLibrary.Logging**</span></span>  
  
    -   <span data-ttu-id="ad1dd-125">**Microsoft.Practices.EnterpriseLibrary.ObjectBuilder2**</span><span class="sxs-lookup"><span data-stu-id="ad1dd-125">**Microsoft.Practices.EnterpriseLibrary.ObjectBuilder2**</span></span>  
  
    -   <span data-ttu-id="ad1dd-126">**Microsoft.Practices.EnterpriseLibrary.Validation**</span><span class="sxs-lookup"><span data-stu-id="ad1dd-126">**Microsoft.Practices.EnterpriseLibrary.Validation**</span></span>  
  
    -   <span data-ttu-id="ad1dd-127">Microsoft.Practices.Unity</span><span class="sxs-lookup"><span data-stu-id="ad1dd-127">Microsoft.Practices.Unity</span></span>  
  
-   <span data-ttu-id="ad1dd-128">[Contrôle de graphique Microsoft](http://go.microsoft.com/fwlink/?LinkId=188293) (http://go.microsoft.com/fwlink/?LinkId=188293) pour Microsoft .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="ad1dd-128">[Microsoft Chart Controls](http://go.microsoft.com/fwlink/?LinkId=188293) (http://go.microsoft.com/fwlink/?LinkId=188293) for Microsoft .NET Framework 4</span></span>  
  
<span data-ttu-id="ad1dd-129">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] suivi métrique étend uniquement pour le suivi des pannes pour le système de gestion d’exception.</span><span class="sxs-lookup"><span data-stu-id="ad1dd-129">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] metric tracking extends only to fault tracking for the exception management system.</span></span>