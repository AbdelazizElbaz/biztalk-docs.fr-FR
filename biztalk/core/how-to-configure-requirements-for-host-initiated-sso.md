---
title: "Configuration requise pour l’ordinateur hôte authentification unique initiée par | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service accounts, granting privileges [SSO]
- host initiated SSO, configuring
- domain function level [SSO]
- host initiated SSO, Transaction Integrator (TI)
- SPN [SSO]
- managing [SSO], granting TCB privileges
- Transaction Integrator (TI)
- host initiated SSO, SPN
- host initiated SSO, TCB privileges
- configuring, host initiated SSO
- creating, SPNs [SSO]
- TCB privileges [SSO]
- managing [SSO], host initiated
- host initiated SSO, domain function level
- service accounts, SSO
- SSO, host initiated
- managing [SSO], creating SPNs
- SSO, service accounts
ms.assetid: 91d77c9f-bab2-4f6e-8bce-e31c59cebb20
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20b14539edc6b9b1026ca048feb881ce0d8a6d1e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-requirements-for-host-initiated-sso"></a><span data-ttu-id="93fd2-102">Configuration des conditions requises pour l'authentification unique initiée par l'hôte</span><span class="sxs-lookup"><span data-stu-id="93fd2-102">How to Configure Requirements for Host Initiated SSO</span></span>
<span data-ttu-id="93fd2-103">L'authentification unique de l'entreprise et l'authentification unique initiée par l'hôte ont plusieurs aspects en commun. Toutefois, certaines conditions requises concernant la plateforme et Active Directory restent uniques à l'authentification unique initiée par l'hôte.</span><span class="sxs-lookup"><span data-stu-id="93fd2-103">Although Enterprise SSO and host initiated SSO have certain aspects in common, certain platform and Active Directory requirements are unique to host initiated SSO.</span></span> <span data-ttu-id="93fd2-104">Cette rubrique présente la configuration requise et répertorie les étapes permettant de la créer ou de la vérifier sur votre système.</span><span class="sxs-lookup"><span data-stu-id="93fd2-104">This topic discusses those requirements, and lists the steps to check or create them on your system.</span></span>  
  
-   <span data-ttu-id="93fd2-105">L'exécution de l'authentification unique initiée par l'hôte est uniquement prise en charge sur un environnement de domaine Windows Server 2008 natif.</span><span class="sxs-lookup"><span data-stu-id="93fd2-105">Host initiated SSO can be executed only on a native Windows Server 2008 domain environment.</span></span>  
  
-   <span data-ttu-id="93fd2-106">Le compte de service pour le service SSO qui effectue l'authentification unique initiée par l'hôte doit être configuré de manière à disposer des privilèges TCB (Trusted Computing Base).</span><span class="sxs-lookup"><span data-stu-id="93fd2-106">The service account for SSO Service that is performing host initiated SSO must be configured to have TCB privileges.</span></span> <span data-ttu-id="93fd2-107">(Vous pouvez configurer ces paramètres pour le compte de service dans la stratégie de sécurité du domaine.)</span><span class="sxs-lookup"><span data-stu-id="93fd2-107">(You can configure this for the service account in the domain security policy.)</span></span>  
  
 <span data-ttu-id="93fd2-108">En outre, certaines conditions sont obligatoires lors de l'utilisation de l'intégrateur de transactions pour le traitement initié par l'hôte.</span><span class="sxs-lookup"><span data-stu-id="93fd2-108">In addition, certain requirements are necessary when using Transaction Integrator for Host Initiated Processing.</span></span> <span data-ttu-id="93fd2-109">Il exploite l'authentification unique initiée par l'hôte dans le but de mettre en place l'authentification unique pour des utilisateurs non-Windows.</span><span class="sxs-lookup"><span data-stu-id="93fd2-109">TI for HIP leverages host initiated SSO to achieve Single Sign-On for non-Windows users.</span></span>  
  
 <span data-ttu-id="93fd2-110">Par exemple, le compte de service associé à l'intégrateur de transactions pour le traitement initié par l'hôte est exécuté sous un compte de service nom_domaine\hipsvc.</span><span class="sxs-lookup"><span data-stu-id="93fd2-110">For example, service account for TI for HIP service runs under a service account domainname\hipsvc.</span></span> <span data-ttu-id="93fd2-111">Ce service peut héberger des applications qui doivent accéder à des ressources Windows locales ou distantes par l'intermédiaire du compte Windows correspondant au compte non-Windows.</span><span class="sxs-lookup"><span data-stu-id="93fd2-111">This service can host applications that want to access remote or local resources on Windows with the Windows account that correspond to the non-Windows account.</span></span>  
  
 <span data-ttu-id="93fd2-112">Le compte nom_domaine\hipsvc doit appartenir au compte de groupe Administrateurs d'application pour l'application associée qui est utilisée pour l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="93fd2-112">The domainname\hipsvc account must belong to the Application Administrator group account for the Affiliate Application that is being used for Single Sign-On.</span></span>  
  
 <span data-ttu-id="93fd2-113">Le compte nom_domaine\hipsvc doit disposer de privilèges de délégation contrainte afin d'utiliser l'authentification unique initiée par l'hôte.</span><span class="sxs-lookup"><span data-stu-id="93fd2-113">The domainname\hipsvc account must have constrained delegation privileges to use host initiated Single Sign-On.</span></span> <span data-ttu-id="93fd2-114">Cette opération incombe à l'administrateur de domaine dans Active Directory.</span><span class="sxs-lookup"><span data-stu-id="93fd2-114">This can be configured by the domain administrator in Active Directory.</span></span> <span data-ttu-id="93fd2-115">La délégation peut être configurée pour les comptes disposant de noms principaux de service enregistrés.</span><span class="sxs-lookup"><span data-stu-id="93fd2-115">Delegation can be configured for accounts that have registered SPNs.</span></span> <span data-ttu-id="93fd2-116">La délégation contrainte autorise le compte de service à accéder uniquement aux composants spécifiés par l'administrateur.</span><span class="sxs-lookup"><span data-stu-id="93fd2-116">Constrained delegation allows the service account to access only components that are specified by the administrator.</span></span>  
  
### <a name="to-check-your-domain-function-level"></a><span data-ttu-id="93fd2-117">Pour vérifier le niveau fonctionnel du domaine</span><span class="sxs-lookup"><span data-stu-id="93fd2-117">To check your domain function level</span></span>  
  
1.  <span data-ttu-id="93fd2-118">Dans votre **Active Directory Domains and Trusts** enfichable MMC, droit, cliquez sur le nœud **Active Directory Domains and Trusts**, puis cliquez sur **augmenter le niveau fonctionnel de la forêt**.</span><span class="sxs-lookup"><span data-stu-id="93fd2-118">In your **Active Directory Domains and Trusts** MMC snap-in, right click the node **Active Directory Domains and Trusts**, and then click **Raise Forest Functional Level**.</span></span>  
  
2.  <span data-ttu-id="93fd2-119">Vérifiez que le niveau fonctionnel est **Windows Server 2008**.</span><span class="sxs-lookup"><span data-stu-id="93fd2-119">Verify that the functional level is **Windows Server 2008**.</span></span> <span data-ttu-id="93fd2-120">Si ce n'est pas le cas, consultez la documentation de Active Directory avant de tenter de modifier ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="93fd2-120">If it is not, refer to your Active Directory documentation before you attempt to change the setting.</span></span>  
  
### <a name="to-create-an-spn"></a><span data-ttu-id="93fd2-121">Pour créer un nom principal de service (SPN)</span><span class="sxs-lookup"><span data-stu-id="93fd2-121">To create an SPN</span></span>  
  
1.  <span data-ttu-id="93fd2-122">Téléchargez le **setspn** utilitaire à partir de l’emplacement suivant : [http://go.microsoft.com/fwlink/?LinkId=33178](http://go.microsoft.com/fwlink/?LinkId=33178).</span><span class="sxs-lookup"><span data-stu-id="93fd2-122">Download the **setspn** utility from the following location: [http://go.microsoft.com/fwlink/?LinkId=33178](http://go.microsoft.com/fwlink/?LinkId=33178).</span></span>  
  
2.  <span data-ttu-id="93fd2-123">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="93fd2-123">On the **Start** menu, click **Run**.</span></span>  
  
3.  <span data-ttu-id="93fd2-124">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="93fd2-124">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="93fd2-125">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="93fd2-125">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="93fd2-126">La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="93fd2-126">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
5.  <span data-ttu-id="93fd2-127">Type **setpsn-hipsvc\computername.domain.com domain\hissvc**</span><span class="sxs-lookup"><span data-stu-id="93fd2-127">Type **setpsn -a hipsvc\computername.domain.com domain\hissvc**</span></span>  
  
     <span data-ttu-id="93fd2-128">où **hipsvc\computername.domain.com** est un service qui effectue l’opération et l’ordinateur, il est en cours d’exécution, et **domain\hissvc** est le compte de service associé à hipsvc.</span><span class="sxs-lookup"><span data-stu-id="93fd2-128">where **hipsvc\computername.domain.com** is the service that will perform the operation and the computer it is running on, and **domain\hissvc** is the service account for hipsvc.</span></span>  
  
 <span data-ttu-id="93fd2-129">Après avoir effectué cette opération, vous pouvez configurer la délégation contrainte dans Active Directory pour ce compte de service (domain\hissvc) afin d'accéder aux ressources appropriées sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="93fd2-129">After doing this, you can configure constrained delegation in Active Directory for this service account (domain\hissvc) to access the appropriate resource in the network.</span></span>  
  
#### <a name="to-give-tcb-privileges-for-the-sso-service-account"></a><span data-ttu-id="93fd2-130">Pour octroyer les privilèges TCB pour le compte de service de l'authentification unique</span><span class="sxs-lookup"><span data-stu-id="93fd2-130">To give TCB privileges for the SSO service account</span></span>  
  
-   <span data-ttu-id="93fd2-131">Sous votre **stratégie de sécurité de domaine - stratégies locales - Attribution des droits utilisateur**, ajoutez le compte de Service d’authentification unique pour le **agir en tant que partie du système d’exploitation** stratégie.</span><span class="sxs-lookup"><span data-stu-id="93fd2-131">Under your **Domain Security Policy - Local Policies - User Rights Assignment**, add the SSO Service account to the **Act as part of operating system** policy.</span></span>  
  
     <span data-ttu-id="93fd2-132">Pour plus d’informations sur Kerberos Protocol Transition and Constrained Delegation, accédez à [http://go.microsoft.com/fwlink/?LinkId=195484](http://go.microsoft.com/fwlink/?LinkId=195484).</span><span class="sxs-lookup"><span data-stu-id="93fd2-132">For more information about Kerberos Protocol Transition and Constrained Delegation, go to [http://go.microsoft.com/fwlink/?LinkId=195484](http://go.microsoft.com/fwlink/?LinkId=195484).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93fd2-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93fd2-133">See Also</span></span>  
 [<span data-ttu-id="93fd2-134">Authentification unique initiée par l’hôte</span><span class="sxs-lookup"><span data-stu-id="93fd2-134">Host Initiated SSO</span></span>](../core/host-initiated-sso.md)