---
title: "Comment créer une Application associée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO applications], creating
- applications [SSO], creating
- creating, applications [SSO]
ms.assetid: d0967c4b-6201-416a-9d3a-23b5de5b83d6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2f621faef7694a3dba7885bab5641e0baa58e8f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-create-an-affiliate-application"></a><span data-ttu-id="29f17-102">Comment créer une Application associée</span><span class="sxs-lookup"><span data-stu-id="29f17-102">How to Create an Affiliate Application</span></span>
<span data-ttu-id="29f17-103">Le composant logiciel enfichable MMC ou cette commande permet de créer une ou plusieurs applications, comme spécifié dans le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="29f17-103">You can use the MMC Snap-In or this command to create one or more applications, as specified by the XML file.</span></span> <span data-ttu-id="29f17-104">Voici un exemple de fichier XML pour l'authentification unique initiée par Windows :</span><span class="sxs-lookup"><span data-stu-id="29f17-104">An example XML file for Windows Initiated SSO is:</span></span>  
  
```  
<sso>  
<application name="SAP">  
<description>The SAP application</description>   
<contact>someone@example.com</contact>   
<appuserAccount>domain\AppUserAccount</appuserAccount>   
<appAdminAccount>domain\AppAdminAccount</appAdminAccount>   
<field ordinal="0" label="User Id" masked="no" />   
<field ordinal="1" label="Password" masked="yes" />   
<flags groupApp="no" configStoreApp="no" allowTickets="no" validateTickets="yes" allowLocalAccounts="no" timeoutTickets="yes" adminAccountSame="no" enableApp="no" />  
</application>  
</sso>  
  
```  
  
 <span data-ttu-id="29f17-105">Après avoir créé une application associée, il est impossible de modifier les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="29f17-105">After you create an affiliate application, you cannot modify the following properties:</span></span>  
  
-   <span data-ttu-id="29f17-106">Nom de l’application associée</span><span class="sxs-lookup"><span data-stu-id="29f17-106">Name of the affiliate application</span></span>  
  
-   <span data-ttu-id="29f17-107">Champs liés à l'application associée</span><span class="sxs-lookup"><span data-stu-id="29f17-107">Fields associated with the affiliate application</span></span>  
  
-   <span data-ttu-id="29f17-108">Type de l'application associée (groupe d'hôtes, individuelle ou magasin de configuration)</span><span class="sxs-lookup"><span data-stu-id="29f17-108">Affiliate application type (host group, individual, or configuration store)</span></span>  
  
-   <span data-ttu-id="29f17-109">Compte d'administration identique au groupe des administrateurs d'applications associées</span><span class="sxs-lookup"><span data-stu-id="29f17-109">Administration account same as affiliate administrators group.</span></span> <span data-ttu-id="29f17-110">(si vous spécifiez cet indicateur, le groupe Administrateurs associés sera toujours utilisé comme compte d'administrateurs pour cette application associée)</span><span class="sxs-lookup"><span data-stu-id="29f17-110">(Specifying this flag will always use the affiliate administrators group as the administrator account for this affiliate application)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="29f17-111">Vous pouvez utiliser les comptes locaux pour le compte d'administration et le compte d'utilisateur en définissant l'indicateur allowLocalAccounts sur Oui.</span><span class="sxs-lookup"><span data-stu-id="29f17-111">You can use local accounts for the administration account and user account by setting the allowLocalAccounts flag to yes.</span></span> <span data-ttu-id="29f17-112">Vous devez toutefois sélectionner cet indicateur uniquement dans des scénarios impliquant un seul ordinateur.</span><span class="sxs-lookup"><span data-stu-id="29f17-112">However, you should only use this flag in single-computer scenarios.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="29f17-113">Pour effectuer cette tâche, vous devez être un administrateur SSO ou un administrateur d'applications associées à SSO.</span><span class="sxs-lookup"><span data-stu-id="29f17-113">You must be an SSO administrator or SSO affiliate administrator to perform this task.</span></span>  
  
 <span data-ttu-id="29f17-114">Après avoir créé l'application associée, vous devez l'activer.</span><span class="sxs-lookup"><span data-stu-id="29f17-114">After you create the affiliate application, you must enable it.</span></span> <span data-ttu-id="29f17-115">Pour plus d’informations, consultez [comment activer une Application associée](../core/how-to-enable-an-affiliate-application.md).</span><span class="sxs-lookup"><span data-stu-id="29f17-115">For more information, see [How to Enable an Affiliate Application](../core/how-to-enable-an-affiliate-application.md).</span></span>  
  
### <a name="to-create-an-affiliate-application-using-the-mmc-snap-in"></a><span data-ttu-id="29f17-116">Pour créer une application associée à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="29f17-116">To create an affiliate application using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="29f17-117">Sur le **Démarrer** menu, cliquez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="29f17-117">On the **Start** menu, click **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="29f17-118">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="29f17-118">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="29f17-119">Avec le bouton droit **Applications associées**, puis cliquez sur **créer une Application**.</span><span class="sxs-lookup"><span data-stu-id="29f17-119">Right-click **Affiliate Applications**, and then click **Create Application**.</span></span>  
  
4.  <span data-ttu-id="29f17-120">Suivez les instructions de la **unique Sign-On Assistant Application d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="29f17-120">Follow the instructions in the **Enterprise Single Sign-On Application Wizard**.</span></span>  
  
### <a name="to-create-an-affiliate-application-using-the-command-line"></a><span data-ttu-id="29f17-121">Pour créer une application associée à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="29f17-121">To create an affiliate application using the command line</span></span>  
  
1.  <span data-ttu-id="29f17-122">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="29f17-122">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="29f17-123">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="29f17-123">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="29f17-124">Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="29f17-124">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="29f17-125">Type **ssomanage – createapps  *\<nom de fichier d’application\>***, où  *\<nom de fichier d’application\>*  est le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="29f17-125">Type **ssomanage –createapps *\<application file name\>***, where *\<application file name\>* is the XML file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="29f17-126">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="29f17-126">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29f17-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29f17-127">See Also</span></span>  
 <span data-ttu-id="29f17-128">[Applications associées SSO](../core/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="29f17-128">[SSO Affiliate Applications](../core/sso-affiliate-applications.md) </span></span>  
 <span data-ttu-id="29f17-129">[Comment activer une Application associée](../core/how-to-enable-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="29f17-129">[How to Enable an Affiliate Application](../core/how-to-enable-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="29f17-130">[Comment supprimer une Application associée](../core/how-to-delete-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="29f17-130">[How to Delete an Affiliate Application](../core/how-to-delete-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="29f17-131">[Gestion des mappages utilisateur](../core/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="29f17-131">[Managing User Mappings](../core/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="29f17-132">Gestion des applications associées</span><span class="sxs-lookup"><span data-stu-id="29f17-132">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)