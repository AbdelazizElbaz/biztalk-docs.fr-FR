---
title: "À l’aide de TIBCO Rendezvous les Ports de réception de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: receive ports, using from BizTalk Server
ms.assetid: 26cb20f9-4d26-48f6-a5e9-a51348a56538
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b8e0999362844570bb56cfbc488e5fd5775e286
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-tibco-rendezvous-receive-ports-from-biztalk-server"></a><span data-ttu-id="51b0c-102">Utilisation des ports de réception TIBCO Rendezvous à partir de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="51b0c-102">Using TIBCO Rendezvous Receive Ports from BizTalk Server</span></span>
<span data-ttu-id="51b0c-103">Pour utiliser un port de réception, vous pouvez fournir un schéma à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="51b0c-103">To use a receive port, you can provide a schema to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for the incoming messages.</span></span> <span data-ttu-id="51b0c-104">Un port de réception est configuré pour écouter un ensemble de noms d'objet particulier.</span><span class="sxs-lookup"><span data-stu-id="51b0c-104">A receive port is configured to listen for a particular set of subject names.</span></span> <span data-ttu-id="51b0c-105">Il fait appel à un nom d'objet possédant des caractères génériques facultatifs de façon à correspondre à plusieurs noms d'objet.</span><span class="sxs-lookup"><span data-stu-id="51b0c-105">It uses a subject name with optional wildcard characters to match multiple subject names.</span></span> <span data-ttu-id="51b0c-106">Dans l'orchestration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez définir des opérations de port distinctes pour chaque objet possible qui correspond à une chaîne donnée.</span><span class="sxs-lookup"><span data-stu-id="51b0c-106">You define different port operations in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration for each possible subject that matches the given string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51b0c-107">L'adaptateur prend en charge les scénarios d'orchestration et de messagerie.</span><span class="sxs-lookup"><span data-stu-id="51b0c-107">The Adapter supports both orchestration and messaging scenarios.</span></span>  
  
## <a name="defining-schemas"></a><span data-ttu-id="51b0c-108">Définition de schémas</span><span class="sxs-lookup"><span data-stu-id="51b0c-108">Defining Schemas</span></span>  
 <span data-ttu-id="51b0c-109">Par exemple, si le port est configuré pour écouter le nom du sujet, **STOCK. MARCHÉ. INDICES. >** («**>**' est un caractère générique signifiant que rien d’autre à droite), il serait valide de définir des opérations pour les noms d’objet comme **STOCK. MARCHÉ. INDEX. WALL STREET. SP500**, **STOCK. MARCHÉ. INDEX. TSX.TSX60**, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="51b0c-109">For example, if the port is configured to listen to the subject name, **STOCK.MARKET.INDICES.>** ('**>**' is a wildcard character that means anything else to the right), it would be valid to define operations for subject names such as **STOCK.MARKET.INDICES.NYSE.SP500**, **STOCK.MARKET.INDICES.TSX.TSX60**, and so on.</span></span> <span data-ttu-id="51b0c-110">L’adaptateur génère des messages à l’aide de la stratégie décrite dans [mappage de Type de données pour les gestionnaires de réception dans TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md)et génère le nom de l’élément racine et les espaces de noms en fonction de l’écoute de l’objet nom et message reçu noms de sujet respectivement.</span><span class="sxs-lookup"><span data-stu-id="51b0c-110">The adapter generates messages using the strategy described in [Data Type Mapping for Receive Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md), and generates the root element name and namespaces based on the listen subject name and received message subject names respectively.</span></span>  
  
 <span data-ttu-id="51b0c-111">Dans l'exemple précédent, l'adaptateur a généré un message pour l'événement SP500 qui ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="51b0c-111">In the previous example, the adapter generates a message that looks like this for the SP500 event:</span></span>  
  
```  
<ns:STOCK.MARKET.INDICES.NYSE.SP500 xmlns:ns='   
http://schemas.microsoft.com/TibcoRendezvous/Types/  
STOCK.MARKET.INDICES.NYSE.GTWILDCARD'  
xmlns:tibrv=' http://schemas.microsoft.com/TibcoRendezvous/Types' … >  
<message body>  
</ns: STOCK.MARKET.INDICES.NYSE.SP500>  
  
```  
  
 <span data-ttu-id="51b0c-112">Vous devez définir un schéma qui fait appel aux mêmes conventions.</span><span class="sxs-lookup"><span data-stu-id="51b0c-112">You must define a schema that uses the same conventions.</span></span> <span data-ttu-id="51b0c-113">Exemple :</span><span class="sxs-lookup"><span data-stu-id="51b0c-113">For example:</span></span>  
  
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
  
 <span data-ttu-id="51b0c-114">Notez l’utilisation de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] **recordInfo/rootTypeName** annotation.</span><span class="sxs-lookup"><span data-stu-id="51b0c-114">Note the use of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**recordInfo/rootTypeName** annotation.</span></span> <span data-ttu-id="51b0c-115">Elle permet d'indiquer à l'intégration [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]/BizTalk qu'il est nécessaire d'utiliser ce nom pour les types .NET Framework générés au lieu du nom contenant des points.</span><span class="sxs-lookup"><span data-stu-id="51b0c-115">This is to instruct the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]/BizTalk integration to use that name for the generated .NET Framework types, instead of the name that contains dots.</span></span> <span data-ttu-id="51b0c-116">Vous pouvez spécifier n'importe quelle valeur.</span><span class="sxs-lookup"><span data-stu-id="51b0c-116">You can specify anything.</span></span> <span data-ttu-id="51b0c-117">Dans les exemples, les points sont remplacés par des traits de soulignement.</span><span class="sxs-lookup"><span data-stu-id="51b0c-117">In the examples, the dots are replaced with underscores.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51b0c-118">Les points entraînent la création de noms qui ne sont pas valides à l'aide des outils de développement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="51b0c-118">The dots cause invalid names to be generated by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] development tools.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51b0c-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51b0c-119">See Also</span></span>  
 <span data-ttu-id="51b0c-120">[Mappage de Type de données pour les gestionnaires de réception dans TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="51b0c-120">[Data Type Mapping for Receive Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="51b0c-121">Gestionnaires de réception création TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="51b0c-121">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)