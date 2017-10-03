---
title: "AS2 Composants d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35113732-fe32-4776-be25-971ec66c365c
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1dbee64dc2e3484e85e6d8e41ce31a77713ffec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="as2-send-components"></a><span data-ttu-id="c3ccc-102">Composants d'envoi AS2</span><span class="sxs-lookup"><span data-stu-id="c3ccc-102">AS2 Send Components</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c3ccc-103"> utilise plusieurs composants pour envoyer des messages AS2.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-103"> uses several components to send AS2 messages.</span></span>  
  
## <a name="as2-send-pipelines"></a><span data-ttu-id="c3ccc-104">Pipelines d'envoi AS2</span><span class="sxs-lookup"><span data-stu-id="c3ccc-104">AS2 Send Pipelines</span></span>  
 <span data-ttu-id="c3ccc-105">La plus grande partie du traitement d'envoi AS2 est effectuée dans les pipelines d'envoi AS2 suivants.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-105">Most AS2 send processing is performed in the following AS2 send pipelines.</span></span> <span data-ttu-id="c3ccc-106">Ces pipelines sont installés dans `Microsoft.BizTalk.Edi.EdiIntPipelines.dll`, dans \Program Files\Microsoft BizTalk Server 20xx\Pipeline Components.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-106">These pipelines are installed in `Microsoft.BizTalk.Edi.EdiIntPipelines.dll` in \Program Files\Microsoft BizTalk Server 20xx\Pipeline Components.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3ccc-107">Le pipeline d'envoi AS2 est seulement pris en charge dans une instance d'hôte BizTalk 32 bits.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-107">The AS2 Send pipeline is only supported in a 32-bit BizTalk Host process.</span></span>  
  
 <span data-ttu-id="c3ccc-108">**AS2EDISend Pipeline**</span><span class="sxs-lookup"><span data-stu-id="c3ccc-108">**AS2EDISend Pipeline**</span></span>  
  
 <span data-ttu-id="c3ccc-109">Ce pipeline génère et envoie les messages EDI via AS2.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-109">This pipeline generates and sends EDI messages over AS2.</span></span> <span data-ttu-id="c3ccc-110">Le pipeline est doté des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="c3ccc-110">The pipeline consists of the following pipeline components:</span></span>  
  
-   <span data-ttu-id="c3ccc-111">Assembleur EDI</span><span class="sxs-lookup"><span data-stu-id="c3ccc-111">EDI Assembler</span></span>  
  
-   <span data-ttu-id="c3ccc-112">Encodeur AS2</span><span class="sxs-lookup"><span data-stu-id="c3ccc-112">AS2 Encoder</span></span>  
  
 <span data-ttu-id="c3ccc-113">Ce pipeline n'est pas utilisé pour générer et envoyer des MDN via AS2, car l'assembleur EDI n'a pas besoin de traiter un MDN.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-113">This pipeline is not used to generate and send MDNs over AS2, because the MDN does not need to be processed by the EDI Assembler.</span></span> <span data-ttu-id="c3ccc-114">Utilisez AS2SendPipeline pour envoyer des MDN.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-114">Use the AS2SendPipeline to send MDNs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3ccc-115">L'exécution du pipeline AS2EDISend depuis une orchestration n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-115">Running the AS2EDISend pipeline from an orchestration is not supported.</span></span>  
  
 <span data-ttu-id="c3ccc-116">**Pipeline de AS2Send**</span><span class="sxs-lookup"><span data-stu-id="c3ccc-116">**AS2Send Pipeline**</span></span>  
  
 <span data-ttu-id="c3ccc-117">Ce pipeline envoie les messages via AS2 lorsque les messages ne sont pas codés dans EDI.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-117">This pipeline sends messages over AS2 when the messages are not encoded in EDI.</span></span> <span data-ttu-id="c3ccc-118">Il envoie aussi les MDN via AS2.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-118">It also sends MDNs over AS2.</span></span> <span data-ttu-id="c3ccc-119">Le pipeline est doté des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="c3ccc-119">The pipeline consists of the following pipeline components:</span></span>  
  
-   <span data-ttu-id="c3ccc-120">Encodeur AS2.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-120">AS2 Encoder.</span></span>  
  
 <span data-ttu-id="c3ccc-121">Si les messages à envoyer via AS2 ne sont pas de type EDI ou XML, vous pouvez créer un pipeline AS2Send personnalisé pour les gérer.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-121">If the messages to be sent over AS2 are neither EDI nor XML messages, you can create a customized AS2Send pipeline to handle these messages.</span></span> <span data-ttu-id="c3ccc-122">Ce pipeline doit posséder un assembleur personnalisé pour convertir dans un autre format le XML intermédiaire dans BizTalk Server avant l'encodage du message dans EDIINT/AS2.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-122">This pipeline must have a customized assembler to convert the intermediate XML in BizTalk Server into the other format before encoding the message in EDIINT/AS2.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3ccc-123">L'exécution du pipeline AS2Send depuis une orchestration n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-123">Running the AS2Send pipeline from an orchestration is not supported.</span></span>  
  
## <a name="as2-send-pipeline-components"></a><span data-ttu-id="c3ccc-124">Composants de pipeline AS2Send</span><span class="sxs-lookup"><span data-stu-id="c3ccc-124">AS2 Send Pipeline Components</span></span>  
 <span data-ttu-id="c3ccc-125">Les pipelines d'envoi AS2 utilisent les composants suivants.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-125">The AS2 send pipelines use the following pipeline components.</span></span> <span data-ttu-id="c3ccc-126">Ces composants sont installés dans `Microsoft.BizTalk.EdiInt.PipelineComponents.dll` dans \Program Files\Microsoft composants de BizTalk Server 20xx\Pipeline\\.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-126">These components are installed in `Microsoft.BizTalk.EdiInt.PipelineComponents.dll` in \Program Files\Microsoft BizTalk Server 20xx\Pipeline Components\\.</span></span>  
  
 <span data-ttu-id="c3ccc-127">**Assembleur EDI**</span><span class="sxs-lookup"><span data-stu-id="c3ccc-127">**EDI Assembler**</span></span>  
  
 <span data-ttu-id="c3ccc-128">Dans les pipelines d'envoi EDIINT, l'assembleur EDI sérialise l'échange EDI.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-128">In the EDIINT send pipelines, the EDI Assembler serializes the EDI interchange.</span></span>  
  
 <span data-ttu-id="c3ccc-129">**Encodeur AS2**</span><span class="sxs-lookup"><span data-stu-id="c3ccc-129">**AS2 Encoder**</span></span>  
  
 <span data-ttu-id="c3ccc-130">L'encodeur AS2 est inclus à la phase d'encodage des pipelines d'envoi AS2.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-130">The AS2 Encoder is included in the encode stage of the AS2 send pipelines.</span></span> <span data-ttu-id="c3ccc-131">Il utilise le composant de pipeline S/MIME BizTalk pour fournir des fonctions d'encodage S/MIME aux messages AS2 et MDN.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-131">It uses the BizTalk S/MIME pipeline component to provide S/MIME encoding functionality to AS2 and MDN messages.</span></span> <span data-ttu-id="c3ccc-132">L'encodeur AS2 assure les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="c3ccc-132">The AS2 Encoder does the following:</span></span>  
  
-   <span data-ttu-id="c3ccc-133">Applique les en-têtes AS2/HTTP</span><span class="sxs-lookup"><span data-stu-id="c3ccc-133">Applies AS2/HTTP headers</span></span>  
  
-   <span data-ttu-id="c3ccc-134">Signe les messages sortants, si activé</span><span class="sxs-lookup"><span data-stu-id="c3ccc-134">Signs outgoing messages, if enabled</span></span>  
  
-   <span data-ttu-id="c3ccc-135">Chiffre les messages sortants, si activé (pour EDI/AS2, pas MDN)</span><span class="sxs-lookup"><span data-stu-id="c3ccc-135">Encrypts outgoing messages, if enabled (for EDI/AS2, not MDN)</span></span>  
  
-   <span data-ttu-id="c3ccc-136">Compresse le message, si activé (pour EDI/AS2, pas MDN)</span><span class="sxs-lookup"><span data-stu-id="c3ccc-136">Compresses the message, if enabled (for EDI/AS2, not MDN)</span></span>  
  
-   <span data-ttu-id="c3ccc-137">Stocke la charge utile au format câble si la **NRR activé pour les messages AS2 décodés sortants** propriété est sélectionnée et stocke le message au format câble si la **NRR activé pour les messages AS2 encodés sortants** propriété est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-137">Stores the payload in wire format if the **NRR enabled for outbound decoded AS2 messages** property is selected, and stores the message in wire format if the **NRR enabled for outbound encoded AS2 messages** property is selected</span></span>  
  
-   <span data-ttu-id="c3ccc-138">Calcule la valeur MIC et la stocke dans la banque de données.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-138">Computes the MIC value and stores it in the data store</span></span>  
  
-   <span data-ttu-id="c3ccc-139">Met à jour et met des enregistrements en corrélation dans la base de données de réception de non-répudiation</span><span class="sxs-lookup"><span data-stu-id="c3ccc-139">Updates and correlates records in the non-repudiation receipt database</span></span>  
  
-   <span data-ttu-id="c3ccc-140">Pour les messages MDN, sert de pipeline Passthru, en routant le MDN généré par le décodeur AS2 dans le pipeline de réception AS2Receive.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-140">For MDN messages, acts as a passthrough pipeline, routing the MDN generated by the AS2 Decoder in the AS2Receive receive pipeline.</span></span> <span data-ttu-id="c3ccc-141">Si les paramètres de configuration le demandent, l'encodeur AS2 signe le MDN.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-141">If required by the configuration settings, the AS2 Encoder will sign the MDN.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c3ccc-142">Le codage sur 8 bits est utilisé dans les messages AS2.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-142">Eight-bit encoding is used on AS2 messages.</span></span> <span data-ttu-id="c3ccc-143">Le codage Base64 n'est appliqué qu'aux signatures dans les messages AS2 et les  MDN.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-143">Base64 encoding is only applied to signatures in AS2 messages and MDNs.</span></span>  
  
## <a name="http-adapter"></a><span data-ttu-id="c3ccc-144">Adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="c3ccc-144">HTTP Adapter</span></span>  
 <span data-ttu-id="c3ccc-145">Les ports d'envoi utilisés pour le traitement AS2 EDIINT utilisent l'adaptateur HTTP [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c3ccc-145">The send ports used for EDIINT AS2 processing use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP Adapter.</span></span> <span data-ttu-id="c3ccc-146">L'adaptateur HTTP est configuré pour les transmissions unidirectionnelles et de type sollicitation-réponse.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-146">The HTTP Adapter is configured in both one-way and solicit-response transmission.</span></span>  
  
## <a name="non-repudiation-database"></a><span data-ttu-id="c3ccc-147">Base de données de non-répudiation</span><span class="sxs-lookup"><span data-stu-id="c3ccc-147">Non-Repudiation Database</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c3ccc-148">utilise la base de données de non répudiation (la table EdiMessageContent de la base de données BizTalkDTADb) pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="c3ccc-148"> uses the non-repudiation database (the EdiMessageContent table of the BizTalkDTADb database) to do the following:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3ccc-149">La table EdiMessageContent existe seulement dans la base de données BizTalkDTADb si l'une des propriétés d'accord de stockage de non-répudiation est vérifiée.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-149">The EdiMessageContent table exists in the BizTalkDTADb database only if one of the non-repudiation storage agreement properties are checked.</span></span>  
  
-   <span data-ttu-id="c3ccc-150">Fournir un journal de non-répudiation pour le MDN signé</span><span class="sxs-lookup"><span data-stu-id="c3ccc-150">Provide a non-repudiation trail for signed MDN</span></span>  
  
-   <span data-ttu-id="c3ccc-151">Mettre en corrélation un message sortant à son MDN entrant</span><span class="sxs-lookup"><span data-stu-id="c3ccc-151">Correlate an outbound message with its incoming MDN</span></span>  
  
-   <span data-ttu-id="c3ccc-152">Stocker des messages à différents changements d'état</span><span class="sxs-lookup"><span data-stu-id="c3ccc-152">Store messages through various state changes</span></span>  
  
-   <span data-ttu-id="c3ccc-153">Associer les codes d'erreur à la réponse HTTP et à MDN</span><span class="sxs-lookup"><span data-stu-id="c3ccc-153">Associate error codes with HTTP Response and MDN</span></span>  
  
-   <span data-ttu-id="c3ccc-154">Afficher les enregistrements selon des critères de filtre</span><span class="sxs-lookup"><span data-stu-id="c3ccc-154">Display records based on filter criteria</span></span>  
  
-   <span data-ttu-id="c3ccc-155">Archiver les enregistrements marqués</span><span class="sxs-lookup"><span data-stu-id="c3ccc-155">Archive marked records</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c3ccc-156">Pour garantir l’authentification et l’intégrité des messages stockés dans la base de données de non-répudiation, les signatures numériques doivent être utilisés sur tous les messages qui sont stockés dans la base de données, les messages AS2 d’origine et MDN.</span><span class="sxs-lookup"><span data-stu-id="c3ccc-156">To ensure authentication and integrity of messages stored in the non-repudiation database, digital signatures should be used on all messages that will be stored in the database, both original AS2 messages and MDNs.</span></span> <span data-ttu-id="c3ccc-157">Pour plus d’informations, consultez la section 9.1 de [RFC 1430, « Basé sur MIME sécurisé pair à pair de données commerciales échange via HTTP, Applicability Statement 2 (AS2) »](http://go.microsoft.com/fwlink/?LinkID=184212) ([http://go.microsoft.com/fwlink/?LinkID=184212](http://go.microsoft.com/fwlink/?LinkID=184212)).</span><span class="sxs-lookup"><span data-stu-id="c3ccc-157">For more information, see section 9.1 of [RFC 1430, "MIME-Based Secure Peer-to-Peer Business Data Interchange Using HTTP, Applicability Statement 2 (AS2)"](http://go.microsoft.com/fwlink/?LinkID=184212) ([http://go.microsoft.com/fwlink/?LinkID=184212](http://go.microsoft.com/fwlink/?LinkID=184212)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ccc-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3ccc-158">See Also</span></span>  
 [<span data-ttu-id="c3ccc-159">Envoi des Messages AS2 par BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="c3ccc-159">How BizTalk Server Sends AS2 Messages</span></span>](../core/how-biztalk-server-sends-as2-messages.md)