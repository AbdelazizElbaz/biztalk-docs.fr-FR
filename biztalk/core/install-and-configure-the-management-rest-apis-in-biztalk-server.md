---
title: Installer et configurer la gestion des API REST | Documents Microsoft
description: "Interroger les artefacts dans votre environnement BizTalk à l’aide des données de gestion des API REST avec Feature Pack dans BizTalk Server"
ms.custom: fp1
ms.date: 11/06/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 39442756-5886-4ddd-b700-3800a237de4a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e05b122047d7e303ed4e187fec19725cce9ae398
ms.sourcegitcommit: 30189176c44873e3de42cc5f2b8951da51ffd251
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="install-and-configure-the-management-rest-apis-in-biztalk-server"></a><span data-ttu-id="d6939-103">Installer et configurer l’API REST de gestion dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d6939-103">Install and configure the management REST APIs in BizTalk Server</span></span>

## <a name="what-are-management-data-apis"></a><span data-ttu-id="d6939-104">Quelles sont les données de gestion des API</span><span class="sxs-lookup"><span data-stu-id="d6939-104">What are management data APIs</span></span>
<span data-ttu-id="d6939-105">API de données de gestion est des points de terminaison qui vous permettent de mettre à jour à distance, ajouter et interroger l’état des différents artefacts dans votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnement.</span><span class="sxs-lookup"><span data-stu-id="d6939-105">Management data APIs are endpoints that let you remotely update, add, and query the status of different artifacts in your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span> <span data-ttu-id="d6939-106">Les points de terminaison sont ajoutés à l’aide de REST et être accompagnée d’une définition swagger.</span><span class="sxs-lookup"><span data-stu-id="d6939-106">The endpoints are added using REST, and come with a swagger definition.</span></span> 

<span data-ttu-id="d6939-107">**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , il existe un script Windows PowerShell qui installe ces API REST et leurs définitions swagger.</span><span class="sxs-lookup"><span data-stu-id="d6939-107">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, there's a Windows PowerShell script that installs these REST APIs, and their swagger definitions.</span></span> <span data-ttu-id="d6939-108">Ces API effectuer des appels REST pour gérer à distance des ports, orchestrations, partenaires, accords, pipelines et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="d6939-108">These APIs make REST calls to remotely manage ports, orchestrations, partners, agreements, pipelines, and more.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="d6939-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="d6939-109">Prerequisites</span></span>
* <span data-ttu-id="d6939-110">Installer [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) sur votre[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6939-110">Install [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>

* <span data-ttu-id="d6939-111">Installer IIS sur le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d6939-111">Install IIS on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="d6939-112">Dans la plupart des [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnements, IIS est déjà installé.</span><span class="sxs-lookup"><span data-stu-id="d6939-112">In most [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environments, IIS is already installed.</span></span> <span data-ttu-id="d6939-113">Consultez [matérielle et logicielle requise pour BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).</span><span class="sxs-lookup"><span data-stu-id="d6939-113">See [Hardware and Software Requirements for BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).</span></span> <span data-ttu-id="d6939-114">Vérifier IIS est installé sur le serveur BizTalk en ouvrant **Gestionnaire des Services Internet**.</span><span class="sxs-lookup"><span data-stu-id="d6939-114">Confirm IIS is installed on the BizTalk Server by opening **Internet Information Services Manager**.</span></span> 

## <a name="step-1-install-the-rest-apis"></a><span data-ttu-id="d6939-115">Étape 1 : Installer l’API REST</span><span class="sxs-lookup"><span data-stu-id="d6939-115">Step 1: Install the REST APIs</span></span>

1. <span data-ttu-id="d6939-116">Exécutez Windows PowerShell en tant qu’administrateur (**Démarrer** menu, tapez **PowerShell**avec le bouton droit et cliquez sur Sélectionner **exécuter en tant qu’administrateur**).</span><span class="sxs-lookup"><span data-stu-id="d6939-116">Run Windows PowerShell as Administrator (**Start** menu, type **PowerShell**, right click, and select **Run as administrator**).</span></span> 
2. <span data-ttu-id="d6939-117">Accédez au dossier d’installation de BizTalk (par exemple, tapez : `cd 'C:\Program Files (x86)\Microsoft BizTalk Server 2016\'`).</span><span class="sxs-lookup"><span data-stu-id="d6939-117">Go to the BizTalk installation folder (for example, type: `cd 'C:\Program Files (x86)\Microsoft BizTalk Server 2016\'`).</span></span>
3. <span data-ttu-id="d6939-118">Dans le texte suivant, remplacez `Default Web Site`, `mgmtServiceAppPool`, `domain/user`, `password`, et `domain\group` avec vos valeurs :</span><span class="sxs-lookup"><span data-stu-id="d6939-118">In the following text, replace `Default Web Site`, `mgmtServiceAppPool`, `domain/user`, `password`, and `domain\group` with your values:</span></span>

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service management -WebSiteName '<Default Web Site>' -ApplicationPool <mgmtServiceAppPool> -ApplicationPoolUser <domain>\<user> -ApplicationPoolUserPassword <password> -AuthorizationRoles '<domain>\<group>, <domain>\<group>'
    ```

    <span data-ttu-id="d6939-119">Dans l’exemple suivant, nous utilisons le `Default Web Site`, créer un pool d’applications nommé `RESTAppPool`, exécuter le pool d’applications en tant que le `bootcampbts2016\btsservice` de compte, utilisez `BIZTALK-serviceacct` comme mot de passe utilisateur, puis donnez aux autorisations du groupe les administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d6939-119">In the following example, we use the `Default Web Site`, create an application pool named `RESTAppPool`, run the appPool as the `bootcampbts2016\btsservice` account, use `BIZTALK-serviceacct` as the user account password, and give the BizTalk Server Administrators group permissions.</span></span> <span data-ttu-id="d6939-120">Veillez à entrer le texte suivant, y compris le seul devis environnantes valeurs avec des espaces :</span><span class="sxs-lookup"><span data-stu-id="d6939-120">Be sure to enter the following, including the single quotes surrounding values with spaces:</span></span> 

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service management -WebSiteName 'Default Web Site' -ApplicationPool RESTAppPool -ApplicationPoolUser bootcampbts2016\btsservice -ApplicationPoolUserPassword  BIZTALK-serviceacct -AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'
    ```

    <span data-ttu-id="d6939-121">Lorsque vous avez terminé, le **BizTalkManagementService** application est créée dans IIS :</span><span class="sxs-lookup"><span data-stu-id="d6939-121">When complete, the **BizTalkManagementService** application is created within IIS:</span></span>  
    <span data-ttu-id="d6939-122">![Application de BizTalkManagementService](../core/media/biztalkmanagementservice-apppool.png)</span><span class="sxs-lookup"><span data-stu-id="d6939-122">![BizTalkManagementService application](../core/media/biztalkmanagementservice-apppool.png)</span></span>

4. <span data-ttu-id="d6939-123">Pour vérifier qu’il fonctionne, accédez à `http://localhost/BizTalkManagementService/swagger`.</span><span class="sxs-lookup"><span data-stu-id="d6939-123">To confirm it’s working, browse to `http://localhost/BizTalkManagementService/swagger`.</span></span> <span data-ttu-id="d6939-124">Si vous êtes invité à la connexion, connectez-vous avec un compte qui est membre de la domaine\groupe que vous avez entré à l’étape précédente (`-AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'`).</span><span class="sxs-lookup"><span data-stu-id="d6939-124">If you are prompted to sign-in, sign in with an account that is member of the domain\group you entered in the previous step (`-AuthorizationRoles 'BOOTCAMPBTS2016\BizTalk Server Administrators'`).</span></span> 

> [!WARNING]
> <span data-ttu-id="d6939-125">L’application BizTalkManagementService dans IIS utilise un fichier web.config.</span><span class="sxs-lookup"><span data-stu-id="d6939-125">The BizTalkManagementService application in IIS uses a web.config file.</span></span> <span data-ttu-id="d6939-126">Éléments dans le fichier web.config **respectent la casse**.</span><span class="sxs-lookup"><span data-stu-id="d6939-126">Elements within web.config **are case sensitive**.</span></span> <span data-ttu-id="d6939-127">Par conséquent, lorsque vous exécutez le script Windows PowerShell, veillez à entrer la casse correcte pour `-AuthorizationRoles` valeur.</span><span class="sxs-lookup"><span data-stu-id="d6939-127">So when you execute the Windows PowerShell script, be sure to enter the correct case for `-AuthorizationRoles` value.</span></span> <span data-ttu-id="d6939-128">Si vous ne savez pas le cas, Voici un moyen simple de déterminer :</span><span class="sxs-lookup"><span data-stu-id="d6939-128">If you’re not sure of the case, here’s an easy way to find out:</span></span> 
> 
> 1. <span data-ttu-id="d6939-129">Ouvrez **gestion de l’ordinateur**, développez **utilisateurs et groupes locaux**.</span><span class="sxs-lookup"><span data-stu-id="d6939-129">Open **Computer Management**, and expand **Local Users and Groups**.</span></span>
> 2. <span data-ttu-id="d6939-130">Sélectionnez **groupes**et faites défiler jusqu'à la **SQLServer...**</span><span class="sxs-lookup"><span data-stu-id="d6939-130">Select **Groups**, and scroll down to the **SQLServer…**</span></span> <span data-ttu-id="d6939-131">groupes.</span><span class="sxs-lookup"><span data-stu-id="d6939-131">groups.</span></span> 
> 3. <span data-ttu-id="d6939-132">Dans l’exemple suivant, notez **BOOTCAMPBTS2016** est en majuscules.</span><span class="sxs-lookup"><span data-stu-id="d6939-132">In the following example, notice **BOOTCAMPBTS2016** is in all caps.</span></span> <span data-ttu-id="d6939-133">Si vous voyez tout en majuscules, puis entrez le nom d’ordinateur dans tout en majuscules.</span><span class="sxs-lookup"><span data-stu-id="d6939-133">If you see all caps, then enter the computer name in all caps.</span></span> 
> 
> ![Nom de l’ordinateur est en majuscules](../core/media/groups-case.png)

<span data-ttu-id="d6939-135">Maintenant que les API REST sont exposées via IIS, ils peuvent accessibles et exécutées par les autres applications.</span><span class="sxs-lookup"><span data-stu-id="d6939-135">Now that the REST APIs are exposed through IIS, they can be accessed and executed by other applications.</span></span> 

<span data-ttu-id="d6939-136">Vous pouvez modifier qui a accès à la mise à jour manuellement la **web.config** fichier, qui se trouve dans le dossier racine de l’application de gestion.</span><span class="sxs-lookup"><span data-stu-id="d6939-136">You can change who has access by manually updating the **web.config** file, which is in the root folder of the management application.</span></span> <span data-ttu-id="d6939-137">Par exemple, utilisez le code suivant à autoriser tout le monde l’accès à la swagger de sortie :</span><span class="sxs-lookup"><span data-stu-id="d6939-137">For example, use the following to allow anyone access to the swagger output:</span></span> 

```
<authorization>
   <allow users="*" />
</authorization>
```

## <a name="step-2-test-the-apis"></a><span data-ttu-id="d6939-138">Étape 2 : Tester les API</span><span class="sxs-lookup"><span data-stu-id="d6939-138">Step 2: Test the APIs</span></span>

1. <span data-ttu-id="d6939-139">Sur le serveur BizTalk Server, accédez à `http://localhost/BizTalkManagementService/swagger`.</span><span class="sxs-lookup"><span data-stu-id="d6939-139">On the BizTalk Server, browse to `http://localhost/BizTalkManagementService/swagger`.</span></span>

2. <span data-ttu-id="d6939-140">Faites défiler vers **hôtes**, puis sélectionnez **afficher/masquer**.</span><span class="sxs-lookup"><span data-stu-id="d6939-140">Scroll to **Hosts**, and select **Show/Hide**.</span></span> <span data-ttu-id="d6939-141">Il existe une commande GET ; Cliquez sur cette ligne :</span><span class="sxs-lookup"><span data-stu-id="d6939-141">There is a GET command; click this row:</span></span>  
<span data-ttu-id="d6939-142">![OBTENIR tous les ordinateurs hôtes](../core/media/managment-rest-apis-hosts-get.png)</span><span class="sxs-lookup"><span data-stu-id="d6939-142">![GET all hosts](../core/media/managment-rest-apis-hosts-get.png)</span></span>

3. <span data-ttu-id="d6939-143">Il affiche les détails.</span><span class="sxs-lookup"><span data-stu-id="d6939-143">It shows the details.</span></span> <span data-ttu-id="d6939-144">Sélectionnez **essayez-le**:</span><span class="sxs-lookup"><span data-stu-id="d6939-144">Select **Try it out**:</span></span>  
<span data-ttu-id="d6939-145">![À votre tour d’essayer](../core/media/managment-rest-apis-hosts-tryitout.png)</span><span class="sxs-lookup"><span data-stu-id="d6939-145">![Try it out](../core/media/managment-rest-apis-hosts-tryitout.png)</span></span>

4. <span data-ttu-id="d6939-146">Le corps de réponse retourne tous les hôtes :</span><span class="sxs-lookup"><span data-stu-id="d6939-146">The Response Body returns all the hosts:</span></span>  
![Réponses](../core/media/managment-rest-apis-hosts-response.png)

> [!NOTE]
> <span data-ttu-id="d6939-148">Si vous y accédez `http://localhost/BizTalkManagementService`, vous devez obtenir une erreur 500.</span><span class="sxs-lookup"><span data-stu-id="d6939-148">If you browse to `http://localhost/BizTalkManagementService`, you should get a 500 error.</span></span> <span data-ttu-id="d6939-149">C’est une bonne chose.</span><span class="sxs-lookup"><span data-stu-id="d6939-149">That’s a good thing.</span></span> <span data-ttu-id="d6939-150">Il suffit d’ajouter `/swagger` à la fin de l’URL et vous verrez les API REST disponible.</span><span class="sxs-lookup"><span data-stu-id="d6939-150">Just add `/swagger` to the end of URL, and you’ll see the available REST APIs.</span></span> 


## <a name="see-also"></a><span data-ttu-id="d6939-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6939-151">See also</span></span>
 [<span data-ttu-id="d6939-152">Configurer le Pack de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="d6939-152">Configure the Feature Pack</span></span>](../core/configure-the-feature-pack.md)