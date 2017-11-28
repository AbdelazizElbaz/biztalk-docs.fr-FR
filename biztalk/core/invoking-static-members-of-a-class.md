---
title: "Appel des membres statiques d’une classe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a51171c-8de0-45dd-8659-f674cf27acbe
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2128bf6cb71c773cd31be497765e39b0d7815b4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoking-static-members-of-a-class"></a><span data-ttu-id="c3fa4-102">Appel de membres statiques d'une classe</span><span class="sxs-lookup"><span data-stu-id="c3fa4-102">Invoking Static Members of a Class</span></span>
<span data-ttu-id="c3fa4-103">Par défaut, le moteur de règles exige que vous déclariez une instance d'une classe .NET pour exécuter une stratégie appelant un membre statique de cette classe.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-103">By default, the rule engine requires you to assert an instance of a .NET class to execute a policy that invokes a static member of the .NET class.</span></span> <span data-ttu-id="c3fa4-104">Vous pouvez modifier ce comportement en modifiant la valeur de la **StaticSupport** clé de Registre sous **HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0** à une des valeurs dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-104">You can modify this behavior by changing the value of the **StaticSupport** registry key under **HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0** to one of the values in the following table.</span></span>  
  
|<span data-ttu-id="c3fa4-105">Valeur de registre StaticSupport</span><span class="sxs-lookup"><span data-stu-id="c3fa4-105">StaticSupport registry value</span></span>|<span data-ttu-id="c3fa4-106">Comportement du moteur de règles</span><span class="sxs-lookup"><span data-stu-id="c3fa4-106">Rule engine behavior</span></span>|  
|----------------------------------|--------------------------|  
|<span data-ttu-id="c3fa4-107">0</span><span class="sxs-lookup"><span data-stu-id="c3fa4-107">0</span></span>|<span data-ttu-id="c3fa4-108">Valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-108">Default value.</span></span> <span data-ttu-id="c3fa4-109">Le moteur de règles suit le modèle de BizTalk Server 2004, selon lequel la méthode statique est appelée uniquement lorsqu'une instance de la classe .NET est déclarée.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-109">The rule engine follows the BizTalk Server 2004 model, where the static method is called only when an instance of the .NET class is asserted.</span></span>|  
|<span data-ttu-id="c3fa4-110">1</span><span class="sxs-lookup"><span data-stu-id="c3fa4-110">1</span></span>|<span data-ttu-id="c3fa4-111">Aucune instance d'objet n'est requise.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-111">An object instance is not required.</span></span> <span data-ttu-id="c3fa4-112">La méthode statique est appelée lors de l'évaluation ou de l'exécution de la règle.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-112">The static method is called when the rule is evaluated or executed.</span></span>|  
|<span data-ttu-id="c3fa4-113">2</span><span class="sxs-lookup"><span data-stu-id="c3fa4-113">2</span></span>|<span data-ttu-id="c3fa4-114">Aucune instance d'objet n'est requise.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-114">An object instance is not required.</span></span> <span data-ttu-id="c3fa4-115">La méthode statique est appelée au moment de la conversion de la stratégie si tous les paramètres sont constants.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-115">The static method is called at the policy translation time if all parameters are constant.</span></span> <span data-ttu-id="c3fa4-116">Les performances s'en trouvent optimisées car la méthode statique n'est appelée qu'une seule fois, et ce même si elle intervient dans plusieurs règles.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-116">This is a performance optimization because the static method is called only once even though it is used in multiple rules in conditions.</span></span> <span data-ttu-id="c3fa4-117">Notez que les méthodes statiques utilisées en tant qu'actions ne sont pas exécutées au moment de la conversion, à la différence des méthodes utilisées en tant que paramètres.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-117">Note that static methods used as actions will not be executed at the translation time, but static methods used as parameters may be executed.</span></span>|  
  
## <a name="adding-and-changing-the-staticsupport-registry-key"></a><span data-ttu-id="c3fa4-118">Ajout et modification de la clé de registre StaticSupport</span><span class="sxs-lookup"><span data-stu-id="c3fa4-118">Adding and Changing the StaticSupport Registry Key</span></span>  
 <span data-ttu-id="c3fa4-119">Si vous ne voyez pas le **StaticSupport** clé de Registre sous **HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**, vous devez l’ajouter en effectuant les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-119">If you do not see the **StaticSupport** registry key under **HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**, you should add it by performing the following steps.</span></span>  
  
 <span data-ttu-id="c3fa4-120">**Pour ajouter la clé de Registre StaticSupport**</span><span class="sxs-lookup"><span data-stu-id="c3fa4-120">**To add the StaticSupport registry key**</span></span>  
  
1.  <span data-ttu-id="c3fa4-121">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **RegEdit**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-121">Click **Start**, click **Run**, type **RegEdit**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="c3fa4-122">Développez **HKEY_LOCAL_MACHINE**, développez **logiciel**, développez **Microsoft**, développez **BusinessRules**, puis sélectionnez **3.0**.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-122">Expand **HKEY_LOCAL_MACHINE**, expand **Software**, expand **Microsoft**, expand **BusinessRules**, and then select **3.0**.</span></span>  
  
3.  <span data-ttu-id="c3fa4-123">Dans le volet droit, cliquez sur, pointez sur **nouveau**, puis cliquez sur **valeur DWORD**.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-123">In the right pane, right-click, point to **New**, and then click **DWORD value**.</span></span>  
  
4.  <span data-ttu-id="c3fa4-124">Pour **nom**, type **StaticSupport**.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-124">For **Name**, type **StaticSupport**.</span></span>  
  
 <span data-ttu-id="c3fa4-125">Si le **StaticSupport** clé de Registre existe déjà, et vous devez modifier sa valeur, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-125">If the **StaticSupport** registry key already exists, and you need to change its value, perform the following steps.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c3fa4-126">Si BizTalk est installé sur un ordinateur 64 bits, vous pouvez alors ajouter **StaticSupport** clé de Registre à l’aide d’une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="c3fa4-126">If BizTalk is installed on a 64-bit machine, then you can add **StaticSupport** registry key using either of the following options:</span></span>  
>   
>  -   <span data-ttu-id="c3fa4-127">Regardez sous HKLM\Software\Wow6432Node\Microsoft\BusinessRules\3.0.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-127">You need to look under HKLM\Software\Wow6432Node\Microsoft\BusinessRules\3.0.</span></span> <span data-ttu-id="c3fa4-128">Si cette clé existe, vous pouvez alors ajouter **StaticSupport** ici.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-128">If this key exists, then you can add **StaticSupport** here.</span></span>  
> -   <span data-ttu-id="c3fa4-129">Une autre option consiste à placer **StaticSupport** dans les **.exe.config de BTNTsvc [64]** de fichiers, comme ici tous les paramètres de remplacement Nouveautés dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-129">Another option is to put **StaticSupport** in the **BTNTsvc[64].exe.config** file, as any settings here override what's in the Registry.</span></span>  <span data-ttu-id="c3fa4-130">Par ailleurs, certains peuvent avancer l’argument que l’utilisation de cette option est préférable étant donné qu’elle permet d’isoler la modification du comportement par défaut à BizTalk uniquement, tandis que les paramètres du Registre sont communs au système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-130">Further, one can also make the argument that this option is preferred since it isolates the change in default behavior to BizTalk only, whereas Registry settings are global to the Operating System.</span></span>  
  
 <span data-ttu-id="c3fa4-131">**Pour modifier la valeur de la clé de Registre StaticSupport**</span><span class="sxs-lookup"><span data-stu-id="c3fa4-131">**To change the value of the StaticSupport registry key**</span></span>  
  
1.  <span data-ttu-id="c3fa4-132">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **RegEdit**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-132">Click **Start**, click **Run**, type **RegEdit**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="c3fa4-133">Développez **HKEY_LOCAL_MACHINE**, développez **logiciel**, développez **Microsoft**, développez **BusinessRules**, puis développez **3.0**.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-133">Expand **HKEY_LOCAL_MACHINE**, expand **Software**, expand **Microsoft**, expand **BusinessRules**, and then expand **3.0**.</span></span>  
  
3.  <span data-ttu-id="c3fa4-134">Double-cliquez sur le **StaticSupport** Registre de clé, ou faites un clic droit, puis cliquez **modifier**.</span><span class="sxs-lookup"><span data-stu-id="c3fa4-134">Double-click the **StaticSupport** registry key, or right-click it and then click **Modify**.</span></span>