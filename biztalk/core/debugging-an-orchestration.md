---
title: "Débogage d’une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging, Orchestration Debugger
- debugging, orchestrations
- Orchestration Debugger, about Orchestration Debugger
- Orchestrations Debugger
- orchestrations, debugging
- debugging, HAT
- HAT, debugging
ms.assetid: aae99cfd-d3dd-41c8-ae7a-b2733352cd69
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c231513ad75520fcadd88e5dd7d88104ddeeced5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="debugging-an-orchestration"></a><span data-ttu-id="7da20-102">Débogage d'une orchestration</span><span class="sxs-lookup"><span data-stu-id="7da20-102">Debugging an Orchestration</span></span>
<span data-ttu-id="7da20-103">Le débogueur de l'orchestration permet de suivre l'activité d'une seule instance de l'orchestration pour chaque forme.</span><span class="sxs-lookup"><span data-stu-id="7da20-103">The Orchestration Debugger enables you to track the activity of a single orchestration instance on a shape-by-shape basis.</span></span> <span data-ttu-id="7da20-104">Il présente un rendu de l'orchestration créée dans le Concepteur d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="7da20-104">It displays a rendered view of the orchestration created in the Orchestration Designer.</span></span>  
  
 <span data-ttu-id="7da20-105">Vous accédez au débogueur orchestration dans la page Présentation du groupe de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="7da20-105">You access the Orchestration Debugger in the Group Overview Page in the BizTalk Server Administration Console.</span></span>  <span data-ttu-id="7da20-106">Pour ce faire, utilisez la sortie d'une requête de suivi au travers d'un menu contextuel accessible en cliquant avec le bouton droit sur une instance de message ou de service associée à un type d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="7da20-106">This is done from the output of a tracking query through a shortcut menu by right-clicking any service or message instance associated with an orchestration type.</span></span> <span data-ttu-id="7da20-107">Une fois dans cette page, vous avez la possibilité de basculer entre l'affichage Flux message et le débogueur orchestration.</span><span class="sxs-lookup"><span data-stu-id="7da20-107">Once you're in i this page, you can switch back and forth between the Orchestration Debugger and the Message Flow view.</span></span>  
  
 <span data-ttu-id="7da20-108">Le débogueur de l'orchestration permet d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="7da20-108">The Orchestration Debugger provides the following functionality:</span></span>  
  
-   <span data-ttu-id="7da20-109">afficher un rendu de l'orchestration dans lequel vous pouvez revoir chaque étape du traitement de cette orchestration ;</span><span class="sxs-lookup"><span data-stu-id="7da20-109">Displays a rendered view of the orchestration in which you can replay each processing step for that particular orchestration.</span></span>  
  
-   <span data-ttu-id="7da20-110">définir des points d'arrêt avant n'importe quelle forme de l'orchestration et continuer l'exécution ;</span><span class="sxs-lookup"><span data-stu-id="7da20-110">Enables you to set breakpoints before any orchestration shape and continue execution.</span></span>  
  
-   <span data-ttu-id="7da20-111">consulter des données de message et des variables spécifiques ;</span><span class="sxs-lookup"><span data-stu-id="7da20-111">Enables you to look at specific variables and message data.</span></span>  
  
-   <span data-ttu-id="7da20-112">activer automatiquement toutes les options de suivi pour une instance d'orchestration particulière quand cette dernière est ouverte dans le débogueur de l'orchestration ;</span><span class="sxs-lookup"><span data-stu-id="7da20-112">Automatically enables all of the tracking options for a particular orchestration instance when that instance opens in the Orchestration Debugger.</span></span>  
  
-   <span data-ttu-id="7da20-113">continuer, reprendre en mode de débogage et terminer une instance d'orchestration particulière.</span><span class="sxs-lookup"><span data-stu-id="7da20-113">It gives you the ability to continue, resume in debug, and terminate the particular orchestration instance.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7da20-114">Quand vous annulez le déploiement d'un assembly, la base de données conserve les options de suivi et les informations sur les points d'arrêt pour cet assembly.</span><span class="sxs-lookup"><span data-stu-id="7da20-114">When you undeploy an assembly, the database maintains the tracking options and breakpoint information for the undeployed assembly.</span></span> <span data-ttu-id="7da20-115">Si, par la suite, vous déployez le même assembly, ces options de suivi et ces informations de points d'arrêt sont restaurées.</span><span class="sxs-lookup"><span data-stu-id="7da20-115">If you subsequently deploy the same assembly, the options and breakpoint information for that assembly are restored.</span></span>  
  
 <span data-ttu-id="7da20-116">Les deux modes disponibles lors de l'utilisation du débogueur de l'orchestration sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="7da20-116">The two modes for using the Orchestration Debugger are:</span></span>  
  
-   [<span data-ttu-id="7da20-117">Mode de création de rapports dans le débogueur de l’Orchestration</span><span class="sxs-lookup"><span data-stu-id="7da20-117">Reporting Mode in Orchestration Debugger</span></span>](../core/reporting-mode-in-orchestration-debugger.md)  
  
-   [<span data-ttu-id="7da20-118">Mode interactif dans le débogueur de l’Orchestration</span><span class="sxs-lookup"><span data-stu-id="7da20-118">Interactive Mode in Orchestration Debugger</span></span>](../core/interactive-mode-in-orchestration-debugger.md)  
  
 <span data-ttu-id="7da20-119">Les fonctionnalités varient selon l'état du service.</span><span class="sxs-lookup"><span data-stu-id="7da20-119">The capabilities differ depending on the state of the service.</span></span> <span data-ttu-id="7da20-120">Vous pouvez effectuer un débogage interactif en appelant une instance de service dont l'état est Point d'arrêt, à partir de n'importe quelle vue.</span><span class="sxs-lookup"><span data-stu-id="7da20-120">You can perform interactive debugging by invoking any service instance currently in the In Breakpoint state, from any view.</span></span> <span data-ttu-id="7da20-121">Pour plus d’informations sur le débogage d’une orchestration, consultez [comment appeler le débogueur d’Orchestration et les vues de flux de Message](../core/how-to-invoke-the-orchestration-debugger-and-the-message-flow-views.md).</span><span class="sxs-lookup"><span data-stu-id="7da20-121">For information about debugging an orchestration, see [How to Invoke the Orchestration Debugger and the Message Flow Views](../core/how-to-invoke-the-orchestration-debugger-and-the-message-flow-views.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7da20-122">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7da20-122">In This Section</span></span>  
  
-   [<span data-ttu-id="7da20-123">Interface utilisateur du débogueur d’orchestration</span><span class="sxs-lookup"><span data-stu-id="7da20-123">Orchestration Debugger User Interface</span></span>](../core/orchestration-debugger-user-interface.md)  
  
-   [<span data-ttu-id="7da20-124">Considérations sur l’utilisation du débogueur de l’Orchestration</span><span class="sxs-lookup"><span data-stu-id="7da20-124">Considerations when Using Orchestration Debugger</span></span>](../core/considerations-when-using-orchestration-debugger.md)  
  
-   [<span data-ttu-id="7da20-125">Utilisation de la vue débogueur Orchestration</span><span class="sxs-lookup"><span data-stu-id="7da20-125">Working with the Orchestration Debugger View</span></span>](../core/working-with-the-orchestration-debugger-view.md)