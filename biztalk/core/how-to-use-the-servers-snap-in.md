---
title: Comment utiliser le composant logiciel enfichable serveurs | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f520692-9606-41f5-98ed-5a4962bd1f09
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12eb72323a6dcd1132f03febc9b4d9bd75316c84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-servers-snap-in"></a><span data-ttu-id="6953b-102">Utilisation du composant logiciel enfichable de serveurs</span><span class="sxs-lookup"><span data-stu-id="6953b-102">How to Use the Servers Snap-in</span></span>
<span data-ttu-id="6953b-103">Cette version de l'authentification unique de l'entreprise inclut le composant logiciel enfichable de serveurs ENTSSO, lequel vous permet d'afficher, d'analyser et d'effectuer certaines actions sur votre serveur ENTSSO via l'interface Windows.</span><span class="sxs-lookup"><span data-stu-id="6953b-103">This version of Enterprise Single Sign-On (SSO) includes the ENTSSO Servers Snap-In, which allows you to view, monitor, and perform certain actions on your ENTSSO Server through the Windows interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6953b-104">Si votre système est protégé par un pare-feu et si le nom de votre serveur utilise le format FQDN, vous risquez de ne pas pouvoir contacter le serveur.</span><span class="sxs-lookup"><span data-stu-id="6953b-104">If your system has a firewall and your server name uses the FQDN format, you may not be able to contact the server.</span></span> <span data-ttu-id="6953b-105">Vous devez alors spécifier le nom NetBIOS ou l'adresse IP qui lui sont associés.</span><span class="sxs-lookup"><span data-stu-id="6953b-105">Instead, you must specify the NetBIOS name or the associated IP address.</span></span>  
  
### <a name="to-use-the-entsso-servers-snap-in"></a><span data-ttu-id="6953b-106">Pour utiliser le composant logiciel enfichable de serveurs ENTSSO</span><span class="sxs-lookup"><span data-stu-id="6953b-106">To use the ENTSSO Servers Snap-In</span></span>  
  
1.  <span data-ttu-id="6953b-107">Ouvrez l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="6953b-107">Open Enterprise Single Sign-On.</span></span>  
  
2.  <span data-ttu-id="6953b-108">Dans le volet d’étendue, cliquez sur le **serveurs** nœud.</span><span class="sxs-lookup"><span data-stu-id="6953b-108">In the Scope pane, click the **Servers** node.</span></span>  
  
     <span data-ttu-id="6953b-109">Les informations suivantes sont affichées dans le volet Résultats.</span><span class="sxs-lookup"><span data-stu-id="6953b-109">The following information is displayed in the Results pane.</span></span>  
  
    -   <span data-ttu-id="6953b-110">**Nom**: nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="6953b-110">**Name**: Name specified.</span></span>  
  
    -   <span data-ttu-id="6953b-111">**État**: état du service ENTSSO (en ligne, hors connexion, en attente, démarré, arrêté, attente de démarrage, arrêt en attente).</span><span class="sxs-lookup"><span data-stu-id="6953b-111">**Status**: Status of the ENTSSO service (Online, Offline, Pending, Started, Stopped, Start Pending, Stop Pending).</span></span>  
  
    -   <span data-ttu-id="6953b-112">**Date**: obtention des informations de Date.</span><span class="sxs-lookup"><span data-stu-id="6953b-112">**Date**: Date when information was obtained.</span></span>  
  
    -   <span data-ttu-id="6953b-113">**Heure**: obtention des informations de temps.</span><span class="sxs-lookup"><span data-stu-id="6953b-113">**Time**: Time when information was obtained.</span></span>  
  
    -   <span data-ttu-id="6953b-114">**Serveur d’authentification unique**: nom complet du serveur.</span><span class="sxs-lookup"><span data-stu-id="6953b-114">**SSO Server**: Fully qualified name of server.</span></span>  
  
    -   <span data-ttu-id="6953b-115">**Compte de service**: compte de service ENTSSO.</span><span class="sxs-lookup"><span data-stu-id="6953b-115">**Service Account**: ENTSSO service account.</span></span>  
  
    -   <span data-ttu-id="6953b-116">**Base de données SSO**: base de données ENTSSO avec lequel communique ce serveur.</span><span class="sxs-lookup"><span data-stu-id="6953b-116">**SSO Database**: ENTSSO Database with which this server is communicating.</span></span>  
  
    -   <span data-ttu-id="6953b-117">**Serveur de secret principal**: indique si le module du serveur de secret principal est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6953b-117">**Secret Server**: Indicates whether the Secret Server module is running.</span></span>  
  
    -   <span data-ttu-id="6953b-118">**Synchronisation de mot de passe**: indique si la synchronisation de mot de passe est installée.</span><span class="sxs-lookup"><span data-stu-id="6953b-118">**Password Sync**: Indicates whether Password Sync is installed.</span></span>  
  
    -   <span data-ttu-id="6953b-119">**Ordinateur**: nom NETBIOS de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6953b-119">**Computer**: NETBIOS name of computer.</span></span>  
  
    -   <span data-ttu-id="6953b-120">**Événement compte**: nombre d’événements informations/avertissement/erreurs.</span><span class="sxs-lookup"><span data-stu-id="6953b-120">**Event counts**: Info/Warning/Errors event count.</span></span> <span data-ttu-id="6953b-121">Si vous réinitialisez cette valeur, le compteur redémarrera à 0.</span><span class="sxs-lookup"><span data-stu-id="6953b-121">Resetting this will start the counter from 0.</span></span>  
  
    -   <span data-ttu-id="6953b-122">**Version SSO installée**: numéro de Version d’ENTSSO.exe.</span><span class="sxs-lookup"><span data-stu-id="6953b-122">**Version of SSO installed**: Version number of ENTSSO.exe.</span></span> <span data-ttu-id="6953b-123">Indique également s'il s'agit d'une version 32 bits (x86) ou 64 bits (x64).</span><span class="sxs-lookup"><span data-stu-id="6953b-123">Also indicates whether this is 32-bit (x86) or 64-bit (x64).</span></span>  
  
### <a name="to-start-or-stop-the-server-service"></a><span data-ttu-id="6953b-124">Pour démarrer ou arrêter le service du serveur</span><span class="sxs-lookup"><span data-stu-id="6953b-124">To start or stop the server service</span></span>  
  
-   <span data-ttu-id="6953b-125">Dans le serveurs enfichable ENTSSO, cliquez sur le serveur, sur **Démarrer** ou **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="6953b-125">In the ENTSSO Servers Snap-In, right-click the server and click **Start** or **Stop**.</span></span>  
  
### <a name="to-display-information-for-one-server"></a><span data-ttu-id="6953b-126">Pour afficher les informations d'un serveur</span><span class="sxs-lookup"><span data-stu-id="6953b-126">To display information for one server</span></span>  
  
-   <span data-ttu-id="6953b-127">Dans l'arborescence des serveurs, cliquez sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="6953b-127">In the Server tree, click the server.</span></span>  
  
     <span data-ttu-id="6953b-128">Les informations sont affichées dans le volet Résultats.</span><span class="sxs-lookup"><span data-stu-id="6953b-128">The information is displayed in the results pane.</span></span>  
  
### <a name="to-add-a-server"></a><span data-ttu-id="6953b-129">Pour ajouter un serveur</span><span class="sxs-lookup"><span data-stu-id="6953b-129">To add a server</span></span>  
  
-   <span data-ttu-id="6953b-130">Avec le bouton droit dans le volet d’étendue, puis cliquez sur **ajouter un serveur**.</span><span class="sxs-lookup"><span data-stu-id="6953b-130">Right-click in the Scope pane, and then click **Add Server**.</span></span>  
  
     <span data-ttu-id="6953b-131">Le **ajouter un serveur** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="6953b-131">The **Add Server** dialog box appears.</span></span> <span data-ttu-id="6953b-132">Tapez ou recherchez le serveur que vous souhaitez ajouter.</span><span class="sxs-lookup"><span data-stu-id="6953b-132">Type or browse to the server you want to add.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6953b-133">Dans certains environnements de groupe de travail, en cliquant sur le **Parcourir** bouton entraînera fermer cette boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6953b-133">In certain Workgroup environments, clicking the **Browse** button will cause this dialog box to close.</span></span> <span data-ttu-id="6953b-134">Au lieu d’utiliser le **Parcourir** bouton, tapez le nom du serveur dans la zone.</span><span class="sxs-lookup"><span data-stu-id="6953b-134">Instead of using the **Browse** button, simply type the server name in the box.</span></span>  
  
### <a name="to-view-or-change-server-properties"></a><span data-ttu-id="6953b-135">Pour afficher ou modifier des propriétés de serveur</span><span class="sxs-lookup"><span data-stu-id="6953b-135">To view or change server properties</span></span>  
  
-   <span data-ttu-id="6953b-136">Dans l’arborescence du serveur, cliquez sur le serveur, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="6953b-136">In the Server tree, right-click the server, and click **Properties**.</span></span>  
  
     <span data-ttu-id="6953b-137">Le **propriétés du serveur** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="6953b-137">The **Server Properties** dialog box appears.</span></span> <span data-ttu-id="6953b-138">Vous pouvez afficher ou modifier les informations sous les onglets suivants :</span><span class="sxs-lookup"><span data-stu-id="6953b-138">You can view or change information in the following tabs:</span></span>  
  
    -   <span data-ttu-id="6953b-139">**Niveaux d’audit**</span><span class="sxs-lookup"><span data-stu-id="6953b-139">**Audit Levels**</span></span>  
  
    -   <span data-ttu-id="6953b-140">**Base de données SSO**</span><span class="sxs-lookup"><span data-stu-id="6953b-140">**SSO Database**</span></span>  
  
    -   <span data-ttu-id="6953b-141">**Service d’authentification unique**</span><span class="sxs-lookup"><span data-stu-id="6953b-141">**SSO Service**</span></span>  
  
    -   <span data-ttu-id="6953b-142">**Synchronisation de mot de passe**</span><span class="sxs-lookup"><span data-stu-id="6953b-142">**Password Sync**</span></span>  
  
    -   <span data-ttu-id="6953b-143">**Avancé**</span><span class="sxs-lookup"><span data-stu-id="6953b-143">**Advanced**</span></span>