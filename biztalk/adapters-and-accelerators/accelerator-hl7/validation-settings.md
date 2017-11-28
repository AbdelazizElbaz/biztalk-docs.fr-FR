---
title: "Paramètres de validation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating, configuring
- configuring, validating
ms.assetid: ee08acac-99f9-4403-b2ae-01b80378aa58
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 108f13dfbdc7b42027f57e70d913202b4d4e3100
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validation-settings"></a><span data-ttu-id="b05cf-102">Paramètres de validation</span><span class="sxs-lookup"><span data-stu-id="b05cf-102">Validation Settings</span></span>
<span data-ttu-id="b05cf-103">À l’aide de [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)], vous pouvez valider vos messages par rapport à la norme HL7.</span><span class="sxs-lookup"><span data-stu-id="b05cf-103">Using [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)], you can validate your messages against the HL7 standard.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="b05cf-104">garantit que les messages que vous envoyez ou recevez un segment de structure et le corps de message qui est conforme à la norme HL7.</span><span class="sxs-lookup"><span data-stu-id="b05cf-104"> ensures that the messages you send or receive have a message structure and body segment that conforms to the HL7 standard.</span></span> <span data-ttu-id="b05cf-105">Vous pouvez également valider HL7 pris en charge les types de données personnalisés et autoriser les délimiteurs de fin.</span><span class="sxs-lookup"><span data-stu-id="b05cf-105">You can also validate HL7 supported custom data types, and allow trailing delimiters.</span></span> <span data-ttu-id="b05cf-106">Vous utilisez la [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **Validation** onglet pour configurer la validation.</span><span class="sxs-lookup"><span data-stu-id="b05cf-106">You use the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **Validation** tab to configure validation.</span></span>  
  
## <a name="configuring-validation-settings"></a><span data-ttu-id="b05cf-107">Configuration des paramètres de Validation</span><span class="sxs-lookup"><span data-stu-id="b05cf-107">Configuring Validation Settings</span></span>  
 <span data-ttu-id="b05cf-108">Vous utilisez la **Validation** onglet de [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration (sous le niveau supérieur **Parties** onglet) pour configurer les paramètres de validation.</span><span class="sxs-lookup"><span data-stu-id="b05cf-108">You use the **Validation** tab of [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer (under the high-level **Parties** tab) to configure validation settings.</span></span> <span data-ttu-id="b05cf-109">Vous pouvez sélectionner les types de validation suivants :</span><span class="sxs-lookup"><span data-stu-id="b05cf-109">You can select the following types of validation:</span></span>  
  
-   <span data-ttu-id="b05cf-110">Syntaxe, structure et la validation de schéma sur des segments de corps, selon le schéma de message</span><span class="sxs-lookup"><span data-stu-id="b05cf-110">Syntax, structure, and schematic validation on body segments, based on the message schema</span></span>  
  
-   <span data-ttu-id="b05cf-111">Validation de HL7 standard sur les types de données personnalisés (DT, TS, TM et TN)</span><span class="sxs-lookup"><span data-stu-id="b05cf-111">HL7 standard validation on custom data types (DT, TS, TM, and TN)</span></span>  
  
-   <span data-ttu-id="b05cf-112">Validation de séparateurs de champs (des délimiteurs de fin sont autorisés)</span><span class="sxs-lookup"><span data-stu-id="b05cf-112">Validation of field delimiters (trailing delimiters are allowed)</span></span>  
  
 <span data-ttu-id="b05cf-113">À l’aide de cet onglet, vous pouvez également définir l’espace de noms du schéma utilisé pour la validation sur les messages pour ce tiers.</span><span class="sxs-lookup"><span data-stu-id="b05cf-113">Using this tab, you can also set the schema namespace used for the validation on the messages for this party.</span></span>  
  
 <span data-ttu-id="b05cf-114">L’illustration suivante montre le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **Validation** onglet.</span><span class="sxs-lookup"><span data-stu-id="b05cf-114">The following figure shows the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **Validation** tab.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-val.gif "hl7_ops_val")  
<span data-ttu-id="b05cf-115">Onglet Validation de l’Explorateur de Configuration de BTAHL7</span><span class="sxs-lookup"><span data-stu-id="b05cf-115">BTAHL7 Configuration Explorer Validation tab</span></span>  
  
 <span data-ttu-id="b05cf-116">Utilisez les procédures suivantes pour configurer les paramètres de validation.</span><span class="sxs-lookup"><span data-stu-id="b05cf-116">Use the following procedures to configure validation settings.</span></span>  
  
#### <a name="to-open-btahl7-configuration-explorer"></a><span data-ttu-id="b05cf-117">Pour ouvrir l’Explorateur de Configuration de BTAHL7</span><span class="sxs-lookup"><span data-stu-id="b05cf-117">To open BTAHL7 Configuration Explorer</span></span>  
  
-   <span data-ttu-id="b05cf-118">Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft BizTalk \<version > Accelerator pour HL7**, puis cliquez sur **BTAHL7 L’Explorateur de configuration**.</span><span class="sxs-lookup"><span data-stu-id="b05cf-118">Click **Start**, click **Programs**, click **Microsoft BizTalk \<version> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
#### <a name="to-configure-validation-settings"></a><span data-ttu-id="b05cf-119">Pour configurer les paramètres de validation</span><span class="sxs-lookup"><span data-stu-id="b05cf-119">To configure validation settings</span></span>  
  
1.  <span data-ttu-id="b05cf-120">Dans l’Explorateur de Configuration BTAHL7 sur la **Validation** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b05cf-120">In BTAHL7 Configuration Explorer on the **Validation** tab, do the following:</span></span>  
  
    |<span data-ttu-id="b05cf-121">Utiliser</span><span class="sxs-lookup"><span data-stu-id="b05cf-121">Use this</span></span>|<span data-ttu-id="b05cf-122">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="b05cf-122">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="b05cf-123">**Valider des segments de corps**</span><span class="sxs-lookup"><span data-stu-id="b05cf-123">**Validate body segments**</span></span>|<span data-ttu-id="b05cf-124">Sélectionnez cette option pour effectuer la syntaxe, la structure et la validation de schéma.</span><span class="sxs-lookup"><span data-stu-id="b05cf-124">Select this option to perform syntax, structure, and schema validation.</span></span>|  
    |<span data-ttu-id="b05cf-125">**Valider le type de données personnalisé**</span><span class="sxs-lookup"><span data-stu-id="b05cf-125">**Validate custom data type**</span></span>|<span data-ttu-id="b05cf-126">Sélectionnez cette option pour effectuer la validation HL7 standard sur les types de données personnalisés DT, TS, TM et TN.</span><span class="sxs-lookup"><span data-stu-id="b05cf-126">Select this option to perform HL7 standard validation on DT, TS, TM, and TN custom data types.</span></span>|  
    |<span data-ttu-id="b05cf-127">**Autoriser les délimiteurs (séparateur) de fin**</span><span class="sxs-lookup"><span data-stu-id="b05cf-127">**Allow trailing delimiters (separators)**</span></span>|<span data-ttu-id="b05cf-128">Sélectionnez cette option pour activer des délimiteurs de champ dans les instances de message.</span><span class="sxs-lookup"><span data-stu-id="b05cf-128">Select this option to enable trailing field delimiters in message instances.</span></span>|  
    |<span data-ttu-id="b05cf-129">**Namespace de schéma**</span><span class="sxs-lookup"><span data-stu-id="b05cf-129">**Schema Namespace**</span></span>|<span data-ttu-id="b05cf-130">Tapez l’emplacement d’espace de noms de schéma.</span><span class="sxs-lookup"><span data-stu-id="b05cf-130">Type the schema namespace location.</span></span> <span data-ttu-id="b05cf-131">La valeur par défaut est http://microsoft.com/HealthCare/HL7/2X.</span><span class="sxs-lookup"><span data-stu-id="b05cf-131">The default value is http://microsoft.com/HealthCare/HL7/2X.</span></span>|  
  
2.  <span data-ttu-id="b05cf-132">Cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="b05cf-132">Click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b05cf-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b05cf-133">See Also</span></span>  
 <span data-ttu-id="b05cf-134">[Configuration de journalisation](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="b05cf-134">[Logging Configuration](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md) </span></span>  
 <span data-ttu-id="b05cf-135">[Paramètres de l’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-settings.md) </span><span class="sxs-lookup"><span data-stu-id="b05cf-135">[Acknowledgment Settings](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-settings.md) </span></span>  
[<span data-ttu-id="b05cf-136">Journalisation opérationnelle, le traitement par lot des messages, paramètres de validation et asknowledgment</span><span class="sxs-lookup"><span data-stu-id="b05cf-136">Operational logging, message batching, validation and asknowledgment settings</span></span>](../../adapters-and-accelerators/accelerator-hl7/operational-logging-message-batching-validation-and-asknowledgment-settings.md)