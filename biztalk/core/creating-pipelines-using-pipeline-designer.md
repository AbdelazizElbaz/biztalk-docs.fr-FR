---
title: "Création de Pipelines à l’aide du Concepteur de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, processing messages
- pipelines, Pipeline Designer
- Pipeline Designer, about Pipeline Designer
ms.assetid: 858302d8-a912-4199-95e5-4322db789b4e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18b693a4e8df20a7f39f81fb820810c1191ef637
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-pipelines-using-pipeline-designer"></a><span data-ttu-id="054d9-102">Création de Pipelines à l’aide du Concepteur de Pipeline</span><span class="sxs-lookup"><span data-stu-id="054d9-102">Creating Pipelines Using Pipeline Designer</span></span>
<span data-ttu-id="054d9-103">Microsoft BizTalk Server fonctionne principalement avec le format de document XML.</span><span class="sxs-lookup"><span data-stu-id="054d9-103">Microsoft BizTalk Server works mainly with the XML document format.</span></span> <span data-ttu-id="054d9-104">Pour qu'un message puisse pleinement profiter du traitement BizTalk Server, son format natif doit souvent être converti en sa représentation XML.</span><span class="sxs-lookup"><span data-stu-id="054d9-104">For a message to take full advantage of BizTalk Server processing, it must often be transformed from its native format into its XML representation.</span></span> <span data-ttu-id="054d9-105">Les pipelines BizTalk Server effectuent cette conversion, ainsi que d'autres actions spécifiques aux données (chiffrement ou déchiffrement de données, promotion des propriétés, etc.) sur les messages entrants et sortants.</span><span class="sxs-lookup"><span data-stu-id="054d9-105">BizTalk Server pipelines perform this transformation, as well as other data-specific actions (such as data encryption or decryption, property promotion, and so on) on incoming and outgoing messages.</span></span> <span data-ttu-id="054d9-106">Cette section fournit des informations concernant les concepts et les tâches spécifiques aux pipelines et au Concepteur de pipeline.</span><span class="sxs-lookup"><span data-stu-id="054d9-106">This section provides conceptual and task-specific information about pipelines and Pipeline Designer.</span></span>  
  
 <span data-ttu-id="054d9-107">L'objectif d'un pipeline est de préparer les messages soit en vue de leur traitement par le serveur après leur réception par un adaptateur, soit en vue de leur envoi après leur traitement par le serveur.</span><span class="sxs-lookup"><span data-stu-id="054d9-107">The purpose of a pipeline is to prepare a message for processing by the server after being received by an adapter or to prepare a message for sending after being processed by the server.</span></span>  
  
 <span data-ttu-id="054d9-108">Tâches couramment effectuées par les pipelines :</span><span class="sxs-lookup"><span data-stu-id="054d9-108">Pipelines commonly perform:</span></span>  
  
-   <span data-ttu-id="054d9-109">Régularisation des données à partir de divers formats vers le format XML</span><span class="sxs-lookup"><span data-stu-id="054d9-109">Data normalization from various formats to XML.</span></span>  
  
-   <span data-ttu-id="054d9-110">Conversion des données à partir du format XML vers divers formats</span><span class="sxs-lookup"><span data-stu-id="054d9-110">Data transformation from XML to various formats.</span></span>  
  
-   <span data-ttu-id="054d9-111">Promotion et rétrogradation des propriétés</span><span class="sxs-lookup"><span data-stu-id="054d9-111">Property promotion and demotion.</span></span>  
  
-   <span data-ttu-id="054d9-112">Désassemblage et assemblage de documents</span><span class="sxs-lookup"><span data-stu-id="054d9-112">Document disassembly and assembly.</span></span>  
  
-   <span data-ttu-id="054d9-113">Codage et décodage de documents</span><span class="sxs-lookup"><span data-stu-id="054d9-113">Document decoding and encoding.</span></span>  
  
-   <span data-ttu-id="054d9-114">Chiffrement et déchiffrement de documents</span><span class="sxs-lookup"><span data-stu-id="054d9-114">Document decryption and encryption.</span></span>  
  
-   <span data-ttu-id="054d9-115">Signature de documents et vérification de signatures numériques</span><span class="sxs-lookup"><span data-stu-id="054d9-115">Document signing and digital signature verification.</span></span>  
  
 <span data-ttu-id="054d9-116">La figure ci-dessous montre le workflow que suppose le traitement d'un message à l'aide de pipelines.</span><span class="sxs-lookup"><span data-stu-id="054d9-116">The following figure shows the workflow involved in processing a message by using pipelines.</span></span>  
  
 <span data-ttu-id="054d9-117">![Diagramme de flux de travail pour le traitement d’un message. ] (../core/media/ebiz-dev-busprcsadptc.gif "ebiz_dev_busprcsadptc")</span><span class="sxs-lookup"><span data-stu-id="054d9-117">![Diagram of workflow for processing a message.](../core/media/ebiz-dev-busprcsadptc.gif "ebiz_dev_busprcsadptc")</span></span>  
<span data-ttu-id="054d9-118">Illustration du workflow de traitement d'un message</span><span class="sxs-lookup"><span data-stu-id="054d9-118">Depicts the message processing workflow.</span></span>  
  
 <span data-ttu-id="054d9-119">Comme le montre la figure, le message passe de l'adaptateur au pipeline de réception, où il est converti au format XML.</span><span class="sxs-lookup"><span data-stu-id="054d9-119">As shown in the figure, the message is passed from the adapter to the receive pipeline where it is transformed to XML.</span></span> <span data-ttu-id="054d9-120">Le message peut alors être utilisé par des orchestrations ou être transmis à un pipeline d'envoi puis à un adaptateur d'envoi.</span><span class="sxs-lookup"><span data-stu-id="054d9-120">The message can then be used by orchestrations, or passed to a send pipeline, and then to a send adapter.</span></span>  
  
 <span data-ttu-id="054d9-121">Pour plus d’informations sur l’utilisation des raccourcis clavier pour le Concepteur de Pipeline, consultez [raccourcis clavier de Concepteur de Pipeline](../core/pipeline-designer-keyboard-shortcuts.md).</span><span class="sxs-lookup"><span data-stu-id="054d9-121">For information about using the keyboard shortcuts for Pipeline Designer, see [Pipeline Designer Keyboard Shortcuts](../core/pipeline-designer-keyboard-shortcuts.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="054d9-122">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="054d9-122">In This Section</span></span>  
  
-   [<span data-ttu-id="054d9-123">À propos des Pipelines, des étapes et des composants</span><span class="sxs-lookup"><span data-stu-id="054d9-123">About Pipelines, Stages, and Components</span></span>](../core/about-pipelines-stages-and-components.md)  
  
-   [<span data-ttu-id="054d9-124">À l’aide du Concepteur de Pipeline</span><span class="sxs-lookup"><span data-stu-id="054d9-124">Using Pipeline Designer</span></span>](../core/using-pipeline-designer.md)  
  
-   [<span data-ttu-id="054d9-125">Création de Pipelines avec le Concepteur de Pipeline</span><span class="sxs-lookup"><span data-stu-id="054d9-125">Creating Pipelines with Pipeline Designer</span></span>](../core/creating-pipelines-with-pipeline-designer.md)  
  
-   [<span data-ttu-id="054d9-126">Configuration des composants de Pipeline natifs</span><span class="sxs-lookup"><span data-stu-id="054d9-126">Configuring Native Pipeline Components</span></span>](../core/configuring-native-pipeline-components.md)  
  
-   [<span data-ttu-id="054d9-127">Comment déployer des Pipelines</span><span class="sxs-lookup"><span data-stu-id="054d9-127">How to Deploy Pipelines</span></span>](../core/how-to-deploy-pipelines.md)  
  
-   [<span data-ttu-id="054d9-128">Sécurisation des Pipelines</span><span class="sxs-lookup"><span data-stu-id="054d9-128">How to Secure Pipelines</span></span>](../core/how-to-secure-pipelines.md)