---
title: "Étape 3 : Créer la Solution BizTalk Server dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4da3333-e430-4caf-bc29-44a60ebac385
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 402434ec74327b55f243fecd9d1c347ce4ff0390
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-create-the-biztalk-server-solution-in-visual-studio"></a><span data-ttu-id="ba35a-102">Étape 3 : Créer la Solution BizTalk Server dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ba35a-102">Step 3: Create the BizTalk Server Solution in Visual Studio</span></span>
<span data-ttu-id="ba35a-103">Dans cette section, nous cherchons à créer la solution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour recevoir des notifications d'opportunités de Salesforce, interroger Salesforce pour obtenir des informations supplémentaires sur l'opportunité et enfin insérer ces informations dans une base de données SQL Server sur site.</span><span class="sxs-lookup"><span data-stu-id="ba35a-103">In this section, we look at creating the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution for receiving opportunity notifications from Salesforce, querying Salesforce to get additional information about the opportunity, and finally inserting that information into an on-premise SQL Server database.</span></span> <span data-ttu-id="ba35a-104">Cette section est catégorisée davantage en fonction de chacune de ces étapes générales.</span><span class="sxs-lookup"><span data-stu-id="ba35a-104">This section is further categorized according to each of these broader steps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba35a-105">Pour être en mesure d'envoyer des messages à Salesforce et recevoir des messages de Salesforce dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], nous devons inclure certains composants personnalisés dans notre solution.</span><span class="sxs-lookup"><span data-stu-id="ba35a-105">To be able to send messages to Salesforce and to receive messages from Salesforce into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], we need to include some custom components into our solution.</span></span> <span data-ttu-id="ba35a-106">Nous créons ces composants personnalisés dans [étape 3d : l’activation de BizTalk Server pour envoyer et recevoir des Messages de Salesforce](../core/step-3d-enabling-biztalk-server-to-send-and-receive-messages-from-salesforce.md).</span><span class="sxs-lookup"><span data-stu-id="ba35a-106">We create those custom components in [Step 3d: Enabling BizTalk Server to Send and Receive Messages from Salesforce](../core/step-3d-enabling-biztalk-server-to-send-and-receive-messages-from-salesforce.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba35a-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ba35a-107">In This Section</span></span>  
  
-   [<span data-ttu-id="ba35a-108">Étape 3 a : recevoir une Notification d’opportunité de Salesforce dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="ba35a-108">Step 3a: Receive Salesforce Opportunity Notification into BizTalk Server</span></span>](../core/step-3a-receive-salesforce-opportunity-notification-into-biztalk-server.md)  
  
-   [<span data-ttu-id="ba35a-109">Étape 3 b : récupérer les détails d’opportunité de Salesforce à l’aide de l’adaptateur WCF-WebHttp</span><span class="sxs-lookup"><span data-stu-id="ba35a-109">Step 3b: Retrieve Opportunity Details from Salesforce using the WCF-WebHttp Adapter</span></span>](../core/step-3b-retrieve-opportunities-from-salesforce-using-the-wcf-webhttp-adapter.md)  
  
-   [<span data-ttu-id="ba35a-110">Étape 3c : insérer des détails d’opportunité dans une base de données SQL Server</span><span class="sxs-lookup"><span data-stu-id="ba35a-110">Step 3c: Insert Opportunity Details into a SQL Server Database</span></span>](../core/step-3c-insert-opportunity-details-into-a-sql-server-database.md)  
  
-   [<span data-ttu-id="ba35a-111">Étape 3d : L’activation de BizTalk Server envoyer et recevoir des Messages de Salesforce</span><span class="sxs-lookup"><span data-stu-id="ba35a-111">Step 3d: Enabling BizTalk Server to Send and Receive Messages from Salesforce</span></span>](../core/step-3d-enabling-biztalk-server-to-send-and-receive-messages-from-salesforce.md)  
  
-   [<span data-ttu-id="ba35a-112">Étape 3e : générer et déployer la Solution BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="ba35a-112">Step 3e: Build and Deploy the BizTalk Server Solution</span></span>](../core/step-3e-build-and-deploy-the-biztalk-server-solution.md)  
  
## <a name="see-also"></a><span data-ttu-id="ba35a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba35a-113">See Also</span></span>  
 [<span data-ttu-id="ba35a-114">Didacticiel 6 : Intégration de BizTalk Server 2013 avec Salesforce</span><span class="sxs-lookup"><span data-stu-id="ba35a-114">Tutorial 6: Integrating BizTalk Server 2013 with Salesforce</span></span>](Tutorial:%20Integrating%20BizTalk%20Server%202013%20with%20Salesforce.md)