---
title: "Comment activer ASP.NET 4.0 pour les Services Web publiés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58646ff2-77a3-49dc-8593-f6e41d85d4f3
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e68b8eef114828ad181e83ce0c7acd70a5545e0d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-aspnet-40-for-published-web-services"></a><span data-ttu-id="3c58d-102">Comment activer ASP.NET 4.0 pour les Services Web publiés</span><span class="sxs-lookup"><span data-stu-id="3c58d-102">How to Enable ASP.NET 4.0 for Published Web Services</span></span>
<span data-ttu-id="3c58d-103">Définissez la version de ASP.Net dans IIS.</span><span class="sxs-lookup"><span data-stu-id="3c58d-103">Set the ASP.Net version in IIS.</span></span>

<span data-ttu-id="3c58d-104">L’Assistant Publication de BizTalk Server Web Services s’appuie sur les fonctionnalités fournies avec ASP.NET, qui est inclus dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3c58d-104">The BizTalk Server Web Services Publishing Wizard relies on functionality provided with ASP.NET, which is included with the .NET Framework.</span></span> <span data-ttu-id="3c58d-105">Les versions de ASP.Net sont incluses avec la version CLR .NET que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="3c58d-105">The ASP.Net versions are included with the .NET CLR version you choose.</span></span> 

<span data-ttu-id="3c58d-106">Cette rubrique montre comment modifier la version CLR .NET.</span><span class="sxs-lookup"><span data-stu-id="3c58d-106">This topic shows you how to change the .NET CLR version.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="3c58d-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="3c58d-107">Prerequisites</span></span>

<span data-ttu-id="3c58d-108">IIS est inclus dans le **serveur Web (IIS)** rôle dans le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="3c58d-108">IIS is included with the **Web Server (IIS)** role in the operating system.</span></span> <span data-ttu-id="3c58d-109">Lorsque vous installez ce rôle, également sélectionner la version la plus récente de ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3c58d-109">When you install this role, also select the newer version of ASP.NET.</span></span> 
  
## <a name="update-an-application-pool"></a><span data-ttu-id="3c58d-110">Mettre à jour un pool d’applications</span><span class="sxs-lookup"><span data-stu-id="3c58d-110">Update an application pool</span></span>
  
1.  <span data-ttu-id="3c58d-111">Ouvrez **Internet Information Services (IIS) Manager**:</span><span class="sxs-lookup"><span data-stu-id="3c58d-111">Open **Internet Information Services (IIS) Manager**:</span></span>

    1. <span data-ttu-id="3c58d-112">Dans **le Gestionnaire de serveur**, sélectionnez **outils**.</span><span class="sxs-lookup"><span data-stu-id="3c58d-112">In **Server Manager**, select **Tools**.</span></span>
    2. <span data-ttu-id="3c58d-113">Sélectionnez **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="3c58d-113">Select **Internet Information Services (IIS) Manager**.</span></span>
  
2.  <span data-ttu-id="3c58d-114">Développez le nom du serveur, puis sélectionnez **Pools d’applications**.</span><span class="sxs-lookup"><span data-stu-id="3c58d-114">Expand the server name, and select **Application Pools**.</span></span>  
  
3.  <span data-ttu-id="3c58d-115">Sélectionnez le pool d’applications, puis ouvrez le **les paramètres de base**.</span><span class="sxs-lookup"><span data-stu-id="3c58d-115">Select the app pool, and open the **Basic Settings**.</span></span>  
  
4. <span data-ttu-id="3c58d-116">Définir le **version .NET CLR** à la version plus récente, puis sélectionnez **OK** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="3c58d-116">Set the **.NET CLR version** to the newer version, and select **OK** to save your changes.</span></span>  

> [!NOTE]
> <span data-ttu-id="3c58d-117">Vous pouvez également modifier la version dans le fichier web.config.</span><span class="sxs-lookup"><span data-stu-id="3c58d-117">You can also change the version in the web.config file.</span></span>
 
## <a name="allow-the-aspnet-extension"></a><span data-ttu-id="3c58d-118">Autoriser l’extension ASP.Net</span><span class="sxs-lookup"><span data-stu-id="3c58d-118">Allow the ASP.Net extension</span></span>
  
1.  <span data-ttu-id="3c58d-119">Ouvrez **Internet Information Services (IIS) Manager**:</span><span class="sxs-lookup"><span data-stu-id="3c58d-119">Open **Internet Information Services (IIS) Manager**:</span></span>

    1. <span data-ttu-id="3c58d-120">Dans **le Gestionnaire de serveur**, sélectionnez **outils**.</span><span class="sxs-lookup"><span data-stu-id="3c58d-120">In **Server Manager**, select **Tools**.</span></span>
    2. <span data-ttu-id="3c58d-121">Sélectionnez **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="3c58d-121">Select **Internet Information Services (IIS) Manager**.</span></span>
  
2.  <span data-ttu-id="3c58d-122">Sélectionnez le nom du serveur, puis double-cliquez sur **Restrictions ISAPI et CGI**.</span><span class="sxs-lookup"><span data-stu-id="3c58d-122">Select the server name, and double-click **ISAPI and CGI Restrictions**.</span></span>  
  
3. <span data-ttu-id="3c58d-123">Confirmer l’ASP.NET **autorisées** pour les versions 32 bits et 64 bits.</span><span class="sxs-lookup"><span data-stu-id="3c58d-123">Confirm ASP.NET is **Allowed** for the 32-bit and 64-bit versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c58d-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c58d-124">See Also</span></span>  
 [<span data-ttu-id="3c58d-125">Planification de la publication de Services Web</span><span class="sxs-lookup"><span data-stu-id="3c58d-125">Planning for Publishing Web Services</span></span>](../core/planning-for-publishing-web-services2.md)