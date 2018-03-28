---
title: Comment supprimer des mappages utilisateur | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c4cdff-b82d-4cfd-8e20-220a2fe78656
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: a9d0a31c3dbc9d5980f59d9f30d20ec15f603a38
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-delete-user-mappings"></a><span data-ttu-id="1a68d-102">Comment supprimer des mappages utilisateur</span><span class="sxs-lookup"><span data-stu-id="1a68d-102">How to Delete User Mappings</span></span>
<span data-ttu-id="1a68d-103">Ces commandes permettent de supprimer un ou plusieurs mappages utilisateur, comme décrit dans le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="1a68d-103">Use these commands to delete one or more user mappings, as specified in the XML file.</span></span> <span data-ttu-id="1a68d-104">Voici un exemple de fichier XML.</span><span class="sxs-lookup"><span data-stu-id="1a68d-104">The following is an example XML file.</span></span>  
  
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
  
 <span data-ttu-id="1a68d-105">Si un utilisateur n’est pas membre du compte utilisateurs d’applications, ou il n’existe pas dans Active Directory, vous devez utiliser cette commande pour supprimer le mappage utilisateur à partir de la base de données d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="1a68d-105">If a user is not a member of the Application Users account, or does not exist in Active Directory, you should use this command to remove the user mapping from the Credential database.</span></span>  
  
 <span data-ttu-id="1a68d-106">Si un compte d'utilisateur est modifié, vous devez utiliser cette commande pour supprimer les anciens mappages utilisateur, puis créer un mappage utilisateur pour le nouveau compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1a68d-106">If a user account is changed, you must use this command to remove the old user mapping, and then create a new user mapping for the new user account.</span></span> <span data-ttu-id="1a68d-107">Pour plus d’informations sur la création d’un mappage, consultez [comment créer des mappages utilisateur](../esso/how-to-create-user-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="1a68d-107">For more information about creating a mapping, see [How to Create User Mappings](../esso/how-to-create-user-mappings.md).</span></span>  
  
### <a name="to-delete-user-mappings-using-the-administration-utility"></a><span data-ttu-id="1a68d-108">Pour supprimer des mappages utilisateur à l'aide de l'utilitaire d'administration</span><span class="sxs-lookup"><span data-stu-id="1a68d-108">To delete user mappings using the administration utility</span></span>  
  
1.  <span data-ttu-id="1a68d-109">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="1a68d-109">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="1a68d-110">À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="1a68d-110">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="1a68d-111">Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="1a68d-111">The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="1a68d-112">Type `ssomanage –deletemappings <mappings file name>`, où \< *nom de fichier de mappage*> est le nom du fichier qui contient les mappages utilisateur que vous souhaitez supprimer.</span><span class="sxs-lookup"><span data-stu-id="1a68d-112">Type `ssomanage –deletemappings <mappings file name>`, where \<*mappings file name*> is the name of the file that contains the user mappings that you want to delete.</span></span>  
  
### <a name="to-delete-a-specific-user-mapping-using-the-administration-utility"></a><span data-ttu-id="1a68d-113">Pour supprimer un mappage utilisateur spécifique à l'aide de l'utilitaire d'administration</span><span class="sxs-lookup"><span data-stu-id="1a68d-113">To delete a specific user mapping using the administration utility</span></span>  
  
1.  <span data-ttu-id="1a68d-114">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="1a68d-114">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="1a68d-115">À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="1a68d-115">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="1a68d-116">Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="1a68d-116">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="1a68d-117">Type `ssomanage –deletemapping <domain>\<username> <application name>`, où  *\<domaine >* correspond au domaine Windows pour le compte d’utilisateur,  *\<nom d’utilisateur >* est le nom d’utilisateur Windows et \< *nom de l’application*> est l’application spécifique pour lequel vous souhaitez supprimer le mappage utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1a68d-117">Type `ssomanage –deletemapping <domain>\<username> <application name>`, where *\<domain>* is the Windows domain for the user account, *\<username>* is the Windows user name, and \<*application name*> is the specific application for which you want to remove the user mapping.</span></span>  
  
### <a name="to-delete-a-user-mapping-using-the-client-utility"></a><span data-ttu-id="1a68d-118">Pour supprimer un mappage utilisateur à l'aide de l'utilitaire client</span><span class="sxs-lookup"><span data-stu-id="1a68d-118">To delete a user mapping using the client utility</span></span>  
  
1.  <span data-ttu-id="1a68d-119">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="1a68d-119">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="1a68d-120">À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="1a68d-120">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="1a68d-121">Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="1a68d-121">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="1a68d-122">Type `ssoclient –deletemapping <application name>`, où  *\<nom de l’application >* est le nom de l’application associée pour laquelle vous souhaitez supprimer le mappage utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1a68d-122">Type `ssoclient –deletemapping <application name>`, where *\<application name>* is the name of the affiliate application for which you want to remove the user mapping.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a68d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a68d-123">See Also</span></span>  
 <span data-ttu-id="1a68d-124">[Mappages SSO](../esso/sso-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="1a68d-124">[SSO Mappings](../esso/sso-mappings.md) </span></span>  
 <span data-ttu-id="1a68d-125">[Gestion des Applications associées](../esso/managing-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="1a68d-125">[Managing Affiliate Applications](../esso/managing-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="1a68d-126">Gestion des mappages utilisateur</span><span class="sxs-lookup"><span data-stu-id="1a68d-126">Managing User Mappings</span></span>](../esso/managing-user-mappings.md)