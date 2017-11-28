---
title: GetContextProperty2 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2554a210-cfb4-4b63-9afa-ffe2a853ba7b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f834bf1271f6706c332123d8b1835e0bd730f069
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getcontextproperty"></a><span data-ttu-id="0297b-102">GetContextProperty</span><span class="sxs-lookup"><span data-stu-id="0297b-102">GetContextProperty</span></span>
<span data-ttu-id="0297b-103">Transmet la propriété de contexte demandée sur la pile.</span><span class="sxs-lookup"><span data-stu-id="0297b-103">Pushes the requested context property onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0297b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0297b-104">Syntax</span></span>  
  
```  
  
<wf:Operation Name="GetContextProperty">  
  <wf:Argument>ContextPropertyName</wf:Argument>  
</wf:Operation>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0297b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0297b-105">Parameters</span></span>  
 <span data-ttu-id="0297b-106">L'un des noms de propriété de contexte suivants :</span><span class="sxs-lookup"><span data-stu-id="0297b-106">One of the following context property names:</span></span>  
  
|<span data-ttu-id="0297b-107">Nom de la propriété de contexte</span><span class="sxs-lookup"><span data-stu-id="0297b-107">Context property name</span></span>|<span data-ttu-id="0297b-108">Description</span><span class="sxs-lookup"><span data-stu-id="0297b-108">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="0297b-109">EventTime</span><span class="sxs-lookup"><span data-stu-id="0297b-109">EventTime</span></span>|<span data-ttu-id="0297b-110">Date et heure actuelles.</span><span class="sxs-lookup"><span data-stu-id="0297b-110">Current date and time.</span></span>|  
|<span data-ttu-id="0297b-111">InstanceId</span><span class="sxs-lookup"><span data-stu-id="0297b-111">InstanceId</span></span>|<span data-ttu-id="0297b-112">ID de l'instance de flux de travail</span><span class="sxs-lookup"><span data-stu-id="0297b-112">Workflow instance ID.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="0297b-113">Les noms des propriétés de contexte respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="0297b-113">The context property names are case-sensitive.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="0297b-114">Valeur transmise</span><span class="sxs-lookup"><span data-stu-id="0297b-114">Pushed Value</span></span>  
 <span data-ttu-id="0297b-115">Chaîne contenant la propriété de contexte demandée.</span><span class="sxs-lookup"><span data-stu-id="0297b-115">String containing the requested context property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0297b-116">Notes</span><span class="sxs-lookup"><span data-stu-id="0297b-116">Remarks</span></span>  
 <span data-ttu-id="0297b-117">L'heure est stockée au format UTC dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="0297b-117">Time is stored in UTC format inside of the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0297b-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="0297b-118">Example</span></span>  
 <span data-ttu-id="0297b-119">Dans l’exemple suivant, une expression pour l’extraction du **InstanceId** utilisé dans un bloc correlationID pour définir l’ID de corrélation.</span><span class="sxs-lookup"><span data-stu-id="0297b-119">In the following sample, an expression for pulling the **InstanceId** is used inside of a correlationID block to set the correlation ID.</span></span>  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <wf:Operation Name="GetContextProperty">  
      <wf:Argument>InstanceId</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
 <span data-ttu-id="0297b-120">Il s'agit d'un modèle d'utilisation courante de `GetContextProperty`.</span><span class="sxs-lookup"><span data-stu-id="0297b-120">This is a common use of `GetContextProperty`.</span></span>