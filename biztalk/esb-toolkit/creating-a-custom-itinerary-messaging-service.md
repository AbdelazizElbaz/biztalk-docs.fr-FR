---
title: "Création d’un Service de messagerie d’itinéraire personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2de44c21-68ca-4cf1-a117-bcb35af1b4a9
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bcf96e8f76a9d2a6ad51bac462c2da101812911d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-custom-itinerary-messaging-service"></a><span data-ttu-id="a96ea-102">Création d’un Service de messagerie d’itinéraire personnalisé</span><span class="sxs-lookup"><span data-stu-id="a96ea-102">Creating a Custom Itinerary Messaging Service</span></span>
<span data-ttu-id="a96ea-103">L’infrastructure d’itinéraire qui fait partie de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] prend en charge l’exécution des étapes d’itinéraire à l’aide des classes implémentant le **IMessagingService** interface qui s’exécutent les services de messagerie d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="a96ea-103">The itinerary framework that is part of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] supports execution of itinerary steps using classes implementing the **IMessagingService** interface that execute itinerary messaging services.</span></span> <span data-ttu-id="a96ea-104">Vous pouvez implémenter un service de messagerie personnalisé lorsque vous souhaitez que le service doit être chargé pour les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="a96ea-104">You can implement a custom messaging service when you want the service to be responsible for the following:</span></span>  
  
-   <span data-ttu-id="a96ea-105">Validation personnalisée des messages configurée dans la feuille de route</span><span class="sxs-lookup"><span data-stu-id="a96ea-105">Custom message validation configured in the itinerary</span></span>  
  
-   <span data-ttu-id="a96ea-106">Transformation de messages personnalisés configurée dans la feuille de route</span><span class="sxs-lookup"><span data-stu-id="a96ea-106">Custom message transformation configured in the itinerary</span></span>  
  
-   <span data-ttu-id="a96ea-107">Traitement personnalisé du message</span><span class="sxs-lookup"><span data-stu-id="a96ea-107">Custom processing of the message</span></span>  
  
 <span data-ttu-id="a96ea-108">Dans tous ces cas, un service d’itinéraire personnalisé que vous implémentez agit comme un intercepteur et est appelé par le composant de pipeline de répartiteur.</span><span class="sxs-lookup"><span data-stu-id="a96ea-108">In all these cases, a custom itinerary service that you implement acts as an interceptor and is called by the Dispatcher pipeline component.</span></span>  
  
 <span data-ttu-id="a96ea-109">Des services d’itinéraire personnalisés en fonction de messagerie ou des services de messagerie, tous les implémenter le **IMessagingService** interface.</span><span class="sxs-lookup"><span data-stu-id="a96ea-109">Custom messaging-based itinerary services, or messaging services, all implement the **IMessagingService** interface.</span></span> <span data-ttu-id="a96ea-110">Cette interface expose le **nom** et **SupportsDisassemble** propriétés et le **Execute** et **ShouldAdvanceStep** méthodes.</span><span class="sxs-lookup"><span data-stu-id="a96ea-110">This interface exposes the **Name** and **SupportsDisassemble** properties and the **Execute** and **ShouldAdvanceStep** methods.</span></span>  
  
 <span data-ttu-id="a96ea-111">Le **nom** propriété est le nom du service tel qu’il apparaîtra dans un itinéraire.</span><span class="sxs-lookup"><span data-stu-id="a96ea-111">The **Name** property is the name of the service as it will appear in an itinerary.</span></span> <span data-ttu-id="a96ea-112">Il doit correspondre au nom configuré dans la configuration des services d’itinéraire dans le fichier Esb.config.</span><span class="sxs-lookup"><span data-stu-id="a96ea-112">It must match the configured name in the itinerary services configuration in the Esb.config file.</span></span>  
  
 <span data-ttu-id="a96ea-113">Le **SupportsDisassemble** propriété indique si le service de messagerie personnalisé que vous créez prend en charge désassembler et l’exécution de plusieurs programmes de résolution.</span><span class="sxs-lookup"><span data-stu-id="a96ea-113">The **SupportsDisassemble** property indicates whether the custom messaging service you are creating supports disassemble and the execution of multiple resolvers.</span></span>  
  
 <span data-ttu-id="a96ea-114">Le **ShouldAdvanceStep** méthode accepte l’étape actuelle de l’itinéraire et le message actuel et retourne une valeur booléenne qui indique si le répartiteur doit passer à la feuille de route une fois que le service s’exécute.</span><span class="sxs-lookup"><span data-stu-id="a96ea-114">The **ShouldAdvanceStep** method takes in the current itinerary step, and the current message, and returns a Boolean value that indicates whether the dispatcher should advance the itinerary after the service executes.</span></span> <span data-ttu-id="a96ea-115">Dans la plupart des cas, cette méthode doit retourner **true**.</span><span class="sxs-lookup"><span data-stu-id="a96ea-115">In almost all cases, this method should return **true**.</span></span>  
  
 <span data-ttu-id="a96ea-116">Le **Execute** méthode revêt une importance plus élevée pour un service de messagerie et contient la logique qui est exécutée au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a96ea-116">The **Execute** method is of greatest importance for a messaging service and contains the logic that will be executed at run time.</span></span> <span data-ttu-id="a96ea-117">Il accepte dans le contexte du pipeline, le message, la chaîne du programme de résolution et l’étape actuelle de l’itinéraire ; et elle retourne le message mis à jour.</span><span class="sxs-lookup"><span data-stu-id="a96ea-117">It takes in the pipeline context, the message, the resolver string, and the current itinerary step; and it returns the updated message.</span></span>  
  
 <span data-ttu-id="a96ea-118">Implémentation de référence de la **Execute** méthode peut être trouvée dans le fichier RoutingService.cs de l’architecture ESB. Projet Itinerary.Services, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="a96ea-118">A reference implementation of the **Execute** method can be found in the RoutingService.cs file of the ESB.Itinerary.Services project, as shown in the following code.</span></span>  
  
```csharp  
public IBaseMessage ExecuteRoute(IPipelineContext context, IBaseMessage msg, string resolverString)  
        {  
            if (context == null)  
                throw new ArgumentNullException("context");  
            if (msg == null)  
                throw new ArgumentNullException("msg");  
            if (string.IsNullOrEmpty(resolverString))  
                throw new ArgumentException(Properties.Resources.ArgumentStringRequired, "resolverString");  
            try  
            {  
                ResolverInfo info = ResolverMgr.GetResolverInfo(ResolutionType.Endpoint, resolverString);  
                if (!info.Success)  
                    throw new RoutingException(Properties.Resources.ResolverStringInvalid, resolverString);  
  
                // Resolve configuration for routing.  
                Dictionary<string, string> resolverDictionary = ResolverMgr.Resolve(info, msg, context);  
  
                if (string.IsNullOrEmpty(resolverDictionary["Resolver.TransportLocation"]))  
                    throw new RoutingException(Properties.Resources.TransportLocationNotResolved, resolverString);  
  
                AdapterMgr.SetEndpoint(resolverDictionary, msg.Context);  
  
                return msg;  
            }  
            catch (System.Exception ex)  
            {  
                EventLogger.Write(MethodInfo.GetCurrentMethod(), ex);  
                throw;  
            }        
        }  
```  
  
 <span data-ttu-id="a96ea-119">**Pour implémenter un service personnalisé d’itinéraire pour la messagerie**</span><span class="sxs-lookup"><span data-stu-id="a96ea-119">**To implement a custom itinerary service for messaging**</span></span>  
  
1.  <span data-ttu-id="a96ea-120">Créer un assembly avec une classe qui dérive de **IMessagingService ;** dans les **Execute** méthode, inclure toute la logique nécessaire pour apporter des modifications au message ou le contexte du message (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="a96ea-120">Create an assembly with a class that derives from **IMessagingService;** in the **Execute** method, include all logic necessary to make modifications to the message or the message context (if any).</span></span>  
  
2.  <span data-ttu-id="a96ea-121">Ajouter une entrée dans le **itineraryServices** section du fichier Esb.config pour votre service en ajoutant une  **\<itineraryService >** élément avec un GUID en tant que le **id**d’attribut, le nom du service en tant que le **nom** d’attribut, le nom qualifié complet de la classe en tant que le **type** attribut, **messagerie** comme le **étendue** attribut et l’étape autorisée (par exemple, **OnRampReceive**, **OnRampSend**, **OffRampSend**, **OffRampReceive**, **AllSend**, **AllReceive**, ou **tous les**) en tant que le **étape** attribut.</span><span class="sxs-lookup"><span data-stu-id="a96ea-121">Add an entry in the **itineraryServices** section of the Esb.config file for your service by adding an **\<itineraryService>** element with a GUID as the **id** attribute, the name of the service as the **name** attribute, the fully qualified name of the class as the **type** attribute, **Messaging** as the **scope** attribute, and the allowed stage (for example, **OnRampReceive**, **OnRampSend**, **OffRampSend**, **OffRampReceive**, **AllSend**, **AllReceive**, or **All**) as the **stage** attribute.</span></span>  
  
3.  <span data-ttu-id="a96ea-122">Enregistrer le nouvel assembly dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="a96ea-122">Register the new assembly in the global assembly cache.</span></span>