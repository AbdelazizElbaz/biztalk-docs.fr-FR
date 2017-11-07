---
redirect_url: /biztalk/core/creating-tibco-rendezvous-receive-handlers/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: b93e747cdc665fb5a8407ca2a3d052b880236378
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="tibco-rendezvous-events-and-receive-locations"></a>Emplacements de réception et événements Rendezvous TIBCO
Un système TIBCO Rendezvous peut envoyer des messages vers le nom d'objet de son choix. Le concept de *événement* est la génération de messages par d’autres programmes TIBCO Rendezvous.  
  
 Les étapes suivantes décrivent le cycle de vie d'un emplacement de réception :  
  
1.  création d'un emplacement de réception ;  
  
2.  association de l'emplacement de réception à un hôte ;  
  
3.  liaison de l'emplacement de réception à une orchestration ;  
  
4.  activation de l'emplacement de réception ;  
  
5.  réception de messages sur l'emplacement de réception.  
  
> [!IMPORTANT]
>  Le nom de chaque emplacement de réception doit être unique. Deux emplacements de réception ne peuvent pas avoir le même nom au sein d'un même déploiement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
> [!IMPORTANT]
>  Il est recommandé de définir des listes de contrôle d'accès renforcées dans l'emplacement de dépôt des emplacements de réception. Par exemple, vous devez définir des listes de contrôle d'accès renforcées pour le répertoire dans lequel l'emplacement de réception des fichiers sélectionne des messages, afin que seuls les utilisateurs autorisés puissent déposer des messages dans cet emplacement.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de gestionnaires de réception TIBCO Rendezvous](../core/creating-tibco-rendezvous-receive-handlers.md)