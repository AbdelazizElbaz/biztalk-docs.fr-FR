---
title: GetUserData | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c243555b-109f-47e3-8084-ab13a8e22ac5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57bc0ffcefc00e9fae20c7b2c8449c21c549b377
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getuserdata"></a><span data-ttu-id="29820-102">GetUserData</span><span class="sxs-lookup"><span data-stu-id="29820-102">GetUserData</span></span>
<span data-ttu-id="29820-103">Transmet les données de l'utilisateur actuel sur la pile.</span><span class="sxs-lookup"><span data-stu-id="29820-103">Pushes the current user data onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29820-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29820-104">Syntax</span></span>  
  
```  
  
<wf:Operation Name="GetUserData" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29820-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="29820-105">Parameters</span></span>  
 <span data-ttu-id="29820-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="29820-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="29820-107">Valeur transmise</span><span class="sxs-lookup"><span data-stu-id="29820-107">Pushed Value</span></span>  
 <span data-ttu-id="29820-108">Chaîne contenant les données de l'utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="29820-108">String containing the current user data.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29820-109">Notes</span><span class="sxs-lookup"><span data-stu-id="29820-109">Remarks</span></span>  
 <span data-ttu-id="29820-110">Cette opération n'est pas valide dans un filtre.</span><span class="sxs-lookup"><span data-stu-id="29820-110">This operation is not valid inside of a filter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29820-111"> Exemple</span><span class="sxs-lookup"><span data-stu-id="29820-111">Example</span></span>  
 <span data-ttu-id="29820-112">L'exemple suivant contient une expression de mise à jour pour l'élément de données « UserData » à l'aide de l'opération `GetUserData`.</span><span class="sxs-lookup"><span data-stu-id="29820-112">The following sample contains an update expression for the data item "UserData" using the `GetUserData` operation.</span></span>  
  
```  
<ic:Update DataItemName="UserData" Type="NVARCHAR">  
  <ic:Expression>  
    <wf:Operation Name="GetUserData" />  
  </ic:Expression>  
</ic:Update>  
```