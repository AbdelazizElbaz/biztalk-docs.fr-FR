---
title: "Schémas SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SWIFT, SWIFT messages
- schemas, SWIFT
- SWIFT messages, SWIFT schemas
- SWIFT, schemas
ms.assetid: 53017a56-a718-4577-a08c-9c92d9a54e7a
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b4bac26d99fb3282650c20381bbc18237f8908a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-schemas"></a><span data-ttu-id="26be6-102">Schémas SWIFT</span><span class="sxs-lookup"><span data-stu-id="26be6-102">SWIFT Schemas</span></span>
[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]<span data-ttu-id="26be6-103">envoie et reçoit des messages de (FIN) de financières SWIFT sous forme de fichiers plats individuels sur le réseau rapide.</span><span class="sxs-lookup"><span data-stu-id="26be6-103"> sends and receives SWIFT financial (FIN) messages as individual flat files over the SWIFT network.</span></span> <span data-ttu-id="26be6-104">Chaque message se compose d’un ensemble de blocs d’en-tête, un bloc de texte composé d’un ensemble prédéfini d’étiqueté de champs et sous-champs positionnels ou ordonnés et un ensemble de codes de fin à l’intérieur d’un bloc de code de fin.</span><span class="sxs-lookup"><span data-stu-id="26be6-104">Each individual message consists of a set of header blocks, a text block made up of a predefined set of labeled fields and positional or ordered subfields, and a set of trailers inside a trailer block.</span></span> <span data-ttu-id="26be6-105">Le contenu du bloc de texte varie selon le type de message.</span><span class="sxs-lookup"><span data-stu-id="26be6-105">The content of the text block varies by message type.</span></span>  
  
 <span data-ttu-id="26be6-106">Il existe également de nombreuses applications, qui échangent des lots de messages (FIN) de financières SWIFT : un ensemble de messages contenus dans un seul fichier.</span><span class="sxs-lookup"><span data-stu-id="26be6-106">There are also many applications, which exchange batches of SWIFT financial (FIN) messages—a set of messages contained in a single file.</span></span> <span data-ttu-id="26be6-107">Le fichier peut être remis localement ou peut être transmis au moyen de FileAct (sur le réseau IP SWIFT : SIPN), ou via FTP.</span><span class="sxs-lookup"><span data-stu-id="26be6-107">The file may be delivered locally or may be transmitted through FileAct (over the SWIFT IP Network—SIPN), or through FTP.</span></span>  
  
 <span data-ttu-id="26be6-108">Pour simplifier la manipulation de données associées à ces messages, qu’ils sont traités par lot ou soumis individuellement, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] fournit un schéma XSD définissant chaque type de message.</span><span class="sxs-lookup"><span data-stu-id="26be6-108">To simplify the manipulation of the data associated with these messages, regardless of whether they are batched or submitted individually, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] provides an XSD schema defining each message type.</span></span> <span data-ttu-id="26be6-109">Ce schéma promeut le type de message afin que les messages peuvent être automatiquement associés au schéma approprié et transformés automatiquement entre la représentation sous forme de fichier plat externe utilisée par le réseau rapide, vers et à partir de XML.</span><span class="sxs-lookup"><span data-stu-id="26be6-109">This schema promotes the message type so that messages can be automatically associated with the proper schema, and automatically transformed between the external flat file representation, used by the SWIFT network, to and from XML.</span></span>  
  
 <span data-ttu-id="26be6-110">Le schéma inclut tous les blocs, y compris les en-têtes, texte et les codes de fin.</span><span class="sxs-lookup"><span data-stu-id="26be6-110">The schema includes all of the blocks including headers, text, and trailers.</span></span> <span data-ttu-id="26be6-111">Ce schéma est un schéma de l’échange, car elle est suffisamment complète pour transmettre des messages sur le réseau rapide en utilisant les protocoles au niveau du message FIN et pour contenir toutes les informations associées à un message reçu via le réseau rapide.</span><span class="sxs-lookup"><span data-stu-id="26be6-111">This schema is an interchange schema, because it is comprehensive enough to transmit messages over the SWIFT network using the FIN message-level protocols, and to contain all of the information associated with a message received through the SWIFT network.</span></span>  
  
 <span data-ttu-id="26be6-112">Le schéma pour chaque type de message définit le format et le contexte de ce type de message globales.</span><span class="sxs-lookup"><span data-stu-id="26be6-112">The schema for each message type defines the overall format and context of that message type.</span></span> <span data-ttu-id="26be6-113">A4SWIFT définit chaque bloc.</span><span class="sxs-lookup"><span data-stu-id="26be6-113">A4SWIFT defines each block.</span></span> <span data-ttu-id="26be6-114">À l’intérieur de chaque bloc, les champs et sous-champs sont disposés. Selon le cas, les champs et sous-champs sont générés à partir des types courants de base ou complexes, définis dans des schémas distincts.</span><span class="sxs-lookup"><span data-stu-id="26be6-114">Inside each block, the fields and subfields are laid out. As appropriate, the fields and subfields are built from common base or complex types, defined in separate schemas.</span></span> <span data-ttu-id="26be6-115">Validation au niveau du schéma inclut le format, jeu de caractères, valeur définie, plage, obligatoire ou facultatif, la répétabilité, position et la longueur, comme il convient.</span><span class="sxs-lookup"><span data-stu-id="26be6-115">Schema-level validation includes format, character set, value set, range, required/optional, repeatability, position, and length, as appropriate.</span></span> <span data-ttu-id="26be6-116">Les règles d’entreprise effectuent des validations de champ croisé et d’autres vérifications logiques.</span><span class="sxs-lookup"><span data-stu-id="26be6-116">The business rules perform cross-field validations and other logical checks.</span></span>  
  
 <span data-ttu-id="26be6-117">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="26be6-117">This section contains:</span></span>  
  
-   [<span data-ttu-id="26be6-118">Exemple de présentation de Message</span><span class="sxs-lookup"><span data-stu-id="26be6-118">Sample Message Presentation</span></span>](../../adapters-and-accelerators/accelerator-swift/sample-message-presentation.md)  
  
-   [<span data-ttu-id="26be6-119">Exemple de présentation de schéma</span><span class="sxs-lookup"><span data-stu-id="26be6-119">Sample Schema Presentation</span></span>](../../adapters-and-accelerators/accelerator-swift/sample-schema-presentation.md)  
  
-   [<span data-ttu-id="26be6-120">En-têtes SWIFT</span><span class="sxs-lookup"><span data-stu-id="26be6-120">SWIFT Headers</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-headers.md)  
  
-   [<span data-ttu-id="26be6-121">Texte SWIFT</span><span class="sxs-lookup"><span data-stu-id="26be6-121">SWIFT Text</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-text.md)  
  
-   [<span data-ttu-id="26be6-122">Codes de fin SWIFT</span><span class="sxs-lookup"><span data-stu-id="26be6-122">SWIFT Trailers</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-trailers.md)  
  
-   [<span data-ttu-id="26be6-123">Mise à jour des normes de messages SWIFT</span><span class="sxs-lookup"><span data-stu-id="26be6-123">Updating SWIFT Message Standards</span></span>](../../adapters-and-accelerators/accelerator-swift/updating-swift-messaging-standards.md)