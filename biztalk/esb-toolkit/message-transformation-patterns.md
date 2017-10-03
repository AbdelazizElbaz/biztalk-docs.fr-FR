---
title: "Modèles de Transformation de message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aef41642-d33b-4878-be65-ef336530647f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: badfb450b51aebbdf81b2beccdeac98fc549bcb0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-transformation-patterns"></a>Modèles de Transformation de messages
Modèles de transformation de messages définissent des recommandations éprouvées pour la transformation des messages pour un traitement supplémentaire ou pour correspondre au format de document attendu du service auquel le message sera envoyé. Un message peut nécessiter la transformation, car la structure du message reçu n’est pas dans la norme attendue ou parce que le message doit être converti à partir d’un format non standard au format XML.  
  
## <a name="message-translator"></a>Convertisseur de messages  
 Le modèle de conversion de messages définit une solution pour la communication entre les systèmes qui utilisent des formats de données incompatibles. Par exemple, une application cliente peut envoyer un message de demande de fichier plat qui doit être converti au format XML avant d’effectuer un traitement supplémentaire. Pour obtenir une description détaillée de ce modèle, consultez [convertisseur de messages](http://go.microsoft.com/fwlink/?LinkId=186845) ([http://go.microsoft.com/fwlink/?LinkId=186845](http://go.microsoft.com/fwlink/?LinkId=186845)) sur le site de modèles d’intégration d’entreprise.  
  
 L’implémentation de ce modèle dans le Concepteur d’itinéraire est une combinaison de le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] service de transformation et d’un seul programme de résolution. Le service de transformation d’itinéraire est chargé de transformer un message à l’aide des propriétés de programme de résolution qui définissent les artefacts requis pour la transformation. L’implémentation d’un programme de résolution est chargée de fournir des paramètres de transformation, qui peuvent être définis de manière statique ou dynamique, selon la configuration du programme de résolution.  
  
 Pour un exemple d’implémentation du modèle de conversion de messages, consultez les ressources suivantes :  
  
-   [Installer et exécuter l’exemple de rampe d’entrée d’itinéraire](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)  
  
-   [Comment : transformer un Message et un itinéraire vers un point de terminaison de Service à l’aide d’un modèle d’échange de Message demande-réponse](../esb-toolkit/transform-message-and-route-to-service-endpoint-using-request-response-message.md)  
  
## <a name="normalizer"></a>Normalisation  
 Le modèle de normalisation est une extension du modèle de Transformation de modèle de données. Ce modèle définit une solution dans laquelle les messages reçus à partir de plusieurs sources sont sémantiquement équivalentes, mais les messages arrivent dans des formats différents. Pour obtenir une description détaillée de ce modèle, consultez [normalisation](http://go.microsoft.com/fwlink/?LinkId=186847) ([http://go.microsoft.com/fwlink/?LinkId=186847](http://go.microsoft.com/fwlink/?LinkId=186847)) sur le site de modèles d’intégration d’entreprise.  
  
 L’implémentation de ce modèle dans le Concepteur d’itinéraire est une combinaison de le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] service de transformation et d’un seul programme de résolution. Le service de transformation d’itinéraire est chargé de transformer un message à l’aide des propriétés de programme de résolution qui définissent les artefacts requis pour la transformation. L’implémentation d’un programme de résolution est responsable de la résolution dynamiquement de la carte Microsoft BizTalk appropriée pour un type de message.  
  
 Pour un exemple d’implémentation du modèle de normalisation, consultez le [l’installation et l’exécution de l’exemple de rampe d’entrée d’itinéraire](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).  
  
## <a name="content-enricher"></a>Contenu enrichisseur  
 Le modèle de contenu enrichisseur définit une solution dans lequel un message reçu ne peut pas inclure toutes les données requises pour le système cible pour traiter de manière appropriée le message. Par exemple, le service d’envoi peut inclure un code postal sans un code d’état redondantes, mais le service de réception attend un message qui inclut un code d’état et un code postal ; données supplémentaires sont requises avant que le service de réception puisse traiter le message reçu. Pour obtenir une description détaillée de ce modèle, consultez [enrichisseur contenu](http://go.microsoft.com/fwlink/?LinkId=186848) ([http://go.microsoft.com/fwlink/?LinkId=186848](http://go.microsoft.com/fwlink/?LinkId=186848)) sur le site de modèles d’intégration d’entreprise.  
  
 Pour un exemple d’implémentation du modèle de contenu enrichisseur, consultez le [installer et exécuter l’exemple d’enrichissement de Message](../esb-toolkit/installing-and-running-the-message-enrichment-sample.md) application.