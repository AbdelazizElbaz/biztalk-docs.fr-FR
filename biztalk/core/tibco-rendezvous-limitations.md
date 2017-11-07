---
redirect_url: /biztalk/core/installing-biztalk-adapter-for-tibco-rendezvous/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: bcccc92430a73685ced9ad7259d8ec57dfc450b8
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="tibco-rendezvous-limitations"></a>Restrictions en relation avec TIBCO Rendezvous
Dans TIBCO Rendezvous, l'unicité des noms de champ n'est pas garantie. Si un message TIBCO Rendezvous contient deux noms de champ identiques, le fichier XML qui en résulte n'est pas valide.  
  
 Les autres limitations suivantes s'appliquent :  
  
-   Il n'est pas possible de classer/trier les champs.  
  
-   Selon la documentation de TIBCO Rendezvous, les caractères non imprimables ne sont pas utilisés dans les noms d'objet. Il reste toutefois possible que de tels caractères soient utilisés. L'adaptateur BizTalk pour TIBCO Rendezvous ne prend pas en charge les noms d'objet contenant ces caractères.  
  
-   La connexion sécurisée aux démons n'est pas prise en charge.  
  
-   Les types de données personnalisés ne sont pas pris en charge.  
  
-   La messagerie certifiée n'est pas prise en charge du côté transmetteur.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de TIBCO Rendezvous](../core/tibco-rendezvous-concepts.md)   
 [Bien démarrer](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)