---
title: "Modèles de routage de messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d95c5ba0-122f-4793-bfce-a95830dfe094
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a332a8ab942363ff5224f34149b345c9c7d40698
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-routing-patterns"></a>Modèles de routage de messages
Modèles de routage de messages définissent des recommandations éprouvées pour acheminer les messages vers son point de terminaison cible. Routage peut être le résultat d’une configuration statique, ou il peut être configuré dynamiquement selon un certain nombre de critères à l’aide d’un certain nombre de méthodes.  
  
## <a name="message-router"></a>Routeur de messages  
 Le modèle de routeur de messages détermine le destinataire du message basé sur un ensemble de conditions. Pour obtenir une description détaillée de ce modèle, consultez [routeur de messages](http://go.microsoft.com/fwlink/?LinkId=186844) ([http://go.microsoft.com/fwlink/?LinkId=186844](http://go.microsoft.com/fwlink/?LinkId=186844)) sur le site de modèles d’intégration d’entreprise.  
  
 L’implémentation de ce modèle dans le Concepteur d’itinéraire est une combinaison de le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] service de routage d’itinéraire et un programme de résolution de contenu unique. Le service de routage d’itinéraire est chargé pour la promotion de propriétés de routage des messages dans le contexte du message BizTalk de Microsoft ou pour le routage explicite d’un message.  
  
 Vous pouvez choisir le service de routage d’itinéraire fourni par le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] comme suit :  
  
-   Définir le service de routage d’itinéraire avec une extension messagerie à s’exécuter dans un pipeline BizTalk à l’aide du Concepteur d’itinéraire.  
  
-   Définir le service d’itinéraire de routage avec un extendeur de l’orchestration à exécuter en tant qu’orchestration à l’aide du Concepteur d’itinéraire qui effectue le routage à l’aide de ports d’envoi BizTalk.  
  
 Le programme de résolution associé au service de routage d’itinéraire détermine le destinataire du message, selon le contenu du message. Vous pouvez choisir à partir de la résolution de cette prise en charge en fonction du contenu routage fournies par le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], ou vous pouvez implémenter votre propre programme de résolution.  
  
 Pour obtenir un exemple d’implémentation de ce modèle dans le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], consultez les ressources suivantes :  
  
-   [Comment : résoudre un point de terminaison de Service à l’aide d’une recherche de clé de liaison de UDDI](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-binding-key-search.md)  
  
-   [Comment : résoudre un point de terminaison de Service à l’aide d’une recherche de catégorie UDDI](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-category-search.md)  
  
## <a name="content-based-router"></a>Routeur basé sur le contenu  
 Le modèle de routeur basé sur le contenu détermine le destinataire d’un message en fonction du contenu. Pour obtenir une description détaillée de ce modèle, consultez [routeur basé sur le contenu](http://go.microsoft.com/fwlink/?LinkId=186839) ([http://go.microsoft.com/fwlink/?LinkId=186839](http://go.microsoft.com/fwlink/?LinkId=186839)) sur le site de modèles d’intégration d’entreprise.  
  
 L’implémentation de ce modèle dans le Concepteur d’itinéraire est une combinaison de le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] service de routage d’itinéraire et un programme de résolution de contenu unique. Le service de routage d’itinéraire est chargé pour la promotion de propriétés de routage des messages dans le contexte du message BizTalk ou d’acheminer les messages de manière explicite.  
  
 Vous pouvez choisir le service de routage d’itinéraire fourni par le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] comme suit :  
  
-   Définir un service de routage d’itinéraire avec une extension messagerie à s’exécuter dans un pipeline BizTalk à l’aide du Concepteur d’itinéraire.  
  
-   Définir un service de routage d’itinéraire avec un extendeur de l’orchestration à exécuter en tant qu’orchestration à l’aide du Concepteur d’itinéraire, qui effectue le routage à l’aide de ports d’envoi BizTalk.  
  
-   Définir un service broker d’itinéraire avec une extension de messagerie service broker à s’exécuter dans un pipeline BizTalk à l’aide du Concepteur d’itinéraire.  
  
 Le programme de résolution associé au service de routage d’itinéraire détermine le destinataire du message basé sur le contenu du message. Vous pouvez choisir les programmes de résolution suivants cette prise en charge en fonction du contenu routage fournies par le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]:  
  
-   **Programme de résolution XPATH**. À l’aide de ce programme de résolution, vous pouvez acheminer le contenu du message à l’aide de requêtes XPATH.  
  
-   **Programme de résolution BRE**. À l’aide de ce programme de résolution, vous pouvez récupérer des informations de routage à partir du contenu du message à l’aide du moteur de règles BizTalk.  
  
-   **Programme de résolution de contexte de message**. À l’aide de ce programme de résolution, vous pouvez récupérer le contenu d’un message à partir du contexte de message BizTalk lorsqu’il est associé un [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] service broker d’itinéraire.  
  
    > [!NOTE]
    >  En plus des scénarios d’implémentation précédente, vous pouvez développer un programme de résolution personnalisé basé sur le contenu et la solution d’itinéraire de routage comme un service basé sur la messagerie ou basée sur une orchestration. Dans ce cas, vous devrez peut-être implémenter d’extendeurs pour le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] service de programme de résolution et de la feuille de route pour interagir avec le Concepteur d’itinéraire.  
  
 Par exemple de cette implémentation, consultez les ressources suivantes :  
  
-   [Installer et exécuter l’exemple de rampe d’entrée d’itinéraire](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)  
  
-   [Comment : implémenter en fonction du contenu routage à l’aide d’une entreprise règles de stratégie pour un Type connu](../esb-toolkit/apply-content-based-routing-using-business-rules-policy-for-known-message-type.md)  
  
-   [Comment : acheminer un Message basé sur le contexte du Message à l’aide d’une stratégie de règles d’entreprise](../esb-toolkit/dynamically-route-messages-based-on-message-context-using-business-rules-policy.md)  
  
## <a name="routing-slip"></a>Bordereau de routage  
 Le modèle de routage décrit un scénario dans lequel un message doit être routé via une série de composants dans un ordre prédéfini, qui ne peut pas être connu au moment du design. Pour obtenir une description détaillée de ce modèle, consultez [routage](http://go.microsoft.com/fwlink/?LinkId=186840) ([http://go.microsoft.com/fwlink/?LinkId=186840](http://go.microsoft.com/fwlink/?LinkId=186840)) sur le site de modèles d’intégration d’entreprise.  
  
 L’implémentation de ce modèle est fournie par le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]; son implémentation varie selon le type d’application cliente qui envoie un message pour le traitement basé sur l’itinéraire :  
  
-   **Proxy de service**. Avec ce type d’application, vous devez configurer le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] rampe d’entrée avec le composant de pipeline du sélecteur de feuille de route et associer un résolveur d’itinéraire pour sélectionner les [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] itinéraire. Les propriétés d’itinéraire peuvent être configurées en tant que propriétés statiques à l’aide du programme de résolution d’itinéraire, ou ils peuvent être configurés en tant que propriétés dynamiques à l’aide du programme de résolution de moteur de règles BizTalk et BRI.  
  
-   **Client avancé**. Avec ce type d’application, vous devez configurer le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] rampe d’entrée avec le composant de pipeline sélecteur d’itinéraire et le programme de résolution d’itinéraire statique. L’application cliente envoie un message avec un en-tête d’itinéraire de référence, qui contient le nom d’itinéraire, une version et un identificateur de suivi.  
  
-   **Client Adaptive**. Avec ce type d’application, l’application cliente appelle le service de résolution, qui, à son tour, identifie la référence d’itinéraire en passant de l’état du client comme un message de demande. Si l’itinéraire est résolu, l’application cliente envoie un message avec les références d’itinéraire de la même façon que dans le scénario de client avancé précédent.  
  
 Pour plus d’informations sur l’implémentation de ce modèle, consultez les ressources suivantes :  
  
-   [Comment : sélectionner un itinéraire à l’aide d’une stratégie de règles d’entreprise](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [Comment : transformer un Message et router le Message résultant à un emplacement de fichier à l’aide d’un bon d’itinéraire de routage](../esb-toolkit/transform-message-and-route-the-message-to-a-location-using-itinerary-routing.md)  
  
    > [!NOTE]
    >  En plus des scénarios précédents, vous pouvez développer un programme de résolution personnalisé d’itinéraire et les services de routage d’itinéraire. Vous pouvez envisager la création d’extensions de concepteur pour des services personnalisés d’itinéraire pour une utilisation dans le Concepteur d’itinéraire.  
  
## <a name="scatter-gather"></a>Ventilation-regroupement  
 Modèle de ventilation-regroupement permet des messages à envoyer à plusieurs destinataires et agréger leurs réponses ; Cela entraîne un seul message. Pour obtenir une description détaillée de ce modèle, consultez [ventilation-regroupement](http://go.microsoft.com/fwlink/?LinkId=186841) ([http://go.microsoft.com/fwlink/?LinkId=186841](http://go.microsoft.com/fwlink/?LinkId=186841)) sur le site de modèles d’intégration d’entreprise.  
  
 Pour obtenir un exemple d’implémentation de ce modèle, consultez la [l’installation et l’exécution de l’exemple de ventilation-regroupement](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md) exemple.  
  
## <a name="recipient-list"></a>Liste de destinataires  
 Le modèle de liste de destinataires traite la solution du scénario dans lequel un message est acheminé vers un ou plusieurs destinataires. La liste de destinataires peut être soit définies de manière statique (c'est-à-dire qu’elle dispose d’une liste fixe de destinataires) ou dynamique. Pour obtenir une description détaillée de ce modèle, consultez [la liste de destinataires](http://go.microsoft.com/fwlink/?LinkId=186842) ([http://go.microsoft.com/fwlink/?LinkId=186842](http://go.microsoft.com/fwlink/?LinkId=186842)) sur le site de modèles d’intégration d’entreprise.  
  
 L’implémentation de ce modèle dans le Concepteur d’itinéraire est une combinaison de le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] service de routage d’itinéraire et plusieurs programmes de résolution. Le service de routage d’itinéraire est chargé pour le clonage d’un message et ensuite à l’aide de ses propriétés de contexte du message BizTalk explicitement router un message.  
  
 Vous pouvez choisir le service de routage d’itinéraire fourni par le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] comme suit :  
  
-   Définir le service de routage d’itinéraire avec une extension messagerie à exécuter dans le pipeline BizTalk à l’aide du Concepteur d’itinéraire.  
  
-   Définir le service de routage d’itinéraire avec une extension messagerie à exécuter en tant qu’orchestration à l’aide du Concepteur d’itinéraire, qui effectue le routage à l’aide de ports d’envoi BizTalk.  
  
 Le programme de résolution associé au service de routage d’itinéraire détermine le destinataire du message basé sur le contenu du message. Vous pouvez choisir l’ensemble des programmes de résolution fournis par le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] pour implémenter ce scénario. Pour plus d’informations sur l’implémentation de ce modèle, consultez la ressource suivante :  
  
-   [Comment : router un Message unique à plusieurs destinataires à l’aide d’un bon d’itinéraire de routage](../esb-toolkit/route-a-single-message-to-multiple-recipients-using-an-itinerary-routing-slip.md)  
  
## <a name="splitter"></a>Splitter  
 Le modèle de séparation résout le problème lorsqu’un message unique doit être fractionné en plusieurs messages. Pour obtenir une description détaillée de ce modèle, consultez [fractionnement](http://go.microsoft.com/fwlink/?LinkId=186843) ([http://go.microsoft.com/fwlink/?LinkId=186843](http://go.microsoft.com/fwlink/?LinkId=186843)) sur le site de modèles d’intégration d’entreprise. Pour plus d’informations sur l’implémentation de ce modèle, consultez la ressource suivante :  
  
-   [Comment : fractionner un échange et de router les Messages résultants vers plusieurs emplacements de fichier à l’aide d’itinéraires distinctes](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md)