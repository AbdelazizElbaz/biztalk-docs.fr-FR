---
title: "Considérations sur l’utilisation de l’adaptateur Siebel avec SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea7da079-3250-4ecc-bf01-6b5495c7f380
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1df22d3eb20dc6286d5b85c3648db98518f23e37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-when-using-the-siebel-adapter-with-sharepoint"></a><span data-ttu-id="83952-102">Considérations sur l’utilisation de l’adaptateur Siebel avec SharePoint</span><span class="sxs-lookup"><span data-stu-id="83952-102">Considerations when using the Siebel adapter with SharePoint</span></span>
<span data-ttu-id="83952-103">Cette rubrique contient des informations sur les problèmes que vous pouvez rencontrer en utilisant la [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] avec Microsoft Office SharePoint Server, ainsi que des résolutions.</span><span class="sxs-lookup"><span data-stu-id="83952-103">This topic contains information about the issues you might encounter while using the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] with Microsoft Office SharePoint Server, along with resolutions.</span></span> <span data-ttu-id="83952-104">Les problèmes sont répartis en deux catégories :</span><span class="sxs-lookup"><span data-stu-id="83952-104">The issues are divided into two categories:</span></span>  
  
-   <span data-ttu-id="83952-105">Problèmes généraux</span><span class="sxs-lookup"><span data-stu-id="83952-105">General issues</span></span>  
  
-   <span data-ttu-id="83952-106">Problèmes qui impliquent des composants WebPart personnalisés</span><span class="sxs-lookup"><span data-stu-id="83952-106">Issues involving custom Web Parts</span></span>  
  
## <a name="general-issues"></a><span data-ttu-id="83952-107">Problèmes généraux</span><span class="sxs-lookup"><span data-stu-id="83952-107">General Issues</span></span>  
 <span data-ttu-id="83952-108">Cette section contient des problèmes qui n’ont aucune solution ou, vous devez modifier le fichier de définition d’application pour la résolution.</span><span class="sxs-lookup"><span data-stu-id="83952-108">This section contains issues that either have no resolution or requires you to modify the application definition file for the resolution.</span></span>  
  
### <a name="issue-1-the-simple-type-data-returned-by-the-wcf-service-is-not-displayed"></a><span data-ttu-id="83952-109">Problème 1 : Les données de type simple retournées par le service WCF ne sont pas affichées.</span><span class="sxs-lookup"><span data-stu-id="83952-109">Issue 1: The simple type data returned by the WCF service is not displayed</span></span>  
 <span data-ttu-id="83952-110">**Explication**: Microsoft Office SharePoint Server attend les données retournées par le service WCF doit être de type jeu de données ou une Collection uniquement.</span><span class="sxs-lookup"><span data-stu-id="83952-110">**Explanation**: Microsoft Office SharePoint Server expects the data returned by the WCF service to be of DataSet or Collection type only.</span></span> <span data-ttu-id="83952-111">Si les données retournées par le service WCF sont de type simple, Microsoft Office SharePoint Server n’affiche pas les données.</span><span class="sxs-lookup"><span data-stu-id="83952-111">If the data returned by the WCF service is of simple type, Microsoft Office SharePoint Server does not display the data.</span></span>  
  
 <span data-ttu-id="83952-112">**Résolution**: aucune résolution.</span><span class="sxs-lookup"><span data-stu-id="83952-112">**Resolution**: No resolution.</span></span> <span data-ttu-id="83952-113">Il s’agit d’une limitation connue avec Microsoft Office SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="83952-113">It is a known limitation with Microsoft Office SharePoint Server.</span></span>  
  
### <a name="issue-2-an-error-message-is-displayed-if-the-data-returned-by-the-wcf-service-is-null"></a><span data-ttu-id="83952-114">Problème 2 : Un message d’erreur s’affiche si les données retournées par le service WCF sont NULL</span><span class="sxs-lookup"><span data-stu-id="83952-114">Issue 2: An error message is displayed if the data returned by the WCF service is NULL</span></span>  
 <span data-ttu-id="83952-115">**Explication**: si les données retournées par le service WCF sont une valeur NULL, Microsoft Office SharePoint Server affiche un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="83952-115">**Explanation**: If the data returned by the WCF service is a NULL value, Microsoft Office SharePoint Server displays an error message.</span></span> <span data-ttu-id="83952-116">Par exemple, supposons que vous utilisez le composant WebPart de liste de données métier pour le **recherche** méthode d’instance et recherchez des clients dans le système Siebel basé sur une expression de recherche.</span><span class="sxs-lookup"><span data-stu-id="83952-116">For example, suppose you are using the Business Data List Web Part for the **Finder** method instance, and are searching for customers in the Siebel system based on a search expression.</span></span> <span data-ttu-id="83952-117">L’expression de recherche que vous avez spécifié extrait une valeur NULL.</span><span class="sxs-lookup"><span data-stu-id="83952-117">The search expression that you specified fetches a NULL value.</span></span> <span data-ttu-id="83952-118">Dans ce cas, Microsoft Office SharePoint Server affiche un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="83952-118">In this case, Microsoft Office SharePoint Server will display an error message.</span></span>  
  
 <span data-ttu-id="83952-119">**Résolution**: aucune résolution.</span><span class="sxs-lookup"><span data-stu-id="83952-119">**Resolution**: No resolution.</span></span> <span data-ttu-id="83952-120">Il s’agit d’une limitation connue avec Microsoft Office SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="83952-120">It is a known limitation with Microsoft Office SharePoint Server.</span></span>  
  
### <a name="issue-3-an-array-of-simple-type-returned-by-the-wcf-service-is-not-displayed"></a><span data-ttu-id="83952-121">Problème 3 : Un tableau de type simple retourné par le service WCF n’est pas affiché.</span><span class="sxs-lookup"><span data-stu-id="83952-121">Issue 3: An array of simple type returned by the WCF service is not displayed</span></span>  
 <span data-ttu-id="83952-122">**Explication**: si les données retournées par le service WCF sont un tableau de type simple, Microsoft Office SharePoint Server n’affiche pas les données.</span><span class="sxs-lookup"><span data-stu-id="83952-122">**Explanation**: If the data returned by the WCF service is an array of simple type, Microsoft Office SharePoint Server does not display the data.</span></span> <span data-ttu-id="83952-123">En outre, lorsque vous exécutez une instance de méthode dans Business Data Catalog Definition Editor qui retourne un tableau de type simple, le message d’erreur suivant s’affiche : « adaptateur de système principal a renvoyé une structure incompatible avec le (métadonnées correspondant MethodInstance, paramètre ou TypeDescriptor). »</span><span class="sxs-lookup"><span data-stu-id="83952-123">Moreover, when you execute a method instance in Business Data Catalog Definition Editor that returns an array of simple type, the following error message is displayed: “Backend system adapter returned a structure incompatible with the corresponding metadata (MethodInstance, Parameter or TypeDescriptor).”</span></span>  
  
 <span data-ttu-id="83952-124">**Résolution**: aucune résolution.</span><span class="sxs-lookup"><span data-stu-id="83952-124">**Resolution**: No resolution.</span></span> <span data-ttu-id="83952-125">Il s’agit d’une limitation connue avec Microsoft Office SharePoint Server et Business Data Catalog Definition Editor.</span><span class="sxs-lookup"><span data-stu-id="83952-125">It is a known limitation with Microsoft Office SharePoint Server and Business Data Catalog Definition Editor.</span></span>  
  
### <a name="issue-4-cannot-import-an-application-definition-file-that-contains-a-complex-type-parameter-having-more-than-300-fields"></a><span data-ttu-id="83952-126">Problème 4 : Impossible d’importer un fichier de définition d’application qui contient un paramètre de type complexe comportant plus de 300 champs</span><span class="sxs-lookup"><span data-stu-id="83952-126">Issue 4: Cannot import an application definition file that contains a complex type parameter having more than 300 fields</span></span>  
 <span data-ttu-id="83952-127">**Explication**: Microsoft Office SharePoint Server ne peut pas importer un fichier de définition d’application qui n’a plus de 300 dans le paramètre de type complexe retournée par le service WCF et affiche un message d’erreur si vous essayez de le faire.</span><span class="sxs-lookup"><span data-stu-id="83952-127">**Explanation**: Microsoft Office SharePoint Server cannot import an application definition file that has more than 300 fields in the complex type parameter returned by the WCF service, and displays an error message if you try to do so.</span></span> <span data-ttu-id="83952-128">Cela est dû à la limitation de Microsoft Office SharePoint Server de ne pas pouvoir afficher plus de 300 champs d’un paramètre de type complexe.</span><span class="sxs-lookup"><span data-stu-id="83952-128">This is due to the limitation of Microsoft Office SharePoint Server of not being able to display more than 300 fields of a complex type parameter.</span></span>  
  
 <span data-ttu-id="83952-129">**Résolution**: utilisez l’éditeur de définition de catalogue de données métier afin de limiter le nombre de champs du paramètre de type complexe à inférieure ou égale à 300.</span><span class="sxs-lookup"><span data-stu-id="83952-129">**Resolution**: Use the Business Data Catalog Definition Editor to limit the number of fields of the complex type parameter to less than or equal to 300.</span></span> <span data-ttu-id="83952-130">Selon vos besoins, vous pouvez supprimer les champs du paramètre de type complexe dans le Business Data Catalog Definition Editor qui ne doit pas être affiché dans Microsoft Office SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="83952-130">Depending on your requirement, you can delete the fields of the complex type parameter in the Business Data Catalog Definition Editor that you do not require to be displayed in Microsoft Office SharePoint Server.</span></span>  <span data-ttu-id="83952-131">Ou bien, vous pouvez également exporter le fichier de définition d’application à partir de Business Data Catalog Definition Editor avec tous les champs et ensuite modifier le fichier de définition d’application dans un bloc-notes ou d’une application de création de XML pour supprimer les champs qui ne sont pas requis pour limiter le nombre de champs à 300.</span><span class="sxs-lookup"><span data-stu-id="83952-131">Alternatively, you can also export the application definition file from Business Data Catalog Definition Editor with all the fields, and then modify the application definition file in a notepad or any XML authoring application to delete the fields that are not required in order to limit the number of fields to 300.</span></span>  
  
##  <span data-ttu-id="83952-132"><a name="Custom_Web_Part"></a>Problèmes qui impliquent des composants WebPart personnalisés</span><span class="sxs-lookup"><span data-stu-id="83952-132"><a name="Custom_Web_Part"></a> Issues Involving Custom Web Parts</span></span>  
 <span data-ttu-id="83952-133">Cette section contient des problèmes qui requièrent l’utilisation de composants WebPart personnalisés pour la résolution.</span><span class="sxs-lookup"><span data-stu-id="83952-133">This section contains issues that require the use of custom Web Parts for resolution.</span></span> <span data-ttu-id="83952-134">Pour plus d’informations sur l’utilisation d’un composant WebPart personnalisé pour résoudre les problèmes qui se produit lorsque vous travaillez avec [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] et Microsoft Office SharePoint Server, consultez [utiliser un composant WebPart personnalisé avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/use-a-custom-web-part-with-the-siebel-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="83952-134">For detailed information about using a custom Web Part to resolve issues that might come up while working with [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] and Microsoft Office SharePoint Server, see [Use a Custom Web Part with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/use-a-custom-web-part-with-the-siebel-adapter.md).</span></span>  
  
### <a name="issue-1-index-of-an-enumerator-is-displayed-instead-of-the-value-for-the-enum-data-type"></a><span data-ttu-id="83952-135">Problème 1 : Les Index d’un énumérateur s’affiche au lieu de la valeur pour le type de données d’enum</span><span class="sxs-lookup"><span data-stu-id="83952-135">Issue 1: Index of an enumerator is displayed instead of the value for the enum data type</span></span>  
 <span data-ttu-id="83952-136">**Explication**: si une liste de données métiers ou un élément de données Business WebPart dans Microsoft Office SharePoint Server contient des données de type d’enum (un type distinct constitué d’un ensemble de constantes nommées, appelées énumérateurs), l’index de l’énumérateur est affiché au lieu de sa valeur dans Microsoft Office SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="83952-136">**Explanation**: If a Business Data List or Business Data Item Web Part in Microsoft Office SharePoint Server contains data of enum type (a distinct type consisting of a set of named constants called the enumerators), the index of the enumerator is displayed instead of its value in Microsoft Office SharePoint Server.</span></span> <span data-ttu-id="83952-137">Il s’agit, car la liste de données métiers et WebPart élément de données métiers incorrectement impriment les valeurs de l’énumération de type de données sur le portail SharePoint.</span><span class="sxs-lookup"><span data-stu-id="83952-137">This is because the Business Data List and Business Data Item Web Parts incorrectly print the values of the enum type data to the SharePoint portal.</span></span>  
  
 <span data-ttu-id="83952-138">**Résolution**: un composant WebPart personnalisé permet d’imprimer la valeur de l’énumérateur au lieu de l’index.</span><span class="sxs-lookup"><span data-stu-id="83952-138">**Resolution**: Use a custom Web Part to print the value of the enumerator instead of the index.</span></span> <span data-ttu-id="83952-139">Pour plus d’informations sur l’utilisation d’un composant WebPart personnalisé, consultez [utiliser un composant WebPart personnalisé avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/use-a-custom-web-part-with-the-siebel-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="83952-139">For information about using a custom Web Part, see [Use a Custom Web Part with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/use-a-custom-web-part-with-the-siebel-adapter.md).</span></span> <span data-ttu-id="83952-140">Par exemple, vous pouvez utiliser l’exemple de code suivant dans votre composant WebPart pour imprimer les valeurs correctes enum de type de données sur Microsoft Office SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="83952-140">For example, you can use the following code sample in your Web part to print the correct values of enum type data on Microsoft Office SharePoint Server.</span></span>  
  
```  
namespace CustomWebpart  
{  
    public class CustomWebPart : WebPart  
    {  
        private string displayText = "Hello World!";  
  
        [WebBrowsable(true), Personalizable(true)]  
        public string DisplayText  
        {  
            get { return displayText; }  
            set { displayText = value; }  
        }  
        protected override void Render(System.Web.UI.HtmlTextWriter writer)  
        {  
            string SearchExpr = "[Address Name] LIKE \"*\"";  
            object ElementType = null;  
  
/***Step 1: Get the required entity and method.***/  
  
            LobSystem newSystem = ApplicationRegistry.GetLobSystems()["WebServiceLobSystem"]; // Name specified in application definition file  
            LobSystemInstance newSystemInstance = newSystem.GetLobSystemInstances()["Siebel_Instance"]; // Name specified in application definition file  
            Entity CategoryEntity = newSystem.GetEntities()["Siebel_Method_Name"]; // Name specified in application definition file  
            Method newMethod = CategoryEntity.GetMethods()["Query"]; // Name specified in application definition file  
            MethodInstance methodInstance = newMethod.GetMethodInstances()["MethodInstance0"]; // Name specified in application definition file  
  
/***Step 2: Get the list of input parameters.***/  
            Object[] args = methodInstance.GetMethod().CreateDefaultParameterInstances(methodInstance); // Get default value of the input parameter  
            Object[] ArgsInput = new Object[args.Length];  
  
/***Step 3: Assign them required values.***/  
  
           //Assigning values to a complex type parameter. Index of this parameter is 3rd in args array.   
           /*** Complex Type Parameter is defined as follows:  
           <Parameter Direction="In" Name="BusinessAddressQueryInputRecord">  
           <TypeDescriptor TypeName="BDC.BusinessAddressQueryInputRecord,WebServiceLobSystem" Name="BusinessAddressQueryInputRecord">  
              <TypeDescriptors>  
                 <TypeDescriptor TypeName="System.String, ...." Name="SearchExpr"></TypeDescriptor>  
                 <TypeDescriptor TypeName="System.String, ...." Name="SortSpec"></TypeDescriptor>  
                 <TypeDescriptor TypeName="System.String[], ...." IsCollection="true" Name="QueryFields"></TypeDescriptor>  
              </TypeDescriptors>  
           </TypeDescriptor>  
           </Parameter>  
            * We are assigning value to Parameter SearchExpr. ***/  
  
            Assembly asm = Assembly.GetAssembly(args[2].GetType());  
            Type t = asm.GetType(args[2].GetType().ToString()); // Get type of the parameter  
  
            FieldInfo[] FI = t.GetFields();  
            ElementType = Activator.CreateInstance(t);  
            ElementType.GetType().GetFields()[0].SetValue(ElementType, (Object)SearchExpr);  
  
            ArgsInput[2] = ElementType; // ArgsInput is fed as input while executing Method Instance.  
  
/***Step 4: Execute the particular method instance using the required value.***/              
  
            IEntityInstanceEnumerator prodEntityInstanceEnumerator = (IEntityInstanceEnumerator)CategoryEntity.Execute(methodInstance, newSystemInstance, ref ArgsInput); //Method instance of type Finder is being used here.  
  
/***Step 5: Display the output on the custom Web Part in Microsoft Office SharePoint Server.***/  
  
            writer.Write("<table>");  
            while (prodEntityInstanceEnumerator.MoveNext())  
            {  
                IEntityInstance IE = prodEntityInstanceEnumerator.Current;  
  
                writer.Write("<tr>");  
                foreach (Field f in CategoryEntity.GetFinderView().Fields)  
                {  
  
                    writer.Write("<td>");  
                    writer.Write(IE[f]);  
                    writer.Write("</td>");  
                }  
                writer.Write("</tr>");  
            }  
            writer.Write("</table>");  
  
        }  
    }  
}  
  
```  
  
### <a name="issue-2-cannot-specify-values-to-array-elements"></a><span data-ttu-id="83952-141">Problème 2 : Ne peut pas spécifier des valeurs pour les éléments de tableau</span><span class="sxs-lookup"><span data-stu-id="83952-141">Issue 2: Cannot specify values to array elements</span></span>  
 <span data-ttu-id="83952-142">**Explication**: si le paramètre d’entrée du service WCF est un tableau, vous ne pouvez pas spécifier des valeurs pour les éléments du tableau à l’aide de filtres qui sont définis dans le fichier de définition d’application créé à l’aide de l’éditeur de définition de catalogue de données métier.</span><span class="sxs-lookup"><span data-stu-id="83952-142">**Explanation**: If the input parameter of the WCF service is an array, you cannot specify values to the array elements using filters that are defined in the application definition file created using the Business Data Catalog Definition Editor.</span></span> <span data-ttu-id="83952-143">Cela implique que vous ne pouvez pas utiliser la liste de données d’entreprise ou d’un WebPart élément de données métier dans Microsoft Office SharePoint Server pour spécifier des valeurs pour ces paramètres d’entrée (éléments du tableau) pour le service WCF.</span><span class="sxs-lookup"><span data-stu-id="83952-143">It implies that you cannot use the Business Data List or Business Data Item Web Part in Microsoft Office SharePoint Server to specify values for these input parameters (elements of array) to the WCF service.</span></span> <span data-ttu-id="83952-144">Il s’agit en raison du mode tableaux sont définis dans le fichier de définition d’application.</span><span class="sxs-lookup"><span data-stu-id="83952-144">This is because of the way arrays are defined in the application definition file.</span></span>  
  
 <span data-ttu-id="83952-145">**Résolution**: utiliser un composant WebPart personnalisé pour affecter des valeurs aux éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="83952-145">**Resolution**: Use a custom Web Part to assign values to array elements.</span></span> <span data-ttu-id="83952-146">Pour plus d’informations sur l’utilisation d’un composant WebPart personnalisé, consultez [utiliser un composant WebPart personnalisé avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/use-a-custom-web-part-with-the-siebel-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="83952-146">For information about using a custom Web Part, see [Use a Custom Web Part with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/use-a-custom-web-part-with-the-siebel-adapter.md).</span></span> <span data-ttu-id="83952-147">Par exemple, vous pouvez utiliser l’exemple de code suivant à l’étape 3 de « problème 1 : Index d’un énumérateur s’affiche au lieu de la valeur pour le type de données d’énumération « pour affecter des valeurs aux éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="83952-147">For example, you can use the following code sample in step 3 in “Issue 1: Index of an enumerator is displayed instead of the value for the enum data type” to assign values to array elements.</span></span>  
  
```  
/***Assign required values to parameters of type array.***/   
/***Assumption is that the ith parameter of Method is of type Array and all the simple type elements in the array are of type string***/  
  
            Type t = asm.GetType(args[i].GetType().ToString()); // Get type of the parameter  
            Type TElement = t.GetElementType(); // Getting type of element of array  
            int index = 5; //Size of Array  
            Array ElementArray = Array.CreateInstance(TElement, index); //Creating an array of length: index  
  
            for (int ind = 0; ind < index; ind++)  
            {  
                //Creating an instance of an element of array  
                object ElementType = Activator.CreateInstance(TElement);  
                FieldInfo[] FI = ElementType.GetType().GetFields();  
                for (int f = 0; f \< FI.Length; f++)  
                {  
                    ElementType.GetType().GetFields()[f].SetValue(ElementType, (Object)"ElementValue");  
                }  
                ElementArray.SetValue(ElementType, ind);  
            }  
  
            ArgsInput[i] = (object)ElementArray; // As shown in sample, ArgsInput is fed as input while executing Method Instance  
  
```  
  
### <a name="issue-3-limitation-with-specifying-null-values-to-complex-type-parameters"></a><span data-ttu-id="83952-148">Problème 3 : Limitation en spécifiant des valeurs NULL pour les paramètres de type complexe</span><span class="sxs-lookup"><span data-stu-id="83952-148">Issue 3: Limitation with specifying NULL values to complex type parameters</span></span>  
 <span data-ttu-id="83952-149">**Explication**: Si vous ne spécifiez pas de valeur pour un paramètre de type complexe à partir d’un composant WebPart dans Microsoft Office SharePoint Server, NULL doit être transmise en tant que la valeur pour le paramètre de type complexe pour le service WCF.</span><span class="sxs-lookup"><span data-stu-id="83952-149">**Explanation**: If you do not specify any value for a complex type parameter from a Web Part in Microsoft Office SharePoint Server, NULL should be passed on as the value for the complex type parameter to the WCF service.</span></span> <span data-ttu-id="83952-150">Toutefois, une valeur non NULL est passée pour le paramètre de type complexe, et NULL est passée pour ses éléments enfants (de type simple).</span><span class="sxs-lookup"><span data-stu-id="83952-150">However, a non-NULL value is passed for the complex type parameter, and NULL is passed for its children elements (of simple type).</span></span> <span data-ttu-id="83952-151">Cela provoque une incompatibilité entre le schéma de message attendu et le schéma de message qui est transmis au service WCF.</span><span class="sxs-lookup"><span data-stu-id="83952-151">This causes a mismatch between the expected message schema and the message schema that is passed on to the WCF service.</span></span> <span data-ttu-id="83952-152">Par conséquent, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] peut afficher un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="83952-152">As a result, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] might display an error message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83952-153">Pour déterminer la valeur par défaut d’un paramètre de type complexe lorsqu’aucune valeur n’est passée à partir d’un composant WebPart dans Microsoft Office SharePoint Server, utilisez l’étape 2 dans l’exemple de code indiqué dans « erreur 1 : Index d’un énumérateur s’affiche au lieu de la valeur pour le type de données d’enum. »</span><span class="sxs-lookup"><span data-stu-id="83952-153">To find out the default value of a complex type parameter when no value is passed from a Web Part in Microsoft Office SharePoint Server, use step 2 in the code sample mentioned in “Issue 1: Index of an enumerator is displayed instead of the value for the enum data type.”</span></span>  
  
 <span data-ttu-id="83952-154">**Résolution**: un composant WebPart personnalisé permet d’attribuer une valeur NULL au paramètre de type complexe lorsque aucune valeur n’est spécifiée à partir d’un composant WebPart dans Microsoft Office SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="83952-154">**Resolution**: Use a custom Web Part to assign a NULL value to the complex type parameter when no value is specified from a Web Part in Microsoft Office SharePoint Server.</span></span> <span data-ttu-id="83952-155">Pour plus d’informations sur l’utilisation d’un composant WebPart personnalisé, consultez [utiliser un composant WebPart personnalisé avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/use-a-custom-web-part-with-the-siebel-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="83952-155">For information about using a custom Web Part, see [Use a Custom Web Part with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/use-a-custom-web-part-with-the-siebel-adapter.md).</span></span>  
  
###  <span data-ttu-id="83952-156"><a name="Issue1"></a>Problème 4 : Limitation avec affichage d’un enregistrement unique dans Microsoft Office SharePoint Server en fonction de plusieurs valeurs</span><span class="sxs-lookup"><span data-stu-id="83952-156"><a name="Issue1"></a> Issue 4: Limitation with displaying a single record in Microsoft Office SharePoint Server based on multiple values</span></span>  
 <span data-ttu-id="83952-157">**Explication**: Si vous souhaitez afficher un enregistrement unique dans Microsoft Office SharePoint Server, en fonction de plusieurs valeurs (paramètres d’entrée) à partir d’un système Siebel, vous ne pouvez pas utiliser un des trois composants (liste de données métiers, élément de données d’entreprise et Professionnel Liste liée aux données) spécifié dans [étape 3 : créer une Application SharePoint pour récupérer des données à partir de Siebel](../../adapters-and-accelerators/adapter-siebel/step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel.md) dans [didacticiel 1 : présentation sur un SharePoint Site de données à partir de système Siebel](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md).</span><span class="sxs-lookup"><span data-stu-id="83952-157">**Explanation**: If you want to display a single record in Microsoft Office SharePoint Server based on multiple values (input parameters) from a Siebel system, you cannot use any of the three Web Parts (Business Data List, Business Data Item, and Business Data Related List) specified in [Step 3: Create a SharePoint Application to Retrieve Data from Siebel](../../adapters-and-accelerators/adapter-siebel/step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel.md) in [Tutorial 1: Presenting Data From a Siebel System on a SharePoint Site](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md).</span></span>  
  
 <span data-ttu-id="83952-158">**Résolution**: vous devez utiliser un composant WebPart personnalisé pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="83952-158">**Resolution**: You must use a custom Web Part to do this.</span></span> <span data-ttu-id="83952-159">Pour plus d’informations sur l’utilisation d’un composant WebPart personnalisé, consultez [utiliser un composant WebPart personnalisé avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/use-a-custom-web-part-with-the-siebel-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="83952-159">For information about using a custom Web Part, see [Use a Custom Web Part with the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/use-a-custom-web-part-with-the-siebel-adapter.md).</span></span> <span data-ttu-id="83952-160">Par exemple, à l’étape 3 « problème 1 : Index d’un énumérateur s’affiche au lieu de la valeur pour le type de données d’enum « vous pouvez modifier le code pour fournir des valeurs pour plusieurs paramètres au lieu de fournir une entrée à un paramètre de composant d’entreprise unique.</span><span class="sxs-lookup"><span data-stu-id="83952-160">For example, in step 3 in “Issue 1: Index of an enumerator is displayed instead of the value for the enum data type” you can modify the code to provide values for more than one parameter instead of providing input to a single business component parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83952-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83952-161">See Also</span></span>  
 [<span data-ttu-id="83952-162">Utilisez l’adaptateur Siebel avec SharePoint</span><span class="sxs-lookup"><span data-stu-id="83952-162">Use the Siebel Adapter with SharePoint</span></span>](../../adapters-and-accelerators/adapter-siebel/use-the-siebel-adapter-with-sharepoint.md)