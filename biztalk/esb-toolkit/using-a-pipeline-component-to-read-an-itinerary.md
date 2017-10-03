---
title: "À l’aide d’un composant de Pipeline pour lire un itinéraire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e3b40c7-0f17-4d33-a26f-f51346a98be5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bceec4df732247be043e006b52c7abbfbf6a6b24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-a-pipeline-component-to-read-an-itinerary"></a>À l’aide d’un composant de Pipeline pour lire un itinéraire
Un message qui arrive dans un pipeline de réception peut contenir des métadonnées dans son en-tête SOAP qui définit ses besoins de traitement (itinéraire côté client). La figure 1 illustre l’utilisation de l’itinéraire d’ESB et composants de pipeline ESB répartiteur.  
  
 ![Lecture de composant de pipeline](../esb-toolkit/media/ch4-pipelinecomponentread.gif "PipelineComponentRead de chapitre 4")  
  
 **Figure 1**  
  
 **Exemple d’un composant de pipeline ESB itinéraire**  
  
 Un composant de pipeline ESB itinéraire peut être utilisé pour capturer les métadonnées à partir d’un message en tant que propriétés de contexte qui peuvent définir le traitement appliqué par l’architecture ESB.  
  
 Les sections suivantes décrivent les étapes effectuées par chaque composant.  
  
## <a name="esb-itinerary-pipeline-component-process-steps"></a>Étapes de processus de composant de Pipeline d’itinéraire ESB  
 Dans l’exemple illustré dans la Figure 1, le composant de pipeline ESB itinéraire exécute les étapes suivantes :  
  
-   Il lit l’en-tête SOAP de l’itinéraire. La partie présentant le définit l’itinéraire en remplissant l’en-tête SOAP lorsqu’il envoie le message. Une série de propriétés de contexte du message BizTalk représentent l’en-tête SOAP ; Ces propriétés varient, selon le type de carte de service Web qui est utilisé. Les cartes de service Web pertinentes sont les suivantes :  
  
    -   **Adaptateur WCF.** Cette carte traite les en-têtes SOAP et remplit les propriétés de contexte de message BizTalk répertoriées dans le tableau suivant.  
  
        |Propriétés|  
        |----------------|  
        |**Nom = feuille de route**|  
        |**Namespace = http://schemas.microsoft.biztalk.practices.esb.com/itinerary**|  
  
        > [!NOTE]
        >  Par défaut, l’adaptateur Windows Communication Foundation (WCF) utilise le nom racine du schéma nommé ItineraryDescription.xsd (ce schéma est utilisé pour générer l’en-tête SOAP d’itinéraire ESB) comme contexte BizTalk **nom** argument, et il utilise l’espace de noms cible du schéma en tant que le contexte de BizTalk **Namespace** argument.  
  
    -   **Adaptateur SOAP.** Cette carte traite les en-têtes SOAP et remplit les propriétés de contexte de message BizTalk répertoriées dans le tableau suivant.  
  
        |Propriétés|  
        |----------------|  
        |**Nom = feuille de route**|  
        |**Namespace = http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**|  
  
        > [!NOTE]
        >  Par défaut, l’adaptateur SOAP utilise le nom racine du schéma nommé Itinerary.xsd (ce schéma est utilisé pour générer l’en-tête SOAP d’itinéraire ESB) comme contexte BizTalk **nom** argument et qu’il utilise l’espace de noms de l’en-tête SOAP, comme le Contexte de BizTalk **Namespace** argument.  
  
-   Il supprime la valeur d’itinéraire d’origine à partir du contexte de message.  
  
-   Il valide l’itinéraire et définit des propriétés spécifiques à prédéfinir des valeurs par défaut s’ils sont null dans l’itinéraire ; par exemple :  
  
    -   Si le compte de Service est inférieur à 1, le composant lève une exception.  
  
    -   Le composant définit les attributs d’itinéraire racine en utilisant les valeurs pour le compte de Service, l’identificateur (**Uuid**), l’heure de début (**BeginTime**), et s’il s’agit d’une demande unidirectionnelle ou bidirectionnelle (**IsRequestResponse**).  
  
    -   Le composant valide les services, définit les identificateurs, définit l’instance de service en cours (le service à traiter suivant) et valide les programmes de résolution associés.  
  
    -   Le composant définit le BizTalk Segment de l’itinéraire à l’aide des propriétés suivantes :  
  
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
        |**ServiceType**|La valeur **Orchestration** ou **de messagerie**|  
        |**IsRequestResponse**|La valeur **True** ou **False**|  
        |**ServiceState**|La valeur **en attente**|  
  
## <a name="esb-dispatcher-pipeline-component-process-steps"></a>Étapes du processus de composant Pipeline ESB répartiteur  
 Dans l’exemple illustré dans la Figure 1, le composant de pipeline ESB répartiteur exécute les étapes suivantes :  
  
-   Il gère l’exécution de toutes les étapes d’itinéraire de type **messagerie** et avance la route. Le composant ESB répartiteur est sensible à l’emplacement et exécute la logique en fonction de son emplacement dans le cycle de traitement messagerie, ce qui pourrait être **de réception entrant, d’envoi de transmission**, **envoyer le trafic entrant**, ou **De réception sortant**. Le composant de pipeline ESB répartiteur appelle ESB feuille de route des services de messagerie spécifiées dans le fichier Esb.config. Par défaut, les propriétés de configuration de ce composant pour le routage et la transformation sont associées avec les services suivants :  
  
    -   **Microsoft.Practices.ESB.Services.Transform.** Ce service exécute les mappages BizTalk par rapport à la charge utile d’un message entrant. Le service valide les exigences de transformation et met à jour les propriétés de contexte BizTalk qui contiennent le nom de spécification de document et le type de message. Le répartiteur ESB exécute ce service uniquement s’il s’agit du nom du service de transformation tel qu’il apparaît dans la propriété correspondante du composant de pipeline ESB répartiteur.  
  
    -   **Microsoft.Practices.ESB.Services.Routing.** Ce service utilise le programme de résolution et le fournisseur d’infrastructure d’adaptateurs pour définir les informations de routage de point de terminaison approprié. Le répartiteur ESB exécute ce service uniquement s’il s’agit du nom du service de routage tel qu’il apparaît dans la propriété correspondante du composant de pipeline ESB répartiteur.