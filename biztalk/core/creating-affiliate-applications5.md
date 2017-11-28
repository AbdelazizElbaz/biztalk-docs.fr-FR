---
title: "Création d’applications associées pour TIBCO EMS | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 191e5b56-dab9-4bf3-9f89-a900907d64e0
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce5df15794886f9177f12f2a9e9a33e3ffdc335f
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="create-affiliate-applications"></a><span data-ttu-id="3f521-102">Création d’Applications associées</span><span class="sxs-lookup"><span data-stu-id="3f521-102">Create Affiliate Applications</span></span>
<span data-ttu-id="3f521-103">Les procédures suivantes décrivent l'utilisation des applications associées et de l'authentification unique (SSO).</span><span class="sxs-lookup"><span data-stu-id="3f521-103">The following steps describe how to start using affiliate applications and Single Sign-On (SSO).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f521-104">si vous recevez des erreurs liées à l'authentification unique, vérifiez que vous avez utilisé un compte de domaine lors de la configuration de BizTalk Server. En effet, cela affecte les fonctionnalités du service d'authentification unique de l'entreprise</span><span class="sxs-lookup"><span data-stu-id="3f521-104">If you receive SSO errors, verify that you used a domain account when you configured BizTalk Server; this affects the function of the Enterprise SSO service.</span></span> <span data-ttu-id="3f521-105">(compatible avec les comptes de domaine uniquement).</span><span class="sxs-lookup"><span data-stu-id="3f521-105">SSO only functions under a domain account</span></span>  
  
## <a name="create-an-affiliate-application"></a><span data-ttu-id="3f521-106">Créer une application associée</span><span class="sxs-lookup"><span data-stu-id="3f521-106">Create an affiliate application</span></span>  
  
1.  <span data-ttu-id="3f521-107">Dans le panneau de configuration, ouvrez **Services**et vérifiez que le service Enterprise Single Sign-On est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3f521-107">In Control Panel, open **Services**, and verify that the Enterprise Single Sign-On service is running.</span></span>  
  
2.  <span data-ttu-id="3f521-108">Dans une invite de commandes, accédez au dossier Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="3f521-108">In a command prompt, change directories to the Enterprise Single Sign-On folder.</span></span>  
  
     <span data-ttu-id="3f521-109">Exemple :</span><span class="sxs-lookup"><span data-stu-id="3f521-109">For example:</span></span>  
  
     <span data-ttu-id="3f521-110">**C:\Program Files\Common Files\Enterprise Single Sign-On >**</span><span class="sxs-lookup"><span data-stu-id="3f521-110">**C:\Program Files\Common Files\Enterprise Single Sign-On>**</span></span>  
  
3.  <span data-ttu-id="3f521-111">Utilisez les commandes du service de l'authentification unique de l'entreprise</span><span class="sxs-lookup"><span data-stu-id="3f521-111">Use the Enterprise Single Sign-On commands.</span></span> <span data-ttu-id="3f521-112">Pour obtenir la liste de commandes, utilisez la **-aide** basculer.</span><span class="sxs-lookup"><span data-stu-id="3f521-112">For a list of commands, use the **-help** switch.</span></span>  
  
4.  <span data-ttu-id="3f521-113">Pour créer l’application associée à l’aide de *. XML en tant qu’un démarrage, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="3f521-113">To create the affiliate application by using *.XML as a start, type the following command:</span></span>  
  
     `ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml`  
  
     <span data-ttu-id="3f521-114">où :</span><span class="sxs-lookup"><span data-stu-id="3f521-114">where:</span></span>  
  
    -   <span data-ttu-id="3f521-115">C:\SSOtest est le dossier qui contient le fichier XML de votre application ;</span><span class="sxs-lookup"><span data-stu-id="3f521-115">C:\SSOtest is the folder that contains your application XML.</span></span>  
  
    -   <span data-ttu-id="3f521-116">AffiliateApplication.xml est l’application XML que vous avez créé et qui contient les informations d’authentification.</span><span class="sxs-lookup"><span data-stu-id="3f521-116">AffiliateApplication.xml is the application XML you created that contains the Sign-On information.</span></span>  
  
     <span data-ttu-id="3f521-117">Exemple :</span><span class="sxs-lookup"><span data-stu-id="3f521-117">For example:</span></span>  
  
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
  
 <span data-ttu-id="3f521-118">Si l'exemple de fichier XML est utilisé, l'application associée (TIBCO EMS App) contient les valeurs indiquées dans l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="3f521-118">By using the example XML, the affiliate application, TIBCO EMS App, contains the values as shown in the command prompt.</span></span>  
  
## <a name="create-single-sign-on-tickets"></a><span data-ttu-id="3f521-119">Créer des tickets de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="3f521-119">Create Single Sign-On tickets</span></span>  
  
1.  <span data-ttu-id="3f521-120">Tapez la commande suivante pour contrôler le comportement des tickets d'authentification unique :</span><span class="sxs-lookup"><span data-stu-id="3f521-120">Type the following command to control SSO ticket behavior:</span></span>  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  <span data-ttu-id="3f521-121">Répondez aux questions :</span><span class="sxs-lookup"><span data-stu-id="3f521-121">Answer the questions:</span></span>  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
     <span data-ttu-id="3f521-122">Une fois terminée, vous recevez une confirmation :</span><span class="sxs-lookup"><span data-stu-id="3f521-122">On completion, you receive a confirmation:</span></span>  
  
     <span data-ttu-id="3f521-123">**Utilisation d'un serveur d'authentification unique sur cet ordinateur. L’opération s’est terminée correctement.**</span><span class="sxs-lookup"><span data-stu-id="3f521-123">**Using SSO server on this computer. The operation completed successfully.**</span></span>  
  
## <a name="enable-affiliate-application-xml"></a><span data-ttu-id="3f521-124">Activer XML de l’application associée</span><span class="sxs-lookup"><span data-stu-id="3f521-124">Enable affiliate application XML</span></span>  
  
1.  <span data-ttu-id="3f521-125">Tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="3f521-125">Type the following command:</span></span>  
  
     `ssomanage -enableapp TIBCO EMSApp`  
  
2.  <span data-ttu-id="3f521-126">Tapez la commande suivante pour afficher la liste des applications et vérifier que l'application a été créée :</span><span class="sxs-lookup"><span data-stu-id="3f521-126">Type the following command to list the applications and to verify that the application was created:</span></span>  
  
     `ssoclient.exe –listapps`  
  
     <span data-ttu-id="3f521-127">Les applications associées utilisables apparaissent dans une liste :</span><span class="sxs-lookup"><span data-stu-id="3f521-127">The affiliate applications that are available for use appear in a list:</span></span>  
  
     <span data-ttu-id="3f521-128">**Applications disponibles pour IBI\YourID - TIBCO EMSApp**</span><span class="sxs-lookup"><span data-stu-id="3f521-128">**Applications available for IBI\YourID - TIBCO EMSApp**</span></span>  
  
3.  <span data-ttu-id="3f521-129">Tapez la commande suivante pour définir des informations d’identification de l’application de la filiale :</span><span class="sxs-lookup"><span data-stu-id="3f521-129">Type the following command to set the affiliate application credentials:</span></span>  
  
     `soclient.exe -setcredentials TIBCO EMSApp`  
  
4.  <span data-ttu-id="3f521-130">Lorsque vous y êtes invité, entrez les nom d'utilisateur et mot de passe.</span><span class="sxs-lookup"><span data-stu-id="3f521-130">Enter the user name and password at the prompts.</span></span> <span data-ttu-id="3f521-131">Entrez les informations d'identification de l'application associée TIBCO EMS App.</span><span class="sxs-lookup"><span data-stu-id="3f521-131">Enter the logon credentials for the TIBCO EMS App affiliate application.</span></span>  
  
     <span data-ttu-id="3f521-132">Par exemple, entrez les ID d'utilisateur et mot de passe suivants pour entrer dans le système via le serveur d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="3f521-132">For example, enter the user identification and the password for that user to enter into the system through the SSO server.</span></span>  
  
    -   <span data-ttu-id="3f521-133">ID d’utilisateur : **utilisateur**</span><span class="sxs-lookup"><span data-stu-id="3f521-133">User ID: **user**</span></span>  
  
    -   <span data-ttu-id="3f521-134">Mot de passe :`******`</span><span class="sxs-lookup"><span data-stu-id="3f521-134">Password: `******`</span></span>  
  
    -   <span data-ttu-id="3f521-135">Confirmer ?</span><span class="sxs-lookup"><span data-stu-id="3f521-135">Confirm?</span></span> <span data-ttu-id="3f521-136">Mot de passe :`******`</span><span class="sxs-lookup"><span data-stu-id="3f521-136">Password: `******`</span></span>  
  
     <span data-ttu-id="3f521-137">L’application associée apparaît dans l’adaptateur BizTalk pour TIBCO EMS **propriétés du Transport** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="3f521-137">The affiliate application appears in the BizTalk Adapter for TIBCO EMS **Transport Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f521-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f521-138">See Also</span></span>  
[<span data-ttu-id="3f521-139">Sécuriser l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="3f521-139">Secure the adapter</span></span>](../core/security-in-biztalk-adapter-for-tibco-ems.md)