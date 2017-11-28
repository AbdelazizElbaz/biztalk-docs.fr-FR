---
title: GetContextProperty1 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8867c29-63de-4a13-9ef9-8c6ab8ea3443
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65b7ffffe4b21e3317b920ac50cdc27b12d708d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getcontextproperty"></a><span data-ttu-id="b4c51-102">GetContextProperty</span><span class="sxs-lookup"><span data-stu-id="b4c51-102">GetContextProperty</span></span>
<span data-ttu-id="b4c51-103">Transmet la propriété de contexte demandée sur la pile.</span><span class="sxs-lookup"><span data-stu-id="b4c51-103">Pushes the requested context property onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4c51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4c51-104">Syntax</span></span>  
  
```  
  
<wcf:Operation Name ="GetContextProperty">  
  <wcf:Argument>EventTime</wcf:Argument>  
</wcf:Operation>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4c51-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b4c51-105">Parameters</span></span>  
 <span data-ttu-id="b4c51-106">L'un des noms de propriété de contexte suivants :</span><span class="sxs-lookup"><span data-stu-id="b4c51-106">One of the following context property names:</span></span>  
  
|<span data-ttu-id="b4c51-107">Nom de la propriété de contexte</span><span class="sxs-lookup"><span data-stu-id="b4c51-107">Context property name</span></span>|<span data-ttu-id="b4c51-108">Description</span><span class="sxs-lookup"><span data-stu-id="b4c51-108">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="b4c51-109">EventTime</span><span class="sxs-lookup"><span data-stu-id="b4c51-109">EventTime</span></span>|<span data-ttu-id="b4c51-110">Date et heure actuelles.</span><span class="sxs-lookup"><span data-stu-id="b4c51-110">Current date and time.</span></span>|  
|<span data-ttu-id="b4c51-111">SessionId</span><span class="sxs-lookup"><span data-stu-id="b4c51-111">SessionId</span></span>|<span data-ttu-id="b4c51-112">ID de la session de workflow.</span><span class="sxs-lookup"><span data-stu-id="b4c51-112">Workflow session id.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="b4c51-113">Les noms des propriétés de contexte respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="b4c51-113">The context property names are case-sensitive.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="b4c51-114">Valeur transmise</span><span class="sxs-lookup"><span data-stu-id="b4c51-114">Pushed Value</span></span>  
 <span data-ttu-id="b4c51-115">Chaîne contenant la propriété de contexte demandée.</span><span class="sxs-lookup"><span data-stu-id="b4c51-115">String containing the requested context property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4c51-116">Notes</span><span class="sxs-lookup"><span data-stu-id="b4c51-116">Remarks</span></span>  
 <span data-ttu-id="b4c51-117">L'heure est stockée au format UTC dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="b4c51-117">Time is stored in UTC format inside of the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4c51-118"> Exemple</span><span class="sxs-lookup"><span data-stu-id="b4c51-118">Example</span></span>  
 <span data-ttu-id="b4c51-119">Dans l'exemple d'expression de mise à jour suivant, la date d'approbation est extraite en récupérant l'heure de l'événement actuel.</span><span class="sxs-lookup"><span data-stu-id="b4c51-119">In the following sample update expression, the approval date is retrieved by retrieving the event time of the current event.</span></span>  
  
```  
<ic:Update DataItemName ="Approval Date" Type ="DATETIME">  
  <ic:Expression>  
    <wcf:Operation Name ="GetContextProperty">  
      <wcf:Argument>EventTime</wcf:Argument>  
    </wcf:Operation>  
  </ic:Expression>  
</ic:Update>  
```  
  
 <span data-ttu-id="b4c51-120">Il s'agit d'un modèle d'utilisation courante de `GetContextProperty`.</span><span class="sxs-lookup"><span data-stu-id="b4c51-120">This is a common use of `GetContextProperty`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4c51-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4c51-121">See Also</span></span>  
 [<span data-ttu-id="b4c51-122">Opérations dans Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="b4c51-122">Operations in Windows Communication Foundation</span></span>](../core/operations-in-windows-communication-foundation.md)