---
title: "Considérations relatives à l’utilisation de l’adaptateur Oracle-Business Suite avec SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56de6267-ec34-4bd2-abd1-3f2b69876b36
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69f87b2971eeb9093257bc022ee12cdafed0dbf3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-using-the-oracle-business-suite-adapter-with-sharepoint"></a><span data-ttu-id="f1d28-102">Considérations relatives à l’utilisation de l’adaptateur Oracle-Business Suite avec SharePoint</span><span class="sxs-lookup"><span data-stu-id="f1d28-102">Considerations using the Oracle-Business Suite adapter with SharePoint</span></span>
<span data-ttu-id="f1d28-103">Cette rubrique contient des informations sur les problèmes que vous pouvez rencontrer en utilisant la [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] avec Microsoft Office SharePoint Server, ainsi que des résolutions.</span><span class="sxs-lookup"><span data-stu-id="f1d28-103">This topic contains information about the issues you might encounter while using the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] with Microsoft Office SharePoint Server, along with resolutions.</span></span> <span data-ttu-id="f1d28-104">Les problèmes sont répartis en deux catégories :</span><span class="sxs-lookup"><span data-stu-id="f1d28-104">The issues are divided into two categories:</span></span>  
  
-   <span data-ttu-id="f1d28-105">Problèmes généraux</span><span class="sxs-lookup"><span data-stu-id="f1d28-105">General issues</span></span>  
  
-   <span data-ttu-id="f1d28-106">Problèmes qui impliquent des composants WebPart personnalisés</span><span class="sxs-lookup"><span data-stu-id="f1d28-106">Issues involving custom Web Parts</span></span>  
  
## <a name="general-issues"></a><span data-ttu-id="f1d28-107">Problèmes généraux</span><span class="sxs-lookup"><span data-stu-id="f1d28-107">General Issues</span></span>  
 <span data-ttu-id="f1d28-108">Cette section contient des problèmes qui n’ont aucune solution.</span><span class="sxs-lookup"><span data-stu-id="f1d28-108">This section contains issues that have no resolution.</span></span>  
  
### <a name="issue-1-the-simple-type-data-returned-by-the-wcf-service-is-not-displayed"></a><span data-ttu-id="f1d28-109">Problème 1 : Les données de type simple retournées par le service WCF ne sont pas affichées.</span><span class="sxs-lookup"><span data-stu-id="f1d28-109">Issue 1: The simple type data returned by the WCF service is not displayed</span></span>  
 <span data-ttu-id="f1d28-110">**Explication**: Microsoft Office SharePoint Server attend les données retournées par le service WCF doit être de type jeu de données ou une Collection uniquement.</span><span class="sxs-lookup"><span data-stu-id="f1d28-110">**Explanation**: Microsoft Office SharePoint Server expects the data returned by the WCF service to be of DataSet or Collection type only.</span></span> <span data-ttu-id="f1d28-111">Si les données retournées par le service WCF sont de type simple, Microsoft Office SharePoint Server n’affiche pas les données.</span><span class="sxs-lookup"><span data-stu-id="f1d28-111">If the data returned by the WCF service is of simple type, Microsoft Office SharePoint Server does not display the data.</span></span>  
  
 <span data-ttu-id="f1d28-112">**Résolution**: aucune résolution.</span><span class="sxs-lookup"><span data-stu-id="f1d28-112">**Resolution**: No resolution.</span></span> <span data-ttu-id="f1d28-113">Il s’agit d’une limitation connue avec Microsoft Office SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="f1d28-113">It is a known limitation with Microsoft Office SharePoint Server.</span></span>  
  
### <a name="issue-2-an-error-message-is-displayed-if-the-data-returned-by-the-wcf-service-is-null"></a><span data-ttu-id="f1d28-114">Problème 2 : Un message d’erreur s’affiche si les données retournées par le service WCF sont NULL</span><span class="sxs-lookup"><span data-stu-id="f1d28-114">Issue 2: An error message is displayed if the data returned by the WCF service is NULL</span></span>  
 <span data-ttu-id="f1d28-115">**Explication**: si les données retournées par le service WCF sont une valeur NULL, Microsoft Office SharePoint Server affiche un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f1d28-115">**Explanation**: If the data returned by the WCF service is a NULL value, Microsoft Office SharePoint Server displays an error message.</span></span> <span data-ttu-id="f1d28-116">Par exemple, supposons que vous utilisez le composant WebPart de liste de données métier pour le **recherche** méthode d’instance et recherchez les clients dans Oracle E-Business Suite basée sur une expression de recherche.</span><span class="sxs-lookup"><span data-stu-id="f1d28-116">For example, suppose you are using the Business Data List Web Part for the **Finder** method instance, and are searching for customers in Oracle E-Business Suite based on a search expression.</span></span> <span data-ttu-id="f1d28-117">L’expression de recherche que vous avez spécifié extrait une valeur NULL.</span><span class="sxs-lookup"><span data-stu-id="f1d28-117">The search expression that you specified fetches a NULL value.</span></span> <span data-ttu-id="f1d28-118">Dans ce cas, Microsoft Office SharePoint Server affiche un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f1d28-118">In this case, Microsoft Office SharePoint Server will display an error message.</span></span>  
  
 <span data-ttu-id="f1d28-119">**Résolution**: aucune résolution.</span><span class="sxs-lookup"><span data-stu-id="f1d28-119">**Resolution**: No resolution.</span></span> <span data-ttu-id="f1d28-120">Il s’agit d’une limitation connue avec Microsoft Office SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="f1d28-120">It is a known limitation with Microsoft Office SharePoint Server.</span></span>  
  
### <a name="issue-3-an-array-of-simple-type-returned-by-the-wcf-service-is-not-displayed"></a><span data-ttu-id="f1d28-121">Problème 3 : Un tableau de type simple retourné par le service WCF n’est pas affiché.</span><span class="sxs-lookup"><span data-stu-id="f1d28-121">Issue 3: An array of simple type returned by the WCF service is not displayed</span></span>  
 <span data-ttu-id="f1d28-122">**Explication**: si les données retournées par le service WCF sont un tableau de type simple, Microsoft Office SharePoint Server n’affiche pas les données.</span><span class="sxs-lookup"><span data-stu-id="f1d28-122">**Explanation**: If the data returned by the WCF service is an array of simple type, Microsoft Office SharePoint Server does not display the data.</span></span> <span data-ttu-id="f1d28-123">En outre, lorsque vous exécutez une instance de méthode dans Business Data Catalog Definition Editor qui retourne un tableau de type simple, le message d’erreur suivant s’affiche : « adaptateur de système principal a renvoyé une structure incompatible avec le (métadonnées correspondant MethodInstance, paramètre ou TypeDescriptor). »</span><span class="sxs-lookup"><span data-stu-id="f1d28-123">Moreover, when you execute a method instance in Business Data Catalog Definition Editor that returns an array of simple type, the following error message is displayed: “Backend system adapter returned a structure incompatible with the corresponding metadata (MethodInstance, Parameter or TypeDescriptor).”</span></span>  
  
 <span data-ttu-id="f1d28-124">**Résolution**: aucune résolution.</span><span class="sxs-lookup"><span data-stu-id="f1d28-124">**Resolution**: No resolution.</span></span> <span data-ttu-id="f1d28-125">Il s’agit d’une limitation connue avec Microsoft Office SharePoint Server et Business Data Catalog Definition Editor.</span><span class="sxs-lookup"><span data-stu-id="f1d28-125">It is a known limitation with Microsoft Office SharePoint Server and Business Data Catalog Definition Editor.</span></span>  
  
### <a name="issue-4-cannot-import-an-application-definition-file-that-contains-a-complex-type-parameter-having-more-than-300-fields"></a><span data-ttu-id="f1d28-126">Problème 4 : Impossible d’importer un fichier de définition d’application qui contient un paramètre de type complexe comportant plus de 300 champs</span><span class="sxs-lookup"><span data-stu-id="f1d28-126">Issue 4: Cannot import an application definition file that contains a complex type parameter having more than 300 fields</span></span>  
 <span data-ttu-id="f1d28-127">**Explication**: Microsoft Office SharePoint Server ne peut pas importer un fichier de définition d’application qui n’a plus de 300 dans le paramètre de type complexe retournée par le service WCF et affiche un message d’erreur si vous essayez de le faire.</span><span class="sxs-lookup"><span data-stu-id="f1d28-127">**Explanation**: Microsoft Office SharePoint Server cannot import an application definition file that has more than 300 fields in the complex type parameter returned by the WCF service, and displays an error message if you try to do so.</span></span> <span data-ttu-id="f1d28-128">Cela est dû à la limitation de Microsoft Office SharePoint Server de ne pas pouvoir afficher plus de 300 champs d’un paramètre de type complexe.</span><span class="sxs-lookup"><span data-stu-id="f1d28-128">This is due to the limitation of Microsoft Office SharePoint Server of not being able to display more than 300 fields of a complex type parameter.</span></span>  
  
 <span data-ttu-id="f1d28-129">**Résolution**: utilisez l’éditeur de définition de catalogue de données métier afin de limiter le nombre de champs du paramètre de type complexe à inférieure ou égale à 300.</span><span class="sxs-lookup"><span data-stu-id="f1d28-129">**Resolution**: Use the Business Data Catalog Definition Editor to limit the number of fields of the complex type parameter to less than or equal to 300.</span></span> <span data-ttu-id="f1d28-130">Selon vos besoins, vous pouvez supprimer les champs du paramètre de type complexe dans le Business Data Catalog Definition Editor qui ne doit pas être affiché dans Microsoft Office SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="f1d28-130">Depending on your requirement, you can delete the fields of the complex type parameter in the Business Data Catalog Definition Editor that you do not require to be displayed in Microsoft Office SharePoint Server.</span></span>  <span data-ttu-id="f1d28-131">Ou bien, vous pouvez également exporter le fichier de définition d’application à partir de Business Data Catalog Definition Editor avec tous les champs et ensuite modifier le fichier de définition d’application dans un bloc-notes ou d’une application de création de XML pour supprimer les champs qui ne sont pas requis pour limiter le nombre de champs à 300.</span><span class="sxs-lookup"><span data-stu-id="f1d28-131">Alternatively, you can also export the application definition file from Business Data Catalog Definition Editor with all the fields, and then modify the application definition file in a notepad or any XML authoring application to delete the fields that are not required in order to limit the number of fields to 300.</span></span>  
  
##  <a name="Custom_Web_Part"></a><span data-ttu-id="f1d28-132">Problèmes qui impliquent des composants WebPart personnalisés</span><span class="sxs-lookup"><span data-stu-id="f1d28-132">Issues Involving Custom Web Parts</span></span>  
 <span data-ttu-id="f1d28-133">Cette section contient des problèmes qui requièrent l’utilisation du composant WebPart personnalisé pour une résolution.</span><span class="sxs-lookup"><span data-stu-id="f1d28-133">This section contains issues that require the use of custom Web Part for a resolution.</span></span> <span data-ttu-id="f1d28-134">Pour plus d’informations sur l’utilisation d’un composant WebPart personnalisé pour résoudre les problèmes qui se produit lorsque vous travaillez avec [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] et Microsoft Office SharePoint Server, consultez [l’utilisation d’un composant WebPart personnalisé avec Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/how-to-use-a-custom-web-part-with-oracle-e-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="f1d28-134">For detailed information about using a custom Web Part to resolve issues that might come up while working with [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] and Microsoft Office SharePoint Server, see [How to use a custom web part with Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/how-to-use-a-custom-web-part-with-oracle-e-business-suite.md).</span></span>  
  
###  <a name="Issue1"></a><span data-ttu-id="f1d28-135">Problème 1 : Limite d’affichage d’un enregistrement unique dans Microsoft Office SharePoint Server en fonction de plusieurs valeurs</span><span class="sxs-lookup"><span data-stu-id="f1d28-135">Issue 1: Limitation with displaying a single record in Microsoft Office SharePoint Server based on multiple values</span></span>  
 <span data-ttu-id="f1d28-136">**Explication**: Si vous souhaitez afficher un enregistrement unique dans Microsoft Office SharePoint Server, en fonction de plusieurs valeurs (paramètres d’entrée) à partir d’Oracle E-Business Suite, vous ne pouvez pas utiliser un des trois composants (liste de données d’entreprise, l’élément de données d’entreprise, et Liste liée aux données métier) spécifié à l’étape 3 : créer une Application SharePoint pour récupérer des données à partir d’Oracle E-Business Suite dans [didacticiel : présenter les données à partir d’Oracle E-Business Suite sur un SharePoint Site](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md).</span><span class="sxs-lookup"><span data-stu-id="f1d28-136">**Explanation**: If you want to display a single record in Microsoft Office SharePoint Server based on multiple values (input parameters) from Oracle E-Business Suite, you cannot use any of the three Web Parts (Business Data List, Business Data Item, and Business Data Related List) specified in Step 3: Create a SharePoint Application to Retrieve Data from Oracle E-Business Suite in [Tutorial: Present data from Oracle E-Business Suite on a SharePoint Site](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md).</span></span>  
  
 <span data-ttu-id="f1d28-137">**Résolution**: vous devez utiliser un composant WebPart personnalisé pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="f1d28-137">**Resolution**: You must use a custom Web Part to do this.</span></span> <span data-ttu-id="f1d28-138">Pour plus d’informations sur l’utilisation d’un composant WebPart personnalisé, consultez [l’utilisation d’un composant WebPart personnalisé avec Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/how-to-use-a-custom-web-part-with-oracle-e-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="f1d28-138">For information about using a custom Web Part, see [How to use a custom web part with Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/how-to-use-a-custom-web-part-with-oracle-e-business-suite.md).</span></span> <span data-ttu-id="f1d28-139">Dans « Étape 1 : créer un personnalisé WebPart » de cette rubrique, vous pouvez utiliser l’exemple de code suivant à l’étape 5.</span><span class="sxs-lookup"><span data-stu-id="f1d28-139">In “Step 1: Create a Custom Web Part” of that topic, you can use the following code sample in step 5.</span></span> <span data-ttu-id="f1d28-140">L’exemple de code suivant prend BankCountry et BankKey en tant que paramètres d’entrée, puis de les affiche sous la forme d’un seul enregistrement dans Microsoft Office SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="f1d28-140">The following code sample takes BankCountry and BankKey as the input parameters, and then displays them as a single record in Microsoft Office SharePoint Server.</span></span>  
  
```  
namespace CustomWebPart  
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
            string BankCountry = "US";  
            string BankKey = "134329042";  
  
/***Step 1: Get the required entity and method.***/  
  
            LobSystem newSystem = ApplicationRegistry.GetLobSystems()["BAPI_BANK_GETDETAIL"]; // Name specified in application definition file  
            LobSystemInstance newSystemInstance = newSystem.GetLobSystemInstances()["BAPI_BANK_GETDETAIL_Instance"]; // Name specified in application definition file  
            Entity CategoryEntity = newSystem.GetEntities()["Entity"]; // Name specified in application definition file  
            Method newMethod = CategoryEntity.GetMethods()["BAPI_BANK_GETDETAIL"]; // Name specified in application definition file  
            MethodInstance methodInstance = newMethod.GetMethodInstances()["MethodInstance"]; // Name specified in application definition file  
  
/***Step 2: Get the list of input parameters.***/  
  
            Object[] args = methodInstance.GetMethod().CreateDefaultParameterInstances(methodInstance); //Get the default values of the input parameters.  
            Object[] ArgsInput = new Object[args.Length];  
  
/***Step 3: Assign them required values.***/  
  
            Type t = null;  
            char[] myString = BankCountry.ToCharArray();  
            String s = new String(myString);  
            t = s.GetType();  
            ArgsInput[0] = Activator.CreateInstance(t, myString);  
  
            myString = BankKey.ToCharArray();  
            s = new String(myString);  
            t = s.GetType();  
            ArgsInput[1] = Activator.CreateInstance(t, myString);  
  
/***Step 4: Execute the particular method instance using the required value.***/  
  
            IEntityInstance IE = (IEntityInstance)CategoryEntity.Execute(methodInstance, newSystemInstance, ref ArgsInput); //Method instance of type Specific Finder is being used here.  
  
/***Step 5: Display the output on the custom Web Part in Microsoft Office SharePoint Server.***/  
  
            writer.Write("<table>");  
            writer.Write("<tr>");  
            foreach (Field f in CategoryEntity.GetFinderView().Fields)  
            {  
                writer.Write("<td>");  
                writer.Write(IE[f]);  
                writer.Write("</td>");  
            }  
            writer.Write("</tr>");  
            writer.Write("</table>");  
        }  
    }  
  
```  
  
> [!NOTE]
>  <span data-ttu-id="f1d28-141">Le fichier de définition d’application doit contenir le **recherche spécifique** instance de méthode.</span><span class="sxs-lookup"><span data-stu-id="f1d28-141">The application definition file must contain the **Specific Finder** method instance.</span></span> <span data-ttu-id="f1d28-142">A **recherche spécifique** méthode trouve un enregistrement spécifique en fonction d’un identificateur.</span><span class="sxs-lookup"><span data-stu-id="f1d28-142">A **Specific Finder** method finds a specific record based on an identifier.</span></span> <span data-ttu-id="f1d28-143">Pour plus d’informations sur la création d’un **recherche spécifique** méthode instance, consultez « Exigence 2 : récupérer détails pour un client à partir de la liste de clients spécifiques » dans [étape 2 : créer un fichier de définition d’application pour le Artefacts de Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md) dans [didacticiel : présenter les données à partir d’Oracle E-Business Suite sur un SharePoint Site](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md).</span><span class="sxs-lookup"><span data-stu-id="f1d28-143">For information about creating a **Specific Finder** method instance, see “Requirement 2: Retrieve Details for a Specific Customer from the List of Customers” in [Step 2: Create an application definition file for the Oracle E-Business Suite artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md) in [Tutorial: Present data from Oracle E-Business Suite on a SharePoint Site](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md).</span></span>  
  
### <a name="issue-2-cannot-specify-values-to-array-elements"></a><span data-ttu-id="f1d28-144">Problème 2 : Ne peut pas spécifier des valeurs pour les éléments de tableau</span><span class="sxs-lookup"><span data-stu-id="f1d28-144">Issue 2: Cannot specify values to array elements</span></span>  
 <span data-ttu-id="f1d28-145">**Explication**: si le paramètre d’entrée du service WCF est un tableau, vous ne pouvez pas spécifier des valeurs pour les éléments du tableau à l’aide de filtres qui sont définis dans le fichier de définition d’application créé à l’aide de l’éditeur de définition de catalogue de données métier.</span><span class="sxs-lookup"><span data-stu-id="f1d28-145">**Explanation**: If the input parameter of the WCF service is an array, you cannot specify values to the array elements using filters that are defined in the application definition file created using the Business Data Catalog Definition Editor.</span></span> <span data-ttu-id="f1d28-146">Cela implique que vous ne pouvez pas utiliser la liste de données d’entreprise ou d’un WebPart élément de données métier dans Microsoft Office SharePoint Server pour spécifier des valeurs pour ces paramètres d’entrée (éléments du tableau) pour le service WCF.</span><span class="sxs-lookup"><span data-stu-id="f1d28-146">It implies that you cannot use the Business Data List or Business Data Item Web Part in Microsoft Office SharePoint Server to specify values for these input parameters (elements of array) to the WCF service.</span></span> <span data-ttu-id="f1d28-147">Il s’agit en raison du mode tableaux sont définis dans le fichier de définition d’application.</span><span class="sxs-lookup"><span data-stu-id="f1d28-147">This is because of the way arrays are defined in the application definition file.</span></span>  
  
 <span data-ttu-id="f1d28-148">**Résolution**: utiliser un composant WebPart personnalisé pour affecter des valeurs aux éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="f1d28-148">**Resolution**: Use a custom Web Part to assign values to array elements.</span></span> <span data-ttu-id="f1d28-149">Pour plus d’informations sur l’utilisation d’un composant WebPart personnalisé, consultez [l’utilisation d’un composant WebPart personnalisé avec Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/how-to-use-a-custom-web-part-with-oracle-e-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="f1d28-149">For information about using a custom Web Part, see [How to use a custom web part with Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/how-to-use-a-custom-web-part-with-oracle-e-business-suite.md).</span></span> <span data-ttu-id="f1d28-150">Par exemple, vous pouvez utiliser l’exemple de code suivant à l’étape 3 de « problème 1 : Limitation avec affichage d’un enregistrement unique dans Microsoft Office SharePoint Server en fonction de plusieurs valeurs » pour affecter des valeurs aux éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="f1d28-150">For example, you can use the following code sample in step 3 in “Issue 1: Limitation with displaying a single record in Microsoft Office SharePoint Server based on multiple values” to assign values to array elements.</span></span>  
  
```  
/***Assign required values to parameters of type array.***/   
/***Assumption is that the ith parameter of Method is of type Array and all the simple type elements in the array are of string type.***/  
  
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
  
### <a name="issue-3-limitation-with-specifying-null-values-to-complex-type-parameters"></a><span data-ttu-id="f1d28-151">Problème 3 : Limitation en spécifiant des valeurs NULL pour les paramètres de type complexe</span><span class="sxs-lookup"><span data-stu-id="f1d28-151">Issue 3: Limitation with specifying NULL values to complex type parameters</span></span>  
 <span data-ttu-id="f1d28-152">**Explication**: Si vous ne spécifiez pas de valeur pour un paramètre de type complexe à partir d’un composant WebPart dans Microsoft Office SharePoint Server, NULL doit être transmise en tant que la valeur pour le paramètre de type complexe pour le service WCF.</span><span class="sxs-lookup"><span data-stu-id="f1d28-152">**Explanation**: If you do not specify any value for a complex type parameter from a Web Part in Microsoft Office SharePoint Server, NULL should be passed on as the value for the complex type parameter to the WCF service.</span></span> <span data-ttu-id="f1d28-153">Toutefois, une valeur non NULL est passée pour le paramètre de type complexe, et NULL est passée pour ses éléments enfants (de type simple).</span><span class="sxs-lookup"><span data-stu-id="f1d28-153">However, a non-NULL value is passed for the complex type parameter, and NULL is passed for its children elements (of simple type).</span></span> <span data-ttu-id="f1d28-154">Cela provoque une incompatibilité entre le schéma de message attendu et le schéma de message qui est transmis au service WCF.</span><span class="sxs-lookup"><span data-stu-id="f1d28-154">This causes a mismatch between the expected message schema and the message schema that is passed on to the WCF service.</span></span> <span data-ttu-id="f1d28-155">Par conséquent, le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] peut afficher un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f1d28-155">As a result, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] might display an error message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1d28-156">Pour déterminer la valeur par défaut d’un paramètre de type complexe lorsqu’aucune valeur n’est passée à partir d’un composant WebPart dans Microsoft Office SharePoint Server, utilisez l’étape 2 dans l’exemple de code indiqué dans « erreur 1 : limite d’affichage d’un enregistrement unique dans Microsoft Office SharePoint Server en fonction de plusieurs valeurs. »</span><span class="sxs-lookup"><span data-stu-id="f1d28-156">To find out the default value of a complex type parameter when no value is passed from a Web Part in Microsoft Office SharePoint Server, use step 2 in the code sample mentioned in “Issue 1: Limitation with displaying a single record in Microsoft Office SharePoint Server based on multiple values.”</span></span>  
  
 <span data-ttu-id="f1d28-157">**Résolution**: un composant WebPart personnalisé permet d’attribuer une valeur NULL au paramètre de type complexe.</span><span class="sxs-lookup"><span data-stu-id="f1d28-157">**Resolution**: Use a custom Web Part to assign a NULL value to the complex type parameter.</span></span> <span data-ttu-id="f1d28-158">Pour plus d’informations sur l’utilisation d’un composant WebPart personnalisé, consultez [l’utilisation d’un composant WebPart personnalisé avec Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/how-to-use-a-custom-web-part-with-oracle-e-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="f1d28-158">For information about using a custom Web Part, see [How to use a custom web part with Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/how-to-use-a-custom-web-part-with-oracle-e-business-suite.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1d28-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1d28-159">See Also</span></span>  
[<span data-ttu-id="f1d28-160">Utilisez l’adaptateur Oracle E-Business Suite avec SharePoint</span><span class="sxs-lookup"><span data-stu-id="f1d28-160">Use the Oracle E-Business Suite adapter with SharePoint</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/use-the-oracle-e-business-suite-adapter-with-sharepoint.md)