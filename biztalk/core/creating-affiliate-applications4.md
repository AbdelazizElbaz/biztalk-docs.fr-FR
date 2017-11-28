---
title: "Création d’applications associées à des Applications4 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tickets, Single Sign-On
- affiliate applications, setting credentials
- affiliate applications
- Single Sign-On, creating tickets
- SSO tickets
ms.assetid: 790fbe21-8081-4d57-803f-23014c8a3135
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87aa9be716e437e80c0e85bd9e462713e48090ad
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="creating-affiliate-applications"></a><span data-ttu-id="6016b-102">Création d’Applications associées</span><span class="sxs-lookup"><span data-stu-id="6016b-102">Creating Affiliate Applications</span></span>
<span data-ttu-id="6016b-103">Les étapes suivantes décrivent la mise en route des applications associées à l'aide de l'authentification unique (SSO).</span><span class="sxs-lookup"><span data-stu-id="6016b-103">The following steps describe how to get started with affiliate applications using SSO.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6016b-104">Si vous obtenez des erreurs de l’authentification unique, vérifiez que vous avez utilisé un compte de domaine lors de la configuration de BizTalk Server, comme cela affecte les fonctionnalités du service SSO de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="6016b-104">If you get SSO errors, verify that you used a domain account when you configured BizTalk Server, as this affects the function of the Enterprise SSO service.</span></span> <span data-ttu-id="6016b-105">(SSO n'est compatible qu'avec les comptes de domaine).</span><span class="sxs-lookup"><span data-stu-id="6016b-105">SSO only functions under a domain account.</span></span>  
  
### <a name="to-create-an-affiliate-application"></a><span data-ttu-id="6016b-106">Pour créer une application associée</span><span class="sxs-lookup"><span data-stu-id="6016b-106">To create an affiliate application</span></span>  
  
1.  <span data-ttu-id="6016b-107">Dans le panneau de configuration, ouvrez **Services**et vérifiez que le service Enterprise Single Sign-On est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6016b-107">In Control Panel, open **Services**, and verify that the Enterprise Single Sign-On service is running.</span></span>  
  
2.  <span data-ttu-id="6016b-108">Ouvrez une invite de commandes, puis accédez au dossier de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="6016b-108">In a command prompt, change directories to the Enterprise Single Sign On folder.</span></span>  
  
     <span data-ttu-id="6016b-109">Exemple :</span><span class="sxs-lookup"><span data-stu-id="6016b-109">For example:</span></span>  
  
     <span data-ttu-id="6016b-110">**C:\Program Files\Common Files\Enterprise Single Sign-On >**</span><span class="sxs-lookup"><span data-stu-id="6016b-110">**C:\Program Files\Common Files\Enterprise Single Sign-On>**</span></span>  
  
3.  <span data-ttu-id="6016b-111">Utilisez les commandes du service de l'authentification unique de l'entreprise</span><span class="sxs-lookup"><span data-stu-id="6016b-111">Use the Enterprise Single Sign-On commands.</span></span> <span data-ttu-id="6016b-112">Pour obtenir la liste de commandes, utilisez la **-aide** basculer.</span><span class="sxs-lookup"><span data-stu-id="6016b-112">For a list of commands, use the **-help** switch.</span></span>  
  
4.  <span data-ttu-id="6016b-113">Pour créer l'application associée à l'aide d'un fichier .XML, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="6016b-113">To create the affiliate application using *.XML as a beginning, type the following command:</span></span>  
  
     `ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml`  
  
     <span data-ttu-id="6016b-114">où :</span><span class="sxs-lookup"><span data-stu-id="6016b-114">where:</span></span>  
  
    -   <span data-ttu-id="6016b-115">C:\SSOtest est le dossier qui contient le fichier XML de votre application ;</span><span class="sxs-lookup"><span data-stu-id="6016b-115">C:\SSOtest is the folder that contains your application XML.</span></span>  
  
    -   <span data-ttu-id="6016b-116">AffiliateApplication.xml est l’application XML que vous avez créé et qui contient les informations d’authentification.</span><span class="sxs-lookup"><span data-stu-id="6016b-116">AffiliateApplication.xml is the application XML you created that contains the Sign-On information.</span></span>  
  
     <span data-ttu-id="6016b-117">Exemple :</span><span class="sxs-lookup"><span data-stu-id="6016b-117">For example:</span></span>  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
        <application name="JDEdwardsApp">  
            <description>JDEdwards SSO Application</description>  
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
  
### <a name="to-create-single-sign-on-tickets"></a><span data-ttu-id="6016b-118">Pour créer des tickets d'authentification unique</span><span class="sxs-lookup"><span data-stu-id="6016b-118">To create Single Sign-On tickets</span></span>  
  
1.  <span data-ttu-id="6016b-119">Tapez la commande suivante pour contrôler le comportement des tickets d'authentification unique :</span><span class="sxs-lookup"><span data-stu-id="6016b-119">Type the following command to control SSO ticket behavior:</span></span>  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  <span data-ttu-id="6016b-120">Répondez aux questions comme suit :</span><span class="sxs-lookup"><span data-stu-id="6016b-120">Answer the following questions as shown:</span></span>  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
     <span data-ttu-id="6016b-121">Lorsque vous avez terminé, vous recevez la confirmation suivante :</span><span class="sxs-lookup"><span data-stu-id="6016b-121">On completion, you receive the following confirmation:</span></span>  
  
     <span data-ttu-id="6016b-122">**Utilisation d'un serveur d'authentification unique sur cet ordinateur. L’opération s’est terminée correctement.**</span><span class="sxs-lookup"><span data-stu-id="6016b-122">**Using SSO server on this computer. The operation completed successfully.**</span></span>  
  
### <a name="to-enable-affiliate-application-xml"></a><span data-ttu-id="6016b-123">Pour activer le fichier XML de l'application associée</span><span class="sxs-lookup"><span data-stu-id="6016b-123">To enable affiliate application XML</span></span>  
  
1.  <span data-ttu-id="6016b-124">Tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="6016b-124">Type the following command:</span></span>  
  
     `ssomanage -enableapp JDEdwardsApp`  
  
2.  <span data-ttu-id="6016b-125">Tapez la commande suivante pour afficher la liste des applications et vérifier que l'application a été créée :</span><span class="sxs-lookup"><span data-stu-id="6016b-125">Type the following command to list the applications and to verify that the application was created:</span></span>  
  
     `ssoclient.exe –listapps`  
  
     <span data-ttu-id="6016b-126">Les applications associées qui sont disponibles pour utilisent l’affichage dans une liste :</span><span class="sxs-lookup"><span data-stu-id="6016b-126">The affiliate applications that are available for use display in a list:</span></span>  
  
     <span data-ttu-id="6016b-127">**Applications disponibles pour IBI\YourID - JDEdwardsApp**</span><span class="sxs-lookup"><span data-stu-id="6016b-127">**Applications available for IBI\YourID - JDEdwardsApp**</span></span>  
  
3.  <span data-ttu-id="6016b-128">Tapez la commande suivante pour définir des informations d’identification de l’application de la filiale :</span><span class="sxs-lookup"><span data-stu-id="6016b-128">Type the following command to set the affiliate application credentials:</span></span>  
  
     `ssoclient.exe -setcredentials JDEdwardsApp`  
  
4.  <span data-ttu-id="6016b-129">Lorsque vous y êtes invité, entrez les nom d'utilisateur et mot de passe.</span><span class="sxs-lookup"><span data-stu-id="6016b-129">Enter the user name and password at the prompts.</span></span> <span data-ttu-id="6016b-130">Entrez les informations d'identification de l'application associée JDEdwardsApp.</span><span class="sxs-lookup"><span data-stu-id="6016b-130">Enter the logon credentials for the JDEdwardsApp affiliate application.</span></span>  
  
     <span data-ttu-id="6016b-131">Par exemple, entrez les ID d'utilisateur et mot de passe suivants pour entrer dans le système via le serveur d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="6016b-131">For example, enter the user identification and the password for that user to enter into the system through the SSO server.</span></span>  
  
    -   <span data-ttu-id="6016b-132">ID d’utilisateur : **utilisateur**</span><span class="sxs-lookup"><span data-stu-id="6016b-132">User ID: **user**</span></span>  
  
    -   <span data-ttu-id="6016b-133">Mot de passe :`******`</span><span class="sxs-lookup"><span data-stu-id="6016b-133">Password: `******`</span></span>  
  
    -   <span data-ttu-id="6016b-134">Confirmer ?</span><span class="sxs-lookup"><span data-stu-id="6016b-134">Confirm?</span></span> <span data-ttu-id="6016b-135">Mot de passe :`******`</span><span class="sxs-lookup"><span data-stu-id="6016b-135">Password: `******`</span></span>  
  
     <span data-ttu-id="6016b-136">L’application associée apparaît dans l’adaptateur BizTalk pour JD Edwards EnterpriseOne **propriétés du Transport** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6016b-136">The affiliate application appears in the BizTalk Adapter for JD Edwards EnterpriseOne **Transport Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6016b-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6016b-137">See Also</span></span>  
 [<span data-ttu-id="6016b-138">Sécurité de l’adaptateur BizTalk pour JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="6016b-138">Security in BizTalk Adapter for JD Edwards EnterpriseOne</span></span>](../core/security-in-biztalk-adapter-for-jd-edwards-enterpriseone.md)