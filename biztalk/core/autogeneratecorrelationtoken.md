---
title: AutoGenerateCorrelationToken | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a24357c9-34e5-4caa-b41c-19551cfe81f9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e396fd0b2c6153a5252d336b9af9c22bf9421fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="autogeneratecorrelationtoken"></a><span data-ttu-id="503b6-102">AutoGenerateCorrelationToken</span><span class="sxs-lookup"><span data-stu-id="503b6-102">AutoGenerateCorrelationToken</span></span>
<span data-ttu-id="503b6-103">Génère automatiquement un jeton de corrélation et le place sur la pile.</span><span class="sxs-lookup"><span data-stu-id="503b6-103">Automatically generates a correlation token and places it onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="503b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="503b6-104">Syntax</span></span>  
  
```  
  
<wcf:Operation Name="AutoGenerateCorrelationToken" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="503b6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="503b6-105">Parameters</span></span>  
 <span data-ttu-id="503b6-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="503b6-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="503b6-107">Valeur transmise</span><span class="sxs-lookup"><span data-stu-id="503b6-107">Pushed Value</span></span>  
 <span data-ttu-id="503b6-108">Chaîne contenant le jeton de corrélation.</span><span class="sxs-lookup"><span data-stu-id="503b6-108">String containing the correlation token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="503b6-109">Notes</span><span class="sxs-lookup"><span data-stu-id="503b6-109">Remarks</span></span>  
 <span data-ttu-id="503b6-110">Vous pouvez utiliser cette opération quand le message ne contient aucun jeton de corrélation, mais que vous voulez néanmoins corréler les informations d'une demande et d'une réponse.</span><span class="sxs-lookup"><span data-stu-id="503b6-110">This operation can be used when there is no correlation token present in the message but you still want to correlate the information from a request and a reply.</span></span> <span data-ttu-id="503b6-111">Vous pouvez les utiliser pour corréler une requête-réponse particulière du côté client ou service.</span><span class="sxs-lookup"><span data-stu-id="503b6-111">It can be used to correlate a particular request/reply on either the client or the service side.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="503b6-112">Si vous voulez corréler les données collectées par la requête et la réponse pour le client et le service (continuation), vous devez utiliser un ou plusieurs éléments de données de votre message.</span><span class="sxs-lookup"><span data-stu-id="503b6-112">If you want to correlate the data gathered by the request and the reply for both the client and the service (a continuation), you will need to use a data element or elements from your message.</span></span>  
  
## <a name="example"></a><span data-ttu-id="503b6-113"> Exemple</span><span class="sxs-lookup"><span data-stu-id="503b6-113">Example</span></span>  
 <span data-ttu-id="503b6-114">L'exemple suivant d'expression de corrélation dépend de `AutoGenerateCorrelationToken` pour générer un jeton de corrélation.</span><span class="sxs-lookup"><span data-stu-id="503b6-114">The following example correlation expression relies on the `AutoGenerateCorrelationToken` to generate a correlation token.</span></span>  
  
```  
<ic:CorrelationID>  
  <ic:Expression>            
    <wcf:Operation Name="AutoGenerateCorrelationToken"/>  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
## <a name="see-also"></a><span data-ttu-id="503b6-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="503b6-115">See Also</span></span>  
 [<span data-ttu-id="503b6-116">Opérations dans Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="503b6-116">Operations in Windows Communication Foundation</span></span>](../core/operations-in-windows-communication-foundation.md)