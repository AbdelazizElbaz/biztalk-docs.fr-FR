---
title: Comment créer des mappages utilisateur | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb91879c-73f4-4e9e-9e5b-534f48cd5584
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 89fd7ab2ca83d23a37944447997becd2d3f008c2
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-create-user-mappings"></a><span data-ttu-id="d5eff-102">Comment créer des mappages utilisateur</span><span class="sxs-lookup"><span data-stu-id="d5eff-102">How to Create User Mappings</span></span>
<span data-ttu-id="d5eff-103">Utilisez le **createmappings** commande pour créer un ou plusieurs mappages utilisateur, tel que spécifié dans le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="d5eff-103">Use the **createmappings** command to create one or more user mappings, as specified in the XML file.</span></span> <span data-ttu-id="d5eff-104">Voici un exemple de fichier XML.</span><span class="sxs-lookup"><span data-stu-id="d5eff-104">The following is an example XML file.</span></span>  
  
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
  
 <span data-ttu-id="d5eff-105">Si un compte d'utilisateur est modifié, vous devez utiliser cette commande pour créer un mappage pour le nouveau compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d5eff-105">If a user account is changed, you must use this command to create a mapping for the new user account.</span></span> <span data-ttu-id="d5eff-106">Vous devez également supprimer l'ancien mappage utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d5eff-106">You should also remove the old user mapping.</span></span> <span data-ttu-id="d5eff-107">Pour plus d’informations sur la suppression d’un mappage, consultez [comment supprimer des mappages utilisateur](../esso/how-to-delete-user-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="d5eff-107">For more information about removing a mapping, see [How to Delete User Mappings](../esso/how-to-delete-user-mappings.md).</span></span>  
  
 <span data-ttu-id="d5eff-108">Après avoir créé un mappage utilisateur, vous devez l’activer avant de pouvoir utiliser ce mappage dans le système Single Sign-On (SSO).</span><span class="sxs-lookup"><span data-stu-id="d5eff-108">After you create a user mapping, you must enable it before you can use this mapping in the Single Sign-On (SSO) system.</span></span> <span data-ttu-id="d5eff-109">Pour plus d’informations, consultez [comment activer un mappage utilisateur](../esso/how-to-enable-a-user-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="d5eff-109">For more information, see [How to Enable a User Mapping](../esso/how-to-enable-a-user-mapping.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d5eff-110">Seuls les groupes de domaine sont pris en charge avec les mappages utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d5eff-110">Only domain groups are supported for user mappings.</span></span>  
  
### <a name="to-create-user-mappings-using-the-administration-utility"></a><span data-ttu-id="d5eff-111">Pour créer des mappages utilisateur à l'aide de l'utilitaire d'administration</span><span class="sxs-lookup"><span data-stu-id="d5eff-111">To create user mappings using the administration utility</span></span>  
  
1.  <span data-ttu-id="d5eff-112">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="d5eff-112">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="d5eff-113">À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="d5eff-113">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="d5eff-114">Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="d5eff-114">The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="d5eff-115">Type `ssomanage –createmappings <mappings file name>`, où  *\<nom de fichier de mappage >* est le nom du fichier qui contient les mappages utilisateur que vous souhaitez créer.</span><span class="sxs-lookup"><span data-stu-id="d5eff-115">Type `ssomanage –createmappings <mappings file name>`, where *\<mappings file name>* is the name of the file that contains the user mappings that you want to create.</span></span>  
  
### <a name="to-create-user-mappings-using-the-client-utility"></a><span data-ttu-id="d5eff-116">Pour créer des mappages utilisateur à l'aide de l'utilitaire client</span><span class="sxs-lookup"><span data-stu-id="d5eff-116">To create user mappings using the client utility</span></span>  
  
1.  <span data-ttu-id="d5eff-117">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="d5eff-117">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="d5eff-118">À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="d5eff-118">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="d5eff-119">Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="d5eff-119">The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="d5eff-120">Type `ssoclient –setcredentials <application name >`, où  *\<nom de l’application >* est le nom de l’application associée que l’utilisateur souhaite créer un mappage pour.</span><span class="sxs-lookup"><span data-stu-id="d5eff-120">Type `ssoclient –setcredentials <application name >`, where *\<application name >* is the name of the affiliate application that the user wants to create a mapping for.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5eff-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5eff-121">See Also</span></span>  
 <span data-ttu-id="d5eff-122">[Mappages SSO](../esso/sso-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="d5eff-122">[SSO Mappings](../esso/sso-mappings.md) </span></span>  
 <span data-ttu-id="d5eff-123">[Gestion des Applications associées](../esso/managing-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="d5eff-123">[Managing Affiliate Applications](../esso/managing-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="d5eff-124">Gestion des mappages utilisateur</span><span class="sxs-lookup"><span data-stu-id="d5eff-124">Managing User Mappings</span></span>](../esso/managing-user-mappings.md)