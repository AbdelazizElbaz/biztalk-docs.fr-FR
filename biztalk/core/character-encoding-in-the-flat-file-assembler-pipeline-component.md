---
title: "Encodage de caractères dans le composant de Pipeline assembleur fichier plat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Flat File Assembler [pipeline component], character encoding
- IBaseMessagePart.Charset property
- pipeline components, Flat File Assembler
- Codepage property
- XMLNorm.SourceCharset property
- XMLNorm.TargetCharset property
- Target Charset property
ms.assetid: 0cf3c0fd-f036-4190-83ce-9064ef4e823c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af38855c81129cd4bafff50544f2aee15e6f3fab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="character-encoding-in-the-flat-file-assembler-pipeline-component"></a><span data-ttu-id="16c7f-102">Encodage de caractères dans le composant de Pipeline d’assembleur de fichier plat</span><span class="sxs-lookup"><span data-stu-id="16c7f-102">Character Encoding in the Flat File Assembler Pipeline Component</span></span>
<span data-ttu-id="16c7f-103">L’Assembleur de fichier plat peut produire des messages dans un codage de caractères spécifié par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="16c7f-103">The Flat File Assembler can produce messages in user-specified character encoding.</span></span> <span data-ttu-id="16c7f-104">Vous pouvez spécifier le codage de caractères à plusieurs niveaux :</span><span class="sxs-lookup"><span data-stu-id="16c7f-104">You can specify the character encoding at several levels:</span></span>  
  
-   <span data-ttu-id="16c7f-105">**Schéma.**</span><span class="sxs-lookup"><span data-stu-id="16c7f-105">**Schema.**</span></span> <span data-ttu-id="16c7f-106">Définir le **page de codes** propriété dans le schéma de fichier plat pour le document.</span><span class="sxs-lookup"><span data-stu-id="16c7f-106">Set the **codepage** property in the flat file schema for the document.</span></span>  
  
-   <span data-ttu-id="16c7f-107">**Composant.**</span><span class="sxs-lookup"><span data-stu-id="16c7f-107">**Component.**</span></span> <span data-ttu-id="16c7f-108">Définir le **jeu de caractères cible** propriété du composant dans le Concepteur de Pipeline.</span><span class="sxs-lookup"><span data-stu-id="16c7f-108">Set the **Target Charset** component property in Pipeline Designer.</span></span>  
  
-   <span data-ttu-id="16c7f-109">**Message.**</span><span class="sxs-lookup"><span data-stu-id="16c7f-109">**Message.**</span></span> <span data-ttu-id="16c7f-110">Définir le **XMLNorm.TargetCharset** propriété dans le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="16c7f-110">Set the **XMLNorm.TargetCharset** property on the message context.</span></span>  
  
 <span data-ttu-id="16c7f-111">La valeur de la propriété définie dans le contexte du message remplace toujours celle spécifiée dans Concepteur de pipeline.</span><span class="sxs-lookup"><span data-stu-id="16c7f-111">The value of the property set on a message context always overrides the one set in Pipeline Designer.</span></span> <span data-ttu-id="16c7f-112">En outre, la valeur définie dans le Concepteur de Pipeline toujours remplace la valeur définie en tant qu’un **page de codes** propriété dans un schéma de document de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="16c7f-112">Also, the value set in Pipeline Designer always overwrites the value set as a **codepage** property in a flat file document schema.</span></span>  
  
 <span data-ttu-id="16c7f-113">L’Assembleur de fichier plat utilise l’algorithme suivant pour déterminer le codage à utiliser pour un message de sortie :</span><span class="sxs-lookup"><span data-stu-id="16c7f-113">The Flat File Assembler uses the following algorithm to determine which encoding to use for an output message:</span></span>  
  
-   <span data-ttu-id="16c7f-114">Si le **XMLNorm.TargetCharset** propriété de contexte est définie, sa valeur est utilisée pour l’encodage.</span><span class="sxs-lookup"><span data-stu-id="16c7f-114">If the **XMLNorm.TargetCharset** context property is set, its value is used for encoding.</span></span>  
  
-   <span data-ttu-id="16c7f-115">Sinon, si le **jeu de caractères cible** propriété dans le Concepteur de Pipeline est spécifiée, sa valeur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="16c7f-115">Otherwise, if the **Target charset** property in Pipeline Designer is specified, its value is used.</span></span>  
  
-   <span data-ttu-id="16c7f-116">Sinon, si le **page de codes** propriété dans le schéma de fichier plat est spécifiée, sa valeur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="16c7f-116">Otherwise, if the **codepage** property in the flat file schema is specified, its value is used.</span></span>  
  
-   <span data-ttu-id="16c7f-117">Sinon, si le **XMLNorm.SourceCharset** propriété est spécifiée, sa valeur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="16c7f-117">Otherwise, if the **XMLNorm.SourceCharset** property is specified, its value is used.</span></span>  
  
-   <span data-ttu-id="16c7f-118">Autrement, la valeur « UTF-8 » est utilisée.</span><span class="sxs-lookup"><span data-stu-id="16c7f-118">Otherwise, "UTF-8" is used.</span></span> <span data-ttu-id="16c7f-119">Notez que le composant de pipeline Assembleur de fichier plat ne place pas de marque d’ordre de tri sur les messages sortants lorsque le codage UTF-8 est utilisé.</span><span class="sxs-lookup"><span data-stu-id="16c7f-119">Note that the Flat File Assembler pipeline component does not put byte order mark on outgoing messages when UTF-8 encoding is used.</span></span>  
  
 <span data-ttu-id="16c7f-120">L’assembleur de fichier plat enregistre les informations de codage dans le corps de l’objet du message BizTalk dans le **IBaseMessagePart.Charset** propriété.</span><span class="sxs-lookup"><span data-stu-id="16c7f-120">The Flat File Assembler saves encoding information on the body part of the BizTalk message object in the **IBaseMessagePart.Charset** property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16c7f-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16c7f-121">See Also</span></span>  
 <span data-ttu-id="16c7f-122">[Composant de Pipeline assembleur de fichier plat](../core/flat-file-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="16c7f-122">[Flat File Assembler Pipeline Component](../core/flat-file-assembler-pipeline-component.md) </span></span>  
 <span data-ttu-id="16c7f-123">[Comment configurer le composant de Pipeline d’assembleur de fichier plat](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="16c7f-123">[How to Configure the Flat File Assembler Pipeline Component](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="16c7f-124">Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="16c7f-124">Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)</span></span>](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)