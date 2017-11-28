---
title: "Procédure : utiliser des Types de ports | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting, port types
- port types, deleting
- port types, Web
- port types, request-response
- orchestrations, ports
- port types, modifier
- port types
- ports, port types
- port types, one-way
ms.assetid: 78ac731e-c330-4888-a9ee-10523fef8ed0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e3b4307cb9d48679ae1b90f7e02dd0288ec2957
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-work-with-port-types"></a><span data-ttu-id="f51fe-102">L’utilisation des Types de ports</span><span class="sxs-lookup"><span data-stu-id="f51fe-102">How to Work with Port Types</span></span>
<span data-ttu-id="f51fe-103">Un type de port est composé d'un modèle de communication, d'un ensemble d'opérations (requêtes ou réponses) et des types de messages dont ces opérations peuvent s'occuper.</span><span class="sxs-lookup"><span data-stu-id="f51fe-103">A port type consists of a communication pattern, a set of operations (requests or responses), and the message types that those operations can work on.</span></span> <span data-ttu-id="f51fe-104">Le modèle peut être de type unidirectionnel ou requête-réponse (bidirectionnel) et toutes les opérations définies sur ce type de port doivent utiliser le même modèle.</span><span class="sxs-lookup"><span data-stu-id="f51fe-104">The pattern can be either one-way or request-response (two-way), and all operations defined on that port type must use the same pattern.</span></span> <span data-ttu-id="f51fe-105">Notez que les types de ports sont indépendants de la direction : direction est spécifiée sur chaque port.</span><span class="sxs-lookup"><span data-stu-id="f51fe-105">Note that port types are direction-agnostic: direction is specified on individual ports.</span></span>  
  
 <span data-ttu-id="f51fe-106">L’étendue d’un type de port est définie par le **modificateur de Type** propriété.</span><span class="sxs-lookup"><span data-stu-id="f51fe-106">The scope of a port type is defined by the **Type Modifier** property.</span></span> <span data-ttu-id="f51fe-107">Le type de port peut être public, privé ou interne.</span><span class="sxs-lookup"><span data-stu-id="f51fe-107">A port type can be public, private, or internal.</span></span> <span data-ttu-id="f51fe-108">S'il est public, il est visible par toute personne interagissant avec l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="f51fe-108">If it is public, it is visible to anyone interacting with the orchestration.</span></span> <span data-ttu-id="f51fe-109">S'il est privé, il est visible par les autres orchestrations appartenant aux mêmes projet et nom d'espaces.</span><span class="sxs-lookup"><span data-stu-id="f51fe-109">If it is private, it is visible to other orchestrations within the same project and namespace.</span></span> <span data-ttu-id="f51fe-110">S'il est interne, il n'est visible que dans le projet.</span><span class="sxs-lookup"><span data-stu-id="f51fe-110">If it is internal, the port type is visible only within the project.</span></span> <span data-ttu-id="f51fe-111">Dans la mesure où une définition de type de port inclut des types de messages, l'étendue du type de message doit englober celle de tout type de port l'utilisant.</span><span class="sxs-lookup"><span data-stu-id="f51fe-111">Since a port type definition includes message types, the scope of the message type must encompass that of any port type that uses it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f51fe-112">Un type de port peut être appliqué à n'importe quel nombre de ports.</span><span class="sxs-lookup"><span data-stu-id="f51fe-112">A port type can be applied to any number of ports.</span></span> <span data-ttu-id="f51fe-113">Un port peut être considéré comme une instance d'un type de port.</span><span class="sxs-lookup"><span data-stu-id="f51fe-113">You can think of a port as an instance of a port type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f51fe-114">Un type de port ne comporte pas par essence une direction de communication ; la direction se définit sur chaque port.</span><span class="sxs-lookup"><span data-stu-id="f51fe-114">A port type does not inherently have a communication direction; you set direction on individual ports.</span></span>  
  
### <a name="to-add-a-request-response-port-type"></a><span data-ttu-id="f51fe-115">Pour ajouter un type de port de requête-réponse</span><span class="sxs-lookup"><span data-stu-id="f51fe-115">To add a request-response port type</span></span>  
  
1.  <span data-ttu-id="f51fe-116">Dans la fenêtre Vue Orchestration, cliquez sur **Types de ports** puis cliquez sur **Type de Port de requête-réponse nouveau**.</span><span class="sxs-lookup"><span data-stu-id="f51fe-116">In the Orchestration View window, right-click **Port Types** and then click **New Request-response Port Type**.</span></span>  
  
     <span data-ttu-id="f51fe-117">Le **Types de ports** nœud se développe, s’il était réduit et un nouveau type de port requête-réponse est ajouté avec une opération par défaut.</span><span class="sxs-lookup"><span data-stu-id="f51fe-117">The **Port Types** node expands, if collapsed, and a new request-response port type is added with one default operation.</span></span>  
  
2.  <span data-ttu-id="f51fe-118">Indiquez un nom pour le type de port.</span><span class="sxs-lookup"><span data-stu-id="f51fe-118">Specify a name for the port type.</span></span>  
  
3.  <span data-ttu-id="f51fe-119">Définissez une ou plusieurs opérations de port.</span><span class="sxs-lookup"><span data-stu-id="f51fe-119">Define one or more port operations.</span></span>  
  
     <span data-ttu-id="f51fe-120">Vous pouvez nommer vos opérations de port, mais si vous les sélectionnez à partir d'un autre projet, ils seront affichés uniquement en tant que « Requête » et « Réponse ».</span><span class="sxs-lookup"><span data-stu-id="f51fe-120">You can name your port operations, but when you are selecting them from another project, you will see them only as "Request" and "Response."</span></span> <span data-ttu-id="f51fe-121">Si vous sélectionnez une opération de port à partir d'un autre projet, vérifiez qu'elle possède le type de message correct.</span><span class="sxs-lookup"><span data-stu-id="f51fe-121">If you select a port operation from another project, verify that it has the correct message type.</span></span>  
  
### <a name="to-add-a-one-way-port-type"></a><span data-ttu-id="f51fe-122">Pour ajouter un type de port unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="f51fe-122">To add a one-way port type</span></span>  
  
1.  <span data-ttu-id="f51fe-123">Dans la fenêtre Vue Orchestration, cliquez sur **Types de ports** puis cliquez sur **nouveau Type de Port unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="f51fe-123">In the Orchestration View window, right-click **Port Types** and then click **New One-way Port Type**.</span></span>  
  
     <span data-ttu-id="f51fe-124">Le **Types de ports** nœud se développe, s’il était réduit et un nouveau type de port unidirectionnel est ajouté avec une opération par défaut.</span><span class="sxs-lookup"><span data-stu-id="f51fe-124">The **Port Types** node expands, if collapsed, and a new one-way port type is added with one default operation.</span></span>  
  
2.  <span data-ttu-id="f51fe-125">Indiquez un nom pour le type de port.</span><span class="sxs-lookup"><span data-stu-id="f51fe-125">Specify a name for the port type.</span></span>  
  
3.  <span data-ttu-id="f51fe-126">Définissez une ou plusieurs opérations de port.</span><span class="sxs-lookup"><span data-stu-id="f51fe-126">Define one or more port operations.</span></span>  
  
### <a name="to-add-a-web-port-type"></a><span data-ttu-id="f51fe-127">Pour ajouter un type de port Web</span><span class="sxs-lookup"><span data-stu-id="f51fe-127">To add a Web port type</span></span>  
  
-   <span data-ttu-id="f51fe-128">Ajoutez une référence de projet à un assembly contenant une classe proxy pour un service Web.</span><span class="sxs-lookup"><span data-stu-id="f51fe-128">Add a project reference to an assembly containing a proxy class for a Web service.</span></span> <span data-ttu-id="f51fe-129">Pour plus d’informations, consultez [création de Ports Web](../core/creating-web-ports.md).</span><span class="sxs-lookup"><span data-stu-id="f51fe-129">For more information, see [Creating Web Ports](../core/creating-web-ports.md).</span></span>  
  
### <a name="to-remove-a-port-type"></a><span data-ttu-id="f51fe-130">Pour supprimer un type de port</span><span class="sxs-lookup"><span data-stu-id="f51fe-130">To remove a port type</span></span>  
  
-   <span data-ttu-id="f51fe-131">Dans la fenêtre Vue Orchestration, cliquez sur le type de port à supprimer, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="f51fe-131">In the Orchestration View window, right-click the port type to delete, and then click **Delete**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f51fe-132">Si le type de port est utilisé, le fait de le supprimer aura une incidence sur la configuration des ports configurés pour l'utiliser.</span><span class="sxs-lookup"><span data-stu-id="f51fe-132">If the port type is in use, deleting it will impact the configuration of any ports that are configured to use it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f51fe-133">Les éléments apparaissant en lecture seule sont définis dans une autre orchestration.</span><span class="sxs-lookup"><span data-stu-id="f51fe-133">Items that appear as read-only are defined in another orchestration.</span></span>  
  
### <a name="to-set-the-type-modifier-for-a-port-type"></a><span data-ttu-id="f51fe-134">Pour définir le modificateur de type d'un type de port</span><span class="sxs-lookup"><span data-stu-id="f51fe-134">To set the type modifier for a port type</span></span>  
  
-   <span data-ttu-id="f51fe-135">Dans la fenêtre Propriétés, définissez la propriété suivante :</span><span class="sxs-lookup"><span data-stu-id="f51fe-135">In the Properties window, set the following property:</span></span>  
  
    |<span data-ttu-id="f51fe-136">Propriété</span><span class="sxs-lookup"><span data-stu-id="f51fe-136">Property</span></span>|<span data-ttu-id="f51fe-137"> Description</span><span class="sxs-lookup"><span data-stu-id="f51fe-137">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="f51fe-138">Modificateur de type</span><span class="sxs-lookup"><span data-stu-id="f51fe-138">Type Modifier</span></span>|<span data-ttu-id="f51fe-139">Détermine l'étendue du type de port :</span><span class="sxs-lookup"><span data-stu-id="f51fe-139">Determines the scope of the port type:</span></span><br /><br /> <span data-ttu-id="f51fe-140">Privé : l'accès à ce type de port est limité au module contenant.</span><span class="sxs-lookup"><span data-stu-id="f51fe-140">Private—Access to this port type is limited to the containing module.</span></span><br /><br /> <span data-ttu-id="f51fe-141">Public : l'accès à ce type de port n'est pas limité.</span><span class="sxs-lookup"><span data-stu-id="f51fe-141">Public—Access to this port type is not limited.</span></span><br /><br /> <span data-ttu-id="f51fe-142">Interne : l'accès à ce type de port est limité aux modules d'un même projet.</span><span class="sxs-lookup"><span data-stu-id="f51fe-142">Internal—Access to this port type is limited to modules within the same project.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f51fe-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f51fe-143">See Also</span></span>  
 <span data-ttu-id="f51fe-144">[Modèle de communication](../core/communication-pattern.md) </span><span class="sxs-lookup"><span data-stu-id="f51fe-144">[Communication Pattern](../core/communication-pattern.md) </span></span>  
 <span data-ttu-id="f51fe-145">[Comment exécuter l’Assistant Configuration du Port](../core/how-to-run-the-port-configuration-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="f51fe-145">[How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md) </span></span>  
 [<span data-ttu-id="f51fe-146">L’utilisation de Ports dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="f51fe-146">Using Ports in Orchestrations</span></span>](../core/using-ports-in-orchestrations.md)