---
title: "Le Service Web de résolution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 236cff15-562a-41d5-bfdc-d250186fb616
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 916181431686ca729c0751d9362570afb7dddeee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-resolver-web-service"></a><span data-ttu-id="e6466-102">Le Service Web de résolution</span><span class="sxs-lookup"><span data-stu-id="e6466-102">The Resolver Web Service</span></span>
<span data-ttu-id="e6466-103">Le service Web du programme de résolution est une passerelle dans le mécanisme de résolution dynamique ESB.</span><span class="sxs-lookup"><span data-stu-id="e6466-103">The Resolver Web service is a gateway into the ESB dynamic resolution mechanism.</span></span> [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]<span data-ttu-id="e6466-104">inclut les deux versions de ce service : une version de ASP.NET (ASMX) et une version de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e6466-104"> includes two versions of this service: an ASP.NET (ASMX) version and a Windows Communication Foundation (WCF) version.</span></span> <span data-ttu-id="e6466-105">Les noms de service sont **ESB. ResolverServices** et **ESB. ResolverServices.WCF**, respectivement, et les services exposent des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="e6466-105">The service names are **ESB.ResolverServices** and **ESB.ResolverServices.WCF**, respectively, and the services expose the following methods:</span></span>  
  
-   <span data-ttu-id="e6466-106">**Résoudre.**</span><span class="sxs-lookup"><span data-stu-id="e6466-106">**Resolve.**</span></span> <span data-ttu-id="e6466-107">Cette méthode prend comme unique paramètre un **chaîne** qui contient la chaîne de connexion de programme de résolution de la demande, qui est conforme pour les chaînes de connexion standard tels que des programmes de résolution des **statique, BRE, UDDI, XPATH, l’itinéraire, itinéraire statique, BRI,** ou **LDAP.**</span><span class="sxs-lookup"><span data-stu-id="e6466-107">This method takes as its single parameter a **String** that contains the resolver connection string for the request, which conforms to the standard connection strings for registered resolvers such as **STATIC, BRE, UDDI, XPATH, ITINERARY, ITINERARY-STATIC, BRI,** or **LDAP.**</span></span>  
  
-   <span data-ttu-id="e6466-108">**ResolveMessage.**</span><span class="sxs-lookup"><span data-stu-id="e6466-108">**ResolveMessage.**</span></span> <span data-ttu-id="e6466-109">Cette méthode prend comme premier paramètre de chaîne qui contient la chaîne de connexion de programme de résolution de la demande, qui est conforme pour les chaînes de connexion standard tels que des programmes de résolution des **statique, BRE, UDDI, XPATH, feuille de route, ITINÉRAIRE statique, BRI,** ou **LDAP**.</span><span class="sxs-lookup"><span data-stu-id="e6466-109">This method takes as its first parameter a String that contains the resolver connection string for the request, which conforms to the standard connection strings for registered resolvers such as  **STATIC, BRE, UDDI, XPATH, ITINERARY, ITINERARY-STATIC, BRI,** or **LDAP**.</span></span> <span data-ttu-id="e6466-110">En outre, la méthode accepte un deuxième paramètre facultatif en tant qu’un **chaîne** qui contient un document de message XML que le service peut utiliser en tant que faits facultatif pour faciliter une résolution ; par exemple, le programme de résolution BRE peut nécessiter un corps de message qui encapsule des faits.</span><span class="sxs-lookup"><span data-stu-id="e6466-110">In addition, the method accepts an optional second parameter as a **String** that contains an XML message document that the service can use as optional facts to assist in a resolution; for example, the BRE resolver may require a message body that encapsulates facts.</span></span>  
  
 <span data-ttu-id="e6466-111">Pour plus d’informations sur les classes de programme de résolution et ResolverDictionary et leur utilisation, consultez [l’utilisation des Classes d’assistance](../esb-toolkit/using-the-helper-classes.md).</span><span class="sxs-lookup"><span data-stu-id="e6466-111">For more information about the Resolver and ResolverDictionary classes and their usage, see [Using the Helper Classes](../esb-toolkit/using-the-helper-classes.md).</span></span>  
  
## <a name="resolver-connection-strings"></a><span data-ttu-id="e6466-112">Programme de résolution des chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="e6466-112">Resolver Connection Strings</span></span>  
 <span data-ttu-id="e6466-113">Le mécanisme de résolution dynamique ESB utilise une chaîne de connexion précédée d’un moniker qui indique le type de résolution à effectuer.</span><span class="sxs-lookup"><span data-stu-id="e6466-113">The ESB dynamic resolution mechanism uses a connection string preceded by a moniker that indicates the type of resolution to perform.</span></span> <span data-ttu-id="e6466-114">Les monikers pris en charge incluent **statique, BRE, UDDI, UDDI3, XPATH, itinéraire, itinéraire statique, BRI,** et **LDAP**.</span><span class="sxs-lookup"><span data-stu-id="e6466-114">The supported monikers include **STATIC, BRE, UDDI, UDDI3, XPATH, ITINERARY, ITINERARY-STATIC, BRI,** and **LDAP**.</span></span> <span data-ttu-id="e6466-115">La chaîne de connexion suivante montre un exemple d’un **UDDI** moniker :</span><span class="sxs-lookup"><span data-stu-id="e6466-115">The following connection string shows an example of a **UDDI** moniker:</span></span>  
  
```  
  
//UDDI  
UDDI:\\serverUrl=http://localhost/uddi;serviceName=PurchaseOrder;serviceProvider=Microsoft.Practices.ESB  
```  
  
 <span data-ttu-id="e6466-116">Pour plus d’informations sur les types de chaînes de connexion pris en charge par le mécanisme de résolution dynamique, consultez [à l’aide de la résolution dynamique et routage](../esb-toolkit/using-dynamic-resolution-and-routing.md).</span><span class="sxs-lookup"><span data-stu-id="e6466-116">For information about the types of connections strings supported by the dynamic resolution mechanism, see [Using Dynamic Resolution and Routing](../esb-toolkit/using-dynamic-resolution-and-routing.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6466-117">Vous devez configurer ce service pour utiliser la sécurité intégrée Windows et pour s’exécuter sous le compte SERVICE réseau intégré.</span><span class="sxs-lookup"><span data-stu-id="e6466-117">You must configure this service to use either Windows Integrated Security and to run under the built-in NETWORK SERVICE account.</span></span>  
>   
>  <span data-ttu-id="e6466-118">Par défaut, les services Web du programme de résolution ne sont pas configurés pour exiger SSL Secure Sockets Layer () lors de l’accès par les clients.</span><span class="sxs-lookup"><span data-stu-id="e6466-118">By default, the Resolver Web services are not configured to require Secure Sockets Layer (SSL) when accessed by clients.</span></span> <span data-ttu-id="e6466-119">Vous devez configurer le service afin qu’il exige SSL pour l’accès client et protéger la connexion entre l’ordinateur hôte du service Web des Internet Information Services (IIS) et votre serveur BizTalk Server à l’aide d’IPSec d’au niveau du réseau et l’accès approprié au niveau des fichiers contrôler les autorisations de liste (ACL).</span><span class="sxs-lookup"><span data-stu-id="e6466-119">You should configure the service so that it requires SSL for client access and protect the connection between the Internet Information Services (IIS) Web service host computer and your BizTalk Server using network-level IPSec and appropriate file-level access control list (ACL) permissions.</span></span> <span data-ttu-id="e6466-120">Pour éviter les risques de sécurité, il n’est pas recommandé pour exposer ce service en dehors de la limite du sous-système approuvé.</span><span class="sxs-lookup"><span data-stu-id="e6466-120">To avoid security risks, it is not recommended to expose this service outside the boundary of the trusted subsystem.</span></span>