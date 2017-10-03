---
title: "Comment supprimer une Application associée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [SSO], deleting
- managing [SSO applications], deleting
- deleting, applications [SSO]
ms.assetid: c7ec065e-ef10-49ff-a350-105dd08dc4a9
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ddb40109ff402f1c1794a90e591a43e11407fba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-delete-an-affiliate-application"></a><span data-ttu-id="17f0d-102">Comment supprimer une Application associée</span><span class="sxs-lookup"><span data-stu-id="17f0d-102">How to Delete an Affiliate Application</span></span>
<span data-ttu-id="17f0d-103">Le composant logiciel enfichable MMC ou la ligne de commande permet de supprimer une application associée de la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="17f0d-103">You can use the MMC Snap-In or the command line to delete the specified affiliate application from the SSO database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="17f0d-104">Lorsque vous supprimez une application associée, le système SSO supprime automatiquement tous les mappages qui y sont associés.</span><span class="sxs-lookup"><span data-stu-id="17f0d-104">When you delete an affiliate application, the SSO system automatically deletes all mappings associated with it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="17f0d-105">Pour effectuer cette tâche, vous devez être un administrateur SSO ou un administrateur d'applications associées à SSO.</span><span class="sxs-lookup"><span data-stu-id="17f0d-105">You must be an SSO administrator or SSO affiliate administrator to perform this task.</span></span>  
  
### <a name="to-delete-an-affiliate-application-using-the-mmc-snap-in"></a><span data-ttu-id="17f0d-106">Pour supprimer une application associée à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="17f0d-106">To delete an affiliate application using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="17f0d-107">Sur le **Démarrer** menu, cliquez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="17f0d-107">On the **Start** menu, click **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="17f0d-108">Dans le volet d’étendue du composant logiciel enfichable MMC, développez le **Enterprise Single Sign-On** nœud.</span><span class="sxs-lookup"><span data-stu-id="17f0d-108">In the scope pane of the MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="17f0d-109">Cliquez sur l’application associée, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="17f0d-109">Right-click the affiliate application, and then click **Delete**.</span></span>  
  
### <a name="to-delete-an-affiliate-application-using-the-command-line"></a><span data-ttu-id="17f0d-110">Pour supprimer une application associée à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="17f0d-110">To delete an affiliate application using the command line</span></span>  
  
1.  <span data-ttu-id="17f0d-111">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="17f0d-111">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="17f0d-112">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="17f0d-112">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="17f0d-113">Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="17f0d-113">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="17f0d-114">Type **ssomanage-deleteapp  *\<nom de l’application >***, où  *\<nom de l’application >* est le nom de l’application associée vous vous souhaitez supprimer de la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="17f0d-114">Type **ssomanage –deleteapp *\<application name>***, where *\<application name>* is the name of the affiliate application you want to remove from the SSO database.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="17f0d-115">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="17f0d-115">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17f0d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17f0d-116">See Also</span></span>  
 <span data-ttu-id="17f0d-117">[Applications associées SSO](../core/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="17f0d-117">[SSO Affiliate Applications](../core/sso-affiliate-applications.md) </span></span>  
 <span data-ttu-id="17f0d-118">[Comment activer une Application associée](../core/how-to-enable-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="17f0d-118">[How to Enable an Affiliate Application](../core/how-to-enable-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="17f0d-119">[Gestion des mappages utilisateur](../core/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="17f0d-119">[Managing User Mappings](../core/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="17f0d-120">Gestion des Applications associées</span><span class="sxs-lookup"><span data-stu-id="17f0d-120">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)