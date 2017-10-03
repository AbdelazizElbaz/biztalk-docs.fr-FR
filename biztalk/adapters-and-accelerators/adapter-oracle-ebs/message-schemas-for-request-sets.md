---
title: "Schémas de message de demande définit | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bba9677d-ee94-4da5-8611-b1e47f2f3798
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6fd81ee75088b41a182c5a2aa675266420f8f32f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-request-sets"></a><span data-ttu-id="32fc8-102">Schémas de message pour les ensembles de requêtes</span><span class="sxs-lookup"><span data-stu-id="32fc8-102">Message Schemas for Request Sets</span></span>
<span data-ttu-id="32fc8-103">Chaque requête définie dans une application Oracle dans Oracle E-Business Suite est présenté comme une opération dans [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="32fc8-103">Each request set in an Oracle application in Oracle E-Business Suite is surfaced as an operation in [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)].</span></span>  
  
## <a name="message-structure-of-request-set-operation"></a><span data-ttu-id="32fc8-104">Opération de définition de Structure de message de demande</span><span class="sxs-lookup"><span data-stu-id="32fc8-104">Message Structure of Request Set Operation</span></span>  
 <span data-ttu-id="32fc8-105">Les opérations exposées en surface pour l’ensemble de la demande suivent un modèle d’échange de message demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="32fc8-105">The operations surfaced for request set follow a request-response message exchange pattern.</span></span> <span data-ttu-id="32fc8-106">Le tableau suivant illustre la structure de ces messages de demande et de réponse.</span><span class="sxs-lookup"><span data-stu-id="32fc8-106">The following table shows the structure of these request and response messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32fc8-107">Consultez les descriptions de l’entité après le tableau.</span><span class="sxs-lookup"><span data-stu-id="32fc8-107">See entity descriptions after the table.</span></span>  
  
|<span data-ttu-id="32fc8-108">Opération</span><span class="sxs-lookup"><span data-stu-id="32fc8-108">Operation</span></span>|<span data-ttu-id="32fc8-109">Message XML</span><span class="sxs-lookup"><span data-stu-id="32fc8-109">XML Message</span></span>|<span data-ttu-id="32fc8-110"> Description</span><span class="sxs-lookup"><span data-stu-id="32fc8-110">Description</span></span>|  
|---------------|-----------------|-----------------|  
|<span data-ttu-id="32fc8-111">[Request_Set_Name] Demande</span><span class="sxs-lookup"><span data-stu-id="32fc8-111">[Request_Set_Name] Request</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <[Request_Set_Name] xmlns="[VERSION]/RequestSets/[APP_SHORT_NAME]/">   <SetRelClassOptions>     <Application>[value]</Application>     <ClassName>[value]</ClassName>     <CancelOrHold>[value]</CancelOrHold>     <StaleDate>[value]</StaleDate>     <ContinueOnFail>[value]</ContinueOnFail>   </SetRelClassOptions>   <SetPrintOptions>     <Printer>[value]</Printer>     <Style>[value]</Style>     <Copies>[value]</Copies>     <SaveOutput>[value]</SaveOutput>     <PrintTogether>[value]</PrintTogether>     <ContinueOnFail>[value]</ContinueOnFail>   </SetPrintOptions>   <SetRepeatOptions>     <RepeatTime>[value]</RepeatTime>     <RepeatInterval>[value]</RepeatInterval>     <RepeatUnit>[value]</RepeatUnit>     <RepeatType>[value]</RepeatType>     <RepeatEndTime>[value]</RepeatEndTime>     <ContinueOnFail>[value]</ContinueOnFail>   </SetRepeatOptions>   <SetNlsOptions>     <Language>[value]</Language>     <Territory>[value]</Territory>     <ContinueOnFail>[value]</ContinueOnFail>   </SetNlsOptions>   <StartTime><[value]</StartTime>   <[CONCURRENT_PROGRAM_NAME1]>[value]</[CONCURRENT_PROGRAM_NAME1]>   <[CONCURRENT_PROGRAM_NAME2]>[value]</[CONCURRENT_PROGRAM_NAME2]>   … </[Request_Set_Name]>`|<span data-ttu-id="32fc8-112">-L’opération [Request_Set_Name] prend cinq paramètres standards : `SetRelClassOptions`, `SetPrintOptions`, `SetRepeatOptions`, `SetNlsOptions`, et `StartTime`.</span><span class="sxs-lookup"><span data-stu-id="32fc8-112">- The [Request_Set_Name] operation takes five standard parameters:  `SetRelClassOptions`, `SetPrintOptions`,  `SetRepeatOptions`, `SetNlsOptions`, and `StartTime`.</span></span><br /><br /> <span data-ttu-id="32fc8-113">-La `ContinueOnFail` paramètre indique si l’envoi de la demande set doit continuer ou lever une exception dans le cas le paramètre parent (`SetRelClassOptions`, `SetPrintOptions`, `SetRepeatOptions` ou `SetNlsOptions`) échoue.</span><span class="sxs-lookup"><span data-stu-id="32fc8-113">- The `ContinueOnFail` parameter indicates whether the request set submission should continue or throw an exception in case the parent parameter (`SetRelClassOptions`, `SetPrintOptions`, `SetRepeatOptions` or `SetNlsOptions`) fails.</span></span> <span data-ttu-id="32fc8-114">Vous pouvez spécifier **True** (Continuer) ou **False** (lèvent une exception).</span><span class="sxs-lookup"><span data-stu-id="32fc8-114">You can specify **True** (continue) or **False** (throw an exception).</span></span><br /><br /> <span data-ttu-id="32fc8-115">-Pour obtenir des informations détaillées sur chaque paramètre, consultez [opérations sur des ensembles de demande](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-request-sets.md).</span><span class="sxs-lookup"><span data-stu-id="32fc8-115">- For detailed information about each parameter, see [Operations on Request Sets](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-request-sets.md).</span></span>|  
|<span data-ttu-id="32fc8-116">[Request_Set_Name] Réponse</span><span class="sxs-lookup"><span data-stu-id="32fc8-116">[Request_Set_Name] Response</span></span>|`<?xml version="1.0" encoding="utf-8" ?> <[Request_Set_Name]Response xmlns="[VERSION]/RequestSets/[APP_SHORT_NAME]">   <[Request_Set_Name]Result>[value]</[Request_Set_Name]Result> </[Request_Set_Name]Response>`|<span data-ttu-id="32fc8-117">La réponse à partir d’Oracle E-Business Suite contient un ID de demandes simultanées.</span><span class="sxs-lookup"><span data-stu-id="32fc8-117">The response from Oracle E-Business Suite contains a concurrent request ID.</span></span>|  
  
 <span data-ttu-id="32fc8-118">Descriptions de l’entité :</span><span class="sxs-lookup"><span data-stu-id="32fc8-118">Entity descriptions:</span></span>  
  
 <span data-ttu-id="32fc8-119">[VERSION] = http://schemas.microsoft.com/OracleEBS/2008/05</span><span class="sxs-lookup"><span data-stu-id="32fc8-119">[VERSION] = http://schemas.microsoft.com/OracleEBS/2008/05</span></span>  
  
 <span data-ttu-id="32fc8-120">.</span><span class="sxs-lookup"><span data-stu-id="32fc8-120">.</span></span>  
  
 <span data-ttu-id="32fc8-121">[CONCURRENT_PROGRAM_NAME] = simultanées du programme inclus dans l’ensemble de la demande.</span><span class="sxs-lookup"><span data-stu-id="32fc8-121">[CONCURRENT_PROGRAM_NAME] = Concurrent program included in the request set.</span></span>  
  
## <a name="message-actions-for-request-sets"></a><span data-ttu-id="32fc8-122">Actions de message pour les ensembles de requêtes</span><span class="sxs-lookup"><span data-stu-id="32fc8-122">Message Actions for Request Sets</span></span>  
 <span data-ttu-id="32fc8-123">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] utilise les actions de message suivantes pour les ensembles de requêtes.</span><span class="sxs-lookup"><span data-stu-id="32fc8-123">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses the following message actions for request sets.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32fc8-124">Consultez les descriptions de l’entité après le tableau.</span><span class="sxs-lookup"><span data-stu-id="32fc8-124">See entity descriptions after the table.</span></span>  
  
|<span data-ttu-id="32fc8-125">Message</span><span class="sxs-lookup"><span data-stu-id="32fc8-125">Message</span></span>|<span data-ttu-id="32fc8-126">Action</span><span class="sxs-lookup"><span data-stu-id="32fc8-126">Action</span></span>|<span data-ttu-id="32fc8-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="32fc8-127">Example</span></span>|  
|-------------|------------|-------------|  
|<span data-ttu-id="32fc8-128">Demande d’ensemble</span><span class="sxs-lookup"><span data-stu-id="32fc8-128">Request Set request</span></span>|<span data-ttu-id="32fc8-129">RequestSets / [APP_SHORT_NAME] / [REQUESTSET_SHORT_NAME]</span><span class="sxs-lookup"><span data-stu-id="32fc8-129">RequestSets/[APP_SHORT_NAME]/[REQUESTSET_SHORT_NAME]</span></span>|<span data-ttu-id="32fc8-130">RequestSets/SQLGL/FNDRSSUB965</span><span class="sxs-lookup"><span data-stu-id="32fc8-130">RequestSets/SQLGL/FNDRSSUB965</span></span>|  
|<span data-ttu-id="32fc8-131">Demande de réponse</span><span class="sxs-lookup"><span data-stu-id="32fc8-131">Request Set response</span></span>|<span data-ttu-id="32fc8-132">RequestSets / [APP_SHORT_NAME] / [REQUESTSET_SHORT_NAME]] / réponse</span><span class="sxs-lookup"><span data-stu-id="32fc8-132">RequestSets/[APP_SHORT_NAME]/[REQUESTSET_SHORT_NAME]]/response</span></span>|<span data-ttu-id="32fc8-133">RequestSets/SQLGL/FNDRSSUB965/réponse</span><span class="sxs-lookup"><span data-stu-id="32fc8-133">RequestSets/SQLGL/FNDRSSUB965/response</span></span>|  
  
 <span data-ttu-id="32fc8-134">Descriptions de l’entité :</span><span class="sxs-lookup"><span data-stu-id="32fc8-134">Entity descriptions:</span></span>  
  
 <span data-ttu-id="32fc8-135">[APP_SHORT_NAME] = nom court de l’Application.</span><span class="sxs-lookup"><span data-stu-id="32fc8-135">[APP_SHORT_NAME] = Application short name.</span></span>  
  
 <span data-ttu-id="32fc8-136">[REQUESTSET_SHORT_NAME] = demande un nom court.</span><span class="sxs-lookup"><span data-stu-id="32fc8-136">[REQUESTSET_SHORT_NAME] = Request Set short name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32fc8-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32fc8-137">See Also</span></span>  
 [<span data-ttu-id="32fc8-138">Messages et des schémas de Message pour l’adaptateur BizTalk pour Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="32fc8-138">Messages and Message Schemas for BizTalk Adapter for Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)