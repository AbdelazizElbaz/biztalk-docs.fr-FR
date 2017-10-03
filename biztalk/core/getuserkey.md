---
title: GetUserKey | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9353a7f0-9bbd-4cfa-92e6-ed2b86e3a88e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0701ff1df912cc113205bad573b6cebc0f02a13a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getuserkey"></a><span data-ttu-id="160aa-102">GetUserKey</span><span class="sxs-lookup"><span data-stu-id="160aa-102">GetUserKey</span></span>
<span data-ttu-id="160aa-103">Transmet la clé utilisateur actuelle sur la pile.</span><span class="sxs-lookup"><span data-stu-id="160aa-103">Pushes the current user key onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="160aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="160aa-104">Syntax</span></span>  
  
```  
  
<wf:Operation Name="GetUserKey" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="160aa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="160aa-105">Parameters</span></span>  
 <span data-ttu-id="160aa-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="160aa-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="160aa-107">Valeur transmise</span><span class="sxs-lookup"><span data-stu-id="160aa-107">Pushed Value</span></span>  
 <span data-ttu-id="160aa-108">Chaîne contenant la clé utilisateur actuelle.</span><span class="sxs-lookup"><span data-stu-id="160aa-108">String containing the current user key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="160aa-109">Notes</span><span class="sxs-lookup"><span data-stu-id="160aa-109">Remarks</span></span>  
 <span data-ttu-id="160aa-110">Cette opération est valide uniquement dans les points de suivi d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="160aa-110">This operation is valid only in user track points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="160aa-111"> Exemple</span><span class="sxs-lookup"><span data-stu-id="160aa-111">Example</span></span>  
 <span data-ttu-id="160aa-112">L'exemple suivant contient une expression de filtre d'événement qui donne le résultat `true` lorsque la clé utilisateur est égale à « DocumentUrl ».</span><span class="sxs-lookup"><span data-stu-id="160aa-112">The following sample contains an event filter expression that will evaluate to `true` when the user key is equal to "DocumentUrl".</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>DocumentUrl</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```