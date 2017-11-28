---
title: "Création d’un programme de résolution personnalisé avec un conteneur Unity | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6f95f5e-64dd-4cc6-802f-0c5fd6a01c91
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15952ef3cc8f19eaa5de1a4155d0dc7f6e03c5c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-custom-resolver-with-a-unity-container"></a><span data-ttu-id="1a3bf-102">Création d’un programme de résolution personnalisé avec un conteneur Unity</span><span class="sxs-lookup"><span data-stu-id="1a3bf-102">Creating a Custom Resolver with a Unity Container</span></span>
<span data-ttu-id="1a3bf-103">Vous pouvez créer un programme de résolution personnalisé à l’aide de la [bloc d’Application Unity](http://go.microsoft.com/fwlink/?LinkId=188286) (Unity) ([http://go.microsoft.com/fwlink/?LinkId=188286](http://go.microsoft.com/fwlink/?LinkId=188286)) pour l’injection de dépendance d’exécution des sources de logique et les métadonnées de résolution.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-103">You can create a custom resolver using the [Unity Application Block](http://go.microsoft.com/fwlink/?LinkId=188286) (Unity) ([http://go.microsoft.com/fwlink/?LinkId=188286](http://go.microsoft.com/fwlink/?LinkId=188286)) for run-time dependency injection of resolution logic and metadata sources.</span></span>
  
 <span data-ttu-id="1a3bf-104">**Fournisseurs de faits**</span><span class="sxs-lookup"><span data-stu-id="1a3bf-104">**Fact Providers**</span></span>  
  
 <span data-ttu-id="1a3bf-105">Les fournisseurs de faits sont des instances de classes qui implémentent la **IFactProvider** interface.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-105">Fact providers are instances of classes that implement the **IFactProvider** interface.</span></span> <span data-ttu-id="1a3bf-106">Cette interface expose trois différentes surcharges d’une méthode nommée **RegisterFact**.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-106">This interface exposes three different overloads of a method named **RegisterFact**.</span></span> <span data-ttu-id="1a3bf-107">Cette méthode accepte dans le message, la configuration du programme de résolution et, dans certains cas, le contexte du pipeline et retourne un objet.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-107">This method takes in the message, the resolver configuration, and, in some cases, the pipeline context, and returns an object.</span></span> <span data-ttu-id="1a3bf-108">Cet objet peut avoir des informations extraites à partir des entrées d’une certaine façon, il peut être un calcul d’une forme ou il peut être recherché à partir d’une source externe.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-108">This object may be information extracted from the inputs in some way, it may be a calculation of some form, or it may be looked up from some external source.</span></span> <span data-ttu-id="1a3bf-109">Chaque objet retourné par un fournisseur de faits peut être référencé en tant que fait et est en principe ajouté à une liste par le conteneur de résolution pour une utilisation ultérieure par un traducteur de faits.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-109">Each object returned by a fact provider can be referred to as a fact and is typically added to a list by the resolve container for later use by a fact translator.</span></span>  
  
 <span data-ttu-id="1a3bf-110">Un programme de résolution Unity peut avoir zéro ou plusieurs fournisseurs de faits qui peuvent être ajoutés ou supprimés à tout moment d’un changement de configuration unique.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-110">A Unity resolver may have zero or more fact providers that can be added or removed at any time with a single configuration change.</span></span>  
  
 <span data-ttu-id="1a3bf-111">Le code suivant est un exemple de la logique contenue dans un fournisseur de faits.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-111">The following code is an example of the logic contained in a fact provider.</span></span> <span data-ttu-id="1a3bf-112">Ce code peut également être trouvé dans le fichier ItineraryStaticFactProvider.cs de l’architecture ESB. Resolver.Itinerary.Facts projet.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-112">This code can also be found in the ItineraryStaticFactProvider.cs file of the ESB.Resolver.Itinerary.Facts project.</span></span> <span data-ttu-id="1a3bf-113">C’est un composant dans le programme de résolution d’itinéraire statique qui regroupe le nom et la version d’un itinéraire à partir de la chaîne de connexion du programme de résolution.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-113">It is a component in the ITINERARY-STATIC resolver that gathers the name and version of an itinerary from the resolver connection string.</span></span>  
  
```csharp  
public object RegisterFact(IBaseMessage message, IPipelineContext pipelineContext, Dictionary\<string, string> resolverContents)  
{  
    return GetItineraryFactFromResolver(resolverContents);  
}  
  
private static object GetItineraryFactFromResolver(Dictionary\<string, string> resolverContents)  
{              
    if (resolverContents == null)  
        throw new ArgumentNullException("resolverContents");  
  
    ItineraryFact itineraryFact = new ItineraryFact();  
    itineraryFact.Name = ResolverMgr.GetConfigValue(resolverContents, true, "name");  
    string version = ResolverMgr.GetConfigValue(resolverContents, false, "version");  
    if (!string.IsNullOrEmpty(version))  
    {  
        EventLogger.Write(string.Format("Version set with value {0}.", version));  
        itineraryFact.SetVersion(version);  
    }  
    return itineraryFact;  
}  
```  
  
 <span data-ttu-id="1a3bf-114">**Convertisseurs de faits**</span><span class="sxs-lookup"><span data-stu-id="1a3bf-114">**Fact Translators**</span></span>  
  
 <span data-ttu-id="1a3bf-115">Convertisseurs de faits sont des instances de classes qui implémentent la **IFactTranslator** interface.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-115">Fact translators are instances of classes that implement the **IFactTranslator** interface.</span></span> <span data-ttu-id="1a3bf-116">Cette interface expose une méthode unique nommée **TranslateFact**.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-116">This interface exposes a single method named **TranslateFact**.</span></span> <span data-ttu-id="1a3bf-117">Cette méthode prend dans un tableau d’objets qui contient une liste des faits et le dictionnaire de programme de résolution qui n’est plus tard renvoyé par le programme de résolution à l’aide du traducteur de faits.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-117">This method takes in an object array that contains a list of facts and the resolver dictionary that will later be returned by the resolver using the fact translator.</span></span> <span data-ttu-id="1a3bf-118">Un convertisseur de faits est chargé de traiter les faits fournis par les fournisseurs de faits d’une manière explicite, puis en remplissant le dictionnaire de programme de résolution.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-118">A fact translator is responsible for processing the facts provided by the fact providers in a meaningful way and then populating the resolver dictionary.</span></span>  
  
 <span data-ttu-id="1a3bf-119">Un programme de résolution Unity peut avoir zéro ou plusieurs traducteurs de faits qui peuvent être ajoutés ou supprimés à tout moment d’un changement de configuration unique.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-119">A Unity resolver may have zero or more fact translators that can be added or removed at any time with a single configuration change.</span></span>  
  
 <span data-ttu-id="1a3bf-120">Le code suivant est un exemple de la logique contenue dans un convertisseur de faits.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-120">The following code is an example of the logic contained in a fact translator.</span></span> <span data-ttu-id="1a3bf-121">Ce code peut également être trouvé dans le fichier ItineraryStaticFactTranslator.cs de l’architecture ESB. Resolver.Itinerary.Facts projet.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-121">This code can also be found in the ItineraryStaticFactTranslator.cs file of the ESB.Resolver.Itinerary.Facts project.</span></span> <span data-ttu-id="1a3bf-122">C’est un composant dans le programme de résolution d’itinéraire statique qui effectue une requête de base de données pour recueillir l’itinéraire XML pour un itinéraire par nom et, éventuellement, par version.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-122">It is a component in the ITINERARY-STATIC resolver that performs a database query to gather the itinerary XML for an itinerary by name and, optionally, by version.</span></span>  
  
```csharp  
public void TranslateFact(object[] facts, Dictionary\<string, string> factDictionary)  
{  
    #region Argument Check  
    if (null == facts) throw new ArgumentNullException("fact");  
    if (null == factDictionary) throw new ArgumentNullException("factDictionary");  
    #endregion  
  
    #region Local Variables  
    Version version = new Version(1, 0);                         
    #endregion  
    try  
    {  
        foreach (object fact in facts)  
        {  
            if (fact is ItineraryFact)  
            {  
                ItineraryFact targetFact = (ItineraryFact)fact;  
                factDictionary.Add(_FactKeyItineraryName, targetFact.Name ?? string.Empty);  
                if (null != targetFact.Version)  
                {  
                    factDictionary.Add(_FactKeyItineraryVersion, targetFact.Version.ToString(2) ?? string.Empty);  
                    version = targetFact.Version;  
                }  
  
                string xml = null;  
  
                if (targetFact.Version != null)  
                {  
                    xml = _repositoryProvider.GetItinerary(targetFact.Name, version.Major, version.Minor);  
                }  
                else  
                {  
                    xml = _repositoryProvider.GetItinerary(targetFact.Name);  
                }  
                if (!string.IsNullOrEmpty(xml))  
                {  
                    factDictionary.Add(_FactKeyItinerary, xml);  
                }  
  
                break;  
            }  
        }  
    }  
    #region Exception Handling  
    catch (System.Exception)  
    {  
        throw;  
    }              
    #endregion  
}  
#endregion  
```  
  
 <span data-ttu-id="1a3bf-123">**Résoudre les conteneurs**</span><span class="sxs-lookup"><span data-stu-id="1a3bf-123">**Resolve Containers**</span></span>  
  
 <span data-ttu-id="1a3bf-124">Un conteneur de résolution est une classe qui implémente le **IResolveContainer** interface.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-124">A resolve container is a class that implements the **IResolveContainer** interface.</span></span> <span data-ttu-id="1a3bf-125">En règle générale, il implémente également la **IResolveProvider** interface.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-125">Typically, it also implements the **IResolveProvider** interface.</span></span> <span data-ttu-id="1a3bf-126">Le **IResolveContainer** interface expose une méthode unique nommée **initialiser** qui accepte un **IUnityContainer**.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-126">The **IResolveContainer** interface exposes a single method named **Initialize** that takes in an **IUnityContainer**.</span></span> <span data-ttu-id="1a3bf-127">Le conteneur passé à cette méthode contiendra toutes les dépendances (autrement dit, les instances des classes **IFactProvider** et **IFactTranslator**et tous les autres types requis) nécessaires pour le programme de résolution pour terminer son traitement.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-127">The container passed to this method will contain all of the dependencies (that is, instances of the classes **IFactProvider** and **IFactTranslator**, and any other types required) necessary for the resolver to complete its processing.</span></span>  
  
 <span data-ttu-id="1a3bf-128">Le code suivant est un exemple d’implémentation de la **IResolveContainer** interface.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-128">The following code is an example of an implementation of the **IResolveContainer** interface.</span></span> <span data-ttu-id="1a3bf-129">Ce code peut également être trouvé dans le fichier StaticItineraryResolveContainer.cs de l’architecture ESB. Resolver.Itinerary projet.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-129">This code can also be found in the StaticItineraryResolveContainer.cs file of the ESB.Resolver.Itinerary project.</span></span>  
  
```csharp  
#region IResolveContainer Members  
  
private static IUnityContainer Container;  
  
// <summary>  
// This is used by the Unity resolver to initialize the current   
// object with the Unity container.  
// </summary>  
// <param name="container">Unity container used for dependency   
// injection.</param>  
// <remarks>  
// The container used is the ITINERARY container, although this is   
// configurable in Esb.config.  
// </remarks>  
  
public void Initialize(IUnityContainer container)  
{  
  if (container == null)  
    throw new ArgumentNullException("container");  
  
  Container = container;  
}  
#endregion  
```  
  
 <span data-ttu-id="1a3bf-130">Dans un conteneur de résolution, dans les implémentations de la **résoudre** méthodes à partir de la **IResolveProvider** interface, il n’est nécessaire pour une itération au sein de tous les fournisseurs de faits et les convertisseurs de faits de l’unité conteneur pour permettre à chacun d’eux pour effectuer leur traitement.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-130">In a resolve container, in the implementations of the **Resolve** methods from the **IResolveProvider** interface, it is necessary to iterate through all the fact providers and fact translators in the Unity container to allow each of them to perform their processing.</span></span>  
  
 <span data-ttu-id="1a3bf-131">Le code suivant est un exemple de la logique contenue dans un conteneur de résolution.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-131">The following code is an example of the logic contained in a Resolve container.</span></span> <span data-ttu-id="1a3bf-132">Ce code peut également être trouvé dans le fichier StaticItineraryResolveContainer.cs de l’architecture ESB. Resolver.Itinerary projet.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-132">This code can also be found in the StaticItineraryResolveContainer.cs file of the ESB.Resolver.Itinerary project.</span></span>  
  
```csharp  
public Dictionary\<string, string> Resolve(ResolverInfo resolverInfo,  
    XLANGMessage message)  
{  
    #region Argument Check  
    if (String.IsNullOrEmpty(resolverInfo.Config))  
        throw new ArgumentNullException("resolverInfo.Config");  
    if (String.IsNullOrEmpty(resolverInfo.Resolver))  
        throw new ArgumentNullException("resolverInfo.Resolver");  
    if (null == message)  
        throw new ArgumentNullException("message");  
    #endregion Argument Check  
  
    return ResolveStatic(resolverInfo.Config, resolverInfo.Resolver,  
        (factProvider, resolverContent) =>   
            factProvider.RegisterFact(message, resolverContent)  
     );  
}          
  
private Dictionary\<string, string> ResolveStatic(string config, string resolver,   
    Func<IFactProvider, Dictionary\<string, string>, object> RegisterFact)  
{  
    try  
    {  
        EventLogger.Write(string.Format("Received {0} value in ITINERARY STATIC resolver.", config));  
  
        Dictionary\<string, string> queryParams =  
                ResolverMgr.GetFacts(config, resolver);  
  
        List<object> facts = new List<object>();  
  
        foreach (IFactProvider factProvider in Container.ResolveAll<IFactProvider>())  
        {  
            facts.Add(RegisterFact(factProvider, queryParams));  
        }  
  
        Dictionary\<string, string> resolverDictionary = new Dictionary\<string, string>();  
  
        object[] convertedFacts = facts.ToArray();  
  
        foreach (IFactTranslator translator in Container.ResolveAll<IFactTranslator>())  
        {  
            translator.TranslateFact(convertedFacts, resolverDictionary);  
        }  
  
        return resolverDictionary;  
    }  
    catch (System.Exception ex)  
    {  
        EventLogger.Write(MethodInfo.GetCurrentMethod(), ex);  
        throw;  
    }  
}  
```  
  
 <span data-ttu-id="1a3bf-133">**Configuration d’un programme de résolution personnalisé Unity**</span><span class="sxs-lookup"><span data-stu-id="1a3bf-133">**Configuring a Custom Unity Resolver**</span></span>  
  
 <span data-ttu-id="1a3bf-134">Pour configurer un programme de résolution personnalisé Unity, les mêmes étapes de configuration s’appliquent lors de la création d’un programme de résolution personnalisé ; Toutefois, il est une configuration supplémentaire qui doit être incluse pour enregistrer correctement les composants qui composent le programme de résolution.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-134">To configure a custom Unity resolver, the same configuration steps apply as when creating a custom resolver; however, there is some additional configuration that must be included to properly register the components that make up the resolver.</span></span>  
  
 <span data-ttu-id="1a3bf-135">Tout d’abord, dans le fichier Esb.config, sous la déclaration de programme de résolution, un **resolverConfig** nœud doit être ajouté avec les deux propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="1a3bf-135">First, in the Esb.config file, under the resolver declaration, a **resolverConfig** node must be added with the following two properties:</span></span>  
  
-   <span data-ttu-id="1a3bf-136">**unitySectionName**.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-136">**unitySectionName**.</span></span> <span data-ttu-id="1a3bf-137">Cette propriété contient le nom de la section de configuration dans le fichier de configuration qui contient la configuration pour le bloc d’Application Unity ; par défaut, la valeur de cette propriété est **esb.resolver**.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-137">This property contains the name of the configuration section in the configuration file that contains the configuration for the Unity Application Block; by default, the value for this property is **esb.resolver**.</span></span>  
  
-   <span data-ttu-id="1a3bf-138">**unityContainerName**.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-138">**unityContainerName**.</span></span> <span data-ttu-id="1a3bf-139">Cette propriété contient le nom du conteneur Unity défini dans la configuration de Unity spécifique à votre programme de résolution personnalisé.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-139">This property contains the name of the Unity container defined in the Unity configuration specific to your custom resolver.</span></span>  
  
 <span data-ttu-id="1a3bf-140">Le code XML suivant est un exemple de la configuration nécessaire dans les **résolveurs** nœud.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-140">The following XML is an example of the configuration necessary in the **resolvers** node.</span></span>  
  
```xml  
<resolver name="ITINERARY-STATIC" type="Microsoft.Practices.ESB.Resolver.Unity.ResolveProvider, Microsoft.Practices.ESB.Resolver.Unity, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22">  
     <resolverConfig>  
          <add name="unitySectionName" value="esb.resolver" />  
          <add name="unityContainerName" value="ITINERARY" />  
     </resolverConfig>  
</resolver>  
```  
  
 <span data-ttu-id="1a3bf-141">Le code XML suivant est un exemple de la configuration nécessaire sous la **esb.resolver** nœud.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-141">The following XML is an example of the configuration necessary under the **esb.resolver** node.</span></span>  
  
```xml  
<typeAliases>  
     \<!-- Lifetime manager types -->  
     <typeAlias alias="singleton" type="Microsoft.Practices.Unity.ContainerControlledLifetimeManager, Microsoft.Practices.Unity, Version=1.2.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
     \<!-- std type providers -->  
     <typeAlias alias="string" type="System.String, mscorlib"/>  
     <typeAlias alias="int" type="System.Int32, mscorlib"/>  
     \<!-- repository providers -->  
     <typeAlias alias="IRepositoryProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.Facts.Repository.IRepositoryProvider, Microsoft.Practices.ESB.Resolver.Itinerary.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="SqlRepositoryProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.DataAccess.SqlRepositoryProvider, Microsoft.Practices.ESB.Resolver.Itinerary.DataAccess, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     \<!-- fact providers -->  
     <typeAlias alias="IFactProvider" type="Microsoft.Practices.ESB.Resolver.Facts.IFactProvider, Microsoft.Practices.ESB.Resolver.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="IFactTranslator" type="Microsoft.Practices.ESB.Resolver.Facts.IFactTranslator, Microsoft.Practices.ESB.Resolver.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="ItineraryFactProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.Facts.ItineraryFactProvider, Microsoft.Practices.ESB.Resolver.Itinerary.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="ItineraryStaticFactProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.Facts.ItineraryStaticFactProvider, Microsoft.Practices.ESB.Resolver.Itinerary.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="ItineraryHeaderFactProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.Facts.ItineraryHeaderFactProvider, Microsoft.Practices.ESB.Resolver.Itinerary.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="ResolutionFactProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.Facts.ResolutionFactProvider, Microsoft.Practices.ESB.Resolver.Itinerary.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="DefaultFactTranslator" type="Microsoft.Practices.ESB.Resolver.Facts.DefaultFactTranslator, Microsoft.Practices.ESB.Resolver.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="ItineraryFactTranslator" type="Microsoft.Practices.ESB.Resolver.Itinerary.Facts.ItineraryFactTranslator, Microsoft.Practices.ESB.Resolver.Itinerary.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     \<!-- resolve providers -->  
     <typeAlias alias="IResolveProvider" type="Microsoft.Practices.ESB.Resolver.IResolveProvider, Microsoft.Practices.ESB.Resolver, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="ItineraryResolveProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.BREItineraryResolverContainer,Microsoft.Practices.ESB.Resolver.Itinerary, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22 "/>  
     <typeAlias alias="StaticItineraryResolveProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.StaticItineraryResolveContainer,Microsoft.Practices.ESB.Resolver.Itinerary, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22 "/>  
</typeAliases>  
<containers>  
     <container name="ITINERARY">  
          <types>  
               <type type="IResolveProvider" mapTo="StaticItineraryResolveProvider" />  
               <type type="IRepositoryProvider" mapTo="SqlRepositoryProvider" name="CurrentRepositoryProvider">  
                    <lifetime type="singleton" />  
                    <typeConfig extensionType="Microsoft.Practices.Unity.Configuration.TypeInjectionElement,Microsoft.Practices.Unity.Configuration, Version=1.2.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35">  
                         <constructor>  
                              <param name="connectionStringName" parameterType="string">  
                                   <value value="ItineraryDb"/>  
                              </param>  
                              <param name="cacheManagerName" parameterType="string">  
                                   <value value="Itinerary Cache Manager"/>  
                              </param>  
                              <param name="cacheTimeout" parameterType="string">  
                                   <value value="120" />  
                              </param>  
                         </constructor>  
                    </typeConfig>  
               </type>  
               <type type="IFactProvider" mapTo="ResolutionFactProvider" name="ResolutionFactProvider"  />  
               <type type="IFactProvider" mapTo="ItineraryHeaderFactProvider" name="HeaderFactProvider"  />  
               <type type="IFactProvider" mapTo="ItineraryStaticFactProvider" name="StaticFactProvider"  />  
               <type type="IFactTranslator" mapTo="DefaultFactTranslator" name="DefaultFactTranslator">  
                    <lifetime type="singleton" />  
               </type>  
               <type type="IFactTranslator" mapTo="ItineraryFactTranslator" name="ItineraryFactTranslator">  
                    <lifetime type="singleton" />  
                    <typeConfig extensionType="Microsoft.Practices.Unity.Configuration.TypeInjectionElement,Microsoft.Practices.Unity.Configuration, Version=1.2.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35">  
                         <constructor>  
                              <param name="repositoryProvider" parameterType="IRepositoryProvider">  
                                   <dependency name="CurrentRepositoryProvider"/>  
                              </param>  
                         </constructor>  
                    </typeConfig>  
               </type>  
          </types>  
     </container>  
</containers>  
```  
  
 <span data-ttu-id="1a3bf-142">Pour plus d’informations sur la configuration est nécessaire dans le **esb.resolvers** nœud, consultez [schéma Source pour le bloc d’Application Unity](http://go.microsoft.com/fwlink/?LinkId=188288) ([http://go.microsoft.com/fwlink/ ? LinkId = 188288](http://go.microsoft.com/fwlink/?LinkId=188288)) sur MSDN.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-142">For detailed information about the configuration that is necessary in the **esb.resolvers** node, see [Source Schema for the Unity Application Block](http://go.microsoft.com/fwlink/?LinkId=188288) ([http://go.microsoft.com/fwlink/?LinkId=188288](http://go.microsoft.com/fwlink/?LinkId=188288)) on MSDN.</span></span>  
  
 <span data-ttu-id="1a3bf-143">**Création d’un programme de résolution personnalisé Unity**</span><span class="sxs-lookup"><span data-stu-id="1a3bf-143">**Creating a Custom Unity Resolver**</span></span>  
  
 <span data-ttu-id="1a3bf-144">**Pour créer un programme de résolution personnalisé Unity**</span><span class="sxs-lookup"><span data-stu-id="1a3bf-144">**To create a custom Unity resolver**</span></span>  
  
1.  <span data-ttu-id="1a3bf-145">(Facultatif) Créer un assembly ou des assemblys avec une classe qui implémente le **IFactProvider** interface et contient un **RegisterFact** méthode qui fournit les informations nécessaires pour la résolution de se produire.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-145">(Optional) Create an assembly or assemblies with a class that implements the **IFactProvider** interface and contains a **RegisterFact** method that provides information necessary for resolution to occur.</span></span>  
  
2.  <span data-ttu-id="1a3bf-146">(Facultatif) Créer un assembly ou des assemblys avec une classe qui implémente le **IFactTranslator** interface et contient un **TranslateFact** méthode qui convertit les faits fournis pour les paires de clé/valeur le dictionnaire de programme de résolution.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-146">(Optional) Create an assembly or assemblies with a class that implements the **IFactTranslator** interface and contains a **TranslateFact** method that translates the provided facts to key/value pairs within the resolver dictionary.</span></span>  
  
3.  <span data-ttu-id="1a3bf-147">Créer un assembly avec une classe qui implémente le **IResolveContainer** et **IResolveProvider** interface et qui contient un **résoudre** méthode valide le configuration du programme de résolution, rassemble tous les faits auprès des fournisseurs de faits, effectue un traitement spécialisé, traduit en utilisant les convertisseurs de faits et retourne les faits traduits sous la forme d’une instance de la **dictionnaire** classe.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-147">Create an assembly with a class that implements the **IResolveContainer** and **IResolveProvider** interface and that contains a **Resolve** method that validates the resolver configuration, gathers all the facts from the fact providers, performs any specialized processing, translates them using the fact translators, and returns the translated facts as an instance of the **Dictionary** class.</span></span>  
  
4.  <span data-ttu-id="1a3bf-148">Enregistrer le programme de résolution en l’ajoutant au fichier de configuration de Esb.config à l’aide un  **\<résolveur >** élément qui contient le moniker racine en tant que le **nom** attribut et qualifié complet nom de l’assembly en tant que le **type** attribut.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-148">Register the resolver by adding it to the Esb.config configuration file using a **\<resolver>** element that contains the root moniker as the **name** attribute and the fully qualified assembly name as the **type** attribute.</span></span>  
  
5.  <span data-ttu-id="1a3bf-149">Ajouter la configuration spécifiques à Unity le fichier Esb.config pour ce programme de résolution.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-149">Add the Unity-specific configuration to the Esb.config file for this resolver.</span></span>  
  
6.  <span data-ttu-id="1a3bf-150">(Facultatif) Créer un schéma qui définit le moniker racine et les paramètres de requête, puis enregistrez-le à l’architecture ESB. Schemas.Resolvers dossier.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-150">(Optional) Create a schema that defines the root moniker and the query parameters, and then save it in the ESB.Schemas.Resolvers folder.</span></span> <span data-ttu-id="1a3bf-151">Le nom doit respecter les conventions d’affectation de noms ESB existantes ; Cela signifie qu’il doit utiliser le nom du moniker racine ajouté avec « _Resolution.xsd ».</span><span class="sxs-lookup"><span data-stu-id="1a3bf-151">The name should follow existing ESB naming conventions; this means it should use the name of the root moniker appended with "_Resolution.xsd".</span></span>  
  
7.  <span data-ttu-id="1a3bf-152">(Facultatif) Générer une classe dans le nouveau schéma et l’enregistrer dans l’assembly du programme de résolution personnalisé.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-152">(Optional) Generate a class from the new schema and save it in the custom resolver assembly.</span></span> <span data-ttu-id="1a3bf-153">Ceci expose des paramètres typés dans le programme de résolution personnalisé.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-153">This will expose typed parameters in the custom resolver.</span></span>  
  
8.  <span data-ttu-id="1a3bf-154">Enregistrer tous les assemblys dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="1a3bf-154">Register all the assemblies in the global assembly cache.</span></span>