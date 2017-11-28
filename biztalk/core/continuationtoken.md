---
title: ContinuationToken | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d4911fc-c6fb-4628-9177-bd723d4d8ebc
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54cf9b9326661925f2d55bacd2fb22d02f565f89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="continuationtoken"></a><span data-ttu-id="45aea-102">ContinuationToken</span><span class="sxs-lookup"><span data-stu-id="45aea-102">ContinuationToken</span></span>
<span data-ttu-id="45aea-103">Un jeton de liaison permet de corréler des informations hétérogènes au sein de l'infrastructure BAM.</span><span class="sxs-lookup"><span data-stu-id="45aea-103">A continuation token is used to correlate heterogeneous information within the BAM infrastructure.</span></span> <span data-ttu-id="45aea-104">Prenons l'exemple d'un processus d'entreprise qui construit les types de messages suivants :</span><span class="sxs-lookup"><span data-stu-id="45aea-104">Consider a business process that constructs the following types of messages:</span></span>  
  
-   <span data-ttu-id="45aea-105">bon de commande identifié par un numéro de bon de commande ;</span><span class="sxs-lookup"><span data-stu-id="45aea-105">Purchase order identified by a purchase order number</span></span>  
  
-   <span data-ttu-id="45aea-106">ordre d'achat identifié par un numéro d'ordre d'achat ;</span><span class="sxs-lookup"><span data-stu-id="45aea-106">Sales order identified by a sales order number</span></span>  
  
-   <span data-ttu-id="45aea-107">bordereau d'expédition identifié par un numéro de bordereau d'expédition.</span><span class="sxs-lookup"><span data-stu-id="45aea-107">Shipping order identified by a shipping order number</span></span>  
  
 <span data-ttu-id="45aea-108">Dans ce processus, il existe trois identificateurs importants : acheter order ID, ID de commande et d’expédition des ID de commande.</span><span class="sxs-lookup"><span data-stu-id="45aea-108">In this process, there are three important identifiers: purchase order ID, sales order ID and shipping order ID.</span></span> <span data-ttu-id="45aea-109">Chacun de ces identificateurs signale un événement important dans la durée de vie de l’ordre d’origine, mais ils ne peuvent pas être corrélés directement.</span><span class="sxs-lookup"><span data-stu-id="45aea-109">Each of these identifiers signals an important event in the lifetime of the original order, but they cannot be directly correlated.</span></span> <span data-ttu-id="45aea-110">Pour suivre les événements associés à un bon de commande, les informations communes aux messages doivent être identifiées pour aider l'infrastructure de suivi BAM à corréler les événements avec précision.</span><span class="sxs-lookup"><span data-stu-id="45aea-110">To track events related to a purchase order, the information that is common between the messages must be identified to help the BAM tracking infrastructure accurately correlate the events.</span></span>  
  
## <a name="format"></a><span data-ttu-id="45aea-111">Format</span><span class="sxs-lookup"><span data-stu-id="45aea-111">Format</span></span>  
 <span data-ttu-id="45aea-112">Un jeton de liaison est constitué d'un élément d'expression et d'une ou plusieurs opérations :</span><span class="sxs-lookup"><span data-stu-id="45aea-112">A continuation token consists of an expression element and one or more operations:</span></span>  
  
```  
<ic:ContinuationToken>  
  <ic:Expression>  
    <!-- Operations -->  
  </ic:Expression>  
</ic:ContinuationToken>  
```  
  
## <a name="remarks"></a><span data-ttu-id="45aea-113">Notes</span><span class="sxs-lookup"><span data-stu-id="45aea-113">Remarks</span></span>  
 <span data-ttu-id="45aea-114">Les opérations communes suivantes ne sont pas autorisées dans les expressions ContinuationToken :</span><span class="sxs-lookup"><span data-stu-id="45aea-114">The following common operations are not allowed in ContinuationToken expressions:</span></span>  
  
-   <span data-ttu-id="45aea-115">And</span><span class="sxs-lookup"><span data-stu-id="45aea-115">And</span></span>  
  
-   <span data-ttu-id="45aea-116">Égal à</span><span class="sxs-lookup"><span data-stu-id="45aea-116">Equals</span></span>  
  
 <span data-ttu-id="45aea-117">[L'en-tête de section des opérations dans WF/WCF doit avoir un graphique similaire et d'autres graphiques au besoin]</span><span class="sxs-lookup"><span data-stu-id="45aea-117">[Operations section header in WF/WCF should have similar chart and other charts as needed]</span></span>  
  
## <a name="example"></a><span data-ttu-id="45aea-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="45aea-118">Example</span></span>  
 <span data-ttu-id="45aea-119">Dans cet exemple, un jeton de liaison pour un processus WF est extrait du flux de travail à l'aide de `GetWorkflowProperty`.</span><span class="sxs-lookup"><span data-stu-id="45aea-119">In this example, a continuation token for a WF process is retrieved from the workflow by using `GetWorkflowProperty`.</span></span> <span data-ttu-id="45aea-120">Ici le développeur a décidé de prendre en charge la continuation dans le flux de travail en utilisant du code personnalisé, probablement parce que le processus d'identification du jeton de liaison implique plusieurs expressions et peut reposer sur des données externes.</span><span class="sxs-lookup"><span data-stu-id="45aea-120">Here the developer decided to provide support for continuation in the workflow by using custom code, probably because the process for determining the continuation token involves more than two or three expressions and may rely on external data.</span></span>  
  
```  
<ic:ContinuationToken>  
  <ic:Expression>  
    <wf:Operation Name="GetWorkflowProperty">  
      <wf:Argument>ContinuationToken</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:ContinuationToken>  
```  
  
 <span data-ttu-id="45aea-121">Vous pouvez choisir d'inclure des fonctionnalités similaires dans vos nouvelles applications WF ou WCF ou, si le jeton est simple à établir à l'aide d'opérations d'expression, vous pouvez éviter d'écrire du code supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="45aea-121">You may choose to provide similar functionality in your new WF or WCF applications or, if the token is easy to establish using expression operations, you can avoid writing additional code.</span></span>  
  
 <span data-ttu-id="45aea-122">L’exemple suivant établit un jeton de liaison pour un processus WCF à l’aide un **XPath** opération à récupérer le numéro de carte de crédit dans le message actuel et le **constante** et  **concaténer** operations pour ajouter la chaîne « CID_ » au numéro récupéré :</span><span class="sxs-lookup"><span data-stu-id="45aea-122">The following example establishes a continuation token for a WCF process by using an **XPath** operation to retrieve the credit card number from the current message and the **constant** and **concatenate** operations to prepend the string "CID_" to the retrieved number:</span></span>  
  
```  
<ic:ContinuationToken>  
  <ic:Expression>  
    <ic:Operation Name="Constant">  
      <ic:Argument>CID_</ic:Argument>  
    </ic:Operation>  
    <wcf:Operation Name="XPath">  
      <wcf:Argument>//Purchase/Payment/CreditCardNumber</wcf:Argument>  
    </wcf:Operation>  
    <ic:Operation Name="Concatenate" />  
  </ic:Expression>  
</ic:ContinuationToken>  
```  
  
## <a name="see-also"></a><span data-ttu-id="45aea-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45aea-123">See Also</span></span>  
 [<span data-ttu-id="45aea-124">Élément OnEvent de l’intercepteur</span><span class="sxs-lookup"><span data-stu-id="45aea-124">Interceptor OnEvent Element</span></span>](../core/interceptor-onevent-element.md)