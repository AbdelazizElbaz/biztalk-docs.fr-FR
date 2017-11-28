---
title: "Comment mettre à jour les propriétés d’une Application associée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO applications], updating properties
- applications [SSO], properties
ms.assetid: b06eefdd-a5ca-4a32-93d7-72246e31a2e4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 577ded3a225acd8b3f95372075103ab37dfba854
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-the-properties-of-an-affiliate-application"></a><span data-ttu-id="134d4-102">Comment mettre à jour les propriétés d’une Application associée</span><span class="sxs-lookup"><span data-stu-id="134d4-102">How to Update the Properties of an Affiliate Application</span></span>
<span data-ttu-id="134d4-103">Le composant logiciel enfichable MMC ou cette commande permet de mettre à jour une ou plusieurs propriétés d'application, comme spécifié dans le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="134d4-103">You can use the MMC Snap-In or this command to update one or more application properties, as specified by the XML file.</span></span> <span data-ttu-id="134d4-104">Pour exécuter cette tâche, vous devez être Administrateur d'applications associées.</span><span class="sxs-lookup"><span data-stu-id="134d4-104">You must be an Affiliate Administrator to perform this task.</span></span> <span data-ttu-id="134d4-105">Voici un exemple de fichier XML qui répertorie les champs que vous pouvez mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="134d4-105">The following is an example XML file that lists the fields you can update.</span></span>  
  
```  
<SSO>  
<application name="SSOApplication">  
<description>An SSO Application</description>  
<contact>someone@companyname.com</contact>  
<appUserAccount>DomainName\AppUserGroup</appUserAccount>  
<appAdminAccount>DomainName\AppAdminGroup</appAdminAccount>  
<flags allowTickets="no" validateTickets="yes"  timeoutTickets="yes" enableApp="no" />  
</application>  
</SSO>  
  
```  
  
 <span data-ttu-id="134d4-106">Après avoir créé une application associée, il est impossible de modifier les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="134d4-106">After you create an affiliate application, you cannot modify the following properties:</span></span>  
  
-   <span data-ttu-id="134d4-107">Nom de l’application associée</span><span class="sxs-lookup"><span data-stu-id="134d4-107">Name of the affiliate application</span></span>  
  
-   <span data-ttu-id="134d4-108">Champs liés à l'application associée</span><span class="sxs-lookup"><span data-stu-id="134d4-108">Fields associated with the affiliate application</span></span>  
  
-   <span data-ttu-id="134d4-109">Type de l'application associée (groupe d'hôtes, individuelle ou magasin de configuration)</span><span class="sxs-lookup"><span data-stu-id="134d4-109">Affiliate application type (host group, individual, or configuration store)</span></span>  
  
-   <span data-ttu-id="134d4-110">Compte d'administration identique au groupe des administrateurs d'applications associées</span><span class="sxs-lookup"><span data-stu-id="134d4-110">Administration account same as affiliate administrators group.</span></span> <span data-ttu-id="134d4-111">(si vous spécifiez cet indicateur, le groupe Administrateurs associés sera toujours utilisé comme compte d'administrateurs pour cette application associée)</span><span class="sxs-lookup"><span data-stu-id="134d4-111">(Specifying this flag will always use the affiliate administrators group as the administrator account for this affiliate application)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="134d4-112">Vous pouvez utiliser les comptes locaux pour le compte d'administration et le compte d'utilisateur en définissant l'indicateur allowLocalAccounts sur Oui.</span><span class="sxs-lookup"><span data-stu-id="134d4-112">You can use local accounts for the administration account and user account by setting the allowLocalAccounts flag to yes.</span></span> <span data-ttu-id="134d4-113">Vous pouvez toutefois sélectionner cet indicateur uniquement dans des scénarios impliquant un seul ordinateur.</span><span class="sxs-lookup"><span data-stu-id="134d4-113">However, you can only use this flag in single-computer scenarios.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="134d4-114">Pour effectuer cette tâche, vous devez être un administrateur SSO, un administrateur d'applications associées à SSO ou un administrateur d'applications.</span><span class="sxs-lookup"><span data-stu-id="134d4-114">You must be an SSO administrator, SSO affiliate administrator, or application administrator to perform this task.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="134d4-115">Pour modifier les indicateurs de tickets (validateTickets et timeoutTickets), vous devez être administrateur SSO.</span><span class="sxs-lookup"><span data-stu-id="134d4-115">You must be an SSO administrator to modify the ticketing flags (validateTickets and timeoutTickets).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="134d4-116">Pour modifier le compte d'administration relatif à l'application, vous devez être administrateur de l'authentification unique ou administrateur d'applications associées à SSO.</span><span class="sxs-lookup"><span data-stu-id="134d4-116">You must be an SSO administrator or an SSO affiliate administrator to modify the application administration account.</span></span>  
  
### <a name="to-update-the-properties-of-an-affiliate-application-using-the-mmc-snap-in"></a><span data-ttu-id="134d4-117">Pour mettre à jour les propriétés d'une application associée à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="134d4-117">To update the properties of an affiliate application using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="134d4-118">Sur le **Démarrer** menu, cliquez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="134d4-118">On the **Start** menu, click **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="134d4-119">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="134d4-119">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="134d4-120">Cliquez sur l’application associée, puis cliquez sur **mise à jour**.</span><span class="sxs-lookup"><span data-stu-id="134d4-120">Right-click the affililate application, and then click **Update**.</span></span>  
  
### <a name="to-update-the-properties-of-an-affiliate-application-using-the-command-line"></a><span data-ttu-id="134d4-121">Pour mettre à jour les propriétés d'une application associée à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="134d4-121">To update the properties of an affiliate application using the command line</span></span>  
  
1.  <span data-ttu-id="134d4-122">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="134d4-122">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="134d4-123">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="134d4-123">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="134d4-124">Le répertoire d’installation par défaut est  **\<lecteur >**: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="134d4-124">The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="134d4-125">Type **ssomanage – updateapps \<nom de fichier d’application >**, où le nom de fichier d’application est le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="134d4-125">Type **ssomanage –updateapps \<application file name>**, where the application file name is the XML file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="134d4-126">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="134d4-126">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="134d4-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="134d4-127">See Also</span></span>  
 <span data-ttu-id="134d4-128">[Applications associées SSO](../core/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="134d4-128">[SSO Affiliate Applications](../core/sso-affiliate-applications.md) </span></span>  
 <span data-ttu-id="134d4-129">[Comment activer une Application associée](../core/how-to-enable-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="134d4-129">[How to Enable an Affiliate Application](../core/how-to-enable-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="134d4-130">[Gestion des mappages utilisateur](../core/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="134d4-130">[Managing User Mappings](../core/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="134d4-131">Gestion des Applications associées</span><span class="sxs-lookup"><span data-stu-id="134d4-131">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)