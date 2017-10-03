---
title: "Basée sur un itinéraire de routage artefacts | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cff38ab7-5a16-42cc-9065-075e9db7acd3
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ca01cc5313c8ca64418f65cec3fdf18fdbc85df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="itinerary-based-routing-artifacts"></a>Artefacts de routage basé sur la feuille de route
Les fonctionnalités de routage basé sur la feuille de route de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] incluent un ensemble de clés artefacts définis dans plusieurs assemblys. Les tableaux suivants répertorient ces artefacts par catégorie pour aider les développeurs lorsque vous travaillez et l’extension de l’implémentation de routage basé sur un itinéraire avec des implémentations de service d’itinéraire ESB supplémentaires.  
  
## <a name="esb-itinerary-classes"></a>Classes de feuille de route ESB  
 Le tableau suivant répertorie les assemblys et les artefacts contenus dans l’architecture ESB. Projet d’itinéraire. Le nom de l’assembly conteneur est **Microsoft.Practices.ESB.Itinerary.dll**.  
  
|Artefact de clé| Description|  
|------------------|-----------------|  
|**MessageHelper**|Contient toutes les fonctions privées appelées par les autres artefacts de projet.|  
|**IItineraryStep**|La classe publique retournée à partir de la **GetItineraryStep** (méthode).|  
|**ResolverCollection**|Implémente une collection de tous les programmes de résolution associé à un service. Cette classe est exposée par le **IItineraryStep** de l’interface et est rempli par le **GetItineraryStep** (méthode).|  
|**IMessagingService**|Définit l’interface implémentée par les services d’itinéraire basés sur la messagerie.|  
|**IMessagingService**|Fabrique pour la création **IMessagingService** objets basés sur un nom configuré dans Esb.config.|  
  
## <a name="esb-itinerary-messaging-services"></a>Services de messagerie d’itinéraire ESB  
 Le tableau suivant répertorie les classes définies dans le **Microsoft.Practices.ESB.Itinerary.Services.dll** assembly dans **Microsoft.Practices.ESB.Itinerary.Services** espace de noms.  
  
|Artefact de clé| Description|  
|------------------|-----------------|  
|**Routage**|Implémentation de l’ESB d’itinéraire messagerie routage : appelé par les composants ESB répartiteur ou désassembler du répartiteur à l’aide du fichier Esb.config.|  
|**Transformation**|Implémentation de l’itinéraire ESB transformation service de messagerie : appelé par les composants ESB répartiteur ou désassembler du répartiteur à l’aide du fichier Esb.config.|  
  
 Le tableau suivant répertorie les artefacts contenus dans le **Microsoft.Practices.ESB.Itinerary.Services.Broker.dll** assembly.  
  
|Artefact de clé| Description|  
|------------------|-----------------|  
|**MessagingBroker**|Implémentation de l’itinéraire ESB service pour le routage par le contexte du message de messagerie : appelé par les composants ESB répartiteur ou désassembler du répartiteur à l’aide du fichier Esb.config.|  
  
 Ces services sont également définis dans le fichier de configuration de BizTalk ESB Toolkit, Esb.config.  
  
## <a name="esb-itinerary-orchestration-services"></a>Services d’Orchestration d’itinéraire ESB  
 Le tableau suivant répertorie les artefacts contenus dans le **Microsoft.Practices.ESB.Agents.dll** assembly.  
  
|Artefact de clé| Description|  
|------------------|-----------------|  
|Delivery.odx|Un exemple d’orchestration d’itinéraire service est identifiée par le nom du service de routage **Microsoft.Practices.ESB.Services.Routing**.|  
|Transform.odx|Un exemple d’orchestration d’itinéraire service de transformation identifié par le nom du service **Microsoft.Practices.ESB.Services.Transform**.|  
  
## <a name="esb-itinerary-pipeline-components"></a>Composants de Pipeline d’itinéraire ESB  
 Le tableau suivant répertorie les assemblys et les artefacts contenus dans le **Microsoft.Practices.ESB.Itinerary.PipelineComponents.dll** assembly.  
  
|Artefact de clé| Description|  
|------------------|-----------------|  
|**Feuille de route**|Le composant de pipeline de traitement d’itinéraire principal qui traite et valide l’itinéraire des messages entrants.|  
|**ItineraryCache**|Le composant d’itinéraire de pipeline mise en cache pour une utilisation dans les ports d’envoi de sollicitation-réponse.|  
|**ItinerarySelector**|Le composant de pipeline sélecteur d’itinéraire qui résout les itinéraires côté serveur dans les écarts génériques.|  
  
## <a name="esb-itinerary-pipelines"></a>Pipelines d’itinéraire ESB  
 Le tableau suivant répertorie les assemblys et les artefacts contenus dans le **Microsoft.Practices.ESB.Itinerary.Pipelines.dll** assembly.  
  
|Artefact de clé| Description|  
|------------------|-----------------|  
|ItineraryReceive|Le pipeline d’itinéraire utilisé dans la feuille de route Web service rampe d’entrée. Utilisé comme une opération de réception pour les emplacements de réception de pipeline et contient les composants suivants :<br /><br /> Répartiteur d’ESB ESB itinéraire, le désassembleur XML,|  
|ItineraryReceivePassthrough||  
|ItineraryReceiveXml|Le pipeline d’itinéraire utilisé dans la feuille de route Web service rampe d’entrée. Utilisé comme une opération de réception pour les emplacements de réception acheminer un message entrant à plusieurs points de terminaison de pipeline et contient les composants suivants :<br /><br /> Feuille de route ESB, désassembleur de répartiteur ESB|  
|ItinerarySend|Le pipeline d’itinéraire utilisé dans la feuille de route rampe. Utilisé comme un envoi pour un port d’envoi de pipeline et contient les composants suivants :<br /><br /> Cache d’itinéraire de ESB répartiteur, l’assembleur XML, ESB|  
|ItinerarySendPassthrough|Le pipeline d’itinéraire utilisé dans la feuille de route rampe. Utilisé comme un envoi pour un port d’envoi de pipeline et contient les composants suivants :<br /><br /> Répartiteur ESB, du Cache d’itinéraire d’ESB|  
|ItinerarySendReceive|Le pipeline d’itinéraire utilisé dans la feuille de route rampe. Utilisé comme un pipeline de réception d’une sollicitation-réponse, un port d’envoi et contient les composants suivants :<br /><br /> Répartiteur d’ESB ESB Cache d’itinéraire, désassembleur XML,|  
|ItineraryForwarderSendReceive|Le pipeline d’itinéraire utilisé dans la feuille de route rampe. Utilisé comme une opération de réception pour un port d’envoi de pipeline et contient les composants suivants :<br /><br /> Répartiteur ESB de Cache d’itinéraire, désassembleur XML, ESB, redirecteur|  
|ItineraryForwarderSendReceiveXml|Le pipeline d’itinéraire utilisé dans la feuille de route Web service rampe d’entrée. Utilisé comme une opération de réception pour un port d’envoi de pipeline et contient les composants suivants :<br /><br /> Cache d’itinéraire d’ESB, ESB répartiteur désassembler, redirecteur|  
|ItinerarySelectReceive|Le pipeline d’itinéraire utilisé dans la feuille de route Web service rampe d’entrée. Utilisé comme une opération de réception pour les emplacements de réception de pipeline et contient les composants suivants :<br /><br /> Répartiteur d’ESB ESB sélecteur d’itinéraire, désassembleur XML,|  
|ItinerarySelectReceivePassthrough|Le pipeline d’itinéraire utilisé dans la feuille de route Web service rampe d’entrée. Utilisé comme une opération de réception pour les emplacements de réception de pipeline et contient les composants suivants :<br /><br /> Sélecteur d’itinéraire ESB, ESB répartiteur|  
|ItinerarySelectReceiveXml|Le pipeline d’itinéraire utilisé dans la feuille de route Web service rampe d’entrée. Utilisé comme une opération de réception pour les emplacements de réception de pipeline et contient les composants suivants :<br /><br /> Répartiteur ESB désassembleur, sélecteur d’itinéraire d’ESB, XML|  
|ItinerarySelectSendReceive|Le pipeline d’itinéraire utilisé dans la feuille de route rampe. Utilisé comme une opération de réception pour un port d’envoi de pipeline et contient les composants suivants :<br /><br /> Désassembleur XML de Cache d’itinéraire, sélecteur d’itinéraire d’ESB, ESB, ESB répartiteur|  
  
## <a name="esb-itinerary-schemas"></a>Schémas d’itinéraire ESB  
 Le tableau suivant répertorie les assemblys et les artefacts contenus dans le **Microsoft.Practices.ESB.Itinerary.Schemas.dll** assembly.  
  
|Artefact de clé| Description|  
|------------------|-----------------|  
|Itinerary.xsd|Définit les en-têtes SOAP d’itinéraire ESB utilisés dans Windows Communication Foundation WCF et SOAP Web service sur écarts.|  
|ItineraryDescription.xsd|Cette scehma représente des données de référence d’itinéraire et doit être utilisé pour l’envoi de message basée sur WCF sur écarts.|  
|Système-.xsd|Définit les propriétés de contexte BizTalk ESB liée à un itinéraire.|