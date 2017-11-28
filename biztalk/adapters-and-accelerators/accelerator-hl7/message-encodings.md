---
title: Encodages de message | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, encodings
- messages, code samples
- encoding [messages]
- code samples
ms.assetid: 360638c0-4094-428f-a7c7-306a5f95a6bf
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36063416e1c5d1f30c9cb9c26056299f0b926a50
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-encodings"></a><span data-ttu-id="52d89-102">Encodages de message</span><span class="sxs-lookup"><span data-stu-id="52d89-102">Message Encodings</span></span>
<span data-ttu-id="52d89-103">Il n’est pas suffisante pour définir une sémantique de message dans l’ordre pour HL7 être utile.</span><span class="sxs-lookup"><span data-stu-id="52d89-103">It is not sufficient to define message semantics in order for HL7 to be useful.</span></span> <span data-ttu-id="52d89-104">Une fois que le contenu du message a été déterminé, la norme doit expliquer comment représenter ce contenu dans une interface réelle.</span><span class="sxs-lookup"><span data-stu-id="52d89-104">Once message content has been determined, the standard has to explain how to represent that content in an actual interface.</span></span> <span data-ttu-id="52d89-105">Autrement dit, il doit être spécifié « encodage de message ».</span><span class="sxs-lookup"><span data-stu-id="52d89-105">That is to say, there must be a specified "message encoding".</span></span> <span data-ttu-id="52d89-106">HL7 Version 2 prend en charge deux formes d’encodage de message, un encodage d’en fonction du délimiteur personnalisé et un encodage XML.</span><span class="sxs-lookup"><span data-stu-id="52d89-106">HL7 Version 2 supports two forms of message encoding, a custom delimiter-based encoding, and an XML encoding.</span></span>  
  
 <span data-ttu-id="52d89-107">HL7 a choisi le codage d’origine en fonction du délimiteur pour réduire la taille des messages autant que possibles.</span><span class="sxs-lookup"><span data-stu-id="52d89-107">HL7 chose the original delimiter-based encoding to reduce the size of messages as much as possible.</span></span> <span data-ttu-id="52d89-108">Par exemple, si vous comparez une structure de données dans laquelle délimiteurs de séparer les éléments vers une structure qui positionne chaque élément dans un ensemble fixe de positions, la structure en fonction du délimiteur est beaucoup plus économique si des messages a) ne contiennent pas certains éléments et (b) certaines éléments ne remplissent pas tout l’espace autorisé.</span><span class="sxs-lookup"><span data-stu-id="52d89-108">For example, if you compare a data structure in which delimiters separate elements to a structure that positions each element in a fixed set of positions, the delimiter-based structure is far more economical if a) messages do not contain some elements, and b) some elements do not fill all the space allowed.</span></span> <span data-ttu-id="52d89-109">La seule surcharge dans les structures en fonction du délimiteur est les délimiteurs eux-mêmes.</span><span class="sxs-lookup"><span data-stu-id="52d89-109">The only overhead in delimiter-based structures is the delimiters themselves.</span></span>  
  
 <span data-ttu-id="52d89-110">L’encodage HL7 d’origine définit cinq séparateurs, qui déclare de chaque message dans le segment MSH.</span><span class="sxs-lookup"><span data-stu-id="52d89-110">The original HL7 encoding defines five delimiters, which each message declares within the MSH segment.</span></span> <span data-ttu-id="52d89-111">Celles-ci indiquent :</span><span class="sxs-lookup"><span data-stu-id="52d89-111">These indicate:</span></span>  
  
-   <span data-ttu-id="52d89-112">Segments</span><span class="sxs-lookup"><span data-stu-id="52d89-112">Segments</span></span>  
  
-   <span data-ttu-id="52d89-113">Champs</span><span class="sxs-lookup"><span data-stu-id="52d89-113">Fields</span></span>  
  
-   <span data-ttu-id="52d89-114">Components</span><span class="sxs-lookup"><span data-stu-id="52d89-114">Components</span></span>  
  
-   <span data-ttu-id="52d89-115">Sous-composants</span><span class="sxs-lookup"><span data-stu-id="52d89-115">Subcomponents</span></span>  
  
-   <span data-ttu-id="52d89-116">Répétition (d’un champ, un composant ou un sous-composant)</span><span class="sxs-lookup"><span data-stu-id="52d89-116">Repetition (of a field, component, or subcomponent)</span></span>  
  
 <span data-ttu-id="52d89-117">Notez que puisque les délimiteurs sont un aspect fondamental de l’encodage, vous devez les définir tout d’abord.</span><span class="sxs-lookup"><span data-stu-id="52d89-117">Note that since delimiters are a fundamental aspect of the encoding, you must define them first.</span></span> <span data-ttu-id="52d89-118">Il en découle est qu’il ne peut y avoir aucun sous-répertoire sub-séparateur de.</span><span class="sxs-lookup"><span data-stu-id="52d89-118">One result of this is that there can be no sub-sub-delimiter.</span></span> <span data-ttu-id="52d89-119">Dans certains cas, cette limitation a des effets fâcheux lors de la conception de nouveaux types de données.</span><span class="sxs-lookup"><span data-stu-id="52d89-119">At times, this limitation has unfortunate effects upon the design of new data types.</span></span>  
  
 <span data-ttu-id="52d89-120">En juin 2003, HL7 publié HL7 Version 2, syntaxe d’encodage XML, version 1.</span><span class="sxs-lookup"><span data-stu-id="52d89-120">In June 2003, HL7 published HL7 Version 2, XML Encoding Syntax, Release 1.</span></span> <span data-ttu-id="52d89-121">Cette norme définit d’autres règles de codage pour les messages HL7 Version 2.3.1 et 2.4 et fournit un mécanisme permettant de déterminer les autres règles de codage pour HL7 ultérieures versions 2.X.</span><span class="sxs-lookup"><span data-stu-id="52d89-121">This standard defines alternate encoding rules for HL7 Version 2.3.1 and 2.4 messages, and provides a mechanism for determining alternate encoding rules for subsequent HL7 2.X versions.</span></span> <span data-ttu-id="52d89-122">Fondamentalement, cette nouvelle norme définit les balises d’éléments XML pour la Version 2.3.1 V2.4 messages abstraits, segments, les champs et les types de données et crée des règles pour définir les balises nécessaires pour les nouvelles structures créés pour les versions ultérieures de la Version 2 standards.</span><span class="sxs-lookup"><span data-stu-id="52d89-122">In essence, this new standard defines XML element tags for the Version 2.3.1 and V2.4 abstract messages, segments, fields, and data types, and creates rules for defining the tags needed for any new structures created for subsequent versions of the Version 2 standard.</span></span> <span data-ttu-id="52d89-123">Le processus de définition de cette norme conduit à une série d’améliorations dans les versions 2.4 et 2.5.</span><span class="sxs-lookup"><span data-stu-id="52d89-123">The process of defining this standard led to a series of improvements in versions 2.4 and 2.5.</span></span> <span data-ttu-id="52d89-124">Cela s’est produite, car la création de balises XML a conduit à la nécessité de prendre quelques ambiguïtés commune dans la norme sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="52d89-124">This happened because creation of XML tags led to the need to address some longstanding ambiguities in the underlying standard.</span></span> <span data-ttu-id="52d89-125">As a result, les codes de structure de message a) bien définis ont été créés pour indiquer les variations dans les messages abstraites associés aux événements de déclencheur, (b) répétition de groupes de segments avec un message abstrait ont été officiellement identifiés et nommés et c) localement type de données défini, CM a été remplacée par des types plus spécifiques.</span><span class="sxs-lookup"><span data-stu-id="52d89-125">As a result, a) well-defined message structure codes were created to indicate variations in the abstract messages associated with trigger events, b) repeating groups of segments with an abstract message were formally identified and named, and c) the locally defined data type, CM was replaced with more specific types.</span></span>  
  
 <span data-ttu-id="52d89-126">Voici, par exemple, un message d’accusé de réception simple en utilisant le format de canal traditionnel délimitée par des :</span><span class="sxs-lookup"><span data-stu-id="52d89-126">For example, the following is a simple acknowledgment message using the traditional pipe delimited format:</span></span>  
  
```  
MSH|^~\&|LAB|767543|ADT|767543|199003141304-0500||ACK^^ACK|XX3657|P|2.4  
MSA|AR|ZZ9380  
ERR|PID^1^16^103&Table value not found&HL70357  
```  
  
 <span data-ttu-id="52d89-127">Le même message représenté sous la forme d’un document XML sont en revanche, les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="52d89-127">By contrast, the following is the same message represented as an XML document:</span></span>  
  
```  
<ACK  
xmlns="urn:hl7-org:v2xml"  
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
xsi:schemaLocation="urn:hl7-org:v2xml ACK.xsd">  
   <MSH>  
      <MSH.1>|</MSH.1>  
      <MSH.2>^~\&</MSH.2>  
      <MSH.3>  
         <HD.1>LAB</HD.1>  
      </MSH.3>  
      <MSH.4>  
         <HD.1>767543</HD.1>  
      </MSH.4>  
      <MSH.5>  
         <HD.1>ADT</HD.1>  
      </MSH.5>  
      <MSH.6>  
         <HD.1>767543</HD.1>  
      </MSH.6>  
      <MSH.7>  
         <TS.1>199003141304-0500</TS.1>  
      </MSH.7>  
      <MSH.9>  
         <MSG.1>ACK</MSG.1>  
         <MSG.3>ACK</MSG.3>  
      </MSH.9>  
      <MSH.10>XX3657</MSH.10>  
      <MSH.11>  
         <PT.1>P</PT.1>  
      </MSH.11>  
      <MSH.12>  
         <VID.1>2.4</VID.1>  
      </MSH.12>  
   </MSH>  
   <MSA>  
      <MSA.1>AR</MSA.1>  
      <MSA.2>ZZ9380</MSA.2>  
   </MSA>  
   <ERR>  
      <ERR.1>  
         <ELD.1>PID</ELD.1>  
         <ELD.2>1</ELD.2>  
         <ELD.3>16</ELD.3>  
         <ELD.4>  
            <CE.1>103</CE.1>  
            <CE.2>Table value not found</CE.2>  
            <CE.3>HL70357</CE.3>  
         </ELD.4>  
      </ERR.1>  
   </ERR>  
</ACK>  
```  
  
 <span data-ttu-id="52d89-128">Les fonctions suivantes de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) prend en charge ces exigences :</span><span class="sxs-lookup"><span data-stu-id="52d89-128">The following functions of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) support these requirements:</span></span>  
  
-   <span data-ttu-id="52d89-129">Prise en charge de canal délimités et l’encodage XML.</span><span class="sxs-lookup"><span data-stu-id="52d89-129">Support of pipe delimited and XML encoding.</span></span>  
  
-   <span data-ttu-id="52d89-130">Prise en charge de la traduction entre XML et canal délimitée par des encodages.</span><span class="sxs-lookup"><span data-stu-id="52d89-130">Support of translation between XML and pipe delimited encodings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52d89-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52d89-131">See Also</span></span>  
 <span data-ttu-id="52d89-132">[Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="52d89-132">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="52d89-133">[Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="52d89-133">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="52d89-134">L’utilisation des schémas 2.X HL7</span><span class="sxs-lookup"><span data-stu-id="52d89-134">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)