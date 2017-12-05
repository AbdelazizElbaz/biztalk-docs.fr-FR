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
ms.openlocfilehash: ef4a96542bcf2a7deae4911c6ee81fa846d0766f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="creating-a-custom-resolver-with-a-unity-container"></a>Création d’un programme de résolution personnalisé avec un conteneur Unity
Vous pouvez créer un programme de résolution personnalisé à l’aide de la [bloc d’Application Unity](http://go.microsoft.com/fwlink/?LinkId=188286) (Unity) ([http://go.microsoft.com/fwlink/?LinkId=188286](http://go.microsoft.com/fwlink/?LinkId=188286)) pour l’injection de dépendance d’exécution des sources de logique et les métadonnées de résolution.
  
 **Fournisseurs de faits**  
  
 Les fournisseurs de faits sont des instances de classes qui implémentent la **IFactProvider** interface. Cette interface expose trois différentes surcharges d’une méthode nommée **RegisterFact**. Cette méthode accepte dans le message, la configuration du programme de résolution et, dans certains cas, le contexte du pipeline et retourne un objet. Cet objet peut avoir des informations extraites à partir des entrées d’une certaine façon, il peut être un calcul d’une forme ou il peut être recherché à partir d’une source externe. Chaque objet retourné par un fournisseur de faits peut être référencé en tant que fait et est en principe ajouté à une liste par le conteneur de résolution pour une utilisation ultérieure par un traducteur de faits.  
  
 Un programme de résolution Unity peut avoir zéro ou plusieurs fournisseurs de faits qui peuvent être ajoutés ou supprimés à tout moment d’un changement de configuration unique.  
  
 Le code suivant est un exemple de la logique contenue dans un fournisseur de faits. Ce code peut également être trouvé dans le fichier ItineraryStaticFactProvider.cs de l’architecture ESB. Resolver.Itinerary.Facts projet. C’est un composant dans le programme de résolution d’itinéraire statique qui regroupe le nom et la version d’un itinéraire à partir de la chaîne de connexion du programme de résolution.  
  
```csharp  
public object RegisterFact(IBaseMessage message, IPipelineContext pipelineContext, Dictionary\<string, string\> resolverContents)  
{  
    return GetItineraryFactFromResolver(resolverContents);  
}  
  
private static object GetItineraryFactFromResolver(Dictionary\<string, string\> resolverContents)  
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
  
 **Convertisseurs de faits**  
  
 Convertisseurs de faits sont des instances de classes qui implémentent la **IFactTranslator** interface. Cette interface expose une méthode unique nommée **TranslateFact**. Cette méthode prend dans un tableau d’objets qui contient une liste des faits et le dictionnaire de programme de résolution qui n’est plus tard renvoyé par le programme de résolution à l’aide du traducteur de faits. Un convertisseur de faits est chargé de traiter les faits fournis par les fournisseurs de faits d’une manière explicite, puis en remplissant le dictionnaire de programme de résolution.  
  
 Un programme de résolution Unity peut avoir zéro ou plusieurs traducteurs de faits qui peuvent être ajoutés ou supprimés à tout moment d’un changement de configuration unique.  
  
 Le code suivant est un exemple de la logique contenue dans un convertisseur de faits. Ce code peut également être trouvé dans le fichier ItineraryStaticFactTranslator.cs de l’architecture ESB. Resolver.Itinerary.Facts projet. C’est un composant dans le programme de résolution d’itinéraire statique qui effectue une requête de base de données pour recueillir l’itinéraire XML pour un itinéraire par nom et, éventuellement, par version.  
  
```csharp  
public void TranslateFact(object[] facts, Dictionary\<string, string\> factDictionary)  
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
  
 **Résoudre les conteneurs**  
  
 Un conteneur de résolution est une classe qui implémente le **IResolveContainer** interface. En règle générale, il implémente également la **IResolveProvider** interface. Le **IResolveContainer** interface expose une méthode unique nommée **initialiser** qui accepte un **IUnityContainer**. Le conteneur passé à cette méthode contiendra toutes les dépendances (autrement dit, les instances des classes **IFactProvider** et **IFactTranslator**et tous les autres types requis) nécessaires pour le programme de résolution pour terminer son traitement.  
  
 Le code suivant est un exemple d’implémentation de la **IResolveContainer** interface. Ce code peut également être trouvé dans le fichier StaticItineraryResolveContainer.cs de l’architecture ESB. Resolver.Itinerary projet.  
  
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
  
 Dans un conteneur de résolution, dans les implémentations de la **résoudre** méthodes à partir de la **IResolveProvider** interface, il n’est nécessaire pour une itération au sein de tous les fournisseurs de faits et les convertisseurs de faits de l’unité conteneur pour permettre à chacun d’eux pour effectuer leur traitement.  
  
 Le code suivant est un exemple de la logique contenue dans un conteneur de résolution. Ce code peut également être trouvé dans le fichier StaticItineraryResolveContainer.cs de l’architecture ESB. Resolver.Itinerary projet.  
  
```csharp  
public Dictionary\<string, string\> Resolve(ResolverInfo resolverInfo,  
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
  
private Dictionary\<string, string\> ResolveStatic(string config, string resolver,   
    Func<IFactProvider, Dictionary\<string, string\>, object> RegisterFact)  
{  
    try  
    {  
        EventLogger.Write(string.Format("Received {0} value in ITINERARY STATIC resolver.", config));  
  
        Dictionary\<string, string\> queryParams =  
                ResolverMgr.GetFacts(config, resolver);  
  
        List<object> facts = new List<object>();  
  
        foreach (IFactProvider factProvider in Container.ResolveAll<IFactProvider>())  
        {  
            facts.Add(RegisterFact(factProvider, queryParams));  
        }  
  
        Dictionary\<string, string\> resolverDictionary = new Dictionary\<string, string\>();  
  
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
  
 **Configuration d’un programme de résolution personnalisé Unity**  
  
 Pour configurer un programme de résolution personnalisé Unity, les mêmes étapes de configuration s’appliquent lors de la création d’un programme de résolution personnalisé ; Toutefois, il est une configuration supplémentaire qui doit être incluse pour enregistrer correctement les composants qui composent le programme de résolution.  
  
 Tout d’abord, dans le fichier Esb.config, sous la déclaration de programme de résolution, un **resolverConfig** nœud doit être ajouté avec les deux propriétés suivantes :  
  
-   **unitySectionName**. Cette propriété contient le nom de la section de configuration dans le fichier de configuration qui contient la configuration pour le bloc d’Application Unity ; par défaut, la valeur de cette propriété est **esb.resolver**.  
  
-   **unityContainerName**. Cette propriété contient le nom du conteneur Unity défini dans la configuration de Unity spécifique à votre programme de résolution personnalisé.  
  
 Le code XML suivant est un exemple de la configuration nécessaire dans les **résolveurs** nœud.  
  
```xml  
<resolver name="ITINERARY-STATIC" type="Microsoft.Practices.ESB.Resolver.Unity.ResolveProvider, Microsoft.Practices.ESB.Resolver.Unity, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22">  
     <resolverConfig>  
          <add name="unitySectionName" value="esb.resolver" />  
          <add name="unityContainerName" value="ITINERARY" />  
     </resolverConfig>  
</resolver>  
```  
  
 Le code XML suivant est un exemple de la configuration nécessaire sous la **esb.resolver** nœud.  
  
```xml  
<typeAliases>  
     <!-- Lifetime manager types -->  
     <typeAlias alias="singleton" type="Microsoft.Practices.Unity.ContainerControlledLifetimeManager, Microsoft.Practices.Unity, Version=1.2.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
     <!-- std type providers -->  
     <typeAlias alias="string" type="System.String, mscorlib"/>  
     <typeAlias alias="int" type="System.Int32, mscorlib"/>  
     <!-- repository providers -->  
     <typeAlias alias="IRepositoryProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.Facts.Repository.IRepositoryProvider, Microsoft.Practices.ESB.Resolver.Itinerary.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="SqlRepositoryProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.DataAccess.SqlRepositoryProvider, Microsoft.Practices.ESB.Resolver.Itinerary.DataAccess, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <!-- fact providers -->  
     <typeAlias alias="IFactProvider" type="Microsoft.Practices.ESB.Resolver.Facts.IFactProvider, Microsoft.Practices.ESB.Resolver.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="IFactTranslator" type="Microsoft.Practices.ESB.Resolver.Facts.IFactTranslator, Microsoft.Practices.ESB.Resolver.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="ItineraryFactProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.Facts.ItineraryFactProvider, Microsoft.Practices.ESB.Resolver.Itinerary.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="ItineraryStaticFactProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.Facts.ItineraryStaticFactProvider, Microsoft.Practices.ESB.Resolver.Itinerary.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="ItineraryHeaderFactProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.Facts.ItineraryHeaderFactProvider, Microsoft.Practices.ESB.Resolver.Itinerary.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="ResolutionFactProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.Facts.ResolutionFactProvider, Microsoft.Practices.ESB.Resolver.Itinerary.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="DefaultFactTranslator" type="Microsoft.Practices.ESB.Resolver.Facts.DefaultFactTranslator, Microsoft.Practices.ESB.Resolver.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="ItineraryFactTranslator" type="Microsoft.Practices.ESB.Resolver.Itinerary.Facts.ItineraryFactTranslator, Microsoft.Practices.ESB.Resolver.Itinerary.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <!-- resolve providers -->  
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
  
 Pour plus d’informations sur la configuration est nécessaire dans le **esb.resolvers** nœud, consultez [schéma Source pour le bloc d’Application Unity](http://go.microsoft.com/fwlink/?LinkId=188288) ([http://go.microsoft.com/fwlink/ ? LinkId = 188288](http://go.microsoft.com/fwlink/?LinkId=188288)) sur MSDN.  
  
 **Création d’un programme de résolution personnalisé Unity**  
  
 **Pour créer un programme de résolution personnalisé Unity**  
  
1.  (Facultatif) Créer un assembly ou des assemblys avec une classe qui implémente le **IFactProvider** interface et contient un **RegisterFact** méthode qui fournit les informations nécessaires pour la résolution de se produire.  
  
2.  (Facultatif) Créer un assembly ou des assemblys avec une classe qui implémente le **IFactTranslator** interface et contient un **TranslateFact** méthode qui convertit les faits fournis pour les paires de clé/valeur le dictionnaire de programme de résolution.  
  
3.  Créer un assembly avec une classe qui implémente le **IResolveContainer** et **IResolveProvider** interface et qui contient un **résoudre** méthode valide le configuration du programme de résolution, rassemble tous les faits auprès des fournisseurs de faits, effectue un traitement spécialisé, traduit en utilisant les convertisseurs de faits et retourne les faits traduits sous la forme d’une instance de la **dictionnaire** classe.  
  
4.  Enregistrer le programme de résolution en l’ajoutant au fichier de configuration de Esb.config à l’aide un  **\<programme de résolution\>**  élément qui contient le moniker racine en tant que le **nom** attribut et entièrement nom d’assembly qualifié en tant que le **type** attribut.  
  
5.  Ajouter la configuration spécifiques à Unity le fichier Esb.config pour ce programme de résolution.  
  
6.  (Facultatif) Créer un schéma qui définit le moniker racine et les paramètres de requête, puis enregistrez-le à l’architecture ESB. Schemas.Resolvers dossier. Le nom doit respecter les conventions d’affectation de noms ESB existantes ; Cela signifie qu’il doit utiliser le nom du moniker racine ajouté avec « _Resolution.xsd ».  
  
7.  (Facultatif) Générer une classe dans le nouveau schéma et l’enregistrer dans l’assembly du programme de résolution personnalisé. Ceci expose des paramètres typés dans le programme de résolution personnalisé.  
  
8.  Enregistrer tous les assemblys dans le global assembly cache.