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
# <a name="schema-generation-in-the-adapter"></a><span data-ttu-id="2f90f-101">Génération de schémas dans l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="2f90f-101">Schema Generation in the Adapter</span></span>
<span data-ttu-id="2f90f-102">Un système TIBCO Rendezvous ne comporte pas de référentiel des types de messages.</span><span class="sxs-lookup"><span data-stu-id="2f90f-102">A TIBCO Rendezvous system does not include a message types repository.</span></span> <span data-ttu-id="2f90f-103">La construction et l'analyse d'un message sont enfouies au niveau de l'application Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="2f90f-103">All the message construction and parsing is buried at the Rendezvous application level.</span></span> <span data-ttu-id="2f90f-104">À cause de cette limitation, l'adaptateur Microsoft BizTalk pour TIBCO Rendezvous n'est pas en mesure d'offrir des fonctionnalités de génération de schémas.</span><span class="sxs-lookup"><span data-stu-id="2f90f-104">Because of this limitation, Microsoft BizTalk Adapter for TIBCO Rendezvous cannot provide schema-generation capabilities.</span></span>  
  
## <a name="writing-schemas"></a><span data-ttu-id="2f90f-105">Écriture de schémas</span><span class="sxs-lookup"><span data-stu-id="2f90f-105">Writing Schemas</span></span>  
 <span data-ttu-id="2f90f-106">Vous devez écrire un schéma et utiliser **ajouter un élément existant** dans Visual Studio pour l’importer pour une utilisation dans les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="2f90f-106">You must write a schema and use **Add Existing Item** in Visual Studio to import it for use in orchestrations.</span></span> <span data-ttu-id="2f90f-107">Les schémas sont essentiels aux outils de développement BizTalk Server et à l'intégration dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2f90f-107">Schemas are very important for BizTalk Server development tools and for integration in Visual Studio.</span></span> <span data-ttu-id="2f90f-108">Les développeurs BizTalk Server peuvent choisir de fournir un schéma complet, minimum ou une version intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="2f90f-108">BizTalk Server developers can choose to provide a complete schema, a minimalist schema, or a version somewhere in between.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f90f-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f90f-109">See Also</span></span>  
 [<span data-ttu-id="2f90f-110">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="2f90f-110">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)