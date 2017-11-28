---
title: "Comment afficher les références d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, viewing
- applications, referencing
ms.assetid: 5f1026e1-c73e-495d-8160-9ba68f38b9d8
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 249e7432216368113e916118910acb6a4e11e415
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-view-the-references-of-an-application"></a><span data-ttu-id="fe0b2-102">Affichage des références d'une application</span><span class="sxs-lookup"><span data-stu-id="fe0b2-102">How to View the References of an Application</span></span>
<span data-ttu-id="fe0b2-103">Cette rubrique explique comment afficher la liste des applications pour lesquelles l'application active possède des références à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="fe0b2-103">This topic describes how to use the BizTalk Server Administration console to view the list of applications to which the current application has references.</span></span> <span data-ttu-id="fe0b2-104">Pour plus d’informations sur l’ajout de références, consultez [comment ajouter une référence à une autre Application](../core/how-to-add-a-reference-to-another-application.md).</span><span class="sxs-lookup"><span data-stu-id="fe0b2-104">For more information about adding references, see [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).</span></span> <span data-ttu-id="fe0b2-105">Vous pouvez également afficher la liste des applications qui possèdent des références à cette application active.</span><span class="sxs-lookup"><span data-stu-id="fe0b2-105">You can also view the list of applications that have references to this application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fe0b2-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="fe0b2-106">Prerequisites</span></span>  
 <span data-ttu-id="fe0b2-107">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="fe0b2-107">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="fe0b2-108">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="fe0b2-108">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-view-the-references-for-an-application"></a><span data-ttu-id="fe0b2-109">Pour afficher les références d'une application</span><span class="sxs-lookup"><span data-stu-id="fe0b2-109">To view the references for an application</span></span>  
  
1.  <span data-ttu-id="fe0b2-110">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="fe0b2-110">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="fe0b2-111">Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], cliquez sur l’application dont vous souhaitez afficher, puis cliquez sur les références **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="fe0b2-111">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click the application whose references you want to view, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="fe0b2-112">Dans le volet gauche de la page de propriétés, cliquez sur **références**.</span><span class="sxs-lookup"><span data-stu-id="fe0b2-112">In the left pane of the properties page, click **References**.</span></span>  
  
     <span data-ttu-id="fe0b2-113">Les applications auxquelles fait référence cette application sont répertoriées dans la partie supérieure du volet droit.</span><span class="sxs-lookup"><span data-stu-id="fe0b2-113">The applications to which this application refers are listed in the upper section of the right pane.</span></span> <span data-ttu-id="fe0b2-114">Les applications faisant référence à cette application sont répertoriées dans la partie inférieure du volet droit.</span><span class="sxs-lookup"><span data-stu-id="fe0b2-114">The applications that refer to this application are listed in the lower section of the right pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe0b2-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe0b2-115">See Also</span></span>  
 [<span data-ttu-id="fe0b2-116">Création et modification des Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="fe0b2-116">Creating and Modifying BizTalk Applications</span></span>](../core/creating-and-modifying-biztalk-applications.md)