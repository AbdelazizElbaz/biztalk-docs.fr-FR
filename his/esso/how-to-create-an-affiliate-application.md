---
title: Comment créer une Application associée | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3be483f8-2617-459e-9081-aab886c75d93
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 5145111b2c585edab92cc10c3e3614e8bb91a85d
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-create-an-affiliate-application"></a><span data-ttu-id="46e4e-102">Comment créer une Application associée</span><span class="sxs-lookup"><span data-stu-id="46e4e-102">How to Create an Affiliate Application</span></span>
<span data-ttu-id="46e4e-103">Vous pouvez utiliser le composant logiciel enfichable MMC ou la **createapps** commande pour créer une ou plusieurs applications, comme spécifié par le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="46e4e-103">You can use the MMC Snap-In or the **createapps** command to create one or more applications, as specified by the XML file.</span></span> <span data-ttu-id="46e4e-104">Voici un exemple de fichier XML pour Windows-Initiated Single Sign-On (SSO) :</span><span class="sxs-lookup"><span data-stu-id="46e4e-104">The following is an example XML file for Windows-Initiated Single Sign-On (SSO):</span></span>  
  
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
  
 <span data-ttu-id="46e4e-105">Après avoir créé une application associée, il est impossible de modifier les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="46e4e-105">After you create an affiliate application, you cannot modify the following properties:</span></span>  
  
-   <span data-ttu-id="46e4e-106">Nom de l'application associée.</span><span class="sxs-lookup"><span data-stu-id="46e4e-106">Name of the affiliate application.</span></span>  
  
-   <span data-ttu-id="46e4e-107">Champs associés à l’application associée.</span><span class="sxs-lookup"><span data-stu-id="46e4e-107">Fields associated with the affiliate application.</span></span>  
  
-   <span data-ttu-id="46e4e-108">Applications associées à type d’application (magasin individuel, groupe ou la configuration d’hôte).</span><span class="sxs-lookup"><span data-stu-id="46e4e-108">Affiliate application type (host group, individual, or configuration store).</span></span>  
  
-   <span data-ttu-id="46e4e-109">Compte d'administration identique au groupe des administrateurs d'applications associées</span><span class="sxs-lookup"><span data-stu-id="46e4e-109">Administration account same as affiliate administrators group.</span></span> <span data-ttu-id="46e4e-110">(Définition de cet indicateur utilisent toujours le groupe Administrateurs associés en tant que le compte d’administrateur pour cette application associée.)</span><span class="sxs-lookup"><span data-stu-id="46e4e-110">(Specifying this flag will always use the affiliate administrators group as the administrator account for this affiliate application.)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="46e4e-111">Vous pouvez utiliser les comptes locaux pour le compte d'administration et le compte d'utilisateur en définissant l'indicateur allowLocalAccounts sur Oui.</span><span class="sxs-lookup"><span data-stu-id="46e4e-111">You can use local accounts for the administration account and user account by setting the allowLocalAccounts flag to yes.</span></span> <span data-ttu-id="46e4e-112">Vous devez toutefois sélectionner cet indicateur uniquement dans des scénarios impliquant un seul ordinateur.</span><span class="sxs-lookup"><span data-stu-id="46e4e-112">However, you should only use this flag in single-computer scenarios.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="46e4e-113">Pour effectuer cette tâche, vous devez être un administrateur SSO ou un administrateur d'applications associées à SSO.</span><span class="sxs-lookup"><span data-stu-id="46e4e-113">You must be an SSO administrator or SSO affiliate administrator to perform this task.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46e4e-114">Si vous effectuez la configuration sur un contrôleur de domaine et les groupes locaux de domaine de la portée sont spécifiées pour les administrateurs d’applications ou utilisateurs de l’Application lors de la création d’Applications associées, il est recommandé d’activer l’indicateur de compte local.</span><span class="sxs-lookup"><span data-stu-id="46e4e-114">If you are performing the configuration on a Domain Controller, and the Domain Local scope groups are specified for Application Administrators or Application Users while creating Affiliate Applications, it is recommended that you enable the local account flag.</span></span> <span data-ttu-id="46e4e-115">Pour effectuer cette opération :</span><span class="sxs-lookup"><span data-stu-id="46e4e-115">To do this:</span></span>  
  
-   <span data-ttu-id="46e4e-116">Dans le composant logiciel enfichable MMC, sélectionnez Autoriser les comptes locaux pour les comptes d’accès pendant le processus de création.</span><span class="sxs-lookup"><span data-stu-id="46e4e-116">In the MMC Snap-in, select Allow local accounts for access accounts during the creation process.</span></span>  
  
-   <span data-ttu-id="46e4e-117">À partir de la ligne de commande, spécifiez allowLocalAccounts = yes dans le fichier XML pour la création d’applications associées à l’Application.</span><span class="sxs-lookup"><span data-stu-id="46e4e-117">From the command line, specify allowLocalAccounts=yes in the XML file for Affiliate Application creation.</span></span>  
  
 <span data-ttu-id="46e4e-118">Après avoir créé l'application associée, vous devez l'activer.</span><span class="sxs-lookup"><span data-stu-id="46e4e-118">After you create the affiliate application, you must enable it.</span></span> <span data-ttu-id="46e4e-119">Pour plus d’informations, consultez [comment activer une Application associée](../esso/how-to-enable-an-affiliate-application.md).</span><span class="sxs-lookup"><span data-stu-id="46e4e-119">For more information, see [How to Enable an Affiliate Application](../esso/how-to-enable-an-affiliate-application.md).</span></span>  
  
### <a name="to-create-an-affiliate-application-using-the-microsoft-management-console-mmc-snap-in"></a><span data-ttu-id="46e4e-120">Pour créer une application associée à l’aide du composant logiciel enfichable Microsoft Management Console (MMC)</span><span class="sxs-lookup"><span data-stu-id="46e4e-120">To create an affiliate application using the Microsoft Management Console (MMC) Snap-In</span></span>  
  
1.  <span data-ttu-id="46e4e-121">Cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="46e4e-121">Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="46e4e-122">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="46e4e-122">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="46e4e-123">Avec le bouton droit **Applications associées**, puis cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="46e4e-123">Right-click **Affiliate Applications**, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="46e4e-124">Suivez les instructions de la **créer une nouvelle Application associée** Assistant.</span><span class="sxs-lookup"><span data-stu-id="46e4e-124">Follow the instructions in the **Create New Affiliate Application** wizard.</span></span>  
  
### <a name="to-create-an-affiliate-application-using-the-command-line"></a><span data-ttu-id="46e4e-125">Pour créer une application associée à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="46e4e-125">To create an affiliate application using the command line</span></span>  
  
1.  <span data-ttu-id="46e4e-126">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="46e4e-126">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="46e4e-127">À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="46e4e-127">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="46e4e-128">Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="46e4e-128">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="46e4e-129">Type `ssomanage –createapps <application file name>`, où  *\<nom de fichier d’application >* est le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="46e4e-129">Type `ssomanage –createapps <application file name>`, where *\<application file name>* is the XML file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46e4e-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46e4e-130">See Also</span></span>  
 <span data-ttu-id="46e4e-131">[Applications associées SSO](../esso/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="46e4e-131">[SSO Affiliate Applications](../esso/sso-affiliate-applications.md) </span></span>  
 <span data-ttu-id="46e4e-132">[Comment activer une Application associée](../esso/how-to-enable-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="46e4e-132">[How to Enable an Affiliate Application](../esso/how-to-enable-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="46e4e-133">[Comment supprimer une Application associée](../esso/how-to-delete-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="46e4e-133">[How to Delete an Affiliate Application](../esso/how-to-delete-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="46e4e-134">[Gestion des mappages utilisateur](../esso/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="46e4e-134">[Managing User Mappings](../esso/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="46e4e-135">Gestion des applications associées</span><span class="sxs-lookup"><span data-stu-id="46e4e-135">Managing Affiliate Applications</span></span>](../esso/managing-affiliate-applications.md)