---
title: "Options d’Installation standard de l’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing, SSO
- SSO, installing
ms.assetid: 59aeb503-f369-4145-8a3c-ab60e9ed31a8
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26441ca5d63ebdb4cba807173f7e7068ff846bdf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="standard-sso-installation-options"></a><span data-ttu-id="f59f7-102">Options d’Installation standard de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="f59f7-102">Standard SSO Installation Options</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f59f7-103"> tire parti des fonctionnalités de l'authentification unique de l'entreprise pour stocker des informations d'identification de manière sécurisée à des fins d'autorisation de scénarios d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="f59f7-103"> leverages the Enterprise Single Sign-On (SSO) capabilities for securely storing credentials to enable single sign-on scenarios.</span></span>  
  
 <span data-ttu-id="f59f7-104">BizTalk Server fait également appel à l'authentification unique pour stocker en toute sécurité des données de configuration personnalisées associées à des adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="f59f7-104">BizTalk Server also uses SSO to store custom configuration data of Adapters securely.</span></span> <span data-ttu-id="f59f7-105">Pour ce faire, les composants d'exécution et d'administration de BizTalk Server installent SSO en tant que composant dépendant.</span><span class="sxs-lookup"><span data-stu-id="f59f7-105">To do this, BizTalk Server runtime and administration features install SSO as a dependent feature.</span></span> <span data-ttu-id="f59f7-106">L'installation par défaut de BizTalk Server comporte l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="f59f7-106">The default installation of BizTalk Server installs Enterprise SSO.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f59f7-107">Après avoir installé l'authentification unique de l'entreprise (composant serveur), vous devez la configurer.</span><span class="sxs-lookup"><span data-stu-id="f59f7-107">When Enterprise Single Sign-on (Server component) is installed, configuration needs to be performed.</span></span> <span data-ttu-id="f59f7-108">La première étape de la configuration d'un système SSO consiste à paramétrer le serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="f59f7-108">The first step to set up an SSO System is to configure the master secret server.</span></span> <span data-ttu-id="f59f7-109">Il est recommandé de configurer un serveur de secret principal autonome.</span><span class="sxs-lookup"><span data-stu-id="f59f7-109">It is recommended to set up a stand-alone master secret server.</span></span> <span data-ttu-id="f59f7-110">Cette opération peut être réalisée en sélectionnant uniquement l'authentification unique de l'entreprise dans l'arborescence des fonctionnalités personnalisées du programme d'installation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f59f7-110">This can be done by only selecting Enterprise Single Sign-on from the custom feature tree in BizTalk Server setup.</span></span>  
>   
>  <span data-ttu-id="f59f7-111">Il est également recommandé que chaque ordinateur exécutant l'authentification unique de l'entreprise dispose d'un service de synchronisation d'heure en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="f59f7-111">We also recommend that any computer running Enterprise Single Sign-On have a time synchronization service running.</span></span> <span data-ttu-id="f59f7-112">Cela permet de synchroniser l'heure d'un ordinateur avec le reste du système, une condition nécessaire au bon fonctionnement des services d'émission de tickets SSO.</span><span class="sxs-lookup"><span data-stu-id="f59f7-112">This keeps the computer time in sync with the rest of the system, which is necessary for SSO ticketing services to function properly.</span></span>  
  
 <span data-ttu-id="f59f7-113">**Liste des options d’installation**: exécuter la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="f59f7-113">**List of installation options**: Run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup program.</span></span> <span data-ttu-id="f59f7-114">Sélectionnez **Installation personnalisée**, puis sélectionnez l’option appropriée dans la liste suivante :</span><span class="sxs-lookup"><span data-stu-id="f59f7-114">Select **Custom Installation**, and then select the appropriate option from the following list:</span></span>  
  
-   <span data-ttu-id="f59f7-115">**Administration de l’authentification unique de l’entreprise :** outils d’Administration et de client pour le mappage et de la connexion aux Services d’authentification unique de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="f59f7-115">**Enterprise Single Sign-On Administration ―** Administration and client tools for mapping and connecting to Enterprise Single Sign-On Services.</span></span>  
  
-   <span data-ttu-id="f59f7-116">**Entreprise seule l’authentification serveur de secret principal :** joue le rôle du serveur de secret principal dans le système d’authentification unique.</span><span class="sxs-lookup"><span data-stu-id="f59f7-116">**Enterprise Single Sign-On Master Secret Server ―** Acts as the Master Secret Server in the SSO System.</span></span> <span data-ttu-id="f59f7-117">Il s'agit du premier serveur qui doit être déployé dans le système SSO mais aussi celui qui vous permet de créer la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="f59f7-117">This is the first server in the SSO System that needs to deployed and this allows you to create the SSO database.</span></span>  
  
 <span data-ttu-id="f59f7-118">À l'aide de l'utilitaire Ajout/Suppression de programmes, vous pouvez également ajouter les composants suivants après l'installation :</span><span class="sxs-lookup"><span data-stu-id="f59f7-118">You can also add the following after setup, by using the Add or Remove Programs utility:</span></span>  
  
-   <span data-ttu-id="f59f7-119">**Serveur Runtime :** Core services pour activer l’authentification unique et à stocker ou accéder aux données de configuration en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="f59f7-119">**Server Runtime ―** Core services to enable single sign-on and to store/access configuration data securely.</span></span>  
  
-   <span data-ttu-id="f59f7-120">**Administration de l’authentification unique de l’entreprise :** outils d’Administration et de client pour le mappage et de la connexion aux Services d’authentification unique de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="f59f7-120">**Enterprise Single Sign-On Administration ―** Administration and client tools for mapping and connecting to Enterprise Single Sign-On Services.</span></span>  
  
-   <span data-ttu-id="f59f7-121">**Seule l’authentification Services d’entreprise avec synchronisation de mot de passe :** Services pour activer la fonctionnalité de synchronisation de mot de passe dans le système d’authentification unique de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="f59f7-121">**Enterprise Single Sign-On Services with Password Synchronization ―** Services to enable the Password Synchronization feature in the Enterprise SSO System.</span></span> <span data-ttu-id="f59f7-122">Ces services s'intègrent également au service de notification de modification de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="f59f7-122">These services also integrate with the Microsoft Password Change Notification Service.</span></span> <span data-ttu-id="f59f7-123">Après avoir installé les principaux services de l'authentification unique de l'entreprise, vous pouvez installer la fonctionnalité de synchronisation de mot de passe à partir du package BizTalk Server. Pour ce faire, exécutez \Platform\SSO\Setup.exe, puis sélectionnez la fonctionnalité Synchronisation de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="f59f7-123">Once you have installed the core Enterprise Single Sign-On services, you can install the Password Synchronization feature of Enterprise SSO from the BizTalk Server package by launching the \Platform\SSO\Setup.exe and selecting the Password Synchronization feature.</span></span>  
  
-   <span data-ttu-id="f59f7-124">**Kit de développement logiciel** informations de référence et de programmation.</span><span class="sxs-lookup"><span data-stu-id="f59f7-124">**Software Development Kit** Programming and Reference information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f59f7-125">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f59f7-125">In This Section</span></span>  
  
-   [<span data-ttu-id="f59f7-126">Comment installer le composant Administration de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="f59f7-126">How to Install the SSO Administration Component</span></span>](../core/how-to-install-the-sso-administration-component.md)  
  
-   [<span data-ttu-id="f59f7-127">Comment installer l’utilitaire Client SSO</span><span class="sxs-lookup"><span data-stu-id="f59f7-127">How to Install the SSO Client Utility</span></span>](../core/how-to-install-the-sso-client-utility.md)