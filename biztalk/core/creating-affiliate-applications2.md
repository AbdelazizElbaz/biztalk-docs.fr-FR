---
title: "Création d’applications associées pour PeopleSoft Enterprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95151163-5aaf-4683-afb7-02949ccda3e1
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a77926fa9d98606770ad2fe7715a3b0ff66ea5c
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="creating-affiliate-applications"></a><span data-ttu-id="457ef-102">Création d’Applications associées</span><span class="sxs-lookup"><span data-stu-id="457ef-102">Creating Affiliate Applications</span></span>
<span data-ttu-id="457ef-103">Les étapes suivantes montrent comment commencer à utiliser les applications associées et Single Sign-On (SSO).</span><span class="sxs-lookup"><span data-stu-id="457ef-103">The following steps show how to start using affiliate applications and Single Sign-On (SSO).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="457ef-104">Si vous recevez des erreurs de l’authentification unique, vérifiez que vous avez utilisé un compte de domaine lorsque vous avez configuré BizTalk Server, comme cela affecte les fonctionnalités du service SSO de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="457ef-104">If you receive SSO errors, verify that you used a domain account when you were configuring BizTalk Server, as this affects the function of the Enterprise SSO service.</span></span> <span data-ttu-id="457ef-105">(SSO n'est compatible qu'avec les comptes de domaine).</span><span class="sxs-lookup"><span data-stu-id="457ef-105">SSO only functions under a domain account.</span></span>  
  
## <a name="create-an-affiliate-application"></a><span data-ttu-id="457ef-106">Créer une application associée</span><span class="sxs-lookup"><span data-stu-id="457ef-106">Create an affiliate application</span></span>  
  
1.  <span data-ttu-id="457ef-107">Dans le panneau de configuration, ouvrez **Services**et vérifiez que le service Enterprise Single Sign-On est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="457ef-107">In Control Panel, open **Services**, and verify that the Enterprise Single Sign-On service is running.</span></span>  
  
2.  <span data-ttu-id="457ef-108">Dans une invite de commandes, accédez au dossier Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="457ef-108">In a command prompt, change directories to the Enterprise Single Sign-On folder.</span></span>  
  
     <span data-ttu-id="457ef-109">Exemple :</span><span class="sxs-lookup"><span data-stu-id="457ef-109">For example:</span></span>  
  
     <span data-ttu-id="457ef-110">**C:\Program Files\Common Files\Enterprise Single Sign-On >**</span><span class="sxs-lookup"><span data-stu-id="457ef-110">**C:\Program Files\Common Files\Enterprise Single Sign-On>**</span></span>  
  
3.  <span data-ttu-id="457ef-111">Utilisez les commandes du service de l'authentification unique de l'entreprise</span><span class="sxs-lookup"><span data-stu-id="457ef-111">Use the Enterprise Single Sign-On commands.</span></span> <span data-ttu-id="457ef-112">Pour obtenir la liste de commandes, utilisez la **-aide** basculer.</span><span class="sxs-lookup"><span data-stu-id="457ef-112">For a list of commands, use the **-help** switch.</span></span>  
  
     ![](../core/media/siebeladapter-23-sso-commands.gif "SiebelAdapter_23_SSO_Commands")  
  
4.  <span data-ttu-id="457ef-113">Pour créer l’application associée à l’aide de *. XML en tant qu’un démarrage, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="457ef-113">To create the affiliate application by using *.XML as a start, type the following command:</span></span>  
  
     `ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml`  
  
     <span data-ttu-id="457ef-114">où :</span><span class="sxs-lookup"><span data-stu-id="457ef-114">where:</span></span>  
  
    -   <span data-ttu-id="457ef-115">C:\SSOtest est le dossier qui contient le fichier XML de votre application ;</span><span class="sxs-lookup"><span data-stu-id="457ef-115">C:\SSOtest is the folder that contains your application XML.</span></span>  
  
    -   <span data-ttu-id="457ef-116">AffiliateApplication.xml est le fichier XML de l'application que vous avez créée qui contient les informations de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="457ef-116">AffiliateApplication.xml is the application XML you created that contains the sign-on information.</span></span>  
  
     <span data-ttu-id="457ef-117">Exemple :</span><span class="sxs-lookup"><span data-stu-id="457ef-117">For example:</span></span>  
  
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
  
## <a name="create-single-sign-on-tickets"></a><span data-ttu-id="457ef-118">Créer des Tickets d’authentification uniques</span><span class="sxs-lookup"><span data-stu-id="457ef-118">Create Single Sign-On Tickets</span></span>  
  
1.  <span data-ttu-id="457ef-119">Tapez la commande suivante pour contrôler le comportement des tickets d'authentification unique :</span><span class="sxs-lookup"><span data-stu-id="457ef-119">Type the following command to control SSO ticket behavior:</span></span>  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  <span data-ttu-id="457ef-120">Répondez aux questions :</span><span class="sxs-lookup"><span data-stu-id="457ef-120">Answer the questions:</span></span>  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
     <span data-ttu-id="457ef-121">Une fois terminée, vous recevez une confirmation :</span><span class="sxs-lookup"><span data-stu-id="457ef-121">On completion, you receive a confirmation:</span></span>  
  
     <span data-ttu-id="457ef-122">**Utilisation d'un serveur d'authentification unique sur cet ordinateur. L’opération s’est terminée correctement.**</span><span class="sxs-lookup"><span data-stu-id="457ef-122">**Using SSO server on this computer. The operation completed successfully.**</span></span>  
  
## <a name="enable-the-affiliate-application-xml"></a><span data-ttu-id="457ef-123">Activer l’Application associée XML</span><span class="sxs-lookup"><span data-stu-id="457ef-123">Enable the Affiliate Application XML</span></span>  
  
1.  <span data-ttu-id="457ef-124">Tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="457ef-124">Type the following command:</span></span>  
  
     `ssomanage -enableapp PeopleSoftApp`  
  
2.  <span data-ttu-id="457ef-125">Tapez la commande suivante pour afficher la liste des applications et vérifier que l'application a été créée :</span><span class="sxs-lookup"><span data-stu-id="457ef-125">Type the following command to list the applications and to verify that the application was created:</span></span>  
  
     `ssoclient.exe –listapps`  
  
     <span data-ttu-id="457ef-126">Les applications associées utilisables apparaissent dans une liste.</span><span class="sxs-lookup"><span data-stu-id="457ef-126">The affiliate applications that are available for use appear in a list.</span></span>  
  
     <span data-ttu-id="457ef-127">**Applications disponibles pour IBI\YourID - PeopleSoftApp**</span><span class="sxs-lookup"><span data-stu-id="457ef-127">**Applications available for IBI\YourID - PeopleSoftApp**</span></span>  
  
3.  <span data-ttu-id="457ef-128">Tapez la commande suivante pour définir des informations d’identification de l’application de la filiale :</span><span class="sxs-lookup"><span data-stu-id="457ef-128">Type the following command to set the affiliate application credentials:</span></span>  
  
     `ssoclient.exe -setcredentials PeopleSoftApp`  
  
4.  <span data-ttu-id="457ef-129">Lorsque vous y êtes invité, entrez les nom d'utilisateur et mot de passe.</span><span class="sxs-lookup"><span data-stu-id="457ef-129">Enter the user name and password at the prompts.</span></span> <span data-ttu-id="457ef-130">Entrez les informations d'identification de l'application associée PeopleSoftApp.</span><span class="sxs-lookup"><span data-stu-id="457ef-130">Enter the logon credentials for the PeopleSoftApp affiliate application.</span></span>  
  
     <span data-ttu-id="457ef-131">Par exemple, entrez les ID d'utilisateur et mot de passe suivants pour entrer dans le système via le serveur d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="457ef-131">For example, enter the user identification and the password for that user to enter into the system through the SSO server.</span></span>  
  
    -   <span data-ttu-id="457ef-132">**ID d’utilisateur :**`user`</span><span class="sxs-lookup"><span data-stu-id="457ef-132">**User ID:** `user`</span></span>  
  
    -   <span data-ttu-id="457ef-133">**Mot de passe :**`******`</span><span class="sxs-lookup"><span data-stu-id="457ef-133">**Password:** `******`</span></span>  
  
    -   <span data-ttu-id="457ef-134">**Confirmer ? Mot de passe :**`******`</span><span class="sxs-lookup"><span data-stu-id="457ef-134">**Confirm? Password:** `******`</span></span>  
  
5.  <span data-ttu-id="457ef-135">L'application associée apparaît dans la boîte de dialogue Propriétés du transport de l'adaptateur BizTalk pour PeopleSoft Enterprise.</span><span class="sxs-lookup"><span data-stu-id="457ef-135">The affiliate application appears in the BizTalk Adapter for PeopleSoft Enterprise Transport Properties dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="457ef-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="457ef-136">See Also</span></span>  
 [<span data-ttu-id="457ef-137">Sécuriser l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="457ef-137">Secure the adapter</span></span>](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)