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
ms.openlocfilehash: 5f08168e69e26d56cb39fb5c05cc53c3cbb51202
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="creating-a-custom-itinerary-messaging-service"></a>Création d’un Service de messagerie d’itinéraire personnalisé
L’infrastructure d’itinéraire qui fait partie de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] prend en charge l’exécution des étapes d’itinéraire à l’aide des classes implémentant le **IMessagingService** interface qui s’exécutent les services de messagerie d’itinéraire. Vous pouvez implémenter un service de messagerie personnalisé lorsque vous souhaitez que le service doit être chargé pour les éléments suivants :  
  
-   Validation personnalisée des messages configurée dans la feuille de route  
  
-   Transformation de messages personnalisés configurée dans la feuille de route  
  
-   Traitement personnalisé du message  
  
 Dans tous ces cas, un service d’itinéraire personnalisé que vous implémentez agit comme un intercepteur et est appelé par le composant de pipeline de répartiteur.  
  
 Des services d’itinéraire personnalisés en fonction de messagerie ou des services de messagerie, tous les implémenter le **IMessagingService** interface. Cette interface expose le **nom** et **SupportsDisassemble** propriétés et le **Execute** et **ShouldAdvanceStep** méthodes.  
  
 Le **nom** propriété est le nom du service tel qu’il apparaîtra dans un itinéraire. Il doit correspondre au nom configuré dans la configuration des services d’itinéraire dans le fichier Esb.config.  
  
 Le **SupportsDisassemble** propriété indique si le service de messagerie personnalisé que vous créez prend en charge désassembler et l’exécution de plusieurs programmes de résolution.  
  
 Le **ShouldAdvanceStep** méthode accepte l’étape actuelle de l’itinéraire et le message actuel et retourne une valeur booléenne qui indique si le répartiteur doit passer à la feuille de route une fois que le service s’exécute. Dans la plupart des cas, cette méthode doit retourner **true**.  
  
 Le **Execute** méthode revêt une importance plus élevée pour un service de messagerie et contient la logique qui est exécutée au moment de l’exécution. Il accepte dans le contexte du pipeline, le message, la chaîne du programme de résolution et l’étape actuelle de l’itinéraire ; et elle retourne le message mis à jour.  
  
 Implémentation de référence de la **Execute** méthode peut être trouvée dans le fichier RoutingService.cs de l’architecture ESB. Projet Itinerary.Services, comme indiqué dans le code suivant.  
  
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
  
 **Pour implémenter un service personnalisé d’itinéraire pour la messagerie**  
  
1.  Créer un assembly avec une classe qui dérive de **IMessagingService ;** dans les **Execute** méthode, inclure toute la logique nécessaire pour apporter des modifications au message ou le contexte du message (le cas échéant).  
  
2.  Ajouter une entrée dans le **itineraryServices** section du fichier Esb.config pour votre service en ajoutant une  **\<itineraryService\>**  élément avec un GUID en tant que le **id**  d’attribut, le nom du service en tant que le **nom** d’attribut, le nom qualifié complet de la classe en tant que le **type** attribut, **messagerie**en tant que le **étendue** attribut et l’étape autorisée (par exemple, **OnRampReceive**, **OnRampSend**, **OffRampSend**, **OffRampReceive**, **AllSend**, **AllReceive**, ou **tous les**) en tant que le **étape**attribut.  
  
3.  Enregistrer le nouvel assembly dans le global assembly cache.