---
title: "Recevoir des schémas et traiter les événements avec l’adaptateur TIBCO Rendezvous | Documents Microsoft"
description: "Utiliser les schémas de TIBCO Rendezvous sur le côté réception et le traitement des événements à l’aide de l’adaptateur BizTalk pour TIBCO Rendezvous dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26cb20f9-4d26-48f6-a5e9-a51348a56538
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bbbae69dc1b7df1f5675442dde544a444cec02fb
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="using-tibco-rendezvous-receive-ports-from-biztalk-server"></a><span data-ttu-id="fc0ed-103">Utilisation des ports de réception TIBCO Rendezvous à partir de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="fc0ed-103">Using TIBCO Rendezvous Receive Ports from BizTalk Server</span></span>

## <a name="overview"></a><span data-ttu-id="fc0ed-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="fc0ed-104">Overview</span></span>
<span data-ttu-id="fc0ed-105">Pour utiliser un port de réception, vous pouvez fournir un schéma à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="fc0ed-105">To use a receive port, you can provide a schema to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for the incoming messages.</span></span> <span data-ttu-id="fc0ed-106">Un port de réception est configuré pour écouter un ensemble de noms d'objet particulier.</span><span class="sxs-lookup"><span data-stu-id="fc0ed-106">A receive port is configured to listen for a particular set of subject names.</span></span> <span data-ttu-id="fc0ed-107">Il fait appel à un nom d'objet possédant des caractères génériques facultatifs de façon à correspondre à plusieurs noms d'objet.</span><span class="sxs-lookup"><span data-stu-id="fc0ed-107">It uses a subject name with optional wildcard characters to match multiple subject names.</span></span> <span data-ttu-id="fc0ed-108">Dans l'orchestration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez définir des opérations de port distinctes pour chaque objet possible qui correspond à une chaîne donnée.</span><span class="sxs-lookup"><span data-stu-id="fc0ed-108">You define different port operations in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration for each possible subject that matches the given string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc0ed-109">L’adaptateur prend en charge à la fois d’orchestration et de scénarios de messagerie.</span><span class="sxs-lookup"><span data-stu-id="fc0ed-109">The adapter supports both orchestration and messaging scenarios.</span></span>  
  
## <a name="define-schemas"></a><span data-ttu-id="fc0ed-110">Définir des schémas</span><span class="sxs-lookup"><span data-stu-id="fc0ed-110">Define schemas</span></span>  
 <span data-ttu-id="fc0ed-111">Par exemple, si le port est configuré pour écouter le nom du sujet, **STOCK. MARCHÉ. INDICES. >** («**>**' est un caractère générique signifiant que rien d’autre à droite), il serait valide de définir des opérations pour les noms d’objet comme **STOCK. MARCHÉ. INDEX. WALL STREET. SP500**, **STOCK. MARCHÉ. INDEX. TSX.TSX60**, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="fc0ed-111">For example, if the port is configured to listen to the subject name, **STOCK.MARKET.INDICES.>** ('**>**' is a wildcard character that means anything else to the right), it would be valid to define operations for subject names such as **STOCK.MARKET.INDICES.NYSE.SP500**, **STOCK.MARKET.INDICES.TSX.TSX60**, and so on.</span></span> <span data-ttu-id="fc0ed-112">L’adaptateur génère des messages à l’aide de la stratégie décrite dans [mappage de Type de données pour les gestionnaires de réception dans TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md)et génère le nom de l’élément racine et les espaces de noms en fonction de l’écoute de l’objet nom et message reçu noms de sujet respectivement.</span><span class="sxs-lookup"><span data-stu-id="fc0ed-112">The adapter generates messages using the strategy described in [Data Type Mapping for Receive Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md), and generates the root element name and namespaces based on the listen subject name and received message subject names respectively.</span></span>  
  
 <span data-ttu-id="fc0ed-113">Dans l’exemple précédent, l’adaptateur génère un message qui ressemble à celui-ci pour l’événement SP500 :</span><span class="sxs-lookup"><span data-stu-id="fc0ed-113">In the previous example, the adapter generates a message that looks like the following for the SP500 event:</span></span>  
  
```  
<ns:STOCK.MARKET.INDICES.NYSE.SP500 xmlns:ns='   
http://schemas.microsoft.com/TibcoRendezvous/Types/  
STOCK.MARKET.INDICES.NYSE.GTWILDCARD'  
xmlns:tibrv=' http://schemas.microsoft.com/TibcoRendezvous/Types' … >  
<message body>  
</ns: STOCK.MARKET.INDICES.NYSE.SP500>  
  
```  
  
 <span data-ttu-id="fc0ed-114">Vous devez définir un schéma qui fait appel aux mêmes conventions.</span><span class="sxs-lookup"><span data-stu-id="fc0ed-114">You must define a schema that uses the same conventions.</span></span> <span data-ttu-id="fc0ed-115">Exemple :</span><span class="sxs-lookup"><span data-stu-id="fc0ed-115">For example:</span></span>  
  
```  
<xsd:schema  
targetNamespace='   
  
http://schemas.microsoft.com/TibcoRendezvous/Types/STOCK.MARKET.INDICES.N  
YSE.GTWILDCARD'  
xmlns:xsd=' http://www.w3.org/2001/XMLSchema'  
xmlns:tibrv=' http://schemas.microsoft.com/TibcoRendezvous/Types'>  
xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
<xsd:element name='STOCK.MARKET.INDICES.NYSE.SP500'>  
  
 <xs:annotation>  
   <xs:appinfo>  
     <b:recordInfo rootTypeName="STOCK_MARKET_INDICES_NYSE_SP500" />  
   </xs:appinfo>  
  
 </xs:annotation>  
<xsd:complexType>  
<SP500 message definitions goes here>  
</xsd:complexType>  
<xsd:element name='STOCK.MARKET.INDICES.TSX.TSX60'>  
  
 <xs:annotation>  
   <xs:appinfo>  
     <b:recordInfo rootTypeName="STOCK_MARKET_INDICES_TSX_TSX60" />  
   </xs:appinfo>  
  
 </xs:annotation>  
<xsd:complexType>  
<TSX60 message definitions goes here>  
</xsd:complexType>  
  
```  
  
 <span data-ttu-id="fc0ed-116">Notez l’utilisation de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] **recordInfo/rootTypeName** annotation.</span><span class="sxs-lookup"><span data-stu-id="fc0ed-116">Note the use of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**recordInfo/rootTypeName** annotation.</span></span> <span data-ttu-id="fc0ed-117">Elle permet d'indiquer à l'intégration [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]/BizTalk qu'il est nécessaire d'utiliser ce nom pour les types .NET Framework générés au lieu du nom contenant des points.</span><span class="sxs-lookup"><span data-stu-id="fc0ed-117">This is to instruct the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]/BizTalk integration to use that name for the generated .NET Framework types, instead of the name that contains dots.</span></span> <span data-ttu-id="fc0ed-118">Vous pouvez spécifier n'importe quelle valeur.</span><span class="sxs-lookup"><span data-stu-id="fc0ed-118">You can specify anything.</span></span> <span data-ttu-id="fc0ed-119">Dans les exemples, les points sont remplacés par des traits de soulignement.</span><span class="sxs-lookup"><span data-stu-id="fc0ed-119">In the examples, the dots are replaced with underscores.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc0ed-120">Les points entraînent la création de noms qui ne sont pas valides à l'aide des outils de développement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fc0ed-120">The dots cause invalid names to be generated by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] development tools.</span></span>  

## <a name="event-processing"></a><span data-ttu-id="fc0ed-121">Traitement des événements</span><span class="sxs-lookup"><span data-stu-id="fc0ed-121">Event processing</span></span>
<span data-ttu-id="fc0ed-122">L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous distribue des événements à partir d'une file d'attente sur plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="fc0ed-122">Microsoft BizTalk Adapter for TIBCO Rendezvous dispatches events from a queue on multiple threads.</span></span> <span data-ttu-id="fc0ed-123">Emplacement de réception BizTalk Server est associé à une file d’attente des événements TIBCO Rendezvous et son pool de threads du répartiteur.</span><span class="sxs-lookup"><span data-stu-id="fc0ed-123">A BizTalk Server receive location is associated with one TIBCO Rendezvous event queue, and its pool of dispatcher threads.</span></span>  
  
### <a name="memory-use-and-errors"></a><span data-ttu-id="fc0ed-124">Utilisation de la mémoire et erreurs</span><span class="sxs-lookup"><span data-stu-id="fc0ed-124">Memory Use and Errors</span></span>  
 <span data-ttu-id="fc0ed-125">L'adaptateur surveille les ressources utilisées lors du traitement d'événements.</span><span class="sxs-lookup"><span data-stu-id="fc0ed-125">While processing events, the adapter keeps an eye on used resources.</span></span> <span data-ttu-id="fc0ed-126">Si l'utilisation de la mémoire dépasse la limite supérieure, l'adaptateur arrête la distribution des événements jusqu'à ce que la consommation de mémoire atteigne la limite inférieure.</span><span class="sxs-lookup"><span data-stu-id="fc0ed-126">If memory use goes above the high-watermark, the adapter stops dispatching events until it reaches the low-watermark memory consumption.</span></span> <span data-ttu-id="fc0ed-127">Notez que des messages TIBCO Rendezvous non certifiés peuvent ainsi être manqués (un utilisateur de TIBCO RV dispose de 60 secondes pour supprimer des messages dans une file d'attente).</span><span class="sxs-lookup"><span data-stu-id="fc0ed-127">Note that this might result in TIBCO Rendezvous messages being missed for non certified messages (a TIBCO RV consumer has 60 seconds to remove messages from a queue).</span></span> <span data-ttu-id="fc0ed-128">Cette perte de données est signalée en tant qu'erreur.</span><span class="sxs-lookup"><span data-stu-id="fc0ed-128">This data loss is reported as an error.</span></span> <span data-ttu-id="fc0ed-129">Si l'adaptateur reçoit un message d'avertissement NO_MEMORY en provenance du système TIBCO Rendezvous, cela signifie que des messages ont déjà été perdus.</span><span class="sxs-lookup"><span data-stu-id="fc0ed-129">If the adapter receives a TIBCO Rendezvous system advisory NO_MEMORY message, messages have already been lost.</span></span>  
  
 <span data-ttu-id="fc0ed-130">L'adaptateur BizTalk pour TIBCO Rendezvous conserve un état et exécute des tâches de différentes façons en fonction de cet état.</span><span class="sxs-lookup"><span data-stu-id="fc0ed-130">BizTalk Adapter for TIBCO Rendezvous maintains a state, and it executes tasks differently based on that state.</span></span> <span data-ttu-id="fc0ed-131">Si le moteur de messagerie BizTalk renvoie une erreur et si l'adaptateur est configuré en tant qu'écouteur certifié, le moteur la signale à TIBCO Rendezvous afin qu'il puisse renvoyer le message.</span><span class="sxs-lookup"><span data-stu-id="fc0ed-131">If the BizTalk Message Engine reports an error, and the adapter is configured to be a certified listener, it reports the error to TIBCO Rendezvous so that it can resubmit the message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc0ed-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc0ed-132">See Also</span></span>  
 <span data-ttu-id="fc0ed-133">[Concepts de TIBCO Rendezvous](../core/tibco-rendezvous-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="fc0ed-133">[TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md) </span></span>  
 <span data-ttu-id="fc0ed-134">[Mappage de Type de données pour les gestionnaires de réception dans TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="fc0ed-134">[Data Type Mapping for Receive Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="fc0ed-135">Création de gestionnaires de réception TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="fc0ed-135">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)