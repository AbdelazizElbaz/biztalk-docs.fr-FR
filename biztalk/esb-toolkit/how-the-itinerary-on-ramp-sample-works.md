---
title: "Fonctionne de l’exemple de rampe d’entrée d’itinéraire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f4f318c-b955-4a3d-88db-c0d324b63b21
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b73b4379944db548a30898403239ffcf9704791a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-the-itinerary-on-ramp-sample-works"></a>Fonctionne de l’exemple de rampe d’entrée d’itinéraire
L’application génère un ensemble d’en-têtes SOAP qui contiennent l’itinéraire que vous créez à l’aide des contrôles dans la fenêtre d’application client, le Client Test itinéraire exemple charge le fichier de message spécifié à partir du disque, ajoute les en-têtes d’itinéraire pour le message, et envoie à l’architecture ESB via un itinéraire rampe d’entrée pour le traitement. Si l’itinéraire génère une réponse, l’application récupère la réponse et l’affiche dans la fenêtre d’application.  
  
 Vous pouvez choisir parmi plusieurs exemples de fichiers de configuration d’itinéraire pour voir les scénarios unidirectionnels et bidirectionnels qui utilisent des orchestrations, messagerie ou une combinaison des deux.  
  
 Pour vous aider à comprendre comment le service de l’itinéraire utilise les informations d’itinéraire dans un message, le code XML suivant montre l’exemple de fichier de configuration d’itinéraire nommé TwoWay (bidirectionnel)-OrchTransform-OrchRoutingGroup-OrchTwoWayCustom.xml utilisé dans l’exemple précédent. La première section de cet itinéraire spécifie trois étapes d’appel de service.  
  
```xml  
<Itinerary xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" uuid="" beginTime="" completeTime="" state="Pending" isRequestResponse="false" servicecount="0" xmlns="http://schemas.microsoft.biztalk.practices.esb.com/itinerary">  
  <BizTalkSegment interchangeId="" epmRRCorrelationToken="" receiveInstanceId="" messageId="" xmlns="" />  
  <ServiceInstance name="Microsoft.Practices.ESB.Services.Transform" type="Orchestration" state="Pending" position="0" isRequestResponse="false" xmlns="" />  
  <Services xmlns="">  
    <Service uuid="92d3b293-e6d4-44a1-b27d-c42b48aec667" beginTime="" completeTime="" name="Microsoft.Practices.ESB.Services.Transform" type="Orchestration" state="Pending" isRequestResponse="false" position="0" serviceInstanceId="" />  
  </Services>  
  <Services xmlns="">  
    <Service uuid="774488bc-e5b9-4a4e-9ae7-d25cdf23fd1c" beginTime="" completeTime="" name="Microsoft.Practices.ESB.Services.Routing" type="Orchestration" state="Pending" isRequestResponse="false" position="1" serviceInstanceId="" />  
  </Services>  
  <Services xmlns="">  
    <Service uuid="" beginTime="" completeTime="" name="ProcessAndRespond" type="Orchestration" state="Pending" isRequestResponse="true" position="2" serviceInstanceId="" />  
  </Services>  
  ...  
```  
  
 Suivant la liste des étapes d’appel de service dans l’itinéraire correspond à la section contenant les détails des programmes de résolution (représentés par les chaînes de connexion) qui permettent au service de l’itinéraire rechercher ou fournir des informations de résolution pour chaque service défini dans le feuille de route.  
  
```xml  
  ...  
<ResolverGroups xmlns="">  
    <Resolvers serviceId="Microsoft.Practices.ESB.Services.Transform0"><![CDATA[BRE:\\Policy=ResolveMap;Version=1.0;UseMsg=False;]]></Resolvers>  
    <Resolvers serviceId="Microsoft.Practices.ESB.Services.Routing1"><![CDATA[STATIC:\\TransportType=FILE;TransportLocation=C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\OUt\%MessageID%.xml;Action=;EndpointConfig=;JaxRpcResponse=False;MessageExchangePattern=;TargetNamespace=;TransformType=;]]><![CDATA[UDDI3:\\ServerUrl=http://localhost/uddi;SearchQualifiers=andAllKeys;CategorySearch=;BindingKey=uddi:esb:orderfileservicev3.1;]]></Resolvers>  
    <Resolvers serviceId="ProcessAndRespond2" />  
  </ResolverGroups>  
</Itinerary>  
```  
  
> [!NOTE]
>  Le contenu réel de chaque  **\<résolveurs\>**  élément ne contient pas les caractères d’espace blanc utilisés pour encapsuler les lignes dans la liste précédente.  
  
 Voici les trois étapes définies dans la configuration précédente d’itinéraire :  
  
1.  Exécutez l’orchestration Microsoft.Practices.ESB.Services.Transform pour transformer le message avec la stratégie de ResolverMap à l’aide du moteur de règles d’entreprise (BRE) BizTalk.  
  
2.  Exécutez l’orchestration Microsoft.Practices.ESB.Services.Routing pour acheminer le message transformé à plusieurs emplacements à l’aide de la Microsoft.Practices.ESB.Services.Routing1 de routage. Le  **\<ResolverGroups\>**  section contient un  **\<résolveurs\>**  élément avec cet identificateur, qui définit les chaînes de connexion.  
  
3.  Exécutez l’orchestration ProcessAndRespond fournie avec cet exemple. L’implémentation de cette orchestration envoie une copie du message de demande en tant que la réponse au client de Test d’itinéraire.  
  
 À la fin de chaque service, le service avance l’itinéraire et promeut le prochain service défini dans l’itinéraire à l’instance de service en cours, avec son état la valeur **en attente**.  
  
> [!NOTE]
>  L’exemple de feuille de route rampe d’entrée utilise la résolution dynamique pour envoyer des messages dans le dossier de sortie. Cela est pourquoi il n’est pas statique port d’envoi défini pour cet exemple.  
  
 Voici la séquence d’événements qui se produisent après que l’application de client de test envoie le message :  
  
-   Port de réception le OnRamp.Itinerary reçoit le message.  
  
-   Le pipeline ItineraryReceiveXml extrait l’itinéraire à partir de l’en-tête SOAP, valide et traite des, écrit l’itinéraire sous la forme d’une propriété de contexte de message dans le message entrant et publie le message dans la base de données MessageBox de BizTalk.  
  
-   Un abonnement pour l’orchestration de service Microsoft.Practices.ESB.Services.Transform déclenche l’appel de cette orchestration. L’orchestration récupère d’abord l’étape actuelle de l’itinéraire en passant le message actuel en tant que paramètre, comme indiqué dans le code suivant.  
  
    ```csharp  
    itineraryStep =   itinerary.Itinerary.GetItineraryStep(InboundMessage);  
    ```  
  
-   Le **ItineraryStep** objet contient toutes les informations sur l’instance de service en cours d’exécution, ainsi que les programmes de résolution associés.  
  
-   Le **résolveur** objet est récupéré à partir de la **ItineraryStep** instance et le cadre du programme de résolution ESB permet de résoudre le nom complet du plan de transformation, comme indiqué dans le code suivant.  
  
    ```csharp  
    resolverDictionary =   
       Microsoft.Practices.ESB.Resolver.ResolverMgr.Resolve(InboundMessage,  
                                                            resolver);  
  
    // Set the transform type.  
    transformType = resolverDictionary.Item("Resolver.TransformType");  
    ```  
  
-   Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] programme de résolution et l’infrastructure d’adaptateurs accomplit cela en chargeant le programme de résolution approprié à partir du cache (dans cet exemple, le programme de résolution du moteur de règles d’entreprise BizTalk), qui appelle la stratégie ResolverMap et remplit la  **ResolverDictionary** objet.  
  
-   Une fois l’orchestration terminée, le code appelle la **AdvanceItinerary** méthode, comme indiqué dans le code suivant.  
  
    ```csharp  
    // Call the Itinerary helper to advance to the next step.  
    itinerary.Itinerary.Advance(OutboundMessage, itineraryStep.ItineraryStep);  
    ```  
  
-   Cela avance l’itinéraire actuel de mise à jour de ses propriétés et de promouvoir le prochain service défini dans la feuille de route en tant que celui à exécuter ensuite. La méthode de copie de la feuille de route dans le message sortant, ce qui est le service publie dans la base de données de la boîte de Message via un port d’envoi de la liaison directe.  
  
-   Un abonnement pour l’orchestration de service Microsoft.Practices.ESB.Services.Delivery déclenche l’appel de cette orchestration. Cette orchestration suit un processus similaire à la première, obtention de l’étape actuelle de la feuille de route. Toutefois, cette orchestration itère sur une collection de programmes de résolution retourné par le **ItineraryStep** instance. Pour chaque programme de résolution dans la collection, l’orchestration de remise utilise le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] programme de résolution et infrastructure d’adaptateurs pour résoudre les emplacements de transport et de les promouvoir en tant que propriétés de contexte dans le message sortant, comme indiqué dans le code suivant.  
  
    ```csharp  
    // Move to retrieve the first resolver.  
    resolver = resolvers.Current;  
  
    // Pass the resolver configuration to the Resolver Manager   
    // for resolution.  
    resolverDictionary =  
       Microsoft.Practices.ESB.Resolver.ResolverMgr.Resolve(InboundMessage,  
                                                            resolver);  
  
    // Set the transport properties.  
    transportLocation =   
       resolverDictionary.Item("Resolver.TransportLocation");  
    transportType =   
       resolverDictionary.Item("Resolver.TransportType");  
  
    // Call the Adapter Manager to set all necessary properties.  
    Microsoft.Practices.ESB.Adapter.AdapterMgr.SetEndpoint(  
                                    resolverDictionary, DeliveryMessage);  
  
    // Set the delivery port address and type.  
    DeliveryPort(Microsoft.XLANGs.BaseTypes.Address) = transportLocation;  
    DeliveryPort(Microsoft.XLANGs.BaseTypes.TransportType) = transportType;  
    ```  
  
-   Un abonnement pour l’orchestration ProcessAndRespond déclenche l’appel de cette orchestration en raison d’une correspondance des propriétés de contexte de message définis pour les propriétés de l’expression de filtre.  
  
    ```  
    (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceName == :"ProcessAndRespond")   
    && Microsoft.Practices.ESB.Itinerary.Schemas.ServiceState == "Pending")  
    && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceType == "Orchestration")  
    ```  
  
-   L’orchestration ProcessAndRespond avance l’itinéraire et envoie le message d’origine de la demande au service rampe d’entrée à l’application de Client de Test d’itinéraire dans la réponse.