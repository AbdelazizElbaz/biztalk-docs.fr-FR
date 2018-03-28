---
title: Création d’applications associées à des Applications3 | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- affiliate applications
- Single Sign-On, creating tickets
- tickets, creating Single Sign-On
- affiliate applications, creating
- SSO tickets
ms.assetid: 800644fd-2286-4e59-894b-260f584dd29f
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 857ee7edd623332e72176ac09082f0ec9fc460f4
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="creating-affiliate-applications"></a><span data-ttu-id="42ea7-102">Création d’Applications associées</span><span class="sxs-lookup"><span data-stu-id="42ea7-102">Creating Affiliate Applications</span></span>
<span data-ttu-id="42ea7-103">Les procédures suivantes décrivent l'utilisation des applications associées à l'aide de l'authentification unique (SSO).</span><span class="sxs-lookup"><span data-stu-id="42ea7-103">The following steps describe how to get started with affiliate applications using Single Sign-On (SSO).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42ea7-104">Si vous recevez des erreurs liées à l'authentification unique, vérifiez que vous avez utilisé un compte de domaine lors de la configuration de BizTalk Server. En effet, cela affecte les fonctionnalités du service d'authentification unique de l'entreprise</span><span class="sxs-lookup"><span data-stu-id="42ea7-104">If you get SSO errors, verify that you used a domain account when you configured BizTalk Server, because this affects the function of the ESSO service.</span></span> <span data-ttu-id="42ea7-105">(SSO n'est compatible qu'avec les comptes de domaine).</span><span class="sxs-lookup"><span data-stu-id="42ea7-105">SSO only functions under a domain account.</span></span>  
  
## <a name="creating-an-affiliate-application"></a><span data-ttu-id="42ea7-106">Création d'une application associée</span><span class="sxs-lookup"><span data-stu-id="42ea7-106">Creating an Affiliate Application</span></span>  
  
#### <a name="to-create-an-affiliate-application"></a><span data-ttu-id="42ea7-107">Pour créer une application associée</span><span class="sxs-lookup"><span data-stu-id="42ea7-107">To create an affiliate application</span></span>  
  
1.  <span data-ttu-id="42ea7-108">Dans **le panneau de configuration**, ouvrez **Services**et vérifiez que le service Enterprise Single Sign-On est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="42ea7-108">In **Control Panel**, open **Services**, and verify that the Enterprise Single Sign-On service is running.</span></span>  
  
2.  <span data-ttu-id="42ea7-109">Dans une invite de commandes, accédez au dossier Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="42ea7-109">In a command prompt, change directories to the Enterprise Single Sign-On folder.</span></span>  
  
     <span data-ttu-id="42ea7-110">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="42ea7-110">For example:</span></span>  
  
     <span data-ttu-id="42ea7-111">**C:\Program Files\Common Files\Enterprise Single Sign-On>**</span><span class="sxs-lookup"><span data-stu-id="42ea7-111">**C:\Program Files\Common Files\Enterprise Single Sign-On>**</span></span>  
  
3.  <span data-ttu-id="42ea7-112">Utilisez les commandes du service de l'authentification unique de l'entreprise</span><span class="sxs-lookup"><span data-stu-id="42ea7-112">Use the Enterprise Single Sign-On commands.</span></span> <span data-ttu-id="42ea7-113">Pour obtenir la liste des commandes, utilisez le commutateur -help.</span><span class="sxs-lookup"><span data-stu-id="42ea7-113">For a list of commands, use the -help switch.</span></span>  
  
     <span data-ttu-id="42ea7-114">![](../core/media/siebeladapter-23-sso-commands.gif "SiebelAdapter_23_SSO_Commands")</span><span class="sxs-lookup"><span data-stu-id="42ea7-114">![](../core/media/siebeladapter-23-sso-commands.gif "SiebelAdapter_23_SSO_Commands")</span></span>  
  
4.  <span data-ttu-id="42ea7-115">Pour créer l’application associée à l’aide la \*. XML en tant qu’un début, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="42ea7-115">To create the affiliate application using the \*.XML as a beginning, type in the following command:</span></span>  
  
     <span data-ttu-id="42ea7-116">**ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml**</span><span class="sxs-lookup"><span data-stu-id="42ea7-116">**ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml**</span></span>  
  
     <span data-ttu-id="42ea7-117">où :</span><span class="sxs-lookup"><span data-stu-id="42ea7-117">where:</span></span>  
  
     <span data-ttu-id="42ea7-118">C:\SSOtest est le dossier contenant le XML de votre application.</span><span class="sxs-lookup"><span data-stu-id="42ea7-118">C:\SSOtest is the folder containing your application XML.</span></span>  
  
     <span data-ttu-id="42ea7-119">AffiliateApplication.xml est l’application XML que vous avez créé contenant les informations de connexion.</span><span class="sxs-lookup"><span data-stu-id="42ea7-119">AffiliateApplication.xml is the application XML you created containing the Sign On information.</span></span>  
  
     <span data-ttu-id="42ea7-120">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="42ea7-120">For example:</span></span>  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
         <application name="JDEdwardsApp">  
              <description>JDEdwards SSO Application</description>  
              <contact>someone@microsoft.com</contact>  
              <userGroup>ibi\Domain Users</userGroup>  
              <!—-an existing group on the domain controller - >   
              <appAdminGroup>ibi\YourID</appAdminGroup>  
              <!-- an existing account within the domain group - >   
              <field ordinal="0" label="User ID" masked="no" />  
              <field ordinal="1" label="Password" masked="yes" />  
              <flags groupApp="no" allowTickets="yes" enableApp="yes"/>  
         </application>  
    </SSO>  
    ```  
  
## <a name="creating-single-sign-on-tickets"></a><span data-ttu-id="42ea7-121">Création de tickets d'authentification unique</span><span class="sxs-lookup"><span data-stu-id="42ea7-121">Creating Single Sign-On Tickets</span></span>  
  
#### <a name="to-create-sso-tickets"></a><span data-ttu-id="42ea7-122">Pour créer des tickets SSO</span><span class="sxs-lookup"><span data-stu-id="42ea7-122">To create SSO tickets</span></span>  
  
1.  <span data-ttu-id="42ea7-123">Tapez la commande suivante pour contrôler le comportement de ticket d’authentification unique :</span><span class="sxs-lookup"><span data-stu-id="42ea7-123">Type in the following command to control SSO ticket behavior:</span></span>  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  <span data-ttu-id="42ea7-124">Répondez aux questions :</span><span class="sxs-lookup"><span data-stu-id="42ea7-124">Answer the questions:</span></span>  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
     <span data-ttu-id="42ea7-125">Lorsque vous avez terminé, vous recevez une confirmation :</span><span class="sxs-lookup"><span data-stu-id="42ea7-125">On completion you receive a confirmation:</span></span>  
  
     <span data-ttu-id="42ea7-126">**Utilisation d'un serveur d'authentification unique sur cet ordinateur. L’opération s’est terminée correctement.**</span><span class="sxs-lookup"><span data-stu-id="42ea7-126">**Using SSO server on this computer. The operation completed successfully.**</span></span>  
  
## <a name="enabling-the-affiliate-application-xml"></a><span data-ttu-id="42ea7-127">Activation du fichier XML de l'application associée</span><span class="sxs-lookup"><span data-stu-id="42ea7-127">Enabling the Affiliate Application XML</span></span>  
  
#### <a name="to-enable-affiliate-application-xml"></a><span data-ttu-id="42ea7-128">Pour activer le fichier XML de l'application associée</span><span class="sxs-lookup"><span data-stu-id="42ea7-128">To enable affiliate application XML</span></span>  
  
1.  <span data-ttu-id="42ea7-129">Tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="42ea7-129">Type in the following command:</span></span>  
  
     `ssomanage -enableapp JDEdwardsApp`  
  
2.  <span data-ttu-id="42ea7-130">Tapez la commande suivante pour répertorier les applications et pour vérifier que l’application a été créée :</span><span class="sxs-lookup"><span data-stu-id="42ea7-130">Type in the following command to list the applications and to verify that the application was created:</span></span>  
  
     `ssoclient.exe –listapps`  
  
     <span data-ttu-id="42ea7-131">Les Applications associées utilisables apparaissent dans une liste.</span><span class="sxs-lookup"><span data-stu-id="42ea7-131">The Affiliate Applications available for use appear in a list.</span></span>  
  
     <span data-ttu-id="42ea7-132">**Applications disponibles pour IBI\YourID - JDEdwardsApp**</span><span class="sxs-lookup"><span data-stu-id="42ea7-132">**Applications available for IBI\YourID - JDEdwardsApp**</span></span>  
  
3.  <span data-ttu-id="42ea7-133">Tapez la commande suivante pour définir les informations d'identification de l'application associée :</span><span class="sxs-lookup"><span data-stu-id="42ea7-133">Type in the following command to set the affiliate application credentials:</span></span>  
  
     `ssoclient.exe -setcredentials JDEdwardsApp`  
  
4.  <span data-ttu-id="42ea7-134">Lorsque vous y êtes invité, entrez les nom d'utilisateur et mot de passe.</span><span class="sxs-lookup"><span data-stu-id="42ea7-134">Enter the user name and password at the prompts.</span></span> <span data-ttu-id="42ea7-135">Entrez les informations d'identification de l'application associée JDEdwardsApp.</span><span class="sxs-lookup"><span data-stu-id="42ea7-135">Enter the logon credentials for the JDEdwardsApp affiliate application.</span></span> <span data-ttu-id="42ea7-136">Par exemple, entrez les ID d'utilisateur et mot de passe suivants pour entrer dans le système via le serveur d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="42ea7-136">For example, enter the user identification and the password for that user to enter into the system through the SSO server.</span></span>  
  
    -   <span data-ttu-id="42ea7-137">**ID d’utilisateur :** utilisateur</span><span class="sxs-lookup"><span data-stu-id="42ea7-137">**User ID:** user</span></span>  
  
    -   <span data-ttu-id="42ea7-138">**Mot de passe :** ******</span><span class="sxs-lookup"><span data-stu-id="42ea7-138">**Password:** ******</span></span>  
  
    -   <span data-ttu-id="42ea7-139">**Confirmer ? Mot de passe :** ******</span><span class="sxs-lookup"><span data-stu-id="42ea7-139">**Confirm? Password:** ******</span></span>  
  
5.  <span data-ttu-id="42ea7-140">L'application associée s'affiche dans la liste déroulante de la boîte de dialogue Propriétés du transport de l'adaptateur BizTalk pour JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="42ea7-140">The affiliate application appears in the drop-down list of the BizTalk Adapter for JD Edwards OneWorld Transport Properties dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42ea7-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42ea7-141">See Also</span></span>  
 [<span data-ttu-id="42ea7-142">Sécurité de la carte</span><span class="sxs-lookup"><span data-stu-id="42ea7-142">Security in the adapter</span></span>](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)