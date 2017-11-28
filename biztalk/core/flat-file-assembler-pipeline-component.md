---
title: Composant de Pipeline assembleur de fichier en 2D | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, Flat File Assembler
- Flat File Assembler [pipeline component]
ms.assetid: 3c851771-55b2-4d21-9291-d707dd66837c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 385b1f8ea6c2ce707069cde522ea2f6712290be7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="flat-file-assembler-pipeline-component"></a><span data-ttu-id="edef2-102">Composant de Pipeline assembleur de fichier plat</span><span class="sxs-lookup"><span data-stu-id="edef2-102">Flat File Assembler Pipeline Component</span></span>
<span data-ttu-id="edef2-103">Un Assembleur de fichier plat combine des documents individuels en un lot et y ajoute éventuellement un en-tête ou un code de fin (ou les deux).</span><span class="sxs-lookup"><span data-stu-id="edef2-103">A Flat File Assembler combines individual documents into a batch and optionally adds a header or trailer (or both) to it.</span></span> <span data-ttu-id="edef2-104">Pour plus d’informations sur les fichiers plats, consultez [des Messages de fichiers plats avec enregistrements délimités](../core/flat-file-messages-with-delimited-records.md).</span><span class="sxs-lookup"><span data-stu-id="edef2-104">For more information about flat files, see [Flat File Messages with Delimited Records](../core/flat-file-messages-with-delimited-records.md).</span></span> <span data-ttu-id="edef2-105">Consultez également [des Messages de fichiers plats avec enregistrements positionnels](../core/flat-file-messages-with-positional-records.md).</span><span class="sxs-lookup"><span data-stu-id="edef2-105">Also see [Flat File Messages with Positional Records](../core/flat-file-messages-with-positional-records.md).</span></span>  
  
 <span data-ttu-id="edef2-106">Le composant de pipeline Assembleur de fichier plat ne valide pas le message XML entrant.</span><span class="sxs-lookup"><span data-stu-id="edef2-106">The Flat File Assembler pipeline component does not validate the incoming XML message.</span></span> <span data-ttu-id="edef2-107">Pour garantir la validation XML, intégrez le composant Valideur XML à la phase de préassemblage du pipeline d’envoi.</span><span class="sxs-lookup"><span data-stu-id="edef2-107">To ensure XML validation, include the XML Validator component in the Pre-Assemble stage of the send pipeline.</span></span>  
  
 <span data-ttu-id="edef2-108">Le composant de pipeline Assembleur de fichier plat ne prend en charge que les conversions acceptées par Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="edef2-108">The Flat File Assembler pipeline component only supports conversions supported by the Microsoft .NET Framework.</span></span> <span data-ttu-id="edef2-109">Tout autre forme de conversion peut être effectuée en écrivant dans un rédacteur de texte personnalisé.</span><span class="sxs-lookup"><span data-stu-id="edef2-109">Any additional conversion can be done by writing to a custom text writer.</span></span>  
  
 <span data-ttu-id="edef2-110">Pour plus d’informations sur la configuration du composant de pipeline assembleur de fichier plat, consultez [comment configurer le composant de Pipeline assembleur de fichier plat](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md).</span><span class="sxs-lookup"><span data-stu-id="edef2-110">For information about configuring the Flat File Assembler pipeline component, see [How to Configure the Flat File Assembler Pipeline Component](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="edef2-111">Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous ne pouvez pas assembler les messages en un échange.</span><span class="sxs-lookup"><span data-stu-id="edef2-111">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you cannot assemble messages into one interchange.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="edef2-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="edef2-112">In This Section</span></span>  
  
-   [<span data-ttu-id="edef2-113">Encodage de caractères dans le composant de Pipeline d’assembleur de fichier plat</span><span class="sxs-lookup"><span data-stu-id="edef2-113">Character Encoding in the Flat File Assembler Pipeline Component</span></span>](../core/character-encoding-in-the-flat-file-assembler-pipeline-component.md)  
  
-   [<span data-ttu-id="edef2-114">Mise en œuvre de Structure de document dans le composant de Pipeline assembleur fichier plat</span><span class="sxs-lookup"><span data-stu-id="edef2-114">Document Structure Enforcement in the Flat File Assembler Pipeline Component</span></span>](../core/document-structure-enforcement-in-the-flat-file-assembler-pipeline-component.md)  
  
-   [<span data-ttu-id="edef2-115">Conservation des délimiteurs dans le composant de Pipeline d’assembleur de fichier plat</span><span class="sxs-lookup"><span data-stu-id="edef2-115">Retaining Delimiters in the Flat File Assembler Pipeline Component</span></span>](../core/retaining-delimiters-in-the-flat-file-assembler-pipeline-component.md)