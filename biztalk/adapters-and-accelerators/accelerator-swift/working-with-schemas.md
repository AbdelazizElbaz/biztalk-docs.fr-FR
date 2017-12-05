---
title: "Utilisation de schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- developing, schemas
- schemas, developing
ms.assetid: 123c4b43-34e4-41c7-980d-5d518b1479c1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 404beaeb617f7a6c0c5e3fc4ddc40126e6b97990
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="working-with-schemas"></a><span data-ttu-id="cff5c-102">Utilisation de schémas</span><span class="sxs-lookup"><span data-stu-id="cff5c-102">Working with Schemas</span></span>
<span data-ttu-id="cff5c-103">Les schémas fournis dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] sont le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] représentation XSD de la société pour les messages FIN de télécommunication financières Interbank (SWIFT) dans le monde entier.</span><span class="sxs-lookup"><span data-stu-id="cff5c-103">The schemas provided in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] are the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] XSD representation of the Society for Worldwide Interbank Financial Telecommunication (SWIFT) FIN messages.</span></span> <span data-ttu-id="cff5c-104">Chaque type de message possède son propre schéma, y compris l’en-tête SWIFT et le code de fin SWIFT (format d’échange).</span><span class="sxs-lookup"><span data-stu-id="cff5c-104">Each message type has its own schema, including the SWIFT header and SWIFT trailer (interchange format).</span></span> <span data-ttu-id="cff5c-105">Ce schéma est suffisant pour envoyer ou recevoir un message SWIFT.</span><span class="sxs-lookup"><span data-stu-id="cff5c-105">This schema is sufficient to send or receive a SWIFT message.</span></span> <span data-ttu-id="cff5c-106">Ces schémas sont une combinaison unique des enregistrements délimités et positionnels, en fournissant une représentation XML détaillée des structures FIN de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="cff5c-106">These schemas are a unique mixture of delimited and positional records, providing a detailed XML representation of the flat-file FIN structures.</span></span>  
  
 <span data-ttu-id="cff5c-107">La plupart des clients SWIFT utilisent un sous-ensemble relativement faible des messages SWIFT FIN.</span><span class="sxs-lookup"><span data-stu-id="cff5c-107">Most SWIFT customers use a relatively small subset of the SWIFT FIN messages.</span></span> <span data-ttu-id="cff5c-108">Pour implémenter une solution pour ces clients, vous pouvez créer un projet de schéma BizTalk (comme dans [Module 2 : ajout d’un nouveau projet de schémas](../../adapters-and-accelerators/accelerator-swift/module-2-adding-a-new-schemas-project.md) du didacticiel A4SWIFT).</span><span class="sxs-lookup"><span data-stu-id="cff5c-108">To implement a solution for these customers, you can create a BizTalk schema project (as demonstrated in [Module 2: Adding a New Schemas Project](../../adapters-and-accelerators/accelerator-swift/module-2-adding-a-new-schemas-project.md) of the A4SWIFT tutorial).</span></span> <span data-ttu-id="cff5c-109">Ajoutez les schémas de message approprié (MT*xxx*.xsd) à partir de \\\ programme Files\Microsoft BizTalk Accelerator pour SWIFT \<version\> MessagePack\SWIFT Messages\A4SWIFT-SRG\< version\>\Category x\MT xyy répertoire, où x est le premier chiffre de la FIN du type de message et xyy est le type de message de trois chiffres pour le message.</span><span class="sxs-lookup"><span data-stu-id="cff5c-109">Add the relevant message schemas (MT*xxx*.xsd) from \\\ Program Files\Microsoft BizTalk Accelerator for SWIFT \<version\> MessagePack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category x\MT xyy directory, where x is the first digit of the FIN message type and xyy is the three-digit message type for the message.</span></span>  
  
 <span data-ttu-id="cff5c-110">Vous pouvez ajouter plusieurs schémas pour le même projet.</span><span class="sxs-lookup"><span data-stu-id="cff5c-110">You can add several schemas to the same project.</span></span> <span data-ttu-id="cff5c-111">Pour maintenir la facilité de gestion, vous devez ajouter des schémas de message plus de 20 par projet.</span><span class="sxs-lookup"><span data-stu-id="cff5c-111">To maintain manageability, you should not add more than 20 message schemas per project.</span></span> <span data-ttu-id="cff5c-112">Vous devez également ajouter les schémas courants et de base pour le projet.</span><span class="sxs-lookup"><span data-stu-id="cff5c-112">You also need to add the base and common schemas to the project.</span></span> <span data-ttu-id="cff5c-113">Si vous avez déjà déployé les schémas courants et de base, vous devez faire référence à leur assembly, plutôt que de les déployer.</span><span class="sxs-lookup"><span data-stu-id="cff5c-113">If you have already deployed the base and common schemas, you need to make a reference to their assembly, rather than deploy them.</span></span> <span data-ttu-id="cff5c-114">Cette section décrit ces schémas.</span><span class="sxs-lookup"><span data-stu-id="cff5c-114">This section describes these schemas.</span></span> <span data-ttu-id="cff5c-115">Les schémas de message prêts à utiliser comme pour les messages envoyés au réseau SWIFT et messages reçus de SWIFT.</span><span class="sxs-lookup"><span data-stu-id="cff5c-115">The message schemas are ready to use as is for both messages sent to the SWIFT network and messages received from SWIFT.</span></span>  
  
 <span data-ttu-id="cff5c-116">Vous pouvez examiner le contenu de chaque schéma SWIFT dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] à l’aide de l’éditeur de schéma.</span><span class="sxs-lookup"><span data-stu-id="cff5c-116">You can examine the contents of each SWIFT schema in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] using the Schema Editor.</span></span> <span data-ttu-id="cff5c-117">Tous les schémas d’échange de message ont la structure courantes suivante :</span><span class="sxs-lookup"><span data-stu-id="cff5c-117">All of the message interchange schemas have the following common structure:</span></span>  
  
-   <span data-ttu-id="cff5c-118">En-têtes</span><span class="sxs-lookup"><span data-stu-id="cff5c-118">Headers</span></span>  
  
-   <span data-ttu-id="cff5c-119">Texte du message</span><span class="sxs-lookup"><span data-stu-id="cff5c-119">Message text</span></span>  
  
-   <span data-ttu-id="cff5c-120">Codes de fin</span><span class="sxs-lookup"><span data-stu-id="cff5c-120">Trailers</span></span>  
  
 <span data-ttu-id="cff5c-121">Cette section décrit les schémas d’en-tête et le code de fin.</span><span class="sxs-lookup"><span data-stu-id="cff5c-121">This section describes the header and trailer schemas.</span></span> <span data-ttu-id="cff5c-122">Le texte du message comprend la charge utile du message FIN et contient tous les champs de données à l’exception des champs contenant l’expéditeur, le récepteur et le type de message.</span><span class="sxs-lookup"><span data-stu-id="cff5c-122">The message text comprises the payload of the FIN message, and contains all of the data fields except the fields containing the sender, receiver, and message type.</span></span> <span data-ttu-id="cff5c-123">Ces trois champs sont contenus dans l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="cff5c-123">These three fields are contained in the header portion.</span></span> <span data-ttu-id="cff5c-124">Certains messages contiennent également un en-tête utilisateur facultatives qui peut-être également fournir des informations de traitement.</span><span class="sxs-lookup"><span data-stu-id="cff5c-124">Some messages also contain an optional user header, which may also provide processing information.</span></span>  
  
 <span data-ttu-id="cff5c-125">Chaque charge de message FIN se compose d’une série de champs dans un ordre défini.</span><span class="sxs-lookup"><span data-stu-id="cff5c-125">Each FIN message payload consists of a series of fields in a defined sequence.</span></span> <span data-ttu-id="cff5c-126">Ces champs sont conformes aux règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="cff5c-126">These fields conform to the following rules:</span></span>  
  
-   <span data-ttu-id="cff5c-127">Les champs peuvent être obligatoires ou facultatifs dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="cff5c-127">The fields may be required or optional within the sequence.</span></span>  
  
-   <span data-ttu-id="cff5c-128">Une séquence peut contenir sous-séquences, et une sous-séquence peut se répètent dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="cff5c-128">A sequence may contain sub-sequences, and a sub-sequence may repeat within a sequence.</span></span>  
  
-   <span data-ttu-id="cff5c-129">Vous pouvez utiliser un champ dans plusieurs types de messages.</span><span class="sxs-lookup"><span data-stu-id="cff5c-129">You can use a field in several message types.</span></span>  
  
-   <span data-ttu-id="cff5c-130">Un champ peut comporter des éléments ou sous-champs.</span><span class="sxs-lookup"><span data-stu-id="cff5c-130">Within a field, there may be elements or subfields.</span></span> <span data-ttu-id="cff5c-131">Un élément ou un sous-champ peut-être être commune à plusieurs champs.</span><span class="sxs-lookup"><span data-stu-id="cff5c-131">An element or subfield may be common to several fields.</span></span>  
  
-   <span data-ttu-id="cff5c-132">Un nœud de groupe représente chaque séquence extensible.</span><span class="sxs-lookup"><span data-stu-id="cff5c-132">A group node represents each repeating sequence.</span></span>  
  
-   <span data-ttu-id="cff5c-133">Chaque champ peut lui-même avoir plusieurs noeuds niveaux, chacune décrite comme un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="cff5c-133">Each field may itself have multiple nodal levels, each described as a record.</span></span>  
  
-   <span data-ttu-id="cff5c-134">Les éléments de schéma représentent uniquement les sous-champs au niveau le plus bas.</span><span class="sxs-lookup"><span data-stu-id="cff5c-134">Schema elements represent only the lowest level subfields.</span></span>  
  
-   <span data-ttu-id="cff5c-135">Les schémas courants et de base définissent courantes des enregistrements et des éléments.</span><span class="sxs-lookup"><span data-stu-id="cff5c-135">The common and base schemas define common records and elements.</span></span>  
  
-   <span data-ttu-id="cff5c-136">Schémas représentent certains champs dans plusieurs formats (tels que les champs de tiers).</span><span class="sxs-lookup"><span data-stu-id="cff5c-136">Schemas represent some fields in several formats (such as party fields).</span></span> <span data-ttu-id="cff5c-137">Les schémas définissent les champs de ce type en tant que champs de choix.</span><span class="sxs-lookup"><span data-stu-id="cff5c-137">Schemas define such fields as choice fields.</span></span>  
  
-   <span data-ttu-id="cff5c-138">Certains champs ont limité des ensembles de valeurs.</span><span class="sxs-lookup"><span data-stu-id="cff5c-138">Some fields have limited sets of values.</span></span> <span data-ttu-id="cff5c-139">La plupart des cas, le schéma répertorie ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="cff5c-139">For the most part, the schema lists these values.</span></span> <span data-ttu-id="cff5c-140">Définitions de schéma également incluent la validation de jeu de caractères.</span><span class="sxs-lookup"><span data-stu-id="cff5c-140">Schema definitions also include character set validation.</span></span>  
  
 <span data-ttu-id="cff5c-141">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="cff5c-141">This section contains:</span></span>  
  
-   [<span data-ttu-id="cff5c-142">Schémas de base et schémas communs</span><span class="sxs-lookup"><span data-stu-id="cff5c-142">Base and Common Schemas</span></span>](../../adapters-and-accelerators/accelerator-swift/base-and-common-schemas.md)  
  
-   [<span data-ttu-id="cff5c-143">Schémas d’en-tête et de code de fin SWIFT</span><span class="sxs-lookup"><span data-stu-id="cff5c-143">SWIFT Header and Trailer Schemas</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-header-and-trailer-schemas.md)  
  
-   [<span data-ttu-id="cff5c-144">Conventions de nommage des schémas SWIFT</span><span class="sxs-lookup"><span data-stu-id="cff5c-144">SWIFT Schema Naming Conventions</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-schema-naming-conventions.md)