---
title: "Étape 6 : Implémenter le Gestionnaire de résoudre des métadonnées de l’adaptateur d’écho | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0105d1b0-efbd-457b-af0d-08e29408a318
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 022da31cacedaa59c9e5821fb049165f463c7f06
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter"></a><span data-ttu-id="05ef1-102">Étape 6 : Implémenter le Gestionnaire de résoudre des métadonnées de l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="05ef1-102">Step 6: Implement the Metadata Resolve Handler for the Echo Adapter</span></span>
<span data-ttu-id="05ef1-103">![Étape 6 de 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-6of9.gif "Step_6of9")</span><span class="sxs-lookup"><span data-stu-id="05ef1-103">![Step 6 of 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-6of9.gif "Step_6of9")</span></span>  
  
 <span data-ttu-id="05ef1-104">**Durée :** 45 minutes</span><span class="sxs-lookup"><span data-stu-id="05ef1-104">**Time to complete:** 45 minutes</span></span>  
  
 <span data-ttu-id="05ef1-105">Dans cette étape, vous implémentez le `Microsoft.ServiceModel.Channels.Common.IMetadataResolverHandler` interface pour l’opération de résolution et de métadonnées de l’adaptateur de l’écho de type.</span><span class="sxs-lookup"><span data-stu-id="05ef1-105">In this step, you implement the `Microsoft.ServiceModel.Channels.Common.IMetadataResolverHandler` interface to resolve operation and type metadata for the echo adapter.</span></span> <span data-ttu-id="05ef1-106">Quelle que soit la capacité de votre carte, vous devez implémenter cette interface.</span><span class="sxs-lookup"><span data-stu-id="05ef1-106">Regardless of your adapter's capability, you must implement this interface.</span></span> <span data-ttu-id="05ef1-107">Le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] génère automatiquement la classe dérivée, appelée EchoAdapterMetadataResolverHandler pour vous.</span><span class="sxs-lookup"><span data-stu-id="05ef1-107">The [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] automatically generates the derived class called EchoAdapterMetadataResolverHandler for you.</span></span>  
  
 <span data-ttu-id="05ef1-108">Dans la section suivante, vous mettez à jour la classe EchoAdapterMetadataResolverHandler pour mieux comprendre comment implémenter cette interface.</span><span class="sxs-lookup"><span data-stu-id="05ef1-108">In the following section, you update the EchoAdapterMetadataResolverHandler class to get a better understanding on how to implement this interface.</span></span> <span data-ttu-id="05ef1-109">Lorsque vous terminez cette étape, vous avez un travail de métadonnées résoudre le Gestionnaire de l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="05ef1-109">When you complete this step, you have a working metadata resolve handler for the echo adapter.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="05ef1-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="05ef1-110">Prerequisites</span></span>  
 <span data-ttu-id="05ef1-111">Avant de commencer cette étape, vous devez avoir terminé avec succès [étape 5 : implémenter le Gestionnaire de recherche de métadonnées de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="05ef1-111">Before you begin this step, you must have successfully completed [Step 5: Implement the Metadata Search Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md).</span></span> <span data-ttu-id="05ef1-112">Vous devez également comprendre les classes d’opération et le type suivants :</span><span class="sxs-lookup"><span data-stu-id="05ef1-112">You must also understand the following operation and type classes:</span></span>  
  
-   `Microsoft.ServiceModel.Channels.Common.ParameterizedOperationMetadata`  
  
-   `Microsoft.ServiceModel.Channels.Common.OperationMetadata`  
  
-   `Microsoft.ServiceModel.Channels.Common.OperationParameter`  
  
-   `Microsoft.ServiceModel.Channels.Common.OperationResult`  
  
-   `Microsoft.ServiceModel.Channels.Common.TypeMetadata`  
  
-   `Microsoft.ServiceModel.Channels.Common.StructuredTypeMetadata`  
  
-   `Microsoft.ServiceModel.Channels.Common.TypeMember`  
  
-   `Microsoft.ServiceModel.Channels.Common.SimpleQualifiedType`  
  
-   `Microsoft.ServiceModel.Channels.Common.ComplexQualifiedType`  
  
## <a name="the-imetadataresolverhandler-interface"></a><span data-ttu-id="05ef1-113">L’Interface IMetadataResolverHandler</span><span class="sxs-lookup"><span data-stu-id="05ef1-113">The IMetadataResolverHandler Interface</span></span>  
  
```  
public interface IMetadataResolverHandler : IConnectionHandler, IDisposable  
  {  
      bool IsOperationMetadataValid(string operationId, DateTime lastUpdatedTimestamp, TimeSpan timeout);        
      bool IsTypeMetadataValid(string typeId, DateTime lastUpdatedTimestamp, TimeSpan timeout);  
      OperationMetadata ResolveOperationMetadata(string operationId, TimeSpan timeout, out TypeMetadataCollection extraTypeMetadataResolved);  
      TypeMetadata ResolveTypeMetadata(string typeId, TimeSpan timeout, out TypeMetadataCollection extraTypeMetadataResolved);  
  }  
```  
  
 <span data-ttu-id="05ef1-114">Le tableau suivant décrit ce que fait chaque méthode :</span><span class="sxs-lookup"><span data-stu-id="05ef1-114">The following table describes what each method does:</span></span>  
  
|<span data-ttu-id="05ef1-115">**Nom de la méthode**</span><span class="sxs-lookup"><span data-stu-id="05ef1-115">**Method Name**</span></span>|<span data-ttu-id="05ef1-116">**Description**</span><span class="sxs-lookup"><span data-stu-id="05ef1-116">**Description**</span></span>|  
|---------------------|---------------------|  
|<span data-ttu-id="05ef1-117">IsOperationMetadataValid</span><span class="sxs-lookup"><span data-stu-id="05ef1-117">IsOperationMetadataValid</span></span>|<span data-ttu-id="05ef1-118">Retourne la valeur true si les métadonnées de type n’a pas changé depuis la date et l’heure spécifiée</span><span class="sxs-lookup"><span data-stu-id="05ef1-118">Returns a true if the type metadata has not changed since the date and time specified</span></span>|  
|<span data-ttu-id="05ef1-119">IsTypeMetadataValid</span><span class="sxs-lookup"><span data-stu-id="05ef1-119">IsTypeMetadataValid</span></span>|<span data-ttu-id="05ef1-120">Retourne une valeur booléenne qui indique si les métadonnées du type spécifié sont valide.</span><span class="sxs-lookup"><span data-stu-id="05ef1-120">Returns a Boolean value that indicates whether the specified type metadata is valid.</span></span>|  
|<span data-ttu-id="05ef1-121">ResolveOperationMetadata</span><span class="sxs-lookup"><span data-stu-id="05ef1-121">ResolveOperationMetadata</span></span>|<span data-ttu-id="05ef1-122">Résout un ID d’opération correspondant`Microsoft.ServiceModel.Channels.Common.OperationMetadata`</span><span class="sxs-lookup"><span data-stu-id="05ef1-122">Resolves an operation ID to corresponding `Microsoft.ServiceModel.Channels.Common.OperationMetadata`</span></span>|  
|<span data-ttu-id="05ef1-123">ResolveTypeMetadata</span><span class="sxs-lookup"><span data-stu-id="05ef1-123">ResolveTypeMetadata</span></span>|<span data-ttu-id="05ef1-124">Résout un typeId métadonnées fournies correspondant `Microsoft.ServiceModel.Channels.Common.TypeMetadata`.</span><span class="sxs-lookup"><span data-stu-id="05ef1-124">Resolves a supplied metadata typeId to a corresponding `Microsoft.ServiceModel.Channels.Common.TypeMetadata`.</span></span>|  
  
### <a name="to-implement-the-isoperationmetadatavalid-method"></a><span data-ttu-id="05ef1-125">Pour implémenter la méthode IsOperationMetadataValid</span><span class="sxs-lookup"><span data-stu-id="05ef1-125">To implement the IsOperationMetadataValid method</span></span>  
  
1.  <span data-ttu-id="05ef1-126">Dans l’Explorateur de solutions, double-cliquez sur le **EchoAdapterMetadataResolverHandler.cs** fichier.</span><span class="sxs-lookup"><span data-stu-id="05ef1-126">In Solution Explorer, double-click the **EchoAdapterMetadataResolverHandler.cs** file.</span></span>  
  
2.  <span data-ttu-id="05ef1-127">Dans l’éditeur Visual Studio, avec le bouton droit n’importe où dans l’éditeur, dans le menu contextuel, pointez sur **mode plan**, puis cliquez sur **arrêter le mode plan**.</span><span class="sxs-lookup"><span data-stu-id="05ef1-127">In the Visual Studio editor, right-click anywhere within the editor, in the context menu, point to **Outlining**, and then click **Stop Outlining**.</span></span>  
  
3.  <span data-ttu-id="05ef1-128">Dans l’éditeur Visual Studio, recherchez le **IsOperationMetadataValid** méthode, à l’intérieur de cette méthode, remplacer l’existant avec l’instruction suivante pour indiquer que les métadonnées de chaque opération spécifiée sont valide.</span><span class="sxs-lookup"><span data-stu-id="05ef1-128">In the Visual Studio editor, find the **IsOperationMetadataValid** method, inside this method, replace the existing with the following single statement to indicate that every specified operation metadata is valid.</span></span>  
  
    ```csharp  
    return true;  
    ```  
  
### <a name="to-implement-the-istypemetadatavalid-method"></a><span data-ttu-id="05ef1-129">Pour implémenter la méthode IsTypeMetadataValid</span><span class="sxs-lookup"><span data-stu-id="05ef1-129">To implement the IsTypeMetadataValid method</span></span>  
  
-   <span data-ttu-id="05ef1-130">Dans l’éditeur Visual Studio, recherchez le **IsTypeMetadataValid** méthode, à l’intérieur de cette méthode, remplacer l’existant avec l’instruction suivante pour indiquer que les métadonnées de chaque type spécifié sont valide.</span><span class="sxs-lookup"><span data-stu-id="05ef1-130">In the Visual Studio editor, find the **IsTypeMetadataValid** method, inside this method, replace the existing with the following single statement to indicate that every specified type metadata is valid.</span></span>  
  
    ```csharp  
    return true;  
    ```  
  
### <a name="to-implement-the-resolveoperationmetadata-method"></a><span data-ttu-id="05ef1-131">Pour implémenter la méthode ResolveOperationMetadata</span><span class="sxs-lookup"><span data-stu-id="05ef1-131">To implement the ResolveOperationMetadata method</span></span>  
  
1.  <span data-ttu-id="05ef1-132">Dans l’éditeur Visual Studio, recherchez le **ResolveOperationMetadata** méthode, à l’intérieur de cette méthode, remplacez existants avec les éléments suivants pour résoudre l’opération OnReceiveEcho, void OnReceiveEcho (chemin d’accès de l’Uri, fileLength long).</span><span class="sxs-lookup"><span data-stu-id="05ef1-132">In the Visual Studio editor, find the **ResolveOperationMetadata** method, inside this method, replace the existing with the following to resolve the OnReceiveEcho operation, void OnReceiveEcho(Uri path, long fileLength).</span></span>  
  
    ```csharp  
    extraTypeMetadataResolved = null;  
    switch( operationId )  
    {  
        case "Echo/OnReceiveEcho":  
            ParameterizedOperationMetadata om = new ParameterizedOperationMetadata(operationId, "OnReceiveEcho");  
            om.OriginalName = "lobNotification";  
            om.Description = "This operation echoes the location and length of a file dropped in the specified file system.";  
            om.OperationGroup = "EchoInboundContract";  
            om.OperationNamespace = EchoAdapter.SERVICENAMESPACE;  
            // syntax: void OnReceiveEcho(Uri path, long fileLength)  
            OperationParameter parmPath = new OperationParameter("path", OperationParameterDirection.In, QualifiedType.UriType, false);  
            parmPath.Description = "Absolute path of the file";  
            OperationParameter parmLength = new OperationParameter("length", OperationParameterDirection.In, QualifiedType.LongType, false);  
            parmLength.Description = "Length of the file received in this location.";  
            om.Parameters.Add(parmPath);  
            om.Parameters.Add(parmLength);  
            om.OperationResult = OperationResult.Empty;  
            return om;  
    ```  
  
2.  <span data-ttu-id="05ef1-133">Poursuivre l’ajout de la commande suivante pour résoudre l’opération Echo/EchoStrings, string [] EchoStrings(string data).</span><span class="sxs-lookup"><span data-stu-id="05ef1-133">Continue adding the following to resolve the Echo/EchoStrings operation, string[] EchoStrings(string data).</span></span>  
  
    ```csharp  
    case "Echo/EchoStrings":  
        om = new ParameterizedOperationMetadata(operationId, "EchoStrings");  
        om.OriginalName = "lobEchoStrings";  
        om.Description = "This operation echoes the incoming string COUNT number of times in a string array.";  
        om.OperationGroup = "EchoOutboundContract";  
        om.OperationNamespace = EchoAdapter.SERVICENAMESPACE;  
        // syntax: string[] EchoStrings(string data)  
        OperationParameter parmData = new OperationParameter("data", OperationParameterDirection.In, QualifiedType.StringType, false);  
        parmData.Description = "Input string";  
        om.Parameters.Add(parmData);  
        om.OperationResult = new OperationResult(QualifiedType.StringType, true);  
        return om;  
    ```  
  
3.  <span data-ttu-id="05ef1-134">Continuez à ajouter la logique suivante pour résoudre l’opération Echo/EchoStrings, string [] EchoStrings(string data).</span><span class="sxs-lookup"><span data-stu-id="05ef1-134">Continue adding the following logic to resolve the Echo/EchoStrings operation, string[] EchoStrings(string data).</span></span>  
  
    ```csharp  
    case "Echo/EchoGreetings":  
        om = new ParameterizedOperationMetadata(operationId, "EchoGreetings");  
        om.OriginalName = "lobEchoGreetings";  
        om.Description = "This operation echoes the incoming Greeting object COUNT number of times in an array of type Greeting.";  
        om.OperationGroup = "EchoOutboundContract";  
        om.OperationNamespace = EchoAdapter.SERVICENAMESPACE;  
        // syntax: Greeting[] EchoGreetings(Greeting greeting)  
        ComplexQualifiedType cqtGreeting = new ComplexQualifiedType("Types/GreetingType");  
        OperationParameter parmGreeting = new OperationParameter("greeting", OperationParameterDirection.In, cqtGreeting, false);  
        parmGreeting.Description = "Input greeting";  
        om.Parameters.Add(parmGreeting);  
        om.OperationResult = new OperationResult(cqtGreeting, true);  
        return om;  
    ```  
  
4.  <span data-ttu-id="05ef1-135">Continuez à ajouter la logique suivante pour résoudre l’opération CustomGreeting EchoCustomGreetingFromFile(Uri greetingInstancePath).</span><span class="sxs-lookup"><span data-stu-id="05ef1-135">Continue adding the following logic to resolve the CustomGreeting EchoCustomGreetingFromFile(Uri greetingInstancePath) operation.</span></span>  
  
    ```csharp  
    case "Echo/EchoCustomGreetingFromFile":  
        om = new ParameterizedOperationMetadata(operationId, "EchoCustomGreetingFromFile");  
        om.OriginalName = "lobEchoGreetingUsePredefinedMetadata";  
        om.Description = "This operation echoes the incoming Greeting object COUNT number of times in an array of type Greeting.  The Greeting type metadata is created using predefined XSD file.";  
        om.OperationGroup = "EchoOutboundContract";  
        om.OperationNamespace = EchoAdapter.SERVICENAMESPACE;  
        OperationParameter parmGreetingInstancePath = new OperationParameter("greetingInstancePath", OperationParameterDirection.In, QualifiedType.UriType, false);  
        om.Parameters.Add(parmGreetingInstancePath);  
        ComplexQualifiedType cqtGreetingXsd = new ComplexQualifiedType("Types/CustomGreetingFromXsdType");  
        om.OperationResult = new OperationResult(cqtGreetingXsd, false);  
  
        // resolve extra typemetadata here  
        extraTypeMetadataResolved = new TypeMetadataCollection();  
  
        // use a predefined schema to generate metadata for this type  
        CustomGreetingTypeMetadata tmGreetingXsd = new CustomGreetingTypeMetadata("Types/CustomGreetingFromXsdType", "CustomGreeting");  
        extraTypeMetadataResolved.Add(tmGreetingXsd);                   
        return om;  
  
    ```  
  
5.  <span data-ttu-id="05ef1-136">Poursuivre l’ajout de la commande suivante pour gérer le cas par défaut.</span><span class="sxs-lookup"><span data-stu-id="05ef1-136">Continue adding the following to handle default case.</span></span>  
  
    ```csharp  
        default:  
            throw new AdapterException("Cannot resolve metadata for operation identifier " + operationId);  
    }  
    ```  
  
### <a name="to-implement-the-resolvetypemetadata-method"></a><span data-ttu-id="05ef1-137">Pour implémenter la méthode ResolveTypeMetadata</span><span class="sxs-lookup"><span data-stu-id="05ef1-137">To implement the ResolveTypeMetadata method</span></span>  
  
-   <span data-ttu-id="05ef1-138">Dans l’éditeur Visual Studio, recherchez le **ResolveTypeMetadata** méthode, à l’intérieur de cette méthode, remplacez existants avec les éléments suivants pour retourner un `Microsoft.ServiceModel.Channels.Common.TypeMetadata` objet.</span><span class="sxs-lookup"><span data-stu-id="05ef1-138">In the Visual Studio editor, find the **ResolveTypeMetadata** method, inside this method, replace the existing with the following to return a `Microsoft.ServiceModel.Channels.Common.TypeMetadata` object.</span></span>  
  
    ```csharp  
    extraTypeMetadataResolved = null;  
    string typeNamespaceForGreeting = EchoAdapter.SERVICENAMESPACE + "/Types";  
    switch (typeId)  
    {  
        case "Types/GreetingType":  
            StructuredTypeMetadata tmGreeting = new StructuredTypeMetadata(typeId, "Greeting");  
            tmGreeting.TypeNamespace = typeNamespaceForGreeting;  
            tmGreeting.Members.Add(new TypeMember("id", QualifiedType.GuidType, false));  
            tmGreeting.Members.Add(new TypeMember("sentDateTime", QualifiedType.DateTimeType, false));  
            ComplexQualifiedType cqtName = new ComplexQualifiedType("Types/NameType");  
            tmGreeting.Members.Add(new TypeMember("name", cqtName, false));  
            tmGreeting.Members.Add(new TypeMember("greetingText", QualifiedType.StringType, false));  
            return tmGreeting;  
  
        case "Types/NameType":  
            StructuredTypeMetadata tmName = new StructuredTypeMetadata(typeId, "Name");  
            tmName.TypeNamespace = typeNamespaceForGreeting;  
            ComplexQualifiedType cqtSalutation = new ComplexQualifiedType("Types/SalutationType");  
            tmName.Members.Add(new TypeMember("salutation", cqtSalutation, false));  
            tmName.Members.Add(new TypeMember("firstName", QualifiedType.StringType, false));  
            tmName.Members.Add(new TypeMember("middleName", QualifiedType.StringType, false));  
            tmName.Members.Add(new TypeMember("lastName", QualifiedType.StringType, false));  
            return tmName;  
  
        case "Types/SalutationType":  
            EnumTypeMetadata tmSalutation = new EnumTypeMetadata(typeId, "Salutation", new string[] { "Mr.", "Mrs.", "Dr.", "Ms.", "Miss" });  
            tmSalutation.TypeNamespace = typeNamespaceForGreeting;  
            return tmSalutation;  
  
        default:  
            throw new AdapterException("Cannot resolve metadata for type identifier " + typeId);  
    }  
  
    ```  
  
### <a name="to-define-the-custom-greeting-type-metadata-class"></a><span data-ttu-id="05ef1-139">Pour définir la classe de métadonnées de type de message d’accueil personnalisée</span><span class="sxs-lookup"><span data-stu-id="05ef1-139">To define the custom greeting type metadata class</span></span>  
  
1.  <span data-ttu-id="05ef1-140">Dans l’Explorateur de solutions, cliquez sur le **Echo adaptateur** de projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="05ef1-140">In Solution Explorer, right-click the **Echo Adapter** project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="05ef1-141">Dans le **ajouter un nouvel élément** boîte de dialogue **modèles**, cliquez sur **classe**.</span><span class="sxs-lookup"><span data-stu-id="05ef1-141">In the **Add New Item** dialog box, under **Templates**, click **Class**.</span></span>  
  
3.  <span data-ttu-id="05ef1-142">Dans le **nom** zone de texte, tapez **CustomGreetingTypeMetadata**.</span><span class="sxs-lookup"><span data-stu-id="05ef1-142">In the **Name** text box, type **CustomGreetingTypeMetadata**.</span></span>  
  
4.  <span data-ttu-id="05ef1-143">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="05ef1-143">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="05ef1-144">Dans l’éditeur Visual Studio, remplacez le code existant avec les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="05ef1-144">In the Visual Studio editor, replace the existing code with the following:</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using Microsoft.ServiceModel.Channels.Common;  
    using System.Xml;  
    using System.Xml.Schema;  
    using System.IO;  
  
    namespace Microsoft.Adapters.Samples.EchoV2  
    {  
        public class CustomGreetingTypeMetadata : TypeMetadata  
        {  
            private const string CONST_METADATA_FILE_NAME = "Microsoft.Adapters.Samples.EchoV2.CustomGreeting.xsd";  
  
            public CustomGreetingTypeMetadata(string typeId, string typeName)  
                : base(typeId, typeName)  
            {  
                this.TypeNamespace = EchoAdapter.SERVICENAMESPACE + "/PreDefinedTypes";  
                this.Description = " ";  
                this.CanUseCommonCache = true;  
                // if the nillable is not set to true, the generated proxy wraps the operation  
                // with request and response objects  
                this.IsNillable = true;  
            }  
  
            /// <summary>  
            /// Override the base ExportXmlSchema to provide own   
            /// custom XML Schema  
            /// </summary>  
            /// <param name="schemaExportContext"></param>  
            /// <param name="metadataLookup"></param>  
            /// <param name="timeout"></param>  
            public override void ExportXmlSchema(XmlSchemaExportContext schemaExportContext, MetadataLookup metadataLookup, TimeSpan timeout)  
            {  
                if (schemaExportContext == null)  
                {  
                    throw new AdapterException("Schema export context is null.");  
                }  
                // Read in XML Schema file or create XmlSchema object yourself  
                Stream predefinedXsdFile = System.Reflection.Assembly.GetExecutingAssembly().GetManifestResourceStream(CONST_METADATA_FILE_NAME);  
                XmlReader reader = XmlReader.Create(predefinedXsdFile);  
                XmlSchema schema = XmlSchema.Read(reader, null);  
                if (!IsComplexTypeAlreadyDefined(schemaExportContext.SchemaSet, schema))  
                {  
                    schemaExportContext.SchemaSet.Add(schema);  
                    if (!schemaExportContext.NamespacePrefixSet.ContainsKey(this.TypeNamespace))  
                    {  
                        schemaExportContext.NamespacePrefixSet.Add(this.TypeNamespace, getUniqueNamespacePrefix(schemaExportContext, 0));  
                    }  
                }  
                reader.Close();  
            }  
  
            /// <summary>  
            /// A default value cannot be set for this type metadata.  
            /// </summary>  
            public override bool CanSetDefaultValue  
            {  
                get { return false; }  
            }  
  
            /// <summary>  
            /// Helper function to see if the schema is already defined in the   
            /// XmlSchemaSet.  
            /// </summary>  
            /// <param name="oldschemaset"></param>  
            /// <param name="newschema"></param>  
            /// <returns></returns>  
            public static bool IsComplexTypeAlreadyDefined(XmlSchemaSet oldschemaset, XmlSchema newschema)  
            {  
                // ensure correct namespace was defined in the passed-in schema  
                foreach (XmlSchema schema in oldschemaset.Schemas(newschema.TargetNamespace))  
                {  
                    foreach (XmlSchemaObject newschemaObject in newschema.Items)  
                    {  
                        if (newschemaObject is XmlSchemaComplexType)  
                        {  
                            //check for the definition of complex type in the schemaset             
                            foreach (XmlSchemaObject schemaObject in schema.Items)  
                            {  
                                XmlSchemaComplexType complexType = schemaObject as XmlSchemaComplexType;  
                                // Definition of this Complex Type already exists  
                                if (complexType != null && String.Compare(complexType.Name, ((XmlSchemaComplexType)newschemaObject).Name, false, System.Globalization.CultureInfo.InvariantCulture) == 0)  
                                    return true;  
                            }  
                        }  
                    }  
                }  
                return false;  
            }  
  
            /// <summary>  
            /// Helper function to generate a unique namespace prefix  
            /// </summary>  
            /// <param name="schemaExportContext"></param>  
            /// <param name="startSuffix"></param>  
            /// <returns></returns>  
            private string getUniqueNamespacePrefix(XmlSchemaExportContext schemaExportContext, int startSuffix)  
            {  
                string defaultPrefix = "ns";  
                string val = defaultPrefix + startSuffix;  
                if (schemaExportContext.NamespacePrefixSet.ContainsValue(val))  
                {  
                    return getUniqueNamespacePrefix(schemaExportContext, ++startSuffix);  
                }  
                else  
                {  
                    return val;  
                }  
            }  
        }  
    }  
    ```  
  
6.  <span data-ttu-id="05ef1-145">Dans Visual Studio, à partir de la **fichier** menu, cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="05ef1-145">In Visual Studio, from the **File** menu, click **Save All**.</span></span>  
  
### <a name="to-create-the-custom-greeting-xml-schema-definition"></a><span data-ttu-id="05ef1-146">Pour créer le message d’accueil personnalisée définition de schéma XML</span><span class="sxs-lookup"><span data-stu-id="05ef1-146">To create the custom greeting XML schema definition</span></span>  
  
1.  <span data-ttu-id="05ef1-147">Dans l’Explorateur de solutions, cliquez sur le **Echo adaptateur** de projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="05ef1-147">In Solution Explorer, right-click the **Echo Adapter** project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="05ef1-148">Dans le **ajouter un nouvel élément** boîte de dialogue **modèles**, cliquez sur **schéma XML**.</span><span class="sxs-lookup"><span data-stu-id="05ef1-148">In the **Add New Item** dialog box, under **Templates**, click **XML Schema**.</span></span>  
  
3.  <span data-ttu-id="05ef1-149">Dans le **nom** zone de texte, tapez **CustomGreeting**.</span><span class="sxs-lookup"><span data-stu-id="05ef1-149">In the **Name** text box, type **CustomGreeting**.</span></span>  
  
4.  <span data-ttu-id="05ef1-150">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="05ef1-150">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="05ef1-151">Dans l’Explorateur de solutions, cliquez sur le **CustomGreeting.xsd** de fichier et choisissez **afficher le Code**.</span><span class="sxs-lookup"><span data-stu-id="05ef1-151">In Solution Explorer, right-click the **CustomGreeting.xsd** file and choose **View Code**.</span></span>  
  
6.  <span data-ttu-id="05ef1-152">Dans l’éditeur Visual Studio, commencez par en remplaçant le code existant par le code suivant qui commence la définition du schéma CustomGreeting :</span><span class="sxs-lookup"><span data-stu-id="05ef1-152">In the Visual Studio editor, begin by replacing the existing code with the following code that begins the definition of the CustomGreeting schema:</span></span>  
  
    ```csharp  
    <?xml version="1.0" encoding="utf-8" ?>   
    <xs:schema id="XMLSchema1"   
                      targetNamespace="http://tempuri.org/XMLSchema1.xsd"  
                      elementFormDefault="qualified"  
                      xmlns="http://tempuri.org/XMLSchema1.xsd"  
                      xmlns:mstns="http://tempuri.org/XMLSchema1.xsd"  
                      xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    </xs:schema>  
    ```  
  
     <span data-ttu-id="05ef1-153">avec le code suivant, qui commence la définition du schéma CustomGreeting :</span><span class="sxs-lookup"><span data-stu-id="05ef1-153">with the following code that begins the definition of the CustomGreeting schema:</span></span>  
  
    ```csharp  
    <?xml version="1.0" encoding="utf-16"?>  
    <xsd:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns="echov2://microsoft.adapters.samples.echov2/PreDefinedTypes" elementFormDefault="qualified" targetNamespace="echov2://microsoft.adapters.samples.echov2/PreDefinedTypes" xmlns:xsd ="http://www.w3.org/2001/XMLSchema">  
    ```  
  
7.  <span data-ttu-id="05ef1-154">Ajoutez la commande suivante pour définir l’élément CustomGreeting :</span><span class="sxs-lookup"><span data-stu-id="05ef1-154">Add the following to define the CustomGreeting element:</span></span>  
  
    ```csharp  
    <xsd:element name="greeting" type="CustomGreeting" />  
    ```  
  
8.  <span data-ttu-id="05ef1-155">Maintenant, ajoutez la définition du type complexe CustomGreeting :</span><span class="sxs-lookup"><span data-stu-id="05ef1-155">Now add the definition of the CustomGreeting complex type:</span></span>  
  
    ```csharp  
    <xsd:complexType name="CustomGreeting">  
      <xsd:sequence>  
        <xsd:element name="address" type="UsAddress" />  
        <xsd:element name="greetingText" type="xsd:string" />  
      </xsd:sequence>  
    </xsd:complexType>  
    ```  
  
9. <span data-ttu-id="05ef1-156">Continuer la définition de schéma CustomGreeting en ajoutant le type complexe UsAddress :</span><span class="sxs-lookup"><span data-stu-id="05ef1-156">Continue the CustomGreeting schema definition by adding the  UsAddress complex type:</span></span>  
  
    ```csharp  
    <xsd:complexType name="UsAddress">  
      <xsd:sequence>  
        <xsd:element minOccurs="1" maxOccurs="1" name="street1" nillable="true" type="xsd:string" />  
        <xsd:element minOccurs="0" maxOccurs="1" name="street2" type="xsd:string" />  
        <xsd:element minOccurs="1" maxOccurs="1" name="city" type="xsd:string" />  
        <xsd:element minOccurs="1" maxOccurs="1" name="state" type="xsd:string" />  
        <xsd:element name="zip" type="PostalCode" />  
      </xsd:sequence>  
    </xsd:complexType>  
    ```  
  
10. <span data-ttu-id="05ef1-157">Terminer la définition du schéma CustomGreeting en ajoutant le type simple PostalCode et la balise de fermeture pour le schéma :</span><span class="sxs-lookup"><span data-stu-id="05ef1-157">Complete the definition of the CustomGreeting schema by adding the PostalCode simple type and the closing tag for the schema:</span></span>  
  
    ```csharp  
      <xsd:simpleType name="PostalCode">  
        <xsd:restriction base="xsd:positiveInteger">  
          <xsd:pattern value="\d{5}" />  
        </xsd:restriction>  
      </xsd:simpleType>  
    </xsd:schema>  
    ```  
  
11. <span data-ttu-id="05ef1-158">Mettre à jour maintenant l’action de génération pour ce fichier afin qu’il est traité comme une ressource incorporée.</span><span class="sxs-lookup"><span data-stu-id="05ef1-158">Now update the build action for this file so it is treated as an embedded resource.</span></span> <span data-ttu-id="05ef1-159">Pour ce faire, dans le volet de la solution Visual Studio, cliquez sur le fichier et choisissez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="05ef1-159">To do this, in the Visual Studio solution pane, right-click the file and choose **Properties**.</span></span> <span data-ttu-id="05ef1-160">Modifier l’Action de génération à partir de **aucun** à **ressource incorporée**.</span><span class="sxs-lookup"><span data-stu-id="05ef1-160">Change Build Action from **None** to **Embedded Resource**.</span></span>  
  
12. <span data-ttu-id="05ef1-161">Dans Visual Studio, à partir de la **fichier** menu, cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="05ef1-161">In Visual Studio, from the **File** menu, click **Save All**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05ef1-162">Vous avez enregistré votre travail.</span><span class="sxs-lookup"><span data-stu-id="05ef1-162">You saved your work.</span></span> <span data-ttu-id="05ef1-163">Vous pouvez en toute sécurité fermer Visual Studio pour l’instant ou accédez à l’étape suivante, [étape 7 : implémenter le Gestionnaire de sortie synchrone pour l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="05ef1-163">You can safely close Visual Studio at this time or go to the next step, [Step 7: Implement the Synchronous Outbound Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter.md).</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="05ef1-164">Quoi simplement ?</span><span class="sxs-lookup"><span data-stu-id="05ef1-164">What Did I Just Do?</span></span>  
 <span data-ttu-id="05ef1-165">Vous venez d’implémenter les métadonnées de la fonctionnalité de l’adaptateur de l’écho de résolution.</span><span class="sxs-lookup"><span data-stu-id="05ef1-165">You just implemented the metadata resolving capability for the echo adapter.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="05ef1-166">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="05ef1-166">Next Steps</span></span>  
 <span data-ttu-id="05ef1-167">Dans l’étape suivante, vous implémentez le Gestionnaire de sortie synchrone pour l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="05ef1-167">In the next step, you implement the synchronous outbound handler for the Echo Adapter.</span></span> <span data-ttu-id="05ef1-168">Vous ensuite implémentez le Gestionnaire d’entrée synchrone et puis générez et déployez l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="05ef1-168">You then implement the synchronous inbound handler and then build and deploy the Echo Adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ef1-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05ef1-169">See Also</span></span>  
 <span data-ttu-id="05ef1-170">[Étape 5 : Implémenter le Gestionnaire de recherche de métadonnées de l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="05ef1-170">[Step 5: Implement the Metadata Search Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md) </span></span>  
 <span data-ttu-id="05ef1-171">[Étape 7 : Implémenter le Gestionnaire de sortie synchrone pour l’adaptateur de l’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="05ef1-171">[Step 7: Implement the Synchronous Outbound Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter.md) </span></span>  
 [<span data-ttu-id="05ef1-172">Didacticiel 1 : Développer l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="05ef1-172">Tutorial 1: Develop the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)