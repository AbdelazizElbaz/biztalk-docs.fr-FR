---
title: "Méthodes définies par l’utilisateur des composants Interface | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- component interfaces, user-defined methods
- user-defined methods, component interface
- custom component interfaces, limitations
- collection limitations
- custom methods, samples
- samples, custom methods
- component interfaces, limitations for custom CI
ms.assetid: e4b15889-35ff-44aa-819d-eade9690bdd6
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 139117ffb26c8fec355dcfe481657817bc64bc0b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="component-interface-user-defined-methods"></a><span data-ttu-id="67e91-102">Méthodes définies par l’utilisateur des composants Interface</span><span class="sxs-lookup"><span data-stu-id="67e91-102">Component Interface User-Defined Methods</span></span>
<span data-ttu-id="67e91-103">L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise prend en charge les méthodes définies par l'utilisateur dans les interfaces de composant.</span><span class="sxs-lookup"><span data-stu-id="67e91-103">Microsoft BizTalk Adapter for PeopleSoft Enterprise supports user-defined methods in component interfaces.</span></span> <span data-ttu-id="67e91-104">Les signatures ont la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="67e91-104">The signatures are of the form:</span></span>  
  
```  
myRet=myCI.myMethod(parameter1, parameter2, ...)  
```  
  
 <span data-ttu-id="67e91-105">où :</span><span class="sxs-lookup"><span data-stu-id="67e91-105">where:</span></span>  
  
-   <span data-ttu-id="67e91-106">`parameter1` et `parameter2` sont des paramètres d'entrée.</span><span class="sxs-lookup"><span data-stu-id="67e91-106">`parameter1`, `parameter2` are input parameters.</span></span>  
  
-   <span data-ttu-id="67e91-107">`myRet` est la valeur renvoyée.</span><span class="sxs-lookup"><span data-stu-id="67e91-107">`myRet` is the return value.</span></span>  
  
 <span data-ttu-id="67e91-108">Les paramètres ne peuvent être que des paramètres d'entrée pour la méthode.</span><span class="sxs-lookup"><span data-stu-id="67e91-108">The parameters can only be input parameters to the method.</span></span> <span data-ttu-id="67e91-109">Une seule valeur peut être renvoyée de la méthode comme paramètre de renvoi.</span><span class="sxs-lookup"><span data-stu-id="67e91-109">Only one value can be returned from the method as the return parameter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67e91-110">L'interface de composant qui contient les méthodes définies par l'utilisateur doit uniquement avoir la fonction `Get` de PeopleSoft activée.</span><span class="sxs-lookup"><span data-stu-id="67e91-110">The component interface that contains user-defined methods should only have the PeopleSoft `Get` function enabled.</span></span> <span data-ttu-id="67e91-111">Si l'interface de composant inclut des clés, les méthodes personnalisées ne fonctionnent pas.</span><span class="sxs-lookup"><span data-stu-id="67e91-111">If the component interface has keys, then custom methods will not work.</span></span>  
  
## <a name="custom-ci-limitation"></a><span data-ttu-id="67e91-112">Limitation des interfaces de composant personnalisées</span><span class="sxs-lookup"><span data-stu-id="67e91-112">Custom CI Limitation</span></span>  
 <span data-ttu-id="67e91-113">L'adaptateur BizTalk pour PeopleSoft Enterprise peut gérer les méthodes PeopleSoft personnalisées à condition que l'interface de composant n'inclut pas de clés.</span><span class="sxs-lookup"><span data-stu-id="67e91-113">BizTalk Adapter for PeopleSoft Enterprise can handle custom PeopleSoft methods provided that the component interface does not have keys.</span></span> <span data-ttu-id="67e91-114">Si l’interface de composant inclut des clés, des méthodes personnalisées ne fonctionnera pas.</span><span class="sxs-lookup"><span data-stu-id="67e91-114">If the component interface has keys, custom methods will not work.</span></span>  
  
### <a name="workaround"></a><span data-ttu-id="67e91-115">Pour contourner le problème</span><span class="sxs-lookup"><span data-stu-id="67e91-115">Workaround</span></span>  
 <span data-ttu-id="67e91-116">Créez une interface de composant sans clé et écrivez une nouvelle méthode personnalisée qui incorpore les clés dans le cadre des paramètres d'appel.</span><span class="sxs-lookup"><span data-stu-id="67e91-116">Create a new component interface that does not have keys, and write a new custom method that incorporates the keys as part of the calling parameters.</span></span> <span data-ttu-id="67e91-117">Par exemple, vous pouvez utiliser la méthode personnalisée SetPassword dans l'interface de composant USER_PROFILE. USER_PROFILE inclut toutefois des clés.</span><span class="sxs-lookup"><span data-stu-id="67e91-117">For example, you could use the SetPassword custom method in the USER_PROFILE component interface; however USER_PROFILE has keys.</span></span> <span data-ttu-id="67e91-118">Vous pouvez créer une interface de composant sans clé, puis créer une méthode personnalisée dans votre nouvelle interface de composant.</span><span class="sxs-lookup"><span data-stu-id="67e91-118">You can create a new component interface that has no keys, and then create a custom method in your new component interface.</span></span> <span data-ttu-id="67e91-119">Cette méthode accepte deux paramètres : l'ID d'utilisateur et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="67e91-119">This method would accept two parameters, user ID and password.</span></span> <span data-ttu-id="67e91-120">La méthode personnalisée peut ensuite appeler USER_PROFILE à l'aide de la fonction `Get`, puis appeler `SetPassword`.</span><span class="sxs-lookup"><span data-stu-id="67e91-120">The custom method could then invoke USER_PROFILE with a `Get` and then invoke `SetPassword`.</span></span> <span data-ttu-id="67e91-121">Pour plus d’informations, consultez la documentation de PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="67e91-121">Consult the PeopleSoft documentation for more details.</span></span>  
  
 <span data-ttu-id="67e91-122">En raison d'une limitation dans PeopleSoft, les types `Date`, `DateTime` et `Time` qui apparaissent dans les méthodes définies par l'utilisateur sont mappés sous la forme de chaînes dans le code client.</span><span class="sxs-lookup"><span data-stu-id="67e91-122">Due to a limitation in PeopleSoft, `Date`, `DateTime`, and `Time` types appearing in user-defined methods are mapped as strings in the client code.</span></span>  
  
## <a name="collection-limitation"></a><span data-ttu-id="67e91-123">Limitation des collections</span><span class="sxs-lookup"><span data-stu-id="67e91-123">Collection Limitation</span></span>  
 <span data-ttu-id="67e91-124">Les méthodes définies par l'utilisateur ne peuvent pas renvoyer de collection, ou plus généralement, d'objet API.</span><span class="sxs-lookup"><span data-stu-id="67e91-124">User-defined methods cannot return a collection, or more generally, any API object.</span></span> <span data-ttu-id="67e91-125">Vous pouvez uniquement renvoyer des types simples (par exemple, chaînes et nombres).</span><span class="sxs-lookup"><span data-stu-id="67e91-125">This means that you can only return simple types, for example, strings and numbers.</span></span> <span data-ttu-id="67e91-126">Vous pouvez contourner cette limitation en envoyant une collection sous la forme d'une chaîne XML et en programmant le client pour analyser les chaînes et extraire les éléments au format correct.</span><span class="sxs-lookup"><span data-stu-id="67e91-126">You can get around this limitation by sending a collection as an XML string and programming the client to parse the strings to extract the items into the correct format.</span></span> <span data-ttu-id="67e91-127">Pour consulter un exemple de ce contournement, vous pouvez examiner l'interface de composant personnalisée GET_CI_INFO.</span><span class="sxs-lookup"><span data-stu-id="67e91-127">You can examine the GET_CI_INFO custom component interface to see an example of this workaround.</span></span>  
  
## <a name="sample-custom-method"></a><span data-ttu-id="67e91-128">Exemple de méthode personnalisée</span><span class="sxs-lookup"><span data-stu-id="67e91-128">Sample Custom Method</span></span>  
 <span data-ttu-id="67e91-129">Vous pouvez utiliser la méthode personnalisée de base suivante (SayHello) pour tester les fonctionnalités de votre interface de composant à l'aide de méthodes personnalisées.</span><span class="sxs-lookup"><span data-stu-id="67e91-129">You can use the following basic custom method, SayHello, to test the functionality of your component interface using custom methods.</span></span>  
  
 <span data-ttu-id="67e91-130">La fonction PeopleCode suivante est une méthode définie par l'utilisateur d'une interface de composant PeopleSoft nommée ACB_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="67e91-130">The following PeopleCode function is a user-defined method of a PeopleSoft component interface named ACB_EMPLOYEE.</span></span> <span data-ttu-id="67e91-131">L’exemple retourne une chaîne où la valeur de retour est **Hello** suivi par la valeur du paramètre d’entrée.</span><span class="sxs-lookup"><span data-stu-id="67e91-131">The sample returns a string where the return value is **Hello** followed by the value of the input parameter.</span></span>  
  
```  
Function SayHello(&sName As string) Returns string  
      &EOL = Char(10);  
      &sResult = "Hello " | &sName | &EOL;  
      Return &sResult;  
End-Function;  
```  
  
> [!NOTE]
>  <span data-ttu-id="67e91-132">Pour modifier plusieurs tables simultanément (à l'aide d'une commande), vous pouvez créer une autre interface de composant ou une méthode définie par l'utilisateur d'une interface de composant.</span><span class="sxs-lookup"><span data-stu-id="67e91-132">To modify multiple tables at the same time (using one command) you can either create another component interface or create a component interface user-defined method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67e91-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67e91-133">See Also</span></span>  
 [<span data-ttu-id="67e91-134">Annexe a : méthodes d’Interface de composant</span><span class="sxs-lookup"><span data-stu-id="67e91-134">Appendix A: Component Interface Methods</span></span>](../core/appendix-a-component-interface-methods.md)