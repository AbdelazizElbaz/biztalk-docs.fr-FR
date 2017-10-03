---
title: "Création de la Solution Contoso | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: private process tutorial, creating solutions
ms.assetid: 02f5326a-68bd-418a-af81-684a73056e2c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e09928a724d99822d652b12daa959a7f7f380bc4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-the-contoso-solution"></a><span data-ttu-id="12f0f-102">Création de la Solution de Contoso</span><span class="sxs-lookup"><span data-stu-id="12f0f-102">Creating the Contoso Solution</span></span>
<span data-ttu-id="12f0f-103">Cette section détaille les étapes à suivre pour l’organisation Contoso.</span><span class="sxs-lookup"><span data-stu-id="12f0f-103">This section details the steps that you have to follow for the Contoso organization.</span></span> <span data-ttu-id="12f0f-104">La première étape consiste à ajouter les contrats de partenaire et les informations de contact pour les deux organisations à l’aide de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion.</span><span class="sxs-lookup"><span data-stu-id="12f0f-104">The first step is to add the contact information and partner agreements for the two organizations using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console.</span></span> <span data-ttu-id="12f0f-105">Vous créez ensuite les schémas de métier (LOB) et construisez un mappage entre ces schémas et leurs schémas respectifs de la base RosettaNet processus PIP (Partner Interface).</span><span class="sxs-lookup"><span data-stu-id="12f0f-105">You then create line-of-business (LOB) schemas, and construct a mapping between those schemas and their respective RosettaNet-based Partner Interface Process (PIP) schemas.</span></span> <span data-ttu-id="12f0f-106">Ensuite, vous configurez les informations de port à l’aide de l’adaptateur SQL pour communiquer avec le système ERP et l’adaptateur HTTP pour envoyer des informations à Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="12f0f-106">Next, you configure port information using the SQL adapter for communicating with the ERP system, and the HTTP adapter for sending information to Fabrikam.</span></span> <span data-ttu-id="12f0f-107">La dernière étape consiste à personnaliser l’orchestration de processus privé pour utiliser le moteur de règles d’entreprise (BRE) dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12f0f-107">The last step is to customize the private process orchestration to use the Business Rule Engine (BRE) in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="12f0f-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="12f0f-108">In This Section</span></span>  
  
-   [<span data-ttu-id="12f0f-109">Création d’organisations et de Contoso accord de partenariat commercial</span><span class="sxs-lookup"><span data-stu-id="12f0f-109">Creating Organizations and Trading Partner Agreement for Contoso</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-organizations-and-trading-partner-agreement-for-contoso.md)  
  
-   [<span data-ttu-id="12f0f-110">Création des mappages et schémas LOB Contoso</span><span class="sxs-lookup"><span data-stu-id="12f0f-110">Creating the Contoso LOB Schemas and Maps</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-the-contoso-lob-schemas-and-maps.md)  
  
-   [<span data-ttu-id="12f0f-111">Création et configuration des Ports BizTalk pour Contoso</span><span class="sxs-lookup"><span data-stu-id="12f0f-111">Creating and Configuring BizTalk Ports for Contoso</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-biztalk-ports-for-contoso.md)  
  
-   [<span data-ttu-id="12f0f-112">Création et modification du processus privé pour Contoso</span><span class="sxs-lookup"><span data-stu-id="12f0f-112">Creating and Modifying the Private Process for Contoso</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-modifying-the-private-process-for-contoso.md)