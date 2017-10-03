---
title: "Exemples de scénarios de menace Model Analysis | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TMA, security
- security examples [TMA]
- TMA, examples
- examples, TMA
ms.assetid: e35d1d7f-a71a-42f5-b1f4-fe3234ba7686
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: afc1e375945ec7b40c56274adc5e18cb1ee67f97
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-scenarios-for-threat-model-analysis"></a><span data-ttu-id="0199e-102">Exemples de scénarios pour l'analyse du modèle des menaces</span><span class="sxs-lookup"><span data-stu-id="0199e-102">Sample Scenarios for Threat Model Analysis</span></span>
<span data-ttu-id="0199e-103">Cette section fournit les étapes et les résultats d’une analyse du modèle (menaces) pour chaque scénario d’utilisation pour l’exemple d’architecture identifié dans [exemples d’architecture pour les petites et moyennes entreprises](../core/sample-architectures-for-small-medium-sized-companies.md).</span><span class="sxs-lookup"><span data-stu-id="0199e-103">This section provides the steps and results of a threat model analysis (TMA) for each usage scenario for the sample architecture identified in [Sample Architectures for Small & Medium-Sized Companies](../core/sample-architectures-for-small-medium-sized-companies.md).</span></span> <span data-ttu-id="0199e-104">Elle illustre les différentes étapes de l'analyse du modèle des menaces,</span><span class="sxs-lookup"><span data-stu-id="0199e-104">The purpose of this section is to show you the steps of a TMA.</span></span> <span data-ttu-id="0199e-105">en décrit le fonctionnement, ainsi que les menaces potentielles identifiées pour l'exemple d'architecture et les meilleures pratiques pour réduire celles-ci.</span><span class="sxs-lookup"><span data-stu-id="0199e-105">This helps you understand how a TMA works, and describes for you the potential threats we identified for the sample architecture and how we recommend that you reduce their effect.</span></span>  
  
 <span data-ttu-id="0199e-106">Les scénarios d'utilisation sont classés sur la base des différents adaptateurs que vous pouvez utiliser avec Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et de l'utilisation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="0199e-106">We categorize the usage scenarios based on the different adapters you can use with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and the use of Enterprise Single-Sign On.</span></span>  
  
 <span data-ttu-id="0199e-107">Pour chaque scénario, nous avons effectué les étapes suivantes en vue d'exécuter l'analyse du modèle des menaces :</span><span class="sxs-lookup"><span data-stu-id="0199e-107">For each scenario, we followed these steps to complete the Threat Model Analysis:</span></span>  
  
-   <span data-ttu-id="0199e-108">Collecter les informations générales</span><span class="sxs-lookup"><span data-stu-id="0199e-108">Collect background information</span></span>  
  
-   <span data-ttu-id="0199e-109">Créer et analyser le modèle des menaces</span><span class="sxs-lookup"><span data-stu-id="0199e-109">Create and analyze the threat model</span></span>  
  
-   <span data-ttu-id="0199e-110">Passer en revue les menaces</span><span class="sxs-lookup"><span data-stu-id="0199e-110">Review threats</span></span>  
  
-   <span data-ttu-id="0199e-111">Identifier les techniques et technologies de prévention</span><span class="sxs-lookup"><span data-stu-id="0199e-111">Identify mitigation techniques and technologies</span></span>  
  
 <span data-ttu-id="0199e-112">Pour plus d’informations analyse du modèle, consultez [analyse du modèle](../core/threat-model-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="0199e-112">For more information Threat Model Analysis, see [Threat Model Analysis](../core/threat-model-analysis.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0199e-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0199e-113">In This Section</span></span>  
  
-   [<span data-ttu-id="0199e-114">Informations générales relatives aux exemples de scénarios</span><span class="sxs-lookup"><span data-stu-id="0199e-114">Background Information for Sample Scenarios</span></span>](../core/background-information-for-sample-scenarios.md)  
  
-   [<span data-ttu-id="0199e-115">Exemple de menaces : Adaptateurs HTTP et SOAP</span><span class="sxs-lookup"><span data-stu-id="0199e-115">Sample TMA: HTTP and SOAP Adapters</span></span>](../core/sample-tma-http-and-soap-adapters.md)  
  
-   [<span data-ttu-id="0199e-116">Exemple de menaces : Adaptateur Message Queuing BizTalk</span><span class="sxs-lookup"><span data-stu-id="0199e-116">Sample TMA: BizTalk Message Queuing Adapter</span></span>](../core/sample-tma-biztalk-message-queuing-adapter.md)  
  
-   [<span data-ttu-id="0199e-117">Exemple menaces : Adaptateur de fichier</span><span class="sxs-lookup"><span data-stu-id="0199e-117">Sample TMA: File Adapter</span></span>](../core/sample-tma-file-adapter.md)  
  
-   [<span data-ttu-id="0199e-118">Exemple de menaces : L’adaptateur FTP</span><span class="sxs-lookup"><span data-stu-id="0199e-118">Sample TMA: FTP Adapter</span></span>](../core/sample-tma-ftp-adapter.md)  
  
-   [<span data-ttu-id="0199e-119">Exemple de menaces : Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="0199e-119">Sample TMA: Enterprise Single Sign-On</span></span>](../core/sample-tma-enterprise-single-sign-on.md)