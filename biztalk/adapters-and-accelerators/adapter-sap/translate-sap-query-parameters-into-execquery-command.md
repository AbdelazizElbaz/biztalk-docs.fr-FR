---
title: "Paramètres de requête SAP se traduire par des commandes EXECQUERY dans mySAP l’adaptateur dans BizTalk | Documents Microsoft"
description: "Conseils pour traduire des requêtes SAP à EXECQUERY, avec des exemples"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8a545e20-2607-4946-a60d-0a227b86d093
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efb50db3e499970c0504f81467d382aee31c868f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="translate-sap-query-parameters-into-execquery-command"></a><span data-ttu-id="8d5cc-103">Paramètres de requête SAP se traduire par des commandes EXECQUERY</span><span class="sxs-lookup"><span data-stu-id="8d5cc-103">Translate SAP query parameters into EXECQUERY command</span></span>
<span data-ttu-id="8d5cc-104">Explique comment les paramètres d’une requête se traduire par un texte de commande EXECQUERY.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-104">Explains how the parameters of a query translate into an EXECQUERY command text.</span></span> <span data-ttu-id="8d5cc-105">Cette rubrique utilise l’exemple d’une requête personnalisée SAP, ZQUERY_TST_NEW.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-105">This topic uses the example of a custom SAP query, ZQUERY_TST_NEW.</span></span>  
  
## <a name="open-the-query-in-sap-gui"></a><span data-ttu-id="8d5cc-106">Ouvrir la requête dans l’interface utilisateur graphique SAP</span><span class="sxs-lookup"><span data-stu-id="8d5cc-106">Open the Query in SAP GUI</span></span>  
 <span data-ttu-id="8d5cc-107">Effectuez les opérations suivantes pour ouvrir la requête dans SAP.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-107">Perform the following steps to open the query in SAP.</span></span> <span data-ttu-id="8d5cc-108">Les étapes décrites ici sont pour les requêtes ZQUERY_TST_NEW et sont spécifiques aux versions SAP.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-108">The steps provided here are for ZQUERY_TST_NEW query and are specific to SAP versions.</span></span>  
  
1.  <span data-ttu-id="8d5cc-109">Exécutez la transaction SQ01.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-109">Run the transaction SQ01.</span></span>  
  
2.  <span data-ttu-id="8d5cc-110">Dans le **requête à partir du groupe d’utilisateurs** , cliquez sur **aperçu rapide**.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-110">In the **Query from User Group** page, click **Quick Viewer**.</span></span>  
  
3.  <span data-ttu-id="8d5cc-111">Dans le **aperçu rapide** page, dans le **aperçu** zone de texte, tapez `ZQUERY_TST_NEW`, puis cliquez sur **affichage**.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-111">In the **Quick Viewer** page, in the **Quick View** text box, type `ZQUERY_TST_NEW`, and then click **Display**.</span></span>  
  
4.  <span data-ttu-id="8d5cc-112">Dans le **aperçu rapide** , cliquez sur le **champs de sélection** onglet pour répertorier tous les paramètres dans la requête.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-112">In the **Quick Viewer** page, click the **Selection fields** tab to list all the parameters in the query.</span></span>  
  
     <span data-ttu-id="8d5cc-113">La figure suivante montre tous les paramètres dans la définition de requête.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-113">The following figure shows all the parameters in the query definition.</span></span>  
  
     <span data-ttu-id="8d5cc-114">![Liste de paramètres pour une requête SAP](../../adapters-and-accelerators/adapter-sap/media/sap-query-param-types.gif "sap_query_param_types")</span><span class="sxs-lookup"><span data-stu-id="8d5cc-114">![List of parameters for an SAP query](../../adapters-and-accelerators/adapter-sap/media/sap-query-param-types.gif "sap_query_param_types")</span></span>  
  
5.  <span data-ttu-id="8d5cc-115">Cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-115">Click **Execute**.</span></span> <span data-ttu-id="8d5cc-116">La page suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-116">The following page is displayed.</span></span>  
  
     <span data-ttu-id="8d5cc-117">![Fournir des valeurs de paramètre pour une requête SAP](../../adapters-and-accelerators/adapter-sap/media/sap-query-all-params.gif "sap_query_all_params")</span><span class="sxs-lookup"><span data-stu-id="8d5cc-117">![Provide parameter values for an SAP query](../../adapters-and-accelerators/adapter-sap/media/sap-query-all-params.gif "sap_query_all_params")</span></span>  
  
6.  <span data-ttu-id="8d5cc-118">Cliquez sur les flèches jaunes pour définir chaque paramètre.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-118">Click the yellow arrows to define each parameter.</span></span> <span data-ttu-id="8d5cc-119">Vous pouvez soit définir des valeurs spécifiques autorisée/non autorisée, ou vous pouvez définir une plage de valeurs autorisée/non autorisée.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-119">You can either define specific allowable/non-allowable values or you can define a range of allowable/non-allowable values.</span></span>  <span data-ttu-id="8d5cc-120">La syntaxe EXECQUERY doit être spécifiée selon les valeurs configurées dans l’interface utilisateur graphique SAP pour chaque paramètre.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-120">The EXECQUERY syntax must be specified based on the values configured in the SAP GUI for each parameter.</span></span>  
  
 <span data-ttu-id="8d5cc-121">La section suivante fournit une explication sur la façon dont les valeurs sont définies dans l’interface GUI SAP, et comment ces valeurs traduites en syntaxe EXECQUERY.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-121">The next section provides an explanation about how the values are defined in the SAP GUI and how those values translate to EXECQUERY syntax.</span></span>  
  
## <a name="frame-an-execquery-syntax"></a><span data-ttu-id="8d5cc-122">Une syntaxe EXECQUERY de frame</span><span class="sxs-lookup"><span data-stu-id="8d5cc-122">Frame an EXECQUERY Syntax</span></span>  
 <span data-ttu-id="8d5cc-123">Voyons ce que la syntaxe EXECQUERY ressemble à selon les valeurs de paramètre définies dans la définition de requête.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-123">Let’s look at what the EXECQUERY syntax looks like based on the parameter values defined in the query definition.</span></span> <span data-ttu-id="8d5cc-124">Pour comprendre cela, nous allons montrer des exemples de la façon dont les valeurs configurées pour le premier paramètre, **nombre à deux chiffres**, traduire les **ZQUERY_TST_NEW** requête.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-124">To understand this, we’ll show examples of how the values configured for the first parameter, **Two digit number**, translate to the  **ZQUERY_TST_NEW** query.</span></span>  
  
 <span data-ttu-id="8d5cc-125">Tout d’abord, supposons que les valeurs dans le **unique ourbes** onglet (avec un point vert) sont définies comme indiqué dans la capture d’écran suivante :</span><span class="sxs-lookup"><span data-stu-id="8d5cc-125">First, let’s assume the values in the **Single vals** tab (with a green dot) are defined as shown in the following screenshot:</span></span>  
  
 <span data-ttu-id="8d5cc-126">![Liste de valeurs de paramètre qu’une requête peut accepter](../../adapters-and-accelerators/adapter-sap/media/sap-query-param-val.gif "sap_query_param_val")</span><span class="sxs-lookup"><span data-stu-id="8d5cc-126">![List of parameter values that a query can take](../../adapters-and-accelerators/adapter-sap/media/sap-query-param-val.gif "sap_query_param_val")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d5cc-127">Cette boîte de dialogue s’affiche après avoir cliqué sur la flèche jaune dans la **nombre à deux chiffres** paramètre.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-127">This dialog box appears after you click the yellow arrow against the **Two digit number** parameter.</span></span>  
  
 <span data-ttu-id="8d5cc-128">Dans ce cas, la syntaxe EXECQUERY ressemble à :</span><span class="sxs-lookup"><span data-stu-id="8d5cc-128">In such a case, the EXECQUERY syntax looks like:</span></span>  
  
```  
EXECQUERY ZQUERY_TST_NEW @USERGROUP='mygroup', @P1 = '2', @P1 = '3', @P1 = '5'  
```  
  
 <span data-ttu-id="8d5cc-129">Pour la même requête, en plus des valeurs dans le **unique ourbes** onglet (avec un point vert), vous pouvez également avoir des valeurs le **unique ourbes** onglet (avec un point rouge), défini comme suit :</span><span class="sxs-lookup"><span data-stu-id="8d5cc-129">For the same query, in addition to the values in the **Single vals** tab (with a green dot), you can also have the values in the **Single vals** tab (with a red dot) defined as following:</span></span>  
  
 <span data-ttu-id="8d5cc-130">![Liste de valeurs de paramètre qu’une requête ne peut pas accepter](../../adapters-and-accelerators/adapter-sap/media/2af88a57-4ff6-4bcc-8961-0f25dbfb8166.gif "2af88a57-4ff6-4bcc-8961-0f25dbfb8166")</span><span class="sxs-lookup"><span data-stu-id="8d5cc-130">![List of parameter values that a query cannot take](../../adapters-and-accelerators/adapter-sap/media/2af88a57-4ff6-4bcc-8961-0f25dbfb8166.gif "2af88a57-4ff6-4bcc-8961-0f25dbfb8166")</span></span>  
  
 <span data-ttu-id="8d5cc-131">Dans ce cas, la syntaxe EXECQUERY ressemble à :</span><span class="sxs-lookup"><span data-stu-id="8d5cc-131">In such a case, EXECQUERY syntax looks like:</span></span>  
  
```  
EXECQUERY ZQUERY_TST_NEW @USERGROUP='mygroup', @P1 = '2', @P1 = '3', @P1 = '5', NOT @P1 = '6', NOT @P1 = '8'  
```  
  
 <span data-ttu-id="8d5cc-132">Maintenant, si vous ajoutez des valeurs à la **plages** onglet (avec un point vert), comme indiqué dans la capture d’écran suivante :</span><span class="sxs-lookup"><span data-stu-id="8d5cc-132">Now, if you add values to the **Ranges** tab (with a green dot), like shown in the following screenshot:</span></span>  
  
 <span data-ttu-id="8d5cc-133">![Plage de valeurs de paramètre qu’une requête peut accepter](../../adapters-and-accelerators/adapter-sap/media/74907c7d-5a7a-4a2d-a614-6a835eca1764.gif "74907c7d-5a7a-4a2d-a614-6a835eca1764")</span><span class="sxs-lookup"><span data-stu-id="8d5cc-133">![Range of parameter values that a query can take](../../adapters-and-accelerators/adapter-sap/media/74907c7d-5a7a-4a2d-a614-6a835eca1764.gif "74907c7d-5a7a-4a2d-a614-6a835eca1764")</span></span>  
  
 <span data-ttu-id="8d5cc-134">la syntaxe EXECQUERY ressemble à :</span><span class="sxs-lookup"><span data-stu-id="8d5cc-134">the EXECQUERY syntax looks like:</span></span>  
  
```  
EXECQUERY ZQUERY_TST_NEW @USERGROUP='mygroup', @P1 = '2', @P1 = '3', @P1 = '5', NOT @P1 = '6', NOT @P1 = '8', @P1 BETWEEN '2' and '5'  
```  
  
 <span data-ttu-id="8d5cc-135">De même, si vous ajoutez des valeurs à la **plages** onglet (avec un point rouge), comme indiqué dans la capture d’écran suivante :</span><span class="sxs-lookup"><span data-stu-id="8d5cc-135">Similarly, if you add values to the **Ranges** tab (with a red dot), like shown in the following screenshot:</span></span>  
  
 <span data-ttu-id="8d5cc-136">![Plage de valeurs de paramètre qu’une requête ne peut pas accepter](../../adapters-and-accelerators/adapter-sap/media/ccc6a7bb-bc47-4325-8b58-094201f791bf.gif "ccc6a7bb-bc47-4325-8b58-094201f791bf")</span><span class="sxs-lookup"><span data-stu-id="8d5cc-136">![Range of parameter values that a query cannot take](../../adapters-and-accelerators/adapter-sap/media/ccc6a7bb-bc47-4325-8b58-094201f791bf.gif "ccc6a7bb-bc47-4325-8b58-094201f791bf")</span></span>  
  
 <span data-ttu-id="8d5cc-137">la syntaxe EXECQUERY ressemble à :</span><span class="sxs-lookup"><span data-stu-id="8d5cc-137">the EXECQUERY syntax looks like:</span></span>  
  
```  
EXECQUERY ZQUERY_TST_NEW @USERGROUP='mygroup', @P1 = '2', @P1 = '3', @P1 = '5', NOT @P1 = '6', NOT @P1 = '8', @P1 BETWEEN '2' and '5', NOT @P1 BETWEEN '6' AND '8'  
```  
  
 <span data-ttu-id="8d5cc-138">Pour plus de simplicité et de compréhension, cette rubrique traite uniquement sur le premier paramètre, **nombre à deux chiffres**.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-138">For simplicity and understanding, this topic only talks about the first parameter, **Two digit number**.</span></span> <span data-ttu-id="8d5cc-139">Vous pouvez utiliser des méthodes semblables pour déterminer comment les valeurs définies pour les autres paramètres traduire en une syntaxe EXECQUERY.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-139">You can use similar methods to determine how values defined for other parameters translate into an EXECQUERY syntax.</span></span>  
  
