---
title: "Développement d’un fonctoid Inline personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4533f09f-b62d-4b09-b7de-44541c6cf053
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a742e6a53b5fb81d92922ff94e7754239f723ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-a-custom-inline-functoid"></a><span data-ttu-id="98e97-102">Développement d'un fonctoid Inline personnalisé</span><span class="sxs-lookup"><span data-stu-id="98e97-102">Developing a Custom Inline Functoid</span></span>
<span data-ttu-id="98e97-103">Les fonctoids Inline personnalisés fonctionnent en copiant le code d'implémentation directement dans un mappage et non pas en référençant un assembly, une classe et un nom de méthode comme le ferait un fonctoid référencé personnalisé.</span><span class="sxs-lookup"><span data-stu-id="98e97-103">Custom inline functoids provide functionality by copying implementation code directly into a map and not by referencing an assembly, class, and method name like a custom referenced functoid.</span></span>  
  
## <a name="building-inline-script"></a><span data-ttu-id="98e97-104">Création d’un script Inline </span><span class="sxs-lookup"><span data-stu-id="98e97-104">Building Inline Script</span></span>  
 <span data-ttu-id="98e97-105">Il existe deux manières de créer du script afin de l'inclure dans le mappage.</span><span class="sxs-lookup"><span data-stu-id="98e97-105">There are two ways to provide script for inclusion into the map.</span></span> <span data-ttu-id="98e97-106">Choisissez parmi les méthodes suivantes, en fonction du nombre variable de paramètres que votre fonctoid personnalisé prend en charge ou non :</span><span class="sxs-lookup"><span data-stu-id="98e97-106">Choose from the following methods, based on whether your custom functoid supports a variable number of parameters:</span></span>  
  
-   <span data-ttu-id="98e97-107">Substituer **GetInlineScriptBuffer** lorsque votre fonctoid personnalisé accepte un nombre variable de paramètres d’entrée et que vous avez défini le **HasVariableInputs** propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="98e97-107">Override **GetInlineScriptBuffer** when your custom functoid accepts a variable number of input parameters and you have set the **HasVariableInputs** property to `true`.</span></span> <span data-ttu-id="98e97-108">Par exemple, utilisez cette méthode si vous voulez concaténer un nombre variable de chaînes ou trouver la valeur la plus grande dans une série de valeurs.</span><span class="sxs-lookup"><span data-stu-id="98e97-108">For example, use this method if you want to concatenate a variable number of strings or find the largest value in a set of values.</span></span>  
  
-   <span data-ttu-id="98e97-109">Utilisez **SetScriptBuffer** lorsque vous n’avez pas besoin de prendre en charge un nombre variable de paramètres d’entrée.</span><span class="sxs-lookup"><span data-stu-id="98e97-109">Use **SetScriptBuffer** when you do not need to support a variable number of input parameters.</span></span> <span data-ttu-id="98e97-110">Vous pouvez toujours utiliser des paramètres facultatifs, mais le nombre total de paramètres est fixe.</span><span class="sxs-lookup"><span data-stu-id="98e97-110">You can still use optional parameters, but the total number of parameters is fixed.</span></span>  
  
 <span data-ttu-id="98e97-111">Ces deux méthodes impliquent des implémentations différentes.</span><span class="sxs-lookup"><span data-stu-id="98e97-111">These two methods require different implementations.</span></span>  
  
### <a name="providing-inline-code-with-setscriptbuffer"></a><span data-ttu-id="98e97-112">Code Inline avec SetScriptBuffer</span><span class="sxs-lookup"><span data-stu-id="98e97-112">Providing Inline Code with SetScriptBuffer</span></span>  
 <span data-ttu-id="98e97-113">Pour configurer votre fonctoid personnalisé de sorte qu’il utilise le script Inline :</span><span class="sxs-lookup"><span data-stu-id="98e97-113">To configure your custom functoid to use inline script:</span></span>  
  
1.  <span data-ttu-id="98e97-114">Appelez **AddScriptTypeSupport** avec [Microsoft.BizTalk.BaseFunctoids.ScriptType](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.scripttype.aspx) pour activer le code inline et définir le type de script pris en charge.</span><span class="sxs-lookup"><span data-stu-id="98e97-114">Call **AddScriptTypeSupport** with [Microsoft.BizTalk.BaseFunctoids.ScriptType](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.scripttype.aspx) to enable inline code and set the supported script type.</span></span>  
  
2.  <span data-ttu-id="98e97-115">Appeler **SetScriptBuffer** pour définir le code à utiliser pour le fonctoid personnalisé.</span><span class="sxs-lookup"><span data-stu-id="98e97-115">Invoke **SetScriptBuffer** to set the code to use for the custom functoid.</span></span> <span data-ttu-id="98e97-116">Vous appellerez cette fonction trois fois avec le paramètre `functionNumber` pour les fonctoids cumulés personnalisés et une fois pour les fonctoids non cumulés personnalisés.</span><span class="sxs-lookup"><span data-stu-id="98e97-116">You will call this function three times with the `functionNumber` parameter for custom cumulative functoids and once for custom noncumulative functoids.</span></span>  
  
3.  <span data-ttu-id="98e97-117">Utilisez **SetScriptGlobalBuffer** pour déclarer des variables globales que votre code inline utilise.</span><span class="sxs-lookup"><span data-stu-id="98e97-117">Use **SetScriptGlobalBuffer** to declare any global variables that your inline code uses.</span></span>  
  
4.  <span data-ttu-id="98e97-118">Utilisez **RequiredGlobalHelperFunctions** pour indiquer les fonctions d’assistance nécessitant votre fonctoid inline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="98e97-118">Use **RequiredGlobalHelperFunctions** to indicate the helper functions that your custom inline functoid requires.</span></span>  
  
 <span data-ttu-id="98e97-119">Vous pouvez générer votre script en utilisant StringBuilder ou des constantes.</span><span class="sxs-lookup"><span data-stu-id="98e97-119">You can build your script by using StringBuilder or constants.</span></span> <span data-ttu-id="98e97-120">Pour écrire du code de script, une des possibilités consiste à écrire d'abord un fonctoid référencé personnalisé puis, lorsque tous les bogues sont éliminés, à le convertir en un fonctoid Inline en copiant toutes vos fonctions dans des constantes de chaîne.</span><span class="sxs-lookup"><span data-stu-id="98e97-120">One approach to writing script code is to write a custom referenced functoid first and, when all bugs are eliminated, convert it to inline by copying your functions into string constants.</span></span>  
  
### <a name="providing-inline-code-with-getinlinescriptbuffer"></a><span data-ttu-id="98e97-121">Code Inline avec GetInlineScriptBuffer</span><span class="sxs-lookup"><span data-stu-id="98e97-121">Providing Inline Code with GetInlineScriptBuffer</span></span>  
 <span data-ttu-id="98e97-122">Si votre fonctoid inline personnalisé prend en charge un nombre variable de paramètres, vous remplacera **GetInlineScriptBuffer**.</span><span class="sxs-lookup"><span data-stu-id="98e97-122">If your custom inline functoid supports a variable number of parameters, you will override **GetInlineScriptBuffer**.</span></span> <span data-ttu-id="98e97-123">Pour configurer votre fonctoid personnalisé de sorte qu’il utilise le script Inline :</span><span class="sxs-lookup"><span data-stu-id="98e97-123">To configure your custom functoid to use inline script:</span></span>  
  
1.  <span data-ttu-id="98e97-124">Dans le constructeur, déclarez que votre fonctoid personnalisé dispose d’entrées variables en définissant **HasVariableInputs** à `true`.</span><span class="sxs-lookup"><span data-stu-id="98e97-124">In the constructor, declare that your custom functoid has variable inputs by setting **HasVariableInputs** to `true`.</span></span>  
  
2.  <span data-ttu-id="98e97-125">Dans le constructeur, appelez **AddScriptTypeSupport** avec [Microsoft.BizTalk.BaseFunctoids.ScriptType](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.scripttype.aspx) pour activer le code inline et définir le type de script pris en charge.</span><span class="sxs-lookup"><span data-stu-id="98e97-125">In the constructor, call **AddScriptTypeSupport** with [Microsoft.BizTalk.BaseFunctoids.ScriptType](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.scripttype.aspx) to enable inline code and set the supported script type.</span></span>  
  
3.  <span data-ttu-id="98e97-126">Substituer **GetInlineScriptBuffer** pour construire et renvoyer le code à utiliser dans le mappage de votre fonctoid personnalisé.</span><span class="sxs-lookup"><span data-stu-id="98e97-126">Override **GetInlineScriptBuffer** to construct and return the code to use in the map for your custom functoid.</span></span> <span data-ttu-id="98e97-127">Utilisez les paramètres pour créer le code correct en vérifiant le `scriptType` et le `numParams`.</span><span class="sxs-lookup"><span data-stu-id="98e97-127">Use the parameters to build the correct code by checking the `scriptType` and `numParams`.</span></span> <span data-ttu-id="98e97-128">Le dernier paramètre, `functionNumber`, doit être 0.</span><span class="sxs-lookup"><span data-stu-id="98e97-128">The final parameter, `functionNumber`, should be 0.</span></span> <span data-ttu-id="98e97-129">Il s’agit, car les fonctions cumulées ont un nombre fixe d’entrées et n’utilisent pas ce mécanisme.</span><span class="sxs-lookup"><span data-stu-id="98e97-129">This is because cumulative functions have a fixed number of inputs and do not use this mechanism.</span></span>  
  
4.  <span data-ttu-id="98e97-130">Utilisez **SetScriptGlobalBuffer** pour déclarer des variables globales que votre code inline utilise.</span><span class="sxs-lookup"><span data-stu-id="98e97-130">Use **SetScriptGlobalBuffer** to declare global variables that your inline code uses.</span></span>  
  
5.  <span data-ttu-id="98e97-131">Utilisez **RequiredGlobalHelperFunctions** pour indiquer les fonctions d’assistance nécessitant votre fonctoid inline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="98e97-131">Use **RequiredGlobalHelperFunctions** to indicate the helper functions that your custom inline functoid requires.</span></span>  
  
 <span data-ttu-id="98e97-132">Le fragment de code suivant crée une fonction C# avec le nombre de paramètres transmis dans `numParams`, mais sans corps.</span><span class="sxs-lookup"><span data-stu-id="98e97-132">The following code fragment builds a C# function with the number of parameters passed in `numParams` but with no function body.</span></span> <span data-ttu-id="98e97-133">Pour utiliser ce fragment de code, copiez l'exemple dans votre solution et ajoutez du code avec les paramètres pour qu'une valeur soit renvoyée.</span><span class="sxs-lookup"><span data-stu-id="98e97-133">To use this code fragment, copy the example to your solution and add code to do something with the parameters and return a value.</span></span>  
  
```  
// Override GetInlineScriptBuffer  
protected override string GetInlineScriptBuffer(ScriptType scriptType, int numParams, int functionNumber)  
{  
    // Is this one of the supported script types?  
    if(ScriptType.CSharp == scriptType)  
    {  
        // Assume functionNumber == 0  
        StringBuilder builder = new StringBuilder();  
        // Function declaration   
        builder.Append("public string MyFunction("  
        // Declare parameters using numParams  
        for(int i=0; i<numParams; i++)  
        {  
            // Separate params with a comma  
            if(i > 0)  
                builder.Append(", ");  
            // Declare parameters, param0 to paramNUMPARAM  
            builder.Append("string param" + i.ToString());  
        }  
        builder.Append(")\n");  
        // Function body; process params as needed  
        builder.Append("{\n");  
        builder.Append("}\n");  
        // Return script  
        return builder.ToString();  
    }  
    // scriptType is unsupported  
    return string.Empty;  
}  
```  
  
## <a name="testing-an-inline-script"></a><span data-ttu-id="98e97-134">Test d’un script Inline</span><span class="sxs-lookup"><span data-stu-id="98e97-134">Testing an Inline Script</span></span>  
 <span data-ttu-id="98e97-135">Le test est un aspect important de tout effort de développement.</span><span class="sxs-lookup"><span data-stu-id="98e97-135">Testing is an important consideration in any development effort.</span></span> <span data-ttu-id="98e97-136">Les fonctoids Inline personnalisés peuvent être soumis à un test.</span><span class="sxs-lookup"><span data-stu-id="98e97-136">Custom inline functoids can be challenging to test.</span></span> <span data-ttu-id="98e97-137">Pour simplifier le processus, utilisez l'une des techniques suivantes ou les deux :</span><span class="sxs-lookup"><span data-stu-id="98e97-137">To simplify the process, use one or both of the following techniques:</span></span>  
  
-   <span data-ttu-id="98e97-138">Examinez le XSLT d’un mappage qui utilise le fonctoid inline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="98e97-138">Examine the XSLT of a map that uses the custom inline functoid.</span></span>  
  
-   <span data-ttu-id="98e97-139">Vérifiez l'entrée et la sortie d'un mappage qui utilise le fonctoid Inline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="98e97-139">Verify the input and output of a map that uses the custom inline functoid.</span></span>  
  
### <a name="examine-the-xslt-of-a-map-that-uses-the-custom-inline-functoid"></a><span data-ttu-id="98e97-140">Examinez le XSLT d'un mappage qui utilise le fonctoid Inline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="98e97-140">Examine the XSLT of a Map That Uses the Custom Inline Functoid</span></span>  
 <span data-ttu-id="98e97-141">Cette technique révèle souvent des problèmes de syntaxe subtiles ou de logique.</span><span class="sxs-lookup"><span data-stu-id="98e97-141">This technique often reveals problems with logic or subtle syntax issues.</span></span> <span data-ttu-id="98e97-142">Elle vous aide également à comprendre ce qui se passe dans le mappage.</span><span class="sxs-lookup"><span data-stu-id="98e97-142">It also helps you to understand what happens in the map.</span></span>  
  
 <span data-ttu-id="98e97-143">Pour afficher le XSLT pour un mappage</span><span class="sxs-lookup"><span data-stu-id="98e97-143">To view the XSLT for a map:</span></span>  
  
1.  <span data-ttu-id="98e97-144">À partir d’un projet BizTalk Visual Studio, cliquez sur le **l’Explorateur de solutions** onglet, cliquez sur un mappage qui utilise votre fonctoid inline personnalisé, puis cliquez sur **valider le mappage**.</span><span class="sxs-lookup"><span data-stu-id="98e97-144">From a Visual Studio BizTalk project, click the **Solution Explorer** tab, right-click a map that uses your custom inline functoid, and then click **Validate Map**.</span></span>  
  
2.  <span data-ttu-id="98e97-145">Faites défiler la fenêtre Sortie pour rechercher l'URL du fichier XSLT.</span><span class="sxs-lookup"><span data-stu-id="98e97-145">Scroll the Output window to find the URL for the XSLT file.</span></span> <span data-ttu-id="98e97-146">Appuyez sur CTRL et cliquez sur l'URL pour afficher le fichier.</span><span class="sxs-lookup"><span data-stu-id="98e97-146">Press CTRL and click the URL to view the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98e97-147">Gardez à l’esprit qu'aucune modification apportée au fichier XSLT ne sera répercutée dans votre fonctoid personnalisé.</span><span class="sxs-lookup"><span data-stu-id="98e97-147">Remember that any changes made to the XSLT file will not be reflected in your custom functoid.</span></span>  
  
### <a name="test-a-map-that-uses-the-custom-inline-functoid"></a><span data-ttu-id="98e97-148">Test d'un mappage qui utilise le fonctoid Inline personnalisé</span><span class="sxs-lookup"><span data-stu-id="98e97-148">Test a Map That Uses the Custom Inline Functoid</span></span>  
 <span data-ttu-id="98e97-149">Ce test permet de vérifier que le mappage et le fonctoid Inline personnalisé fonctionnent comme prévu.</span><span class="sxs-lookup"><span data-stu-id="98e97-149">This tests whether the map and custom inline functoid work as expected.</span></span>  
  
 <span data-ttu-id="98e97-150">Pour tester un mappage</span><span class="sxs-lookup"><span data-stu-id="98e97-150">To test a map:</span></span>  
  
1.  <span data-ttu-id="98e97-151">À partir d’un projet BizTalk Visual Studio, cliquez sur le **l’Explorateur de solutions** onglet, cliquez sur un mappage qui utilise votre fonctoid inline personnalisé, puis cliquez sur **Test Map**.</span><span class="sxs-lookup"><span data-stu-id="98e97-151">From a Visual Studio BizTalk project, click the **Solution Explorer** tab, right-click a map that uses your custom inline functoid, and then click **Test Map**.</span></span>  
  
2.  <span data-ttu-id="98e97-152">Faites défiler la fenêtre Sortie pour rechercher l'URL du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="98e97-152">Scroll the Output window to find the URL for the output file.</span></span> <span data-ttu-id="98e97-153">Appuyez sur CTRL et cliquez sur l'URL pour afficher le fichier.</span><span class="sxs-lookup"><span data-stu-id="98e97-153">Press CTRL and click the URL to view the file.</span></span>  
  
 <span data-ttu-id="98e97-154">Vous pouvez vérifier les valeurs d’entrée et de sortie pour vous assurer que le mappage s'est comporté comme prévu.</span><span class="sxs-lookup"><span data-stu-id="98e97-154">You can check input and output values to verify that the map behaved as expected.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98e97-155">Exemple</span><span class="sxs-lookup"><span data-stu-id="98e97-155">Example</span></span>  
 <span data-ttu-id="98e97-156">L'exemple suivant montre comment créer un fonctoid Inline personnalisé pour concaténer deux chaînes.</span><span class="sxs-lookup"><span data-stu-id="98e97-156">The following example illustrates how to create a custom inline functoid for concatenating two strings.</span></span> <span data-ttu-id="98e97-157">Il repose sur un fichier de ressources contenant trois ressources de chaîne et une ressource bitmap 16 x 16 pixels.</span><span class="sxs-lookup"><span data-stu-id="98e97-157">It relies on a resource file containing three string resources and a 16x16-pixel bitmap resource.</span></span>  
  
```  
using System;  
using Microsoft.BizTalk.BaseFunctoids;  
using System.Reflection;  
using System.Text;  
  
namespace Microsoft.Samples.BizTalk.CustomFunctoid  
{  
    /// <summary>  
    /// Performs a string concatenation using inline code.  
    /// </summary>  
    public class CustomStringConcatFunctoid : BaseFunctoid  
    {  
        public CustomStringConcatFunctoid()  
            : base()  
        {  
            //ID for this functoid  
            this.ID = 6001;  
  
            // Resource assembly must be ProjectName.ResourceName if building with VS.Net  
            SetupResourceAssembly("Microsoft.Samples.BizTalk.CustomFunctoid.CustomFunctoidResources", Assembly.GetExecutingAssembly());  
  
            // Pass the resource ID names for functoid name, tooltip  
            // description and the 16x16 bitmap for the Map palette  
            SetName("IDS_CUSTOMSTRINGCONCATFUNCTOID_NAME");  
            SetTooltip("IDS_CUSTOMSTRINGCONCATFUNCTOID_TOOLTIP");  
            SetDescription("IDS_CUSTOMSTRINGCONCATFUNCTOID_DESCRIPTION");  
            SetBitmap("IDB_CUSTOMSTRINGCONCATFUNCTOID_BITMAP");  
  
            // Put this string handling function under the String   
            // Functoid tab in the Visual Studio toolbox for functoids  
            this.Category = FunctoidCategory.String;  
  
            // 2 required parameters, no optional parameters  
            this.SetMinParams(2);  
            this.SetMaxParams(2);  
  
            // Functoid accepts two inputs  
            AddInputConnectionType(ConnectionType.AllExceptRecord);  
            AddInputConnectionType(ConnectionType.AllExceptRecord);  
  
            // Set the output connection type  
            this.OutputConnectionType = ConnectionType.AllExceptRecord;  
  
            // Declare support for CSharp inline function and  
            // pass the method implementation to the buffer  
            AddScriptTypeSupport(ScriptType.CSharp);  
            SetScriptBuffer(ScriptType.CSharp, GetCSharpBuffer());  
        }  
  
        private string GetCSharpBuffer()  
        {  
            StringBuilder builder = new StringBuilder();  
  
            builder.Append("public string ConCatStrings(string val1, string val2)\n");  
            builder.Append("{\n");  
            builder.Append("    return val2+val1;\n");  
            builder.Append("}\n");  
  
            return builder.ToString();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="98e97-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98e97-158">See Also</span></span>  
 <span data-ttu-id="98e97-159">[Utilisation de BaseFunctoid](../core/using-basefunctoid.md) </span><span class="sxs-lookup"><span data-stu-id="98e97-159">[Using BaseFunctoid](../core/using-basefunctoid.md) </span></span>  
 <span data-ttu-id="98e97-160">[Développement personnalisé référencé fonctoid](../core/developing-a-custom-referenced-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="98e97-160">[Developing a Custom Referenced Functoid](../core/developing-a-custom-referenced-functoid.md) </span></span>  
 [<span data-ttu-id="98e97-161">Fonctoid personnalisé (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="98e97-161">Custom Functoid (BizTalk Server Sample)</span></span>](../core/custom-functoid-biztalk-server-sample.md)