---
title: "Comment afficher les dépendances d’un Assembly BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- viewing, dependencies
- assemblies, dependencies
- managing [assemblies], dependencies
- assemblies, viewing
- viewing, assemblies
- managing [assemblies], viewing
ms.assetid: 872abc99-8248-4397-9fcb-24a0ba6f4757
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99fbc09a5adb59691a4914a8ddc341c8034c8bb8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-view-the-dependencies-for-a-biztalk-assembly"></a><span data-ttu-id="a03b2-102">Affichage des dépendances d'un assembly BizTalk</span><span class="sxs-lookup"><span data-stu-id="a03b2-102">How to View the Dependencies for a BizTalk Assembly</span></span>
<span data-ttu-id="a03b2-103">Cette rubrique explique comment afficher la liste des artefacts dépendants d'un assembly BizTalk à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a03b2-103">This topic describes how to use the BizTalk Server Administration console to view the list of artifacts that have dependencies on a BizTalk assembly.</span></span> <span data-ttu-id="a03b2-104">Pour plus d’informations générales sur les dépendances et comment ils affectent le déploiement d’application, consultez [des dépendances et déploiement d’applications](../core/dependencies-and-application-deployment.md).</span><span class="sxs-lookup"><span data-stu-id="a03b2-104">For background information about dependencies and how they affect application deployment, see [Dependencies and Application Deployment](../core/dependencies-and-application-deployment.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a03b2-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="a03b2-105">Prerequisites</span></span>  
 <span data-ttu-id="a03b2-106">Pour exécuter cette procédure, vous devez avoir ouvert une session en tant que membre du groupe des opérateurs de BizTalk ou du groupe d'administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a03b2-106">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group or BizTalk Operators group.</span></span> <span data-ttu-id="a03b2-107">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="a03b2-107">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-view-the-dependencies-of-a-biztalk-assembly"></a><span data-ttu-id="a03b2-108">Pour afficher les dépendances d'un assembly BizTalk</span><span class="sxs-lookup"><span data-stu-id="a03b2-108">To view the dependencies of a BizTalk assembly</span></span>  
  
1.  <span data-ttu-id="a03b2-109">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="a03b2-109">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a03b2-110">Dans l'arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], le groupe BizTalk contenant l'assembly BizTalk dont vous souhaitez afficher les dépendances, puis l'application le contenant.</span><span class="sxs-lookup"><span data-stu-id="a03b2-110">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group containing the BizTalk assembly for which you want to view dependencies, and then expand the application containing the BizTalk assembly.</span></span>  
  
3.  <span data-ttu-id="a03b2-111">Cliquez sur le **ressources** dossier, cliquez sur l’assembly BizTalk, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="a03b2-111">Click the **Resources** folder, right-click the BizTalk assembly, and then click **Modify**.</span></span>  
  
4.  <span data-ttu-id="a03b2-112">Cliquez sur le **dépendances** onglet.</span><span class="sxs-lookup"><span data-stu-id="a03b2-112">Click the **Dependencies** tab.</span></span>  
  
     <span data-ttu-id="a03b2-113">Le nom et l'état des artefacts dépendants de cet assembly BizTalk s'affichent dans la liste.</span><span class="sxs-lookup"><span data-stu-id="a03b2-113">The name and status of the artifacts that have dependencies on this BizTalk assembly are displayed in the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a03b2-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a03b2-114">See Also</span></span>  
 [<span data-ttu-id="a03b2-115">Gestion des assemblys BizTalk</span><span class="sxs-lookup"><span data-stu-id="a03b2-115">Managing BizTalk Assemblies</span></span>](../core/managing-biztalk-assemblies.md)