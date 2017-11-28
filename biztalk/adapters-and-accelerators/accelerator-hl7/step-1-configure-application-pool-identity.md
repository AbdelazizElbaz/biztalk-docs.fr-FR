---
title: "Étape 1 : Configurer l’identité du Pool d’applications | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, application pools
- application pools
ms.assetid: 66286327-8580-4378-89ee-ddd7204b03c6
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e61ee2994e81c3fdd352506d6a9757cde557fbb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-configure-application-pool-identity"></a><span data-ttu-id="f97bf-102">Étape 1 : Configurer l’identité du Pool d’applications</span><span class="sxs-lookup"><span data-stu-id="f97bf-102">Step 1: Configure Application Pool Identity</span></span>
<span data-ttu-id="f97bf-103">Dans ce didacticiel, vous utilisez un pool d’applications dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Internet Information Services (IIS) pour traiter l’orchestration, vous publiez en tant qu’un service Web.</span><span class="sxs-lookup"><span data-stu-id="f97bf-103">In this tutorial, you use an application pool in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Internet Information Services (IIS) to process the orchestration, which you publish as a Web service.</span></span> <span data-ttu-id="f97bf-104">Un pool d’applications est un regroupement d’une ou plusieurs URL servies par un processus de travail.</span><span class="sxs-lookup"><span data-stu-id="f97bf-104">An application pool is a grouping of one or more URLs served by a worker process.</span></span>  
  
 <span data-ttu-id="f97bf-105">L’identité d’un pool d’applications est le nom du compte de service sous lequel s’exécute le processus de travail du pool d’applications.</span><span class="sxs-lookup"><span data-stu-id="f97bf-105">The identity of an application pool is the name of the service account under which the worker process of the application pool runs.</span></span> <span data-ttu-id="f97bf-106">Par défaut, les pools d’applications fonctionnent sous le compte d’utilisateur Service réseau dispose de droits d’accès utilisateur bas niveau et ne suffit pas pour ce didacticiel pour la fonction.</span><span class="sxs-lookup"><span data-stu-id="f97bf-106">By default, application pools operate under the Network Service user account, which has low-level user-access rights and is insufficient for this tutorial to function.</span></span> <span data-ttu-id="f97bf-107">Pour des raisons de sécurité, vous souhaitez configurer l’identité du pool d’application pour un compte d’utilisateur avec les autorisations minimales, mais au moins d’autorisations pour écrire dans la base de données MessageBox (BizTalkMsgBoxDb) et la base de données (également appelé BizTalk Base de données de gestion, ou BizTalkMgmtDb).</span><span class="sxs-lookup"><span data-stu-id="f97bf-107">For security reasons, you want to configure the application pool identity to a user account with the absolute minimum permissions, but at least permissions to write to the MessageBox database (BizTalkMsgBoxDb) and Configuration database (also known as the BizTalk Management database, or BizTalkMgmtDb).</span></span>  
  
### <a name="to-change-the-service-account-under-which-an-application-pool-runs"></a><span data-ttu-id="f97bf-108">Pour modifier le compte de service sous lequel s’exécute un pool d’applications</span><span class="sxs-lookup"><span data-stu-id="f97bf-108">To change the service account under which an application pool runs</span></span>  
  
1.  <span data-ttu-id="f97bf-109">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="f97bf-109">Click **Start**, point to **Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="f97bf-110">Dans le Gestionnaire des Services Internet (IIS), développez l’ordinateur local, puis **Pools d’applications**.</span><span class="sxs-lookup"><span data-stu-id="f97bf-110">In Internet Information Services (IIS) Manager, expand the local computer, and expand **Application Pools**.</span></span>  
  
3.  <span data-ttu-id="f97bf-111">Cliquez sur le pool d’applications que vous souhaitez configurer (par défaut, ce didacticiel s’exécute sous le **DefaultAppPool**), puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f97bf-111">Right-click the application pool you want to configure (by default, this tutorial runs under the **DefaultAppPool**), and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="f97bf-112">Dans la boîte de dialogue Propriétés de DefaultAppPool sur le **identité** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f97bf-112">In the DefaultAppPool Properties dialog box, on the **Identity** tab, do the following:</span></span>  
  
    |<span data-ttu-id="f97bf-113">Utiliser</span><span class="sxs-lookup"><span data-stu-id="f97bf-113">Use this</span></span>|<span data-ttu-id="f97bf-114">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="f97bf-114">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="f97bf-115">**Prédéfinis**</span><span class="sxs-lookup"><span data-stu-id="f97bf-115">**Predefined**</span></span>|<span data-ttu-id="f97bf-116">Désélectionnez **prédéfinies**.</span><span class="sxs-lookup"><span data-stu-id="f97bf-116">Deselect **Predefined**.</span></span> <span data-ttu-id="f97bf-117">**Prédéfinies** fait référence à des comptes de service standard, tels que les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="f97bf-117">**Predefined** refers to standard service accounts, such as the following:</span></span><br /><br /> <span data-ttu-id="f97bf-118">-   **Service réseau** (la valeur par défaut), qui a des droits d’accès utilisateur de niveau inférieur qui peuvent être utilisés pour accéder aux ressources sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="f97bf-118">-   **Network Service** (the default), which has low-level user access rights that can be used for access to resources on remote computers.</span></span><br /><span data-ttu-id="f97bf-119">-   **Service local**, ce qui a des droits d’accès de bas niveau.</span><span class="sxs-lookup"><span data-stu-id="f97bf-119">-   **Local Service**, which has low-level access rights.</span></span> <span data-ttu-id="f97bf-120">Vous utilisez ce paramètre pour les situations qui ne nécessitent pas d’accès aux ressources sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="f97bf-120">You use this setting for situations that do not require access to resources on remote computers.</span></span><br /><span data-ttu-id="f97bf-121">-   **Système local**, qui est un compte avec des droits d’utilisateur plus que le compte Service réseau ou Service Local.</span><span class="sxs-lookup"><span data-stu-id="f97bf-121">-   **Local System**, which is an account with more user rights than the Network Service or Local Service account.</span></span>|  
    |<span data-ttu-id="f97bf-122">**Configurable**</span><span class="sxs-lookup"><span data-stu-id="f97bf-122">**Configurable**</span></span>|<span data-ttu-id="f97bf-123">Sélectionnez **Configurable**.</span><span class="sxs-lookup"><span data-stu-id="f97bf-123">Select **Configurable**.</span></span> <span data-ttu-id="f97bf-124">**Configurable** fait référence aux noms d’utilisateur inscrit.</span><span class="sxs-lookup"><span data-stu-id="f97bf-124">**Configurable** refers to registered user names.</span></span>|  
    |<span data-ttu-id="f97bf-125">**Nom d'utilisateur**</span><span class="sxs-lookup"><span data-stu-id="f97bf-125">**User name**</span></span>|<span data-ttu-id="f97bf-126">Tapez le nom d’utilisateur du compte sous lequel le processus de travail de fonctionner.</span><span class="sxs-lookup"><span data-stu-id="f97bf-126">Type the user name of the account under which you want the worker process to operate.</span></span>|  
    |<span data-ttu-id="f97bf-127">**Mot de passe**</span><span class="sxs-lookup"><span data-stu-id="f97bf-127">**Password**</span></span>|<span data-ttu-id="f97bf-128">Tapez le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="f97bf-128">Type the password.</span></span>|  
  
5.  <span data-ttu-id="f97bf-129">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f97bf-129">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f97bf-130">Ou bien, pour une sécurité accrue, vous pouvez créer un nouveau pool d’applications qui s’exécute sous une identité personnalisée que vous créez avec des autorisations personnalisées pour ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="f97bf-130">Alternatively, for increased security, you could create an entirely new application pool that runs under a custom identity that you create with permissions tailored for this tutorial.</span></span>  
  
 <span data-ttu-id="f97bf-131">Passez à [étape 2 : créer un nouveau projet](../../adapters-and-accelerators/accelerator-hl7/step-2-create-a-new-project.md).</span><span class="sxs-lookup"><span data-stu-id="f97bf-131">Proceed to [Step 2: Create a New Project](../../adapters-and-accelerators/accelerator-hl7/step-2-create-a-new-project.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f97bf-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f97bf-132">See Also</span></span>  
 [<span data-ttu-id="f97bf-133">Didacticiel d’enrichissement de message</span><span class="sxs-lookup"><span data-stu-id="f97bf-133">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)