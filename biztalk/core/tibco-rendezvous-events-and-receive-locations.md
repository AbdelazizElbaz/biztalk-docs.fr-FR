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
# <a name="tibco-rendezvous-events-and-receive-locations"></a><span data-ttu-id="b388b-101">Emplacements de réception et événements Rendezvous TIBCO</span><span class="sxs-lookup"><span data-stu-id="b388b-101">TIBCO Rendezvous Events and Receive Locations</span></span>
<span data-ttu-id="b388b-102">Un système TIBCO Rendezvous peut envoyer des messages vers le nom d'objet de son choix.</span><span class="sxs-lookup"><span data-stu-id="b388b-102">Any TIBCO Rendezvous system can send messages to their subject name of choice.</span></span> <span data-ttu-id="b388b-103">Le concept de *événement* est la génération de messages par d’autres programmes TIBCO Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="b388b-103">The concept of *event* is the generation of messages by other TIBCO Rendezvous programs.</span></span>  
  
 <span data-ttu-id="b388b-104">Les étapes suivantes décrivent le cycle de vie d'un emplacement de réception :</span><span class="sxs-lookup"><span data-stu-id="b388b-104">The following steps describe the life cycle of a receive location:</span></span>  
  
1.  <span data-ttu-id="b388b-105">création d'un emplacement de réception ;</span><span class="sxs-lookup"><span data-stu-id="b388b-105">Receive location is created.</span></span>  
  
2.  <span data-ttu-id="b388b-106">association de l'emplacement de réception à un hôte ;</span><span class="sxs-lookup"><span data-stu-id="b388b-106">Receive location is associated with a host.</span></span>  
  
3.  <span data-ttu-id="b388b-107">liaison de l'emplacement de réception à une orchestration ;</span><span class="sxs-lookup"><span data-stu-id="b388b-107">Receive location is bound to an orchestration.</span></span>  
  
4.  <span data-ttu-id="b388b-108">activation de l'emplacement de réception ;</span><span class="sxs-lookup"><span data-stu-id="b388b-108">Receive location is enabled.</span></span>  
  
5.  <span data-ttu-id="b388b-109">réception de messages sur l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="b388b-109">Receive location receives messages.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b388b-110">Le nom de chaque emplacement de réception doit être unique.</span><span class="sxs-lookup"><span data-stu-id="b388b-110">Each receive location must have a unique name.</span></span> <span data-ttu-id="b388b-111">Deux emplacements de réception ne peuvent pas avoir le même nom au sein d'un même déploiement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b388b-111">Two receive locations cannot have the same name in the same [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b388b-112">Il est recommandé de définir des listes de contrôle d'accès renforcées dans l'emplacement de dépôt des emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="b388b-112">It is recommended that you set strong access control lists (ACL) in the receive locations drop locations.</span></span> <span data-ttu-id="b388b-113">Par exemple, vous devez définir des listes de contrôle d'accès renforcées pour le répertoire dans lequel l'emplacement de réception des fichiers sélectionne des messages, afin que seuls les utilisateurs autorisés puissent déposer des messages dans cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="b388b-113">For example, you must set strong ACLs for the directory where the file receive location picks up messages, so that only authorized users can drop messages in this location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b388b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b388b-114">See Also</span></span>  
 [<span data-ttu-id="b388b-115">Création de gestionnaires de réception TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="b388b-115">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)