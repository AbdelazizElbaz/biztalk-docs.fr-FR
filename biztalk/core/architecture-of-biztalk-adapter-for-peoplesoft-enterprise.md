---
title: "Architecture de l’adaptateur BizTalk pour PeopleSoft Enterprise | Documents Microsoft"
description: "Décrit la façon dont les messages sont reçus, comment les messages sont valide et fournit des informations sur les méthodes d’interface de composant à l’aide de l’adaptateur PeopleSoft avec BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f246e974-a082-430c-ad15-23a5e597738b
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3eb0f43dacdbd6036ef59fa3fe16102d4fe12379
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="peoplesoft-enterprise-adapter-architecture"></a><span data-ttu-id="1245c-103">Architecture de l’adaptateur PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="1245c-103">PeopleSoft Enterprise adapter architecture</span></span>
<span data-ttu-id="1245c-104">Au cours de son fonctionnement de base, l'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise reçoit un message XML de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="1245c-104">During the basic operation of Microsoft BizTalk Adapter for PeopleSoft Enterprise, the adapter receives an XML message from BizTalk Server.</span></span> <span data-ttu-id="1245c-105">qu'il place dans une enveloppe SOAP.</span><span class="sxs-lookup"><span data-stu-id="1245c-105">It encloses the XML message in a SOAP envelope.</span></span> <span data-ttu-id="1245c-106">Il transmet ensuite les requêtes SOAP au serveur.</span><span class="sxs-lookup"><span data-stu-id="1245c-106">BizTalk Adapter for PeopleSoft Enterprise forwards the SOAP requests to the server.</span></span> <span data-ttu-id="1245c-107">Il communique avec le système PeopleSoft à l'aide des classes psjoa, qui se connectent au système PeopleSoft via le protocole JTP (Jolt Transaction Protocol).</span><span class="sxs-lookup"><span data-stu-id="1245c-107">The adapter communicates with the PeopleSoft system using the PeopleSoft psjoa classes, which connect to the PeopleSoft system through Jolt Transaction Protocol.</span></span> <span data-ttu-id="1245c-108">Le système PeopleSoft reçoit la requête et exécute la logique d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="1245c-108">The PeopleSoft system receives the request and executes the business logic.</span></span> <span data-ttu-id="1245c-109">Le processus de réponse est similaire.</span><span class="sxs-lookup"><span data-stu-id="1245c-109">The reply is sent back through a similar process.</span></span>  
  
 ![](../core/media/psadapter-01-architecture.gif "PSAdapter_01_Architecture")  

  
## <a name="component-interface-methods"></a><span data-ttu-id="1245c-110">méthodes relatives à l'interface de composant</span><span class="sxs-lookup"><span data-stu-id="1245c-110">Component Interface Methods</span></span>  
 <span data-ttu-id="1245c-111">Par défaut, les API fournies par l'interface de composant PeopleSoft sont des API de base</span><span class="sxs-lookup"><span data-stu-id="1245c-111">The basic APIs that are provided by the PeopleSoft component interface are low-level in nature.</span></span> <span data-ttu-id="1245c-112">que le client doit appeler à plusieurs reprises.</span><span class="sxs-lookup"><span data-stu-id="1245c-112">The client requires multiple invocations of these APIs.</span></span> <span data-ttu-id="1245c-113">Par exemple, pour obtenir la propriété d'une instance d'une interface de composant, le client doit effectuer un ou plusieurs appels pour définir les valeurs de clé, puis un appel de la méthode Get de bas niveau.</span><span class="sxs-lookup"><span data-stu-id="1245c-113">For example, to obtain the property of an instance of a component interface, the client needs one or more calls to set the key values followed by a low-level Get method call.</span></span> <span data-ttu-id="1245c-114">Il doit ensuite envoyer plusieurs appels pour obtenir les propriétés.</span><span class="sxs-lookup"><span data-stu-id="1245c-114">It must then send multiple calls to get the properties.</span></span> <span data-ttu-id="1245c-115">L'adaptateur BizTalk pour PeopleSoft Enterprise fournit un nouvel ensemble de méthodes standard (Get, Create, Find et Update) qui permettent au client d'effectuer un seul appel pour obtenir le même résultat.</span><span class="sxs-lookup"><span data-stu-id="1245c-115">With BizTalk Adapter for PeopleSoft Enterprise, a new set of standard methods (Get, Create, Find, and Update) are provided in such a way that the client is required to make a single call to accomplish the same result.</span></span> <span data-ttu-id="1245c-116">Pour ce faire, l'adaptateur BizTalk pour PeopleSoft Enterprise doit effectuer plusieurs appels au nom du client.</span><span class="sxs-lookup"><span data-stu-id="1245c-116">You do this by having BizTalk Adapter for PeopleSoft Enterprise perform multiple calls on behalf of the client.</span></span> <span data-ttu-id="1245c-117">Pour plus d’informations sur les méthodes, consultez [annexe a : composant Interface méthodes](../core/appendix-a-component-interface-methods.md).</span><span class="sxs-lookup"><span data-stu-id="1245c-117">For more information about the methods, see [Appendix A: Component Interface Methods](../core/appendix-a-component-interface-methods.md).</span></span>  
  
 <span data-ttu-id="1245c-118">Pour créer un schéma pour PeopleSoft, l'adaptateur BizTalk pour PeopleSoft Enterprise extrait les définitions ou métadonnées de l'interface de composant PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="1245c-118">To create a schema for PeopleSoft, BizTalk Adapter for PeopleSoft Enterprise retrieves the PeopleSoft component interface definitions or metadata.</span></span>  
  
 <span data-ttu-id="1245c-119">L'adaptateur BizTalk pour PeopleSoft Enterprise est basé sur les interfaces de composant de la fonctionnalité Envoi et ne requiert pas PeopleSoft Integration Broker.</span><span class="sxs-lookup"><span data-stu-id="1245c-119">BizTalk Adapter for PeopleSoft Enterprise is based on component interfaces for the Send functionality and does not require the PeopleSoft Integration Broker.</span></span> <span data-ttu-id="1245c-120">Les interfaces de composant sont exposées en tant que services Web, accessibles à partir de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="1245c-120">The component interfaces are exposed as Web services, which can be accessed from BizTalk Server.</span></span>  
  
### <a name="validation"></a><span data-ttu-id="1245c-121">Validation</span><span class="sxs-lookup"><span data-stu-id="1245c-121">Validation</span></span>  
 <span data-ttu-id="1245c-122">Lorsque l'adaptateur BizTalk pour PeopleSoft Enterprise reçoit un message XML de BizTalk Server, deux niveaux de validation ont lieu :</span><span class="sxs-lookup"><span data-stu-id="1245c-122">When BizTalk Adapter for PeopleSoft Enterprise receives an XML message from BizTalk Server, two levels of validation are performed:</span></span>  
  
-   <span data-ttu-id="1245c-123">Le message XML doit être conforme à la spécification XML.</span><span class="sxs-lookup"><span data-stu-id="1245c-123">The XML message must be valid with regard to XML specification.</span></span>  
  
-   <span data-ttu-id="1245c-124">Le message XML doit correspondre aux composants requis par le service Web spécifique (par exemple, mise en correspondance des types de données de l'interface).</span><span class="sxs-lookup"><span data-stu-id="1245c-124">The XML message must match what is required by the specific Web service (for example, interface matching such as data types).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1245c-125">Aucune validation de la logique d'entreprise (domaine du système PeopleSoft transparent à l'adaptateur BizTalk pour PeopleSoft Enterprise) n'est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="1245c-125">There is no validation with regard to business logic, which is the domain of the PeopleSoft system, and is transparent to BizTalk Adapter for PeopleSoft Enterprise.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1245c-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1245c-126">See Also</span></span>  
 [<span data-ttu-id="1245c-127">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="1245c-127">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-peoplesoft-enterprise.md)   