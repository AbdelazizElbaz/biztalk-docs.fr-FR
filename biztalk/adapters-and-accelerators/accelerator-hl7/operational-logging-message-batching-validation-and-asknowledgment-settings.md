---
title: "Journalisation opérationnelle, le traitement par lot des messages, les paramètres de validation et asknowledgment | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BTAHL7, administering
- managing
- BTAHL7, managing
- administering
ms.assetid: c7376de4-4e1d-47e2-acf7-0a32e7a4b073
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3282d69fc572c4aa32888f9a3ed8a806deef5c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operational-logging-message-batching-validation-and-asknowledgment-settings"></a><span data-ttu-id="810f9-102">Journalisation opérationnelle, le traitement par lot des messages, paramètres de validation et asknowledgment</span><span class="sxs-lookup"><span data-stu-id="810f9-102">Operational logging, message batching, validation and asknowledgment settings</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="810f9-103">[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] comprend un serveur et une série d’outils pour l’intégration d’application d’entreprise (IAE), automatisation des processus d’entreprise et de faciliter les interactions avec des partenaires commerciaux.</span><span class="sxs-lookup"><span data-stu-id="810f9-103"> [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] encompasses a server and series of tools for enterprise application integration (EAI), automating business processes, and facilitating interactions with business partners.</span></span> <span data-ttu-id="810f9-104">Reposant sur la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] plate-forme, BTAHL7 promeut intégration d’applications médicales pour toute installation à l’aide de la norme HL7.</span><span class="sxs-lookup"><span data-stu-id="810f9-104">Built on the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] platform, BTAHL7 promotes medical application integration for any facility using the HL7 standard.</span></span> <span data-ttu-id="810f9-105">HL7 contient les normes pour l’échange, d’intégration et de la récupération des informations électroniques de pratiques cliniques et de gestion.</span><span class="sxs-lookup"><span data-stu-id="810f9-105">HL7 contains standards for exchanging, integrating, and retrieving electronic information in clinical practice and management.</span></span>  
  
 <span data-ttu-id="810f9-106">Interface utilisateur analystes configurer des partenaires commerciaux, accusés de réception de message, le traitement par lots du message et d’autres détails que requiert votre processus d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="810f9-106">Interface user analysts configure trading partners, message acknowledgments, message batching, and other details that your business process requires.</span></span>  
  
 <span data-ttu-id="810f9-107">Cette section fournit des informations conceptuelles et des procédures qui vous permet de surveiller et maintenir votre environnement d’application de BTAHL7 efficacement.</span><span class="sxs-lookup"><span data-stu-id="810f9-107">This section provides conceptual and procedural information that enables you to effectively monitor and maintain your BTAHL7 application environment.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="810f9-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="810f9-108">In This Section</span></span>  
  
-   [<span data-ttu-id="810f9-109">Configuration de journalisation</span><span class="sxs-lookup"><span data-stu-id="810f9-109">Logging Configuration</span></span>](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md)  
  
-   [<span data-ttu-id="810f9-110">Le traitement par lots du message</span><span class="sxs-lookup"><span data-stu-id="810f9-110">Message Batching</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-batching.md)  
  
-   [<span data-ttu-id="810f9-111">Paramètres de validation</span><span class="sxs-lookup"><span data-stu-id="810f9-111">Validation Settings</span></span>](../../adapters-and-accelerators/accelerator-hl7/validation-settings.md)  
  
-   [<span data-ttu-id="810f9-112">Remplacements de champ de MSH</span><span class="sxs-lookup"><span data-stu-id="810f9-112">MSH Field Overrides</span></span>](../../adapters-and-accelerators/accelerator-hl7/msh-field-overrides.md)  
  
-   [<span data-ttu-id="810f9-113">Paramètres de l’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="810f9-113">Acknowledgment Settings</span></span>](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-settings.md)  
  
-   [<span data-ttu-id="810f9-114">Prise en charge du codage étendue</span><span class="sxs-lookup"><span data-stu-id="810f9-114">Extended Encoding Support</span></span>](../../adapters-and-accelerators/accelerator-hl7/extended-encoding-support.md)