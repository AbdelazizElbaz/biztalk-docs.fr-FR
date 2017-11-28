---
title: "Composant de Pipeline de Messages non reconnus dans l’assembleur XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XMLNorm.AllowUnrecognizedMessage property
- XML Assembler [pipeline component], unrecognized messages
- pipeline components, XML Assembler
ms.assetid: dd98512a-33a4-4b2e-977e-1b3a30747c6a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6766554374413c3d1b6a3ce385f24d4046521c91
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unrecognized-messages-in-the-xml-assembler-pipeline-component"></a><span data-ttu-id="42948-102">Messages non reconnus dans le composant de Pipeline assembleur XML</span><span class="sxs-lookup"><span data-stu-id="42948-102">Unrecognized Messages in the XML Assembler Pipeline Component</span></span>
<span data-ttu-id="42948-103">Le composant Assembleur XML traite un message comme « non reconnu » si un message :</span><span class="sxs-lookup"><span data-stu-id="42948-103">The XML Assembler component treats a message as "unrecognized" if a message has:</span></span>  
  
-   <span data-ttu-id="42948-104">n’a pas de corps ;</span><span class="sxs-lookup"><span data-stu-id="42948-104">No body part.</span></span>  
  
-   <span data-ttu-id="42948-105">a un corps vide ;</span><span class="sxs-lookup"><span data-stu-id="42948-105">An empty body part.</span></span>  
  
-   <span data-ttu-id="42948-106">n’a aucune donnée dans le corps ;</span><span class="sxs-lookup"><span data-stu-id="42948-106">No data in the body part.</span></span>  
  
-   <span data-ttu-id="42948-107">n’a pas de schéma déployé associé.</span><span class="sxs-lookup"><span data-stu-id="42948-107">No associated schema deployed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42948-108">Les messages non XML sont systématiquement traités comme non reconnus.</span><span class="sxs-lookup"><span data-stu-id="42948-108">Non-XML messages are always treated as unrecognized.</span></span>  
  
 <span data-ttu-id="42948-109">La manière dont l’assembleur XML gère un message non reconnu est contrôlée par le **XMLNorm.AllowUnrecognizedMessage** propriété de contexte de message.</span><span class="sxs-lookup"><span data-stu-id="42948-109">The manner in which the XML Assembler handles an unrecognized message is controlled by the **XMLNorm.AllowUnrecognizedMessage** message context property.</span></span>  
  
 <span data-ttu-id="42948-110">Lorsque **XMLNorm.AllowUnrecognizedMessage** a la valeur **True**, l’assembleur XML traite les documents XML comme suit :</span><span class="sxs-lookup"><span data-stu-id="42948-110">When **XMLNorm.AllowUnrecognizedMessage** is set to **True**, the XML Assembler handles XML documents as follows:</span></span>  
  
-   <span data-ttu-id="42948-111">Les messages sans corps, avec un corps vide ou avec un corps comportant des données vides sont transmis sans modification via l’assembleur.</span><span class="sxs-lookup"><span data-stu-id="42948-111">A message with no body part or with an empty body part or empty data in the body part passes unchanged through the assembler.</span></span>  
  
-   <span data-ttu-id="42948-112">Les documents sans schéma déployé associé sont transmis sans modification via l’assembleur.</span><span class="sxs-lookup"><span data-stu-id="42948-112">A document that does not have a deployed schema associated with it passes unchanged through the assembler.</span></span>  
  
-   <span data-ttu-id="42948-113">Les documents associés à un schéma déployé sont traités par l’assembleur que le schéma soit explicitement référencé dans une propriété de composant ou trouvé durant le processus de résolution de schéma.</span><span class="sxs-lookup"><span data-stu-id="42948-113">A document with an associated deployed schema is processed by the assembler (regardless of whether the schema is explicitly referenced in a component property or found during the schema resolution process).</span></span>  
  
 <span data-ttu-id="42948-114">Si **XMLNorm.AllowUnrecognizedMessage** a la valeur **False**, l’assembleur XML traite les documents XML comme suit :</span><span class="sxs-lookup"><span data-stu-id="42948-114">If **XMLNorm.AllowUnrecognizedMessage** is set to **False**, the XML Assembler handles XML documents as follows:</span></span>  
  
-   <span data-ttu-id="42948-115">Les messages sans corps, avec un corps vide ou avec un corps comportant des données vides ne sont pas traités.</span><span class="sxs-lookup"><span data-stu-id="42948-115">A message with no body part or with an empty body part or empty data in the body part is not processed.</span></span> <span data-ttu-id="42948-116">Une erreur est renvoyée et le message est interrompu.</span><span class="sxs-lookup"><span data-stu-id="42948-116">An error is reported and the message is suspended.</span></span>  
  
-   <span data-ttu-id="42948-117">Les messages sans schéma déployé associé ne sont pas traités.</span><span class="sxs-lookup"><span data-stu-id="42948-117">A message that does not have a deployed schema associated with it is not processed.</span></span> <span data-ttu-id="42948-118">Une erreur est renvoyée et le message est interrompu.</span><span class="sxs-lookup"><span data-stu-id="42948-118">An error is reported and the message is suspended.</span></span>  
  
-   <span data-ttu-id="42948-119">Les documents associés à un schéma déployé sont traités par l’assembleur que le schéma soit explicitement référencé dans une propriété de composant ou trouvé durant le processus de résolution de schéma.</span><span class="sxs-lookup"><span data-stu-id="42948-119">A document with an associated deployed schema is processed by the assembler (regardless of whether the schema is explicitly referenced in a component property or found during the schema resolution process).</span></span>  
  
-   <span data-ttu-id="42948-120">Par défaut, le composant Assembleur XML n’autorise pas les messages non reconnus (c'est-à-dire, **XMLNorm.AllowUnrecognizedMessages** est considéré comme **False** si elle n’est pas définie dans le contexte du message).</span><span class="sxs-lookup"><span data-stu-id="42948-120">By default, the XML Assembler component does not allow unrecognized messages (that is, **XMLNorm.AllowUnrecognizedMessages** is considered **False** if it is not set on the message context).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42948-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42948-121">See Also</span></span>  
 <span data-ttu-id="42948-122">[Composant de Pipeline assembleur XML](../core/xml-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="42948-122">[XML Assembler Pipeline Component](../core/xml-assembler-pipeline-component.md) </span></span>  
 <span data-ttu-id="42948-123">[Comment configurer le composant de Pipeline assembleur XML](../core/how-to-configure-the-xml-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="42948-123">[How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="42948-124">Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="42948-124">Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)</span></span>](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)