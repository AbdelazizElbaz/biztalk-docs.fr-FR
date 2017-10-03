---
title: "Comment modifier le nom d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- naming conventions, renaming
- naming conventions, applications
- applications, renaming
ms.assetid: ae59c792-44bd-43e0-a4ae-e67bcad2e128
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4826688935bf18cd5288924d4544f484b3dcf0cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-change-the-name-of-an-application"></a><span data-ttu-id="ef200-102">Changement du nom d'une application</span><span class="sxs-lookup"><span data-stu-id="ef200-102">How to Change the Name of an Application</span></span>
<span data-ttu-id="ef200-103">Cette rubrique explique comment changer le nom d'une application à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="ef200-103">This topic describes how to use the BizTalk Server Administration console to change the name of an application.</span></span> <span data-ttu-id="ef200-104">Le nom d'application que vous utilisez ne doit pas déjà exister dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="ef200-104">The application name that you use cannot already exist in the group.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef200-105">Si vous avez exporté un fichier .msi pour une application qui a une référence à l'application renommée, cette référence ne fonctionnera plus lorsque vous importerez le fichier.</span><span class="sxs-lookup"><span data-stu-id="ef200-105">If you have exported an .msi file for an application that has a reference to the renamed application, the reference will no longer function when you import the .msi file.</span></span> <span data-ttu-id="ef200-106">Vous devrez mettre la référence à jour avec le nouveau nom d'application.</span><span class="sxs-lookup"><span data-stu-id="ef200-106">You will need to update the reference with the new application name.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ef200-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="ef200-107">Prerequisites</span></span>  
 <span data-ttu-id="ef200-108">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="ef200-108">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="ef200-109">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="ef200-109">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-change-the-name-of-an-application"></a><span data-ttu-id="ef200-110">Pour changer le nom d'une application</span><span class="sxs-lookup"><span data-stu-id="ef200-110">To change the name of an application</span></span>  
  
1.  <span data-ttu-id="ef200-111">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="ef200-111">Click **Start**, point to **Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="ef200-112">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, cliquez sur l’application dont vous souhaitez modifier, puis cliquez sur le nom **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="ef200-112">In the console tree, expand  **BizTalk Server Administration**, right-click the application whose name you want to change, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="ef200-113">Dans le **nom** zone, tapez un nouveau nom pour l’application, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ef200-113">In the **Name** box, type a new name for the application, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef200-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef200-114">See Also</span></span>  
 [<span data-ttu-id="ef200-115">Création et modification des Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="ef200-115">Creating and Modifying BizTalk Applications</span></span>](../core/creating-and-modifying-biztalk-applications.md)