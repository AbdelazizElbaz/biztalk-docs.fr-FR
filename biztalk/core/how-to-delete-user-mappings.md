---
title: Comment supprimer des mappages utilisateur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maps [SSO], deleting
- managing [SSO maps], deleting user maps
ms.assetid: de511113-b0b0-4920-91dc-4c9e380fda58
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03f7c1fa75b6fe7bb4c78e18c97fccd1404f89c9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-delete-user-mappings"></a><span data-ttu-id="b5fb6-102">Comment supprimer des mappages utilisateur</span><span class="sxs-lookup"><span data-stu-id="b5fb6-102">How to Delete User Mappings</span></span>
<span data-ttu-id="b5fb6-103">Ces commandes permettent de supprimer un ou plusieurs mappages utilisateur, comme décrit dans le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="b5fb6-103">Use these commands to delete one or more user mappings, as specified in the XML file.</span></span> <span data-ttu-id="b5fb6-104">Voici un exemple de fichier XML.</span><span class="sxs-lookup"><span data-stu-id="b5fb6-104">The following is an example XML file.</span></span>  
  
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
  
 <span data-ttu-id="b5fb6-105">Si un utilisateur n'est pas membre du compte Utilisateurs d'applications ou n'existe pas dans Active Directory, vous devez utiliser cette commande pour supprimer le mappage utilisateur de la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="b5fb6-105">If a user is not a member of the Application Users account, or does not exist in Active Directory, you should use this command to remove the user mapping from the SSO database.</span></span>  
  
 <span data-ttu-id="b5fb6-106">Si un compte d'utilisateur est modifié, vous devez utiliser cette commande pour supprimer les anciens mappages utilisateur, puis créer un mappage utilisateur pour le nouveau compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b5fb6-106">If a user account is changed, you must use this command to remove the old user mapping, and then create a new user mapping for the new user account.</span></span> <span data-ttu-id="b5fb6-107">Pour plus d’informations sur la création d’un mappage, consultez [comment créer des mappages utilisateur](../core/how-to-create-user-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="b5fb6-107">For more information about creating a mapping, see [How to Create User Mappings](../core/how-to-create-user-mappings.md).</span></span>  
  
### <a name="to-delete-user-mappings-using-the-administration-utility"></a><span data-ttu-id="b5fb6-108">Pour supprimer des mappages utilisateur à l'aide de l'utilitaire d'administration</span><span class="sxs-lookup"><span data-stu-id="b5fb6-108">To delete user mappings using the administration utility</span></span>  
  
1.  <span data-ttu-id="b5fb6-109">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="b5fb6-109">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="b5fb6-110">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="b5fb6-110">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="b5fb6-111">Le répertoire d’installation par défaut est \< *lecteur*\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="b5fb6-111">The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="b5fb6-112">Type **ssomanage – deletemappings  *\<nom de fichier de mappage\>***, où \< *nom de fichier de mappage* \> est le nom du fichier qui contient les ou les mappages utilisateur que vous souhaitez supprimer.</span><span class="sxs-lookup"><span data-stu-id="b5fb6-112">Type **ssomanage –deletemappings *\<mappings file name\>***, where \<*mappings file name*\> is the name of the file that contains the user mapping(s) you want to delete.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b5fb6-113">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="b5fb6-113">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-delete-a-specific-user-mapping-using-the-administration-utility"></a><span data-ttu-id="b5fb6-114">Pour supprimer un mappage utilisateur spécifique à l'aide de l'utilitaire d'administration</span><span class="sxs-lookup"><span data-stu-id="b5fb6-114">To delete a specific user mapping using the administration utility</span></span>  
  
1.  <span data-ttu-id="b5fb6-115">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="b5fb6-115">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="b5fb6-116">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="b5fb6-116">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="b5fb6-117">Le répertoire d’installation par défaut est  *\<lecteur*\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="b5fb6-117">The default installation directory is *\<drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="b5fb6-118">Type  **ssomanage-deletemapping  *\<domaine\>*\\*\<nom d’utilisateur\>*   *\<nom de l’application\>***, où  *\<domaine\>*  correspond au domaine Windows pour le compte d’utilisateur,  *\<nom d’utilisateur\>*  est le nom d’utilisateur Windows et \<* nom de l’application* \> l’application spécifique pour lequel vous souhaitez supprimer le mappage utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b5fb6-118">Type **ssomanage –deletemapping *\<domain\>*\\*\<username\>* *\<application name\>***, where *\<domain\>* is the Windows domain for the user account, *\<username\>* is the Windows user name, and \<*application name*\> is the specific application for which you want to remove the user mapping.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b5fb6-119">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="b5fb6-119">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-delete-a-user-mapping-using-the-client-utility"></a><span data-ttu-id="b5fb6-120">Pour supprimer un mappage utilisateur à l'aide de l'utilitaire client</span><span class="sxs-lookup"><span data-stu-id="b5fb6-120">To delete a user mapping using the client utility</span></span>  
  
1.  <span data-ttu-id="b5fb6-121">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="b5fb6-121">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="b5fb6-122">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="b5fb6-122">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="b5fb6-123">Le répertoire d’installation par défaut est  *\<lecteur*\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="b5fb6-123">The default installation directory is *\<drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="b5fb6-124">Type **ssoclient – deletemapping  *\<nom de l’application\>***, où  *\<nom de l’application\>*  est le nom de l’application associée que vous souhaitez supprimer le mappage utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b5fb6-124">Type **ssoclient –deletemapping *\<application name\>***, where *\<application name\>* is the name of the affiliate application you want to remove the user mapping for.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b5fb6-125">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="b5fb6-125">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5fb6-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5fb6-126">See Also</span></span>  
 <span data-ttu-id="b5fb6-127">[Mappages SSO](../core/sso-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="b5fb6-127">[SSO Mappings](../core/sso-mappings.md) </span></span>  
 <span data-ttu-id="b5fb6-128">[Gestion des Applications associées](../core/managing-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="b5fb6-128">[Managing Affiliate Applications](../core/managing-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="b5fb6-129">Gestion des mappages utilisateur</span><span class="sxs-lookup"><span data-stu-id="b5fb6-129">Managing User Mappings</span></span>](../core/managing-user-mappings.md)