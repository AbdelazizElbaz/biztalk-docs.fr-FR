---
title: "Comment définir les informations d’identification d’un mappage utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maps [SSO], credentials
- managing [SSO maps], configuring credentials
ms.assetid: 75b29114-56b6-4db0-8666-61cf6c675401
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc5947b13d9ffcc3721f460ccbcd5bd25701be07
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-credentials-for-a-user-mapping"></a><span data-ttu-id="a6a9d-102">Comment définir les informations d’identification d’un mappage utilisateur</span><span class="sxs-lookup"><span data-stu-id="a6a9d-102">How to Set Credentials for a User Mapping</span></span>
<span data-ttu-id="a6a9d-103">Cette commande permet de définir les informations d’identification pour un utilisateur d’accéder à une application spécifique.</span><span class="sxs-lookup"><span data-stu-id="a6a9d-103">Use this command to set the credentials for a user to access a specific application.</span></span>  
  
 <span data-ttu-id="a6a9d-104">Cette commande n'affiche pas le mot de passe durant sa saisie.</span><span class="sxs-lookup"><span data-stu-id="a6a9d-104">This command does not display the password as you type it.</span></span>  
  
 <span data-ttu-id="a6a9d-105">Si le mappage utilisateur existe déjà, cette commande définit les informations d’identification pour le mappage existant.</span><span class="sxs-lookup"><span data-stu-id="a6a9d-105">If the user mapping already exists, this command sets the credentials for that existing mapping.</span></span> <span data-ttu-id="a6a9d-106">Si vous n'avez pas créé le mappage utilisateur, le système SSO vous invite à saisir l'ID de l'utilisateur pour l'application.</span><span class="sxs-lookup"><span data-stu-id="a6a9d-106">If you have not created the user mapping, the SSO system will prompt you for the user ID for the application.</span></span>  
  
### <a name="to-set-credentials-for-a-user-mapping"></a><span data-ttu-id="a6a9d-107">Pour définir les informations d'identification d'un mappage utilisateur</span><span class="sxs-lookup"><span data-stu-id="a6a9d-107">To set credentials for a user mapping</span></span>  
  
1.  <span data-ttu-id="a6a9d-108">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="a6a9d-108">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="a6a9d-109">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="a6a9d-109">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="a6a9d-110">Le répertoire d’installation par défaut est  **\<lecteur >**: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="a6a9d-110">The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="a6a9d-111">Type **ssomanage – setcredentials \<domaine >\\< nom d’utilisateur\> \<applicationname >**, où  **\<domaine >** est domaine Windows pour le compte d’utilisateur,  **\<nom d’utilisateur >** est le nom d’utilisateur Windows et  **\<applicationname >** est l’application spécifique pour lequel vous souhaitez définir les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="a6a9d-111">Type **ssomanage –setcredentials \<domain>\\<username\> \<applicationname>**, where **\<domain>** is the Windows domain for the user account, **\<username>** is the Windows user name, and **\<applicationname>** is the specific application for which you want to set the credentials for.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a6a9d-112">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="a6a9d-112">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="a6a9d-113">Lorsque vous y êtes invité, entrez le mot de passe d'utilisateur pour cette application.</span><span class="sxs-lookup"><span data-stu-id="a6a9d-113">When the SSO system prompts you for the user credentials, enter the user password for this application.</span></span>  
  
5.  <span data-ttu-id="a6a9d-114">Si vous n'avez pas créé le mappage utilisateur, le système SSO vous invite à saisir l'ID de l'utilisateur pour l'application.</span><span class="sxs-lookup"><span data-stu-id="a6a9d-114">If you have not created the user mapping, the SSO system will prompt you for the user ID for the application.</span></span>  
  
### <a name="to-set-credentials-for-a-user-mapping-from-the-client-utility"></a><span data-ttu-id="a6a9d-115">Pour définir les informations d'identification d'un mappage utilisateur à partir de l'utilitaire client</span><span class="sxs-lookup"><span data-stu-id="a6a9d-115">To set credentials for a user mapping from the client utility</span></span>  
  
1.  <span data-ttu-id="a6a9d-116">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="a6a9d-116">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="a6a9d-117">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="a6a9d-117">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="a6a9d-118">Le répertoire d’installation par défaut est  **\<lecteur >**: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="a6a9d-118">The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="a6a9d-119">Type **ssoclient - setcredentials \<nom de l’application >**, où  **\<nom de l’application >** est le nom de l’application associée que vous souhaitez supprimer le mappage utilisateur .</span><span class="sxs-lookup"><span data-stu-id="a6a9d-119">Type **ssoclient -setcredentials \<application name>**, where **\<application name>** is the name of the affiliate application you want to remove the user mapping for.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a6a9d-120">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="a6a9d-120">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6a9d-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6a9d-121">See Also</span></span>  
 <span data-ttu-id="a6a9d-122">[Comment créer des mappages utilisateur](../core/how-to-create-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="a6a9d-122">[How to Create User Mappings](../core/how-to-create-user-mappings.md) </span></span>  
 <span data-ttu-id="a6a9d-123">[Mappages SSO](../core/sso-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="a6a9d-123">[SSO Mappings](../core/sso-mappings.md) </span></span>  
 <span data-ttu-id="a6a9d-124">[Gestion des Applications associées](../core/managing-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="a6a9d-124">[Managing Affiliate Applications](../core/managing-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="a6a9d-125">Gestion des mappages utilisateur</span><span class="sxs-lookup"><span data-stu-id="a6a9d-125">Managing User Mappings</span></span>](../core/managing-user-mappings.md)