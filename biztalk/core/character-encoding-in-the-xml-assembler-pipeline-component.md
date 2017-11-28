---
title: "Encodage de caractères dans le composant de Pipeline assembleur XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IBaseMessagePart.Charset property
- XMLNorm.SourceCharset property
- pipeline components, XML Assembler
- XMLNorm.TargetCharset property
- Target Charset property
- XML Assembler [pipeline component], character encoding
ms.assetid: c031fbbf-f00f-41ba-8ac9-cec7d625cef6
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82709af574e3577990cf99cd430e1a5e6a7f8485
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="character-encoding-in-the-xml-assembler-pipeline-component"></a><span data-ttu-id="2d23b-102">Encodage de caractères dans le composant de Pipeline assembleur XML</span><span class="sxs-lookup"><span data-stu-id="2d23b-102">Character Encoding in the XML Assembler Pipeline Component</span></span>
<span data-ttu-id="2d23b-103">Le composant de pipeline Assembleur XML peut produire des messages codés à l'aide de caractères spécifiés par l'utilisateur de deux manières, comme le montre le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="2d23b-103">The XML Assembler pipeline component can produce messages in user-specified character encoding in two ways, as shown in the following table.</span></span>  
  
|<span data-ttu-id="2d23b-104">Niveau de codage</span><span class="sxs-lookup"><span data-stu-id="2d23b-104">Encoding level</span></span>|<span data-ttu-id="2d23b-105">Méthode de codage</span><span class="sxs-lookup"><span data-stu-id="2d23b-105">Encoding method</span></span>|  
|--------------------|---------------------|  
|<span data-ttu-id="2d23b-106">Composant</span><span class="sxs-lookup"><span data-stu-id="2d23b-106">Component</span></span>|<span data-ttu-id="2d23b-107">Définir le **jeu de caractères cible** propriété du composant dans le Concepteur de Pipeline.</span><span class="sxs-lookup"><span data-stu-id="2d23b-107">Set the **Target charset** component property in Pipeline Designer.</span></span>|  
|<span data-ttu-id="2d23b-108">Message</span><span class="sxs-lookup"><span data-stu-id="2d23b-108">Message</span></span>|<span data-ttu-id="2d23b-109">Définir le **XMLNorm.TargetCharset** propriété dans le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="2d23b-109">Set the **XMLNorm.TargetCharset** property on the message context.</span></span> <span data-ttu-id="2d23b-110">**Remarque :** message d’une propriété de contexte remplace toujours n’importe quelle propriété de contexte définie dans le Concepteur de Pipeline.</span><span class="sxs-lookup"><span data-stu-id="2d23b-110">**Note:**  A message context property always overrides any context property set in Pipeline Designer.</span></span>|  
  
 <span data-ttu-id="2d23b-111">L'Assembleur XML utilise l'algorithme suivant pour déterminer le codage du message de sortie :</span><span class="sxs-lookup"><span data-stu-id="2d23b-111">The XML Assembler uses the following algorithm to determine output message encoding:</span></span>  
  
1.  <span data-ttu-id="2d23b-112">Si le **XMLNorm.TargetCharset** propriété de contexte est définie, sa valeur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="2d23b-112">If the **XMLNorm.TargetCharset** context property is set, its value is used.</span></span>  
  
2.  <span data-ttu-id="2d23b-113">Sinon, si le **jeu de caractères cible** propriété est spécifiée dans le Concepteur de Pipeline, sa valeur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="2d23b-113">Otherwise, if the **Target charset** property is specified in Pipeline Designer, its value is used.</span></span>  
  
3.  <span data-ttu-id="2d23b-114">Sinon, si le **XMLNorm.SourceCharset** propriété est spécifiée, sa valeur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="2d23b-114">Otherwise, if the **XMLNorm.SourceCharset** property is specified, its value is used.</span></span>  
  
4.  <span data-ttu-id="2d23b-115">Si aucune des propriétés précédentes n'est définie, le codage UTF-8 est utilisé.</span><span class="sxs-lookup"><span data-stu-id="2d23b-115">If none of the preceding properties is set, UTF-8 encoding is used.</span></span>  
  
 <span data-ttu-id="2d23b-116">L’assembleur XML enregistre les informations de codage d’un objet de message BizTalk dans le `IBaseMessagePart.Charset` propriété.</span><span class="sxs-lookup"><span data-stu-id="2d23b-116">The XML Assembler saves the encoding information of a BizTalk message object in the `IBaseMessagePart.Charset` property.</span></span> <span data-ttu-id="2d23b-117">Quand le codage Unicode ou UTF-8 est utilisé, l'Assembleur XML place toujours une marque d'ordre de tri sur les messages sortants.</span><span class="sxs-lookup"><span data-stu-id="2d23b-117">When using Unicode or UTF-8 encoding, the XML Assembler always adds the byte order mark (BOM) to outgoing messages.</span></span>  
  
 <span data-ttu-id="2d23b-118">Notez que lors de l’utilisation de la valeur par défaut d’envoi XML pipeline, qui contient le composant Assembleur XML, les documents produits peuvent être encodées en utilisant le même jeu de caractères en tant que lorsqu’ils ont été soumis au serveur, ou ils peuvent être encodées à l’aide de UTF-8 si les documents ont été créés au sein du serveur et **XMLNorm.TargetCharset** n’était pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="2d23b-118">Note that when using the default XML send pipeline, which contains the XML Assembler component, the produced documents may be encoded by using the same charset as when they were submitted into the server, or they may be encoded by using UTF-8 if documents were created within the server and **XMLNorm.TargetCharset** was not specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d23b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d23b-119">See Also</span></span>  
 <span data-ttu-id="2d23b-120">[Composant de Pipeline assembleur XML](../core/xml-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="2d23b-120">[XML Assembler Pipeline Component](../core/xml-assembler-pipeline-component.md) </span></span>  
 <span data-ttu-id="2d23b-121">[Comment configurer le composant de Pipeline assembleur XML](../core/how-to-configure-the-xml-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="2d23b-121">[How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="2d23b-122">Pipelines-AssemblerDisassembler (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="2d23b-122">Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)</span></span>](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)