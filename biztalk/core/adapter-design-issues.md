---
title: "Problèmes de conception de carte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e5568be-a046-40ff-a94a-eda086457564
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79c6228db8342f3d1ad2628d4e4caf418efd9b29
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-design-issues"></a><span data-ttu-id="da15e-102">Problèmes de conception de l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="da15e-102">Adapter Design Issues</span></span>
<span data-ttu-id="da15e-103">La configuration de l’adaptateur est conservée dans la base de données d’authentification unique lorsque l’utilisateur modifie la configuration au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="da15e-103">Adapter configuration is stored in the Single Sign-On (SSO) database when the user makes configuration changes during design time.</span></span> <span data-ttu-id="da15e-104">Au moment de l’exécution, le moteur de messagerie extrait la configuration de l'adaptateur et la livre à l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="da15e-104">At run time the Messaging Engine retrieves the adapter's configuration and delivers it to the adapter.</span></span> <span data-ttu-id="da15e-105">Quatre types d'informations de configuration sont livrés à l'adaptateurs :</span><span class="sxs-lookup"><span data-stu-id="da15e-105">Four types of configuration information are delivered to adapters:</span></span>  
  
-   <span data-ttu-id="da15e-106">configuration du gestionnaire de réception</span><span class="sxs-lookup"><span data-stu-id="da15e-106">Receive handler configuration</span></span>  
  
-   <span data-ttu-id="da15e-107">configuration (point de terminaison) de l'emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="da15e-107">Receive location (endpoint) configuration</span></span>  
  
-   <span data-ttu-id="da15e-108">configuration du gestionnaire d’envoi</span><span class="sxs-lookup"><span data-stu-id="da15e-108">Send handler configuration</span></span>  
  
-   <span data-ttu-id="da15e-109">configuration (point de terminaison) de l'emplacement d’envoi</span><span class="sxs-lookup"><span data-stu-id="da15e-109">Send location (endpoint) configuration</span></span>  
  
## <a name="receive-and-send-handler-configuration"></a><span data-ttu-id="da15e-110">configuration du gestionnaire de réception et d’envoi</span><span class="sxs-lookup"><span data-stu-id="da15e-110">Receive and Send Handler Configuration</span></span>  
 <span data-ttu-id="da15e-111">Configuration du Gestionnaire d’un adaptateur est remise à l’adaptateur dans son implémentation de l’option **IPersistPropertyBag**. **Charge** interface.</span><span class="sxs-lookup"><span data-stu-id="da15e-111">An adapter's handler configuration is delivered to the adapter on its implementation of the optional **IPersistPropertyBag**.**Load** interface.</span></span> <span data-ttu-id="da15e-112">La configuration du gestionnaire n'est remise qu'une fois, par conséquent, si la configuration du gestionnaire de l'adaptateur est modifiée une fois que le service BizTalk a démarré, l’adaptateur n’est pas mis à jour.</span><span class="sxs-lookup"><span data-stu-id="da15e-112">The handler configuration is delivered only once, so if the adapter handler configuration is changed after the BizTalk service has started the adapter is not updated.</span></span> <span data-ttu-id="da15e-113">Dans le modèle commun l’adaptateur considère la configuration du gestionnaire comme configuration par défaut ; la configuration de la terminaison remplace la configuration du gestionnaire terminaison par terminaison.</span><span class="sxs-lookup"><span data-stu-id="da15e-113">The common model is for the adapter to treat the handler configuration as the default configuration; endpoint configuration overrides the handler configuration on a per-endpoint basis.</span></span>  
  
 <span data-ttu-id="da15e-114">Le fragment de code suivant illustre l’analyse de la configuration.</span><span class="sxs-lookup"><span data-stu-id="da15e-114">The following code fragment demonstrates parsing the configuration.</span></span> <span data-ttu-id="da15e-115">Configuration de l’adaptateur est dans la propriété transmise à la **charge** appeler dans la propriété de chaîne **AdapterConfig**.</span><span class="sxs-lookup"><span data-stu-id="da15e-115">The adapter's configuration is in the property passed in to the **Load** call in the string property **AdapterConfig**.</span></span> <span data-ttu-id="da15e-116">Cette valeur de propriété contient un document XML qui représente la configuration de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="da15e-116">This property value contains an XML document representing the adapter's configuration.</span></span> <span data-ttu-id="da15e-117">L’adaptateur doit charger cette configuration dans un modèle objet de document (DOM) ou dans un lecteur XML et utiliser XPath pour extraire les propriétés individuelles.</span><span class="sxs-lookup"><span data-stu-id="da15e-117">The adapter needs to load this configuration into a document object model (DOM) or an XML reader and use XPath to retrieve the individual properties.</span></span>  
  
```  
public class MyAdapter : IBTTransport,   
 IBTTransportConfig,   
 IBTTransportControl,  
 IPersistPropertyBag,   
 IBaseComponent  
{  
...  
// Handler configuration properties...  
private int defaultBatchSize = 0;  
private string defaultHeader;  
  
// IPersistPropertyBag.Load() implementation...  
public void Load(IPropertyBag pb, int pErrorLog)  
{  
// The adapter configuration is in the property  
 // “AdapterConfig” in the form of an Xml blob...  
object obj = null;  
pb.Read("AdapterConfig", out obj, 0);  
  
// Create a DOM and load the Xml blob...  
XmlDocument dom = new XmlDocument();  
string adapterConfig = (string)obj;  
dom.LoadXml(adapterConfig);  
  
// XPath the individual properties...  
XmlNode node =   
 document.SelectSingleNode(“/Config/batchSize”);  
defaultBatchSize = int.Parse(node.InnerText);  
  
node = document.SelectSingleNode(“/Config/header”);  
defaultHeader = node.InnerText;  
}  
}  
```  
  
## <a name="receive-location-configuration"></a><span data-ttu-id="da15e-118">Configuration des emplacements de réception</span><span class="sxs-lookup"><span data-stu-id="da15e-118">Receive Location Configuration</span></span>  
 <span data-ttu-id="da15e-119">Emplacement de réception des informations de configuration sont remises à l’adaptateur dans son implémentation de **IBTTransportConfig**.</span><span class="sxs-lookup"><span data-stu-id="da15e-119">Receive location configuration information is delivered to an adapter on its implementation of **IBTTransportConfig**.</span></span> <span data-ttu-id="da15e-120">Cette interface contient trois méthodes **AddReceiveEndpoint**, **UpdateEndpointConfig**, et **RemoveReceiveEndpoint**.</span><span class="sxs-lookup"><span data-stu-id="da15e-120">This interface contains the three methods **AddReceiveEndpoint**, **UpdateEndpointConfig**, and **RemoveReceiveEndpoint**.</span></span> <span data-ttu-id="da15e-121">Le moteur de messagerie indique à l’adaptateur sur quels points de terminaison il a besoin d’écouter pour recevoir des messages.</span><span class="sxs-lookup"><span data-stu-id="da15e-121">The Messaging Engine notifies the adapter of which endpoints it needs to listen on to receive messages.</span></span> <span data-ttu-id="da15e-122">Lorsque la configuration d'un point de terminaison individuel est modifiée, l’adaptateur est averti de la modification apportée à ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="da15e-122">When the configuration for an individual endpoint is changed the adapter is notified of the change for that endpoint.</span></span> <span data-ttu-id="da15e-123">En revanche, lorsque la configuration du gestionnaire est modifiée, l'adaptateur ne reçoit aucune notification.</span><span class="sxs-lookup"><span data-stu-id="da15e-123">This is in contrast to the fact that when handler configuration changes the adapter is not notified.</span></span> <span data-ttu-id="da15e-124">De la même façon, l’adaptateur n’a pas besoin de gérer les fenêtres de service car BizTalk Server ajoute ou supprime les points de terminaison à mesure que les fenêtres de service deviennent actives ou non.</span><span class="sxs-lookup"><span data-stu-id="da15e-124">Similarly, the adapter does not need to handle service windows because BizTalk Server adds or removes endpoints as service windows become active or inactive.</span></span>  
  
### <a name="addreceiveendpoint"></a><span data-ttu-id="da15e-125">AddReceiveEndpoint</span><span class="sxs-lookup"><span data-stu-id="da15e-125">AddReceiveEndpoint</span></span>  
 <span data-ttu-id="da15e-126">Lorsqu’un adaptateur doit commencer à écouter sur un point de terminaison, le moteur appelle **IBTTransportConfig.AddReceiveEndpoint** de passage dans l’URI de l’emplacement de réception, un jeu de propriétés contenant la configuration de l’adaptateur pour ce point de terminaison, et un deuxième jeu de propriétés contenant la configuration spécifique à BizTalk Server pour ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="da15e-126">When an adapter needs to begin listening on an endpoint, the engine calls **IBTTransportConfig.AddReceiveEndpoint** passing in the receive location's URI, a property bag containing the adapter's configuration for that endpoint, and a second property bag containing BizTalk Server-specific configuration for that endpoint.</span></span> <span data-ttu-id="da15e-127">L’adaptateur doit écrire l’URI dans le contexte du message en tant que la propriété système BizTalk Server **InboundTransportLocation**.</span><span class="sxs-lookup"><span data-stu-id="da15e-127">The adapter needs to write the URI to the message context as the BizTalk Server system property **InboundTransportLocation**.</span></span>  
  
 <span data-ttu-id="da15e-128">Le fait de lire les propriétés de l’emplacement de réception à partir du jeu de propriété est identique au fait de lire la configuration du gestionnaire selon la description ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="da15e-128">Reading the receive location properties from the adapter's property bag is the same as reading the handler configuration as detailed above.</span></span> <span data-ttu-id="da15e-129">La configuration de BizTalk Server transmise dans l’adaptateur contient une seule propriété, **TwoWayReceivePort**, qui indique si le port est unidirectionnel ou bidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="da15e-129">The BizTalk Server configuration passed into the adapter contains a single property, **TwoWayReceivePort**, which indicates whether the port is one-way or two-way.</span></span> <span data-ttu-id="da15e-130">Le fragment de code suivant montre comment déterminer si le port de réception est unidirectionnel ou bidirectionnel dans le jeu de propriétés de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="da15e-130">The following code fragment illustrates how to evaluate if the receive port is one-way or two-way from the BizTalk Server property bag:</span></span>  
  
```  
public void AddReceiveEndpoint(  
 string  url,   
 IPropertyBag adapterConfig,   
 IPropertyBag bizTalkConfig )  
{  
...  
  
// The property "TwoWayReceivePort" in the BizTalk Config  
// property bag indicates whether the port is one or two  
 // way...  
  
 // Add receive location to config cache (not shown here)  
  
object obj = null;  
bizTalkConfig.Read("TwoWayReceivePort", out obj, 0);  
  
if ( null != obj )  
this.twoWay = (bool)obj;  
}  
```  
  
### <a name="updateendpointconfig"></a><span data-ttu-id="da15e-131">UpdateEndpointConfig</span><span class="sxs-lookup"><span data-stu-id="da15e-131">UpdateEndpointConfig</span></span>  
 <span data-ttu-id="da15e-132">Lorsque la configuration d’un actif de réception emplacement est modifié, le moteur utilise le **UpdateEndpointConfig** API pour avertir l’adaptateur qu’il doit utiliser une configuration différente.</span><span class="sxs-lookup"><span data-stu-id="da15e-132">When the configuration of an active receive location is changed, the engine uses the **UpdateEndpointConfig** API to notify the adapter that it needs to use a different configuration.</span></span> <span data-ttu-id="da15e-133">Toute la configuration est transmise à l’adaptateur, y compris la configuration spécifique à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="da15e-133">All of the configuration is delivered to the adapter, including the BizTalk Server-specific configuration.</span></span>  
  
### <a name="removereceiveendpoint"></a><span data-ttu-id="da15e-134">RemoveReceiveEndpoint</span><span class="sxs-lookup"><span data-stu-id="da15e-134">RemoveReceiveEndpoint</span></span>  
 <span data-ttu-id="da15e-135">Lorsqu’un emplacement de réception n’est plus actif, l’adaptateur est notifié via **RemoveReceiveEndpoint**.</span><span class="sxs-lookup"><span data-stu-id="da15e-135">When a receive location is no longer active, the adapter is notified through **RemoveReceiveEndpoint**.</span></span> <span data-ttu-id="da15e-136">Une fois que l’adaptateur retourne à partir de **RemoveReceiveEndpoint** il n’est plus autorisé à utiliser cet URI pour envoyer des messages dans le moteur.</span><span class="sxs-lookup"><span data-stu-id="da15e-136">After the adapter returns from **RemoveReceiveEndpoint** it is no longer allowed to use that URI to submit messages into the engine.</span></span>  
  
## <a name="send-port-configuration"></a><span data-ttu-id="da15e-137">Configuration du port d’envoi</span><span class="sxs-lookup"><span data-stu-id="da15e-137">Send Port Configuration</span></span>  
 <span data-ttu-id="da15e-138">Le moteur de messagerie écrit la configuration du port d’envoi au contexte de message dans l’espace nom de l’adaptateur avant d’envoyer le message à l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="da15e-138">The Messaging Engine writes the configuration for the send port to the message context in the adapter’s namespace before delivering the message to the adapter.</span></span> <span data-ttu-id="da15e-139">L’adaptateur lit et valide la configuration, qu’il utilise immédiatement pour contrôler la transmission du message.</span><span class="sxs-lookup"><span data-stu-id="da15e-139">It is the adapters’ responsibility to read and validate the configuration, which it subsequently uses to control the transmission of the message.</span></span> <span data-ttu-id="da15e-140">Pour les adaptateurs d’envoi qui prennent en charge des envois par lots, il se peut que des messages destinés à différents ports d'envoi se trouvent dans le même lot, par conséquent l'adaptateur doit gérer ces lots "mixtes".</span><span class="sxs-lookup"><span data-stu-id="da15e-140">For send adapters that support batched sends, messages destined for different send ports may be in the same batch, so the adapter needs to handle these "mixed" batches.</span></span>  
  
 <span data-ttu-id="da15e-141">Le fragment de code suivant montre comment lire le **OutboundTransportLocation** qui est l’URI du port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="da15e-141">The following code fragment illustrates how to read the **OutboundTransportLocation** that is the URI for the send port.</span></span> <span data-ttu-id="da15e-142">Il montre également lire l'objet blob XML contenant la configuration de l’adaptateur avant de lire les propriétés individuelles.</span><span class="sxs-lookup"><span data-stu-id="da15e-142">It also shows how to read the XML blob containing the adapter's configuration and then read the individual properties.</span></span>  
  
```  
...  
 private static readonly PropertyBase UriProperty =   
 new BTS.OutboundTransportLocation();  
  
 private string propertyNamespace =   
  "http://schemas.mySchemas.com/MyAdapter/myadapter-properties";  
private string uri;  
private string headers;  
private int timeOut = 1000;  
  
private void ReadSendPortConfig(IBaseMessage msg)  
{  
// Read the OutboundTransportLocation,   
 // i.e. the send port uri....  
uri = (string)msg.Context.Read(  
 UriProperty.Name.Name, UriProperty.Name.Namespace);  
  
// Read the adapters configuration Xml blob from   
 // the message...  
XmlDocument locationConfigDom = null;  
object obj = msg.Context.Read(  
 "AdapterConfig", this.propertyNamespace);  
  
// If this is a dynamic send there will not be   
 // any configuration...  
if ( null != obj )  
{  
locationConfigDom = new XmlDocument();  
locationConfigDom.LoadXml((string)obj);  
  
this.headers = Extract(  
 locationConfigDom, "/Config/headers", true);  
  
 this.timeOut = ExtractInt32(  
 locationConfigDom, "/Config/timeOut", true);  
}  
}  
  
 // Helper method to XPath string properties...  
private static string Extract(  
 XmlDocument document, string path, bool required)  
{  
XmlNode node = document.SelectSingleNode(path);  
if (!required && null == node)  
return String.Empty;  
if (null == node)  
throw new ApplicationException(string.Format(  
 "No property was found at {0}", path));  
return node.InnerText;  
}  
  
  // Helper method to XPath int32 properties...  
private static int ExtractInt32(  
 XmlDocument document, string path, bool required)  
{  
string s = Extract(document, path, required);  
return int.Parse(s);  
}   
```  
  
 <span data-ttu-id="da15e-143">**Conseil pour l’implémentation :** adaptateurs doivent en général utiliser le **OutboundTransportLocation** propriété de contexte pour déterminer l’adresse pour envoyer le message au message.</span><span class="sxs-lookup"><span data-stu-id="da15e-143">**Implementation Tip:** Adapters should in general use the **OutboundTransportLocation** message context property to determine the address to send the message to.</span></span> <span data-ttu-id="da15e-144">Ce faisant, l’adaptateur peut gérer les transmissions statiques et dynamiques de façon cohérente.</span><span class="sxs-lookup"><span data-stu-id="da15e-144">By doing this the adapter can handle transmissions to both static and dynamic sends consistently.</span></span> <span data-ttu-id="da15e-145">Cela permet également de simplifier la modification des adresses dans les fichiers de liaison de production.</span><span class="sxs-lookup"><span data-stu-id="da15e-145">This also simplifies the modification of addresses in production binding files.</span></span>  
  
## <a name="xsd"></a><span data-ttu-id="da15e-146">XSD</span><span class="sxs-lookup"><span data-stu-id="da15e-146">XSD</span></span>  
 <span data-ttu-id="da15e-147">Quatre fichiers XSD inclus dans l’exemple d’adaptateur de fichier SDK principalement descripteur de configuration de la carte : ReceiveHandler.xsd, ReceiveLocation.xsd, TransmitLocation.xsd et TransmitHandler.xsd.</span><span class="sxs-lookup"><span data-stu-id="da15e-147">Four XSD files included in the SDK File Adapter sample primarily handle adapter configuration: ReceiveHandler.xsd, ReceiveLocation.xsd, TransmitLocation.xsd, and TransmitHandler.xsd.</span></span>  
  
 <span data-ttu-id="da15e-148">Les rubriques suivantes portent sur chacun de ces fichiers et expliquent comment les modifier :</span><span class="sxs-lookup"><span data-stu-id="da15e-148">The following topics discuss each of these files and describe how you can modify them.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="da15e-149">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="da15e-149">In This Section</span></span>  
  
-   [<span data-ttu-id="da15e-150">Validation de la Configuration de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="da15e-150">Validating the Adapter Configuration</span></span>](../core/validating-the-adapter-configuration.md)  
  
-   [<span data-ttu-id="da15e-151">Inscription d’un adaptateur</span><span class="sxs-lookup"><span data-stu-id="da15e-151">Registering an Adapter</span></span>](../core/registering-an-adapter.md)  
  
-   [<span data-ttu-id="da15e-152">Extensions de schéma de Configuration Framework adaptateur</span><span class="sxs-lookup"><span data-stu-id="da15e-152">Adapter Framework Configuration Schema Extensions</span></span>](../core/adapter-framework-configuration-schema-extensions.md)  
  
-   [<span data-ttu-id="da15e-153">Types d’éléments XSD adaptateur pris en charge</span><span class="sxs-lookup"><span data-stu-id="da15e-153">Supported Adapter XSD Element Types</span></span>](../core/supported-adapter-xsd-element-types.md)  
  
-   [<span data-ttu-id="da15e-154">Constructions élément-attribut XSD l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="da15e-154">Adapter XSD Element-Attribute Constructs</span></span>](../core/adapter-xsd-element-attribute-constructs.md)  
  
-   [<span data-ttu-id="da15e-155">Constructions de facette de Type de données XSD adaptateur</span><span class="sxs-lookup"><span data-stu-id="da15e-155">Adapter XSD Data Type-Facet Constructs</span></span>](../core/adapter-xsd-data-type-facet-constructs.md)  
  
-   [<span data-ttu-id="da15e-156">Composants de Configuration avancée pour les cartes</span><span class="sxs-lookup"><span data-stu-id="da15e-156">Advanced Configuration Components for Adapters</span></span>](../core/advanced-configuration-components-for-adapters.md)