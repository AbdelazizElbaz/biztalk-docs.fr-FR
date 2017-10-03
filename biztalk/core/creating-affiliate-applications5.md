---
title: "Création d’applications associées à des Applications5 | Documents Microsoft"
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
- creating affiliate applications
- tickets, SSO
- affiliate applications, enabling XML
- SSO tickets
ms.assetid: 191e5b56-dab9-4bf3-9f89-a900907d64e0
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc6b42a6f3251d9e897af21fcb4207b6790e91cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-affiliate-applications"></a><span data-ttu-id="c60b2-102">Création d’Applications associées</span><span class="sxs-lookup"><span data-stu-id="c60b2-102">Creating Affiliate Applications</span></span>
<span data-ttu-id="c60b2-103">Les procédures suivantes décrivent l'utilisation des applications associées et de l'authentification unique (SSO).</span><span class="sxs-lookup"><span data-stu-id="c60b2-103">The following steps describe how to start using affiliate applications and Single Sign-On (SSO).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c60b2-104">si vous recevez des erreurs liées à l'authentification unique, vérifiez que vous avez utilisé un compte de domaine lors de la configuration de BizTalk Server. En effet, cela affecte les fonctionnalités du service d'authentification unique de l'entreprise</span><span class="sxs-lookup"><span data-stu-id="c60b2-104">If you receive SSO errors, verify that you used a domain account when you configured BizTalk Server; this affects the function of the Enterprise SSO service.</span></span> <span data-ttu-id="c60b2-105">(compatible avec les comptes de domaine uniquement).</span><span class="sxs-lookup"><span data-stu-id="c60b2-105">SSO only functions under a domain account</span></span>  
  
### <a name="to-create-an-affiliate-application"></a><span data-ttu-id="c60b2-106">Pour créer une application associée</span><span class="sxs-lookup"><span data-stu-id="c60b2-106">To create an affiliate application</span></span>  
  
1.  <span data-ttu-id="c60b2-107">Dans le panneau de configuration, ouvrez **Services**et vérifiez que le service Enterprise Single Sign-On est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="c60b2-107">In Control Panel, open **Services**, and verify that the Enterprise Single Sign-On service is running.</span></span>  
  
2.  <span data-ttu-id="c60b2-108">Dans une invite de commandes, accédez au dossier Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="c60b2-108">In a command prompt, change directories to the Enterprise Single Sign-On folder.</span></span>  
  
     <span data-ttu-id="c60b2-109">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c60b2-109">For example:</span></span>  
  
     <span data-ttu-id="c60b2-110">**C:\Program Files\Common Files\Enterprise Single Sign-On >**</span><span class="sxs-lookup"><span data-stu-id="c60b2-110">**C:\Program Files\Common Files\Enterprise Single Sign-On>**</span></span>  
  
3.  <span data-ttu-id="c60b2-111">Utilisez les commandes du service de l'authentification unique de l'entreprise</span><span class="sxs-lookup"><span data-stu-id="c60b2-111">Use the Enterprise Single Sign-On commands.</span></span> <span data-ttu-id="c60b2-112">Pour obtenir la liste de commandes, utilisez la **-aide** basculer.</span><span class="sxs-lookup"><span data-stu-id="c60b2-112">For a list of commands, use the **-help** switch.</span></span>  
  
4.  <span data-ttu-id="c60b2-113">Pour créer l’application associée à l’aide de *. XML en tant qu’un démarrage, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="c60b2-113">To create the affiliate application by using *.XML as a start, type the following command:</span></span>  
  
     `ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml`  
  
     <span data-ttu-id="c60b2-114">où :</span><span class="sxs-lookup"><span data-stu-id="c60b2-114">where:</span></span>  
  
    -   <span data-ttu-id="c60b2-115">C:\SSOtest est le dossier qui contient le fichier XML de votre application ;</span><span class="sxs-lookup"><span data-stu-id="c60b2-115">C:\SSOtest is the folder that contains your application XML.</span></span>  
  
    -   <span data-ttu-id="c60b2-116">AffiliateApplication.xml est l’application XML que vous avez créé et qui contient les informations d’authentification.</span><span class="sxs-lookup"><span data-stu-id="c60b2-116">AffiliateApplication.xml is the application XML you created that contains the Sign-On information.</span></span>  
  
     <span data-ttu-id="c60b2-117">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c60b2-117">For example:</span></span>  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
        <application name="TIBCO EMS App">  
            <description>TIBCO EMS SSO Application</description>  
            <contact>someone@example.com</contact>  
            <appUserAccount>DomainName\AppUserGroup</appUserAccount>  
            <!—an existing group on the domain controller - >   
            <appAdminAccount>DomainName\AppAdminGroup</appAdminAccount>  
            <!-- an existing account in the domain group - >   
            <field ordinal="0" label="User ID" masked="no" />  
            <field ordinal="1" label="Password" masked="yes" />  
            <flags groupApp="no" allowTickets="yes" enableApp="yes"/>  
        </application>  
    </SSO>  
    ```  
  
 <span data-ttu-id="c60b2-118">Si l'exemple de fichier XML est utilisé, l'application associée (TIBCO EMS App) contient les valeurs indiquées dans l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="c60b2-118">By using the example XML, the affiliate application, TIBCO EMS App, contains the values as shown in the command prompt.</span></span>  
  
### <a name="to-create-single-sign-on-tickets"></a><span data-ttu-id="c60b2-119">Pour créer des tickets d'authentification unique</span><span class="sxs-lookup"><span data-stu-id="c60b2-119">To create Single Sign-On tickets</span></span>  
  
1.  <span data-ttu-id="c60b2-120">Tapez la commande suivante pour contrôler le comportement des tickets d'authentification unique :</span><span class="sxs-lookup"><span data-stu-id="c60b2-120">Type the following command to control SSO ticket behavior:</span></span>  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  <span data-ttu-id="c60b2-121">Répondez aux questions :</span><span class="sxs-lookup"><span data-stu-id="c60b2-121">Answer the questions:</span></span>  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
     <span data-ttu-id="c60b2-122">Une fois terminée, vous recevez une confirmation :</span><span class="sxs-lookup"><span data-stu-id="c60b2-122">On completion, you receive a confirmation:</span></span>  
  
     <span data-ttu-id="c60b2-123">**Utilisation d'un serveur d'authentification unique sur cet ordinateur. L’opération s’est terminée correctement.**</span><span class="sxs-lookup"><span data-stu-id="c60b2-123">**Using SSO server on this computer. The operation completed successfully.**</span></span>  
  
### <a name="to-enable-affiliate-application-xml"></a><span data-ttu-id="c60b2-124">Pour activer le fichier XML de l'application associée</span><span class="sxs-lookup"><span data-stu-id="c60b2-124">To enable affiliate application XML</span></span>  
  
1.  <span data-ttu-id="c60b2-125">Tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="c60b2-125">Type the following command:</span></span>  
  
     `ssomanage -enableapp TIBCO EMSApp`  
  
2.  <span data-ttu-id="c60b2-126">Tapez la commande suivante pour afficher la liste des applications et vérifier que l'application a été créée :</span><span class="sxs-lookup"><span data-stu-id="c60b2-126">Type the following command to list the applications and to verify that the application was created:</span></span>  
  
     `ssoclient.exe –listapps`  
  
     <span data-ttu-id="c60b2-127">Les applications associées utilisables apparaissent dans une liste :</span><span class="sxs-lookup"><span data-stu-id="c60b2-127">The affiliate applications that are available for use appear in a list:</span></span>  
  
     <span data-ttu-id="c60b2-128">**Applications disponibles pour IBI\YourID - TIBCO EMSApp**</span><span class="sxs-lookup"><span data-stu-id="c60b2-128">**Applications available for IBI\YourID - TIBCO EMSApp**</span></span>  
  
3.  <span data-ttu-id="c60b2-129">Tapez la commande suivante pour définir des informations d’identification de l’application de la filiale :</span><span class="sxs-lookup"><span data-stu-id="c60b2-129">Type the following command to set the affiliate application credentials:</span></span>  
  
     `soclient.exe -setcredentials TIBCO EMSApp`  
  
4.  <span data-ttu-id="c60b2-130">Lorsque vous y êtes invité, entrez les nom d'utilisateur et mot de passe.</span><span class="sxs-lookup"><span data-stu-id="c60b2-130">Enter the user name and password at the prompts.</span></span> <span data-ttu-id="c60b2-131">Entrez les informations d'identification de l'application associée TIBCO EMS App.</span><span class="sxs-lookup"><span data-stu-id="c60b2-131">Enter the logon credentials for the TIBCO EMS App affiliate application.</span></span>  
  
     <span data-ttu-id="c60b2-132">Par exemple, entrez les ID d'utilisateur et mot de passe suivants pour entrer dans le système via le serveur d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="c60b2-132">For example, enter the user identification and the password for that user to enter into the system through the SSO server.</span></span>  
  
    -   <span data-ttu-id="c60b2-133">ID d’utilisateur : **utilisateur**</span><span class="sxs-lookup"><span data-stu-id="c60b2-133">User ID: **user**</span></span>  
  
    -   <span data-ttu-id="c60b2-134">Mot de passe :`******`</span><span class="sxs-lookup"><span data-stu-id="c60b2-134">Password: `******`</span></span>  
  
    -   <span data-ttu-id="c60b2-135">Confirmer ?</span><span class="sxs-lookup"><span data-stu-id="c60b2-135">Confirm?</span></span> <span data-ttu-id="c60b2-136">Mot de passe :`******`</span><span class="sxs-lookup"><span data-stu-id="c60b2-136">Password: `******`</span></span>  
  
     <span data-ttu-id="c60b2-137">L’application associée apparaît dans l’adaptateur BizTalk pour TIBCO EMS **propriétés du Transport** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="c60b2-137">The affiliate application appears in the BizTalk Adapter for TIBCO EMS **Transport Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c60b2-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c60b2-138">See Also</span></span>  
 [<span data-ttu-id="c60b2-139">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="c60b2-139">Using Single Sign-On</span></span>](../core/using-single-sign-on4.md)