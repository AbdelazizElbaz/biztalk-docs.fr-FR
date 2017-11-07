---
redirect_url: /biztalk/core/using-tibco-rendezvous-receive-ports-from-biztalk-server/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: b1738a0933b5f570edfd882778e50ebf7e2ca730
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="using-biztalk-server-from-tibco-rendezvous-to-receive-messages"></a>Utilisation de BizTalk Server à partir de TIBCO Rendezvous pour recevoir des messages
L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous distribue des événements à partir d'une file d'attente sur plusieurs threads. Un emplacement de réception BizTalk Server est associé à une file d'attente TIBCO Rendezvous et à son pool de threads du répartiteur.  
  
## <a name="memory-use-and-errors"></a>Utilisation de la mémoire et erreurs  
 L'adaptateur surveille les ressources utilisées lors du traitement d'événements. Si l'utilisation de la mémoire dépasse la limite supérieure, l'adaptateur arrête la distribution des événements jusqu'à ce que la consommation de mémoire atteigne la limite inférieure. Notez que des messages TIBCO Rendezvous non certifiés peuvent ainsi être manqués (un utilisateur de TIBCO RV dispose de 60 secondes pour supprimer des messages dans une file d'attente). Cette perte de données est signalée en tant qu'erreur. Si l'adaptateur reçoit un message d'avertissement NO_MEMORY en provenance du système TIBCO Rendezvous, cela signifie que des messages ont déjà été perdus.  
  
 L'adaptateur BizTalk pour TIBCO Rendezvous conserve un état et exécute des tâches de différentes façons en fonction de cet état. Si le moteur de messagerie BizTalk renvoie une erreur et si l'adaptateur est configuré en tant qu'écouteur certifié, le moteur la signale à TIBCO Rendezvous afin qu'il puisse renvoyer le message.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de TIBCO Rendezvous](../core/tibco-rendezvous-concepts.md)   
 [Création de gestionnaires de réception TIBCO Rendezvous](../core/creating-tibco-rendezvous-receive-handlers.md)