---
title: "Création de schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20b88194-b400-4ebc-8882-d493fbf30e0f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac019276923467fe2d95f5a0a0b4a7b53513e9c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-schemas"></a><span data-ttu-id="57710-102">Création de schémas</span><span class="sxs-lookup"><span data-stu-id="57710-102">Creating Schemas</span></span>
<span data-ttu-id="57710-103">Vous pouvez utiliser l’Éditeur BizTalk pour créer deux types de schémas : les schémas et les schémas de propriété de message.</span><span class="sxs-lookup"><span data-stu-id="57710-103">You can use BizTalk Editor to create two types of schemas: message schemas and property schemas.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57710-104">Il existe plusieurs types de schémas de message, dont les schémas de message XML, les schémas de message de fichier plat et les schémas d'enveloppe.</span><span class="sxs-lookup"><span data-stu-id="57710-104">There are several types of message schemas, including XML message schemas, flat file message schemas, and envelope schemas.</span></span>  
  
 <span data-ttu-id="57710-105">Les schémas de message définissent la structure et limitent le contenu des messages que vous pensez envoyer à vos partenaires commerciaux ou applications, ou recevoir de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="57710-105">Message schemas define the structure and constrain the content of messages that you expect to send to, and receive from, your trading partners or applications.</span></span> <span data-ttu-id="57710-106">Schémas de message sont les plus courants de schémas que vous utiliserez avec Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="57710-106">Message schemas are the most common types of schemas that you will use with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="57710-107">créer des schémas de message XML pour les documents d’entreprise et les enveloppes utilisées pour les contenir et via l’utilisation de l’Extension de fichier plat à l’Éditeur BizTalk, il peut créer des schémas de message de fichier plat, y compris des schémas pour les en-têtes, corps et codes de fin.</span><span class="sxs-lookup"><span data-stu-id="57710-107"> can create XML message schemas for both business documents and the envelopes used to contain them, and through the use of the Flat File Extension to BizTalk Editor, it can create flat file message schemas, including schemas for headers, bodies and trailers.</span></span>  
  
 <span data-ttu-id="57710-108">Les schémas de propriété sont un type de schéma particulier.</span><span class="sxs-lookup"><span data-stu-id="57710-108">Property schemas are a special type of schema.</span></span> <span data-ttu-id="57710-109">Les schémas de propriété fournissent un modèle de validation pour les données de champ et/ou d'enregistrement promues depuis un message d'instance vers ce que l’on appelle le contexte de message.</span><span class="sxs-lookup"><span data-stu-id="57710-109">Property schemas provide a validation template for field and/or record data that is promoted from within an instance message into what is known as the message context.</span></span> <span data-ttu-id="57710-110">L'objectif des schémas de propriété est de fournir une définition formelle, fortement typée des données à promouvoir pendant l’exécution.</span><span class="sxs-lookup"><span data-stu-id="57710-110">The purpose of property schemas is to provide a formal, strongly typed definition of the data to be promoted at run time.</span></span>  
  
 <span data-ttu-id="57710-111">La promotion de propriété fournit un mécanisme centralisé pour l'extraction d'éléments d'information clés, que vous définissez, à partir d'un message d'instance et pour les rendre plus accessibles aux composants BizTalk Server qui gèrent le message lors de sa transmission via BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="57710-111">Property promotion provides a centralized mechanism for pulling key pieces of information, defined by you, from within an instance message and making it more easily accessible to BizTalk Server components that are handling the message as it passes through BizTalk Server.</span></span> <span data-ttu-id="57710-112">La mise en correspondance d’une instance de message avec un abonnement constitue une utilisation courante des propriétés promues, permettant au message d’être correctement acheminé pour être traité.</span><span class="sxs-lookup"><span data-stu-id="57710-112">One common use of promoted properties is in matching a message instance to a subscription, allowing the message to be properly routed for processing.</span></span>  
  
 <span data-ttu-id="57710-113">Cette section décrit les méthodes selon lesquelles vous pouvez créer différents types de schémas dans BizTalk Server et présente les sujets connexes qui appartiennent à plusieurs types de schémas.</span><span class="sxs-lookup"><span data-stu-id="57710-113">This section describes the ways in which you can create different types of schemas within BizTalk Server, and presents related subjects that pertain to multiple types of schemas.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="57710-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="57710-114">In This Section</span></span>  
  
-   [<span data-ttu-id="57710-115">Gestion des schémas dans des projets</span><span class="sxs-lookup"><span data-stu-id="57710-115">Managing Schemas Within Projects</span></span>](../core/managing-schemas-within-projects.md)  
  
-   [<span data-ttu-id="57710-116">Gestion des nœuds dans un schéma</span><span class="sxs-lookup"><span data-stu-id="57710-116">Managing the Nodes Within a Schema</span></span>](../core/managing-the-nodes-within-a-schema.md)  
  
-   [<span data-ttu-id="57710-117">Promotion des propriétés</span><span class="sxs-lookup"><span data-stu-id="57710-117">Promoting Properties</span></span>](../core/promoting-properties.md)