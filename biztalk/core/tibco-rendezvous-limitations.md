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
# <a name="tibco-rendezvous-limitations"></a><span data-ttu-id="88fb1-101">Restrictions en relation avec TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="88fb1-101">TIBCO Rendezvous Limitations</span></span>
<span data-ttu-id="88fb1-102">Dans TIBCO Rendezvous, l'unicité des noms de champ n'est pas garantie.</span><span class="sxs-lookup"><span data-stu-id="88fb1-102">In TIBCO Rendezvous, field name uniqueness is not guaranteed.</span></span> <span data-ttu-id="88fb1-103">Si un message TIBCO Rendezvous contient deux noms de champ identiques, le fichier XML qui en résulte n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="88fb1-103">If a TIBCO Rendezvous message contains two field names that are the same, the resulting XML is not valid.</span></span>  
  
 <span data-ttu-id="88fb1-104">Les autres limitations suivantes s'appliquent :</span><span class="sxs-lookup"><span data-stu-id="88fb1-104">Other limitations include the following:</span></span>  
  
-   <span data-ttu-id="88fb1-105">Il n'est pas possible de classer/trier les champs.</span><span class="sxs-lookup"><span data-stu-id="88fb1-105">Field ordering/sorting is not provided.</span></span>  
  
-   <span data-ttu-id="88fb1-106">Selon la documentation de TIBCO Rendezvous, les caractères non imprimables ne sont pas utilisés dans les noms d'objet. Il reste toutefois possible que de tels caractères soient utilisés.</span><span class="sxs-lookup"><span data-stu-id="88fb1-106">According to TIBCO Rendezvous documentation, non-printable characters are not used in subject names; however, it is still possible that such characters are used.</span></span> <span data-ttu-id="88fb1-107">L'adaptateur BizTalk pour TIBCO Rendezvous ne prend pas en charge les noms d'objet contenant ces caractères.</span><span class="sxs-lookup"><span data-stu-id="88fb1-107">BizTalk Adapter for TIBCO Rendezvous does not support subject names containing those characters.</span></span>  
  
-   <span data-ttu-id="88fb1-108">La connexion sécurisée aux démons n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="88fb1-108">Secure connection to daemons is not supported.</span></span>  
  
-   <span data-ttu-id="88fb1-109">Les types de données personnalisés ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="88fb1-109">Custom data types are not supported.</span></span>  
  
-   <span data-ttu-id="88fb1-110">La messagerie certifiée n'est pas prise en charge du côté transmetteur.</span><span class="sxs-lookup"><span data-stu-id="88fb1-110">Certified Messaging is not supported on the transmit side.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88fb1-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88fb1-111">See Also</span></span>  
 <span data-ttu-id="88fb1-112">[Concepts de TIBCO Rendezvous](../core/tibco-rendezvous-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="88fb1-112">[TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md) </span></span>  
 [<span data-ttu-id="88fb1-113">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="88fb1-113">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)