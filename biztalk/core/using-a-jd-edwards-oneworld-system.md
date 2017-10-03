---
title: "À l’aide d’un système JD Edwards OneWorld | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5346aa04-ebd7-4545-9062-b349fd73b7f1
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 835432e50bce3f347e6f769fb8182ab35fc4f949
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-a-jd-edwards-oneworld-system"></a><span data-ttu-id="19fe8-102">Utilisation d'un système JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="19fe8-102">Using a JD Edwards OneWorld System</span></span>
<span data-ttu-id="19fe8-103">Le système JD Edwards OneWorld est accessible à partir d'un système [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'aide de l'adaptateur JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="19fe8-103">The JD Edwards OneWorld system is accessible from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system by using the JD Edwards OneWorld adapter.</span></span> <span data-ttu-id="19fe8-104">Ce dernier fait partie des 8 adaptateurs sectoriels fournis par Microsoft à des fins d'utilisation avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="19fe8-104">This adapter is one of a group of eight line-of-business (LOB) adapters shipped by Microsoft for use with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="19fe8-105">L'atelier JD Edwards OneWorld est divisé en deux parties.</span><span class="sxs-lookup"><span data-stu-id="19fe8-105">The JD Edwards OneWorld lab work is divided into two parts.</span></span> <span data-ttu-id="19fe8-106">Le premier atelier (Atelier 1) vous permet d'utiliser le système JD Edwards OneWorld sans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou produit Microsoft.</span><span class="sxs-lookup"><span data-stu-id="19fe8-106">This first lab (Lab 1) allows you to use the JD Edwards OneWorld system without needing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or any Microsoft products.</span></span> <span data-ttu-id="19fe8-107">Vous allez utiliser l'outil client JD Edwards OneWorld pour vous connecter à une base de données JD Edwards OneWorld et localiser un enregistrement spécifique sur la base de l'adresse.</span><span class="sxs-lookup"><span data-stu-id="19fe8-107">You will use the JD Edwards OneWorld Client tool to connect to a JD Edwards OneWorld database and locate a specific record based upon address.</span></span>  
  
 <span data-ttu-id="19fe8-108">Dans le cadre du deuxième atelier (Atelier 2), vous allez créer un projet et une orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="19fe8-108">In the second lab (Lab 2), you will create a BizTalk project and orchestration.</span></span> <span data-ttu-id="19fe8-109">Une fois l'application créée, vous allez la déployer et l'utiliser pour vous connecter au système JD Edwards OneWorld à l'aide de l'adaptateur associé.</span><span class="sxs-lookup"><span data-stu-id="19fe8-109">After you create the application, you will deploy it and use it to connect to a JD Edwards OneWorld system by using the JD Edwards OneWorld adapter.</span></span> <span data-ttu-id="19fe8-110">Celui-ci vous permettra d'accéder aux données via l'application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="19fe8-110">The goal is to access data through the BizTalk application by using the adapter.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="19fe8-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="19fe8-111">Prerequisites</span></span>  
 <span data-ttu-id="19fe8-112">Pour exécuter les procédures de cet atelier, vous devez installer le logiciel client JD Edwards OneWorld ainsi que sa dernière mise à jour.</span><span class="sxs-lookup"><span data-stu-id="19fe8-112">To perform the procedures for this lab, you need to install the JD Edwards OneWorld client software and its latest update.</span></span> <span data-ttu-id="19fe8-113">Pour utiliser les outils du logiciel client, vous avez besoin d'une base de données JD Edwards OneWorld, d'une connectivité réseau à celle-ci et d'un compte utilisateur sur ce système.</span><span class="sxs-lookup"><span data-stu-id="19fe8-113">To use any of the client software tools you will need a JD Edwards OneWorld database, network connectivity to that database, and a user account on that system.</span></span> <span data-ttu-id="19fe8-114">Vous n'avez pas besoin de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour réaliser cet atelier.</span><span class="sxs-lookup"><span data-stu-id="19fe8-114">You do not need [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to complete this lab.</span></span>  
  
## <a name="lab-1---using-a-jd-edwards-oneworld-system"></a><span data-ttu-id="19fe8-115">Atelier 1 : utilisation d'un système JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="19fe8-115">Lab 1 - Using a JD Edwards OneWorld System</span></span>  
 <span data-ttu-id="19fe8-116">Au cours de cet atelier, vous allez utiliser le système JD Edwards OneWorld uniquement. Vous n'aurez besoin d'aucun composant de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="19fe8-116">In this lab, you will use the JD Edwards OneWorld system without using any components of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="19fe8-117">Vous allez tester la connectivité à JD Edwards OneWorld pour vous assurer que l'atelier 2 fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="19fe8-117">The goals are to test your connectivity to JD Edwards OneWorld and to ensure that the second lab will work correctly.</span></span> <span data-ttu-id="19fe8-118">Vous allez utiliser l'outil SQL Plus pour JD Edwards OneWorld afin de créer et manipuler une table de données dans une base de données JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="19fe8-118">You will use the JD Edwards OneWorld SQL Plus tool to create and manipulate a data table in a JD Edwards OneWorld database.</span></span>  
  
## <a name="procedures-for-lab-1---using-a-jd-edwards-oneworld-system"></a><span data-ttu-id="19fe8-119">Atelier 1 : utilisation d’un système JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="19fe8-119">Procedures for Lab 1 - Using a JD Edwards OneWorld System</span></span>  
  
#### <a name="to-log-on-to-jd-edwards-oneworld-by-using-a-browser"></a><span data-ttu-id="19fe8-120">Pour se connecter à JD Edwards OneWorld à l'aide d'un navigateur</span><span class="sxs-lookup"><span data-stu-id="19fe8-120">To log on to JD Edwards OneWorld by using a browser</span></span>  
  
-   <span data-ttu-id="19fe8-121">Connectez-vous au système JD Edwards OneWorld en cliquant sur l'icône JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="19fe8-121">Log on to the JD Edwards OneWorld system by clicking the JD Edwards OneWorld icon.</span></span> <span data-ttu-id="19fe8-122">Entrez votre **ID utilisateur**, **mot de passe**, et **environnement**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="19fe8-122">Enter your **User ID**, **Password**, and **Environment**, and then click **OK**.</span></span>  
  
     ![](../core/media/f04db2ef-d587-4357-b9e8-c96319886e97.gif "f04db2ef-d587-4357-b9e8-c96319886e97")  
  
#### <a name="to-locate-and-view-jd-edwards-oneworld-data"></a><span data-ttu-id="19fe8-123">Pour rechercher et afficher des données JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="19fe8-123">To locate and view JD Edwards OneWorld data</span></span>  
  
1.  <span data-ttu-id="19fe8-124">Une fois connecté à la **Explorateur JD Edwards OneWorld**.</span><span class="sxs-lookup"><span data-stu-id="19fe8-124">A successful logon places you at the **JD Edwards OneWorld Explorer**.</span></span>  
  
     ![](../core/media/14e8c206-7e38-48f8-9108-e32a7ac9a740.gif "14e8c206-7e38-48f8-9108-e32a7ac9a740")  
  
2.  <span data-ttu-id="19fe8-125">Développez **répertoire principal**, puis **Foundation Systems**, puis **carnet d’adresses**, puis **traitement tous les jours**.</span><span class="sxs-lookup"><span data-stu-id="19fe8-125">Expand **Master Directory**, then **Foundation Systems**, then **Address Book**, and then **Daily Processing**.</span></span>  
  
     ![](../core/media/1f742221-00e5-4697-95ff-64aa63ed567a.gif "1f742221-00e5-4697-95ff-64aa63ed567a")  
  
3.  <span data-ttu-id="19fe8-126">Dans la fenêtre de droite, double-cliquez sur **Address Book Revisions**.</span><span class="sxs-lookup"><span data-stu-id="19fe8-126">In the right-hand window, double-click **Address Book Revisions**.</span></span>  
  
     ![](../core/media/a6d4e871-9c9c-4bc0-9c4f-4bdfd7cc5031.gif "a6d4e871-9c9c-4bc0-9c4f-4bdfd7cc5031")  
  
4.  <span data-ttu-id="19fe8-127">Pour **Alpha Name**, entrez `Ga`, sélectionnez le **affichage adresse** case à cocher, puis cliquez sur **trouver** dans la barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="19fe8-127">For **Alpha Name**, enter `Ga`, select the **Display Address** check box, and then click **Find** on the toolbar.</span></span>  
  
     ![](../core/media/2f58413f-41a9-4ed9-ba5c-1d6d59eafb01.gif "2f58413f-41a9-4ed9-ba5c-1d6d59eafb01")  
  
     <span data-ttu-id="19fe8-128">Dans le **Address Book Revisions - [Work With Addresses]** boîte de dialogue, deux enregistrements sont affichés à la suite de la recherche.</span><span class="sxs-lookup"><span data-stu-id="19fe8-128">In the **Address Book Revisions - [Work With Addresses]** dialog box, two records are displayed as a result of the search.</span></span>  
  
     ![](../core/media/9284df4e-ca9b-48ab-b2bf-a90d765d4a05.gif "9284df4e-ca9b-48ab-b2bf-a90d765d4a05")  
  
     <span data-ttu-id="19fe8-129">Une autre méthode de localisation des données consiste à effacer le **Alpha Name** , cliquez sur dans la zone de texte ci-dessus le **numéro d’adresse** colonne, puis entrez `500`.</span><span class="sxs-lookup"><span data-stu-id="19fe8-129">An alternative method of locating data is to clear the **Alpha Name** field, click in the text box above the **Address Number** column, and enter `500`.</span></span> <span data-ttu-id="19fe8-130">Cliquez sur **trouver** dans la barre d’outils pour afficher les résultats de recherche.</span><span class="sxs-lookup"><span data-stu-id="19fe8-130">Click **Find** on the toolbar to display the search results.</span></span>  
  
     ![](../core/media/a88bd867-9a16-416a-a43e-cdfcc65fc670.gif "a88bd867-9a16-416a-a43e-cdfcc65fc670")  
  
     <span data-ttu-id="19fe8-131">Dans l’atelier 2, il y a des instructions pour l’utilisation de l’adaptateur JD Edwards OneWorld pour extraire les informations d’un **numéro d’adresse** de `500`.</span><span class="sxs-lookup"><span data-stu-id="19fe8-131">In Lab 2, there will be instructions for using the JD Edwards OneWorld adapter to retrieve the information for an **Address Number** of `500`.</span></span>  
  
5.  <span data-ttu-id="19fe8-132">Sur le **fichier** menu, cliquez sur **quitter** pour quitter la session Client JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="19fe8-132">On the **File** menu, click **Exit** to exit the JE Edwards OneWorld Client session.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="19fe8-133">Résumé</span><span class="sxs-lookup"><span data-stu-id="19fe8-133">Summary</span></span>  
 <span data-ttu-id="19fe8-134">Dans cet atelier, vous avez utilisé l'outil client JD Edwards OneWorld pour vous connecter au système JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="19fe8-134">In this lab, you used the JD Edwards OneWorld Client tool to log on to the JD Edwards OneWorld system.</span></span> <span data-ttu-id="19fe8-135">Après avoir établi la connexion, vous avez recherché des données spécifiques et vous avez affiché les enregistrements de données renvoyés.</span><span class="sxs-lookup"><span data-stu-id="19fe8-135">After you were connected, you searched for specific data and viewed the data records returned.</span></span>