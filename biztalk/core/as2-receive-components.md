---
title: "AS2 Composants de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bdab87fd-15b9-4e3c-a4d7-984693262293
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c919a54a307a234237dd4086a0abf2a2c0c2fd8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="as2-receive-components"></a><span data-ttu-id="56193-102">Composants de réception AS2</span><span class="sxs-lookup"><span data-stu-id="56193-102">AS2 Receive Components</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="56193-103"> utilise plusieurs composants pour recevoir des messages AS2.</span><span class="sxs-lookup"><span data-stu-id="56193-103"> uses several components to receive AS2 messages.</span></span>  
  
## <a name="as2-receive-pipelines"></a><span data-ttu-id="56193-104">Pipelines de réception AS2</span><span class="sxs-lookup"><span data-stu-id="56193-104">AS2 Receive Pipelines</span></span>  
 <span data-ttu-id="56193-105">La plus grande partie du traitement de réception AS2 est effectuée dans les pipelines de réception AS2 suivants.</span><span class="sxs-lookup"><span data-stu-id="56193-105">Most AS2 receive processing is performed in the following AS2 receive pipelines.</span></span> <span data-ttu-id="56193-106">Ces pipelines sont installés dans `Microsoft.BizTalk.EdiInt.PipelineComponents.dll` dans \Program Files\Microsoft composants de BizTalk Server 20xx\Pipeline\\.</span><span class="sxs-lookup"><span data-stu-id="56193-106">These pipelines are installed in `Microsoft.BizTalk.EdiInt.PipelineComponents.dll` in \Program Files\Microsoft BizTalk Server 20xx\Pipeline Components\\.</span></span>  
  
 <span data-ttu-id="56193-107">**Pipeline de AS2EdiReceive**</span><span class="sxs-lookup"><span data-stu-id="56193-107">**AS2EdiReceive Pipeline**</span></span>  
  
 <span data-ttu-id="56193-108">Ce pipeline traite les messages EDI reçus via AS2, y compris les MDN.</span><span class="sxs-lookup"><span data-stu-id="56193-108">This pipeline processes EDI messages received over AS2, including MDNs.</span></span> <span data-ttu-id="56193-109">Le pipeline est doté des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="56193-109">The pipeline consists of the following pipeline components:</span></span>  
  
-   <span data-ttu-id="56193-110">Décodeur AS2</span><span class="sxs-lookup"><span data-stu-id="56193-110">AS2 Decoder</span></span>  
  
-   <span data-ttu-id="56193-111">Désassembleur EDI</span><span class="sxs-lookup"><span data-stu-id="56193-111">EDI Disassembler</span></span>  
  
-   <span data-ttu-id="56193-112">BatchMarker.</span><span class="sxs-lookup"><span data-stu-id="56193-112">BatchMarker.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="56193-113">Lors de l'utilisation du pipeline AS2EdiReceive, vous devez ajouter le compte d'utilisateur que le processus d'instance de l'hôte BizTalk isolé exécute sous le groupe Utilisateurs d'applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="56193-113">When using the AS2EdiReceive pipeline, you must add the user account that the BizTalk Isolated Host Instance process is running under to the BizTalk Application Users group.</span></span> <span data-ttu-id="56193-114">Le pipeline AS2EdiReceive s'exécute dans le processus d'instance de l'hôte BizTalk isolé.</span><span class="sxs-lookup"><span data-stu-id="56193-114">The AS2EdiReceive pipeline executes in the BizTalk Isolated Host Instance process.</span></span> <span data-ttu-id="56193-115">Le pipeline AS2EdiReceive accède au magasin SSO, qui requiert que l'utilisateur figure dans le groupe Utilisateurs d'applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="56193-115">The AS2EdiReceive pipeline accesses the SSO store, which requires that the user is in the BizTalk Application Users group.</span></span>  
  
 <span data-ttu-id="56193-116">**AS2Receive Pipeline**</span><span class="sxs-lookup"><span data-stu-id="56193-116">**AS2Receive Pipeline**</span></span>  
  
 <span data-ttu-id="56193-117">Ce pipeline traite les messages reçus via AS2 lorsque les messages ne sont pas codés dans EDI.</span><span class="sxs-lookup"><span data-stu-id="56193-117">This pipeline processes messages received over AS2 when the messages are not encoded in EDI.</span></span> <span data-ttu-id="56193-118">Ces messages sont traités comme messages binaires.</span><span class="sxs-lookup"><span data-stu-id="56193-118">These messages are treated as binary messages.</span></span> <span data-ttu-id="56193-119">Le pipeline traite également les MDN reçus via AS2.</span><span class="sxs-lookup"><span data-stu-id="56193-119">The pipeline also processes MDNs received over AS2.</span></span> <span data-ttu-id="56193-120">Le pipeline est doté des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="56193-120">The pipeline consists of the following pipeline components:</span></span>  
  
-   <span data-ttu-id="56193-121">Décodeur AS2</span><span class="sxs-lookup"><span data-stu-id="56193-121">AS2 Decoder</span></span>  
  
-   <span data-ttu-id="56193-122">Désassembleur AS2.</span><span class="sxs-lookup"><span data-stu-id="56193-122">AS2 Disassembler.</span></span>  
  
## <a name="as2-receive-pipeline-components"></a><span data-ttu-id="56193-123">Composants du pipeline de réception AS2</span><span class="sxs-lookup"><span data-stu-id="56193-123">AS2 Receive Pipeline Components</span></span>  
 <span data-ttu-id="56193-124">Les pipelines de réception AS2 utilisent les composants suivants.</span><span class="sxs-lookup"><span data-stu-id="56193-124">The AS2 receive pipelines use the following pipeline components.</span></span> <span data-ttu-id="56193-125">Ces composants sont installés dans `Microsoft.BizTalk.EdiInt.PipelineComponents.dll` dans \Program Files\Microsoft composants de BizTalk Server 20xx\Pipeline\\.</span><span class="sxs-lookup"><span data-stu-id="56193-125">These components are installed in `Microsoft.BizTalk.EdiInt.PipelineComponents.dll` in \Program Files\Microsoft BizTalk Server 20xx\Pipeline Components\\.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56193-126">Le pipeline de réception AS2 est seulement pris en charge dans une instance d'hôte BizTalk 32 bits.</span><span class="sxs-lookup"><span data-stu-id="56193-126">The AS2 Receive pipeline is only supported in a 32-bit BizTalk Host process.</span></span>  
  
 <span data-ttu-id="56193-127">**Décodeur AS2**</span><span class="sxs-lookup"><span data-stu-id="56193-127">**AS2 Decoder**</span></span>  
  
 <span data-ttu-id="56193-128">Le décodeur AS2 est inclus dans l'étape Décoder des pipelines de réception AS2EDIReceivePipeline et AS2Receive.</span><span class="sxs-lookup"><span data-stu-id="56193-128">The AS2 Decoder is included in the decode stage of both the AS2EDIReceivePipeline and AS2Receive receive pipelines.</span></span> <span data-ttu-id="56193-129">Il utilise le composant de pipeline S/MIME BizTalk pour apporter des fonctions de décodage S/MIME aux messages AS2 et MDN.</span><span class="sxs-lookup"><span data-stu-id="56193-129">It uses the BizTalk S/MIME Pipeline Component to provide S/MIME decoding functionality to AS2 and MDN messages.</span></span>  
  
-   <span data-ttu-id="56193-130">Traite les en-têtes AS2/HTTP</span><span class="sxs-lookup"><span data-stu-id="56193-130">Processes AS2/HTTP headers</span></span>  
  
-   <span data-ttu-id="56193-131">Vérifie la signature, si le message a été signé</span><span class="sxs-lookup"><span data-stu-id="56193-131">Verifies the signature, if the message was signed</span></span>  
  
-   <span data-ttu-id="56193-132">Déchiffre les messages, si le message a été chiffré (pour un message EDI/AS2, pas un MDN)</span><span class="sxs-lookup"><span data-stu-id="56193-132">Decrypts the messages, if the message was encrypted (for an EDI/AS2 message, not an MDN)</span></span>  
  
-   <span data-ttu-id="56193-133">Décompresse le message, s'il était compressé</span><span class="sxs-lookup"><span data-stu-id="56193-133">Decompresses the message, if the message was compressed</span></span>  
  
-   <span data-ttu-id="56193-134">Rapproche un MDN reçu du message sortant original</span><span class="sxs-lookup"><span data-stu-id="56193-134">Reconciles a received MDN with the original outbound message</span></span>  
  
-   <span data-ttu-id="56193-135">Met à jour et met des enregistrements en corrélation dans la base de données de non-répudiation.</span><span class="sxs-lookup"><span data-stu-id="56193-135">Updates and correlates records in the non-repudiation database</span></span>  
  
-   <span data-ttu-id="56193-136">Ecrit des enregistrements pour les rapports d'état AS2</span><span class="sxs-lookup"><span data-stu-id="56193-136">Writes records for AS2 status reporting</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="56193-137">Si une erreur survient au cours du traitement d'un message AS2 côté réception, le décodeur AS2 arrêtera le traitement des messages en aval (par exemple, le Désassembleur EDI n'analysera pas l'échange).</span><span class="sxs-lookup"><span data-stu-id="56193-137">If an error occurs during receive-side processing of an AS2 message, the AS2 Decoder will stop further downstream message processing (for example, the EDI disassembler will not parse the interchange).</span></span> <span data-ttu-id="56193-138">Toutefois, le Désassembleur AS2 ou EDI doit toutefois générer le MDN.</span><span class="sxs-lookup"><span data-stu-id="56193-138">However, the AS2 Disassembler or EDI Disassembler must still generate the MDN.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="56193-139">Le codage sur 8 bits est utilisé dans les messages AS2.</span><span class="sxs-lookup"><span data-stu-id="56193-139">Eight-bit encoding is used on AS2 messages.</span></span> <span data-ttu-id="56193-140">Le codage Base64 n'est appliqué qu'aux signatures dans les messages AS2 et les  MDN.</span><span class="sxs-lookup"><span data-stu-id="56193-140">Base64 encoding is only applied to signatures in AS2 messages and MDNs.</span></span>  
  
 <span data-ttu-id="56193-141">**Désassembleur AS2**</span><span class="sxs-lookup"><span data-stu-id="56193-141">**AS2 Disassembler**</span></span>  
  
 <span data-ttu-id="56193-142">Dans le pipeline de réception AS2Receive, le Désassembleur AS2 effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="56193-142">In the AS2Receive receive pipeline, the AS2 Disassembler does the following:</span></span>  
  
-   <span data-ttu-id="56193-143">Détermine si un MDN est requis et si le MDN doit être synchrone ou asynchrone.</span><span class="sxs-lookup"><span data-stu-id="56193-143">Determines whether an MDN is required, and whether the MDN should be synchronous or asynchronous.</span></span>  
  
-   <span data-ttu-id="56193-144">Génère un MDN AS2.</span><span class="sxs-lookup"><span data-stu-id="56193-144">Generates an AS2 MDN.</span></span>  
  
-   <span data-ttu-id="56193-145">Si le MDN est synchrone, il définit la propriété `EdiIntAS.IsAS2AsynchronousMDN` sur la valeur False ; s'il est asynchrone, il définit cette propriété sur la valeur True.</span><span class="sxs-lookup"><span data-stu-id="56193-145">If the MDN is synchronous, sets the `EdiIntAS.IsAS2AsynchronousMDN` property to False; if asynchronous, sets the property to True.</span></span>  
  
-   <span data-ttu-id="56193-146">Définit les jetons et les propriétés de corrélation sur le MDN.</span><span class="sxs-lookup"><span data-stu-id="56193-146">Sets the correlation tokens and properties on the MDN.</span></span>  
  
 <span data-ttu-id="56193-147">**Désassembleur EDI**</span><span class="sxs-lookup"><span data-stu-id="56193-147">**EDI Disassembler**</span></span>  
  
 <span data-ttu-id="56193-148">Dans le AS2EDIReceivePipeline, le Désassembleur EDI analysera le message EDI dans un message XML intermédiaire en vue du traitement.</span><span class="sxs-lookup"><span data-stu-id="56193-148">In the AS2EDIReceivePipeline, the EDI Disassembler will parse the EDI message into intermediate XML message(s) for processing.</span></span> <span data-ttu-id="56193-149">Pour plus d’informations, consultez [EDI désassembleur fonctionnement](../core/how-the-edi-disassembler-works.md).</span><span class="sxs-lookup"><span data-stu-id="56193-149">For more information, see [How the EDI Disassembler Works](../core/how-the-edi-disassembler-works.md).</span></span>  
  
 <span data-ttu-id="56193-150">**BatchMarker**</span><span class="sxs-lookup"><span data-stu-id="56193-150">**BatchMarker**</span></span>  
  
 <span data-ttu-id="56193-151">Dans le AS2EDIReceivePipeline, le composant de pipeline BatchMarker définit les propriétés de contexte AgreementPartIdForSend et ToBeBatched nécessaires au traitement d'un échange par lot.</span><span class="sxs-lookup"><span data-stu-id="56193-151">In the AS2EDIReceivePipeline, the BatchMarker pipeline component sets the AgreementPartIdForSend and ToBeBatched context properties that are required for processing a batched interchange.</span></span> <span data-ttu-id="56193-152">Ce composant est inclus dans la dernière étape (résolution de l'accord) du pipeline AS2EDIReceive.</span><span class="sxs-lookup"><span data-stu-id="56193-152">This component is included in the last stage (agreement resolution) of the AS2EDIReceive pipeline.</span></span> <span data-ttu-id="56193-153">Tous les pipelines chargés du traitement par lot des messages EDI doivent inclure le composant de pipeline BatchMarker.</span><span class="sxs-lookup"><span data-stu-id="56193-153">All pipelines that will batch EDI messages should include the BatchMarker pipeline component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56193-154">Le composant de pipeline BatchMarker n'est pas inclus dans le pipeline AS2Receive utilisé pour le traitement des messages non-EDI.</span><span class="sxs-lookup"><span data-stu-id="56193-154">The BatchMarker pipeline component is not included in the AS2Receive pipeline that is used to process non-EDI messages.</span></span> <span data-ttu-id="56193-155">Toutefois, vous pouvez inclure le composant BatchMarker dans un pipeline de réception personnalisé qui ne contient pas le Désassembleur EDI.</span><span class="sxs-lookup"><span data-stu-id="56193-155">However, you can include the BatchMarker component in a custom receive pipeline that does not include the EDI Dissassembler.</span></span> <span data-ttu-id="56193-156">Pour plus d’informations, consultez « Traitement de Non-EDI Messages dans le composant de BatchMarker » dans [assembler un échange EDI par lot](../core/assembling-a-batched-edi-interchange.md).</span><span class="sxs-lookup"><span data-stu-id="56193-156">For more information, see "Processing Non-EDI Messages in the BatchMarker Component" in [Assembling a Batched EDI Interchange](../core/assembling-a-batched-edi-interchange.md).</span></span>  
  
## <a name="http-adapter"></a><span data-ttu-id="56193-157">Adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="56193-157">HTTP Adapter</span></span>  
 <span data-ttu-id="56193-158">Les ports et emplacements de réception utilisés pour le traitement AS2 utilisent l'adaptateur HTTP [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56193-158">The receive ports and locations used for AS2 processing use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP Adapter.</span></span> <span data-ttu-id="56193-159">L'adaptateur HTTP est configuré pour les transmissions unidirectionnelles et de type requête-réponse.</span><span class="sxs-lookup"><span data-stu-id="56193-159">The HTTP Adapter is configured for either one-way and request-response transmission.</span></span>  
  
## <a name="non-repudiation-database"></a><span data-ttu-id="56193-160">Base de données de non-répudiation</span><span class="sxs-lookup"><span data-stu-id="56193-160">Non-Repudiation Database</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="56193-161">utilise la base de données de non répudiation (la table EdiMessageContent de la base de données BizTalkDTADb) pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="56193-161"> uses the non-repudiation database (the EdiMessageContent table of the BizTalkDTADb database) to do the following:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56193-162">La table EdiMessageContent existe seulement dans la base de données BizTalkDTADb si l'une des propriétés d'accord de stockage de non-répudiation a été sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="56193-162">The EdiMessageContent table exists in the BizTalkDTADb database only if one of the non-repudiation storage agreement properties has been checked.</span></span>  
  
-   <span data-ttu-id="56193-163">Fournit un journal de non-répudiation pour le MDN signé</span><span class="sxs-lookup"><span data-stu-id="56193-163">Provides a non-repudiation trail for signed MDN</span></span>  
  
-   <span data-ttu-id="56193-164">Associe un message sortant à son MDN entrant</span><span class="sxs-lookup"><span data-stu-id="56193-164">Correlates an outbound message with its incoming MDN</span></span>  
  
-   <span data-ttu-id="56193-165">Stocke des messages à différents changements d'état</span><span class="sxs-lookup"><span data-stu-id="56193-165">Stores messages through various state changes</span></span>  
  
-   <span data-ttu-id="56193-166">Associe les codes d'erreur à la réponse HTTP et à MDN</span><span class="sxs-lookup"><span data-stu-id="56193-166">Associates error codes with HTTP Response and MDN</span></span>  
  
-   <span data-ttu-id="56193-167">Affiche les enregistrements selon des critères de filtre</span><span class="sxs-lookup"><span data-stu-id="56193-167">Displays records based on filter criteria</span></span>  
  
-   <span data-ttu-id="56193-168">Archive les enregistrements marqués.</span><span class="sxs-lookup"><span data-stu-id="56193-168">Archives marked records.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="56193-169">Pour garantir l'authentification et l'intégrité des messages stockés dans la base de données de réception de non-répudiation, les signatures numériques doivent être utilisées sur tous les messages devant être stockés dans la base de données, à la fois les messages AS2 et les MDN d'origine.</span><span class="sxs-lookup"><span data-stu-id="56193-169">To ensure authentication and integrity of messages stored in the non-repudiation receipt database, digital signatures should be used on all messages that will be stored in the database, both original AS2 messages and MDNs.</span></span> <span data-ttu-id="56193-170">Pour plus d’informations, consultez la section 9.1 de [RFC 1430, « Basé sur MIME sécurisé pair à pair de données commerciales échange via HTTP, Applicability Statement 2 (AS2) »](http://go.microsoft.com/fwlink/?LinkID=184212) ([http://go.microsoft.com/fwlink/?LinkID=184212](http://go.microsoft.com/fwlink/?LinkID=184212)).</span><span class="sxs-lookup"><span data-stu-id="56193-170">For more information, see section 9.1 of [RFC 1430, "MIME-Based Secure Peer-to-Peer Business Data Interchange Using HTTP, Applicability Statement 2 (AS2)"](http://go.microsoft.com/fwlink/?LinkID=184212) ([http://go.microsoft.com/fwlink/?LinkID=184212](http://go.microsoft.com/fwlink/?LinkID=184212)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56193-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56193-171">See Also</span></span>  
 [<span data-ttu-id="56193-172">Réception des Messages AS2 par BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="56193-172">How BizTalk Server Receives AS2 Messages</span></span>](../core/how-biztalk-server-receives-as2-messages.md)