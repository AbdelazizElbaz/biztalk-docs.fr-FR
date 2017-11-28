---
title: "Ajout d’artefacts à une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9b5e92e-2e55-41d7-9959-f62753bbeb04
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c08fa95dddad06efb2c51d93df56b757ae4caca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-artifacts-to-an-application"></a><span data-ttu-id="ad753-102">Ajout d’artefacts à une Application</span><span class="sxs-lookup"><span data-stu-id="ad753-102">Adding Artifacts to an Application</span></span>
<span data-ttu-id="ad753-103">Vous pouvez ajouter et configurer des artefacts tels que de l’envoi et ports de réception, orchestrations et les emplacements de réception, à l’aide de l’Administration de la console.</span><span class="sxs-lookup"><span data-stu-id="ad753-103">You can add and configure artifacts, such as send and receive ports, receive locations, and orchestrations, by using the Administration console.</span></span> <span data-ttu-id="ad753-104">Vous pouvez également générer des fichiers de liaison et les ajouter à l’application si vous souhaitez appliquer diverses liaisons pour les différents environnements que vous allez importer l’application dans.</span><span class="sxs-lookup"><span data-stu-id="ad753-104">You can also generate binding files and add them to the application if you want to apply different bindings for the different environments that you will import the application into.</span></span>  
  
 <span data-ttu-id="ad753-105">Vous pouvez ajouter d’autres (en général, non - BizTalk Server) des artefacts tels que les scripts, les certificats et les fichiers Lisezmoi, à l’application sous le nœud de ressources.</span><span class="sxs-lookup"><span data-stu-id="ad753-105">You can add additional (typically non-BizTalk Server) artifacts, such as scripts, certificates, and Readme files, to the application under the Resources node.</span></span> <span data-ttu-id="ad753-106">Pour ce faire, utilisez la console d’Administration ou de BTSTask.</span><span class="sxs-lookup"><span data-stu-id="ad753-106">To do so, use the Administration console or BTSTask.</span></span>  
  
 <span data-ttu-id="ad753-107">Pour plus d’informations sur les artefacts, consultez [comment créer ou ajouter un artefact](http://go.microsoft.com/fwlink/?LinkID=154724) (http://go.Microsoft.com/fwlink/?) LinkID = 154724), [la gestion des artefacts](http://go.microsoft.com/fwlink/?LinkID=154725) (http://go.Microsoft.com/fwlink/?) LinkID = 154725) et [fichiers de liaison et déploiement d’applications](http://go.microsoft.com/fwlink/?LinkID=154726) (http://go.Microsoft.com/fwlink/?) LinkID = 154726).</span><span class="sxs-lookup"><span data-stu-id="ad753-107">For more information about artifacts, see [How to Create or Add an Artifact](http://go.microsoft.com/fwlink/?LinkID=154724) (http://go.microsoft.com/fwlink/?LinkID=154724), [Managing Artifacts](http://go.microsoft.com/fwlink/?LinkID=154725) (http://go.microsoft.com/fwlink/?LinkID=154725) and [Binding Files and Application Deployment](http://go.microsoft.com/fwlink/?LinkID=154726) (http://go.microsoft.com/fwlink/?LinkID=154726).</span></span>  
  
## <a name="factoring-artifacts-into-multiple-biztalk-applications"></a><span data-ttu-id="ad753-108">Factorisation des artefacts dans plusieurs Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="ad753-108">Factoring Artifacts into Multiple BizTalk Applications</span></span>  
 <span data-ttu-id="ad753-109">Pendant le processus de déploiement, vous pouvez avoir déployé vos assemblys dans une seule application à des fins pratiques.</span><span class="sxs-lookup"><span data-stu-id="ad753-109">During the development process, you may have deployed your assemblies into a single application for convenience.</span></span> <span data-ttu-id="ad753-110">Pour diverses raisons, vous pouvez être amené à factoriser les artefacts dans plusieurs applications avant de les déployer en production.</span><span class="sxs-lookup"><span data-stu-id="ad753-110">For various reasons, you may want to factor the artifacts into multiple applications before they are deployed into production.</span></span>  
  
 <span data-ttu-id="ad753-111">Avant de déployer, vous devez effectuer une analyse approfondie de la conception d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="ad753-111">Before deploying, you should perform an in-depth analysis of the factoring of an assembly.</span></span> <span data-ttu-id="ad753-112">Déterminer si vous ne devez effectuer aucune factorisation, factorisation complète ou factorisation Optimal.</span><span class="sxs-lookup"><span data-stu-id="ad753-112">Determine whether you should perform No factoring, Full factoring, or Optimal factoring.</span></span>  
  
 <span data-ttu-id="ad753-113">**Aucun factorisation**</span><span class="sxs-lookup"><span data-stu-id="ad753-113">**No Factoring**</span></span>  
  
 <span data-ttu-id="ad753-114">Tous les artefacts BizTalk sont dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="ad753-114">All BizTalk artifacts are in one assembly.</span></span> <span data-ttu-id="ad753-115">Cela est très facile à comprendre et à déployer, mais fournit moins de flexibilité.</span><span class="sxs-lookup"><span data-stu-id="ad753-115">This is the easiest to understand and deploy, but provides the least amount of flexibility.</span></span>  
  
 <span data-ttu-id="ad753-116">**Factorisation complète**</span><span class="sxs-lookup"><span data-stu-id="ad753-116">**Full Factoring**</span></span>  
  
 <span data-ttu-id="ad753-117">Chaque artefact BizTalk est dans son propre assembly.</span><span class="sxs-lookup"><span data-stu-id="ad753-117">Each BizTalk artifact is in its own assembly.</span></span> <span data-ttu-id="ad753-118">Cela offre davantage de souplesse, mais il est plus complexe à déployer et à comprendre.</span><span class="sxs-lookup"><span data-stu-id="ad753-118">This provides the most flexibility, but is the most complex to deploy and understand.</span></span>  
  
 <span data-ttu-id="ad753-119">**Factorisation optimal**</span><span class="sxs-lookup"><span data-stu-id="ad753-119">**Optimal Factoring**</span></span>  
  
 <span data-ttu-id="ad753-120">Factorisation optimal se situe entre non factorisation et factorisation complète basée sur une analyse approfondie de vos applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ad753-120">Optimal factoring falls between No Factoring and Full Factoring based on in-depth analysis of your BizTalk applications.</span></span> <span data-ttu-id="ad753-121">Outre le contrôle de version, cela permet que plus facilement implémentent votre conception de l’hôte BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ad753-121">In addition to versioning, this allows you to more easily implement your BizTalk host design.</span></span> <span data-ttu-id="ad753-122">Cela est possible en recherchant des relations entre les artefacts BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ad753-122">This is achieved by looking for relationships among BizTalk artifacts.</span></span> <span data-ttu-id="ad753-123">Si possible, placez les artefacts qui sont toujours gérées dans le même assembly.</span><span class="sxs-lookup"><span data-stu-id="ad753-123">If possible, put artifacts that are always versioned together in the same assembly.</span></span> <span data-ttu-id="ad753-124">Si le contrôle de version indépendant des artefacts est requis, ils doivent être mis dans des assemblys différents.</span><span class="sxs-lookup"><span data-stu-id="ad753-124">If independent versioning of the artifacts is required, then they must be put in different assemblies.</span></span> <span data-ttu-id="ad753-125">C’est le niveau de conception que vous souhaitez obtenir.</span><span class="sxs-lookup"><span data-stu-id="ad753-125">This is the level of factoring that you want to achieve.</span></span>