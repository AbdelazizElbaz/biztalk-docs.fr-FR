---
title: "Gestion des partenaires à l’aide de BizTalk Server commerciaux | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f31a5e49-ef19-41a3-9cf3-cf85d0685a59
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5a1ac3c072b21633c3b6f6226aa7cce20729077
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="trading-partner-management-using-biztalk-server"></a><span data-ttu-id="05ccb-102">Gestion des partenaires commerciaux à l'aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="05ccb-102">Trading Partner Management Using BizTalk Server</span></span>
## <a name="introduction-to-tpm"></a><span data-ttu-id="05ccb-103">Introduction au module de plateforme sécurisée</span><span class="sxs-lookup"><span data-stu-id="05ccb-103">Introduction to TPM</span></span>
<span data-ttu-id="05ccb-104">L'interface utilisateur de gestion des partenaires commerciaux (GPC) de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] réinvente les concepts fondamentaux liés à la gestion et au stockage des informations sur les partenaires et leurs activités.</span><span class="sxs-lookup"><span data-stu-id="05ccb-104">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Trading Partner Management (TPM) rebuilds the fundamental concepts around how to manage and store information about partners and their business.</span></span> <span data-ttu-id="05ccb-105">Elle reflète les entités commerciales et leurs relations car elle permet aux organisations de mieux gérer les partenariats avec des partenaires commerciaux.</span><span class="sxs-lookup"><span data-stu-id="05ccb-105">The enhanced TPM solution reflects the business entities and relationships in the field, thereby enabling organizations to better manage your business partnerships with trading partners.</span></span> <span data-ttu-id="05ccb-106">Pour plus d’informations sur la façon dont la solution GPC partenariats commerciaux dans un environnement BizTalk, consultez [blocs de construction d’une Solution de gestion des partenaires commerciaux](../core/building-blocks-of-a-trading-partner-management-solution.md).</span><span class="sxs-lookup"><span data-stu-id="05ccb-106">For more information on how the TPM solution models trading partnerships in a BizTalk environment, see [Building Blocks of a Trading Partner Management Solution](../core/building-blocks-of-a-trading-partner-management-solution.md).</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="05ccb-107">inclut la prise en charge native pour l’échange de données de l’échange de données électroniques (EDI) et le transport de données AS2.</span><span class="sxs-lookup"><span data-stu-id="05ccb-107"> includes native support for Electronic Data Interchange (EDI) data exchange and AS2 data transport.</span></span> <span data-ttu-id="05ccb-108">Cette prise en charge permet aux entreprises d'étendre leurs solutions EDI de gestion des processus d'entreprise, et ainsi de tirer parti des améliorations apportées par l'échange automatisé des transactions EDI en termes de productivité.</span><span class="sxs-lookup"><span data-stu-id="05ccb-108">This support enables businesses to extend their EDI-based business process management solutions, taking advantage of the productivity improvements that the automated exchange of EDI transactions provides.</span></span> <span data-ttu-id="05ccb-109">Grâce à EDI et EDIINT/AS2, BizTalk Server permet aux entreprises de connecter en toute sécurité et fiabilité les partenaires aux processus d'entreprise critiques en relation avec la chaîne logistique.</span><span class="sxs-lookup"><span data-stu-id="05ccb-109">BizTalk Server provides these businesses with the means to more securely and reliably connect partners to critical supply-chain business processes using EDI and EDIINT/AS2.</span></span>  
  
 <span data-ttu-id="05ccb-110">La solution GPC couplée avec la prise en charge EDI et AS2 fournissent une solution fiable et évolutive pour la gestion des partenaires commerciaux dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="05ccb-110">The TPM solution coupled with the EDI and AS2 support provide a robust and scalable solution for managing trading partners in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="05ccb-111">Les rubriques de cette section, ainsi que les rubriques répertoriées ci-dessous, fournissent une présentation détaillée de la solution GPC et de son utilisation dans le cadre de la gestion des partenaires commerciaux.</span><span class="sxs-lookup"><span data-stu-id="05ccb-111">The topics in this section, and other topics listed below, provide a high-level overview of TPM and how to use TPM to manage trading partners.</span></span> <span data-ttu-id="05ccb-112">Elles décrivent également les traitements EDI et AS2 effectués par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="05ccb-112">The topics also provide description of how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performs EDI and AS2 processing.</span></span>  
  
## <a name="in-this-section-and-more-good-info"></a><span data-ttu-id="05ccb-113">Dans cette section et les bonnes informations</span><span class="sxs-lookup"><span data-stu-id="05ccb-113">In this section and more good info</span></span>

<span data-ttu-id="05ccb-114">**En savoir plus, la mise en route et des didacticiels**</span><span class="sxs-lookup"><span data-stu-id="05ccb-114">**Learn, get started, and tutorials**</span></span>  

-   [<span data-ttu-id="05ccb-115">Blocs de construction d’une Solution de gestion des partenaires commerciaux</span><span class="sxs-lookup"><span data-stu-id="05ccb-115">Building Blocks of a Trading Partner Management Solution</span></span>](../core/building-blocks-of-a-trading-partner-management-solution.md)  
  
-   [<span data-ttu-id="05ccb-116">Fonctionnalité EDI de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="05ccb-116">BizTalk Server EDI Functionality</span></span>](../core/biztalk-server-edi-functionality.md)  
  
-   [<span data-ttu-id="05ccb-117">Fonctionnalités AS2 de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="05ccb-117">BizTalk Server AS2 Functionality</span></span>](../core/biztalk-server-as2-functionality.md)  

- [<span data-ttu-id="05ccb-118">Architecture de la solution EDI et AS2</span><span class="sxs-lookup"><span data-stu-id="05ccb-118">EDI and AS2 solution architecture</span></span>](../core/edi-and-as2-solution-architecture.md)

-   [<span data-ttu-id="05ccb-119">Étapes d’optimisation de l’environnement après configuration</span><span class="sxs-lookup"><span data-stu-id="05ccb-119">Post-configuration steps to optimize your environment</span></span>](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md) 

- [<span data-ttu-id="05ccb-120">Didacticiels et procédures pas à pas pour EDI, AS2 et EDIFACT</span><span class="sxs-lookup"><span data-stu-id="05ccb-120">Tutorials and walkthroughs for EDI, AS2, and EDIFACT</span></span>](../core/tutorials-and-walkthroughs-for-edi-as2-and-edifact.md)


<span data-ttu-id="05ccb-121">**Présentation détaillée de la création de solutions EDI et AS2**</span><span class="sxs-lookup"><span data-stu-id="05ccb-121">**Deep-dive in creating EDI and AS2 solutions**</span></span>
- [<span data-ttu-id="05ccb-122">Créer des artefacts EDI et AS2</span><span class="sxs-lookup"><span data-stu-id="05ccb-122">Create EDI and AS2 artifacts</span></span>](../core/managing-edi-and-as2-solutions.md)

- [<span data-ttu-id="05ccb-123">Développement et la configuration des Solutions EDI BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="05ccb-123">Developing and Configuring BizTalk Server EDI Solutions</span></span>](../core/developing-and-configuring-biztalk-server-edi-solutions.md)

- [<span data-ttu-id="05ccb-124">Développement et la configuration des Solutions AS2 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="05ccb-124">Developing and Configuring BizTalk Server AS2 Solutions</span></span>](../core/developing-and-configuring-biztalk-server-as2-solutions.md)

-   [<span data-ttu-id="05ccb-125">Exemples EDI et AS2 SDK)</span><span class="sxs-lookup"><span data-stu-id="05ccb-125">EDI and AS2 SDK samples)</span></span>](../core/edi-and-as2-biztalk-server-samples-folder.md)  


 <span data-ttu-id="05ccb-126">**À l’aide de fichiers de liaison**</span><span class="sxs-lookup"><span data-stu-id="05ccb-126">**Using binding files**</span></span>  

- [<span data-ttu-id="05ccb-127">Utiliser des fichiers de liaison pour importer ou exporter - NEW dans BizTalk Server 2016</span><span class="sxs-lookup"><span data-stu-id="05ccb-127">Use binding files to import or export - NEW in BizTalk Server 2016</span></span>](../core/use-binding-files-to-import-or-export.md)  

-   [<span data-ttu-id="05ccb-128">Comment exporter des liaisons pour une Solution EDI AS2</span><span class="sxs-lookup"><span data-stu-id="05ccb-128">How to Export Bindings for an EDI-AS2 Solution</span></span>](../core/how-to-export-bindings-for-an-edi-as2-solution.md)  
  
-   [<span data-ttu-id="05ccb-129">Comment importer des liaisons pour une Solution EDI-AS2</span><span class="sxs-lookup"><span data-stu-id="05ccb-129">How to Import Bindings for an EDI-AS2 Solution</span></span>](../core/how-to-import-bindings-for-an-edi-as2-solution.md)  
  
-   [<span data-ttu-id="05ccb-130">Personnalisation des fichiers de liaison</span><span class="sxs-lookup"><span data-stu-id="05ccb-130">Customizing Binding Files</span></span>](../core/customizing-binding-files.md)  


<span data-ttu-id="05ccb-131">**Surveiller et résoudre les problèmes**</span><span class="sxs-lookup"><span data-stu-id="05ccb-131">**Monitor and troubleshoot**</span></span>

- [<span data-ttu-id="05ccb-132">Surveillance des Solutions EDI et AS2</span><span class="sxs-lookup"><span data-stu-id="05ccb-132">Monitoring EDI and AS2 Solutions</span></span>](../core/monitoring-edi-and-as2-solutions.md)

- [<span data-ttu-id="05ccb-133">Dépannage des Solutions EDI et AS2</span><span class="sxs-lookup"><span data-stu-id="05ccb-133">Troubleshooting EDI and AS2 Solutions</span></span>](../core/troubleshooting-edi-and-as2-solutions.md)
  
-   <span data-ttu-id="05ccb-134">Afficher les détails de l’interface utilisateur[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="05ccb-134">View UI details [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span> 
  
-   [<span data-ttu-id="05ccb-135">EDI et AS2 événements et erreurs</span><span class="sxs-lookup"><span data-stu-id="05ccb-135">EDI and AS2 Events and Errors</span></span>](../core/edi-and-as2-events-and-errors.md)
 


  
