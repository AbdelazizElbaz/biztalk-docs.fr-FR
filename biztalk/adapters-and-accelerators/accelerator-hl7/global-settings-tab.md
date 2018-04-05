---
title: Onglet Paramètres globaux | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- btahl7.configurationexplorer.tab.globalsettings
helpviewer_keywords:
- configuring, auditing
- configuring, logging
- logging, configuring
- Global Settings tab [Configuration Explorer]
- auditing, configuring
ms.assetid: 057189f7-9072-4841-950f-371ba1f73a15
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 022ad14cc93b55c7ad928c06358f2714531b40b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="global-settings-tab"></a><span data-ttu-id="94e93-102">Onglet Paramètres généraux</span><span class="sxs-lookup"><span data-stu-id="94e93-102">Global Settings Tab</span></span>
<span data-ttu-id="94e93-103">Vous utilisez la **paramètres globaux** tab pour configurer le magasin de journalisation utilisé par [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)].</span><span class="sxs-lookup"><span data-stu-id="94e93-103">You use the **Global Settings** tab to configure the logging store used by [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)].</span></span>  
  
 <span data-ttu-id="94e93-104">Dans le **BTAHL7 Configuration Explorer** boîte de dialogue le **paramètres globaux** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="94e93-104">In the **BTAHL7 Configuration Explorer** dialog box, on the **Global Settings** tab, do the following:</span></span>  
  
|<span data-ttu-id="94e93-105">Utiliser</span><span class="sxs-lookup"><span data-stu-id="94e93-105">Use this</span></span>|<span data-ttu-id="94e93-106">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="94e93-106">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="94e93-107">**WMI**</span><span class="sxs-lookup"><span data-stu-id="94e93-107">**WMI**</span></span>|<span data-ttu-id="94e93-108">Sélectionnez cette option si vous souhaitez générer [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] notifications Management Instrumentation (WMI) pour BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="94e93-108">Select this option if you want to generate [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Management Instrumentation (WMI) notifications for BTAHL7.</span></span>|  
|<span data-ttu-id="94e93-109">**SQL**</span><span class="sxs-lookup"><span data-stu-id="94e93-109">**SQL**</span></span>|<span data-ttu-id="94e93-110">Sélectionnez cette option si vous souhaitez utiliser [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] comme magasin de journalisation pour BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="94e93-110">Select this option if you want to use [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] as your logging store for BTAHL7.</span></span> <span data-ttu-id="94e93-111">**Remarque :** BTAHL7 crée automatiquement les tables requises pour la journalisation s’ils n’existent pas.</span><span class="sxs-lookup"><span data-stu-id="94e93-111">**Note:**  BTAHL7 automatically creates the tables required for logging if they do not exist.</span></span>|  
|<span data-ttu-id="94e93-112">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="94e93-112">**SQL Server**</span></span>|<span data-ttu-id="94e93-113">Type de le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] nom.</span><span class="sxs-lookup"><span data-stu-id="94e93-113">Type the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] name.</span></span> <span data-ttu-id="94e93-114">Cela est nécessaire lorsque vous sélectionnez le **SQL** option.</span><span class="sxs-lookup"><span data-stu-id="94e93-114">This is required when you select the **SQL** option.</span></span> <span data-ttu-id="94e93-115">La longueur maximale autorisée est de 64 caractères.</span><span class="sxs-lookup"><span data-stu-id="94e93-115">The maximum allowed length is 64 characters.</span></span><br /><br /> <span data-ttu-id="94e93-116">Le nom de serveur et de base de données par défaut est la base de données BTAHL7 configurée.</span><span class="sxs-lookup"><span data-stu-id="94e93-116">The default server and database name is the configured BTAHL7 database.</span></span>|  
|<span data-ttu-id="94e93-117">**Nom de la base de données**</span><span class="sxs-lookup"><span data-stu-id="94e93-117">**Database name**</span></span>|<span data-ttu-id="94e93-118">Type de le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] nom de la base de données.</span><span class="sxs-lookup"><span data-stu-id="94e93-118">Type the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database name.</span></span> <span data-ttu-id="94e93-119">Cela est nécessaire lorsque vous sélectionnez le **SQL** option.</span><span class="sxs-lookup"><span data-stu-id="94e93-119">This is required when you select the **SQL** option.</span></span> <span data-ttu-id="94e93-120">La longueur maximale autorisée est de 128 caractères.</span><span class="sxs-lookup"><span data-stu-id="94e93-120">The maximum allowed length is 128 characters.</span></span>|  
|<span data-ttu-id="94e93-121">**Journal des événements**</span><span class="sxs-lookup"><span data-stu-id="94e93-121">**Event Log**</span></span>|<span data-ttu-id="94e93-122">Sélectionnez cette option si vous souhaitez utiliser le [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] journal des événements en tant que la banque de journalisation pour BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="94e93-122">Select this option if you want to use the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Log as the logging store for BTAHL7.</span></span> <span data-ttu-id="94e93-123">Vous utilisez la [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Observateur d’événements pour afficher les messages d’événement.</span><span class="sxs-lookup"><span data-stu-id="94e93-123">You use the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Viewer to view event messages.</span></span>|