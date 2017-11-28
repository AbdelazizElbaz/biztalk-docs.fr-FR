---
title: "Sélection de la banque de journalisation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, auditing
- configuring, logging
- logging, configuring
- auditing, configuring
ms.assetid: 6ba64c59-3a15-4c10-b44f-18e0e432c6d3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e15bc1f9004c79b8d87375d9fe9f6cb805e12e94
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="selecting-the-logging-store"></a><span data-ttu-id="a387e-102">Sélection de la banque de journalisation</span><span class="sxs-lookup"><span data-stu-id="a387e-102">Selecting the Logging Store</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="a387e-103">[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] vous offre l’option pour sélectionner une combinaison de journalisation de différents magasins, tel que [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Management Instrumentation (WMI), [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)], et [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] journal des événements.</span><span class="sxs-lookup"><span data-stu-id="a387e-103"> [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] provides you with the option to select a combination of different logging stores, such as [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Management Instrumentation (WMI), [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)], and [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Log.</span></span>  
  
 <span data-ttu-id="a387e-104">Vous utilisez la [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration pour configurer le magasin de journalisation.</span><span class="sxs-lookup"><span data-stu-id="a387e-104">You use the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer to configure the logging store.</span></span>  
  
 <span data-ttu-id="a387e-105">Utilisez les procédures suivantes pour ouvrir [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Explorateur de Configuration et sélectionnez le magasin de journalisation.</span><span class="sxs-lookup"><span data-stu-id="a387e-105">Use the following procedures to open [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer and select the logging store.</span></span>  
  
### <a name="to-open-btahl7-configuration-explorer"></a><span data-ttu-id="a387e-106">Pour ouvrir l’Explorateur de Configuration de BTAHL7</span><span class="sxs-lookup"><span data-stu-id="a387e-106">To open BTAHL7 Configuration Explorer</span></span>  
  
-   <span data-ttu-id="a387e-107">Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft BizTalk \<version > Accelerator pour HL7**, puis cliquez sur **BTAHL7 L’Explorateur de configuration**.</span><span class="sxs-lookup"><span data-stu-id="a387e-107">Click **Start**, click **Programs**, click **Microsoft BizTalk \<version> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
### <a name="to-select-the--logging-store"></a><span data-ttu-id="a387e-108">Pour sélectionner la banque de journalisation</span><span class="sxs-lookup"><span data-stu-id="a387e-108">To select the  logging store</span></span>  
  
1.  <span data-ttu-id="a387e-109">Dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration, dans le **paramètres globaux** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="a387e-109">In [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer, on the **Global Settings** tab, do the following:</span></span>  
  
    |<span data-ttu-id="a387e-110">Utiliser</span><span class="sxs-lookup"><span data-stu-id="a387e-110">Use this</span></span>|<span data-ttu-id="a387e-111">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="a387e-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="a387e-112">**WMI**</span><span class="sxs-lookup"><span data-stu-id="a387e-112">**WMI**</span></span>|<span data-ttu-id="a387e-113">Sélectionnez cette option si vous souhaitez générer des notifications de WMI pour BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="a387e-113">Select this option if you want to generate WMI notifications for BTAHL7.</span></span>|  
    |<span data-ttu-id="a387e-114">**SQL**</span><span class="sxs-lookup"><span data-stu-id="a387e-114">**SQL**</span></span>|<span data-ttu-id="a387e-115">Sélectionnez cette option si vous souhaitez utiliser [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] comme magasin de journalisation.</span><span class="sxs-lookup"><span data-stu-id="a387e-115">Select this option if you want to use [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] as your  logging store.</span></span> <span data-ttu-id="a387e-116">**Remarque :** BTAHL7 crée automatiquement les tables requises pour la journalisation s’ils n’existent pas.</span><span class="sxs-lookup"><span data-stu-id="a387e-116">**Note:**  BTAHL7 automatically creates the tables required for  logging if they do not exist.</span></span>|  
    |<span data-ttu-id="a387e-117">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="a387e-117">**SQL Server**</span></span>|<span data-ttu-id="a387e-118">Type de le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] nom.</span><span class="sxs-lookup"><span data-stu-id="a387e-118">Type the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] name.</span></span> <span data-ttu-id="a387e-119">Cela est nécessaire lorsque vous sélectionnez le **SQL** option.</span><span class="sxs-lookup"><span data-stu-id="a387e-119">This is required when you select the **SQL** option.</span></span> <span data-ttu-id="a387e-120">La longueur maximale autorisée est de 64 caractères.</span><span class="sxs-lookup"><span data-stu-id="a387e-120">The maximum allowed length is 64 characters.</span></span><br /><br /> <span data-ttu-id="a387e-121">Le nom de serveur et de base de données par défaut est la base de données BTAHL7 configurée.</span><span class="sxs-lookup"><span data-stu-id="a387e-121">The default server and database name is the configured BTAHL7 database.</span></span>|  
    |<span data-ttu-id="a387e-122">**Nom de la base de données**</span><span class="sxs-lookup"><span data-stu-id="a387e-122">**Database name**</span></span>|<span data-ttu-id="a387e-123">Type de le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] nom de la base de données.</span><span class="sxs-lookup"><span data-stu-id="a387e-123">Type the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database name.</span></span> <span data-ttu-id="a387e-124">Cela est nécessaire lorsque vous sélectionnez le **SQL** option.</span><span class="sxs-lookup"><span data-stu-id="a387e-124">This is required when you select the **SQL** option.</span></span> <span data-ttu-id="a387e-125">La longueur maximale autorisée est de 128 caractères.</span><span class="sxs-lookup"><span data-stu-id="a387e-125">The maximum allowed length is 128 characters.</span></span>|  
    |<span data-ttu-id="a387e-126">**Journal des événements**</span><span class="sxs-lookup"><span data-stu-id="a387e-126">**Event  Log**</span></span>|<span data-ttu-id="a387e-127">Sélectionnez cette option si vous souhaitez utiliser le [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] journal des événements en tant que votre banque de journalisation.</span><span class="sxs-lookup"><span data-stu-id="a387e-127">Select this option if you want to use the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Log as your  logging store.</span></span> <span data-ttu-id="a387e-128">Vous utilisez la [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Observateur d’événements pour afficher les messages d’événement.</span><span class="sxs-lookup"><span data-stu-id="a387e-128">You use the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Viewer to view event messages.</span></span>|  
  
2.  <span data-ttu-id="a387e-129">Cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="a387e-129">Click **Save**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a387e-130">Les paramètres régionaux des événements consignés par l’intermédiaire d’événements de journalisation varient selon les paramètres régionaux du compte de Service de journalisation.</span><span class="sxs-lookup"><span data-stu-id="a387e-130">The locale of the events logged by the  Logging event broker depend on the locale of the  Logging Service account.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a387e-131">Lorsque vous modifiez le mot de passe de compte de Service de journalisation, vous devez tout d’abord modifier le mot de passe [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsAD](../../includes/btsad-md.md)] service d’annuaire et redémarrez la journalisation du Service après avoir modifié le mot de passe du Service de journalisation sur chaque serveur.</span><span class="sxs-lookup"><span data-stu-id="a387e-131">When changing the  Logging Service account password, you should first change the password in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsAD](../../includes/btsad-md.md)] directory service, and then restart the  Logging Service after changing the  Logging Service password on every server running it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a387e-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a387e-132">See Also</span></span>  
 <span data-ttu-id="a387e-133">[Le traitement par lots du message](../../adapters-and-accelerators/accelerator-hl7/message-batching.md) </span><span class="sxs-lookup"><span data-stu-id="a387e-133">[Message Batching](../../adapters-and-accelerators/accelerator-hl7/message-batching.md) </span></span>  
 [<span data-ttu-id="a387e-134">Configuration de journalisation</span><span class="sxs-lookup"><span data-stu-id="a387e-134">Logging Configuration</span></span>](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md)