---
title: "À l’aide de composants de prise en charge du Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df0346ea-15d4-49c5-98d8-f9ec06f4e036
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6313a337e8527f3fb275f7c15745a5a7f6552151
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-pipeline-support-components"></a>À l’aide de composants de prise en charge du Pipeline
La [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] inclut les composants suivants :  
  
-   **Sélecteur d’itinéraire d’ESB**. Vous pouvez utiliser ce composant sur le côté réception (dans un pipeline de réception) pour sélectionner une feuille de route côté serveur pour un message à suivre. Pour plus d’informations, consultez [le composant de sélecteur de feuille de route ESB](../esb-toolkit/the-esb-itinerary-selector-component.md).  
  
-   **Feuille de route ESB**. Vous pouvez utiliser ce composant sur le côté réception (dans un pipeline de réception) pour promouvoir les propriétés de métadonnées ESB des en-têtes SOAP dans le contexte du message. Pour plus d’informations, consultez [le composant d’itinéraire ESB](../esb-toolkit/the-esb-itinerary-component.md).  
  
-   **Redirecteur d’itinéraire d’ESB**. Pour plus d’informations, consultez [le composant de redirecteur ESB itinéraire](../esb-toolkit/the-esb-itinerary-forwarder-component.md).  
  
-   **Cache d’itinéraire d’ESB**. Vous pouvez utiliser ce composant pour les itinéraires de cache et les réappliquer les messages de réponse reçus par les ports d’envoi de sollicitation-réponse. Pour plus d’informations, consultez [le composant d’itinéraire ESB](../esb-toolkit/the-esb-itinerary-component.md).  
  
-   **ESB JMS décodeur**. Vous pouvez utiliser ce composant sur le côté réception (dans un emplacement de réception) d’une orchestration ou un port d’envoi pour analyser les en-têtes IBM JMS (MQRFH2) et de les conserver en tant que propriétés de contexte. Vous pouvez ensuite accéder à ces propriétés de contexte et les modifier dans la même façon que d’autres propriétés de contexte de BizTalk. Pour plus d’informations, consultez [l’encodeur de JMS ESB et les composants décodeur](../esb-toolkit/the-esb-jms-encoder-and-decoder-components.md).  
  
-   **Encodeur de ESB JMS**. Vous pouvez utiliser ce composant dans un port d’envoi pour écrire les en-têtes IBM JMS (MQRFH2) pour les messages. Pour plus d’informations, consultez [l’encodeur de JMS ESB et les composants décodeur](../esb-toolkit/the-esb-jms-encoder-and-decoder-components.md).  
  
-   **ESB ajouter Namespace**. Vous pouvez utiliser ce composant dans un emplacement de réception ou un port d’envoi pour ajouter des espaces de noms à des documents XML. Pour plus d’informations, consultez [le Namespace d’ajouter ESB et supprimer des composants Namespace](../esb-toolkit/the-esb-add-namespace-and-remove-namespace-components.md).  
  
-   **ESB supprimer Namespace**. Vous pouvez utiliser ce composant dans un emplacement de réception ou un port d’envoi à supprimer les espaces de noms de documents XML. Pour plus d’informations, consultez [le Namespace d’ajouter ESB et supprimer des composants Namespace](../esb-toolkit/the-esb-add-namespace-and-remove-namespace-components.md).  
  
-   **ESB Exception encodeur**. Vous pouvez utiliser ce composant pour envoyer des messages d’erreur dans le système de fichiers, Microsoft InfoPath, ou Microsoft SharePoint. Ce composant fait partie de l’exception d’ESB mécanisme de gestion, et elle normalise et enrichit toutes les exceptions traitées par un port d’envoi. Le composant sérialise les informations sur les exceptions (y compris les messages persistants incorporés et les propriétés de contexte) dans un format canonique afin que tous les contenus des messages et l’exception lui-même sont disponibles.  
  
-   **Transformation d’ESB**. Vous pouvez utiliser ce composant pour transformer le message d’un format vers un autre en spécifiant le mappage BizTalk.  
  
-   **Dispositif de suivi BAM d’ESB**. Vous pouvez utiliser ce composant d’intercepter le message d’erreur émis à partir de l’encodeur d’Exception ESB et d’insérer les données dans le message dans la table d’importation principale BAM (en utilisant le flux d’événements BAM dans le pipeline). Ce composant fait partie de l’exception d’ESB mécanisme de gestion.  
  
-   **Répartiteur d’ESB**. Vous pouvez utiliser ce composant dans un emplacement de réception (pipeline entrant) pour définir dynamiquement les propriétés d’emplacement de point de terminaison pour les messages sortants. Vous pouvez également utiliser ce composant dans le pipeline d’envoi pour exécuter les services de messagerie d’itinéraire. Pour plus d’informations, consultez [le composant de répartiteur ESB](../esb-toolkit/the-esb-dispatcher-component.md).  
  
-   **Répartiteur d’ESB désassembler**. Vous pouvez utiliser ce composant dans un emplacement de réception (pipeline entrant) pour définir dynamiquement les propriétés d’emplacement de point de terminaison pour les messages sortants. Le comportement de ce composant est semblable au composant ESB répartiteur, à ceci près qu’il transforme le message de résultat (si vous spécifiez une valeur pour le **MapName** propriété). Le message passe par le désassembleur XML, ce qui promeut les propriétés et les types de messages. Le composant de désassemblage de répartiteur ESB prend également en charge la répartition par lot de plusieurs messages à différents points de terminaison. Pour plus d’informations, consultez [l’ESB répartiteur désassembler composant](../esb-toolkit/the-esb-dispatcher-disassemble-component.md).