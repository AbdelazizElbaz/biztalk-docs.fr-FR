---
title: "Comment répertorier les Applications associées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO applications], listing applications
- applications [SSO], listing applications
ms.assetid: b51ff597-824e-4488-a47f-3a9b3d4437c6
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f6c4d4e4118bfe5f5cab7a9c44e770dd12656c7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-list-affiliate-applications"></a><span data-ttu-id="d613e-102">Comment répertorier les Applications associées</span><span class="sxs-lookup"><span data-stu-id="d613e-102">How to List Affiliate Applications</span></span>
<span data-ttu-id="d613e-103">Cette commande permet de répertorier toutes les applications associées.</span><span class="sxs-lookup"><span data-stu-id="d613e-103">Use this command to list all the affiliate applications.</span></span> <span data-ttu-id="d613e-104">Si l'utilisateur est membre du compte Administrateurs d’application, cette commande affiche uniquement l'application dont il est administrateur.</span><span class="sxs-lookup"><span data-stu-id="d613e-104">If the user is a member of the Application Administrators account, this command will only display the application for which the user is an administrator.</span></span>  
  
### <a name="to-list-affiliate-applications-using-the-administration-utility"></a><span data-ttu-id="d613e-105">Pour répertorier les applications associées à l'aide de l'utilitaire d'administration</span><span class="sxs-lookup"><span data-stu-id="d613e-105">To list affiliate applications using the administration utility</span></span>  
  
1.  <span data-ttu-id="d613e-106">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="d613e-106">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="d613e-107">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="d613e-107">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="d613e-108">Le répertoire d’installation par défaut est \< *lecteur*\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="d613e-108">The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="d613e-109">Type **ssomanage - listapps [all]** où **tous les** est un paramètre optionnel qui affiche également des applications à l’aide de la fonctionnalité de magasin de Configuration.</span><span class="sxs-lookup"><span data-stu-id="d613e-109">Type **ssomanage -listapps [all]** where **all** is an optional parameter that will also display applications using the Configuration Store feature.</span></span> <span data-ttu-id="d613e-110">Si l'utilisateur exécutant cette commande est un administrateur d'applications, la commande répertorie uniquement les applications dont il est administrateur.</span><span class="sxs-lookup"><span data-stu-id="d613e-110">If the user running this command is an Application administrator, it will only list the applications for which they are an administrator.</span></span> <span data-ttu-id="d613e-111">Si l’utilisateur qui exécute cette commande est un administrateur d’applications associées ou un administrateur SSO, il répertorie toutes les applications associées.</span><span class="sxs-lookup"><span data-stu-id="d613e-111">If the user running this command is an Affiliate Administrator or an SSO Administrator, it will list all the affiliate applications.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d613e-112">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="d613e-112">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-list-affiliate-applications-using-the-client-utility"></a><span data-ttu-id="d613e-113">Pour répertorier les applications associées à l'aide de l'utilitaire client</span><span class="sxs-lookup"><span data-stu-id="d613e-113">To list affiliate applications using the client utility</span></span>  
  
1.  <span data-ttu-id="d613e-114">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="d613e-114">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="d613e-115">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="d613e-115">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="d613e-116">Le répertoire d’installation par défaut est \< *lecteur*\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="d613e-116">The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="d613e-117">Type **ssoclient – listapps** pour répertorier les applications associées.</span><span class="sxs-lookup"><span data-stu-id="d613e-117">Type **ssoclient –listapps** to list the affiliate applications.</span></span> <span data-ttu-id="d613e-118">Cela a pour effet de répertorier uniquement les applications associées dont l'utilisateur exécutant cette tâche est membre. Par exemple, l'utilisateur doit appartenir au compte du groupe d'utilisateurs de l'application pour cette application associée.</span><span class="sxs-lookup"><span data-stu-id="d613e-118">This will list only the affiliate applications that the user performing this task is a member of, i.e., they need to belong the application user group account for that affiliate application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d613e-119">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="d613e-119">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d613e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d613e-120">See Also</span></span>  
 <span data-ttu-id="d613e-121">[Applications associées SSO](../core/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="d613e-121">[SSO Affiliate Applications](../core/sso-affiliate-applications.md) </span></span>  
 <span data-ttu-id="d613e-122">[Comment créer une Application associée](../core/how-to-create-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="d613e-122">[How to Create an Affiliate Application](../core/how-to-create-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="d613e-123">[Gestion des mappages utilisateur](../core/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="d613e-123">[Managing User Mappings](../core/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="d613e-124">Gestion des applications associées</span><span class="sxs-lookup"><span data-stu-id="d613e-124">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)