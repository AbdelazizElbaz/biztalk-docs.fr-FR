---
title: Traitement des fichiers plats BTAHL72X | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ACKs
- 2.X messages, disassembler
- property promotion, MSH-header schemas
- disassembler, validating messages
- HL7, errors
- 2.X messages, validating headers
- acknowledgements, generating
- assembler, validating messages
- messages, multi-part messages
- property promotion, property schemas
- generating aknowledgements
- messages, 2.X messages
- schemas, MSH-header schemas
- 2.X messages, validating message bodies
- 2.X messages
- schemas, property schemas
- message modes, 2.X messages
- errors, HL7 error format
- flat files
- validating, messages
- schemas, property promotion
- headers, validating
- 2.X messages, message modes
- 2.X messages, header validation
- 2.X messages, parsing flat files
ms.assetid: c92e2f70-0bfa-4bc8-8044-4a6e62cabee3
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b15d21653b9f0d6109487677484506c7a5d6bcc2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="btahl72x-flat-file-processing"></a><span data-ttu-id="2e4b2-102">Traitement des fichiers plats BTAHL72X</span><span class="sxs-lookup"><span data-stu-id="2e4b2-102">BTAHL72X Flat File Processing</span></span>
<span data-ttu-id="2e4b2-103">Les composants suivants dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) processus HL7 2.X (HL7 messages codés au format) :</span><span class="sxs-lookup"><span data-stu-id="2e4b2-103">The following components in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) process HL7 2.X (HL7-encoded) messages:</span></span>  
  
-   <span data-ttu-id="2e4b2-104">Pipelines et les bibliothèques principales : [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. PipelineCommon.dll et [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. PipelineMessageCore.dll</span><span class="sxs-lookup"><span data-stu-id="2e4b2-104">Pipelines and core libraries: [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].PipelineCommon.dll and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].PipelineMessageCore.dll</span></span>  
  
-   <span data-ttu-id="2e4b2-105">Bibliothèques d’assembleur et désassembleur : [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. HL72fAsm.dll et [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. HL72fDAsm.dll</span><span class="sxs-lookup"><span data-stu-id="2e4b2-105">Assembler and disassembler libraries: [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL72fAsm.dll and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL72fDAsm.dll</span></span>  
  
-   <span data-ttu-id="2e4b2-106">Adaptateur d’envoi de la bibliothèque de validation d’accusé de réception (ACK) utilisée pour le MLLP bidirectionnelle : [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. HL7ACKHelper.dll</span><span class="sxs-lookup"><span data-stu-id="2e4b2-106">The acknowledgment (ACK) validation library used for the two-way MLLP send adapter: [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL7ACKHelper.dll</span></span>  
  
## <a name="hl7-message-modes"></a><span data-ttu-id="2e4b2-107">HL7 Modes de Message</span><span class="sxs-lookup"><span data-stu-id="2e4b2-107">HL7 Message Modes</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="2e4b2-108">prend en charge les modes de message suivants pour les messages 2.X :</span><span class="sxs-lookup"><span data-stu-id="2e4b2-108"> supports the following message modes for 2.X messages:</span></span>  
  
-   <span data-ttu-id="2e4b2-109">Mode éditeur-abonné (pub-sub)</span><span class="sxs-lookup"><span data-stu-id="2e4b2-109">Publisher-subscriber (pub-sub) mode</span></span>  
  
     <span data-ttu-id="2e4b2-110">Le serveur de publication diffuse à un tiers d’abonnés, comme déclaratives ou une non sollicité mise à jour.</span><span class="sxs-lookup"><span data-stu-id="2e4b2-110">The publisher broadcasts to a party of subscribers, either as declarative or an unsolicited update.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2e4b2-111">et [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] fournissent une grande souplesse pour ce mode, étant donné que vous pouvez gérer les abonnements et les parties après le moment du design.</span><span class="sxs-lookup"><span data-stu-id="2e4b2-111"> and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] provide flexibility to this mode, since you can manage subscriptions and parties after design time.</span></span>  
  
-   <span data-ttu-id="2e4b2-112">Mode de requête-réponse</span><span class="sxs-lookup"><span data-stu-id="2e4b2-112">Request-response mode</span></span>  
  
     <span data-ttu-id="2e4b2-113">Un échange de messages interrogative ou d’une requête dans lequel une demande spécifique à partir d’une entité spécifique génère un message de répond.</span><span class="sxs-lookup"><span data-stu-id="2e4b2-113">An interrogative or query message exchange in which a specific request from a specific entity results in a responding message.</span></span>  
  
## <a name="flat-file-parsing"></a><span data-ttu-id="2e4b2-114">Analyse de fichier plat</span><span class="sxs-lookup"><span data-stu-id="2e4b2-114">Flat File Parsing</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="2e4b2-115">messages à parties multiples 2.X analyse HL7 en trois parties :</span><span class="sxs-lookup"><span data-stu-id="2e4b2-115"> parses HL7 2.X multi-part messages into three parts:</span></span>  
  
-   <span data-ttu-id="2e4b2-116">Partie d’en-tête-MSH</span><span class="sxs-lookup"><span data-stu-id="2e4b2-116">Header-MSH part</span></span>  
  
-   <span data-ttu-id="2e4b2-117">Partie du corps</span><span class="sxs-lookup"><span data-stu-id="2e4b2-117">Body part</span></span>  
  
-   <span data-ttu-id="2e4b2-118">Partie de Z</span><span class="sxs-lookup"><span data-stu-id="2e4b2-118">Z part</span></span>  
  
## <a name="hl7-header-validation"></a><span data-ttu-id="2e4b2-119">HL7 Validation de l’en-tête</span><span class="sxs-lookup"><span data-stu-id="2e4b2-119">HL7 Header Validation</span></span>  
 <span data-ttu-id="2e4b2-120">Le HL7 désassembleur et assembleur effectuent une validation structurelle et schématique de l’en-tête d’un message 2.X, afin de vérifier qu’il peut traiter le message.</span><span class="sxs-lookup"><span data-stu-id="2e4b2-120">The HL7 disassembler and assembler perform structural and schematic validation of the header of a 2.X message, in order to verify that it can process the message.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="2e4b2-121">base de la validation de schéma sur le schéma d’en-tête commun, MSH_25_GLO_DEF.</span><span class="sxs-lookup"><span data-stu-id="2e4b2-121"> bases the schematic validation on the common header schema, MSH_25_GLO_DEF.</span></span>  
  
 <span data-ttu-id="2e4b2-122">Par exemple, l’analyseur détermine que les champs MSH1 et où MSH2 a été sont bien formés.</span><span class="sxs-lookup"><span data-stu-id="2e4b2-122">For instance, the parser determines that the MSH1 and MSH2 fields are well formed.</span></span> <span data-ttu-id="2e4b2-123">MSH1 doit avoir qu’un seul caractère.</span><span class="sxs-lookup"><span data-stu-id="2e4b2-123">MSH1 must have only one character.</span></span> <span data-ttu-id="2e4b2-124">Où MSH2 a été doit être comprise entre deux et quatre caractères, et aucun caractère ne peut se répéter.</span><span class="sxs-lookup"><span data-stu-id="2e4b2-124">MSH2 must be between two and four characters, and no characters can repeat.</span></span>  
  
## <a name="hl7-body-validation"></a><span data-ttu-id="2e4b2-125">HL7 Validation du corps</span><span class="sxs-lookup"><span data-stu-id="2e4b2-125">HL7 Body Validation</span></span>  
 <span data-ttu-id="2e4b2-126">Le HL7 désassembleur et assembleur effectuent une validation structurelle de base du corps d’un message 2.X et la validation de schéma, si vous l’activez.</span><span class="sxs-lookup"><span data-stu-id="2e4b2-126">The HL7 disassembler and assembler perform basic structural validation of the body of a 2.X message, and schematic validation, if you enable it.</span></span>  
  
 <span data-ttu-id="2e4b2-127">La validation structurelle de base du corps, lequel [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] toujours effectue, consiste à vérifier les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="2e4b2-127">The basic structural validation of the body, which [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] always performs, includes verifying the following:</span></span>  
  
-   <span data-ttu-id="2e4b2-128">Qu’il n’y a trois caractères dans des segments</span><span class="sxs-lookup"><span data-stu-id="2e4b2-128">That there are three characters in segments</span></span>  
  
-   <span data-ttu-id="2e4b2-129">Que le délimiteur de segment est \<CR > ou \<CR >\<LF > (facultatif pour le dernier segment)</span><span class="sxs-lookup"><span data-stu-id="2e4b2-129">That the segment delimiter is \<CR> or \<CR>\<LF> (optional for the last segment)</span></span>  
  
-   <span data-ttu-id="2e4b2-130">Conviennent de séparateurs de champs</span><span class="sxs-lookup"><span data-stu-id="2e4b2-130">That field delimiters are appropriate</span></span>  
  
-   <span data-ttu-id="2e4b2-131">Qu’il n’y a aucun segment déclaré (avec une balise de segment de trois caractères défini) dans un segment Z non déclaré</span><span class="sxs-lookup"><span data-stu-id="2e4b2-131">That there are no declared segments (with a defined three-character segment tag) in an undeclared Z segment</span></span>  
  
 <span data-ttu-id="2e4b2-132">Validation de schéma plus étendue du corps inclut les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="2e4b2-132">More extensive schema validation of the body includes the following:</span></span>  
  
-   <span data-ttu-id="2e4b2-133">Délimiteurs de fin de champ</span><span class="sxs-lookup"><span data-stu-id="2e4b2-133">Trailing-field delimiters</span></span>  
  
     <span data-ttu-id="2e4b2-134">Dans le segment d’en-tête-MSH et segments de corps</span><span class="sxs-lookup"><span data-stu-id="2e4b2-134">In Header-MSH segment and body segments</span></span>  
  
-   <span data-ttu-id="2e4b2-135">Segment de Z</span><span class="sxs-lookup"><span data-stu-id="2e4b2-135">Z segment</span></span>  
  
-   <span data-ttu-id="2e4b2-136">Type de données pris en charge XSD et personnalisées</span><span class="sxs-lookup"><span data-stu-id="2e4b2-136">XSD-supported and custom data type</span></span>  
  
     <span data-ttu-id="2e4b2-137">XSD prises en charge et les types de non XSD (TS (date), DT (date), TM (heure) et TN (numéro de téléphone)</span><span class="sxs-lookup"><span data-stu-id="2e4b2-137">XSD supported and non-XSD types (TS (Time Stamp), DT (date), TM (time), and TN (telephone number)</span></span>  
  
-   <span data-ttu-id="2e4b2-138">Énumérations</span><span class="sxs-lookup"><span data-stu-id="2e4b2-138">Enumerations</span></span>  
  
     <span data-ttu-id="2e4b2-139">ID (tables définies par l’HL7) et IS (tables définies par l’utilisateur)</span><span class="sxs-lookup"><span data-stu-id="2e4b2-139">ID (HL7-defined tables) and IS (user-defined tables)</span></span>  
  
-   <span data-ttu-id="2e4b2-140">Caractère facultatif</span><span class="sxs-lookup"><span data-stu-id="2e4b2-140">Optionality</span></span>  
  
     <span data-ttu-id="2e4b2-141">Obligatoires et facultatifs</span><span class="sxs-lookup"><span data-stu-id="2e4b2-141">Required and optional</span></span>  
  
-   <span data-ttu-id="2e4b2-142">Répétition</span><span class="sxs-lookup"><span data-stu-id="2e4b2-142">Repetition</span></span>  
  
     <span data-ttu-id="2e4b2-143">Segment et champ</span><span class="sxs-lookup"><span data-stu-id="2e4b2-143">Segment and field</span></span>  
  
-   <span data-ttu-id="2e4b2-144">Séquences d’échappement</span><span class="sxs-lookup"><span data-stu-id="2e4b2-144">Escape sequences</span></span>  
  
     <span data-ttu-id="2e4b2-145">Encodage de caractères, la mise en forme et les jeux de caractères</span><span class="sxs-lookup"><span data-stu-id="2e4b2-145">Encoding characters, formatting, and character sets</span></span>  
  
 <span data-ttu-id="2e4b2-146">Pour activer ou désactiver la validation de schéma pour tous les messages reçus ou envoyés à un tiers spécifique (tiers de source pour le désassembleur, tiers de destination de l’assembleur).</span><span class="sxs-lookup"><span data-stu-id="2e4b2-146">You enable or disable schematic validation for all messages received from or sent to a specific party (source party for the disassembler, destination party for the assembler).</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="2e4b2-147">schémas 2.X utilise le HL7 directement pour ce traitement, comme déterminé par le champ d’en-tête de message-structure MSH9.3, le champ ID de Version MSH12 (2.3.1, 2.4 ou 2.5) et l’espace de noms définissant dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration.</span><span class="sxs-lookup"><span data-stu-id="2e4b2-147"> uses the HL7 2.X schemas directly for this processing, as determined by the MSH9.3 message-structure header field, the MSH12 Version ID field (2.3.1, 2.4, or 2.5), and the namespace setting in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.</span></span>  
  
## <a name="hl7-disassembler-processing"></a><span data-ttu-id="2e4b2-148">HL7 Le traitement du désassembleur</span><span class="sxs-lookup"><span data-stu-id="2e4b2-148">HL7 Disassembler Processing</span></span>  
 <span data-ttu-id="2e4b2-149">Le désassembleur HL7 analyse les messages entrants HL7 en segments XML pour le traitement.</span><span class="sxs-lookup"><span data-stu-id="2e4b2-149">The HL7 disassembler parses incoming HL7 messages into XML segments for processing.</span></span> <span data-ttu-id="2e4b2-150">Comme il traite les messages, le désassembleur effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="2e4b2-150">As it parses the messages, the disassembler performs the following tasks:</span></span>  
  
-   <span data-ttu-id="2e4b2-151">Gère les séquences d’échappement</span><span class="sxs-lookup"><span data-stu-id="2e4b2-151">Handles escape sequences</span></span>  
  
-   <span data-ttu-id="2e4b2-152">Gère les vérifications des propriétés obligatoire ou facultatif</span><span class="sxs-lookup"><span data-stu-id="2e4b2-152">Handles checks of the required/optional properties</span></span>  
  
-   <span data-ttu-id="2e4b2-153">Handles défini des segments et des segments Z indéfinis ou inattendus (pour obtenir une description des segments de Z, consultez [personnalisation des Messages via des objets de Z](../../adapters-and-accelerators/accelerator-hl7/customizing-messages-through-z-objects.md)).</span><span class="sxs-lookup"><span data-stu-id="2e4b2-153">Handles defined segments and undefined or unexpected Z segments (for a description of Z segments, see [Customizing Messages through Z Objects](../../adapters-and-accelerators/accelerator-hl7/customizing-messages-through-z-objects.md)).</span></span>  
  
-   <span data-ttu-id="2e4b2-154">Ignore les segments inattendues à la fin d’une instance (qui deviennent des segments Z non déclarés)</span><span class="sxs-lookup"><span data-stu-id="2e4b2-154">Ignores unexpected segments at the end of an instance (which become undeclared Z segments)</span></span>  
  
## <a name="error-reporting"></a><span data-ttu-id="2e4b2-155">Rapport d'erreurs</span><span class="sxs-lookup"><span data-stu-id="2e4b2-155">Error Reporting</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="2e4b2-156">signale la plupart des erreurs dans le format d’erreur HL7 standard, notamment le code de segment, séquence, champ et d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2e4b2-156"> reports most errors in standard HL7 error format, which include the segment, sequence, field, and error code.</span></span> <span data-ttu-id="2e4b2-157">Toutefois, la condition d’erreur peut être que tous ces éléments soient disponibles, par exemple, si aucun schéma n’est présent.</span><span class="sxs-lookup"><span data-stu-id="2e4b2-157">However, the error condition may be such that not all of these are available, for instance, if no schema is present.</span></span> <span data-ttu-id="2e4b2-158">Pour gérer cet cas, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] peuvent signaler les erreurs dans un autre [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] format d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2e4b2-158">To handle such cases, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] can report errors in an alternate [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] error format.</span></span> <span data-ttu-id="2e4b2-159">Le segment dans un message d’erreur comprend deux parties : un pour l’erreur HL7 et un pour l’autre [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] erreur.</span><span class="sxs-lookup"><span data-stu-id="2e4b2-159">The error segment in a message includes two parts: one for the HL7 error and one for the alternative [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] error.</span></span>  
  
## <a name="ack-generation"></a><span data-ttu-id="2e4b2-160">Génération de l’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="2e4b2-160">ACK Generation</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="2e4b2-161">prend en charge les types d’accusés de réception (ACK) suivants pour les messages 2.X.</span><span class="sxs-lookup"><span data-stu-id="2e4b2-161"> supports the following types of acknowledgments (ACKs) for 2.X messages.</span></span> <span data-ttu-id="2e4b2-162">Les deux le type d’erreur HL7 et [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] type d’erreur (secondaire) sont utilisées :</span><span class="sxs-lookup"><span data-stu-id="2e4b2-162">Both the HL7 error type and the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] (alternate) error type are used:</span></span>  
  
-   <span data-ttu-id="2e4b2-163">Mappage du message d’origine et de l’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="2e4b2-163">Mapping original message and ACK</span></span>  
  
-   <span data-ttu-id="2e4b2-164">Accusés de réception d’origine HL7</span><span class="sxs-lookup"><span data-stu-id="2e4b2-164">HL7 original ACKs</span></span>  
  
-   <span data-ttu-id="2e4b2-165">HL7 améliorée des accusés de réception</span><span class="sxs-lookup"><span data-stu-id="2e4b2-165">HL7 enhanced ACKs</span></span>  
  
     <span data-ttu-id="2e4b2-166">Validation acceptent et Application</span><span class="sxs-lookup"><span data-stu-id="2e4b2-166">Commit Accept and Application Accept</span></span>  
  
-   <span data-ttu-id="2e4b2-167">Statique/proxy l’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="2e4b2-167">Static/proxy ACK</span></span>  
  
     <span data-ttu-id="2e4b2-168">L’accusé de réception ou NAK</span><span class="sxs-lookup"><span data-stu-id="2e4b2-168">ACK or NAK</span></span>  
  
## <a name="property-promotion"></a><span data-ttu-id="2e4b2-169">Promotion des propriétés</span><span class="sxs-lookup"><span data-stu-id="2e4b2-169">Property Promotion</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="2e4b2-170">prend en charge la promotion des propriétés 2.X suivantes :</span><span class="sxs-lookup"><span data-stu-id="2e4b2-170"> supports promoting the following 2.X properties:</span></span>  
  
-   <span data-ttu-id="2e4b2-171">Schéma de propriété</span><span class="sxs-lookup"><span data-stu-id="2e4b2-171">Property schema</span></span>  
  
-   <span data-ttu-id="2e4b2-172">Schéma d’en-tête de MSH</span><span class="sxs-lookup"><span data-stu-id="2e4b2-172">MSH-header schema</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2e4b2-173">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="2e4b2-173">In This Section</span></span>  
  
-   [<span data-ttu-id="2e4b2-174">Détermination du schéma dans le désassembleur 2.X HL7</span><span class="sxs-lookup"><span data-stu-id="2e4b2-174">Schema Determination in the HL7 2.X Disassembler</span></span>](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-disassembler.md)  
  
-   [<span data-ttu-id="2e4b2-175">Détermination du schéma dans l’assembleur 2.X HL7</span><span class="sxs-lookup"><span data-stu-id="2e4b2-175">Schema Determination in the HL7 2.X Assembler</span></span>](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-assembler.md)  
  
## <a name="see-also"></a><span data-ttu-id="2e4b2-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e4b2-176">See Also</span></span>  
 <span data-ttu-id="2e4b2-177">[Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="2e4b2-177">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 <span data-ttu-id="2e4b2-178">[Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="2e4b2-178">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 [<span data-ttu-id="2e4b2-179">L’utilisation des schémas 2.X HL7</span><span class="sxs-lookup"><span data-stu-id="2e4b2-179">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)