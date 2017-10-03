---
title: "Configuration d’une Solution CIDX | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CIDX, process configuration
- creating, CIDX solutions
- CIDX, connecting to Elemica network
- agreements, CIDX
- process configuration, CIDX
- CIDX, agreements
- PIPs, importing for CIDX
- CIDX, PIPs
- CIDX, creating solutions
- CIDX, importing PIPs
- PIPs, CIDX
ms.assetid: 7f1f159f-3b09-4efd-907b-9a75f7f3ecd1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab617efc701551f1d5bcbae2a292676cc4f33251
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-up-a-cidx-solution"></a><span data-ttu-id="eb692-102">Configuration d’une Solution CIDX</span><span class="sxs-lookup"><span data-stu-id="eb692-102">Setting Up a CIDX Solution</span></span>
<span data-ttu-id="eb692-103">Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] prend en charge pour l’échange de messages XML de CIDX (Chemical Industry Data Exchange) (les normes de CIDX chem versions 2.0 et 3.0).</span><span class="sxs-lookup"><span data-stu-id="eb692-103">Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] support for CIDX (Chemical Industry Data Exchange) XML message exchange (CIDX Chem eStandards versions 2.0 and 3.0).</span></span> <span data-ttu-id="eb692-104">Cette rubrique décrit comment configurer une solution CIDX en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="eb692-104">This topic describes how to set up a CIDX solution by doing the following:</span></span>  
  
-   <span data-ttu-id="eb692-105">Configuration d’une configuration de processus</span><span class="sxs-lookup"><span data-stu-id="eb692-105">Setting up a process configuration</span></span>  
  
-   <span data-ttu-id="eb692-106">Configuration d’un accord</span><span class="sxs-lookup"><span data-stu-id="eb692-106">Setting up an agreement</span></span>  
  
-   <span data-ttu-id="eb692-107">Application d’un PIP</span><span class="sxs-lookup"><span data-stu-id="eb692-107">Applying a PIP</span></span>  
  
-   <span data-ttu-id="eb692-108">Importation d'un PIP basé sur XSD</span><span class="sxs-lookup"><span data-stu-id="eb692-108">Importing an XSD-based PIP</span></span>  
  
-   <span data-ttu-id="eb692-109">Connexion au réseau Elemica</span><span class="sxs-lookup"><span data-stu-id="eb692-109">Connecting to the Elemica Network</span></span>  
  
## <a name="setting-up-a-cidx-process-configuration"></a><span data-ttu-id="eb692-110">Installation d’une Configuration de processus CIDX</span><span class="sxs-lookup"><span data-stu-id="eb692-110">Setting Up a CIDX Process Configuration</span></span>  
 <span data-ttu-id="eb692-111">Pour configurer un échange de messages chem CIDX, vous devez créer une configuration de processus qui a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="eb692-111">To set up a CIDX eStandards message exchange, you need to create a process configuration that has the following properties:</span></span>  
  
-   <span data-ttu-id="eb692-112">**Standard** propriété dans les paramètres de configuration de processus la valeur **CIDX**</span><span class="sxs-lookup"><span data-stu-id="eb692-112">**Standard** property in the process configuration settings set to **CIDX**</span></span>  
  
-   <span data-ttu-id="eb692-113">**Est la seule Action** propriété dans les paramètres de configuration de processus la valeur **True**</span><span class="sxs-lookup"><span data-stu-id="eb692-113">**Is Single Action** property in the process configuration settings set to **True**</span></span>  
  
-   <span data-ttu-id="eb692-114">**Accord de 0 a 1** propriété dans l’accord de partenariat commercial, la valeur **aucune 0 a 1**</span><span class="sxs-lookup"><span data-stu-id="eb692-114">**0A1 agreement** property in the trading partner agreement set to **No 0A1**</span></span>  
  
 <span data-ttu-id="eb692-115">Pour plus d’informations, consultez [paramètre des CIDX chem échange de messages](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md).</span><span class="sxs-lookup"><span data-stu-id="eb692-115">For more information, see [Setting Up CIDX eStandards Message Exchange](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md).</span></span>  
  
## <a name="creating-a-cidx-agreement"></a><span data-ttu-id="eb692-116">Création d’un accord CIDX</span><span class="sxs-lookup"><span data-stu-id="eb692-116">Creating a CIDX Agreement</span></span>  
 <span data-ttu-id="eb692-117">Pour configurer un échange de messages chem CIDX, vous devez créer un accord qui a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="eb692-117">To set up a CIDX eStandards message exchange, you need to create an agreement that has the following properties:</span></span>  
  
-   <span data-ttu-id="eb692-118">**Version de RNIF** propriété dans les paramètres d’accord définie sur **V01.10.00**</span><span class="sxs-lookup"><span data-stu-id="eb692-118">**RNIF Version** property in the agreement settings set to **V01.10.00**</span></span>  
  
-   <span data-ttu-id="eb692-119">**Accord de 0 a 1** propriété dans les paramètres d’accord défini sur **aucune 0 a 1**</span><span class="sxs-lookup"><span data-stu-id="eb692-119">**0A1 agreement** property in the agreement settings set to **No 0A1**</span></span>  
  
 <span data-ttu-id="eb692-120">Pour plus d’informations, consultez [création ou modification d’un accord](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).</span><span class="sxs-lookup"><span data-stu-id="eb692-120">For more information, see [Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).</span></span>  
  
## <a name="applying-a-pip-for-cidx"></a><span data-ttu-id="eb692-121">Application d’une adresse PIP pour CIDX</span><span class="sxs-lookup"><span data-stu-id="eb692-121">Applying a PIP for CIDX</span></span>  
 <span data-ttu-id="eb692-122">Pour appliquer une adresse PIP à une implémentation CIDX, définissez la **Standard** propriété dans le profil de configuration de processus pour **CIDX**.</span><span class="sxs-lookup"><span data-stu-id="eb692-122">To apply a PIP to a CIDX implementation, set the **Standard** property in the process configuration profile to **CIDX**.</span></span> <span data-ttu-id="eb692-123">Une fois que vous avez terminé, vous serez en mesure d’entrer des valeurs pour le **standard Message**, **version Standard**, et **ID de liaison de charge utile**.</span><span class="sxs-lookup"><span data-stu-id="eb692-123">After you have finished, you will be able to enter values for the **Message standard**, **Standard version**, and **Payload binding ID**.</span></span> <span data-ttu-id="eb692-124">Vous pouvez trouver ces valeurs dans la spécification de chem CIDX normes.</span><span class="sxs-lookup"><span data-stu-id="eb692-124">You can find these values in the CIDX Chem eStandards specification.</span></span>  
  
## <a name="importing-an-xsd-based-pip-for-cidx"></a><span data-ttu-id="eb692-125">L’importation d’un PIP basé sur XSD pour CIDX</span><span class="sxs-lookup"><span data-stu-id="eb692-125">Importing an XSD-based PIP for CIDX</span></span>  
 <span data-ttu-id="eb692-126">Pour importer un PIP basé sur XSD pour CIDX, vous devez télécharger le fichier ZIP de l’adresse du PIP à partir de CIDX.org à l’adresse [http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=62361).</span><span class="sxs-lookup"><span data-stu-id="eb692-126">To import an XSD-based PIP for CIDX, you need to download the PIP's ZIP file from CIDX.org at [http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=62361).</span></span> <span data-ttu-id="eb692-127">Procédez comme décrite dans la procédure d’importation [l’importation d’un PIP basé sur XSD](../../adapters-and-accelerators/accelerator-rosettanet/importing-an-xsd-based-pip.md).</span><span class="sxs-lookup"><span data-stu-id="eb692-127">Follow the import procedure described in [Importing an XSD-based PIP](../../adapters-and-accelerators/accelerator-rosettanet/importing-an-xsd-based-pip.md).</span></span>  
  
## <a name="connecting-to-the-elemica-network"></a><span data-ttu-id="eb692-128">Connexion au réseau Elemica</span><span class="sxs-lookup"><span data-stu-id="eb692-128">Connecting to the Elemica Network</span></span>  
 <span data-ttu-id="eb692-129">Vous pouvez personnaliser [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] pour se connecter à Elemica à l’aide de fichiers de projet dans le Pack de connectivité Elemica.</span><span class="sxs-lookup"><span data-stu-id="eb692-129">You can customize [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] to connect to Elemica using project files in the Elemica Connectivity Pack.</span></span> <span data-ttu-id="eb692-130">Vous pouvez télécharger le Pack de connectivité à partir de [http://go.microsoft.com/fwlink/?LinkId=46195](http://go.microsoft.com/fwlink/?LinkId=46195).</span><span class="sxs-lookup"><span data-stu-id="eb692-130">You can download the Connectivity Pack from [http://go.microsoft.com/fwlink/?LinkId=46195](http://go.microsoft.com/fwlink/?LinkId=46195).</span></span> <span data-ttu-id="eb692-131">Pour plus d’informations, consultez le livre blanc « Connexion au réseau Elemica avec BizTalk Accelerator pour RosettaNet 3.0 » sur MSDN à l’adresse [http://go.microsoft.com/fwlink/?linkid=46539](http://go.microsoft.com/fwlink/?linkid=46539).</span><span class="sxs-lookup"><span data-stu-id="eb692-131">For more information, see the “Connecting to the Elemica Network with BizTalk Accelerator for RosettaNet 3.0” white paper on MSDN at [http://go.microsoft.com/fwlink/?linkid=46539](http://go.microsoft.com/fwlink/?linkid=46539).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb692-132">Les informations contenues dans le livre blanc « Connexion au réseau Elemica avec BizTalk Accelerator pour RosettaNet 3.0 » sont valides pour [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb692-132">The information in the "Connecting to the Elemica Network with BizTalk Accelerator for RosettaNet 3.0" white paper is valid for [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb692-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb692-133">See Also</span></span>  
 <span data-ttu-id="eb692-134">[Prise en charge CIDX](../../adapters-and-accelerators/accelerator-rosettanet/cidx-support.md) </span><span class="sxs-lookup"><span data-stu-id="eb692-134">[CIDX Support](../../adapters-and-accelerators/accelerator-rosettanet/cidx-support.md) </span></span>  
 <span data-ttu-id="eb692-135">[Normes de messagerie CIDX](../../adapters-and-accelerators/accelerator-rosettanet/cidx-messaging-standards.md) </span><span class="sxs-lookup"><span data-stu-id="eb692-135">[CIDX Messaging Standards](../../adapters-and-accelerators/accelerator-rosettanet/cidx-messaging-standards.md) </span></span>  
 <span data-ttu-id="eb692-136">[Paramètre des CIDX chem échange de messages](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md) </span><span class="sxs-lookup"><span data-stu-id="eb692-136">[Setting Up CIDX eStandards Message Exchange](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md) </span></span>  
 <span data-ttu-id="eb692-137">[Création ou modification d’un accord](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md) </span><span class="sxs-lookup"><span data-stu-id="eb692-137">[Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md) </span></span>  
 [<span data-ttu-id="eb692-138">L’importation d’un PIP basé sur XSD</span><span class="sxs-lookup"><span data-stu-id="eb692-138">Importing an XSD-based PIP</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/importing-an-xsd-based-pip.md)