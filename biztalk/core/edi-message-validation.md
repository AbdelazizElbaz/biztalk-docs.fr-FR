---
title: Validation des messages EDI | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71f34561-d280-48bb-b1dd-ce37b87c5023
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21439969bc8e23b5b9901077c14a98128aa64c2b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-message-validation"></a><span data-ttu-id="ad4ab-102">Validation des messages EDI</span><span class="sxs-lookup"><span data-stu-id="ad4ab-102">EDI Message Validation</span></span>
<span data-ttu-id="ad4ab-103">Les données EDI sont transmises sous forme de fichiers délimités (sans balise autodescriptive). Les règles de codage appliquent donc des règles de formatage strictes pour garantir que l'application de destination peut analyser correctement les informations et les utiliser en vue du traitement en aval.</span><span class="sxs-lookup"><span data-stu-id="ad4ab-103">EDI data is transmitted as delimited files (without self describing tags) and therefore the encoding rules enforce strict formatting rules to ensure the destination application is able to successfully parse and consume the information for downstream processing.</span></span>  
  
 <span data-ttu-id="ad4ab-104">Le pipeline de réception EDI et le pipeline d'envoi EDI des fonctionnalités EDI et AS2 de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] réalisent une série de validations.</span><span class="sxs-lookup"><span data-stu-id="ad4ab-104">The EDI receive pipeline and EDI send pipeline in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI and AS2 perform a series of validations.</span></span> <span data-ttu-id="ad4ab-105">Certaines sont effectuées systématiquement ; d'autres seulement si elles sont activées dans les propriétés de l'accord ou dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="ad4ab-105">Some are always performed; others are performed if enabled in agreement properties or in the schema.</span></span> <span data-ttu-id="ad4ab-106">Pour plus d’informations sur la configuration de la validation, consultez [la Validation d’un EDI de l’échange est configuré](../core/how-validation-of-an-edi-interchange-is-configured.md).</span><span class="sxs-lookup"><span data-stu-id="ad4ab-106">For more information about how validation is configured, see [How Validation of an EDI Interchange Is Configured](../core/how-validation-of-an-edi-interchange-is-configured.md).</span></span>  
  
 <span data-ttu-id="ad4ab-107">La validation d'un échange EDI implique plusieurs types de validation différents, comme décrit dans les rubriques suivantes.</span><span class="sxs-lookup"><span data-stu-id="ad4ab-107">Validation of an EDI interchange involves several different kinds of validation, as described in the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ad4ab-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ad4ab-108">In This Section</span></span>  
  
-   [<span data-ttu-id="ad4ab-109">Configuration de la Validation d’un échange EDI</span><span class="sxs-lookup"><span data-stu-id="ad4ab-109">How Validation of an EDI Interchange Is Configured</span></span>](../core/how-validation-of-an-edi-interchange-is-configured.md)  
  
-   [<span data-ttu-id="ad4ab-110">Validation structurelle EDI</span><span class="sxs-lookup"><span data-stu-id="ad4ab-110">EDI Structural Validation</span></span>](../core/edi-structural-validation.md)  
  
-   [<span data-ttu-id="ad4ab-111">Validation des propriétés de contrat</span><span class="sxs-lookup"><span data-stu-id="ad4ab-111">Agreement Properties Validation</span></span>](../core/agreement-properties-validation.md)  
  
-   [<span data-ttu-id="ad4ab-112">Validation de Type (élément de données) EDI</span><span class="sxs-lookup"><span data-stu-id="ad4ab-112">EDI Type (Data Element) Validation</span></span>](../core/edi-type-data-element-validation.md)  
  
-   [<span data-ttu-id="ad4ab-113">Validation étendue (BTS-XSD)</span><span class="sxs-lookup"><span data-stu-id="ad4ab-113">Extended (BTS-XSD) Validation</span></span>](../core/extended-bts-xsd-validation.md)  
  
-   [<span data-ttu-id="ad4ab-114">Validation de schéma</span><span class="sxs-lookup"><span data-stu-id="ad4ab-114">Schema Validation</span></span>](../core/schema-validation2.md)  
  
-   [<span data-ttu-id="ad4ab-115">Validation de Segment de champ croisée</span><span class="sxs-lookup"><span data-stu-id="ad4ab-115">Cross Field-Segment Validation</span></span>](../core/cross-field-segment-validation.md)