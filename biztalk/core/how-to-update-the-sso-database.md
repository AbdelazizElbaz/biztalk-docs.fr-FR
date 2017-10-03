---
title: "Comment mettre à jour la base de données SSO | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tickets [SSO], modifying
- managing [SSO], modifying Credential cache timeout
- tickets [SSO], timeouts
- modifying, SSO database
- managing [SSO], modifying ticket timeouts
- SSO database, modifying
ms.assetid: 45eb6a77-d91a-44a8-b26d-05508c288c36
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1381ee4e5c2b90a96c52b59d125ec3121af02a4e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-the-sso-database"></a><span data-ttu-id="97331-102">Comment mettre à jour la base de données SSO</span><span class="sxs-lookup"><span data-stu-id="97331-102">How to Update the SSO Database</span></span>
<span data-ttu-id="97331-103">Le composant logiciel enfichable MMC et la ligne de commande permettent de modifier les informations globales dans la base de données SSO, telles que l'identification du serveur de secret principal, les noms de compte, l'audit dans la base de données, le délai d'expiration du ticket et le délai d'expiration du cache des informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="97331-103">You can change the global information in the SSO database, such as the master secret server identification, the account names, auditing in the database, ticket timeout, and credential cache timeout, by using either the MMC Snap-In or the command line.</span></span>  
  
## <a name="changing-timeouts-for-the-sso-system"></a><span data-ttu-id="97331-104">Modification des délais d'expiration du système d'authentification unique</span><span class="sxs-lookup"><span data-stu-id="97331-104">Changing timeouts for the SSO System</span></span>  
 <span data-ttu-id="97331-105">Vous pouvez modifier deux délais d'expiration au niveau du système d'authentification unique de l'entreprise (SSO) :</span><span class="sxs-lookup"><span data-stu-id="97331-105">You can modify two timeouts at the Enterprise Single Sign-On (SSO) system level:</span></span>  
  
 <span data-ttu-id="97331-106">**Délai d’expiration du ticket.**</span><span class="sxs-lookup"><span data-stu-id="97331-106">**Ticket timeout.**</span></span> <span data-ttu-id="97331-107">Cette propriété indique la durée de validité d’un ticket émis par le système d’authentification unique.</span><span class="sxs-lookup"><span data-stu-id="97331-107">This property specifies the length of time for which a ticket SSO issues is valid.</span></span> <span data-ttu-id="97331-108">Afin de répondre aux critères de la plupart des entreprises utilisant le système d'authentification unique, le délai d'expiration du ticket est défini sur 2 minutes par défaut.</span><span class="sxs-lookup"><span data-stu-id="97331-108">To satisfy most of the scenarios in an enterprise that use SSO, the default ticket timeout is 2 minutes.</span></span> <span data-ttu-id="97331-109">L'administrateur de l'authentification unique peut modifier ce délai selon les conditions requises par l'application.</span><span class="sxs-lookup"><span data-stu-id="97331-109">The SSO administrator can change this based on the application requirements.</span></span>  
  
 <span data-ttu-id="97331-110">**Délai d’expiration du Cache des informations d’identification.**</span><span class="sxs-lookup"><span data-stu-id="97331-110">**Credential Cache timeout.**</span></span> <span data-ttu-id="97331-111">Cette propriété indique le délai d’expiration du cache des informations d’identification pour tous les serveurs d’authentification unique (SSO).</span><span class="sxs-lookup"><span data-stu-id="97331-111">This property specifies the credential cache timeout for all SSO Servers.</span></span> <span data-ttu-id="97331-112">Les serveurs d'authentification unique mettent les informations d'identification en cache après la première recherche.</span><span class="sxs-lookup"><span data-stu-id="97331-112">SSO Servers cache the credentials after the first lookup.</span></span> <span data-ttu-id="97331-113">Par défaut, le délai d'attente de ce cache est de 60 minutes.</span><span class="sxs-lookup"><span data-stu-id="97331-113">By default, the credential cache timeout is 60 minutes.</span></span> <span data-ttu-id="97331-114">L'administrateur de l'authentification unique peut modifier ce délai selon les conditions de sécurité requises.</span><span class="sxs-lookup"><span data-stu-id="97331-114">The SSO administrator can change this to a suitable value based on the security requirements.</span></span>  
  
 <span data-ttu-id="97331-115">Vous devez modifier ces deux délais d'expiration en mettant à jour la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="97331-115">You change both of these timeouts by updating the SSO database.</span></span>  
  
 <span data-ttu-id="97331-116">Voici un exemple de fichier XML pour la mise à jour de la base de données SSO :</span><span class="sxs-lookup"><span data-stu-id="97331-116">A sample XML file for updating the SSO database is:</span></span>  
  
```  
<sso>  
<globalInfo>  
<ssoAdminAccount>Domain\Accountname</ssoAdminAccount>  
<ssoAffiliateAdminAccount>Domain\Accountname</ssoAffiliateAdminAccount>  
<secretServer>ComputerA</secretServer>  
<auditDeletedApps>1000</auditDeletedApps>  
<auditDeletedMappings>1000</auditDeletedMappings>  
<auditCredentialLookups>1000</auditCredentialLookups>  
<ticketTimeout>2</ticketTimeout>  
<credCacheTimeout>60</credCacheTimeout>  
</globalInfo>  
</sso>  
  
```  
  
#### <a name="to-change-timeouts-using-the-mmc-snap-in"></a><span data-ttu-id="97331-117">Pour modifier les délais d'expiration à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="97331-117">To change timeouts using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="97331-118">Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="97331-118">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="97331-119">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="97331-119">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="97331-120">Cliquez avec le bouton droit sur **Système**, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="97331-120">Right-click **System**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="97331-121">Dans la boîte de dialogue **Propriétés système** , cliquez sur l'onglet **Général** .</span><span class="sxs-lookup"><span data-stu-id="97331-121">On the **System Properties** dialog box, click the **General** tab.</span></span>  
  
5.  <span data-ttu-id="97331-122">Entrez les paramètres appropriés, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="97331-122">Enter the appropriate settings, and click **OK**.</span></span>  
  
#### <a name="to-update-the-sso-database-using-the-mmc-snap-in"></a><span data-ttu-id="97331-123">Pour mettre à jour la base de données SSO à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="97331-123">To update the SSO database using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="97331-124">Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="97331-124">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="97331-125">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="97331-125">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="97331-126">Cliquez avec le bouton droit sur **Système**, puis cliquez sur **Mettre à niveau la base de données**.</span><span class="sxs-lookup"><span data-stu-id="97331-126">Right-click **System**, and then click **Upgrade Database**.</span></span>  
  
#### <a name="to-update-the-sso-database-using-the-command-line"></a><span data-ttu-id="97331-127">Pour mettre à jour la base de données SSO à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="97331-127">To update the SSO database using the command line</span></span>  
  
1.  <span data-ttu-id="97331-128">Cliquez sur **Démarrer**, **Exécuter**, puis entrez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="97331-128">Click **Start**, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="97331-129">Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="97331-129">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="97331-130">Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="97331-130">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="97331-131">Type **ssomanage-updatedb \<mise à jour de fichier >**, où  **\<mise à jour de fichier >** est le chemin d’accès et le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="97331-131">Type **ssomanage –updatedb \<update file>**, where **\<update file>** is the path and name of the file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="97331-132">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="97331-132">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97331-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97331-133">See Also</span></span>  
 <span data-ttu-id="97331-134">[Comment configurer les Tickets d’authentification unique](../core/how-to-configure-the-sso-tickets.md) </span><span class="sxs-lookup"><span data-stu-id="97331-134">[How to Configure the SSO Tickets](../core/how-to-configure-the-sso-tickets.md) </span></span>  
 [<span data-ttu-id="97331-135">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="97331-135">Using SSO</span></span>](../core/using-sso.md)