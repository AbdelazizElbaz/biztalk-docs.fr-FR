---
redirect_url: /biztalk/core/installing-biztalk-adapter-for-tibco-rendezvous/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 4e4209c75ca52585c0a11141dbe0d9841fa6a5ba
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="schema-generation-in-the-adapter"></a>Génération de schémas dans l'adaptateur
Un système TIBCO Rendezvous ne comporte pas de référentiel des types de messages. La construction et l'analyse d'un message sont enfouies au niveau de l'application Rendezvous. À cause de cette limitation, l'adaptateur Microsoft BizTalk pour TIBCO Rendezvous n'est pas en mesure d'offrir des fonctionnalités de génération de schémas.  
  
## <a name="writing-schemas"></a>Écriture de schémas  
 Vous devez écrire un schéma et utiliser **ajouter un élément existant** dans Visual Studio pour l’importer pour une utilisation dans les orchestrations. Les schémas sont essentiels aux outils de développement BizTalk Server et à l'intégration dans Visual Studio. Les développeurs BizTalk Server peuvent choisir de fournir un schéma complet, minimum ou une version intermédiaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Bien démarrer](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)