---
title: "Module 6 : Déployer les règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tutorial, deploying business rules
- deploying, business rules
- business rules
ms.assetid: e8fb8993-3450-4795-80fd-ff28bff8fe97
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e890456b7ff3e467a0f513a261d12a52f92689f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="module-6-deploying-the-business-rules"></a><span data-ttu-id="74b5e-102">Module 6 : Déployer les règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="74b5e-102">Module 6: Deploying the Business Rules</span></span>
<span data-ttu-id="74b5e-103">Dans ce module, vous déployez les règles d’entreprise, confirmez votre journal d’installation et votre déploiement à l’aide de l’outil Éditeur des règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="74b5e-103">In this module, you deploy the business rules, confirm your installation log, and confirm your deployment using the Business Rule Composer tool.</span></span>  
  
 <span data-ttu-id="74b5e-104">Vous utilisez des règles d’entreprise pour vous assurer que [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] messages est conforme aux spécifications de format, les spécifications de champ et les règles de validation de réseau tel que défini dans la société pour les normes de télécommunication financières Interbank (SWIFT) dans le monde entier.</span><span class="sxs-lookup"><span data-stu-id="74b5e-104">You use business rules to ensure that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] messages adhere to format specifications, field specifications, and network validated rules as defined in the Society for Worldwide Interbank Financial Telecommunication (SWIFT) standards.</span></span> <span data-ttu-id="74b5e-105">Spécifications de format se rapportent à la structure du message dans son ensemble et caractéristiques des champs de détaillent de chaque champ dans le message.</span><span class="sxs-lookup"><span data-stu-id="74b5e-105">Format specifications pertain to the structure of the message as a whole and field specifications detail each field in the message.</span></span> <span data-ttu-id="74b5e-106">Règles de validation de réseau s’appliquent aux validations de champ croisé et sont complexes par nature.</span><span class="sxs-lookup"><span data-stu-id="74b5e-106">Network validated rules apply to cross-field validations and are complex in nature.</span></span>  
  
 <span data-ttu-id="74b5e-107">A4SWIFT fournit des spécifications de schéma XSD pour chaque message.</span><span class="sxs-lookup"><span data-stu-id="74b5e-107">A4SWIFT provides XSD schema specifications for each message.</span></span> <span data-ttu-id="74b5e-108">Le désassembleur de A4SWIFT (DASM) et l’assembleur (ASM) utilisent le schéma pour analyser ou de sérialiser et de valider les messages de fichier plat natifs.</span><span class="sxs-lookup"><span data-stu-id="74b5e-108">The A4SWIFT disassembler (DASM) and assembler (ASM) use the schema to parse or serialize and validate native flat-file messages.</span></span> <span data-ttu-id="74b5e-109">Validations sont limitées aux spécifications de format et les spécifications de champ qui le schéma de code.</span><span class="sxs-lookup"><span data-stu-id="74b5e-109">Validations are limited to format specifications and field specifications that the schema encodes.</span></span> <span data-ttu-id="74b5e-110">Toutefois, vous ne peut pas encoder certains formats et les règles associées au sein du schéma de champ.</span><span class="sxs-lookup"><span data-stu-id="74b5e-110">However, you cannot encode some formats and field related rules within the schema.</span></span>  
  
 <span data-ttu-id="74b5e-111">A4SWIFT inclut également un ensemble de règles d’entreprise qui suivent les Guides de mise en production normes SWIFT (SRG).</span><span class="sxs-lookup"><span data-stu-id="74b5e-111">A4SWIFT also includes a set of business rules that follow the SWIFT Standards Release Guides (SRG).</span></span> <span data-ttu-id="74b5e-112">Le moteur de règle entreprise (BRE) BizTalk Server appelle les stratégies d’A4SWIFT et applique les règles d’entreprise A4SWIFT.</span><span class="sxs-lookup"><span data-stu-id="74b5e-112">The BizTalk Server Business Rule Engine (BRE) calls the A4SWIFT policies and enforces the A4SWIFT business rules.</span></span>  
  
 <span data-ttu-id="74b5e-113">Ces règles d’entreprise sont incluses en raison des validations complexes relatives au format et des champs et des règles de validation de réseau qui dépassent la capacité physique du schéma.</span><span class="sxs-lookup"><span data-stu-id="74b5e-113">These business rules are included due to the complex validations relating to format and fields, and network-validated rules that are beyond the natural capability of the schema.</span></span> <span data-ttu-id="74b5e-114">Les composants SWIFT DASM ou ASM dans un pipeline de réception ou d’envoi d’appeler le moteur BRE.</span><span class="sxs-lookup"><span data-stu-id="74b5e-114">The SWIFT DASM or ASM components within a receive or send pipeline call the BRE.</span></span>  
  
 <span data-ttu-id="74b5e-115">Vous activez les validations ou désactiver en modifiant le **BREValidation** propriété pour le DASM au sein de votre pipeline.</span><span class="sxs-lookup"><span data-stu-id="74b5e-115">You turn the validations on or off by changing the **BREValidation** property for the DASM within your pipeline.</span></span>  
  
 <span data-ttu-id="74b5e-116">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="74b5e-116">This section contains:</span></span>  
  
-   [<span data-ttu-id="74b5e-117">Leçon 1 : Déploiement des règles métier connexes</span><span class="sxs-lookup"><span data-stu-id="74b5e-117">Lesson 1: Deploying the Related Business Rules</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-1-deploying-the-related-business-rules.md)  
  
-   [<span data-ttu-id="74b5e-118">Leçon 2 : Confirmer le déploiement à l’aide de l’outil de Composer de règle métier</span><span class="sxs-lookup"><span data-stu-id="74b5e-118">Lesson 2: Confirming the Deployment Using the Business Rule Composer Tool</span></span>](../../adapters-and-accelerators/accelerator-swift/lesson-2-confirming-the-deployment-using-the-business-rule-composer-tool.md)