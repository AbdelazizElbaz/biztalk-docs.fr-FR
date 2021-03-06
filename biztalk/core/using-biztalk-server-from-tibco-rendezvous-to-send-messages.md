---
redirect_url: /biztalk/core/using-tibco-rendezvous-send-ports-from-biztalk-server/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: d4a4f4fce200089db0e29d09b3ea49af00f3792f
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="using-biztalk-server-from-tibco-rendezvous-to-send-messages"></a>Utilisation de BizTalk Server à partir de TIBCO Rendezvous pour envoyer des messages
L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous utilise l'API asynchrone (Transport.Send). Vous pouvez spécifier le type de message envoyé par l'adaptateur à l'aide d'une propriété de contexte de message :  
  
-   **Structuré**: l’adaptateur génère un message structuré TIBRVMSG_MSG, basé sur les données XML reçues de BizTalk Server. (*)  
  
 Si BizTalk Server envoie un message avec des champs dont le nom comporte plus de 127 caractères, l'adaptateur BizTalk pour TIBCO Rendezvous tronque les noms en fonction de la taille de nom de champ maximale pour TIBCO Rendezvous (127).  
  
 Si une propriété `reply subject name` est fournie, elle est utilisée pour définir l'objet de réponse sur le message TIBCO Rendezvous. Il est supposé qu'un port de réception est défini pour écouter la réponse et la transmettre à BizTalk Server, ou qu'un autre programme TIBCO Rendezvous traite la réponse.  
  
 Le triplet (service, démon, réseau) constitue la configuration de transport. Une configuration de transport vide (par défaut) entraîne l'envoi d'un message via l'objet de transport par défaut.  
  
 Si la page de code n'est pas spécifiée, l'adaptateur utilise le codage UTF-8 (page de code 65001). Les messages certifiés ne sont pas pris en charge du côté transmetteur.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de TIBCO Rendezvous](../core/tibco-rendezvous-concepts.md)   
 [Création de gestionnaires d’envoi TIBCO Rendezvous](../core/creating-tibco-rendezvous-send-handlers.md)