---
title: Application de la Structure dans le composant de Pipeline assembleur fichier plat de document | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, Flat File Assembler
- Flat File Assembler [pipeline component], document structure
ms.assetid: 3ac75706-1d4d-443a-a4bf-af8f79a6a092
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb35c7b31eda69d03d532d13d975d618d4f36f76
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="document-structure-enforcement-in-the-flat-file-assembler-pipeline-component"></a><span data-ttu-id="1d287-102">Mise en œuvre de Structure de document dans le composant de Pipeline assembleur fichier plat</span><span class="sxs-lookup"><span data-stu-id="1d287-102">Document Structure Enforcement in the Flat File Assembler Pipeline Component</span></span>
<span data-ttu-id="1d287-103">Si des schémas de document ou d'enveloppe sont référencés explicitement dans l'Assembleur de fichier plat, ce dernier s'assure que seuls les documents dont le type de message correspond aux schémas référencés sont traités.</span><span class="sxs-lookup"><span data-stu-id="1d287-103">If document or envelope schemas are explicitly referenced in the Flat File Assembler, the Flat File Assembler ensures that only documents with the message type corresponding to referenced schemas are processed.</span></span> <span data-ttu-id="1d287-104">Les autres documents ne sont pas traités, même si un schéma est déployé pour eux.</span><span class="sxs-lookup"><span data-stu-id="1d287-104">All the other documents are not processed even though a schema may be deployed for them.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d287-105">Le schéma d'enveloppe est extrait du premier message uniquement.</span><span class="sxs-lookup"><span data-stu-id="1d287-105">The envelope schema is taken from the first message only.</span></span> <span data-ttu-id="1d287-106">Les propriétés de l'enveloppe sont toujours extraites du premier message.</span><span class="sxs-lookup"><span data-stu-id="1d287-106">The properties for the envelope are always taken from the first message.</span></span>