---
title: "Propriétés de contexte du Message BizTalk Server (gestionnaires d’envoi) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a065ba89-9fdb-47dc-9021-fb95cf347cdc
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0504e13115229f1325938e8ca48acc17fa5bc1d
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="biztalk-server-message-context-properties-send-handlers"></a>Propriétés de contexte du Message BizTalk Server (gestionnaires d’envoi)
En plus de la charge de message, les informations supplémentaires composant un message doivent être accessibles à partir de l'orchestration BizTalk Server au moment de l'exécution.  
  
## <a name="tibco-rv-message-information-promoted-as-message-context-properties"></a>Informations de message TIBCO RV promues en tant que propriétés de contexte  
  
|Identification des données|Type|Routable|Emplacement d'envoi|  
|-------------------------|----------|--------------|-------------------|  
|Objet d'envoi|chaîne|Oui|L'orchestration spécifie l'objet d'envoi TIBCO Rendezvous. Valeur par défaut est Null. Obligatoire, sauf si un objet par défaut est spécifié dans la configuration du port.|  
|Objet de réponse|chaîne|Oui|L'orchestration fournit un objet pour les messages de réponse lorsque c'est approprié. Valeur par défaut est Null.|  
  
## <a name="getting-a-tibco-reply"></a>Obtention d'une réponse TIBCO  
 **Question :** en quoi l’adaptateur BizTalk pour TIBCO Rendezvous de lecture de manipuler l’objet de réponse à l’intérieur d’une orchestration afin que vous pouvez l’utiliser comme objet d’envoi pour la réponse ? Comment l'adaptateur obtient-il le contexte d'un message entrant de Rendezvous ?  
  
 **Réponse :** l’objet de réponse est renseigné dans le contexte du message entrant et l’orchestration peut le lire. Si l'orchestration fournit finalement une réponse, il peut utiliser la valeur pour définir l'objet d'envoi du message de réponse.  
  
1.  Dans un projet BizTalk Server, ajoutez une référence à <répertoire d'installation>\TibcoRV\bin\Microsoft.BizTalk.Adapters.TibRV.Properties.dll.  
  
2.  Dans l'orchestration (quelque part entre la forme Réception qui remet le message Rendezvous entrant et la forme forme Envoi qui envoie la réponse), ajoutez à la réponse que vous avez construite une forme de construction/d'affectation de message (ou une forme Expression) pour obtenir quelque chose comme l'exemple suivant :  
  
    ```  
    OutgoingMsg(Rendezvous.SendSubject) = IncomingMsg  
    (Rendezvous.ReplySubject);  
    ```  
## <a name="management-assembly"></a>Assembly de gestion
TIBCO Rendezvous n'inclut pas de référentiels de métadonnées. Par ailleurs, l'assembly de gestion de l'adaptateur Microsoft BizTalk pour TIBCO Rendezvous n'inclut pas de fonctionnalités de navigation ou de génération de schémas. Vous devez donc fournir un schéma à BizTalk Server. Pour plus d’informations, consultez [installation, les schémas et les limitations](../core/installing-biztalk-adapter-for-tibco-rendezvous.md).
  
 L'adaptateur BizTalk pour TIBCO Rendezvous inclut un schéma avec des types prédéfinis. L'adaptateur utilise ces types lors de la génération de messages pour certains types de données spécifiques (tableaux).

  
## <a name="see-also"></a>Voir aussi  
 [Mappage de Type de données pour les gestionnaires d’envoi dans TIBCO Rendezvous](../core/data-type-mapping-for-send-handlers-in-tibco-rendezvous.md)   
 [Création de gestionnaires d’envoi TIBCO Rendezvous](../core/creating-tibco-rendezvous-send-handlers.md)