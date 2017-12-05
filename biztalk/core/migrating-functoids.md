---
title: Migration des fonctoids | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functoids, migrating
- migrating, maps
- Migrating functoids, about Migrating functoids
- Migrating functoids
- Scripting functoids
- migrating, functoids
- migrating, Scripting functoids
ms.assetid: fc5b3ac9-28c6-41df-b779-15a8c3188528
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fac30a9b884bc769752623003d16e7089b140d4
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="migrating-functoids"></a><span data-ttu-id="805d7-102">Migration des fonctoids</span><span class="sxs-lookup"><span data-stu-id="805d7-102">Migrating Functoids</span></span>
<span data-ttu-id="805d7-103">Lorsque vous migrez un mappage à partir de versions précédentes de BizTalk Server à BizTalk Server, les fonctoids inclus dans le mappage sont également migrés.</span><span class="sxs-lookup"><span data-stu-id="805d7-103">When you migrate a map from previous versions of BizTalk Server to BizTalk Server, any functoids included in the map are also migrated.</span></span> <span data-ttu-id="805d7-104">Si les fonctoids que vous migrez n’incluent pas **script** fonctoids, aucune tâche de migration supplémentaires n’est nécessaires.</span><span class="sxs-lookup"><span data-stu-id="805d7-104">If the functoids you migrate do not include **Scripting** functoids, no additional migration tasks are required.</span></span> <span data-ttu-id="805d7-105">Toutefois si votre mappage comprend **script** fonctoids ou des fonctoids personnalisés, vous avez peut-être des étapes supplémentaires à effectuer.</span><span class="sxs-lookup"><span data-stu-id="805d7-105">However if your map includes **Scripting** functoids or custom functoids, you may have additional steps to perform.</span></span>  
  
 <span data-ttu-id="805d7-106">Dans les versions précédentes de BizTalk Server, tout le script personnalisé inclus dans un **script** fonctoid était écrit inline.</span><span class="sxs-lookup"><span data-stu-id="805d7-106">In previous versions of BizTalk Server, all custom script included with a **Scripting** functoid was written inline.</span></span> <span data-ttu-id="805d7-107">Autrement dit, lorsque vous créiez le fonctoid, tout le script appelé par le fonctoid lors de l’exécution était stocké avec le fonctoid.</span><span class="sxs-lookup"><span data-stu-id="805d7-107">That is, when you created the functoid, all the script the functoid called during run time was stored with the functoid.</span></span> <span data-ttu-id="805d7-108">Si vous souhaitez utiliser le même script avec un autre fonctoid, vous soit copié et collé à partir d’un **script** fonctoid à un autre, ou vous réécriviez le script à partir de zéro.</span><span class="sxs-lookup"><span data-stu-id="805d7-108">If you wanted to use the same script with a different functoid, you either copied and pasted it from one **Scripting** functoid to another, or you rewrote the script from scratch.</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="805d7-109"> copie les scripts inline existants avec les fonctoids lors de la migration d’un mappage.</span><span class="sxs-lookup"><span data-stu-id="805d7-109"> copies existing inline scripts with the functoids when you migrate a map.</span></span> <span data-ttu-id="805d7-110">Toutefois, tous les scripts ne fonctionnent pas correctement.</span><span class="sxs-lookup"><span data-stu-id="805d7-110">However, not all of the scripts may function correctly.</span></span> <span data-ttu-id="805d7-111">BizTalk Server utilise Visual Basic .NET et JScript .NET plutôt que le code VBScript et JScript utilisés dans les versions précédentes.</span><span class="sxs-lookup"><span data-stu-id="805d7-111">BizTalk Server uses Visual Basic .NET and JScript .NET rather than the VBScript and JScript used in previous versions.</span></span> <span data-ttu-id="805d7-112">Les versions .NET des langages incluent des modifications de la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="805d7-112">The .NET versions of the languages include some changes in syntax.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="805d7-113">Veillez à tester votre **script** fonctoids après la migration.</span><span class="sxs-lookup"><span data-stu-id="805d7-113">Be sure to test your **Scripting** functoids after migration.</span></span>  
  
 <span data-ttu-id="805d7-114">Vous devez réécrire les fonctoids personnalisés.</span><span class="sxs-lookup"><span data-stu-id="805d7-114">You will need to rewrite custom functoids.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="805d7-115">attend des fonctoids personnalisés à utiliser le .NET framework.</span><span class="sxs-lookup"><span data-stu-id="805d7-115"> expects custom functoids to use the .NET framework.</span></span> <span data-ttu-id="805d7-116">Il ne peut pas utiliser les anciens fonctoids personnalisés COM.</span><span class="sxs-lookup"><span data-stu-id="805d7-116">It cannot use the older, COM-based custom functoids.</span></span> <span data-ttu-id="805d7-117">Les fonctoids personnalisés peuvent être réécrits pour utiliser .NET framework.</span><span class="sxs-lookup"><span data-stu-id="805d7-117">Custom functoids can be rewritten to use the .NET framework.</span></span> <span data-ttu-id="805d7-118">Pour un exemple de code d’un fonctoid personnalisé, consultez [fonctoid personnalisé (exemple BizTalk Server)](../core/custom-functoid-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="805d7-118">For sample code of a custom functoid, see [Custom Functoid (BizTalk Server Sample)](../core/custom-functoid-biztalk-server-sample.md).</span></span>  
  
 <span data-ttu-id="805d7-119">Une alternative consiste à encapsuler la fonctionnalité du fonctoid personnalisé dans un assembly externe et appeler cet assembly via un **script** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="805d7-119">An alternative is to wrap the functionality of the custom functoid in an external assembly and call this assembly through a **Scripting** functoid.</span></span> <span data-ttu-id="805d7-120">La section suivante décrit ce processus.</span><span class="sxs-lookup"><span data-stu-id="805d7-120">The following section describes this process.</span></span>  
  
### <a name="to-migrate-your-custom-functoids"></a><span data-ttu-id="805d7-121">Pour migrer vos fonctoids personnalisés</span><span class="sxs-lookup"><span data-stu-id="805d7-121">To migrate your custom functoids</span></span>  
  
1.  <span data-ttu-id="805d7-122">Recréez la fonctionnalité du fonctoid dans un langage .NET, tel que Microsoft Visual Basic .NET, JScript .NET ou Microsoft Visual C# .NET.</span><span class="sxs-lookup"><span data-stu-id="805d7-122">Re-create the functionality of the functoid in a .NET language, such as Microsoft Visual Basic .NET, JScript .NET, or Microsoft Visual C# .NET.</span></span>  
  
2.  <span data-ttu-id="805d7-123">Créez un assembly pour contenir la nouvelle fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="805d7-123">Create an assembly to contain the new functionality.</span></span>  
  
3.  <span data-ttu-id="805d7-124">Enregistrez l’assembly dans le Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="805d7-124">Register the assembly in the global assembly cache (GAC).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="805d7-125">Pour l’enregistrement des assemblys dans le GAC, ils doivent être dotés d'un nom fort et signés.</span><span class="sxs-lookup"><span data-stu-id="805d7-125">To register assemblies in the global assembly cache, they must be strong named and signed.</span></span> <span data-ttu-id="805d7-126">Pour plus d'informations sur l’enregistrement des assemblys, voir « Global Assembly Cache » dans la collection combinée [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="805d7-126">For more information about registering assemblies, see "Global Assembly Cache" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Combined Collection.</span></span>  
  
4.  <span data-ttu-id="805d7-127">Créer une référence entre le mappage contenant le **script** fonctoid et l’assembly qui contient la fonctionnalité réécrite.</span><span class="sxs-lookup"><span data-stu-id="805d7-127">Create a reference between the map that contains the **Scripting** functoid and the assembly that contains the rewritten functionality.</span></span>  
  
5.  <span data-ttu-id="805d7-128">Configurer le **Script** propriété pour le **script** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="805d7-128">Configure the **Script** property for the **Scripting** functoid.</span></span> <span data-ttu-id="805d7-129">Cette propriété détermine quel script le **script** appelle fonctoid lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="805d7-129">This property determines what script the **Scripting** functoid calls during run time.</span></span> <span data-ttu-id="805d7-130">Vous devez faire correspondre la valeur de cette propriété avec le langage dans lequel vous avez converti votre script personnalisé.</span><span class="sxs-lookup"><span data-stu-id="805d7-130">You must match the value of this property to the language into which you converted your custom script.</span></span> <span data-ttu-id="805d7-131">Pour plus d’informations sur la configuration de la propriété de Script, consultez [modification des propriétés de fonctoid et les paramètres d’entrée](../core/editing-functoid-properties-and-input-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="805d7-131">For more information about how to configure the Script property, see [Editing Functoid Properties and Input Parameters](../core/editing-functoid-properties-and-input-parameters.md).</span></span> <span data-ttu-id="805d7-132">Consultez également [le fonctoid script](../core/scripting-functoid.md).</span><span class="sxs-lookup"><span data-stu-id="805d7-132">Also see [Scripting Functoid](../core/scripting-functoid.md).</span></span>  
  
6.  <span data-ttu-id="805d7-133">Générez le projet BizTalk qui contient le mappage avec le **script** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="805d7-133">Build the BizTalk project that contains the map with the **Scripting** functoid.</span></span>  
  
7.  <span data-ttu-id="805d7-134">Validez et testez le mappage.</span><span class="sxs-lookup"><span data-stu-id="805d7-134">Validate and test the map.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="805d7-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="805d7-135">See Also</span></span>  
 <span data-ttu-id="805d7-136">[Modification des propriétés des fonctoids et des paramètres d’entrée](../core/editing-functoid-properties-and-input-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="805d7-136">[Editing Functoid Properties and Input Parameters](../core/editing-functoid-properties-and-input-parameters.md) </span></span>  
 [<span data-ttu-id="805d7-137">Fonctoid Script</span><span class="sxs-lookup"><span data-stu-id="805d7-137">Scripting Functoid</span></span>](../core/scripting-functoid.md)