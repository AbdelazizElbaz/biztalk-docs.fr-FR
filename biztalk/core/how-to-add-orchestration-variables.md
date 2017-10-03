---
title: "Comment ajouter des Variables d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: orchestrations, variables
ms.assetid: c387cd56-5443-4de2-bbda-be34b95cbe71
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4416534bdd73e8ae6eeeca28165ebc62c11bfc92
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-orchestration-variables"></a><span data-ttu-id="69afd-102">Ajout de variables d'orchestration</span><span class="sxs-lookup"><span data-stu-id="69afd-102">How to Add Orchestration Variables</span></span>
<span data-ttu-id="69afd-103">La fenêtre Vue Orchestration vous permet de gérer les propriétés d’une orchestration (également appelé **Service** propriétés), paramètres, ports, messages et autres variables.</span><span class="sxs-lookup"><span data-stu-id="69afd-103">The Orchestration View window enables you to manage an orchestration's properties (also known as **Service** properties), parameters, ports, messages, and other variables.</span></span> <span data-ttu-id="69afd-104">En plus des ports et des messages, vous pouvez créer des variables entières, des variables booléennes, des variables de chaînes ou des variables d'une classe .NET.</span><span class="sxs-lookup"><span data-stu-id="69afd-104">In addition to ports and messages, you can create integer variables, Boolean variables, string variables, or variables of a .NET class.</span></span>  
  
 <span data-ttu-id="69afd-105">Vous pouvez aussi utiliser la fenêtre Vue Orchestration pour gérer les variables appartenant à vos étendues.</span><span class="sxs-lookup"><span data-stu-id="69afd-105">You can also use the Orchestration View window to manage the variables that belong to your scopes.</span></span>  
  
### <a name="to-add-a-variable"></a><span data-ttu-id="69afd-106">Pour ajouter une variable</span><span class="sxs-lookup"><span data-stu-id="69afd-106">To add a variable</span></span>  
  
1.  <span data-ttu-id="69afd-107">Dans la fenêtre Vue Orchestration, cliquez sur le **Variables** dossier, puis cliquez sur **nouvelle Variable**.</span><span class="sxs-lookup"><span data-stu-id="69afd-107">In the Orchestration View window, right-click the **Variables** folder and then click **New Variable**.</span></span>  
  
     <span data-ttu-id="69afd-108">Le **Variables** dossier se développe, s’il était réduit et une nouvelle variable est ajoutée.</span><span class="sxs-lookup"><span data-stu-id="69afd-108">The **Variables** folder expands, if collapsed, and a new variable is added.</span></span>  
  
2.  <span data-ttu-id="69afd-109">Nommez la variable en tapant un nom dans la propriété Identificateur de la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="69afd-109">Name the variable by typing a name in the Identifier property in the Properties window.</span></span>  
  
3.  <span data-ttu-id="69afd-110">Associez cette variable à un type, tel qu'une classe .NET.</span><span class="sxs-lookup"><span data-stu-id="69afd-110">Associate the variable with a type, such as a .NET class.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="69afd-111">Le **Types** liste déroulante contienne les types de variables prédéfinies suivantes : **booléenne**, **octets**, **datetime**,  **décimal**, **double**, **int16**, **int32**, **int64**, **sbyte** , **unique**, **chaîne**, **timespan**, **uint16**, **uint32**et **uint64**.</span><span class="sxs-lookup"><span data-stu-id="69afd-111">The **Types** drop-down list contains the following predefined variable types: **boolean**, **byte**, **datetime**, **decimal**, **double**, **int16**, **int32**, **int64**, **sbyte**, **single**, **string**, **timespan**, **uint16**, **uint32**, and **uint64**.</span></span> <span data-ttu-id="69afd-112">Vous pouvez également accéder aux classes et les types de données .NET en sélectionnant  **\<.NET classe.. >**, ce qui permet d’afficher le **sélectionner le Type d’artefact** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="69afd-112">You can also access .NET data types and classes by selecting **\<.NET Class...>**, which brings up the **Select Artifact Type** dialog box.</span></span>  
  
4.  <span data-ttu-id="69afd-113">Si vous sélectionnez un type de variable prédéfini, vous avez la possibilité de spécifier une valeur initiale pour la variable.</span><span class="sxs-lookup"><span data-stu-id="69afd-113">If you select a predefined variable type, you have the option of specifying an initial value for the variable.</span></span> <span data-ttu-id="69afd-114">Dans la fenêtre Propriétés, définissez la **valeur initiale** propriété.</span><span class="sxs-lookup"><span data-stu-id="69afd-114">In the Properties window, set the **Initial Value** property.</span></span>  
  
     <span data-ttu-id="69afd-115">Sinon, si le type sélectionné est une classe .NET, vous avez la possibilité d'utiliser un constructeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="69afd-115">Otherwise, if the selected type is a .NET class, you have the option of using a default constructor.</span></span> <span data-ttu-id="69afd-116">Dans la fenêtre Propriétés, définissez la propriété suivante :</span><span class="sxs-lookup"><span data-stu-id="69afd-116">In the Properties window, set the following property:</span></span>  
  
    |<span data-ttu-id="69afd-117">Propriété</span><span class="sxs-lookup"><span data-stu-id="69afd-117">Property</span></span>|<span data-ttu-id="69afd-118"> Description</span><span class="sxs-lookup"><span data-stu-id="69afd-118">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="69afd-119">**Utiliser le constructeur par défaut**</span><span class="sxs-lookup"><span data-stu-id="69afd-119">**Use Default Constructor**</span></span>|<span data-ttu-id="69afd-120">Si un constructeur par défaut est disponible pour une classe .NET, cette propriété détermine s'il sera appelé lorsque vous utiliserez la variable pour la première fois :</span><span class="sxs-lookup"><span data-stu-id="69afd-120">If a default constructor is available for a .NET class, this property determines whether the default constructor will be called when you use the variable for the first time:</span></span><br /><br /> <span data-ttu-id="69afd-121">True - Le constructeur par défaut sera appelé.</span><span class="sxs-lookup"><span data-stu-id="69afd-121">True—The default constructor will be called.</span></span> <span data-ttu-id="69afd-122">Il s'agit de la valeur par défaut lorsqu'un constructeur par défaut est disponible.</span><span class="sxs-lookup"><span data-stu-id="69afd-122">This is the default value when a default constructor is available.</span></span><br /><br /> <span data-ttu-id="69afd-123">False - Le constructeur par défaut ne sera pas appelé ; vous devez appeler un constructeur dans une expression ou réaliser une assignation pour la variable avant de pouvoir l'utiliser dans votre orchestration.</span><span class="sxs-lookup"><span data-stu-id="69afd-123">False—The default constructor will not be called; you must call a constructor in an expression or make an assignment to the variable before you can use it in your orchestration.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="69afd-124">Si le constructeur par défaut requiert des paramètres d’entrée, vous pouvez définir **utiliser le constructeur par défaut** à **False** , puis appelez le constructeur d’une **affectation** forme ; pour exemple, `myVariable = myNamespace.myClass (param1, param2)`.</span><span class="sxs-lookup"><span data-stu-id="69afd-124">If the default constructor requires input parameters, you can set **Use Default Constructor** to **False** and then call the constructor from an **Assignment** shape; for example, `myVariable = myNamespace.myClass (param1, param2)`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="69afd-125">Lorsque vous ajouterez une variable à l'orchestration, avant qu'elle ne soit entièrement définie, vous verrez apparaître des points d'exclamation dans cette dernière.</span><span class="sxs-lookup"><span data-stu-id="69afd-125">When you add a variable to the orchestration, before it is fully defined, you will see exclamation marks in the orchestration.</span></span> <span data-ttu-id="69afd-126">Si vous supprimez cette variable avant qu'elle ne soit entièrement définie et que les points d'exclamation apparaissent toujours, vous pouvez obliger l'orchestration à supprimer ces points en créant puis supprimant un paramètre d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="69afd-126">If you delete this variable before it is fully defined and the exclamation marks still appear in the orchestration, you can force the orchestration to remove these exclamation marks by creating and then deleting an orchestration parameter.</span></span>  
  
### <a name="to-remove-a-variable"></a><span data-ttu-id="69afd-127">Suppression d'une variable</span><span class="sxs-lookup"><span data-stu-id="69afd-127">To remove a variable</span></span>  
  
-   <span data-ttu-id="69afd-128">Dans la fenêtre Vue Orchestration, cliquez sur la variable que vous souhaitez supprimer, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="69afd-128">In the Orchestration View window, right-click the variable you want to remove and then click **Delete**.</span></span>