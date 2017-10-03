---
title: "Développement de fonctoids personnalisés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77419e1f-9f01-44ac-bf5b-a393f1d17f61
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e5534f3209cb943fb3e2c2a63a18f9e29928be5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-custom-functoids"></a><span data-ttu-id="9737d-102">Développement de fonctoids personnalisés</span><span class="sxs-lookup"><span data-stu-id="9737d-102">Developing Custom Functoids</span></span>
<span data-ttu-id="9737d-103">Bien que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournisse plusieurs fonctoids permettant la prise en charge de diverses opérations, il est probable que vous rencontriez une situation requérant une approche différente.</span><span class="sxs-lookup"><span data-stu-id="9737d-103">Although [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides many functoids to support a range of diverse operations, you will likely encounter a situation that requires a different approach.</span></span> <span data-ttu-id="9737d-104">Les fonctoids personnalisés vous offrent un moyen pour étendre la gamme des opérations disponibles dans l'environnement de mappage de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9737d-104">Custom functoids provide a way for you to extend the range of operations available within the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] mapping environment.</span></span> <span data-ttu-id="9737d-105">Chaque fonctoid personnalisé est déployé comme un assembly .NET à l’aide des classes dérivées de **Microsoft.BizTalk.BaseFunctoids**.</span><span class="sxs-lookup"><span data-stu-id="9737d-105">Each custom functoid is deployed as a .NET assembly using classes derived from **Microsoft.BizTalk.BaseFunctoids**.</span></span> <span data-ttu-id="9737d-106">Un assembly peut contenir plusieurs fonctoids personnalisés.</span><span class="sxs-lookup"><span data-stu-id="9737d-106">An assembly can contain more than one custom functoid.</span></span>  
  
 <span data-ttu-id="9737d-107">Vous devez envisager d'utiliser un fonctoid personnalisé dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="9737d-107">You should consider using a custom functoid in the following scenarios:</span></span>  
  
-   <span data-ttu-id="9737d-108">Vous possédez des règles de validation et de conversion pour un champ de code de caractère utilisant des données accessibles uniquement par l'intermédiaire d'une API héritée propriétaire.</span><span class="sxs-lookup"><span data-stu-id="9737d-108">You have special validation and conversion rules for a character code field using data that is only accessible through a proprietary legacy API.</span></span>  
  
-   <span data-ttu-id="9737d-109">Vous devez chiffrer ou déchiffrer des champs à l'aide d'une gestion personnalisée de la logique métier et des clés.</span><span class="sxs-lookup"><span data-stu-id="9737d-109">You need to encrypt or decrypt fields using custom business logic and key management.</span></span>  
  
-   <span data-ttu-id="9737d-110">Vous devez générer un code de hachage à partir d'une partie du message pour l'utiliser dans une autre application.</span><span class="sxs-lookup"><span data-stu-id="9737d-110">You need to generate a hash code from part of the message for use in another application.</span></span>  
  
-   <span data-ttu-id="9737d-111">Le service Comptabilité demande que les messages qui lui sont transmis incluent des informations récapitulatives sur le total des ventes par type de produit.</span><span class="sxs-lookup"><span data-stu-id="9737d-111">Accounting requests that messages transmitted to their department include summary information about total sales by each product type.</span></span>  
  
-   <span data-ttu-id="9737d-112">Vous souhaitez réduire la complexité d'un mappage en combinant plusieurs étapes liées, en utilisant une méthode différente ou de nouvelles bibliothèques de classes.</span><span class="sxs-lookup"><span data-stu-id="9737d-112">You want to reduce the complexity of a map by combining several related steps, by using a different approach, or by using new class libraries.</span></span>  
  
-   <span data-ttu-id="9737d-113">Dans un fonctoid de script, plusieurs mappages utilisent le même code de script.</span><span class="sxs-lookup"><span data-stu-id="9737d-113">More than one map is using the same script code in a script functoid.</span></span>  
  
-   <span data-ttu-id="9737d-114">Vous devez signaler tout échec d'opération dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="9737d-114">You need to write to the event log when an operation fails.</span></span>  
  
 <span data-ttu-id="9737d-115">Les fonctoids personnalisés peuvent être intégrés dans une solution directement à l'aide de code Inline ou indirectement par référence à une méthode d'une bibliothèque de classes déployée dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="9737d-115">Custom functoids can be integrated into a solution directly by using inline code or indirectly by reference to a method in a class library deployed into the global assembly cache.</span></span> <span data-ttu-id="9737d-116">Les deux types d’intégration s’appuient sur la **BizTalk.BaseFunctoid** classe et suivre le même ensemble d’étapes générales :</span><span class="sxs-lookup"><span data-stu-id="9737d-116">Both types of integration rely on the **BizTalk.BaseFunctoid** class and follow the same set of general steps:</span></span>  
  
1.  <span data-ttu-id="9737d-117">Créez un projet de bibliothèque de classes en utilisant le langage .NET de votre choix.</span><span class="sxs-lookup"><span data-stu-id="9737d-117">Create a new class library project using the .NET language of your choice.</span></span>  
  
2.  <span data-ttu-id="9737d-118">À l'aide de l'utilitaire d'attribution de noms forts sn.exe, créez un fichier clé et affectez-le au projet.</span><span class="sxs-lookup"><span data-stu-id="9737d-118">Using the strong-naming utility sn.exe, create a keyfile and assign it to the project.</span></span>  
  
3.  <span data-ttu-id="9737d-119">Ajoutez une référence à Microsoft.BizTalk.BaseFunctoids.dll.</span><span class="sxs-lookup"><span data-stu-id="9737d-119">Add a reference to Microsoft.BizTalk.BaseFunctoids.dll.</span></span> <span data-ttu-id="9737d-120">Cet assembly contient la **BaseFunctoid** classe de base.</span><span class="sxs-lookup"><span data-stu-id="9737d-120">This assembly contains the **BaseFunctoid** base class.</span></span>  
  
4.  <span data-ttu-id="9737d-121">Créez un fichier de ressources et ajoutez-le au projet.</span><span class="sxs-lookup"><span data-stu-id="9737d-121">Create a resource file and add it to the project.</span></span> <span data-ttu-id="9737d-122">Ajoutez des ressources de chaîne pour le nom de fonctoid, l'info-bulle et la description.</span><span class="sxs-lookup"><span data-stu-id="9737d-122">Add string resources for the functoid name, tooltip, and description.</span></span> <span data-ttu-id="9737d-123">Ajoutez une ressource image de 16 x 16 pixels pour représenter le fonctoid dans la palette du concepteur de mappages.</span><span class="sxs-lookup"><span data-stu-id="9737d-123">Add a 16x16-pixel image resource to represent the functoid on the map designer palette.</span></span>  
  
5.  <span data-ttu-id="9737d-124">Implémentez la classe de fonctoid par dérivation de **BaseFunctoid**, l’établissement des paramètres de base dans le constructeur, puis en écrivant la méthode fonctoid et toutes les méthodes de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="9737d-124">Implement the functoid class by deriving from **BaseFunctoid**, establishing basic parameters in the constructor, and then writing the functoid method and any supporting methods.</span></span> <span data-ttu-id="9737d-125">L'assembly peut contenir plusieurs fonctoids personnalisés.</span><span class="sxs-lookup"><span data-stu-id="9737d-125">The assembly can contain multiple custom functoids.</span></span>  
  
6.  <span data-ttu-id="9737d-126">Déployez l'assembly et assurez-vous que le nouveau fonctoid est disponible dans la palette de la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="9737d-126">Deploy the assembly and ensure the new functoid is available from the Toolbox palette.</span></span> <span data-ttu-id="9737d-127">Consultez [Ajout et suppression de fonctoids personnalisés à partir de la boîte à outils Visual Studio](../core/adding-and-removing-custom-functoids-from-the-visual-studio-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="9737d-127">See [Adding and Removing Custom Functoids from the Visual Studio Toolbox](../core/adding-and-removing-custom-functoids-from-the-visual-studio-toolbox.md).</span></span>  
  
 <span data-ttu-id="9737d-128">Voici une illustration du fonctoid Floor.</span><span class="sxs-lookup"><span data-stu-id="9737d-128">The following is an illustration for Floor functoid.</span></span>  
  
```  
/// <summary>  
/// Floor Functoid - finds the floor of input  
/// </summary>  
public class FloorFunctoid : BaseFunctoid  
{  
    public FloorFunctoid()  
        : base()  
    {  
        this.ID = 11001;  
        SetupResourceAssembly("MultipleFunctoids.Resource", Assembly.GetExecutingAssembly());  
  
        SetName("NAME_FLOOR");  
        SetDescription("DESCRIPTION_FLOOR");  
        SetTooltip("DESCRIPTION_FLOOR");  
        SetBitmap("IMAGE_FLOOR");  
  
        SetExternalFunctionName(GetType().Assembly.FullName, " MultipleFunctoids.FloorFunctoid", "MathFloor");  
        this.RequiredGlobalHelperFunctions = InlineGlobalHelperFunction.IsNumeric;  
  
        AddScriptTypeSupport(ScriptType.CSharp);  
        SetMinParams(1);  
        SetMaxParams(1);  
  
        this.Category = FunctoidCategory.Math;  
        this.OutputConnectionType = ConnectionType.AllExceptRecord;  
        AddInputConnectionType(ConnectionType.AllExceptRecord);  
        this.HasSideEffects = false;  
    }  
  
    /// <summary>  
    /// To create the C# function  
    /// </summary>  
    /// <param name="scriptType">Script type</param>  
    /// <param name="numParams">Number of parameters</param>  
    /// <param name="functionNumber">Functoid number</param>  
    /// <returns>C# script</returns>  
    protected override string GetInlineScriptBuffer(ScriptType scriptType, int numParams, int functionNumber)  
    {  
        if (ScriptType.CSharp == scriptType)  
        {  
            StringBuilder builder = new StringBuilder();  
  
            builder.Append("public string MathFloor(string input)\n");  
            builder.Append("{\n");  
            builder.Append("  if(string.IsNullOrEmpty(input))\n");  
            builder.Append("    return string.Empty;\n");  
            builder.Append("double d = 0.0;\n");  
            builder.Append("if (IsNumeric(input, ref d))\n");  
            builder.Append("    return Math.Floor(d).ToString(System.Globalization.CultureInfo.InvariantCulture);\n");  
            builder.Append("else\n");  
            builder.Append("    return string.Empty;\n");  
            builder.Append("}\n");  
  
            return builder.ToString();  
        }  
        else  
        {  
            return string.Empty;  
        }  
    }  
}  
  
```  
  
 <span data-ttu-id="9737d-129">Lorsque vous utilisez cet exemple de code dans le cadre d'un projet C#, « Nom de l'assembly » doit être défini sur « MultipleFunctoids ».</span><span class="sxs-lookup"><span data-stu-id="9737d-129">While using this sample code as part of your C# project, the “Assembly name” must be set to “MultipleFunctoids”.</span></span> <span data-ttu-id="9737d-130">Le projet C# (contenant ce code) doit inclure un fichier Resource.resx.</span><span class="sxs-lookup"><span data-stu-id="9737d-130">Your C# project (containing this code) should include a Resource.resx file.</span></span>  
  
```  
SetName("NAME_FLOOR");  
SetDescription("DESCRIPTION_FLOOR");  
SetTooltip("DESCRIPTION_FLOOR");  
SetBitmap("IMAGE_FLOOR");  
  
```  
  
 <span data-ttu-id="9737d-131">Dans le code ci-dessus, les valeurs « NAME_FLOOR », « DESCRIPTION_FLOOR » et « DESCRIPTION_FLOOR » sont les « clés » des chaînes de ressources incorporées dans le fichier Resource.resx.</span><span class="sxs-lookup"><span data-stu-id="9737d-131">In the above code, the values “NAME_FLOOR”, “DESCRIPTION_FLOOR”, and “DESCRIPTION_FLOOR” are the “keys” of resource strings embedded in Resource.resx file.</span></span> <span data-ttu-id="9737d-132">« IMAGE_FLOOR » est le nom d'une image incorporée dans le fichier Resource.resx.</span><span class="sxs-lookup"><span data-stu-id="9737d-132">And, “IMAGE_FLOOR” is the name of an image embedded in the Resource.resx file.</span></span> <span data-ttu-id="9737d-133">Celle-ci agira en tant qu'icône pour le fonctoid.</span><span class="sxs-lookup"><span data-stu-id="9737d-133">This image will act as an icon for the functoid.</span></span>  
  
 <span data-ttu-id="9737d-134">Si vous ne spécifiez pas de clés de ressources appropriées ou si vous supprimez la méthode SetName, un fonctoid personnalisé sans nom est créé, ce qui est déconseillé.</span><span class="sxs-lookup"><span data-stu-id="9737d-134">If you do not specify proper resource keys, or if you delete the SetName method, then a nameless custom functoid is created, which is not a good practice.</span></span> <span data-ttu-id="9737d-135">Cela est vrai également pour les méthodes SetDescription et SetTooltip.</span><span class="sxs-lookup"><span data-stu-id="9737d-135">Same holds true for SetDescription and SetTooltip methods.</span></span> <span data-ttu-id="9737d-136">Utilisez toujours ces méthodes de manière appropriée pour éviter tout comportement de nettoyage indésirable.</span><span class="sxs-lookup"><span data-stu-id="9737d-136">Always use these methods properly to avoid any unwanted garbage behavior.</span></span> <span data-ttu-id="9737d-137">Toutefois, vous pouvez ignorer la méthode SetBitmap si vous ne disposez pas d'images appropriées à utiliser comme icônes pour les fonctoids.</span><span class="sxs-lookup"><span data-stu-id="9737d-137">However, you may skip the SetBitmap method if you do not have any suitable images to be used as functoid icons.</span></span> <span data-ttu-id="9737d-138">Dans ce cas, une icône par défaut est utilisée par le fonctoid personnalisé. Ceci ne présente aucun danger sauf si plusieurs fonctoids sans icône sont présents.</span><span class="sxs-lookup"><span data-stu-id="9737d-138">In such a case, a default icon is used by the custom functoid, which is harmless (unless there are multiple icon-less functoids).</span></span>  
  
 <span data-ttu-id="9737d-139">Pour plus d’informations sur la création d’un fonctoid personnalisé, consultez [fonctoid personnalisé (exemple BizTalk Server)](../core/custom-functoid-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="9737d-139">For more information about how to create a custom functoid, see [Custom Functoid (BizTalk Server Sample)](../core/custom-functoid-biztalk-server-sample.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9737d-140">Certains ID de fonctoids sont réservés par des fonctoids standard/intégrés du Mappeur.</span><span class="sxs-lookup"><span data-stu-id="9737d-140">Certain functoid IDs are reserved by standard/inbuilt Mapper functoids.</span></span> <span data-ttu-id="9737d-141">En règle générale, les fonctoids du Mappeur standards utilisent les ID de 1 à 10000.</span><span class="sxs-lookup"><span data-stu-id="9737d-141">Usually, the standard Mapper functoids use the IDs from 1 to 10000.</span></span> <span data-ttu-id="9737d-142">Lors de la création des fonctoids personnalisés, n’utilisez pas le fonctoid ID inférieurs à 10 000.</span><span class="sxs-lookup"><span data-stu-id="9737d-142">While creating custom functoids, do not use the functoid IDs less than 10000.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9737d-143">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9737d-143">In This Section</span></span>  
 <span data-ttu-id="9737d-144">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="9737d-144">This section contains:</span></span>  
  
-   [<span data-ttu-id="9737d-145">Utilisation de BaseFunctoid</span><span class="sxs-lookup"><span data-stu-id="9737d-145">Using BaseFunctoid</span></span>](../core/using-basefunctoid.md)  
  
-   [<span data-ttu-id="9737d-146">Développement personnalisé référencé fonctoid</span><span class="sxs-lookup"><span data-stu-id="9737d-146">Developing a Custom Referenced Functoid</span></span>](../core/developing-a-custom-referenced-functoid.md)  
  
-   [<span data-ttu-id="9737d-147">Développement d’un fonctoid Inline personnalisé</span><span class="sxs-lookup"><span data-stu-id="9737d-147">Developing a Custom Inline Functoid</span></span>](../core/developing-a-custom-inline-functoid.md)  
  
-   [<span data-ttu-id="9737d-148">Développement d’un fonctoid cumulé personnalisé</span><span class="sxs-lookup"><span data-stu-id="9737d-148">Developing a Custom Cumulative Functoid</span></span>](../core/developing-a-custom-cumulative-functoid.md)  
  
-   [<span data-ttu-id="9737d-149">Ajout et suppression de fonctoids personnalisés à partir de la boîte à outils de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9737d-149">Adding and Removing Custom Functoids from the Visual Studio Toolbox</span></span>](../core/adding-and-removing-custom-functoids-from-the-visual-studio-toolbox.md)  
  
## <a name="see-also"></a><span data-ttu-id="9737d-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9737d-150">See Also</span></span>  
 [<span data-ttu-id="9737d-151">À l’aide des fonctoids pour créer des mappages plus complexes</span><span class="sxs-lookup"><span data-stu-id="9737d-151">Using Functoids to Create More Complex Mappings</span></span>](../core/using-functoids-to-create-more-complex-mappings.md)