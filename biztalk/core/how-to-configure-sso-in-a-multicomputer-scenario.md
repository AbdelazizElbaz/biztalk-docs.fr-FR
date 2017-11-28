---
title: "Comment configurer l’authentification unique dans un scénario multiserveur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, SSO
- SSO database, clustering
- clustering, Master Secret server
- SSO, configuring
- configuring, Master Secret server
- Master Secret server, clustering
- clustering, SSO database
- Master Secret server, configuring
- SSO, multiple computers
ms.assetid: 4511a03d-96f2-45f0-9891-e8b3e253499c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45bfa58c1fc11a76109f56938b8e1b43790935f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-sso-in-a-multicomputer-scenario"></a><span data-ttu-id="a4f7d-102">Comment configurer l’authentification unique dans un scénario multiserveur</span><span class="sxs-lookup"><span data-stu-id="a4f7d-102">How to Configure SSO in a Multicomputer Scenario</span></span>
<span data-ttu-id="a4f7d-103">Cette section contient des instructions pour la configuration de l'authentification unique (SSO) de l'entreprise dans un scénario incluant trois ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="a4f7d-103">This section contains instructions for configuring Enterprise Single Sign-On (SSO) in a three-computer scenario.</span></span>  
  
 <span data-ttu-id="a4f7d-104">Dans le scénario suivant, l'ordinateur A est le serveur de secret principal, l'ordinateur B est le serveur d'authentification unique et l'ordinateur C héberge la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="a4f7d-104">In the following scenario, computer A is the master secret server, computer B is the Single Sign-On server, and computer C holds the SSO database.</span></span> <span data-ttu-id="a4f7d-105">L'ordinateur B peut agir comme serveur d'exécution, serveur d'administration (les sous-services d'administration de l'authentification unique utilisent ce serveur pour gérer la base de données SSO) ou serveur de mappage (les sous-services d'administration et de client de l'authentification unique utilisent ce serveur pour gérer les mappages).</span><span class="sxs-lookup"><span data-stu-id="a4f7d-105">Computer B can act as a runtime server, as an administration server (administration sub services of SSO use this server for managing the SSO database), or as a mapping server (administration and client sub services of SSO use this server to manage mappings).</span></span>  
  
 <span data-ttu-id="a4f7d-106">Si vous souhaitez ajouter d'autres serveurs d'authentification unique à votre environnement, suivez les étapes de configuration de l'ordinateur B. Les nouveaux serveurs pointeront vers la base de données SSO existante et ne peuvent correspondre au serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="a4f7d-106">If you want to add more SSO servers to your environment, follow the steps for configuring computer B. Any new SSO servers will point to the existing SSO database, and cannot be the master secret server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4f7d-107">Il est recommandé de configurer le serveur de secret principal sur un ordinateur distinct du serveur d'authentification unique et de celui hébergeant la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="a4f7d-107">It is recommended that you configure the master secret server on a different computer from the Single Sign-On server and the SSO database.</span></span>  
  
### <a name="to-configure-the-master-secret-server-and-create-the-sso-database-on-computer-a"></a><span data-ttu-id="a4f7d-108">Pour configurer le serveur de secret principal et créer la base de données SSO sur l'ordinateur A</span><span class="sxs-lookup"><span data-stu-id="a4f7d-108">To configure the master secret server and create the SSO database on Computer A</span></span>  
  
1.  <span data-ttu-id="a4f7d-109">Effectuez une installation personnalisée de BizTalk Server et installez uniquement le composant Serveur de secret principal du système d'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="a4f7d-109">Perform a custom installation of BizTalk Server, and install only the Enterprise Single Sign-On Master Secret Server component.</span></span>  
  
2.  <span data-ttu-id="a4f7d-110">Exécutez l'Assistant Configuration pour configurer l'authentification unique sur le serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="a4f7d-110">Run the Configuration Wizard to configure SSO on the master secret server.</span></span> <span data-ttu-id="a4f7d-111">Sur le **Questions de Configuration** page, sélectionnez l’option à **créer un nouveau système SSO**.</span><span class="sxs-lookup"><span data-stu-id="a4f7d-111">On the **Configuration Questions** page, select the option to **Create a new SSO system**.</span></span>  
  
3.  <span data-ttu-id="a4f7d-112">Sur le **comptes Windows** , spécifiez les informations d’identification du compte de service pour le service d’authentification unique.</span><span class="sxs-lookup"><span data-stu-id="a4f7d-112">On the **Windows Accounts** page, specify the service account credentials for the SSO service.</span></span> <span data-ttu-id="a4f7d-113">Vous devez être membre du groupe Administrateurs de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="a4f7d-113">This must be a member of the SSO Administrators group.</span></span>  
  
4.  <span data-ttu-id="a4f7d-114">Sur le **les Configurations de base de données** , spécifiez l’emplacement de SQL Server (ordinateur C) et le nom de la base de données SSO (SSODB).</span><span class="sxs-lookup"><span data-stu-id="a4f7d-114">On the **Database Configurations** page, specify the location of the SQL Server (computer C) and the name of the SSO database (SSODB).</span></span>  
  
5.  <span data-ttu-id="a4f7d-115">Indiquez les options de sauvegarde du secret principal.</span><span class="sxs-lookup"><span data-stu-id="a4f7d-115">Specify the options to back up the Master Secret.</span></span>  
  
6.  <span data-ttu-id="a4f7d-116">Terminez la configuration.</span><span class="sxs-lookup"><span data-stu-id="a4f7d-116">Complete the configuration.</span></span>  
  
### <a name="to-configure-the-sso-server-on-computer-b"></a><span data-ttu-id="a4f7d-117">Pour configurer le serveur d'authentification unique sur l'ordinateur B</span><span class="sxs-lookup"><span data-stu-id="a4f7d-117">To configure the SSO server on Computer B</span></span>  
  
1.  <span data-ttu-id="a4f7d-118">Installez le service d'authentification unique de l'entreprise sur l'ordinateur B.</span><span class="sxs-lookup"><span data-stu-id="a4f7d-118">Install Enterprise Single Sign-On on Computer B.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a4f7d-119">Il peut s'agir d'un ordinateur BizTalk Server ou Host Integration Server, d'un serveur Web ou d'un simple serveur d'authentification unique (composants d'exécution SSO).</span><span class="sxs-lookup"><span data-stu-id="a4f7d-119">This can be a BizTalk Server or Host Integration Server computer, a Web server, or an SSO-only server (SSO runtime components).</span></span>  
  
2.  <span data-ttu-id="a4f7d-120">Exécutez l'Assistant Configuration pour configurer l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="a4f7d-120">Run the Configuration Wizard to configure SSO.</span></span> <span data-ttu-id="a4f7d-121">Sur le **Questions de Configuration** page, sélectionnez l’option à **joindre un système SSO existant**.</span><span class="sxs-lookup"><span data-stu-id="a4f7d-121">On the **Configuration Questions** page, select the option to **Join an existing SSO system**.</span></span>  
  
3.  <span data-ttu-id="a4f7d-122">Sur le **comptes Windows** , spécifiez les informations d’identification du compte de service pour le service d’authentification unique.</span><span class="sxs-lookup"><span data-stu-id="a4f7d-122">On the **Windows Accounts** page, specify the service account credentials for the SSO service.</span></span> <span data-ttu-id="a4f7d-123">Vous devez être membre du groupe Administrateurs de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="a4f7d-123">This must be a member of the SSO Administrators group.</span></span>  
  
4.  <span data-ttu-id="a4f7d-124">Sur le **les Configurations de base de données** page, pointez sur l’emplacement de SQL Server (ordinateur C) et le nom de la base de données SSO (SSODB).</span><span class="sxs-lookup"><span data-stu-id="a4f7d-124">On the **Database Configurations** page, point to the location of the SQL Server (computer C) and the name of the SSO database (SSODB).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4f7d-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4f7d-125">See Also</span></span>  
 <span data-ttu-id="a4f7d-126">[Mise en Cluster du serveur de secret principal](../core/how-to-cluster-the-master-secret-server1.md) </span><span class="sxs-lookup"><span data-stu-id="a4f7d-126">[How to Cluster the Master Secret Server](../core/how-to-cluster-the-master-secret-server1.md) </span></span>  
 [<span data-ttu-id="a4f7d-127">L’installation de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="a4f7d-127">Installing SSO</span></span>](../core/installing-sso.md)