---
title: "Recommandées de développement à l’aide de WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ea3a13b-e41f-4920-bf0d-26f7bb145aa3
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4693d3ae4a443138c078e0da415fb72205dbd528
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="development-best-practices-using-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="a3246-102">Recommandées de développement à l’aide de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="a3246-102">Development best practices using the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="a3246-103">Vous pouvez utiliser les meilleures pratiques dans cette rubrique afin d’améliorer vos applications et les cartes.</span><span class="sxs-lookup"><span data-stu-id="a3246-103">You can use the best practices in this topic to improve your applications and adapters.</span></span>  
  
## <a name="call-abort-before-close-on-channel-exception"></a><span data-ttu-id="a3246-104">Abandon de l’appel avant de fermer sur l’Exception de canal</span><span class="sxs-lookup"><span data-stu-id="a3246-104">Call Abort Before Close on Channel Exception</span></span>  
 <span data-ttu-id="a3246-105">Lorsque vous écrivez une application qui utilise le modèle de canal WCF, vous devez appeler `IRequestChannel.Abort` avant d’appeler `ChannelFactory.Close`.</span><span class="sxs-lookup"><span data-stu-id="a3246-105">When you write an application that uses the WCF channel model, you should call `IRequestChannel.Abort` before calling `ChannelFactory.Close`.</span></span> <span data-ttu-id="a3246-106">Si vous ne le faites pas, `ChannelFactory.Close` lève une exception.</span><span class="sxs-lookup"><span data-stu-id="a3246-106">If you do not, `ChannelFactory.Close` throws an exception.</span></span>  
  
 <span data-ttu-id="a3246-107">Dans l’exemple suivant, les opérations de canal sont tentées dans un bloc try/catch.</span><span class="sxs-lookup"><span data-stu-id="a3246-107">In the following example, channel operations are attempted within a try/catch block.</span></span> <span data-ttu-id="a3246-108">Si une exception se produit, le canal est abandonné.</span><span class="sxs-lookup"><span data-stu-id="a3246-108">If an exception occurs, the channel is aborted.</span></span>  
  
```csharp  
ChannelFactory<IRequestChannel> cf = new  ChannelFactory<IRequestChannel>();  
IRequestChannel channel = null;  
try  
{  
  cf.Open();  
  channel = cf.CreateChannel();  
  channel.Open();  
  channel.Request();// This causes the channel to go into a faulted state.  
  channel.Close();  
}  
catch (Exception e)  
{  
  // Abort the channel if we have one  
  if(channel != null)  
    channel.Abort();  
}  
finally  
{  
  if (cf.State == CommunicationState.Opened)  
  {  
    cf.Close(); // It throws an exception that the channel is in a faulted state.  
  }  
}  
```  
  
## <a name="implement-both-asynchronous-and-synchronous-handlers"></a><span data-ttu-id="a3246-109">Implémenter des gestionnaires asynchrones ou synchrones</span><span class="sxs-lookup"><span data-stu-id="a3246-109">Implement Both Asynchronous and Synchronous Handlers</span></span>  
 <span data-ttu-id="a3246-110">Si possible, implémentez les gestionnaires asynchrones ou synchrones dans votre carte.</span><span class="sxs-lookup"><span data-stu-id="a3246-110">If possible, implement both asynchronous and synchronous handlers in your adapter.</span></span> <span data-ttu-id="a3246-111">Si votre adaptateur implémente uniquement les appels synchrones, vous risquez de rencontrer des problèmes de blocage lors du traitement d’un volume important de messages ou lorsque l’adaptateur est utilisé dans un environnement multithread.</span><span class="sxs-lookup"><span data-stu-id="a3246-111">If your adapter only implements synchronous calls, you may run into blocking issues when processing a large volume of messages or when the adapter is used in a multithreaded environment.</span></span>  
  
## <a name="use-connection-pooling"></a><span data-ttu-id="a3246-112">Utiliser le regroupement de connexions</span><span class="sxs-lookup"><span data-stu-id="a3246-112">Use Connection Pooling</span></span>  
 <span data-ttu-id="a3246-113">Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] prend en charge le regroupement de connexions par défaut.</span><span class="sxs-lookup"><span data-stu-id="a3246-113">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] supports connection pooling by default.</span></span> <span data-ttu-id="a3246-114">Toutefois, c’est au développeur d’adaptateur pour déterminer les propriétés à exposer en tant que la liaison des propriétés de regroupement de connexions.</span><span class="sxs-lookup"><span data-stu-id="a3246-114">However, it is up to the adapter developer to determine which connection pooling properties to expose as binding properties.</span></span> <span data-ttu-id="a3246-115">Les paramètres de Pool de connexions disponibles sont définies dans `Microsoft.ServiceModel.Channels.Common.ConnectionPoolSettings`.</span><span class="sxs-lookup"><span data-stu-id="a3246-115">The available Connection Pool settings are defined within `Microsoft.ServiceModel.Channels.Common.ConnectionPoolSettings`.</span></span>  
  
 <span data-ttu-id="a3246-116">Il n’existe aucune option dans le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] exposer facilement ces propriétés en tant que propriétés de connexion de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="a3246-116">There are no options within the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to easily expose these properties as adapter connection properties.</span></span> <span data-ttu-id="a3246-117">Le développeur d’adaptateur doit définir manuellement les propriétés dans l’implémentation de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="a3246-117">The adapter developer must manually define the properties in the adapter implementation.</span></span>  
  
```csharp  
public CustomAdapter(): base()  
{  
   this.Settings.ConnectionPool.EnablePooling = true;  
   this.Settings.ConnectionPool.HandlersShareSameConnection = true;  
   this.Settings.ConnectionPool.MaxConnectionsPerSystem = 50;  
   this.Settings.ConnectionPool.MaxAvailableConnections = 5;  
}  
```  
  
## <a name="ensure-that-the-adapter-supports-two-way-operations"></a><span data-ttu-id="a3246-118">Assurez-vous que l’adaptateur prend en charge les opérations bidirectionnelles</span><span class="sxs-lookup"><span data-stu-id="a3246-118">Ensure That the Adapter Supports Two-Way Operations</span></span>  
 <span data-ttu-id="a3246-119">Si votre carte est appelée à partir de BizTalk Server, il doit prendre en charge les opérations bidirectionnelles, même si la valeur de retour est void.</span><span class="sxs-lookup"><span data-stu-id="a3246-119">If your adapter is called from BizTalk Server, it must support two-way operations, even if the return value is void.</span></span> <span data-ttu-id="a3246-120">Cela est, car BizTalk Server attend une réponse retournée à partir de n’importe quel demande sortante et lève une exception si votre adaptateur implémente uniquement les opérations unidirectionnelles.</span><span class="sxs-lookup"><span data-stu-id="a3246-120">This is because BizTalk Server expects a response returned from any outgoing request, and throws an exception if your adapter only implements one-way operations.</span></span>  
  
 <span data-ttu-id="a3246-121">Voici un exemple d’un contrat demande-réponse qui retourne void.</span><span class="sxs-lookup"><span data-stu-id="a3246-121">Here is an example of a request-response contract that returns void.</span></span>  
  
```csharp  
[ServiceContract(Namespace=”Http:Microsoft.BizTalk.Samples.WCFAdapterSample”)]  
public interface ICalculator  
{  
   [OperationContract]  
   void Add(double n1, double n2);  
}  
```  
  
## <a name="implement-tracing"></a><span data-ttu-id="a3246-122">Implémenter le suivi</span><span class="sxs-lookup"><span data-stu-id="a3246-122">Implement Tracing</span></span>  
 <span data-ttu-id="a3246-123">Au cours du cycle de développement, il ne semble pas important d’ajouter le suivi à votre carte, étant donné que vous pouvez parcourir le code et déboguer les problèmes.</span><span class="sxs-lookup"><span data-stu-id="a3246-123">During the development cycle, it might not seem important to add tracing to your adapter, since you can step through the code and debug any problems.</span></span> <span data-ttu-id="a3246-124">Toutefois, une fois que l’adaptateur est installé dans un environnement de production, vous peut-être pas en mesure d’utiliser le débogage du runtime pour isoler les problèmes.</span><span class="sxs-lookup"><span data-stu-id="a3246-124">However, once the adapter is installed in a production environment, you might not be able to use run-time debugging to isolate problems.</span></span> <span data-ttu-id="a3246-125">Si vous avez activé le suivi dans l’ensemble de votre adaptateur, il peut être utilisé pour isoler où des échecs sont produisent.</span><span class="sxs-lookup"><span data-stu-id="a3246-125">If you have enabled tracing throughout your adapter, it can be used to isolate where failures are occurring.</span></span>  
  
 <span data-ttu-id="a3246-126">Consultez [Trace une carte avec WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/trace-an-adapter-with-the-wcf-lob-adapter-sdk.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="a3246-126">See [Trace an adapter with the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/trace-an-adapter-with-the-wcf-lob-adapter-sdk.md) for further details.</span></span>  
  
## <a name="use-uri-properties-for-frequently-changed-settings"></a><span data-ttu-id="a3246-127">Utiliser les propriétés de l’URI pour les paramètres modifiés fréquemment</span><span class="sxs-lookup"><span data-stu-id="a3246-127">Use URI Properties for Frequently Changed Settings</span></span>  
 <span data-ttu-id="a3246-128">Lorsque vous décidez d’exposer une propriété personnalisée en tant qu’une liaison ou une propriété URI, il est recommandé d’utiliser une propriété URI si la valeur change souvent.</span><span class="sxs-lookup"><span data-stu-id="a3246-128">When deciding whether to expose a custom property as a binding or URI property, it is recommended to use a URI property if the value changes often.</span></span> <span data-ttu-id="a3246-129">Propriétés de liaison doivent être réservée pour les valeurs qui changent rarement.</span><span class="sxs-lookup"><span data-stu-id="a3246-129">Binding properties should be reserved for values that rarely change.</span></span>  
  
 <span data-ttu-id="a3246-130">Un exemple de propriété de liaison est un nom de serveur de base de données qui est utilisé par toutes les connexions.</span><span class="sxs-lookup"><span data-stu-id="a3246-130">An example binding property would be a database server name that is used by all connections.</span></span> <span data-ttu-id="a3246-131">Un exemple de propriété URI serait une table spécifique ou une procédure stockée à utiliser par cette connexion spécifique.</span><span class="sxs-lookup"><span data-stu-id="a3246-131">An example URI property would be a specific table or stored procedure to be used by that specific connection.</span></span>  
  
## <a name="do-not-pass-user-name-or-password-values-in-the-uri"></a><span data-ttu-id="a3246-132">Ne passez pas de nom d’utilisateur ou des valeurs de mot de passe dans l’URI</span><span class="sxs-lookup"><span data-stu-id="a3246-132">Do Not Pass User Name or Password Values in the URI</span></span>  
 <span data-ttu-id="a3246-133">Si votre adaptateur requiert des informations d’identification de l’appelant, il est recommandé d’utiliser le **ClientCredentials** classe pour récupérer les informations d’identification des valeurs au lieu de passer les informations d’identification du client dans le cadre de l’URI.</span><span class="sxs-lookup"><span data-stu-id="a3246-133">If your adapter requires the caller’s credentials, it is recommended to use the **ClientCredentials** class to retrieve credential values instead of passing client credentials as part of the URI.</span></span> <span data-ttu-id="a3246-134">Le **ClientCredentials** classe est une fonctionnalité standard de WCF est conçu pour passer des informations d’identification à partir du client au service de manière plus sécurisée.</span><span class="sxs-lookup"><span data-stu-id="a3246-134">The **ClientCredentials** class is a standard feature of WCF that is intended for passing credential information from the client to the service in a more secure manner.</span></span> <span data-ttu-id="a3246-135">En transmettant les informations utilisateur dans la chaîne d’URI peut exposer les informations utilisateur lors de leur transit.</span><span class="sxs-lookup"><span data-stu-id="a3246-135">Passing the user information as part of the URI string may expose the user information while in transit.</span></span>  
  
 <span data-ttu-id="a3246-136">Les méthodes recommandées de passer les informations d’identification sont affichés dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="a3246-136">The recommended methods of passing credentials are shown in the following table.</span></span>  
  
|<span data-ttu-id="a3246-137">Méthode</span><span class="sxs-lookup"><span data-stu-id="a3246-137">Method</span></span>|<span data-ttu-id="a3246-138"> Description</span><span class="sxs-lookup"><span data-stu-id="a3246-138">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a3246-139">Moment du design</span><span class="sxs-lookup"><span data-stu-id="a3246-139">Design time</span></span>|<span data-ttu-id="a3246-140">Lorsque vous utilisez la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], vous pouvez spécifier les types d’informations d’identification du client qui prend en charge de la carte.</span><span class="sxs-lookup"><span data-stu-id="a3246-140">When using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], you can specify the client credential types that the adapter supports.</span></span>|  
|<span data-ttu-id="a3246-141">Durée d’exécution</span><span class="sxs-lookup"><span data-stu-id="a3246-141">Run time</span></span>|<span data-ttu-id="a3246-142">Lorsque vous utilisez un proxy .NET CLR généré, vous pouvez définir par programme le client informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="a3246-142">When using a generated .NET CLR proxy, you can programmatically set the client credentials.</span></span><br /><br /> `static void Main(string[] args) {    EchoServiceClient client = new EchoServiceClient();    client.ClientCredentials.UserName.UserName = "TestUser";    client.ClientCredentials.UserName.Password = "TestPassword";    string response=client.EchoString("Test String"); }`<br /><br /> <span data-ttu-id="a3246-143">Si vous avez besoin d’interagir directement avec le canal, vous pouvez également utiliser le modèle de canal WCF pour spécifier les informations d’identification du client lors de la création d’une fabrique de canaux.</span><span class="sxs-lookup"><span data-stu-id="a3246-143">Alternatively, if you need to interact with the channel directly, you can use the WCF channel model to specify the client credentials when creating a channel factory.</span></span><br /><br /> `EchoAdapterBinding binding = new EchoAdapterBinding(); binding.Count = 3; ClientCredentials clientCredentials = new ClientCredentials(); clientCredentials.UserName.UserName = "TestUser"; clientCredentials.UserName.Password = "TestPassword"; BindingParameterCollection bindingParms = new BindingParameterCollection(); bindingParms.Add(clientCredentials); EndpointAddress address = new EndpointAddress("echo://"); IChannelFactory<IRequestChannel> requestChannelFactory = binding.BuildChannelFactory<IRequestChannel>(bindingParms); requestChannelFactory.Open();`|  
|<span data-ttu-id="a3246-144">Configuration WCF</span><span class="sxs-lookup"><span data-stu-id="a3246-144">WCF configuration</span></span>|<span data-ttu-id="a3246-145">Dans le fichier de configuration client, ajoutez une \<endpointBehaviors\> élément inclut \<clientCredentials\>.</span><span class="sxs-lookup"><span data-stu-id="a3246-145">In the client configuration file, add an \<endpointBehaviors\> element that includes \<clientCredentials\>.</span></span><br /><br /> `<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">       <system.serviceModel>           . . . . .           <behaviors>             <endpointBehaviors>               <behavior name="clientEndpointCredential">                 <clientCredentials>                   <windows allowNtlm="false" allowedImpersonationLevel="Delegation" />                    </clientCredentials>               </behavior>             </endpointBehaviors>           </behaviors>       </system.serviceModel>   </configuration>`|  
|<span data-ttu-id="a3246-146">À l’aide de BizTalk</span><span class="sxs-lookup"><span data-stu-id="a3246-146">Using BizTalk</span></span>|<span data-ttu-id="a3246-147">Lorsque vous utilisez l’adaptateur WCF pour consommer votre carte, vous pouvez ajouter la **clientCredentials** extension de comportement sur le **comportement** onglet. Une fois qu’il a été ajouté, vous pouvez définir des informations d’identification du client souhaité dans le comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a3246-147">When using the WCF adapter to consume your adapter, you can add the **clientCredentials** behavior extension on the **Behavior** tab. Once this has been added, you can set the desired client credentials in the endpoint behavior.</span></span>|  
  
## <a name="do-not-return-both-strongdatasettype-and-weakdatasettype"></a><span data-ttu-id="a3246-148">Ne retournent pas les deux StrongDataSetType et WeakDataSetType</span><span class="sxs-lookup"><span data-stu-id="a3246-148">Do Not Return Both StrongDataSetType and WeakDataSetType</span></span>  
 <span data-ttu-id="a3246-149">Si votre adaptateur renvoie un `DataSet`, utilisez `Microsoft.ServiceModel.Channels.Common.QualifiedType.StrongDataSetType%2A` ou `Microsoft.ServiceModel.Channels.Common.QualifiedType.WeakDataSetType%2A`, mais n’utilisent pas les deux en même temps.</span><span class="sxs-lookup"><span data-stu-id="a3246-149">If your adapter returns a `DataSet`, use either `Microsoft.ServiceModel.Channels.Common.QualifiedType.StrongDataSetType%2A` or `Microsoft.ServiceModel.Channels.Common.QualifiedType.WeakDataSetType%2A`, but do not use both at the same time.</span></span> <span data-ttu-id="a3246-150">Le nom du nœud racine et espace de noms généré par les deux types sont identiques et ne peut pas exister simultanément dans un WSDL.</span><span class="sxs-lookup"><span data-stu-id="a3246-150">The root node name and namespace produced by both types are identical, and cannot exist simultaneously in a WSDL.</span></span>  
  
 <span data-ttu-id="a3246-151">Alors que `WeakDataSetType` et `StrongDataSetType` tous deux représentent un `System.Data.DataSet`, `StrongDataSetType` est plus facile à utiliser dans les applications .NET, étant donné que le proxy généré apparaît sous la forme `System.Data.Dataset`.</span><span class="sxs-lookup"><span data-stu-id="a3246-151">While `WeakDataSetType` and `StrongDataSetType` both represent a `System.Data.DataSet`, `StrongDataSetType` is easier to use in .NET applications, since the proxy generated appears as `System.Data.Dataset`.</span></span> <span data-ttu-id="a3246-152">Le proxy généré par `WeakDataSetType` est `XmlElement[]`, qui est plus difficile à utiliser dans une application .NET.</span><span class="sxs-lookup"><span data-stu-id="a3246-152">The proxy generated by `WeakDataSetType` is `XmlElement[]`, which is more difficult to use in a .NET application.</span></span>  <span data-ttu-id="a3246-153">BizTalk Server ne peut pas utiliser le schéma retourné de `StrongDataSet`, mais est en mesure de consommer `WeakDataSetType`.</span><span class="sxs-lookup"><span data-stu-id="a3246-153">BizTalk Server cannot consume the schema returned from `StrongDataSet`, but is able to consume `WeakDataSetType`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3246-154">`StrongDataSetType`et `WeakDataSetType` uniquement contrôler comment l’application client interprète les messages XML transmis par l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="a3246-154">`StrongDataSetType` and `WeakDataSetType` only control how the client application interprets the XML messages passed by the adapter.</span></span> <span data-ttu-id="a3246-155">Le message XML est le même quel type est spécifié.</span><span class="sxs-lookup"><span data-stu-id="a3246-155">The XML message is the same regardless of which type is specified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3246-156">Lors du retour `StrongDataSetType`, vous devez définir `Microsoft.ServiceModel.Channels.Common.MetadataSettings.CompileWsdl%2A` à `false`.</span><span class="sxs-lookup"><span data-stu-id="a3246-156">When returning `StrongDataSetType`, you must set `Microsoft.ServiceModel.Channels.Common.MetadataSettings.CompileWsdl%2A` to `false`.</span></span> <span data-ttu-id="a3246-157">Lorsque la valeur `true`, la valeur par défaut, `XmlSchemaSet::Compile` est appelée au sein de l’adaptateur pour vous assurer qu’aucune erreur dans le WSDL, cependant le schéma produit par `StrongDataSetType` génère une exception dans `XmlSchemaSet`.</span><span class="sxs-lookup"><span data-stu-id="a3246-157">When set to `true`, the default, `XmlSchemaSet::Compile` is called within the adapter to ensure there are no errors in the WSDL, however the schema produced by `StrongDataSetType` generates an exception in `XmlSchemaSet`.</span></span>  
>   
>  <span data-ttu-id="a3246-158">Paramètre `CompileWsdl` à `false` ignore la validation de schéma WSDL au sein de l’adaptateur et la validation se produit pendant la génération du proxy.</span><span class="sxs-lookup"><span data-stu-id="a3246-158">Setting `CompileWsdl` to `false` bypasses WSDL schema validation within the adapter and validation occurs during proxy generation.</span></span>  <span data-ttu-id="a3246-159">Utilitaires, tels que svcutil.exe sont en mesure de générer un proxy pour les deux `StrongDataSetType` et `WeakDataSetType`.</span><span class="sxs-lookup"><span data-stu-id="a3246-159">Utilities such as svcutil.exe are able to generate a proxy for both `StrongDataSetType` and `WeakDataSetType`.</span></span>  
  
 <span data-ttu-id="a3246-160">Pour travailler avec les environnements BizTalk et .NET, envisagez d’implémenter une propriété de liaison qui permet de basculer entre les deux types de retournés, comme stipulé par l’environnement.</span><span class="sxs-lookup"><span data-stu-id="a3246-160">To work with both BizTalk and .NET environments, consider implementing a binding property that allows switching between the two return types as dictated by the environment.</span></span>  
  
```csharp  
internal static QualifiedType GetDataSetQualifiedType(MyAdapterBindingProperties bindingProperties)  
{  
   if (bindingProperties.EnableBizTalkCompatibility)  
      return QualifiedType.WeakDataSetType;  
   else  
      return QualifiedType.StrongDataSetType;  
}  
```  
  
## <a name="create-meaningful-xsd-schema-names-in-biztalk-server"></a><span data-ttu-id="a3246-161">Créer des noms de schéma XSD significatives dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="a3246-161">Create Meaningful XSD Schema Names in BizTalk Server</span></span>  
 <span data-ttu-id="a3246-162">Lors de l’utilisation du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] outil de conception, le nom du schéma XSD généré dans votre projet BizTalk est créé à l’aide de la `DefaultXsdFileNamePrefix` propriété, le `fileNameHint` annotation dans le WSDL et, si nécessaire, une valeur d’entier unique.</span><span class="sxs-lookup"><span data-stu-id="a3246-162">When using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] design-time tool, the name of the XSD schema generated in your BizTalk project is created using the `DefaultXsdFileNamePrefix` property, the `fileNameHint` annotation in the WSDL and, if required, a unique integer value.</span></span>  
  
 <span data-ttu-id="a3246-163">Par exemple, si `DefaultXsdFileNamePrefix` est défini sur « MyAdapter » et le `fileNameHint` annotation est définie sur « Stream », le schéma XSD créé est nommé MyAdapterStream.xsd.</span><span class="sxs-lookup"><span data-stu-id="a3246-163">For example, if `DefaultXsdFileNamePrefix` is set to “MyAdapter” and the `fileNameHint` annotation is set to “Stream”, the XSD schema created is named MyAdapterStream.xsd.</span></span>  
  
```  
<xs:schema elementFormDefault='qualified' targetNamespace='http://schemas.microsoft.com/Message' xmlns:xs='http://www.w3.org/2001/XMLSchema' xmlns:tns='http://schemas.microsoft.com/Message'>  
<xs:annotation>  
<xs:appinfo>  
<fileNameHint xmlns='http://schemas.microsoft.com/servicemodel/adapters/metadata/xsd'>Stream</fileNameHint>  
</xs:appinfo>  
</xs:annotation>  
<xs:simpleType name='StreamBody'>  
<xs:restriction base='xs:base64Binary' />  
</xs:simpleType>  
</xs:schema>  
  
```  
  
> [!NOTE]
>  <span data-ttu-id="a3246-164">La valeur par défaut de `DefaultXsdFileNamePrefix` est le nom de votre liaison.</span><span class="sxs-lookup"><span data-stu-id="a3246-164">The default value of `DefaultXsdFileNamePrefix` is the name of your binding.</span></span> <span data-ttu-id="a3246-165">Pour spécifier une valeur différente, substituez `DefaultXsdFileNamePrefix` dans votre classe d’adaptateur qui est dérivé de `Microsoft.ServiceModel.Channels.Common.AdapterBinding`.</span><span class="sxs-lookup"><span data-stu-id="a3246-165">To specify a different value, override `DefaultXsdFileNamePrefix` in your Adapter class that is derived from `Microsoft.ServiceModel.Channels.Common.AdapterBinding`.</span></span>  
  
 <span data-ttu-id="a3246-166">Il existe deux méthodes pour ajouter la `fileNameHint` annotation au schéma : remplacer l’exportation... Méthodes de schéma sur OperationMetadata\TypeMetadata ou remplacer l’implémentation de IWsdlRetrieval de la carte.</span><span class="sxs-lookup"><span data-stu-id="a3246-166">There are two possible methods to add the `fileNameHint` annotation to the schema: override the Export…Schema methods on OperationMetadata\TypeMetadata or override the IWsdlRetrieval implementation of the adapter.</span></span> <span data-ttu-id="a3246-167">Soit la méthode, vous pouvez appeler l’implémentation de base, puis ajoutez l’annotation pour les schémas dans la collection de schémas.</span><span class="sxs-lookup"><span data-stu-id="a3246-167">For either method, you can call the base implementation and then add the annotation to the schemas in the schema collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3246-168">Lors de la substitution de l’exportation... Méthodes de schéma, il peut y avoir plusieurs définitions de type d’opération dans le même schéma. l’adaptateur doit vous assurer que plusieurs occurrences de la `fileNameHints` annotation dans le même schéma éviter les conflits.</span><span class="sxs-lookup"><span data-stu-id="a3246-168">When overriding the Export…Schema methods, there may be multiple operation/type definitions in the same schema; the adapter should make sure that multiple occurrences of the `fileNameHints` annotation in the same schema do not conflict.</span></span> <span data-ttu-id="a3246-169">Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] utilise la première occurrence de `fileNameHint` si elle apparaît plusieurs fois dans un schéma.</span><span class="sxs-lookup"><span data-stu-id="a3246-169">The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] uses the first occurrence of `fileNameHint` if it occurs multiple times within a schema.</span></span>  
  
 <span data-ttu-id="a3246-170">Dans l’exemple suivant, IWsdlRetrieval est utilisé pour ajouter le `fileNameHint` annotation au service WSDL.</span><span class="sxs-lookup"><span data-stu-id="a3246-170">In the following example, IWsdlRetrieval is used to add the `fileNameHint` annotation to the WSDL.</span></span>  
  
```csharp  
sealed class MyAdapterWsdlRetrieval : IWsdlRetrieval  
{  
   IWsdlRetrieval mBaseWsdlRetrieval;  
   public MyAdapterWsdlRetrieval(IWsdlRetrieval baseWsdlRetrieval)  
   {  
      mBaseWsdlRetrieval = baseWsdlRetrieval;  
   }  
  
   ServiceDescription IWsdlRetrieval.GetWsdl(Microsoft.ServiceModel.Channels.MetadataRetrievalNode[] nodes, Uri uri, TimeSpan timeout)  
   {  
      ServiceDescription baseDesc = mBaseWsdlRetrieval.GetWsdl(nodes, uri, timeout);  
      foreach (XmlSchema schema in baseDesc.Types.Schemas)  
      {  
         CreateFileNameHint(schema);  
      }  
      return baseDesc;  
   }  
  
   void CreateFileNameHint(XmlSchema schema)  
   {  
      string targetNamespace = schema.TargetNamespace;  
      if (string.IsNullOrEmpty(targetNamespace))  
         return;  
      string fileNameHint = null;  
      //determine the filename based on namespace  
      if (targetNamespace.StartsWith("myadapter:// adapters.samples.myadaptpter/HelloWorld"))  
      {  
         fileNameHint = "HelloWorld";  
      }  
      if (targetNamespace.StartsWith("myadapter:// adapters.samples.myadapter/Hello"))  
      {  
         fileNameHint = "Hello";  
      }  
      //create the annotation and populate it with fileNameHint  
      XmlSchemaAnnotation annotation = new XmlSchemaAnnotation();  
      XmlSchemaAppInfo appInfo = new XmlSchemaAppInfo();  
      XmlDocument doc = new XmlDocument();  
      XmlNode[] fileNameHintNodes = new XmlNode[1];  
      fileNameHintNodes[0] = doc.CreateElement(null, "fileNameHint", "http://schemas.microsoft.com/servicemodel/adapters/metadata/xsd");  
      fileNameHintNodes[0].AppendChild(doc.CreateTextNode(fileNameHint));  
      appInfo.Markup = fileNameHintNodes;  
      annotation.Items.Add(appInfo);  
      schema.Items.Insert(0, annotation);  
   }  
```  
  
## <a name="do-not-modify-adapterenvironmentsettings-during-processing"></a><span data-ttu-id="a3246-171">Ne modifiez pas AdapterEnvironmentSettings lors du traitement</span><span class="sxs-lookup"><span data-stu-id="a3246-171">Do Not Modify AdapterEnvironmentSettings During Processing</span></span>  
 <span data-ttu-id="a3246-172">L’adaptateur doit uniquement définir le **AdapterEnvironmentSettings**, **ConnectionPoolManager**, **ConnectionPool**, et **CommonCacheSize**lors de l’initialisation de carte et ne doit pas tenter de modifier les valeurs pour une instance en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a3246-172">The adapter should only set the **AdapterEnvironmentSettings**, **ConnectionPoolManager**, **ConnectionPool**, and **CommonCacheSize** during adapter initialization and should not attempt to modify the values for a running instance.</span></span>  
  
 <span data-ttu-id="a3246-173">Si ces paramètres sont modifiées sur une instance de la carte en cours d’exécution, cela peut entraîner de nouvelles connexions remplacement des paramètres de configuration pour les connexions en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a3246-173">If these settings are modified on a currently running adapter instance, this may result in new connections overwriting configuration settings for currently executing connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3246-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3246-174">See Also</span></span>  
 [<span data-ttu-id="a3246-175">Recommandées de développement à l’aide de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="a3246-175">Development best practices using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)