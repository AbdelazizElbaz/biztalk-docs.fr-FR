---
title: "Échec de Messages et les objets ErrorCollection | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- failed messages, ErrorCollection objects
- ErrorCollection objects
ms.assetid: 8a2ff3b5-d7a0-4595-8b74-3133e9e3a821
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65598ef44bfe3e34bd1695aa81bee368c5175793
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="failed-messages-and-errorcollection-objects"></a><span data-ttu-id="f205e-102">Messages d’échec et les objets ErrorCollection</span><span class="sxs-lookup"><span data-stu-id="f205e-102">Failed Messages and ErrorCollection Objects</span></span>
<span data-ttu-id="f205e-103">Outre le fait de décorer un message ayant échoué avec les propriétés promues, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] publie le message ayant échoué dans la base de données MessageBox avec un message supplémentaire *partie*, appelé **ErrorSegment** .</span><span class="sxs-lookup"><span data-stu-id="f205e-103">In addition to decorating a failed message with promoted properties, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] publishes the failed message to the MessageBox database with an additional message *part*, called **ErrorSegment**.</span></span> <span data-ttu-id="f205e-104">Cette partie de l’erreur contient le XML représentant un **ErrorCollection** objet.</span><span class="sxs-lookup"><span data-stu-id="f205e-104">This error part contains XML representing an **ErrorCollection** object.</span></span> <span data-ttu-id="f205e-105">Le désassembleur A4SWIFT remplit la **ErrorCollection** l’objet au cours de chaque étape de traitement (analyse, validation XML et la validation du moteur de règles d’entreprise (BRE)) du message.</span><span class="sxs-lookup"><span data-stu-id="f205e-105">The A4SWIFT disassembler populates the **ErrorCollection** object during each stage of message processing (parsing, XML validation, and Business Rule Engine (BRE) validation).</span></span>  
  
 <span data-ttu-id="f205e-106">Le **ErrorCollection** objet est une collection de *des objets d’erreur*, chacun représentant une erreur particulière ou une défaillance lors du traitement du message.</span><span class="sxs-lookup"><span data-stu-id="f205e-106">The **ErrorCollection** object is a collection of *error objects*, each of which represents a particular error or failure during message processing.</span></span> <span data-ttu-id="f205e-107">Les objets d’erreurs individuels contiennent plus d’informations sur une seule erreur (par exemple, l’emplacement dans le message et une description de l’échec).</span><span class="sxs-lookup"><span data-stu-id="f205e-107">The individual error objects contain details about a single failure (such as the location in the message and a description of the failure).</span></span>  
  
 <span data-ttu-id="f205e-108">Pour plus d’informations sur la **ErrorCollection** application programming interface (API) et les détails d’utilisation, consultez la classe de ErrorCollection.</span><span class="sxs-lookup"><span data-stu-id="f205e-108">For more information about the **ErrorCollection** application programming interface (API) and usage details, see ErrorCollection Class.</span></span> <span data-ttu-id="f205e-109">Pour plus d’informations sur les objets d’erreur individuels, consultez ErrorBase, classe (classe de base pour les objets d’erreur), classe de BreValidationError, ParseError classe et XmlValidationError classe.</span><span class="sxs-lookup"><span data-stu-id="f205e-109">For more information about individual error objects, see ErrorBase Class (the base class for error objects), BreValidationError Class, ParseError Class, and XmlValidationError Class.</span></span>  
  
 <span data-ttu-id="f205e-110">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="f205e-110">This section contains:</span></span>  
  
-   [<span data-ttu-id="f205e-111">Extension de la Solution pour la Capture et la réparation de messages</span><span class="sxs-lookup"><span data-stu-id="f205e-111">Extending the Solution for Capture and Message Repair</span></span>](../../adapters-and-accelerators/accelerator-swift/extending-the-solution-for-capture-and-message-repair.md)