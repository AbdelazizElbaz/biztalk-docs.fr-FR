---
title: "Comment démarrer l’éditeur des règles d’entreprise et de charger une stratégie | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, loading
- opening, Busines Rule Composer
- Business Rule Composer, policies
- Business Rule Composer, opening
ms.assetid: 34a6034d-90b3-4ce0-9770-3790763affe3
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 420517c51fd6c7a6c854afe161a11a58f952db83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-start-the-business-rule-composer-and-load-a-policy"></a><span data-ttu-id="ecdfe-102">Comment démarrer l’éditeur des règles d’entreprise et de charger une stratégie</span><span class="sxs-lookup"><span data-stu-id="ecdfe-102">How to Start the Business Rule Composer and Load a Policy</span></span>
<span data-ttu-id="ecdfe-103">Cette section explique comment démarrer l'Éditeur des règles d'entreprise et charger une stratégie.</span><span class="sxs-lookup"><span data-stu-id="ecdfe-103">This section describes how to start the Business Rule Composer and load a policy.</span></span>  
  
### <a name="to-start-the-business-rule-composer"></a><span data-ttu-id="ecdfe-104">Pour démarrer l'Éditeur des règles d'entreprise</span><span class="sxs-lookup"><span data-stu-id="ecdfe-104">To start the Business Rule Composer</span></span>  
  
-   <span data-ttu-id="ecdfe-105">Sur le **Démarrer** menu, pointez sur **tous les programmes**, pointez sur Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], puis cliquez sur **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="ecdfe-105">On the **Start** menu, point to **All Programs**, point to Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and then click **Business Rule Composer**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ecdfe-106">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="ecdfe-106">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="ecdfe-107">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="ecdfe-107">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
### <a name="to-load-a-policy"></a><span data-ttu-id="ecdfe-108">Pour charger une stratégie</span><span class="sxs-lookup"><span data-stu-id="ecdfe-108">To load a policy</span></span>  
  
1.  <span data-ttu-id="ecdfe-109">Dans l’éditeur des règles d’entreprise, sur le **magasin de règles** menu, cliquez sur **charge**.</span><span class="sxs-lookup"><span data-stu-id="ecdfe-109">In the Business Rule Composer, on the **Rule Store** menu, click **Load**.</span></span>  
  
2.  <span data-ttu-id="ecdfe-110">Dans le **magasin de règles** boîte de dialogue le **SQL Server** liste déroulante, sélectionnez l’ordinateur SQL Server™ auquel vous souhaitez vous connecter.</span><span class="sxs-lookup"><span data-stu-id="ecdfe-110">In the **Rule Store** dialog box, in the **SQL Server** drop-down list, select the SQL Server™ computer to which you want to connect.</span></span>  
  
3.  <span data-ttu-id="ecdfe-111">Dans le **base de données** liste déroulante, sélectionnez la base de données qui contient le magasin de règles que vous souhaitez ouvrir.</span><span class="sxs-lookup"><span data-stu-id="ecdfe-111">In the **Database** drop-down list, select the database that contains the rule store you want to open.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ecdfe-112">La base de données par défaut pour le magasin de règles installé par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est **BizTalkRuleEngineDb**.</span><span class="sxs-lookup"><span data-stu-id="ecdfe-112">The default database for the rule store installed by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is **BizTalkRuleEngineDb**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ecdfe-113">Si vous utilisez un compte SQL Server nouvellement créé qui a le **appliquer l’expiration du mot de passe** et **utilisateur doit changer de mot de passe à la prochaine connexion** options set, l’éditeur des règles d’entreprise ne pourront pas se connecter à la règle Moteur de base de données.</span><span class="sxs-lookup"><span data-stu-id="ecdfe-113">If you use a newly created SQL Server account that has the **Enforce password expiration** and **User must change password at next login** options set, the business rule composer will fail to connect to the Rule Engine database.</span></span>