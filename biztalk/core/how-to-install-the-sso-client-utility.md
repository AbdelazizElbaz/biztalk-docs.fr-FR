---
title: "Comment installer l’utilitaire Client SSO | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing, SSO
- SSO, client utility
- client utility [SSO]
- SSO, installing
ms.assetid: e14d257e-2fde-46af-b90c-5dbc0884536b
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4eba4e0747c9566c5303e04602d957173cc56052
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-the-sso-client-utility"></a><span data-ttu-id="08b8c-102">Comment installer l’utilitaire Client SSO</span><span class="sxs-lookup"><span data-stu-id="08b8c-102">How to Install the SSO Client Utility</span></span>
<span data-ttu-id="08b8c-103">L'utilitaire client SSO autonome (utilitaire de ligne de commande basé sur l'interface client) permet aux utilisateurs finaux de configurer leurs mappages clients dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="08b8c-103">The stand-alone SSO client utility (command-line utility and user interface-based) allows end users to configure their client mappings in the SSO database.</span></span> <span data-ttu-id="08b8c-104">Vous pouvez installer l'utilitaire client à partir d'un fichier à extraction automatique (SSOClientInstall.exe) qui est installé avec la fonctionnalité d'administration de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="08b8c-104">You can install the client utility from a self-extracting file (SSOClientInstall.exe) which is installed with the SSO administration feature.</span></span> <span data-ttu-id="08b8c-105">Les administrateurs peuvent également mettre à la disposition des utilisateurs finaux le package d'installation en plaçant une copie de ce dernier sur un partage réseau.</span><span class="sxs-lookup"><span data-stu-id="08b8c-105">Administrators can also make the installer package available to client users by placing a copy of the installer package on a network share.</span></span>  
  
 <span data-ttu-id="08b8c-106">Pour installer l'utilitaire client SSO, vous devez exécuter l'un des systèmes d'exploitation suivants sur l'ordinateur client :</span><span class="sxs-lookup"><span data-stu-id="08b8c-106">To install the SSO client utility, you must be running one of the following operating systems on the client computer:</span></span>  
  
-   [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
-   [!INCLUDE[btsDotNetFramework3.5](../includes/btsdotnetframework3-5-md.md)]<span data-ttu-id="08b8c-107"> ou [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] (nécessaire uniquement si vous utilisez l'utilitaire client SSO basé sur l'interface utilisateur ou pour exploiter le composant d'interopérabilité géré de l'authentification unique de l'entreprise).</span><span class="sxs-lookup"><span data-stu-id="08b8c-107"> or [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] (only necessary if you are using the UI-based SSO Client Utility or for leveraging the managed interoperability component of Enterprise SSO).</span></span>  
  
 <span data-ttu-id="08b8c-108">Après l’installation de l’utilitaire Client SSO, vous pouvez le lancer à partir de la **Démarrer** en cliquant sur **programmes**, **Microsoft Enterprise Single Sign-On**, puis **Utilitaire Client SSO**.</span><span class="sxs-lookup"><span data-stu-id="08b8c-108">After installing the SSO Client Utility, you can launch it from the **Start** menu by clicking **Programs**, **Microsoft Enterprise Single Sign-On**, and then **SSO Client Utility**.</span></span>  
  
### <a name="to-install-the-sso-client-utility"></a><span data-ttu-id="08b8c-109">Pour installer l'utilitaire client SSO</span><span class="sxs-lookup"><span data-stu-id="08b8c-109">To install the SSO client utility</span></span>  
  
1.  <span data-ttu-id="08b8c-110">Double-cliquez sur le package d'installation SSOClientInstall.</span><span class="sxs-lookup"><span data-stu-id="08b8c-110">Double-click the installer package SSOClientInstall.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="08b8c-111">Demandez à votre administrateur SSO de vous indiquer l'emplacement de ce fichier dans votre société.</span><span class="sxs-lookup"><span data-stu-id="08b8c-111">Ask your Enterprise Single Sign-On Administrator for the location of this file in your enterprise.</span></span>  
  
     <span data-ttu-id="08b8c-112">Le **WinZip Self-Extractor** programme s’affiche.</span><span class="sxs-lookup"><span data-stu-id="08b8c-112">The **WinZip Self-Extractor** program appears.</span></span>  
  
2.  <span data-ttu-id="08b8c-113">Sélectionnez le dossier dans lequel vous souhaitez décompresser les fichiers, puis cliquez sur **Unzip**.</span><span class="sxs-lookup"><span data-stu-id="08b8c-113">Select the folder where you want to unzip the files, and click **Unzip**.</span></span>  
  
     <span data-ttu-id="08b8c-114">Il est recommandé de décompresser les fichiers dans un dossier temporaire.</span><span class="sxs-lookup"><span data-stu-id="08b8c-114">It is recommended to unzip the files in a temporary folder.</span></span>  
  
     <span data-ttu-id="08b8c-115">Le **entreprise authentification Client d’installation unique** programme s’affiche.</span><span class="sxs-lookup"><span data-stu-id="08b8c-115">The **Enterprise Single Sign-On Client Setup** program appears.</span></span>  
  
3.  <span data-ttu-id="08b8c-116">Sur **la Bienvenue dans l’entreprise l’authentification Client unique** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="08b8c-116">On **the Welcome to the Enterprise Single Sign-On Client** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="08b8c-117">Dans la page Contrat de licence, cliquez sur **J’accepte les termes de ce contrat de licence**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="08b8c-117">On the License Agreement page, click **I accept the terms of this license agreement**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="08b8c-118">Sur le **informations utilisateur** page, tapez votre nom d’utilisateur, le nom de l’organisation, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="08b8c-118">On the **User Information** page, type your user name, organization name, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="08b8c-119">Sur le **démarrer l’Installation** , cliquez sur **installer**.</span><span class="sxs-lookup"><span data-stu-id="08b8c-119">On the **Start Installation** page, click **Install**.</span></span>  
  
7.  <span data-ttu-id="08b8c-120">Sur le **fin de l’entreprise seule l’authentification Client Assistant** , cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="08b8c-120">On the **Completing the Enterprise Single Sign-On Client Wizard** page, click **Finish**.</span></span>  
  
8.  <span data-ttu-id="08b8c-121">Spécifiez le serveur SSO en procédant de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="08b8c-121">Specify the SSO server by doing either of the following:</span></span>  
  
    -   <span data-ttu-id="08b8c-122">Ouvrez le composant logiciel enfichable MMC du Administration ENTSSO.</span><span class="sxs-lookup"><span data-stu-id="08b8c-122">Open the ENTSSO Administration MMC Snap-In.</span></span> <span data-ttu-id="08b8c-123">Le **sélectionner le serveur SSO** boîte de dialogue apparaît.</span><span class="sxs-lookup"><span data-stu-id="08b8c-123">The **Select SSO Server** dialog will appear.</span></span> <span data-ttu-id="08b8c-124">Accédez au serveur SSO auquel vous voulez vous connecter lors de l'exécution des opérations d'administration.</span><span class="sxs-lookup"><span data-stu-id="08b8c-124">Enter or browse to the SSO Server that you want to connect to when you perform administration operations.</span></span> <span data-ttu-id="08b8c-125">Pour spécifier le serveur SSO pour tous les utilisateurs sur l’ordinateur, sélectionnez **définir le serveur d’authentification unique pour tous les utilisateurs**.</span><span class="sxs-lookup"><span data-stu-id="08b8c-125">To specify the SSO Server for all users on the machine, select **Set SSO Server for all users**.</span></span>  
  
         <span data-ttu-id="08b8c-126">ou</span><span class="sxs-lookup"><span data-stu-id="08b8c-126">OR</span></span>  
  
    -   <span data-ttu-id="08b8c-127">À l’invite de commandes, tapez `ssomanage –server` pour spécifier le serveur SSO souhaité.</span><span class="sxs-lookup"><span data-stu-id="08b8c-127">At a command prompt, type `ssomanage –server` to specify the SSO server desired.</span></span> <span data-ttu-id="08b8c-128">Vous pouvez également taper `ssomanage -serverall` pour spécifier le serveur SSO auquel tous les utilisateurs de cet ordinateur se connectera lors des opérations d’administration.</span><span class="sxs-lookup"><span data-stu-id="08b8c-128">You can also type `ssomanage -serverall` to specify the SSO server that all users of this computer will connect to when performing administration operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08b8c-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08b8c-129">See Also</span></span>  
 <span data-ttu-id="08b8c-130">[Comment installer le composant Administration de l’authentification unique](../core/how-to-install-the-sso-administration-component.md) </span><span class="sxs-lookup"><span data-stu-id="08b8c-130">[How to Install the SSO Administration Component](../core/how-to-install-the-sso-administration-component.md) </span></span>  
 <span data-ttu-id="08b8c-131">[Configuration de l’authentification unique](../core/configuring-sso.md) </span><span class="sxs-lookup"><span data-stu-id="08b8c-131">[Configuring SSO](../core/configuring-sso.md) </span></span>  
 [<span data-ttu-id="08b8c-132">L’installation de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="08b8c-132">Installing SSO</span></span>](../core/installing-sso.md)