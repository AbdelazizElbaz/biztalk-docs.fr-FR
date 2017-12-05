---
title: "Création d’un programme de résolution personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2775460-8e04-40be-9557-8278336b031c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57fb0073437c32c8a8f064a4c77f267ee6806858
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="creating-a-custom-resolver"></a><span data-ttu-id="1f7a7-102">Création d’un programme de résolution personnalisé</span><span class="sxs-lookup"><span data-stu-id="1f7a7-102">Creating a Custom Resolver</span></span>
<span data-ttu-id="1f7a7-103">L’implémentation du programme de résolution et l’infrastructure d’adaptateurs fournisseur [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] utilise un composant de pipeline nommé répartiteur et pipelines nommés ItineraryReceive et ItinerarySend.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-103">The Resolver and Adapter Provider Framework implementation in [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] uses a pipeline component named Dispatcher and pipelines named ItineraryReceive and ItinerarySend.</span></span>  
  
 <span data-ttu-id="1f7a7-104">Le composant de pipeline de répartiteur possède quatre propriétés : **Validate, Enabled, point de terminaison,** et **MapName**.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-104">The Dispatcher pipeline component has four properties: **Validate, Enabled, EndPoint,** and **MapName**.</span></span> <span data-ttu-id="1f7a7-105">Le **point de terminaison** propriété peut contenir des chaînes de connexion de programme de résolution avec des valeurs telles que la commande suivante, où **UDDI :\\ \\**  représente le type de résolution à utiliser (la racine moniker).</span><span class="sxs-lookup"><span data-stu-id="1f7a7-105">The **EndPoint** property can contain resolver connection strings with values such as the following, where **UDDI:\\\\** represents the resolution type to use (the root moniker).</span></span>  
  
```  
UDDI:\\serverUrl=http://localhost/uddi;serviceName=OrderPurchaseToOrderPost;serviceProvider=Microsoft.Practices.ESB  
```  
  
 <span data-ttu-id="1f7a7-106">Incluent d’autres prises en charge les monikers **XPATH :\\\\statique :\\\\,** et **BRE :\\\\**.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-106">Other supported monikers include **XPATH:\\\\, STATIC:\\\\,** and **BRE:\\\\**.</span></span> <span data-ttu-id="1f7a7-107">Chaque type de moniker utilise une classe spécifique qui implémente le **IResolveProvider** interface.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-107">Each moniker type uses a specific class that implements the **IResolveProvider** interface.</span></span> <span data-ttu-id="1f7a7-108">Vous pouvez créer vos propres programmes de résolution personnalisés pour d’autres types de moniker et les enregistrer pour une utilisation par le système de résolution dynamique.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-108">You can create your own custom resolvers for other moniker types and register them for use by the dynamic resolution system.</span></span>  
  
 <span data-ttu-id="1f7a7-109">Le moniker équivaut à une chaîne de connexion du programme de résolution.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-109">The moniker equates to a resolver connection string.</span></span> <span data-ttu-id="1f7a7-110">Les schémas individuels définissent les paramètres et leur moniker racine.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-110">Individual schemas define the parameters and their root moniker.</span></span> <span data-ttu-id="1f7a7-111">Un programme de résolution prend le résolveur de chaîne de connexion, il valide et utilise le résultat pour interroger et remplir un **dictionnaire** objet qui peut être utilisé pour le routage de la transformation, la sélection d’itinéraire ou d’autres fins spécifiques à votre service.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-111">A resolver takes the resolver connection string, validates it, and uses the result to query and populate a **Dictionary** object that can be used for routing, transformation, itinerary selection, or some other purpose specific to your service.</span></span>  
  
## <a name="resolver-configuration"></a><span data-ttu-id="1f7a7-112">Configuration du programme de résolution</span><span class="sxs-lookup"><span data-stu-id="1f7a7-112">Resolver Configuration</span></span>  
 <span data-ttu-id="1f7a7-113">Vous devez inscrire tous les programmes de résolution dans le fichier de configuration Esb.config.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-113">You must register all resolvers in the Esb.config configuration file.</span></span> <span data-ttu-id="1f7a7-114">Le code XML suivant montre un exemple du contenu du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-114">The following XML shows an example of the configuration file content.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
     <configSections>  
          <section name="esb" type="Microsoft.Practices.ESB.Configuration.ESBConfigurationSection, Microsoft.Practices.ESB.Configuration, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
          <!-- Other Section Definitions Here -->  
     </configSections>  
  
     <esb>  
          <resolvers cacheManager= "Resolver Providers Cache Manager"  absoluteExpiration="3600">  
               <resolver name="UDDI" type="Microsoft.Practices.ESB.Resolver.UDDI.ResolveProvider, Microsoft.Practices.ESB.Resolver.UDDI, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22">  
                    <resolverConfig>  
                         <add name="cacheTimeoutValue" value="120" />  
                         <add name="cacheName" value="UDDI Cache Manager" />  
                    </resolverConfig>  
               </resolver>  
               <resolver name="XPATH" type="Microsoft.Practices.ESB.Resolver.XPATH.ResolveProvider, Microsoft.Practices.ESB.Resolver.XPATH, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
               <!-- Other Resolver Definitions Here -->  
          </resolvers>  
          <!-- Other ESB Configuration Settings Here -->  
     </esb>  
     <!-- Other Configuration Sections Here -->  
</configuration>  
```  
  
 <span data-ttu-id="1f7a7-115">Le **resolverConfig** section sous chaque nœud du programme de résolution permet de configurer des propriétés supplémentaires pour votre programme de résolution peut nécessiter de fonctionner dans un environnement spécifique.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-115">The **resolverConfig** section under each resolver node allows you to configure additional properties that your resolver may require to operate in a specific environment.</span></span> <span data-ttu-id="1f7a7-116">Pour accéder à la configuration, votre programme de résolution doit exposer un constructeur qui prend un paramètre de type **Microsoft.Practices.ESB.Configuration.Resolver**.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-116">To have access to the configuration, your resolver must expose a constructor that takes in a parameter of type **Microsoft.Practices.ESB.Configuration.Resolver**.</span></span> <span data-ttu-id="1f7a7-117">Dans votre implémentation d’un programme de résolution, propriétés de configuration sont ensuite accessible à l’aide de la **ReadResolverConfigByKey** méthode de la **ResolverConfigHelper** classe ; pour ce faire, passez dans le paramètre initialement passée au constructeur, puis passer le nom de la valeur en question.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-117">In your resolver implementation, configuration properties can then be accessed using the **ReadResolverConfigByKey** method of the **ResolverConfigHelper** class; to do this, pass in the parameter originally passed to the constructor, and then pass in the name of the value in question.</span></span> <span data-ttu-id="1f7a7-118">Si aucune paire nom-valeur n’est spécifiés dans le **resolverConfig** nœud, le constructeur sans paramètre par défaut permet d’instancier votre programme de résolution.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-118">If no name-value pairs are specified in the **resolverConfig** node, the default parameterless constructor will be used to instantiate your resolver.</span></span>  
  
 <span data-ttu-id="1f7a7-119">Deux Universal Description, Discovery and Integration (UDDI) 3 programmes de résolution ont été définies dans la configuration : UDDI 3 et UDDI 3-SOASOFTWARE.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-119">Two Universal Description, Discovery, and Integration (UDDI) 3 resolvers have been defined in the configuration: UDDI 3 and UDDI 3-SOASOFTWARE.</span></span> <span data-ttu-id="1f7a7-120">Les deux de ces programmes de résolution utilisent le même assembly sous-jacent, mais ils fournissent des configurations différentes pour prendre en charge différents registres 3.0 compatible UDDI avec différents formats d’identificateur de ressource uniforme (URI) et des exigences de sécurité.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-120">Both of these resolvers use the same underlying assembly, but they provide different configurations for supporting different UDDI 3.0–compliant registries with different Uniform Resource Identifier (URI) formats and security requirements.</span></span> <span data-ttu-id="1f7a7-121">Si vous avez besoin configurer un moniker supplémentaire pour un Registre compatible 3.0 UDDI en plus de ceux déjà pris en charge, les propriétés suivantes de la configuration peuvent être utilisées :</span><span class="sxs-lookup"><span data-stu-id="1f7a7-121">If you need to configure an additional moniker for a UDDI 3.0–compliant registry besides those already supported, the following configuration properties can be used:</span></span>  
  
-   <span data-ttu-id="1f7a7-122">**cacheTimeoutValue**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-122">**cacheTimeoutValue**</span></span>  
  
-   <span data-ttu-id="1f7a7-123">**nom du cache**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-123">**cacheName**</span></span>  
  
-   <span data-ttu-id="1f7a7-124">**publisherKey**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-124">**publisherKey**</span></span>  
  
-   <span data-ttu-id="1f7a7-125">**useUddiAuth**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-125">**useUddiAuth**</span></span>  
  
-   <span data-ttu-id="1f7a7-126">**baseUri**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-126">**baseUri**</span></span>  
  
-   <span data-ttu-id="1f7a7-127">**inquireUriSuffix**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-127">**inquireUriSuffix**</span></span>  
  
-   <span data-ttu-id="1f7a7-128">**securityUriSuffix**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-128">**securityUriSuffix**</span></span>  
  
-   <span data-ttu-id="1f7a7-129">**securityMode**.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-129">**securityMode**.</span></span> <span data-ttu-id="1f7a7-130">Pour connaître les valeurs valides, consultez l’énumération [System.ServiceModel.BasicHttpSecurityMode](http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409) ([http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409](http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409)).</span><span class="sxs-lookup"><span data-stu-id="1f7a7-130">For valid values, see the enumeration [System.ServiceModel.BasicHttpSecurityMode](http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409) ([http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409](http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409)).</span></span> <span data-ttu-id="1f7a7-131">La valeur par défaut est **TransportCredentialOnly**.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-131">The default value is **TransportCredentialOnly**.</span></span>  
  
-   <span data-ttu-id="1f7a7-132">**credentialType**.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-132">**credentialType**.</span></span> <span data-ttu-id="1f7a7-133">Pour connaître les valeurs valides, consultez l’énumération [System.ServiceModel.HttpClientCredentialType](http://go.microsoft.com/fwlink/?LinkId=188285) ([http://go.microsoft.com/fwlink/?LinkId=188285](http://go.microsoft.com/fwlink/?LinkId=188285)).</span><span class="sxs-lookup"><span data-stu-id="1f7a7-133">For valid values, see the enumeration [System.ServiceModel.HttpClientCredentialType](http://go.microsoft.com/fwlink/?LinkId=188285) ([http://go.microsoft.com/fwlink/?LinkId=188285](http://go.microsoft.com/fwlink/?LinkId=188285)).</span></span> <span data-ttu-id="1f7a7-134">La valeur par défaut est **Windows**.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-134">The default value is **Windows**.</span></span>  
  
-   <span data-ttu-id="1f7a7-135">**nom d’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-135">**username**</span></span>  
  
-   <span data-ttu-id="1f7a7-136">**mot de passe**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-136">**password**</span></span>  
  
 <span data-ttu-id="1f7a7-137">Si vous souhaitez créer un programme de résolution qui s’appuie sur les fonctionnalités d’injection de dépendance du bloc Application Unity, une configuration supplémentaire est requise.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-137">If you want to create a resolver that relies on the dependency injection capabilities of the Unity Application Block, additional configuration is required.</span></span> <span data-ttu-id="1f7a7-138">Pour plus d’informations, consultez [création d’un programme de résolution personnalisé avec un conteneur Unity](../esb-toolkit/creating-a-custom-resolver-with-a-unity-container.md).</span><span class="sxs-lookup"><span data-stu-id="1f7a7-138">For more information, see [Creating a Custom Resolver with a Unity Container](../esb-toolkit/creating-a-custom-resolver-with-a-unity-container.md).</span></span>  
  
## <a name="the-iresolveprovider-interface"></a><span data-ttu-id="1f7a7-139">L’Interface IResolveProvider</span><span class="sxs-lookup"><span data-stu-id="1f7a7-139">The IResolveProvider Interface</span></span>  
 <span data-ttu-id="1f7a7-140">Tous les programmes de résolution doivent implémenter la **IResolveProvider** interface.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-140">All resolvers must implement the **IResolveProvider** interface.</span></span> <span data-ttu-id="1f7a7-141">Le **IResolveProvider** interface, situé dans le projet Microsoft.Practices.ESB.Resolver, se compose de trois surcharges de la **résoudre** méthode qui retourne une instance de la  **Dictionnaire** (classe), qui contient des faits de résolution fournis par l’instance de la classe concrète resolver.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-141">The **IResolveProvider** interface, located in the Microsoft.Practices.ESB.Resolver project, consists of three overloads of the **Resolve** method that return an instance of the **Dictionary** class, which contains resolution facts provided by the instance of concrete resolver class.</span></span> <span data-ttu-id="1f7a7-142">L’exemple de code suivant montre la signature de ces surcharges de méthode.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-142">The following code example shows the signature of these method overloads.</span></span>  
  
```csharp  
// <summary>  
// This is the main interface that is called from the   
// ResolverMgr class.  
// This interface supports being called from a Microsoft BizTalk   
// Server pipeline component.  
// </summary>  
// <param name="config">Configuration string entered into   
// pipeline component as argument</param>  
// <param name="resolver">Moniker representing the resolver   
// to load</param>.  
// <param name="message">IBaseMessage passed from pipeline</param>.  
// <param name="pipelineContext">IPipelineContext passed from   
// pipeline</param>.  
// <returns>Dictionary object fully populated</returns>.  
        Dictionary<string, string> Resolve(string config, string resolver,  
              IBaseMessage message, IPipelineContext pipelineContext);  
  
// <summary>  
// This is the main interface that is called from the ResolverMgr   
// class.  
// This interface supports being called from a Web service interface.  
// </summary>  
// <param name="config">Configuration string entered into Web   
// service as argument</param>.  
// <param name="resolver">Moniker representing the resolver   
// to load</param>.  
// <param name="message">XML document passed from Web   
// service</param>.  
// <returns>Dictionary object fully populated</returns>.  
        Dictionary<string,string> Resolve(string config, string resolver, System.Xml.XmlDocument message);  
  
// <summary>  
// This is the main interface that is called from the   
// ResolverMgr class.  
// This interface supports being called from an orchestration.  
// </summary>  
// <param name="resolverInfo">Configuration string containing   
// configuration and resolver</param>.  
// <param name="message">XLANGMessage passed from   
// orchestration</param>.  
// <returns>Dictionary object fully populated</returns>.  
        Dictionary<string, string> Resolve(ResolverInfo resolverInfo, XLANGs.BaseTypes.XLANGMessage message);  
```  
  
 <span data-ttu-id="1f7a7-143">Le **résolution** structure, situé dans le projet de Microsoft.Practices.ESB.Resolver, définit également les paires nom/valeur stockées dans le **dictionnaire** instance.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-143">The **Resolution** structure, located in Microsoft.Practices.ESB.Resolver project, also defines the name/value pairs stored in the **Dictionary** instance.</span></span> <span data-ttu-id="1f7a7-144">Le **résolution** structure expose plusieurs propriétés ; le tableau suivant répertorie les plus pertinentes.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-144">The **Resolution** structure exposes several properties; the following table lists the most relevant of these.</span></span> <span data-ttu-id="1f7a7-145">Le **CreateResolverDictionary** méthode de la **ResolutionHelper** classe peut être utilisée pour générer un dictionnaire de programme de résolution qui contient les clés plus utilisés, avec des valeurs de chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-145">The **CreateResolverDictionary** method of the **ResolutionHelper** class can be used to generate a resolver dictionary that contains the most used keys, with empty string values.</span></span> <span data-ttu-id="1f7a7-146">Le **dictionnaire** instance prend en charge l’ajout de paires nom/valeur de programme de résolution personnalisé via une implémentation concrète de la **résolveur** classe.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-146">The **Dictionary** instance supports the addition of custom resolver name/value pairs through a concrete implementation of the **Resolver** class.</span></span>  
  
|<span data-ttu-id="1f7a7-147">Propriété</span><span class="sxs-lookup"><span data-stu-id="1f7a7-147">Property</span></span>|<span data-ttu-id="1f7a7-148">Type de données</span><span class="sxs-lookup"><span data-stu-id="1f7a7-148">Data type</span></span>|<span data-ttu-id="1f7a7-149">Type de données</span><span class="sxs-lookup"><span data-stu-id="1f7a7-149">Data type</span></span>|<span data-ttu-id="1f7a7-150">Type de données</span><span class="sxs-lookup"><span data-stu-id="1f7a7-150">Data type</span></span>|  
|--------------|---------------|---------------|---------------|  
|<span data-ttu-id="1f7a7-151">**TransformType**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-151">**TransformType**</span></span>|<span data-ttu-id="1f7a7-152">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-152">String</span></span>|<span data-ttu-id="1f7a7-153">**ActionField**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-153">**ActionField**</span></span>|<span data-ttu-id="1f7a7-154">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-154">String</span></span>|  
|<span data-ttu-id="1f7a7-155">**Réussi**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-155">**Success**</span></span>|<span data-ttu-id="1f7a7-156">Booléen</span><span class="sxs-lookup"><span data-stu-id="1f7a7-156">Boolean</span></span>|<span data-ttu-id="1f7a7-157">**EpmRRCorrelationTokenField**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-157">**EpmRRCorrelationTokenField**</span></span>|<span data-ttu-id="1f7a7-158">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-158">String</span></span>|  
|<span data-ttu-id="1f7a7-159">**TransportNamespace**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-159">**TransportNamespace**</span></span>|<span data-ttu-id="1f7a7-160">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-160">String</span></span>|<span data-ttu-id="1f7a7-161">**InboundTransportLocationField**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-161">**InboundTransportLocationField**</span></span>|<span data-ttu-id="1f7a7-162">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-162">String</span></span>|  
|<span data-ttu-id="1f7a7-163">**TransportType**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-163">**TransportType**</span></span>|<span data-ttu-id="1f7a7-164">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-164">String</span></span>|<span data-ttu-id="1f7a7-165">**InterchangeIDField**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-165">**InterchangeIDField**</span></span>|<span data-ttu-id="1f7a7-166">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-166">String</span></span>|  
|<span data-ttu-id="1f7a7-167">**TransportLocation**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-167">**TransportLocation**</span></span>|<span data-ttu-id="1f7a7-168">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-168">String</span></span>|<span data-ttu-id="1f7a7-169">**ReceiveLocationNameField**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-169">**ReceiveLocationNameField**</span></span>|<span data-ttu-id="1f7a7-170">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-170">String</span></span>|  
|<span data-ttu-id="1f7a7-171">**Action**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-171">**Action**</span></span>|<span data-ttu-id="1f7a7-172">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-172">String</span></span>|<span data-ttu-id="1f7a7-173">**ReceivePortNameField**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-173">**ReceivePortNameField**</span></span>|<span data-ttu-id="1f7a7-174">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-174">String</span></span>|  
|<span data-ttu-id="1f7a7-175">**MessageExchangePattern**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-175">**MessageExchangePattern**</span></span>|<span data-ttu-id="1f7a7-176">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-176">String</span></span>|<span data-ttu-id="1f7a7-177">**InboundTransportTypeField**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-177">**InboundTransportTypeField**</span></span>|<span data-ttu-id="1f7a7-178">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-178">String</span></span>|  
|<span data-ttu-id="1f7a7-179">**EndpointConfig**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-179">**EndpointConfig**</span></span>|<span data-ttu-id="1f7a7-180">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-180">String</span></span>|<span data-ttu-id="1f7a7-181">**IsRequestResponseField**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-181">**IsRequestResponseField**</span></span>|<span data-ttu-id="1f7a7-182">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-182">String</span></span>|  
|<span data-ttu-id="1f7a7-183">**TargetNamespace**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-183">**TargetNamespace**</span></span>|<span data-ttu-id="1f7a7-184">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-184">String</span></span>|<span data-ttu-id="1f7a7-185">**DocumentSpecStrongNameField**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-185">**DocumentSpecStrongNameField**</span></span>|<span data-ttu-id="1f7a7-186">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-186">String</span></span>|  
|<span data-ttu-id="1f7a7-187">**FixJaxRPC**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-187">**FixJaxRPC**</span></span>|<span data-ttu-id="1f7a7-188">Booléen</span><span class="sxs-lookup"><span data-stu-id="1f7a7-188">Boolean</span></span>|<span data-ttu-id="1f7a7-189">**DocumentSpecNameField**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-189">**DocumentSpecNameField**</span></span>|<span data-ttu-id="1f7a7-190">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-190">String</span></span>|  
|<span data-ttu-id="1f7a7-191">**WindowUserField**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-191">**WindowUserField**</span></span>|<span data-ttu-id="1f7a7-192">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-192">String</span></span>|<span data-ttu-id="1f7a7-193">**MessageType**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-193">**MessageType**</span></span>|<span data-ttu-id="1f7a7-194">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-194">String</span></span>|  
|<span data-ttu-id="1f7a7-195">**CacheTimeout**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-195">**CacheTimeout**</span></span>|<span data-ttu-id="1f7a7-196">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-196">String</span></span>|<span data-ttu-id="1f7a7-197">**OutboundTransportCLSID**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-197">**OutboundTransportCLSID**</span></span>|<span data-ttu-id="1f7a7-198">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-198">String</span></span>|  
|<span data-ttu-id="1f7a7-199">**MethodNameField**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-199">**MethodNameField**</span></span>|<span data-ttu-id="1f7a7-200">Chaîne</span><span class="sxs-lookup"><span data-stu-id="1f7a7-200">String</span></span>|||  
  
## <a name="creating-a-custom-resolver"></a><span data-ttu-id="1f7a7-201">Création d’un programme de résolution personnalisé</span><span class="sxs-lookup"><span data-stu-id="1f7a7-201">Creating a Custom Resolver</span></span>  
 <span data-ttu-id="1f7a7-202">Au moment de l’exécution, un pipeline extrait la chaîne de connexion du programme de résolution et appelle le programme de résolution manager (une instance de la **ResolverMgr** classe).</span><span class="sxs-lookup"><span data-stu-id="1f7a7-202">At run time, a pipeline retrieves the resolver connection string and calls the resolver manager (an instance of the **ResolverMgr** class).</span></span> <span data-ttu-id="1f7a7-203">Le Gestionnaire de programme de résolution analyse remplit et valide la chaîne de connexion du programme de résolution.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-203">The resolver manager parses, populates, and validates the resolver connection string.</span></span> <span data-ttu-id="1f7a7-204">Pour cela, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="1f7a7-204">It does this by doing the following:</span></span>  
  
-   <span data-ttu-id="1f7a7-205">Il analyse la chaîne de connexion afin de déterminer les **résolveur** type à charger.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-205">It parses the connection string to determine which **Resolver** type to load.</span></span>  
  
-   <span data-ttu-id="1f7a7-206">Elle correspond à ce type en un moniker défini dans le fichier de configuration (la clé est le moniker racine, tel que UDDI).</span><span class="sxs-lookup"><span data-stu-id="1f7a7-206">It matches this type to a moniker defined in the configuration file (the key is the root moniker, such as UDDI).</span></span>  
  
-   <span data-ttu-id="1f7a7-207">Il lit le nom de l’assembly du programme de résolution de ce moniker.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-207">It reads the assembly name of the resolver for this moniker.</span></span>  
  
-   <span data-ttu-id="1f7a7-208">Il charge l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-208">It loads the specified assembly.</span></span>  
  
 <span data-ttu-id="1f7a7-209">Le mécanisme de résolution dynamique met en cache chargé de toutes les implémentations de la **IResolveProvider** interface afin d’éviter les répétées de la lecture des informations de configuration et l’assembly à charger lorsque plusieurs messages entrants utilisent le même programme de résolution.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-209">The dynamic resolution mechanism caches all loaded implementations of the **IResolveProvider** interface to avoid repeated reading of configuration information and assembly loading when several incoming messages use the same resolver.</span></span>  
  
 <span data-ttu-id="1f7a7-210">Enfin, le Gestionnaire de programme de résolution s’exécute le **résoudre** méthode le concrète **IResolveProvider** mise en œuvre et retourne rempli **dictionnaire** instance.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-210">Finally, the resolver manager executes the **Resolve** method of the concrete **IResolveProvider** implementation and returns the populated **Dictionary** instance.</span></span>  
  
 <span data-ttu-id="1f7a7-211">**Pour créer un programme de résolution personnalisé**</span><span class="sxs-lookup"><span data-stu-id="1f7a7-211">**To create a custom resolver**</span></span>  
  
1.  <span data-ttu-id="1f7a7-212">Créer un assembly avec une classe qui implémente le **IResolveProvider** interface et contient un **résoudre** méthode qui retourne les faits de programme de résolution comme une instance de la **dictionnaire**classe.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-212">Create an assembly with a class that implements the **IResolveProvider** interface and contains a **Resolve** method that returns resolver facts as an instance of the **Dictionary** class.</span></span>  
  
2.  <span data-ttu-id="1f7a7-213">Enregistrer le programme de résolution en l’ajoutant au fichier de configuration de Esb.config à l’aide un  **\<programme de résolution\>**  élément qui contient le moniker racine en tant que le **nom** attribut et entièrement nom d’assembly qualifié en tant que le **type** attribut.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-213">Register the resolver by adding it to the Esb.config configuration file using a **\<resolver\>** element that contains the root moniker as the **name** attribute and the fully qualified assembly name as the **type** attribute.</span></span>  
  
3.  <span data-ttu-id="1f7a7-214">(Facultatif) Créer un schéma qui définit le moniker racine et les paramètres de requête, puis enregistrez-le à l’architecture ESB. Schemas.Resolvers dossier.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-214">(Optional) Create a schema that defines the root moniker and the query parameters, and then save it in the ESB.Schemas.Resolvers folder.</span></span> <span data-ttu-id="1f7a7-215">Le nom doit respecter les conventions d’affectation de noms ESB existantes ; Cela signifie qu’il doit utiliser le nom du moniker racine ajouté avec « _Resolution.xsd ».</span><span class="sxs-lookup"><span data-stu-id="1f7a7-215">The name should follow existing ESB naming conventions; this means it should use the name of the root moniker appended with "_Resolution.xsd".</span></span>  
  
4.  <span data-ttu-id="1f7a7-216">(Facultatif) Générer une classe dans le nouveau schéma et l’enregistrer dans l’assembly du programme de résolution personnalisé.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-216">(Optional) Generate a class from the new schema and save it in the custom resolver assembly.</span></span> <span data-ttu-id="1f7a7-217">Cela expose des paramètres typés dans le programme de résolution personnalisé.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-217">This exposes typed parameters in the custom resolver.</span></span>  
  
5.  <span data-ttu-id="1f7a7-218">Enregistrer le nouvel assembly dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="1f7a7-218">Register the new assembly in the global assembly cache.</span></span>