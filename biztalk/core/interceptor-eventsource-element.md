---
title: "Élément EventSource de l’intercepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d78846c1-3984-43af-a13f-9d5c0a66d3b5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35b5cd6b2e872f689988f3d10d18df002f66d6a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interceptor-eventsource-element"></a><span data-ttu-id="11c25-102">Élément EventSource de l'intercepteur</span><span class="sxs-lookup"><span data-stu-id="11c25-102">Interceptor EventSource Element</span></span>
<span data-ttu-id="11c25-103">Le **EventSource** élément fournit des informations sur la source d’un ou plusieurs des événements qui apparaissent dans le fichier de configuration de l’intercepteur.</span><span class="sxs-lookup"><span data-stu-id="11c25-103">The **EventSource** element provides information about the source of one or more of the events appearing in the interceptor configuration file.</span></span> <span data-ttu-id="11c25-104">Outre un nom de source d'événements, vous devez indiquez la technologie ainsi qu'un manifeste pour la source.</span><span class="sxs-lookup"><span data-stu-id="11c25-104">In addition to an event source name, you need to indicate the technology and a manifest for the source.</span></span>  
  
## <a name="format"></a><span data-ttu-id="11c25-105">Format</span><span class="sxs-lookup"><span data-stu-id="11c25-105">Format</span></span>  
 <span data-ttu-id="11c25-106">L'élément `EventSource` dispose de trois attributs et peut comporter des éléments enfants selon l'élément incluant les schémas.</span><span class="sxs-lookup"><span data-stu-id="11c25-106">The `EventSource` element has three attributes and may or may not have child elements depending upon which schemas are included.</span></span> <span data-ttu-id="11c25-107">Par exemple, le schéma WCF WcfInterceptorConfiguration.xsd propose l'élément `NamespaceMapping`.</span><span class="sxs-lookup"><span data-stu-id="11c25-107">For example, the WCF schema WcfInterceptorConfiguration.xsd provides for the `NamespaceMapping` element.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11c25-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="11c25-108">Attributes</span></span>  
  
|<span data-ttu-id="11c25-109">Nom de l'attribut</span><span class="sxs-lookup"><span data-stu-id="11c25-109">Attribute name</span></span>|<span data-ttu-id="11c25-110"> Description</span><span class="sxs-lookup"><span data-stu-id="11c25-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="11c25-111">Nom</span><span class="sxs-lookup"><span data-stu-id="11c25-111">Name</span></span>|<span data-ttu-id="11c25-112">Nom de cette source d'événements.</span><span class="sxs-lookup"><span data-stu-id="11c25-112">Name for this event source.</span></span> <span data-ttu-id="11c25-113">Ce nom est utilisé par **OnEvent** entrées pour faire référence à la source.</span><span class="sxs-lookup"><span data-stu-id="11c25-113">This name is used by **OnEvent** entries to refer to the source.</span></span>|  
|<span data-ttu-id="11c25-114">Technologie</span><span class="sxs-lookup"><span data-stu-id="11c25-114">Technology</span></span>|<span data-ttu-id="11c25-115">Type de technologie hébergeant la source d'événements indiquée dans le manifeste.</span><span class="sxs-lookup"><span data-stu-id="11c25-115">Technology type hosting the event source indicated in the manifest.</span></span> <span data-ttu-id="11c25-116">Indiquez « WF » pour Windows Workflow Foundation et « WCF » pour Windows Communication Framework.</span><span class="sxs-lookup"><span data-stu-id="11c25-116">Use "WF" for Windows Workflow Foundation and "WCF" for Windows Communication Framework.</span></span>|  
|<span data-ttu-id="11c25-117">Manifeste</span><span class="sxs-lookup"><span data-stu-id="11c25-117">Manifest</span></span>|<span data-ttu-id="11c25-118">Nom de classe qualifié pour les assemblys du type à utiliser comme source d'événements.</span><span class="sxs-lookup"><span data-stu-id="11c25-118">Assembly-qualified class name of the type to use as an event source.</span></span> <span data-ttu-id="11c25-119">Par exemple, `TopNamespace.SubNameSpace.ContainingClass+NestedClass, MyAssembly, Version=1.3.0.0, Culture=neutral, PublicKeyToken=b17a5c561934e08`</span><span class="sxs-lookup"><span data-stu-id="11c25-119">For example, `TopNamespace.SubNameSpace.ContainingClass+NestedClass, MyAssembly, Version=1.3.0.0, Culture=neutral, PublicKeyToken=b17a5c561934e08`</span></span><br /><br /> <span data-ttu-id="11c25-120">Si vous ne disposez pas de jeton de clé publique, utilisez `PublicKeyToken=null`.</span><span class="sxs-lookup"><span data-stu-id="11c25-120">If you do not have a public key token, use `PublicKeyToken=null`.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="11c25-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="11c25-121">Example</span></span>  
 <span data-ttu-id="11c25-122">L’exemple suivant contient deux **EventSource** éléments, un ciblant WF et l’autre ciblant WCF.</span><span class="sxs-lookup"><span data-stu-id="11c25-122">The following example contains two **EventSource** elements, one targeting WF and one targeting WCF.</span></span>  
  
```  
<!-- WF -->  
<ic:EventSource Name="OrderWorkflow" Technology="WF" Manifest="SimpleWorkflow.OrderWorkflow, SimpleWorkflow, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
<!-- WCF -->  
<ic:EventSource Name="PurchaseService" Technology="WCF" Manifest="Service.IProcessPOContract, DuplexService, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
```