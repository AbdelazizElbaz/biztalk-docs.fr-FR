---
title: "Comment configurer MIIS pour l’agent de gestion ENTSSO | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7820384-ff64-4628-9e35-02b13803928f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 969a52beb02c3d2ba237369c16efec9ee84e2ef1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-miis-for-entsso-ma"></a><span data-ttu-id="0d259-102">Configuration de MIIS pour l'agent de gestion de l'authentification unique de l'entreprise</span><span class="sxs-lookup"><span data-stu-id="0d259-102">How to Configure MIIS for ENTSSO MA</span></span>
<span data-ttu-id="0d259-103">Lorsque vous installez la fonctionnalité Administration de l'authentification unique de l'entreprise (que ce soit la version complète ou la version pour les administrateurs uniquement) sur un ordinateur exécutant MIIS (Microsoft Identity Integration Server), l'agent de gestion ENTSSO est installé automatiquement.</span><span class="sxs-lookup"><span data-stu-id="0d259-103">When you install the Enterprise Single Sign-On (SSO) Administration feature (either the full version or the Admin-only version) on a computer running Microsoft Identity Integration Server (MIIS), the ENTSSO Management Agent is automatically installed.</span></span> <span data-ttu-id="0d259-104">Cela signifie que lorsque vous ouvrez MIIS, quasiment l'intégralité de la configuration a déjà été effectuée.</span><span class="sxs-lookup"><span data-stu-id="0d259-104">This means that when you open MIIS, nearly all of the configuration has already been done.</span></span> <span data-ttu-id="0d259-105">La seule partie manquante concerne les informations de connexion.</span><span class="sxs-lookup"><span data-stu-id="0d259-105">The only part missing is the connection information.</span></span>  
  
 <span data-ttu-id="0d259-106">Avant de commencer cette procédure, assurez-vous de disposer des informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="0d259-106">Before starting this procedure, make sure you have the following information available:</span></span>  
  
-   <span data-ttu-id="0d259-107">Le nom du serveur ENTSSO.</span><span class="sxs-lookup"><span data-stu-id="0d259-107">ENTSSO Server name.</span></span>  
  
-   <span data-ttu-id="0d259-108">L'ID utilisateur et le mot de passe du compte Windows sous lequel l'agent de gestion ENTSSO communique avec le serveur SSO.</span><span class="sxs-lookup"><span data-stu-id="0d259-108">UserId and password of the Windows account under which the ENTSSO Management Agent will communicate with the SSO Server.</span></span>  
  
### <a name="to-configure-the-management-agent-within-miis"></a><span data-ttu-id="0d259-109">Pour configurer l'agent de gestion dans MIIS</span><span class="sxs-lookup"><span data-stu-id="0d259-109">To configure the Management Agent within MIIS</span></span>  
  
1.  <span data-ttu-id="0d259-110">Ouvrez MIIS, puis ouvrez le **Identity Manager**.</span><span class="sxs-lookup"><span data-stu-id="0d259-110">Open MIIS, and open the **Identity Manager**.</span></span>  
  
2.  <span data-ttu-id="0d259-111">Ouvrez le **créer un Agent de gestion** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="0d259-111">Open the **Create Management Agent** dialog box.</span></span>  
  
3.  <span data-ttu-id="0d259-112">Sélectionnez **Enterprise Single Sign-On** dans la liste.</span><span class="sxs-lookup"><span data-stu-id="0d259-112">Select **Enterprise Single Sign-On** in the list.</span></span>  
  
     <span data-ttu-id="0d259-113">Cela démarre le **Assistant Création de l’Agent de gestion**.</span><span class="sxs-lookup"><span data-stu-id="0d259-113">This starts the **Create Management Agent Wizard**.</span></span>  
  
4.  <span data-ttu-id="0d259-114">Sur le **configurer les informations de connexion** page, dans le **se connecter à :** , entrez le nom du serveur SSO.</span><span class="sxs-lookup"><span data-stu-id="0d259-114">On the **Configure Connection Information** page, in the **Connect To:** field, enter the name of the SSO Server.</span></span>  
  
5.  <span data-ttu-id="0d259-115">Entrez le nom de l'agent de gestion ENTSSO.</span><span class="sxs-lookup"><span data-stu-id="0d259-115">Enter the name of the ENTSSO Management Agent.</span></span> <span data-ttu-id="0d259-116">Ce nom doit correspondre à celui spécifié dans le fichier ENTSSO.xml.</span><span class="sxs-lookup"><span data-stu-id="0d259-116">This name must match the name specified in your ENTSSO.xml file.</span></span>  
  
6.  <span data-ttu-id="0d259-117">Dans le **utilisateur** champ, spécifiez le compte de domaine que l’Agent de gestion ENTSSO utilise pour gérer les mappages dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="0d259-117">In the **User** field, specify the domain account that the ENTSSO Management Agent uses to manage mappings in the SSO Database.</span></span>  
  
     <span data-ttu-id="0d259-118">Dans le système SSO, ce compte doit être membre du compte Administrateurs d'applications associées à authentification unique ou du compte Administrateurs de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="0d259-118">This account should be either a member of the SSO Affiliate Administrators or SSO Administrators accounts within the SSO System.</span></span>  
  
7.  <span data-ttu-id="0d259-119">Dans le **mot de passe** , entrez le mot de passe pour cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0d259-119">In the **Password** field, enter the password for that user.</span></span>  
  
8.  <span data-ttu-id="0d259-120">Cliquez sur **suivant**, en acceptant les valeurs par défaut jusqu'à ce que vous atteigniez le **configurer des Extensions** page.</span><span class="sxs-lookup"><span data-stu-id="0d259-120">Click **Next**, accepting the defaults until you reach the **Configure Extensions** page.</span></span>  
  
9. <span data-ttu-id="0d259-121">Près de **les informations de connexion** pour l’extension de mot de passe, cliquez sur **paramètres**.</span><span class="sxs-lookup"><span data-stu-id="0d259-121">Near **Connection information** for password extension, click **Settings**.</span></span>  
  
     <span data-ttu-id="0d259-122">Le **paramètres de connexion** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="0d259-122">The **Connection Settings** dialog box appears.</span></span>  
  
10. <span data-ttu-id="0d259-123">Dans le **se connecter à** , entrez le compte approprié.</span><span class="sxs-lookup"><span data-stu-id="0d259-123">In the **Connect To** box, enter the appropriate account.</span></span> <span data-ttu-id="0d259-124">Ce compte doit être le même que le compte de service pour le service ENTSSO exécuté sur l'ordinateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="0d259-124">This account must be the same as the service account for the ENTSSO service running on the computer specified.</span></span>  
  
11. <span data-ttu-id="0d259-125">Dans le **utilisateur** et **mot de passe** , saisissez le nom d’utilisateur et un mot de passe pour le compte.</span><span class="sxs-lookup"><span data-stu-id="0d259-125">In the **User** and **Password** fields, enter the user name and password for the account.</span></span>  
  
12. <span data-ttu-id="0d259-126">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0d259-126">Click **OK**.</span></span>  
  
13. <span data-ttu-id="0d259-127">Dans le **Agent de gestion MIISCreate**, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="0d259-127">In the **MIISCreate Management Agent**, click **Finish**.</span></span>  
  
14. <span data-ttu-id="0d259-128">Toujours dans le **Identity Manager**, cliquez sur le **outils** menu, puis sur **Options**.</span><span class="sxs-lookup"><span data-stu-id="0d259-128">While still in the **Identity Manager**, click the **Tools** menu, and then click **Options**.</span></span>  
  
     <span data-ttu-id="0d259-129">Le **Options** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="0d259-129">The **Options** dialog box appears.</span></span>  
  
15. <span data-ttu-id="0d259-130">Sélectionnez **activer l’extension de règles du métaverse**.</span><span class="sxs-lookup"><span data-stu-id="0d259-130">Select **Enable metaverse rules extension**.</span></span>  
  
16. <span data-ttu-id="0d259-131">Dans le **le champ de nom d’extension des règles**, entrez **Microsoft.EnterpriseSingleSignOn.ManagementAgent.dll**.</span><span class="sxs-lookup"><span data-stu-id="0d259-131">In the **Rules extension name field**, enter **Microsoft.EnterpriseSingleSignOn.ManagementAgent.dll**.</span></span>  
  
17. <span data-ttu-id="0d259-132">Cliquez sur **OK** puis fermez MIIS.</span><span class="sxs-lookup"><span data-stu-id="0d259-132">Click **OK** and close MIIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d259-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d259-133">See Also</span></span>  
 [<span data-ttu-id="0d259-134">L’utilisation de l’Agent de gestion ENTSSO</span><span class="sxs-lookup"><span data-stu-id="0d259-134">How to Use the ENTSSO Management Agent</span></span>](../core/how-to-use-the-entsso-management-agent.md)