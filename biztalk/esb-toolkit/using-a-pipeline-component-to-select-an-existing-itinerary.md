---
title: "À l’aide d’un composant de Pipeline pour sélectionner un itinéraire existant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b93c5cb6-071f-485d-b0bb-22f95bafa3d0
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a733da2348de13120ce37a205b77d2e8194c7790
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-a-pipeline-component-to-select-an-existing-itinerary"></a>À l’aide d’un composant de Pipeline pour sélectionner un itinéraire existant
## <a name="esb-itinerary-selector-pipeline-component"></a>Composant de Pipeline ESB sélecteur d’itinéraire  
 Messages envoyés à l’aide de générique d’itinéraire sur écarts sont envoyées sans un en-tête d’itinéraire. Pour résoudre l’itinéraire approprié et l’attacher au message entrant, le démarrage doit fournir un mécanisme qui peut être configuré pour accéder à des itinéraires à partir d’un référentiel central.  
  
 Le composant de pipeline ESB itinéraire sélecteur utilise une chaîne de connexion de programme de résolution, conjointement avec les programmes de résolution spécifiques, pour résoudre le contenu d’un itinéraire côté serveur stocké dans un référentiel central (par défaut, SQL Server).  
  
 Lorsque le composant de pipeline ESB itinéraire sélecteur est utilisé dans WCF les écarts conjointement avec le programme de résolution d’itinéraire statique, le nom et la version de l’itinéraire demandé par le client (comme représenté dans l’en-tête SOAP) sont récupérées à partir du contexte de message et permet de sélectionner l’itinéraire approprié.  
  
 Par défaut, le composant de pipeline ESB itinéraire sélecteur se trouve dans les pipelines suivants :  
  
-   ItinerarySelectReceive  
  
-   ItinerarySelectReceivePassthrough  
  
-   ItinerarySelectReceiveXml  
  
-   ItinerarySelectSendReceive  
  
 Les sections suivantes décrivent les étapes effectuées par chaque composant.  
  
## <a name="esb-itinerary-selector-pipeline-component-processing-steps"></a>Étapes de traitement de composant de Pipeline de sélecteur d’itinéraire ESB  
 Le composant de pipeline ESB itinéraire sélecteur exécute les étapes suivantes :  
  
-   Le tiers émetteur envoie un message pour le traitement. Le composant de sélecteur d’itinéraire utilise un programme de résolution spécifié comme une chaîne de connexion propriété configurée par le développeur, pour déterminer et sélectionnez la feuille de route approprié à partir du magasin d’itinéraire, basé sur le contenu du message ou le contexte.  
  
-   Il valide l’itinéraire et définit des propriétés spécifiques à prédéfinir des valeurs par défaut s’ils sont null dans l’itinéraire ; par exemple :  
  
    -   Si le compte de Service est inférieur à 1, le composant lève une exception.  
  
    -   Le composant définit les attributs d’itinéraire racine en utilisant les valeurs pour le compte de Service, l’identificateur (**Uuid**), l’heure de début (**BeginTime**), et s’il s’agit d’une demande unidirectionnelle ou bidirectionnelle (**IsRequestResponse**).  
  
    -   Le composant valide les services, définit les identificateurs, définit l’instance de service en cours (le service à traiter suivant) et valide les programmes de résolution associés.  
  
    -   Le composant définit le segment de Microsoft BizTalk Server de l’itinéraire à l’aide des propriétés suivantes :  
  
        -   **correlationToken**  
  
        -   **reqRespTransmitPipelineID**  
  
        -   **interchangeId**  
  
        -   **receiveInstanceId**  
  
        -   **epmRRCorrelationToken**  
  
    -   Le composant écrit l’itinéraire modifié dans les propriétés de contexte de message BizTalk répertoriées dans le tableau suivant à l’aide des propriétés définies dans le schéma.xsd de système.  
  
        |Propriétés|  
        |----------------|  
        |**Nom = ItineraryHeader**|  
        |**Namespace = http://schemas.microsoft.biztalk.practices.esb.com/itinerary/system-properties**|  
  
    -   Le composant promeut les propriétés de contexte BizTalk quatre répertoriées dans le tableau suivant à l’aide des valeurs définies dans le schéma.xsd de système.  
  
        |Propriété|Valeur|  
        |--------------|-----------|  
        |**ServiceName**|Le nom de l’instance actuelle de service défini dans la feuille de route.|  
        |**ServiceType**|La valeur **Orchestration** ou **de messagerie**.|  
        |**IsRequestResponse**|La valeur **True** ou **False**.|  
        |**ServiceState**|La valeur **en attente**.|  
  
## <a name="esb-dispatcher-pipeline-component-process-steps"></a>Étapes du processus de composant Pipeline ESB répartiteur  
 Le composant de pipeline ESB répartiteur exécute les étapes suivantes :  
  
-   Il gère l’exécution de toutes les étapes d’itinéraire de type **messagerie** et avance la route. Le composant ESB répartiteur est sensible à l’emplacement et exécute la logique en fonction de son emplacement dans le cycle de traitement messagerie, ce qui pourrait être **de réception entrant**, **envoyer transmettre**, **d’envoi Trafic entrant**, ou **de réception sortant**. Le composant de pipeline ESB répartiteur appelle ESB feuille de route des services de messagerie spécifiées dans le fichier Esb.config. Par défaut, les propriétés de configuration de ce composant pour le routage et la transformation sont associées avec les services suivants :  
  
    -   **Microsoft.Practices.ESB.Services.Transform**. Ce service exécute les mappages BizTalk par rapport à la charge utile d’un message entrant. Le service valide les exigences de transformation et met à jour les propriétés de contexte BizTalk qui contiennent le nom de spécification de document et le type de message. Le répartiteur ESB exécute ce service uniquement s’il s’agit du nom du service de transformation tel qu’il apparaît dans la propriété correspondante du composant de pipeline ESB répartiteur.  
  
    -   **Microsoft.Practices.ESB.Services.Routing.** Ce service utilise le programme de résolution et le fournisseur d’infrastructure d’adaptateurs pour définir les informations de routage de point de terminaison approprié. Le répartiteur ESB exécute ce service uniquement s’il s’agit du nom du service de routage tel qu’il apparaît dans la propriété correspondante du composant de pipeline ESB répartiteur.