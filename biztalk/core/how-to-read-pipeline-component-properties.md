---
title: "La lecture des propriétés du composant de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: pipeline components, properties
ms.assetid: 10b1c59c-7ba4-453f-9aaa-1ce9ecf31fac
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19a6ccbcbe7588a0a75b4dbe6bf821a19fab965c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-read-pipeline-component-properties"></a><span data-ttu-id="0f7c9-102">La lecture des propriétés du composant de Pipeline</span><span class="sxs-lookup"><span data-stu-id="0f7c9-102">How to Read Pipeline Component Properties</span></span>
<span data-ttu-id="0f7c9-103">La fenêtre Propriétés contient deux sections pour les composants : les propriétés générales et les propriétés du composant.</span><span class="sxs-lookup"><span data-stu-id="0f7c9-103">The Properties window contains two sections for components: general properties and component properties.</span></span> <span data-ttu-id="0f7c9-104">Les propriétés générales sont communes à tous les composants, bien que leurs valeurs changent d’un composant à l’autre.</span><span class="sxs-lookup"><span data-stu-id="0f7c9-104">General properties are common to all components, though their values change between components.</span></span>  
  
### <a name="to-read-the-general-properties-for-a-pipeline-component"></a><span data-ttu-id="0f7c9-105">Pour lire les propriétés générales d’un composant de pipeline</span><span class="sxs-lookup"><span data-stu-id="0f7c9-105">To read the general properties for a pipeline component</span></span>  
  
1.  <span data-ttu-id="0f7c9-106">Déplacez le composant de pipeline dans une étape de pipeline ou sélectionnez un composant s’il existe déjà dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="0f7c9-106">Drag the pipeline component into a stage of the pipeline, or select a component if it already exists in the pipeline.</span></span>  
  
2.  <span data-ttu-id="0f7c9-107">Dans la fenêtre Propriétés, dans le **général** section, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="0f7c9-107">In the Properties window, in the **General** section, do the following.</span></span>  
  
    |<span data-ttu-id="0f7c9-108">Utiliser</span><span class="sxs-lookup"><span data-stu-id="0f7c9-108">Use this</span></span>|<span data-ttu-id="0f7c9-109">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="0f7c9-109">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="0f7c9-110">**Nom**</span><span class="sxs-lookup"><span data-stu-id="0f7c9-110">**Name**</span></span>|<span data-ttu-id="0f7c9-111">Indique le nom du composant.</span><span class="sxs-lookup"><span data-stu-id="0f7c9-111">Indicates the component name.</span></span>|  
    |<span data-ttu-id="0f7c9-112">**Assembly**</span><span class="sxs-lookup"><span data-stu-id="0f7c9-112">**Assembly**</span></span>|<span data-ttu-id="0f7c9-113">Indique l'assembly du composant et les informations .NET qui lui sont associées.</span><span class="sxs-lookup"><span data-stu-id="0f7c9-113">Indicates the assembly and associated .NET information for the component.</span></span>|  
    |<span data-ttu-id="0f7c9-114">**Description**</span><span class="sxs-lookup"><span data-stu-id="0f7c9-114">**Description**</span></span>|<span data-ttu-id="0f7c9-115">Indique le nom convivial du composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="0f7c9-115">Indicates the friendly name of the pipeline component.</span></span>|  
    |<span data-ttu-id="0f7c9-116">**Géré**</span><span class="sxs-lookup"><span data-stu-id="0f7c9-116">**Managed**</span></span>|<span data-ttu-id="0f7c9-117">Indique si le composant de pipeline est géré.</span><span class="sxs-lookup"><span data-stu-id="0f7c9-117">Indicates whether the pipeline component is managed.</span></span> <span data-ttu-id="0f7c9-118">**Oui** si le composant est un composant .NET géré ; **Non** si le composant de pipeline est un composant COM.</span><span class="sxs-lookup"><span data-stu-id="0f7c9-118">**Yes** if the component is a .NET managed component; **No** if the pipeline component is a COM component.</span></span>|  
    |<span data-ttu-id="0f7c9-119">**Chemin d'accès**</span><span class="sxs-lookup"><span data-stu-id="0f7c9-119">**Path**</span></span>|<span data-ttu-id="0f7c9-120">Indique le chemin d’accès complet au composant .NET.</span><span class="sxs-lookup"><span data-stu-id="0f7c9-120">Indicates the fully qualified path to the .NET component.</span></span>|  
    |<span data-ttu-id="0f7c9-121">**Type**</span><span class="sxs-lookup"><span data-stu-id="0f7c9-121">**Type**</span></span>|<span data-ttu-id="0f7c9-122">Indique le type, l'assembly et les informations .NET associées du composant.</span><span class="sxs-lookup"><span data-stu-id="0f7c9-122">Indicates the component type, the assembly, and the associated .NET information for the component.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0f7c9-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f7c9-123">See Also</span></span>  
 <span data-ttu-id="0f7c9-124">[Configuration des composants de Pipeline natifs](../core/configuring-native-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="0f7c9-124">[Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md) </span></span>  
 [<span data-ttu-id="0f7c9-125">Création de Pipelines avec le Concepteur de Pipeline</span><span class="sxs-lookup"><span data-stu-id="0f7c9-125">Creating Pipelines with Pipeline Designer</span></span>](../core/creating-pipelines-with-pipeline-designer.md)