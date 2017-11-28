---
title: "Composant de Pipeline de Messages non reconnus dans le désassembleur XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Allow Unrecognized Messages property
- XMLNorm.AllowUnrecognizedMessage property
- pipeline components, XML Disassembler
- XML Disassembler [pipeline component], unrecognized messages
ms.assetid: 5a6be3a8-0bac-426a-bf0b-5091191091de
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d82396002ff9d35484af5f0000dc3468c8ad37fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unrecognized-messages-in-the-xml-disassembler-pipeline-component"></a><span data-ttu-id="8869d-102">Messages non reconnus dans le composant de Pipeline désassembleur XML</span><span class="sxs-lookup"><span data-stu-id="8869d-102">Unrecognized Messages in the XML Disassembler Pipeline Component</span></span>
<span data-ttu-id="8869d-103">Le composant Désassembleur XML est susceptible de traiter un message comme « non reconnu » dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="8869d-103">The XML Disassembler component may handle a message as "unrecognized" in the following cases:</span></span>  
  
-   <span data-ttu-id="8869d-104">Lorsque le corps du message XML reçu est absent, vide ou qu'il comporte des données vides.</span><span class="sxs-lookup"><span data-stu-id="8869d-104">An XML message is received with no body, an empty body, or empty data in the body.</span></span>  
  
-   <span data-ttu-id="8869d-105">Lorsqu'un message XML a été reçu mais qu'aucun schéma n'est déployé à son intention.</span><span class="sxs-lookup"><span data-stu-id="8869d-105">An XML message is received but no schema is deployed for it.</span></span>  
  
 <span data-ttu-id="8869d-106">Un message non reconnu est géré selon le **autoriser un message non reconnu** propriété (ou, dans le **XMLNorm.AllowUnrecognizedMessage** propriété du contexte de message).</span><span class="sxs-lookup"><span data-stu-id="8869d-106">An unrecognized message is handled based on the **Allow Unrecognized Messages** property (or on the **XMLNorm.AllowUnrecognizedMessage** property on the message context).</span></span>  
  
 <span data-ttu-id="8869d-107">Si **autoriser un message non reconnu** a la valeur **True**, les éléments suivants se produisent :</span><span class="sxs-lookup"><span data-stu-id="8869d-107">If **Allow Unrecognized Messages** is set to **True**, the following occurs:</span></span>  
  
-   <span data-ttu-id="8869d-108">Les messages sans corps, avec un corps vide/nul ou avec un corps comportant des données vides/nulles sont transmis sans modification via le Désassembleur XML.</span><span class="sxs-lookup"><span data-stu-id="8869d-108">A message with no body, an empty/null body, or with empty/null data in the body passes unchanged through the XML Disassembler.</span></span>  
  
-   <span data-ttu-id="8869d-109">Les documents XML sans schéma déployé associé sont transmis sans modification via le Désassembleur XML.</span><span class="sxs-lookup"><span data-stu-id="8869d-109">An XML document with no associated deployed schema passes unchanged through the XML Disassembler.</span></span>  
  
-   <span data-ttu-id="8869d-110">Les documents XML associés à un schéma déployé sont traités par le Désassembleur XML que le schéma soit explicitement référencé dans une propriété de composant ou trouvé durant le processus de résolution de schéma.</span><span class="sxs-lookup"><span data-stu-id="8869d-110">An XML document that has a deployed schema associated with it is processed by the XML Disassembler regardless of whether the schema is explicitly referenced in a component property or found during the schema resolution process.</span></span>  
  
 <span data-ttu-id="8869d-111">Si **autoriser un message non reconnu** a la valeur **False**, les éléments suivants se produisent :</span><span class="sxs-lookup"><span data-stu-id="8869d-111">If **Allow Unrecognized Messages** is set to **False**, the following occurs:</span></span>  
  
-   <span data-ttu-id="8869d-112">Les messages sans corps ou avec un corps vide/nul ou avec un corps comportant des données vides/nulles ne sont pas transmis via le Désassembleur XML.</span><span class="sxs-lookup"><span data-stu-id="8869d-112">A message with no body or an empty/null body or with empty/null data in the body is not passed through the XML Disassembler.</span></span>  
  
-   <span data-ttu-id="8869d-113">Les documents XML sans schéma déployé associé ne sont pas transmis via le désassembleur.</span><span class="sxs-lookup"><span data-stu-id="8869d-113">An XML document that does not have a deployed schema associated with it is not passed through the disassembler.</span></span> <span data-ttu-id="8869d-114">Une erreur est renvoyée et le message est interrompu, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="8869d-114">An error is reported and the message is suspended, if possible.</span></span>  
  
-   <span data-ttu-id="8869d-115">Les documents XML associés à un schéma déployé sont traités par le Désassembleur XML que le schéma soit explicitement référencé dans une propriété de composant ou trouvé durant le processus de résolution de schéma.</span><span class="sxs-lookup"><span data-stu-id="8869d-115">An XML document that has a deployed schema associated with it is processed by the XML Disassembler regardless of whether the schema is explicitly referenced in a component property or found during the schema resolution process.</span></span>  
  
 <span data-ttu-id="8869d-116">Par défaut, le Désassembleur XML n'autorise pas les messages non reconnus.</span><span class="sxs-lookup"><span data-stu-id="8869d-116">By default, the XML Disassembler does not allow unrecognized messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8869d-117">Les messages non XML ne sont pas traités par le désassembleur XML, quel que soit le **autoriser un message non reconnu** paramètre de propriété.</span><span class="sxs-lookup"><span data-stu-id="8869d-117">Non-XML messages are not processed by the XML Disassembler regardless of the **Allow Unrecognized Messages** property setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8869d-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8869d-118">See Also</span></span>  
 <span data-ttu-id="8869d-119">[Composant de Pipeline désassembleur XML](../core/xml-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="8869d-119">[XML Disassembler Pipeline Component](../core/xml-disassembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="8869d-120">Comment configurer le composant de Pipeline désassembleur XML</span><span class="sxs-lookup"><span data-stu-id="8869d-120">How to Configure the XML Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)