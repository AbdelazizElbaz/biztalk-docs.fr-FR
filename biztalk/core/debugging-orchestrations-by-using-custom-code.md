---
title: "Débogage des Orchestrations à l’aide de Code personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, debugging
- building, debugging
ms.assetid: 94e569fa-8dea-4027-abb5-37b4a8015621
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47f69fa635a90db90c461f75c300334ccc499b94
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="debugging-orchestrations-by-using-custom-code"></a><span data-ttu-id="8d082-102">Débogage des orchestrations à l'aide d'un code personnalisé</span><span class="sxs-lookup"><span data-stu-id="8d082-102">Debugging Orchestrations by using Custom Code</span></span>
<span data-ttu-id="8d082-103">Si votre orchestration va être testés dans un environnement de test ou si vous créez un prototype et que vous souhaitez modifier les valeurs des champs de message et des variables d’orchestration, vous pouvez écrire la sortie vers le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] console en utilisant le code suivant dans un  **Expression** forme :</span><span class="sxs-lookup"><span data-stu-id="8d082-103">If your orchestration is going to be exercised in a test environment or you are creating a prototype and want to modify the values of message fields and orchestration variables, you can write the output to the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] console by using the following code in an **Expression** shape:</span></span>  
  
```  
System.Diagnostics.Debug.WriteLine(iResult);  
```  
  
 <span data-ttu-id="8d082-104">Vous devez placer ce **Expression** forme immédiatement après la forme qui effectue l’opération, afin que vous puissiez sortir le résultat pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="8d082-104">You need to place this **Expression** shape immediately after the shape that performs the operation so that you can output the result for debugging.</span></span>  
  
 <span data-ttu-id="8d082-105">Il est également possible d'écrire un simple débogueur personnalisé. Pour ce faire, créez une DLL de débogage avec une classe contenant une méthode qui accepte en entrée un message au format défini dans votre orchestration et référencé dans la DLL de débogage.</span><span class="sxs-lookup"><span data-stu-id="8d082-105">Alternatively, you can write a simple custom debugger by creating a debugging DLL with a class that includes a method which takes as input a message with a format defined in your orchestration and referenced in the debug DLL.</span></span> <span data-ttu-id="8d082-106">Pour plus d’informations sur la transmission d’un message en tant que paramètre, consultez [comment utiliser des Expressions pour créer des objets et appeler des méthodes objet](../core/how-to-use-expressions-to-create-objects-and-call-object-methods.md).</span><span class="sxs-lookup"><span data-stu-id="8d082-106">For more information about passing a message as a parameter, see [How to Use Expressions to Create Objects and Call Object Methods](../core/how-to-use-expressions-to-create-objects-and-call-object-methods.md).</span></span>  
  
 <span data-ttu-id="8d082-107">Cette méthode peut afficher une boîte de dialogue de débogage qui contient une zone de liste ou une autre commande qui permet la modification des valeurs par l'utilisateur, regroupe le message modifié, puis le retransmet comme valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="8d082-107">This method can bring up a debug dialog that includes a combo box or other control to allow user modification of values, puts the edited message back together, and passes it back out as the return value.</span></span>  
  
 <span data-ttu-id="8d082-108">Définir une variable booléenne pour indiquer si l’orchestration est en mode débogage, puis, là où vous avez un point dans l’orchestration à laquelle vous souhaitez être en mesure de modifier les valeurs, vous pouvez ajouter un **décider** forme avec une dynamique branche qui s’exécute uniquement lorsque la variable de mode de débogage est définie sur True, ou lorsqu’une condition particulière survient que vous souhaitez examiner.</span><span class="sxs-lookup"><span data-stu-id="8d082-108">Set up a Boolean variable to indicate whether or not your orchestration is in debug mode, then wherever you have a point in your orchestration at which you would like to be able to modify values, you can add a **Decide** shape with one live branch that runs only when your debug mode variable is set to True, or when a particular condition arises that you want to examine.</span></span> <span data-ttu-id="8d082-109">Vous appelez la méthode à partir une **Expression** forme dans la branche active de la **décider**.</span><span class="sxs-lookup"><span data-stu-id="8d082-109">You call your method from an **Expression** shape in the live branch of the **Decide**.</span></span> <span data-ttu-id="8d082-110">Lorsque vous n’avez plus besoin de déboguer, vous définissez votre variable de mode de débogage sur False, ou supprimez la **décider** recompile puis recompilez l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="8d082-110">When you no longer need to debug, you set your debug mode variable to False, or remove the **Decide** shape(s) altogether and recompile.</span></span>  
  
## <a name="to-debug-a-net-component-called-by-an-orchestration"></a><span data-ttu-id="8d082-111">Pour déboguer un composant .NET appelé par une orchestration</span><span class="sxs-lookup"><span data-stu-id="8d082-111">To Debug a .NET component called by an Orchestration</span></span>  
 <span data-ttu-id="8d082-112">Les étapes suivantes indiquent comment déboguer un composant .NET appelé par une orchestration.</span><span class="sxs-lookup"><span data-stu-id="8d082-112">The following steps demonstrate how to debug a .NET component called by an Orchestration:</span></span>  
  
1.  <span data-ttu-id="8d082-113">Ouvrez le projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] de votre composant.</span><span class="sxs-lookup"><span data-stu-id="8d082-113">Open the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for your component.</span></span>  
  
2.  <span data-ttu-id="8d082-114">Définissez dans le composant un point d'arrêt sur la méthode qui est appelée par l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="8d082-114">Set a breakpoint in your component on the method that is called by the orchestration.</span></span>  
  
3.  <span data-ttu-id="8d082-115">Cliquez sur le **déboguer** menu et sélectionnez **attacher au processus...**</span><span class="sxs-lookup"><span data-stu-id="8d082-115">Click the **Debug** menu and select **Attach to Process…**</span></span> <span data-ttu-id="8d082-116">Pour afficher le **attacher au processus** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8d082-116">to display the **Attach to Process** dialog.</span></span>  
  
4.  <span data-ttu-id="8d082-117">Cliquez sur le **sélectionnez...**</span><span class="sxs-lookup"><span data-stu-id="8d082-117">Click the **Select…**</span></span> <span data-ttu-id="8d082-118">situé en regard du **attacher à :** zone de texte pour afficher le **sélectionner le Type de Code** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8d082-118">button next to the **Attach to:** text box to display the **Select Code Type** dialog.</span></span>  
  
5.  <span data-ttu-id="8d082-119">Cliquez pour sélectionner l’option à **déboguer ces types de codes :** et sélectionnez **Managed** puis cliquez sur le **OK** bouton.</span><span class="sxs-lookup"><span data-stu-id="8d082-119">Click to select the option to **Debug these code types:** and select **Managed** and then click the **OK** button.</span></span>  
  
6.  <span data-ttu-id="8d082-120">Cliquez pour sélectionner le **BTSNTSvc.exe** des **processus disponibles** puis cliquez sur le **attacher** bouton.</span><span class="sxs-lookup"><span data-stu-id="8d082-120">Click to select the **BTSNTSvc.exe** process from **Available Processes** and then click the **Attach** button.</span></span>  
  
7.  <span data-ttu-id="8d082-121">Envoyez un message à votre orchestration via un port de réception.</span><span class="sxs-lookup"><span data-stu-id="8d082-121">Send a message to your orchestration through a receive port.</span></span>  
  
8.  <span data-ttu-id="8d082-122">Le composant .NET doit être arrêté sur le point d'arrêt.</span><span class="sxs-lookup"><span data-stu-id="8d082-122">The .NET component should be stopped in the breakpoint.</span></span>  
  
9. <span data-ttu-id="8d082-123">Vous pouvez effectuer un débogage classique à l'aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8d082-123">You can perform debugging as usual with [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8d082-124">Pour de meilleurs résultats, le composant .NET doit être enregistré dans le GAC (Global Assembly Cache).</span><span class="sxs-lookup"><span data-stu-id="8d082-124">For best results, the .NET component should be registered in the Global Assembly Cache (GAC).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d082-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d082-125">See Also</span></span>  
 <span data-ttu-id="8d082-126">[Interface utilisateur du débogueur d’orchestration](../core/orchestration-debugger-user-interface.md) </span><span class="sxs-lookup"><span data-stu-id="8d082-126">[Orchestration Debugger User Interface](../core/orchestration-debugger-user-interface.md) </span></span>  
 [<span data-ttu-id="8d082-127">Débogage des Orchestrations</span><span class="sxs-lookup"><span data-stu-id="8d082-127">Debugging Orchestrations</span></span>](../core/debugging-orchestrations.md)