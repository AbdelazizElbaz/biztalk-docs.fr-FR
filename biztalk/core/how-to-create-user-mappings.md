---
title: Comment créer des mappages utilisateur | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maps [SSO], creating
- managing [SSO maps], creating user maps
ms.assetid: c2e9f0db-920b-4d89-8e1e-5dc92805fd23
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 019adf0cd41c643ac77790c96a3450bb967ddd6b
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-create-user-mappings"></a><span data-ttu-id="e0ea0-102">Comment créer des mappages utilisateur</span><span class="sxs-lookup"><span data-stu-id="e0ea0-102">How to Create User Mappings</span></span>
<span data-ttu-id="e0ea0-103">Cette commande permet de créer un ou plusieurs mappages utilisateur, comme décrit dans le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="e0ea0-103">Use this command to create one or more user mappings, as specified in the XML file.</span></span> <span data-ttu-id="e0ea0-104">Voici un exemple de fichier XML.</span><span class="sxs-lookup"><span data-stu-id="e0ea0-104">The following is an example XML file.</span></span>  
  
```  
<sso>  
<mapping>  
<windowsDomain>domain</windowsDomain>   
<windowsUserId>WindowsUserName</windowsUserId>   
<externalApplication>Application name1</externalApplication>   
<externalUserId>App1UserName</externalUserId>   
</mapping>  
<mapping>  
<windowsDomain>domain</windowsDomain>   
<windowsUserId>WindowsUserName</windowsUserId>   
<externalApplication>Application name2</externalApplication>   
<externalUserId>App2UserName</externalUserId>   
</mapping>  
</sso>  
  
```  
  
 <span data-ttu-id="e0ea0-105">Si un compte d'utilisateur est modifié, vous devez utiliser cette commande pour créer un mappage pour le nouveau compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e0ea0-105">If a user account is changed, you must use this command to create a mapping for the new user account.</span></span> <span data-ttu-id="e0ea0-106">Vous devez également supprimer l'ancien mappage utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e0ea0-106">You should also remove the old user mapping.</span></span> <span data-ttu-id="e0ea0-107">Pour plus d’informations sur la suppression d’un mappage, consultez [comment supprimer des mappages utilisateur](../core/how-to-delete-user-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="e0ea0-107">For more information about removing a mapping, see [How to Delete User Mappings](../core/how-to-delete-user-mappings.md).</span></span>  
  
 <span data-ttu-id="e0ea0-108">Après avoir créé un mappage utilisateur, vous devez l'activer avant de pouvoir l'utiliser dans le système d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="e0ea0-108">After you create a user mapping, you must enable it before you can use this mapping in the SSO system.</span></span> <span data-ttu-id="e0ea0-109">Pour plus d’informations, consultez [comment activer un mappage utilisateur](../core/how-to-enable-a-user-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="e0ea0-109">For more information, see [How to Enable a User Mapping](../core/how-to-enable-a-user-mapping.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e0ea0-110">Seuls les groupes de domaine sont pris en charge avec les mappages utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e0ea0-110">Only domain groups are supported for user mappings.</span></span>  
  
### <a name="to-create-user-mappings-using-the-administration-utility"></a><span data-ttu-id="e0ea0-111">Pour créer des mappages utilisateur à l'aide de l'utilitaire d'administration</span><span class="sxs-lookup"><span data-stu-id="e0ea0-111">To create user mappings using the administration utility</span></span>  
  
1.  <span data-ttu-id="e0ea0-112">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="e0ea0-112">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="e0ea0-113">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="e0ea0-113">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="e0ea0-114">Le répertoire d’installation par défaut est \< *lecteur*\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="e0ea0-114">The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="e0ea0-115">Type ** ssomanage – createmappings *\<nom de fichier de mappage\>***, où *\<nom de fichier de mappage\>* est le nom du fichier qui contient les ou les mappages utilisateur que vous souhaitez créer.</span><span class="sxs-lookup"><span data-stu-id="e0ea0-115">Type **ssomanage –createmappings *\<mappings file name\>***, where *\<mappings file name\>* is the name of file that contains the user mapping(s) you want to create.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e0ea0-116">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="e0ea0-116">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-create-user-mappings-using-the-client-utility"></a><span data-ttu-id="e0ea0-117">Pour créer des mappages utilisateur à l'aide de l'utilitaire client</span><span class="sxs-lookup"><span data-stu-id="e0ea0-117">To create user mappings using the client utility</span></span>  
  
1.  <span data-ttu-id="e0ea0-118">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="e0ea0-118">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="e0ea0-119">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="e0ea0-119">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="e0ea0-120">Le répertoire d’installation par défaut est \< *lecteur*\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="e0ea0-120">The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="e0ea0-121">Type ** ssoclient – setcredentials *\<nom de l’application \>***, où *\<nom de l’application \>* est le nom de l’application associée que l’utilisateur souhaite créer un mappage pour.</span><span class="sxs-lookup"><span data-stu-id="e0ea0-121">Type **ssoclient –setcredentials *\<application name \>***, where *\<application name \>* is the name of affiliate application that the user wants to create a mapping for.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e0ea0-122">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="e0ea0-122">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0ea0-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0ea0-123">See Also</span></span>  
 <span data-ttu-id="e0ea0-124">[Mappages SSO](../core/sso-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="e0ea0-124">[SSO Mappings](../core/sso-mappings.md) </span></span>  
 <span data-ttu-id="e0ea0-125">[Gestion des Applications associées](../core/managing-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="e0ea0-125">[Managing Affiliate Applications](../core/managing-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="e0ea0-126">Gestion des mappages utilisateur</span><span class="sxs-lookup"><span data-stu-id="e0ea0-126">Managing User Mappings</span></span>](../core/managing-user-mappings.md)