---
title: "Création d’applications associées à des SNMP2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Single Sign-On, creating tickets
- creating affiliate applications
- tickets, SSO
- affiliate applications, enabling XML
- affiliate applications, creating
- SSO tickets
ms.assetid: 95151163-5aaf-4683-afb7-02949ccda3e1
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f39fbbfb62a9081937891b98e2b01a5e7f046e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-affiliate-applications"></a><span data-ttu-id="35768-102">Création d’Applications associées</span><span class="sxs-lookup"><span data-stu-id="35768-102">Creating Affiliate Applications</span></span>
<span data-ttu-id="35768-103">Les étapes suivantes montrent comment commencer à utiliser les applications associées et Single Sign-On (SSO).</span><span class="sxs-lookup"><span data-stu-id="35768-103">The following steps show how to start using affiliate applications and Single Sign-On (SSO).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35768-104">Si vous recevez des erreurs de l’authentification unique, vérifiez que vous avez utilisé un compte de domaine lorsque vous avez configuré BizTalk Server, comme cela affecte les fonctionnalités du service SSO de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="35768-104">If you receive SSO errors, verify that you used a domain account when you were configuring BizTalk Server, as this affects the function of the Enterprise SSO service.</span></span> <span data-ttu-id="35768-105">(SSO n'est compatible qu'avec les comptes de domaine).</span><span class="sxs-lookup"><span data-stu-id="35768-105">SSO only functions under a domain account.</span></span>  
  
### <a name="to-create-an-affiliate-application"></a><span data-ttu-id="35768-106">Pour créer une application associée</span><span class="sxs-lookup"><span data-stu-id="35768-106">To create an affiliate application</span></span>  
  
1.  <span data-ttu-id="35768-107">Dans le panneau de configuration, ouvrez **Services**et vérifiez que le service Enterprise Single Sign-On est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="35768-107">In Control Panel, open **Services**, and verify that the Enterprise Single Sign-On service is running.</span></span>  
  
2.  <span data-ttu-id="35768-108">Dans une invite de commandes, accédez au dossier Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="35768-108">In a command prompt, change directories to the Enterprise Single Sign-On folder.</span></span>  
  
     <span data-ttu-id="35768-109">Exemple :</span><span class="sxs-lookup"><span data-stu-id="35768-109">For example:</span></span>  
  
     <span data-ttu-id="35768-110">**C:\Program Files\Common Files\Enterprise Single Sign-On >**</span><span class="sxs-lookup"><span data-stu-id="35768-110">**C:\Program Files\Common Files\Enterprise Single Sign-On>**</span></span>  
  
3.  <span data-ttu-id="35768-111">Utilisez les commandes du service de l'authentification unique de l'entreprise</span><span class="sxs-lookup"><span data-stu-id="35768-111">Use the Enterprise Single Sign-On commands.</span></span> <span data-ttu-id="35768-112">Pour obtenir la liste de commandes, utilisez la **-aide** basculer.</span><span class="sxs-lookup"><span data-stu-id="35768-112">For a list of commands, use the **-help** switch.</span></span>  
  
     ![](../core/media/siebeladapter-23-sso-commands.gif "SiebelAdapter_23_SSO_Commands")  
  
4.  <span data-ttu-id="35768-113">Pour créer l’application associée à l’aide de *. XML en tant qu’un démarrage, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="35768-113">To create the affiliate application by using *.XML as a start, type the following command:</span></span>  
  
     `ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml`  
  
     <span data-ttu-id="35768-114">où :</span><span class="sxs-lookup"><span data-stu-id="35768-114">where:</span></span>  
  
    -   <span data-ttu-id="35768-115">C:\SSOtest est le dossier qui contient le fichier XML de votre application ;</span><span class="sxs-lookup"><span data-stu-id="35768-115">C:\SSOtest is the folder that contains your application XML.</span></span>  
  
    -   <span data-ttu-id="35768-116">AffiliateApplication.xml est le fichier XML de l'application que vous avez créée qui contient les informations de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="35768-116">AffiliateApplication.xml is the application XML you created that contains the sign-on information.</span></span>  
  
     <span data-ttu-id="35768-117">Exemple :</span><span class="sxs-lookup"><span data-stu-id="35768-117">For example:</span></span>  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
         <application name="PeopleSoftApp">  
              <description>PeopleSoft SSO Application</description>  
              <contact>someone@microsoft.com</contact>  
             <appUserAccount>DomainName\AppUserGroup</appUserAccount>  
              <!—-an existing group on the domain controller - >   
              <appAdminAccount>DomainName\AppAdminGroup<appAdminAccount>   
              <!-- an existing account in the domain group - >   
              <field ordinal="0" label="User ID" masked="no" />  
              <field ordinal="1" label="Password" masked="yes" />  
              <flags groupApp="no" allowTickets="yes" enableApp="yes"/>  
         </application>  
    </SSO>  
    ```  
  
## <a name="creating-single-sign-on-tickets"></a><span data-ttu-id="35768-118">Création de tickets d'authentification unique</span><span class="sxs-lookup"><span data-stu-id="35768-118">Creating Single Sign-On Tickets</span></span>  
  
#### <a name="to-create-sso-tickets"></a><span data-ttu-id="35768-119">Pour créer des tickets SSO</span><span class="sxs-lookup"><span data-stu-id="35768-119">To create SSO tickets</span></span>  
  
1.  <span data-ttu-id="35768-120">Tapez la commande suivante pour contrôler le comportement des tickets d'authentification unique :</span><span class="sxs-lookup"><span data-stu-id="35768-120">Type the following command to control SSO ticket behavior:</span></span>  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  <span data-ttu-id="35768-121">Répondez aux questions :</span><span class="sxs-lookup"><span data-stu-id="35768-121">Answer the questions:</span></span>  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
     <span data-ttu-id="35768-122">Une fois terminée, vous recevez une confirmation :</span><span class="sxs-lookup"><span data-stu-id="35768-122">On completion, you receive a confirmation:</span></span>  
  
     <span data-ttu-id="35768-123">**Utilisation d'un serveur d'authentification unique sur cet ordinateur. L’opération s’est terminée correctement.**</span><span class="sxs-lookup"><span data-stu-id="35768-123">**Using SSO server on this computer. The operation completed successfully.**</span></span>  
  
## <a name="enabling-the-affiliate-application-xml"></a><span data-ttu-id="35768-124">Activation du fichier XML de l'application associée</span><span class="sxs-lookup"><span data-stu-id="35768-124">Enabling the Affiliate Application XML</span></span>  
  
#### <a name="to-enable-affiliate-application-xml"></a><span data-ttu-id="35768-125">Pour activer le fichier XML de l'application associée</span><span class="sxs-lookup"><span data-stu-id="35768-125">To enable affiliate application XML</span></span>  
  
1.  <span data-ttu-id="35768-126">Tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="35768-126">Type the following command:</span></span>  
  
     `ssomanage -enableapp PeopleSoftApp`  
  
2.  <span data-ttu-id="35768-127">Tapez la commande suivante pour afficher la liste des applications et vérifier que l'application a été créée :</span><span class="sxs-lookup"><span data-stu-id="35768-127">Type the following command to list the applications and to verify that the application was created:</span></span>  
  
     `ssoclient.exe –listapps`  
  
     <span data-ttu-id="35768-128">Les applications associées utilisables apparaissent dans une liste.</span><span class="sxs-lookup"><span data-stu-id="35768-128">The affiliate applications that are available for use appear in a list.</span></span>  
  
     <span data-ttu-id="35768-129">**Applications disponibles pour IBI\YourID - PeopleSoftApp**</span><span class="sxs-lookup"><span data-stu-id="35768-129">**Applications available for IBI\YourID - PeopleSoftApp**</span></span>  
  
3.  <span data-ttu-id="35768-130">Tapez la commande suivante pour définir des informations d’identification de l’application de la filiale :</span><span class="sxs-lookup"><span data-stu-id="35768-130">Type the following command to set the affiliate application credentials:</span></span>  
  
     `ssoclient.exe -setcredentials PeopleSoftApp`  
  
4.  <span data-ttu-id="35768-131">Lorsque vous y êtes invité, entrez les nom d'utilisateur et mot de passe.</span><span class="sxs-lookup"><span data-stu-id="35768-131">Enter the user name and password at the prompts.</span></span> <span data-ttu-id="35768-132">Entrez les informations d'identification de l'application associée PeopleSoftApp.</span><span class="sxs-lookup"><span data-stu-id="35768-132">Enter the logon credentials for the PeopleSoftApp affiliate application.</span></span>  
  
     <span data-ttu-id="35768-133">Par exemple, entrez les ID d'utilisateur et mot de passe suivants pour entrer dans le système via le serveur d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="35768-133">For example, enter the user identification and the password for that user to enter into the system through the SSO server.</span></span>  
  
    -   <span data-ttu-id="35768-134">**ID d’utilisateur :**`user`</span><span class="sxs-lookup"><span data-stu-id="35768-134">**User ID:** `user`</span></span>  
  
    -   <span data-ttu-id="35768-135">**Mot de passe :**`******`</span><span class="sxs-lookup"><span data-stu-id="35768-135">**Password:** `******`</span></span>  
  
    -   <span data-ttu-id="35768-136">**Confirmer ? Mot de passe :**`******`</span><span class="sxs-lookup"><span data-stu-id="35768-136">**Confirm? Password:** `******`</span></span>  
  
5.  <span data-ttu-id="35768-137">L'application associée apparaît dans la boîte de dialogue Propriétés du transport de l'adaptateur BizTalk pour PeopleSoft Enterprise.</span><span class="sxs-lookup"><span data-stu-id="35768-137">The affiliate application appears in the BizTalk Adapter for PeopleSoft Enterprise Transport Properties dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35768-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35768-138">See Also</span></span>  
 [<span data-ttu-id="35768-139">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="35768-139">Using Single Sign-On</span></span>](../core/using-single-sign-on2.md)