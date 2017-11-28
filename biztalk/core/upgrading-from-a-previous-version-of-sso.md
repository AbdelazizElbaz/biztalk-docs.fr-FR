---
title: "La mise à niveau à partir d’une Version précédente de l’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading, SSO
- SSO, upgrading
ms.assetid: 78b99d99-9a10-4453-9db5-ae1bacd7de50
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf36c33b9480c0e8658089fdc9d996b3701d7660
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="upgrading-from-a-previous-version-of-sso"></a><span data-ttu-id="99bb6-102">La mise à niveau à partir d’une Version précédente de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="99bb6-102">Upgrading from a Previous Version of SSO</span></span>
<span data-ttu-id="99bb6-103">Si vous installez la fonctionnalité Enterprise Single Sign-on et que vous disposez déjà d’une version précédente est déployée sur votre ordinateur (par exemple, à partir de Microsoft BizTalk Server 2009), vous devez effectuer les étapes ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="99bb6-103">If you are installing the Enterprise Single Sign-on feature and you already have a previous version deployed on your computer (for example, from Microsoft BizTalk Server 2009), you must complete the steps below.</span></span>  
  
1.  <span data-ttu-id="99bb6-104">Sauvegardez la base de données SSO dans un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="99bb6-104">Back up the SSO database to a secure location</span></span>  
  
2.  <span data-ttu-id="99bb6-105">Sauvegardez la clé de secret principal sur le serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="99bb6-105">Back up the master secret key on the master secret server</span></span>  
  
3.  <span data-ttu-id="99bb6-106">Mettre à jour le serveur de secret principal en exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] le programme d’installation en choisissant **Installation personnalisée**, puis en sélectionnant **Enterprise Single Sign-On**.</span><span class="sxs-lookup"><span data-stu-id="99bb6-106">Update the master secret server by running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup, choosing **Custom Installation**, and then selecting **Enterprise Single Sign-On**.</span></span>  
  
4.  <span data-ttu-id="99bb6-107">Après avoir sélectionné **activer Enterprise Single Sign-on sur cet ordinateur**, sélectionnez **joindre un système SSO existant**.</span><span class="sxs-lookup"><span data-stu-id="99bb6-107">After selecting **Enable Enterprise Single Sign-on on this computer**, select **Join an existing SSO system**.</span></span>  
  
 <span data-ttu-id="99bb6-108">La mise à jour des autres serveurs SSO (serveurs de secret non principaux) de votre installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="99bb6-108">It is not necessary to update the other SSO servers (non-master secret servers) from your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation.</span></span> <span data-ttu-id="99bb6-109">Toutefois, si vous souhaitez que les nouvelles fonctionnalités d'authentification unique de l'entreprise soient disponibles sur ces serveurs, vous devez les mettre à jour en suivant la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="99bb6-109">However, if you want the new Enterprise Single Sign-On features to be available on those servers, you must update them by using the same procedure outlined above.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99bb6-110">Ces considérations s’appliquent également si vous installez Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur un ordinateur avec une installation existante de Host Integration Server 2009 Enterprise Single Sign-On et que vous souhaitez mettre à jour les serveurs.</span><span class="sxs-lookup"><span data-stu-id="99bb6-110">These considerations also apply if you are installing Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on a computer with an existing installation of Host Integration Server 2009 Enterprise Single Sign-On, and you want to update the servers.</span></span>  
  
 <span data-ttu-id="99bb6-111">Si vous installez Host Integration Server sur un ordinateur sur lequel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est déjà installé, ne sélectionnez pas la fonctionnalité d'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="99bb6-111">If you are installing Host Integration Server on a computer where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is already installed, do not select the Enterprise Single Sign-On feature.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="99bb6-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="99bb6-112">In This Section</span></span>  
  
-   [<span data-ttu-id="99bb6-113">Utilisation de l’hôte initiée par les fonctionnalités de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="99bb6-113">Using Host Initiated SSO Functionality</span></span>](../core/using-host-initiated-sso-functionality.md)  
  
-   [<span data-ttu-id="99bb6-114">Serveurs de traitement pour l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="99bb6-114">Processing Servers for SSO</span></span>](../core/processing-servers-for-sso.md)