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
# <a name="considerations-when-using-the-siebel-adapter-with-sharepoint"></a>Considérations sur l’utilisation de l’adaptateur Siebel avec SharePoint
Cette rubrique contient des informations sur les problèmes que vous pouvez rencontrer en utilisant la [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] avec Microsoft Office SharePoint Server, ainsi que des résolutions. Les problèmes sont répartis en deux catégories :  
  
-   Problèmes généraux  
  
-   Problèmes qui impliquent des composants WebPart personnalisés  
  
## <a name="general-issues"></a>Problèmes généraux  
 Cette section contient des problèmes qui n’ont aucune solution ou, vous devez modifier le fichier de définition d’application pour la résolution.  
  
### <a name="issue-1-the-simple-type-data-returned-by-the-wcf-service-is-not-displayed"></a>Problème 1 : Les données de type simple retournées par le service WCF ne sont pas affichées.  
 **Explication**: Microsoft Office SharePoint Server attend les données retournées par le service WCF doit être de type jeu de données ou une Collection uniquement. Si les données retournées par le service WCF sont de type simple, Microsoft Office SharePoint Server n’affiche pas les données.  
  
 **Résolution**: aucune résolution. Il s’agit d’une limitation connue avec Microsoft Office SharePoint Server.  
  
### <a name="issue-2-an-error-message-is-displayed-if-the-data-returned-by-the-wcf-service-is-null"></a>Problème 2 : Un message d’erreur s’affiche si les données retournées par le service WCF sont NULL  
 **Explication**: si les données retournées par le service WCF sont une valeur NULL, Microsoft Office SharePoint Server affiche un message d’erreur. Par exemple, supposons que vous utilisez le composant WebPart de liste de données métier pour le **recherche** méthode d’instance et recherchez des clients dans le système Siebel basé sur une expression de recherche. L’expression de recherche que vous avez spécifié extrait une valeur NULL. Dans ce cas, Microsoft Office SharePoint Server affiche un message d’erreur.  
  
 **Résolution**: aucune résolution. Il s’agit d’une limitation connue avec Microsoft Office SharePoint Server.  
  
### <a name="issue-3-an-array-of-simple-type-returned-by-the-wcf-service-is-not-displayed"></a>Problème 3 : Un tableau de type simple retourné par le service WCF n’est pas affiché.  
 **Explication**: si les données retournées par le service WCF sont un tableau de type simple, Microsoft Office SharePoint Server n’affiche pas les données. En outre, lorsque vous exécutez une instance de méthode dans Business Data Catalog Definition Editor qui retourne un tableau de type simple, le message d’erreur suivant s’affiche : « adaptateur de système principal a renvoyé une structure incompatible avec le (métadonnées correspondant MethodInstance, paramètre ou TypeDescriptor). »  
  
 **Résolution**: aucune résolution. Il s’agit d’une limitation connue avec Microsoft Office SharePoint Server et Business Data Catalog Definition Editor.  
  
### <a name="issue-4-cannot-import-an-application-definition-file-that-contains-a-complex-type-parameter-having-more-than-300-fields"></a>Problème 4 : Impossible d’importer un fichier de définition d’application qui contient un paramètre de type complexe comportant plus de 300 champs  
 **Explication**: Microsoft Office SharePoint Server ne peut pas importer un fichier de définition d’application qui n’a plus de 300 dans le paramètre de type complexe retournée par le service WCF et affiche un message d’erreur si vous essayez de le faire. Cela est dû à la limitation de Microsoft Office SharePoint Server de ne pas pouvoir afficher plus de 300 champs d’un paramètre de type complexe.  
  
 **Résolution**: utilisez l’éditeur de définition de catalogue de données métier afin de limiter le nombre de champs du paramètre de type complexe à inférieure ou égale à 300. Selon vos besoins, vous pouvez supprimer les champs du paramètre de type complexe dans le Business Data Catalog Definition Editor qui ne doit pas être affiché dans Microsoft Office SharePoint Server.  Ou bien, vous pouvez également exporter le fichier de définition d’application à partir de Business Data Catalog Definition Editor avec tous les champs et ensuite modifier le fichier de définition d’application dans un bloc-notes ou d’une application de création de XML pour supprimer les champs qui ne sont pas requis pour limiter le nombre de champs à 300.  
  
##  <a name="Custom_Web_Part"></a>Problèmes qui impliquent des composants WebPart personnalisés  
 Cette section contient des problèmes qui requièrent l’utilisation de composants WebPart personnalisés pour la résolution. Pour plus d’informations sur l’utilisation d’un composant WebPart personnalisé pour résoudre les problèmes qui se produit lorsque vous travaillez avec [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] et Microsoft Office SharePoint Server, consultez [utiliser un composant WebPart personnalisé avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/use-a-custom-web-part-with-the-siebel-adapter.md).  
  
### <a name="issue-1-index-of-an-enumerator-is-displayed-instead-of-the-value-for-the-enum-data-type"></a>Problème 1 : Les Index d’un énumérateur s’affiche au lieu de la valeur pour le type de données d’enum  
 **Explication**: si une liste de données métiers ou un élément de données Business WebPart dans Microsoft Office SharePoint Server contient des données de type d’enum (un type distinct constitué d’un ensemble de constantes nommées, appelées énumérateurs), l’index de l’énumérateur est affiché au lieu de sa valeur dans Microsoft Office SharePoint Server. Il s’agit, car la liste de données métiers et WebPart élément de données métiers incorrectement impriment les valeurs de l’énumération de type de données sur le portail SharePoint.  
  
 **Résolution**: un composant WebPart personnalisé permet d’imprimer la valeur de l’énumérateur au lieu de l’index. Pour plus d’informations sur l’utilisation d’un composant WebPart personnalisé, consultez [utiliser un composant WebPart personnalisé avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/use-a-custom-web-part-with-the-siebel-adapter.md). Par exemple, vous pouvez utiliser l’exemple de code suivant dans votre composant WebPart pour imprimer les valeurs correctes enum de type de données sur Microsoft Office SharePoint Server.  
  
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
  
### <a name="issue-2-cannot-specify-values-to-array-elements"></a>Problème 2 : Ne peut pas spécifier des valeurs pour les éléments de tableau  
 **Explication**: si le paramètre d’entrée du service WCF est un tableau, vous ne pouvez pas spécifier des valeurs pour les éléments du tableau à l’aide de filtres qui sont définis dans le fichier de définition d’application créé à l’aide de l’éditeur de définition de catalogue de données métier. Cela implique que vous ne pouvez pas utiliser la liste de données d’entreprise ou d’un WebPart élément de données métier dans Microsoft Office SharePoint Server pour spécifier des valeurs pour ces paramètres d’entrée (éléments du tableau) pour le service WCF. Il s’agit en raison du mode tableaux sont définis dans le fichier de définition d’application.  
  
 **Résolution**: utiliser un composant WebPart personnalisé pour affecter des valeurs aux éléments du tableau. Pour plus d’informations sur l’utilisation d’un composant WebPart personnalisé, consultez [utiliser un composant WebPart personnalisé avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/use-a-custom-web-part-with-the-siebel-adapter.md). Par exemple, vous pouvez utiliser l’exemple de code suivant à l’étape 3 de « problème 1 : Index d’un énumérateur s’affiche au lieu de la valeur pour le type de données d’énumération « pour affecter des valeurs aux éléments du tableau.  
  
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
  
### <a name="issue-3-limitation-with-specifying-null-values-to-complex-type-parameters"></a>Problème 3 : Limitation en spécifiant des valeurs NULL pour les paramètres de type complexe  
 **Explication**: Si vous ne spécifiez pas de valeur pour un paramètre de type complexe à partir d’un composant WebPart dans Microsoft Office SharePoint Server, NULL doit être transmise en tant que la valeur pour le paramètre de type complexe pour le service WCF. Toutefois, une valeur non NULL est passée pour le paramètre de type complexe, et NULL est passée pour ses éléments enfants (de type simple). Cela provoque une incompatibilité entre le schéma de message attendu et le schéma de message qui est transmis au service WCF. Par conséquent, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] peut afficher un message d’erreur.  
  
> [!NOTE]
>  Pour déterminer la valeur par défaut d’un paramètre de type complexe lorsqu’aucune valeur n’est passée à partir d’un composant WebPart dans Microsoft Office SharePoint Server, utilisez l’étape 2 dans l’exemple de code indiqué dans « erreur 1 : Index d’un énumérateur s’affiche au lieu de la valeur pour le type de données d’enum. »  
  
 **Résolution**: un composant WebPart personnalisé permet d’attribuer une valeur NULL au paramètre de type complexe lorsque aucune valeur n’est spécifiée à partir d’un composant WebPart dans Microsoft Office SharePoint Server. Pour plus d’informations sur l’utilisation d’un composant WebPart personnalisé, consultez [utiliser un composant WebPart personnalisé avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/use-a-custom-web-part-with-the-siebel-adapter.md).  
  
###  <a name="Issue1"></a>Problème 4 : Limitation avec affichage d’un enregistrement unique dans Microsoft Office SharePoint Server en fonction de plusieurs valeurs  
 **Explication**: Si vous souhaitez afficher un enregistrement unique dans Microsoft Office SharePoint Server, en fonction de plusieurs valeurs (paramètres d’entrée) à partir d’un système Siebel, vous ne pouvez pas utiliser un des trois composants (liste de données métiers, élément de données d’entreprise et Professionnel Liste liée aux données) spécifié dans [étape 3 : créer une Application SharePoint pour récupérer des données à partir de Siebel](../../adapters-and-accelerators/adapter-siebel/step-3-create-a-sharepoint-application-to-retrieve-data-from-siebel.md) dans [didacticiel 1 : présentation sur un SharePoint Site de données à partir de système Siebel](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md).  
  
 **Résolution**: vous devez utiliser un composant WebPart personnalisé pour ce faire. Pour plus d’informations sur l’utilisation d’un composant WebPart personnalisé, consultez [utiliser un composant WebPart personnalisé avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/use-a-custom-web-part-with-the-siebel-adapter.md). Par exemple, à l’étape 3 « problème 1 : Index d’un énumérateur s’affiche au lieu de la valeur pour le type de données d’enum « vous pouvez modifier le code pour fournir des valeurs pour plusieurs paramètres au lieu de fournir une entrée à un paramètre de composant d’entreprise unique.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisez l’adaptateur Siebel avec SharePoint](../../adapters-and-accelerators/adapter-siebel/use-the-siebel-adapter-with-sharepoint.md)