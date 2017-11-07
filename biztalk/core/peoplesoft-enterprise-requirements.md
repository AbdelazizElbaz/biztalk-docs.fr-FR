---
redirect_url: /biztalk/core/architecture-of-biztalk-adapter-for-peoplesoft-enterprise/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: a277c5f5588a9455119b96f7c600dbadccffb8ac
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="peoplesoft-enterprise-requirements"></a>Configuration requise de PeopleSoft Enterprise

## <a name="send-handler-requirements"></a>Configuration requise du Gestionnaire d’envoi  
 L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise inclut une interface de composant personnalisée accessible via une API Java. Un objet interface de composant personnalisée (`GET_CI_INFO`) est déployé dans le système PeopleSoft à l'aide des outils PeopleSoft pour fournir les informations de métadonnées requises par l'adaptateur BizTalk pour PeopleSoft Enterprise. Pour plus d’informations, consultez [cartes d’installer des Applications d’entreprise](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md).  
  
 Téléchargement de l’interface de composant personnalisée est une occurrence unique. Installé avec le produit, ce fichier (`GET_CI_INFO.pc`) doit être installé avant d'utiliser l'adaptateur pour explorer les interfaces de composant. Vous devez avoir accès au Concepteur d’applications PeopleSoft. L’application de concepteur d’applications pas nécessairement se trouver sur l’ordinateur BizTalk Server. Le Concepteur d'applications permet de télécharger l'interface de composant personnalisée sur l'ordinateur PeopleSoft que vous utilisez.  
  
 Vous devez avoir accès à l’ordinateur PeopleSoft, car vous devez définir la variable d’environnement CLASSPATH (ou définir les informations dans le **propriétés du Transport** écran) pour pointer vers de PeopleSoft `PSJOA/psjoa.jar` fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Bien démarrer](../core/getting-started-with-biztalk-adapter-for-peoplesoft-enterprise.md)   
 