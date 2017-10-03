---
title: "Comment supprimer une référence à une autre Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: applications, references
ms.assetid: cc867706-7c56-4386-b7ec-9fd7cf6c83a4
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de51adb1a9c42874025527ad458ecb6e3c311b3f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-reference-to-another-application"></a><span data-ttu-id="5839f-102">Suppression d'une référence à une autre application</span><span class="sxs-lookup"><span data-stu-id="5839f-102">How to Remove a Reference to Another Application</span></span>
<span data-ttu-id="5839f-103">La présente rubrique explique comment supprimer une référence d'une application à une autre application à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="5839f-103">This topic describes how to use the BizTalk Server Administration console to remove a reference from one application to another application.</span></span> <span data-ttu-id="5839f-104">Vous supprimez une référence lorsque vous n'avez plus besoin, dans l'application actuelle, d'un artefact existant déjà dans une autre application du même groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5839f-104">You remove a reference when you no longer need to use an artifact in the current application that exists in another application in the same BizTalk group.</span></span> <span data-ttu-id="5839f-105">Pour plus d’informations sur l’ajout de références, consultez [comment ajouter une référence à une autre Application](../core/how-to-add-a-reference-to-another-application.md).</span><span class="sxs-lookup"><span data-stu-id="5839f-105">For more information on adding references, see [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).</span></span>  
  
 <span data-ttu-id="5839f-106">Dans l'application actuelle, si des artefacts utilisent toujours des artefacts dans l'application référencée, l'opération de suppression de la référence échouera.</span><span class="sxs-lookup"><span data-stu-id="5839f-106">If artifacts in the current application still use artifacts in the referenced application, the operation to remove the reference will fail.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="5839f-107">Toute application BizTalk Server contient automatiquement une référence à l'application BizTalk.System.</span><span class="sxs-lookup"><span data-stu-id="5839f-107">Every application in BizTalk Server automatically contains a reference to the BizTalk.System application.</span></span> <span data-ttu-id="5839f-108">Ceci est dû au fait que les artefacts que contient BizTalk.System sont utilisés par toutes les applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5839f-108">This is because the artifacts that BizTalk.System contains are used by every BizTalk application.</span></span> <span data-ttu-id="5839f-109">Vous ne devez jamais supprimer une référence à l'application BizTalk.System.</span><span class="sxs-lookup"><span data-stu-id="5839f-109">You should never remove a reference to the BizTalk.System application.</span></span> <span data-ttu-id="5839f-110">Votre application risquerait sinon de ne plus fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="5839f-110">If you do, your application may not function correctly.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5839f-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="5839f-111">Prerequisites</span></span>  
 <span data-ttu-id="5839f-112">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="5839f-112">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="5839f-113">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="5839f-113">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-remove-a-reference-to-another-application"></a><span data-ttu-id="5839f-114">Pour supprimer une référence à une autre application</span><span class="sxs-lookup"><span data-stu-id="5839f-114">To remove a reference to another application</span></span>  
  
1.  <span data-ttu-id="5839f-115">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="5839f-115">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="5839f-116">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, cliquez sur l’application à partir de laquelle vous souhaitez supprimer une référence (celle qui fait référence à une autre application), puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5839f-116">In the console tree, expand  **BizTalk Server Administration**, right-click the application from which you want to remove a reference (the one that refers to another application), and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="5839f-117">Dans le volet gauche de la page de propriétés, cliquez sur **références**.</span><span class="sxs-lookup"><span data-stu-id="5839f-117">In the left pane of the properties page, click **References**.</span></span>  
  
4.  <span data-ttu-id="5839f-118">Dans le volet droit, cliquez sur l’application que vous ne souhaitez plus faire référence à partir de cette application, cliquez sur **supprimer**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5839f-118">In the right pane, click the application that you no longer want to reference from this application, click **Remove**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5839f-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5839f-119">See Also</span></span>  
 [<span data-ttu-id="5839f-120">Création et modification des Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="5839f-120">Creating and Modifying BizTalk Applications</span></span>](../core/creating-and-modifying-biztalk-applications.md)