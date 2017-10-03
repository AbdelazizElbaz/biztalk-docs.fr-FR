---
title: "Considérations sur l’utilisation de l’adaptateur SAP avec SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d310741-b648-4028-a75f-35b843edcc8d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07aef41626c9ac2336565cdca9fa3470bf0144e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-when-using-the-sap-adapter-with-sharepoint"></a>Considérations sur l’utilisation de l’adaptateur SAP avec SharePoint
Cette rubrique contient des informations sur les problèmes que vous pouvez rencontrer en utilisant la [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] avec Microsoft Office SharePoint Server, ainsi que des résolutions. Les problèmes sont répartis en deux catégories :  
  
-   Problèmes généraux  
  
-   Problèmes qui impliquent des composants WebPart personnalisés  
  
## <a name="general-issues"></a>Problèmes généraux  
 Cette section contient des problèmes qui n’ont aucune solution ou, vous devez modifier le fichier de définition d’application pour la résolution.  
  
### <a name="issue-1-the-simple-type-data-returned-by-the-wcf-service-is-not-displayed"></a>Problème 1 : Les données de type simple retournées par le service WCF ne sont pas affichées.  
 **Explication**: Microsoft Office SharePoint Server attend les données retournées par le service WCF doit être de type jeu de données ou une Collection uniquement. Si les données retournées par le service WCF sont de type simple, Microsoft Office SharePoint Server n’affiche pas les données.  
  
 **Résolution**: aucune résolution. Il s’agit d’une limitation connue avec Microsoft Office SharePoint Server.  
  
### <a name="issue-2-an-error-message-is-displayed-if-the-data-returned-by-the-wcf-service-is-null"></a>Problème 2 : Un message d’erreur s’affiche si les données retournées par le service WCF sont NULL  
 **Explication**: si les données retournées par le service WCF sont une valeur NULL, Microsoft Office SharePoint Server affiche un message d’erreur. Par exemple, supposons que vous utilisez le composant WebPart de liste de données métier pour le **recherche** méthode d’instance et recherchez des clients dans le système SAP basé sur une expression de recherche. L’expression de recherche que vous avez spécifié extrait une valeur NULL. Dans ce cas, Microsoft Office SharePoint Server affiche un message d’erreur.  
  
 **Résolution**: aucune résolution. Il s’agit d’une limitation connue avec Microsoft Office SharePoint Server.  
  
### <a name="issue-3-an-array-of-simple-type-returned-by-the-wcf-service-is-not-displayed"></a>Problème 3 : Un tableau de type simple retourné par le service WCF n’est pas affiché.  
 **Explication**: si les données retournées par le service WCF sont un tableau de type simple, Microsoft Office SharePoint Server n’affiche pas les données. En outre, lorsque vous exécutez une instance de méthode dans Business Data Catalog Definition Editor qui retourne un tableau de type simple, le message d’erreur suivant s’affiche : « adaptateur de système principal a renvoyé une structure incompatible avec le (métadonnées correspondant MethodInstance, paramètre ou TypeDescriptor). »  
  
 **Résolution**: aucune résolution. Il s’agit d’une limitation connue avec Microsoft Office SharePoint Server et Business Data Catalog Definition Editor.  
  
### <a name="issue-4-cannot-import-an-application-definition-file-that-contains-a-complex-type-parameter-having-more-than-300-fields"></a>Problème 4 : Impossible d’importer un fichier de définition d’application qui contient un paramètre de type complexe comportant plus de 300 champs  
 **Explication**: Microsoft Office SharePoint Server ne peut pas importer un fichier de définition d’application qui n’a plus de 300 dans le paramètre de type complexe retournée par le service WCF et affiche un message d’erreur si vous essayez de le faire. Cela est dû à la limitation de Microsoft Office SharePoint Server de ne pas pouvoir afficher plus de 300 champs d’un paramètre de type complexe.  
  
 **Résolution**: utilisez l’éditeur de définition de catalogue de données métier afin de limiter le nombre de champs du paramètre de type complexe à inférieure ou égale à 300. Selon vos besoins, vous pouvez supprimer les champs du paramètre de type complexe dans le Business Data Catalog Definition Editor qui ne doit pas être affiché dans Microsoft Office SharePoint Server.  Ou bien, vous pouvez également exporter le fichier de définition d’application à partir de Business Data Catalog Definition Editor avec tous les champs et ensuite modifier le fichier de définition d’application dans un bloc-notes ou d’une application de création de XML pour supprimer les champs qui ne sont pas requis pour limiter le nombre de champs à 300.  
  
##  <a name="Custom_Web_Part"></a>Problèmes qui impliquent des composants WebPart personnalisés  
 Cette section contient des problèmes qui requièrent l’utilisation du composant WebPart personnalisé pour une résolution. Pour plus d’informations sur l’utilisation d’un composant WebPart personnalisé pour résoudre les problèmes qui se produit lorsque vous travaillez avec [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] et Microsoft Office SharePoint Server, consultez [utiliser un composant WebPart personnalisé avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/use-a-custom-web-part-with-the-sap-adapter.md).  
  
###  <a name="Issue1"></a>Problème 1 : Limite d’affichage d’un enregistrement unique dans Microsoft Office SharePoint Server en fonction de plusieurs valeurs  
 **Explication**: Si vous souhaitez afficher un enregistrement unique dans Microsoft Office SharePoint Server, en fonction de plusieurs valeurs (paramètres d’entrée) à partir d’un système SAP, vous ne pouvez pas utiliser un des trois composants (liste de données métiers, élément de données d’entreprise et Professionnel Liste liée aux données) spécifié dans [étape 3 : créer une Application SharePoint pour récupérer des données à partir de SAP](../../adapters-and-accelerators/adapter-sap/step-3-create-a-sharepoint-application-to-retrieve-data-from-sap.md) dans [didacticiel 1 : présentation des données à partir d’un système SAP sur un SharePoint Site](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md).  
  
 **Résolution**: vous devez utiliser un composant WebPart personnalisé pour ce faire. Pour plus d’informations sur l’utilisation d’un composant WebPart personnalisé, consultez [utiliser un composant WebPart personnalisé avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/use-a-custom-web-part-with-the-sap-adapter.md). Dans « Étape 1 : créer un personnalisé WebPart » de cette rubrique, vous pouvez utiliser l’exemple de code suivant à l’étape 5. L’exemple de code suivant prend BankCountry et BankKey en tant que paramètres d’entrée, puis de les affiche sous la forme d’un seul enregistrement dans Microsoft Office SharePoint Server.  
  
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
>  Le fichier de définition d’application doit contenir le **recherche spécifique** instance de méthode. A **recherche spécifique** méthode trouve un enregistrement spécifique en fonction d’un identificateur. Pour plus d’informations sur la création d’un **recherche spécifique** méthode d’instance, consultez la section « Exigence 2 : récupérer détails pour un client à partir de la liste de clients spécifiques » dans [étape 2 : créer un fichier de définition d’Application pour SAP Artefacts](../../adapters-and-accelerators/adapter-sap/step-2-create-an-application-definition-file-for-the-sap-artifacts.md) dans [didacticiel 1 : présentation des données à partir d’un système SAP sur un Site SharePoint](../../adapters-and-accelerators/adapter-sap/tutorial-1-presenting-data-from-an-sap-system-on-a-sharepoint-site.md).  
  
### <a name="issue-2-cannot-specify-values-to-array-elements"></a>Problème 2 : Ne peut pas spécifier des valeurs pour les éléments de tableau  
 **Explication**: si le paramètre d’entrée du service WCF est un tableau, vous ne pouvez pas spécifier des valeurs pour les éléments du tableau à l’aide de filtres qui sont définis dans le fichier de définition d’application créé à l’aide de l’éditeur de définition de catalogue de données métier. Cela implique que vous ne pouvez pas utiliser la liste de données d’entreprise ou d’un WebPart élément de données métier dans Microsoft Office SharePoint Server pour spécifier des valeurs pour ces paramètres d’entrée (éléments du tableau) pour le service WCF. Il s’agit en raison du mode tableaux sont définis dans le fichier de définition d’application.  
  
 **Résolution**: utiliser un composant WebPart personnalisé pour affecter des valeurs aux éléments du tableau. Pour plus d’informations sur l’utilisation d’un composant WebPart personnalisé, consultez [utiliser un composant WebPart personnalisé avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/use-a-custom-web-part-with-the-sap-adapter.md). Par exemple, vous pouvez utiliser l’exemple de code suivant à l’étape 3 de « problème 1 : Limitation avec affichage d’un enregistrement unique dans Microsoft Office SharePoint Server en fonction de plusieurs valeurs » pour affecter des valeurs aux éléments du tableau.  
  
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
  
### <a name="issue-3-limitation-with-specifying-null-values-to-complex-type-parameters"></a>Problème 3 : Limitation en spécifiant des valeurs NULL pour les paramètres de type complexe  
 **Explication**: Si vous ne spécifiez pas de valeur pour un paramètre de type complexe à partir d’un composant WebPart dans Microsoft Office SharePoint Server, NULL doit être transmise en tant que la valeur pour le paramètre de type complexe pour le service WCF. Toutefois, une valeur non NULL est passée pour le paramètre de type complexe, et NULL est passée pour ses éléments enfants (de type simple). Cela provoque une incompatibilité entre le schéma de message attendu et le schéma de message qui est transmis au service WCF. Par conséquent, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] peut afficher un message d’erreur.  
  
> [!NOTE]
>  Pour déterminer la valeur par défaut d’un paramètre de type complexe lorsqu’aucune valeur n’est passée à partir d’un composant WebPart dans Microsoft Office SharePoint Server, utilisez l’étape 2 dans l’exemple de code indiqué dans « erreur 1 : limite d’affichage d’un enregistrement unique dans Microsoft Office SharePoint Server en fonction de plusieurs valeurs. »  
  
 **Résolution**: un composant WebPart personnalisé permet d’attribuer une valeur NULL au paramètre de type complexe. Pour plus d’informations sur l’utilisation d’un composant WebPart personnalisé, consultez [utiliser un composant WebPart personnalisé avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/use-a-custom-web-part-with-the-sap-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
[Utilisez l’adaptateur SAP avec SharePoint](../../adapters-and-accelerators/adapter-sap/use-the-sap-adapter-with-sharepoint.md)