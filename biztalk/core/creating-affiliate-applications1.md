---
title: "Création d’applications associées à des Applications1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, affiliate
- Single Sign-On, tickets
- affiliate applications
- tickets, SSO
- affiliate applications, enabling XML
- SSO tickets
ms.assetid: f3603fcb-3594-460b-b74a-618e22d9c4e0
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f52c59caf451a2e0b55c775bf70a36a9a05ae9c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-affiliate-applications"></a><span data-ttu-id="9c81e-102">Création d’Applications associées</span><span class="sxs-lookup"><span data-stu-id="9c81e-102">Creating Affiliate Applications</span></span>
<span data-ttu-id="9c81e-103">Les procédures suivantes décrivent comment travailler avec des applications associées et de l'authentification unique (SSO).</span><span class="sxs-lookup"><span data-stu-id="9c81e-103">The following steps describe how to start working with affiliate applications and Single Sign-On (SSO).</span></span> <span data-ttu-id="9c81e-104">Pour obtenir des informations exhaustives sur l'utilisation de l'authentification unique de l'entreprise, consultez la documentation de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9c81e-104">For complete information about how to use Enterprise Single Sign-On, see the Microsoft documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c81e-105">Si vous recevez des erreurs de l’authentification unique, vérifiez que vous avez utilisé un compte de domaine lors de la configuration de BizTalk Server, comme cela affecte les fonctionnalités du service SSO de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="9c81e-105">If you receive SSO errors, verify that you used a domain account when you configured BizTalk Server, as this affects the function of the Enterprise SSO service.</span></span> <span data-ttu-id="9c81e-106">(SSO n'est compatible qu'avec les comptes de domaine).</span><span class="sxs-lookup"><span data-stu-id="9c81e-106">SSO only functions under a domain account.</span></span>  
  
### <a name="to-create-an-affiliate-application"></a><span data-ttu-id="9c81e-107">Pour créer une application associée</span><span class="sxs-lookup"><span data-stu-id="9c81e-107">To create an affiliate application</span></span>  
  
1.  <span data-ttu-id="9c81e-108">Dans le panneau de configuration, ouvrez **Services**et vérifiez que le service Enterprise Single Sign-On est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="9c81e-108">In Control Panel, open **Services**, and verify that the Enterprise Single Sign-On service is running.</span></span>  
  
2.  <span data-ttu-id="9c81e-109">Dans une invite de commandes, accédez au dossier Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="9c81e-109">In a command prompt, change directories to the Enterprise Single Sign-On folder.</span></span> <span data-ttu-id="9c81e-110">Exemple :</span><span class="sxs-lookup"><span data-stu-id="9c81e-110">For example:</span></span>  
  
     <span data-ttu-id="9c81e-111">**C:\Program Files\Common Files\Enterprise Single Sign-On >**</span><span class="sxs-lookup"><span data-stu-id="9c81e-111">**C:\Program Files\Common Files\Enterprise Single Sign-On>**</span></span>  
  
3.  <span data-ttu-id="9c81e-112">Utilisez les commandes du service de l'authentification unique de l'entreprise</span><span class="sxs-lookup"><span data-stu-id="9c81e-112">Use the Enterprise Single Sign-On commands.</span></span> <span data-ttu-id="9c81e-113">Pour obtenir la liste de commandes, utilisez la **-aide** basculer.</span><span class="sxs-lookup"><span data-stu-id="9c81e-113">For a list of commands, use the **-help** switch.</span></span>  
  
4.  <span data-ttu-id="9c81e-114">Pour créer l’application associée à l’aide de *. XML en tant qu’un démarrage, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="9c81e-114">To create the affiliate application by using *.XML as a start, type the following command:</span></span>  
  
     `ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml`  
  
     <span data-ttu-id="9c81e-115">Où :</span><span class="sxs-lookup"><span data-stu-id="9c81e-115">Where:</span></span>  
  
     <span data-ttu-id="9c81e-116">C:\SSOtest est le dossier qui contient le fichier XML de votre application ;</span><span class="sxs-lookup"><span data-stu-id="9c81e-116">C:\SSOtest is the folder that contains your application XML.</span></span>  
  
     <span data-ttu-id="9c81e-117">AffiliateApplication.xml est l’application XML que vous avez créé et qui contient les informations d’authentification.</span><span class="sxs-lookup"><span data-stu-id="9c81e-117">AffiliateApplication.xml is the application XML you created that contains the Sign-On information.</span></span>  
  
     <span data-ttu-id="9c81e-118">Exemple :</span><span class="sxs-lookup"><span data-stu-id="9c81e-118">For example:</span></span>  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
        <application name="TIBCO RendezvousApp">  
            <description> TIBCO Rendezvous SSO Application</description>  
            <contact>someone@microsoft.com</contact>  
            <userGroup>ibi\Domain Users</userGroup>  
            <!—an existing group on the domain controller - >   
            <appAdminGroup>ibi\YourID</appAdminGroup>  
            <!-- an existing account within the domain group - >   
  
            <field ordinal="0" label="User ID" masked="no" />  
            <field ordinal="1" label="Password" masked="yes" />  
            <flags groupApp="no" allowTickets="yes" enableApp="yes"/>  
  
        </application>  
    </SSO>  
    ```  
  
### <a name="to-create-single-sign-on-tickets"></a><span data-ttu-id="9c81e-119">Pour créer des tickets d'authentification unique</span><span class="sxs-lookup"><span data-stu-id="9c81e-119">To create Single Sign-On tickets</span></span>  
  
1.  <span data-ttu-id="9c81e-120">Tapez la commande suivante pour contrôler le comportement des tickets d'authentification unique :</span><span class="sxs-lookup"><span data-stu-id="9c81e-120">Type the following command to control SSO ticket behavior:</span></span>  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  <span data-ttu-id="9c81e-121">Répondez aux questions comme suit :</span><span class="sxs-lookup"><span data-stu-id="9c81e-121">Answer the following questions as shown:</span></span>  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
3.  <span data-ttu-id="9c81e-122">Lorsque vous avez terminé, vous recevez la confirmation suivante :</span><span class="sxs-lookup"><span data-stu-id="9c81e-122">On completion, you receive the following confirmation:</span></span>  
  
     <span data-ttu-id="9c81e-123">**Utilisation d'un serveur d'authentification unique sur cet ordinateur. L’opération s’est terminée correctement.**</span><span class="sxs-lookup"><span data-stu-id="9c81e-123">**Using SSO server on this computer. The operation completed successfully.**</span></span>  
  
### <a name="to-enable-affiliate-application-xml"></a><span data-ttu-id="9c81e-124">Pour activer le fichier XML de l'application associée</span><span class="sxs-lookup"><span data-stu-id="9c81e-124">To enable affiliate application XML</span></span>  
  
1.  <span data-ttu-id="9c81e-125">Tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="9c81e-125">Type the following command:</span></span>  
  
     `ssomanage -enableapp TIBCO RendezvousApp`  
  
2.  <span data-ttu-id="9c81e-126">Tapez la commande suivante pour afficher la liste des applications et vérifier que l'application a été créée :</span><span class="sxs-lookup"><span data-stu-id="9c81e-126">Type the following command to list the applications and to verify that the application was created:</span></span>  
  
     `ssoclient.exe –listapps`  
  
     <span data-ttu-id="9c81e-127">Les applications associées utilisables apparaissent dans une liste.</span><span class="sxs-lookup"><span data-stu-id="9c81e-127">The affiliate applications that are available for use appear in a list.</span></span>  
  
     <span data-ttu-id="9c81e-128">**Applications disponibles pour IBI\YourID - TIBCO RendezvousApp**</span><span class="sxs-lookup"><span data-stu-id="9c81e-128">**Applications available for IBI\YourID - TIBCO RendezvousApp**</span></span>  
  
3.  <span data-ttu-id="9c81e-129">Tapez la commande suivante pour définir des informations d’identification de l’application de la filiale :</span><span class="sxs-lookup"><span data-stu-id="9c81e-129">Type the following command to set the affiliate application credentials:</span></span>  
  
     `ssoclient.exe -setcredentials TIBCO RendezvousApp`  
  
4.  <span data-ttu-id="9c81e-130">Entrez le nom d’utilisateur et un mot de passe à la demande.</span><span class="sxs-lookup"><span data-stu-id="9c81e-130">Enter the User name and password at the prompts.</span></span>  
  
5.  <span data-ttu-id="9c81e-131">Entrez les informations d'identification de l'application associée TIBCO RendezvousApp.</span><span class="sxs-lookup"><span data-stu-id="9c81e-131">Enter the logon credentials for the TIBCO RendezvousApp affiliate application.</span></span>  
  
     <span data-ttu-id="9c81e-132">Par exemple, entrez l'ID d'utilisateur et le mot de passe pour entrer dans le système via le serveur d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="9c81e-132">For example, enter the user identification and the password for the user to enter into the system through the SSO server.</span></span>  
  
    -   <span data-ttu-id="9c81e-133">ID d'utilisateur : utilisateur</span><span class="sxs-lookup"><span data-stu-id="9c81e-133">User ID: user</span></span>  
  
    -   <span data-ttu-id="9c81e-134">Mot de passe : ******</span><span class="sxs-lookup"><span data-stu-id="9c81e-134">Password: ******</span></span>  
  
    -   <span data-ttu-id="9c81e-135">Confirmer le mot de passe : ******</span><span class="sxs-lookup"><span data-stu-id="9c81e-135">Confirm Password: ******</span></span>  
  
6.  <span data-ttu-id="9c81e-136">L’application associée apparaît dans l’adaptateur BizTalk pour TIBCO Rendezvous **propriétés du Transport** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="9c81e-136">The affiliate application appears in the BizTalk Adapter for TIBCO Rendezvous **Transport Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c81e-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c81e-137">See Also</span></span>  
 <span data-ttu-id="9c81e-138">[Sécurité de l’adaptateur BizTalk pour TIBCO Rendezvous](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="9c81e-138">[Security in BizTalk Adapter for TIBCO Rendezvous](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="9c81e-139">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="9c81e-139">Using Single Sign-On</span></span>](../core/using-single-sign-on5.md)