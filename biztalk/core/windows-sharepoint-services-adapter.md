---
title: Adaptateur de Windows SharePoint Services | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Windows SharePoint Services adapters
ms.assetid: cbfc9bf3-912d-4849-ba8c-07a116888bbd
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a6f1365b11ce93717223ec35e395165e8d0e551
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="windows-sharepoint-services-adapter"></a><span data-ttu-id="307c8-102">Adaptateur Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="307c8-102">Windows SharePoint Services Adapter</span></span>
<span data-ttu-id="307c8-103">L'adaptateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour Microsoft Windows SharePoint Services fournit une intégration étroite de BizTalk Server avec Windows SharePoint Services et Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="307c8-103">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapter for Microsoft Windows SharePoint Services provides a tighter integration of BizTalk Server with Windows SharePoint Services and Microsoft Office.</span></span> <span data-ttu-id="307c8-104">L'utilisation de l'adaptateur Windows SharePoint Services au sein de votre solution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vous permet de bénéficier des fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="307c8-104">Using the Windows SharePoint Services adapter in your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution provides you with the following capabilities:</span></span>  
  
-   <span data-ttu-id="307c8-105">Accès aisé aux messages entrants et sortants via Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="307c8-105">Easy access to input and output messages through Windows SharePoint Services.</span></span>  
  
-   <span data-ttu-id="307c8-106">Capacité à modifier les messages XML à l’aide des applications Office telles que Microsoft Office InfoPath.</span><span class="sxs-lookup"><span data-stu-id="307c8-106">The ability to edit XML messages by using Office applications such as Microsoft Office InfoPath.</span></span>  
  
-   <span data-ttu-id="307c8-107">Transformation bidirectionnelle des messages XML vers et depuis InfoPath.</span><span class="sxs-lookup"><span data-stu-id="307c8-107">Two-way transformations of XML messages to and from InfoPath.</span></span>  
  
 <span data-ttu-id="307c8-108">L’adaptateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] possède les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="307c8-108">The [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] adapter consists of the following components:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="307c8-109">Adaptateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] CSOM</span><span class="sxs-lookup"><span data-stu-id="307c8-109">CSOM [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Adapter</span></span>|<span data-ttu-id="307c8-110">Utilise le Modèle objet côté client (CSOM) [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="307c8-110">Uses the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Client Side Object Model (CSOM).</span></span> <span data-ttu-id="307c8-111">L’adaptateur est installé lors de l’installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="307c8-111">The adapter is installed when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed.</span></span> <span data-ttu-id="307c8-112">Aucune étape d’installation supplémentaire n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="307c8-112">There are no additional installation steps.</span></span><br /><br /> <span data-ttu-id="307c8-113">Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation ***automatiquement*** installe le SharePoint Client composant redistribuable du modèle, qui est également disponible à l’adresse [http://go.microsoft.com/fwlink/p/?LinkId=263482](http://go.microsoft.com/fwlink/p/?LinkId=263482).</span><span class="sxs-lookup"><span data-stu-id="307c8-113">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation ***automatically*** installs the SharePoint Client Object Model Redistributable, which is also available at [http://go.microsoft.com/fwlink/p/?LinkId=263482](http://go.microsoft.com/fwlink/p/?LinkId=263482).</span></span>|  
|<span data-ttu-id="307c8-114">Service Web [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] SSOM</span><span class="sxs-lookup"><span data-stu-id="307c8-114">SSOM [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Web Service</span></span>|<span data-ttu-id="307c8-115">**Option déconseillée**.</span><span class="sxs-lookup"><span data-stu-id="307c8-115">**Deprecated**.</span></span> <span data-ttu-id="307c8-116">Utilise le modèle SSOM (Service-Side Object Model) [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="307c8-116">Uses the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Service Side Object Model (SSOM).</span></span><br /><br /> <span data-ttu-id="307c8-117">Le service web est installé sur l’ordinateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)], qui peut se trouver sur le même ordinateur que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou sur un ordinateur différent.</span><span class="sxs-lookup"><span data-stu-id="307c8-117">The web service is installed on the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] computer, which can be on the same computer as [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or a separate computer.</span></span><br /><br /> <span data-ttu-id="307c8-118">Pour installer le service web, exécutez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation sur le [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] ordinateur et recherchez **adaptateur Windows SharePoint Services**.</span><span class="sxs-lookup"><span data-stu-id="307c8-118">To install the web service, run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation on the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] computer and check **Windows SharePoint Services Adapter**.</span></span>|  
  
 <span data-ttu-id="307c8-119">[Annexe b : installer l’adaptateur SharePoint de Microsoft](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) fournit des informations sur la [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="307c8-119">[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) provides more information on the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] installation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="307c8-120">L'authentification fédérée n'est pas prise en charge pour l'instant.</span><span class="sxs-lookup"><span data-stu-id="307c8-120">Currently, federated authentication is not supported.</span></span> <span data-ttu-id="307c8-121">Seule l'authentification par nom d'utilisateur et mot de passe est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="307c8-121">Only Username and Password are supported.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="307c8-122">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="307c8-122">In This Section</span></span>  
  
-   [<span data-ttu-id="307c8-123">CSOM : L’adaptateur SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="307c8-123">CSOM: SharePoint Services Adapter</span></span>](../core/csom-sharepoint-services-adapter.md)  
  
-   [<span data-ttu-id="307c8-124">SSOM : Le Service Web adaptateur SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="307c8-124">SSOM: SharePoint Services Adapter Web Service</span></span>](../core/ssom-sharepoint-services-adapter-web-service.md)  
  
## <a name="see-also"></a><span data-ttu-id="307c8-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="307c8-125">See Also</span></span>  
 <span data-ttu-id="307c8-126">[À l’aide des adaptateurs](../core/using-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="307c8-126">[Using Adapters](../core/using-adapters.md) </span></span>  
 [<span data-ttu-id="307c8-127">Développement d’Applications de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="307c8-127">Developing BizTalk Server Applications</span></span>](../core/developing-biztalk-server-applications.md)