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
# <a name="adapter-design-issues"></a>Problèmes de conception de l'adaptateur
La configuration de l’adaptateur est conservée dans la base de données d’authentification unique lorsque l’utilisateur modifie la configuration au moment de la conception. Au moment de l’exécution, le moteur de messagerie extrait la configuration de l'adaptateur et la livre à l'adaptateur. Quatre types d'informations de configuration sont livrés à l'adaptateurs :  
  
-   configuration du gestionnaire de réception  
  
-   configuration (point de terminaison) de l'emplacement de réception  
  
-   configuration du gestionnaire d’envoi  
  
-   configuration (point de terminaison) de l'emplacement d’envoi  
  
## <a name="receive-and-send-handler-configuration"></a>configuration du gestionnaire de réception et d’envoi  
 Configuration du Gestionnaire d’un adaptateur est remise à l’adaptateur dans son implémentation de l’option **IPersistPropertyBag**. **Charge** interface. La configuration du gestionnaire n'est remise qu'une fois, par conséquent, si la configuration du gestionnaire de l'adaptateur est modifiée une fois que le service BizTalk a démarré, l’adaptateur n’est pas mis à jour. Dans le modèle commun l’adaptateur considère la configuration du gestionnaire comme configuration par défaut ; la configuration de la terminaison remplace la configuration du gestionnaire terminaison par terminaison.  
  
 Le fragment de code suivant illustre l’analyse de la configuration. Configuration de l’adaptateur est dans la propriété transmise à la **charge** appeler dans la propriété de chaîne **AdapterConfig**. Cette valeur de propriété contient un document XML qui représente la configuration de l'adaptateur. L’adaptateur doit charger cette configuration dans un modèle objet de document (DOM) ou dans un lecteur XML et utiliser XPath pour extraire les propriétés individuelles.  
  
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
  
## <a name="receive-location-configuration"></a>Configuration des emplacements de réception  
 Emplacement de réception des informations de configuration sont remises à l’adaptateur dans son implémentation de **IBTTransportConfig**. Cette interface contient trois méthodes **AddReceiveEndpoint**, **UpdateEndpointConfig**, et **RemoveReceiveEndpoint**. Le moteur de messagerie indique à l’adaptateur sur quels points de terminaison il a besoin d’écouter pour recevoir des messages. Lorsque la configuration d'un point de terminaison individuel est modifiée, l’adaptateur est averti de la modification apportée à ce point de terminaison. En revanche, lorsque la configuration du gestionnaire est modifiée, l'adaptateur ne reçoit aucune notification. De la même façon, l’adaptateur n’a pas besoin de gérer les fenêtres de service car BizTalk Server ajoute ou supprime les points de terminaison à mesure que les fenêtres de service deviennent actives ou non.  
  
### <a name="addreceiveendpoint"></a>AddReceiveEndpoint  
 Lorsqu’un adaptateur doit commencer à écouter sur un point de terminaison, le moteur appelle **IBTTransportConfig.AddReceiveEndpoint** de passage dans l’URI de l’emplacement de réception, un jeu de propriétés contenant la configuration de l’adaptateur pour ce point de terminaison, et un deuxième jeu de propriétés contenant la configuration spécifique à BizTalk Server pour ce point de terminaison. L’adaptateur doit écrire l’URI dans le contexte du message en tant que la propriété système BizTalk Server **InboundTransportLocation**.  
  
 Le fait de lire les propriétés de l’emplacement de réception à partir du jeu de propriété est identique au fait de lire la configuration du gestionnaire selon la description ci-dessus. La configuration de BizTalk Server transmise dans l’adaptateur contient une seule propriété, **TwoWayReceivePort**, qui indique si le port est unidirectionnel ou bidirectionnel. Le fragment de code suivant montre comment déterminer si le port de réception est unidirectionnel ou bidirectionnel dans le jeu de propriétés de BizTalk Server.  
  
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
  
### <a name="updateendpointconfig"></a>UpdateEndpointConfig  
 Lorsque la configuration d’un actif de réception emplacement est modifié, le moteur utilise le **UpdateEndpointConfig** API pour avertir l’adaptateur qu’il doit utiliser une configuration différente. Toute la configuration est transmise à l’adaptateur, y compris la configuration spécifique à BizTalk Server.  
  
### <a name="removereceiveendpoint"></a>RemoveReceiveEndpoint  
 Lorsqu’un emplacement de réception n’est plus actif, l’adaptateur est notifié via **RemoveReceiveEndpoint**. Une fois que l’adaptateur retourne à partir de **RemoveReceiveEndpoint** il n’est plus autorisé à utiliser cet URI pour envoyer des messages dans le moteur.  
  
## <a name="send-port-configuration"></a>Configuration du port d’envoi  
 Le moteur de messagerie écrit la configuration du port d’envoi au contexte de message dans l’espace nom de l’adaptateur avant d’envoyer le message à l’adaptateur. L’adaptateur lit et valide la configuration, qu’il utilise immédiatement pour contrôler la transmission du message. Pour les adaptateurs d’envoi qui prennent en charge des envois par lots, il se peut que des messages destinés à différents ports d'envoi se trouvent dans le même lot, par conséquent l'adaptateur doit gérer ces lots "mixtes".  
  
 Le fragment de code suivant montre comment lire le **OutboundTransportLocation** qui est l’URI du port d’envoi. Il montre également lire l'objet blob XML contenant la configuration de l’adaptateur avant de lire les propriétés individuelles.  
  
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
  
 **Conseil pour l’implémentation :** adaptateurs doivent en général utiliser le **OutboundTransportLocation** propriété de contexte pour déterminer l’adresse pour envoyer le message au message. Ce faisant, l’adaptateur peut gérer les transmissions statiques et dynamiques de façon cohérente. Cela permet également de simplifier la modification des adresses dans les fichiers de liaison de production.  
  
## <a name="xsd"></a>XSD  
 Quatre fichiers XSD inclus dans l’exemple d’adaptateur de fichier SDK principalement descripteur de configuration de la carte : ReceiveHandler.xsd, ReceiveLocation.xsd, TransmitLocation.xsd et TransmitHandler.xsd.  
  
 Les rubriques suivantes portent sur chacun de ces fichiers et expliquent comment les modifier :  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Validation de la Configuration de l’adaptateur](../core/validating-the-adapter-configuration.md)  
  
-   [Inscription d’un adaptateur](../core/registering-an-adapter.md)  
  
-   [Extensions de schéma de Configuration Framework adaptateur](../core/adapter-framework-configuration-schema-extensions.md)  
  
-   [Types d’éléments XSD adaptateur pris en charge](../core/supported-adapter-xsd-element-types.md)  
  
-   [Constructions élément-attribut XSD l’adaptateur](../core/adapter-xsd-element-attribute-constructs.md)  
  
-   [Constructions de facette de Type de données XSD adaptateur](../core/adapter-xsd-data-type-facet-constructs.md)  
  
-   [Composants de Configuration avancée pour les cartes](../core/advanced-configuration-components-for-adapters.md)