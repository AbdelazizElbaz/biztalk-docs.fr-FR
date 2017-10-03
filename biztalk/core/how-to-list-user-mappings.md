---
title: Affichage des mappages utilisateur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO maps], listing maps
- maps [SSO], listing maps
ms.assetid: f9b73785-3a59-45c8-9e88-d2d16b5a46aa
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f6041b40c2b6a3fa468462478754079d41881bc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-list-user-mappings"></a><span data-ttu-id="e7304-102">Affichage des mappages utilisateur</span><span class="sxs-lookup"><span data-stu-id="e7304-102">How to List User Mappings</span></span>
<span data-ttu-id="e7304-103">Cette commande permet de répertorier tous les mappages existants pour l'utilisateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="e7304-103">Use this command to list all the existing mappings for the specified user.</span></span>  
  
 <span data-ttu-id="e7304-104">Pour effectuer cette tâche, vous devez être un administrateur SSO, un administrateur d'applications, un administrateur d'applications associées à SSO ou un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e7304-104">You must be an SSO administrator, application administrator, SSO affiliate administrator, or user to do this task.</span></span>  
  
 <span data-ttu-id="e7304-105">Mappages utilisateur activés apparaissent sous la forme (E) \< *domaine*>\\*\<nom d’utilisateur >*, alors que désactivé mappages utilisateur apparaissent en tant que (D) \< *domaine*>\\*\<nom d’utilisateur >*.</span><span class="sxs-lookup"><span data-stu-id="e7304-105">Enabled user mappings appear as (E) \<*domain*>\\*\<username>*, while disabled user mappings appear as (D) \<*domain*>\\*\<username>*.</span></span>  
  
### <a name="to-list-user-mappings-using-the-administration-utility"></a><span data-ttu-id="e7304-106">Pour répertorier des mappages utilisateur à l'aide de l'utilitaire d'administration</span><span class="sxs-lookup"><span data-stu-id="e7304-106">To list user mappings using the administration utility</span></span>  
  
1.  <span data-ttu-id="e7304-107">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="e7304-107">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="e7304-108">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="e7304-108">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="e7304-109">Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="e7304-109">The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="e7304-110">Procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="e7304-110">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="e7304-111">Type **ssomanage – listmappings  *\<domaine >\\< nom d’utilisateur\>***  pour répertorier tous les mappages d’un utilisateur donné possède dans les applications associées auxquelles il appartient vers l’emplacement où  *\<domaine >* est le domaine Microsoft Windows pour le compte d’utilisateur, et  *\<nom d’utilisateur >* est le nom d’utilisateur Windows pour lequel vous souhaitez répertorier les Mappages utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e7304-111">Type **ssomanage –listmappings *\<domain>\\<username\>*** to list all the mappings a given user has in the affiliate applications he/she belongs to, where *\<domain>* is the Microsoft Windows domain for the user account, and *\<username>* is the Windows user name for which you want to list the user mappings.</span></span> <span data-ttu-id="e7304-112">Si l'utilisateur est un administrateur d'applications associées ou un administrateur SSO, cette commande répertorie tous les mappages pour cet utilisateur dans toutes les applications associées.</span><span class="sxs-lookup"><span data-stu-id="e7304-112">If the user is an Affiliate Administrator or an SSO Administrator, this command will list all the mappings for that user in all the affiliate applications.</span></span>  
  
         <span data-ttu-id="e7304-113">Ou</span><span class="sxs-lookup"><span data-stu-id="e7304-113">Or</span></span>  
  
    -   <span data-ttu-id="e7304-114">Type **ssomanage – listmappings  *\<nom de l’application >***  pour répertorier tous les mappages utilisateur pour une application donnée.</span><span class="sxs-lookup"><span data-stu-id="e7304-114">Type **ssomanage –listmappings *\<application name>*** to list all the user mappings for a given application.</span></span>  
  
         <span data-ttu-id="e7304-115">Ou</span><span class="sxs-lookup"><span data-stu-id="e7304-115">Or</span></span>  
  
    -   <span data-ttu-id="e7304-116">Si vous êtes un administrateur d’application, tapez **ssomanage – listmappings  *\<domaine >\\< nom d’utilisateur\>*   *\<nom de l’application >***  pour répertorier tous les mappages d’un utilisateur donné possède dans les applications associées dont vous êtes un administrateur.</span><span class="sxs-lookup"><span data-stu-id="e7304-116">If you are an application administrator, type **ssomanage –listmappings *\<domain>\\<username\>* *\<application name>*** to list all the mappings a given user has in the affiliate applications for which you are an administrator.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e7304-117">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="e7304-117">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-list-user-mappings-using-the-client-utility"></a><span data-ttu-id="e7304-118">Pour répertorier des mappages utilisateur à l'aide de l'utilitaire client</span><span class="sxs-lookup"><span data-stu-id="e7304-118">To list user mappings using the client utility</span></span>  
  
1.  <span data-ttu-id="e7304-119">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="e7304-119">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="e7304-120">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="e7304-120">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="e7304-121">Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="e7304-121">The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="e7304-122">Type **ssoclient – listmappings** pour répertorier tous les mappages que vous avez.</span><span class="sxs-lookup"><span data-stu-id="e7304-122">Type **ssoclient –listmappings** to list all the mappings you have.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e7304-123">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="e7304-123">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7304-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7304-124">See Also</span></span>  
 <span data-ttu-id="e7304-125">[Comment créer des mappages utilisateur](../core/how-to-create-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="e7304-125">[How to Create User Mappings](../core/how-to-create-user-mappings.md) </span></span>  
 <span data-ttu-id="e7304-126">[Mappages SSO](../core/sso-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="e7304-126">[SSO Mappings](../core/sso-mappings.md) </span></span>  
 <span data-ttu-id="e7304-127">[Gestion des Applications associées](../core/managing-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="e7304-127">[Managing Affiliate Applications](../core/managing-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="e7304-128">Gestion des mappages utilisateur</span><span class="sxs-lookup"><span data-stu-id="e7304-128">Managing User Mappings</span></span>](../core/managing-user-mappings.md)