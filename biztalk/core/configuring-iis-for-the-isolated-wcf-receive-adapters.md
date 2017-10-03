---
title: "Configuration d’IIS pour WCF isolé des adaptateurs de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive adapters, WCF services
- WCF services, receive adapters
- IIS, configuring [WCF receive adapters]
ms.assetid: 1c6f1561-a7ba-4eb0-8878-bf213ebcd6a6
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1515a69ab6a9150668db4f3415f0483dd1ce4e7a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-iis-for-the-isolated-wcf-receive-adapters"></a><span data-ttu-id="aac72-102">Configuration d'IIS pour les adaptateurs de réception WCF isolés</span><span class="sxs-lookup"><span data-stu-id="aac72-102">Configuring IIS for the Isolated WCF Receive Adapters</span></span>
<span data-ttu-id="aac72-103">Pour publier des services WCF à l'aide de l'Assistant Publication de services WCF BizTalk, vous devez configurer les services Internet (IIS), les hôtes isolés de BizTalk et les comptes du groupe Utilisateurs Windows.</span><span class="sxs-lookup"><span data-stu-id="aac72-103">To publish WCF services by using the BizTalk WCF Service Publishing Wizard, you must configure Internet Information Services (IIS), BizTalk isolated hosts, and Windows user group accounts.</span></span> <span data-ttu-id="aac72-104">Cette section traite des problèmes de configuration des services Internet (IIS) pour publier les services WCF à l'aide des adaptateurs de réception WCF isolés, tels que l'adaptateur de réception WCF-BasicHttp, l'adaptateur de réception WCF-WSHttp et l'adaptateur WCF-CustomIsolated.</span><span class="sxs-lookup"><span data-stu-id="aac72-104">This section discusses issues related to configuring IIS for publishing WCF services with isolated WCF receive adapters such as the WCF-BasicHttp receive adapter, WCF-WSHttp receive adapter, and WCF-CustomIsolated adapter.</span></span> <span data-ttu-id="aac72-105">Pour obtenir des informations générales sur l’hébergement de services WCF dans IIS, consultez « Hosting in IIS » à [http://go.microsoft.com/fwlink/?LinkId=75700](http://go.microsoft.com/fwlink/?LinkId=75700).</span><span class="sxs-lookup"><span data-stu-id="aac72-105">For general information about hosting WCF services in IIS, see "Hosting in IIS" at [http://go.microsoft.com/fwlink/?LinkId=75700](http://go.microsoft.com/fwlink/?LinkId=75700).</span></span>  
  
## <a name="considerations-when-configuring-iis"></a><span data-ttu-id="aac72-106">Considérations à prendre en compte lors de la configuration des services Internet (IIS)</span><span class="sxs-lookup"><span data-stu-id="aac72-106">Considerations When Configuring IIS</span></span>  
 <span data-ttu-id="aac72-107">**Internet Information Services 7.0 et 7.5**</span><span class="sxs-lookup"><span data-stu-id="aac72-107">**Internet Information Services 7.0 and 7.5**</span></span>  
  
 <span data-ttu-id="aac72-108">Vous pouvez utiliser IIS 7.0 and 7.5 configurés avec ASP.NET 4.0 pour publier les services WCF à l'aide des adaptateurs de réception WCF isolés.</span><span class="sxs-lookup"><span data-stu-id="aac72-108">You can use IIS 7.0 and 7.5 configured with ASP.NET 4.0 to publish WCF services with isolated WCF receive adapters.</span></span>  
  
 <span data-ttu-id="aac72-109">IIS 7.0 (pour Windows Server 2008 SP2) et IIS 7.5 (pour Windows Server 2008 R2) utilisent les pools d'applications IIS pour traiter les demandes de service Web.</span><span class="sxs-lookup"><span data-stu-id="aac72-109">IIS 7.0 (for Windows Server 2008 SP2) and IIS 7.5 (for Windows Server 2008 R2) use the IIS application pools for processing Web service requests.</span></span> <span data-ttu-id="aac72-110">IIS 7.0 prend en charge plusieurs pools d'applications.</span><span class="sxs-lookup"><span data-stu-id="aac72-110">IIS 7.0 supports multiple application pools.</span></span> <span data-ttu-id="aac72-111">Chaque processus de pool d'applications peut être exécuté sous un contexte de l'utilisateur différent.</span><span class="sxs-lookup"><span data-stu-id="aac72-111">Each application pool process can run under a different user context.</span></span>  
  
 <span data-ttu-id="aac72-112">**Hôtes BizTalk isolé**</span><span class="sxs-lookup"><span data-stu-id="aac72-112">**BizTalk isolated hosts**</span></span>  
  
 <span data-ttu-id="aac72-113">Pour héberger les services WCF à l'aide des adaptateurs de réception WCF isolés, vous devez créer au moins un hôte isolé dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="aac72-113">To host the WCF services with isolated WCF receive adapters, you must create at least one isolated host in BizTalk Server.</span></span> <span data-ttu-id="aac72-114">Pour plus d’informations sur la configuration des hôtes BizTalk isolé, consultez « Hôtes BizTalk isolés » dans [activation des Services Web](../core/enabling-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="aac72-114">For more information about how to configure BizTalk isolated hosts, see "BizTalk Isolated Hosts" in [Enabling Web Services](../core/enabling-web-services.md).</span></span>  
  
 <span data-ttu-id="aac72-115">**Accès aux données de plusieurs installations de serveur**</span><span class="sxs-lookup"><span data-stu-id="aac72-115">**Database access for multiple server installations**</span></span>  
  
 <span data-ttu-id="aac72-116">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et la base de données de gestion BizTalk résident sur des serveurs différents, vous devez modifier le contexte de l'utilisateur du pool d'applications IIS en un compte d'utilisateur de domaine.</span><span class="sxs-lookup"><span data-stu-id="aac72-116">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the BizTalk Management database reside on different servers, you should change the user context of the IIS Application Pool to a domain user account.</span></span>  
  
 <span data-ttu-id="aac72-117">Lors de l'implémentation d'un déploiement multiserveur, les groupes Windows Hôte isolé doivent exister sur le domaine auquel appartiennent les serveurs de bases de données BizTalk.</span><span class="sxs-lookup"><span data-stu-id="aac72-117">When implementing a multi-server deployment, the Isolated Host Windows groups must exist on the domain to which the BizTalk database servers belong.</span></span>  
  
 <span data-ttu-id="aac72-118">**Réduction des droits d’utilisateur et des privilèges de compte**</span><span class="sxs-lookup"><span data-stu-id="aac72-118">**Minimizing account privileges and user rights**</span></span>  
  
 <span data-ttu-id="aac72-119">Utilisez des hôtes isolés pour donner aux adaptateurs, qui sont exécutés dans des processus externes, l'accès au nombre minimal de ressources requises pour interagir avec BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="aac72-119">You use isolated hosts to give adapters that run in external processes access to the minimal amount of required resources to interact with BizTalk Server.</span></span> <span data-ttu-id="aac72-120">Pour un déploiement sécurisé, vous devez donner les privilèges minimaux au contexte de l'utilisateur pour les processus externes.</span><span class="sxs-lookup"><span data-stu-id="aac72-120">For a secure deployment, you should give the user context for the external processes minimal privileges.</span></span>  
  
 <span data-ttu-id="aac72-121">**Recommandations de sécurité pour l’Assistant de publication des Services Web BizTalk**</span><span class="sxs-lookup"><span data-stu-id="aac72-121">**Security recommendations for the BizTalk Web Services Publishing Wizard**</span></span>  
  
 <span data-ttu-id="aac72-122">Le répertoire virtuel créé par l'Assistant Publication de services WCF BizTalk hérite des listes de contrôle d'accès (ACL) du répertoire virtuel parent ou du site Web.</span><span class="sxs-lookup"><span data-stu-id="aac72-122">The virtual directory created by the BizTalk WCF Service Publishing Wizard inherits the access control lists (ACL) from the parent virtual directory or Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aac72-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aac72-123">See Also</span></span>  
 [<span data-ttu-id="aac72-124">Publication des Services WCF</span><span class="sxs-lookup"><span data-stu-id="aac72-124">Publishing WCF Services</span></span>](../core/publishing-wcf-services.md)