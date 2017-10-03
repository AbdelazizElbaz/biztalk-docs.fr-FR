---
title: "Sur le processus d’enregistrement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- logging, about logging
- auditing, about auditing
- logging
- auditing
ms.assetid: 859ee1f5-aae4-4a47-ab39-8d2b4168a429
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07dba617358d6ad451c53eeb75dbe5d1986f9066
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-the-logging-process"></a><span data-ttu-id="6c316-102">Sur le processus d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="6c316-102">About the Logging Process</span></span>
<span data-ttu-id="6c316-103">Étant donné que vos applications gèrent critiques, données sensibles et monétaires heure, l’audit devient un élément essentiel de l’application.</span><span class="sxs-lookup"><span data-stu-id="6c316-103">Since your applications handle critical, time sensitive and monetary data, auditing becomes a critical part of the application.</span></span> <span data-ttu-id="6c316-104">Pour activer la gestion de niveau entreprise et la disponibilité, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] s’appuie sur l’exécution partagée suivante et les composants d’administration :</span><span class="sxs-lookup"><span data-stu-id="6c316-104">To enable enterprise level manageability and availability, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] relies on the following shared run time and administrative components:</span></span>  
  
-   <span data-ttu-id="6c316-105">**Journalisation**: pour collecter et acheminer tous les événements du journal d’une manière managée pour une base de données désigné</span><span class="sxs-lookup"><span data-stu-id="6c316-105">**Logging**: to collect and route all log events in a managed way to a designated database</span></span>  
  
-   <span data-ttu-id="6c316-106">**Surveillance des événements et le débogage de Service**: pour configurer le comportement de journalisation et pour examiner et gérer les informations collectées pour les administrateurs système et autres professionnels de l’informatique</span><span class="sxs-lookup"><span data-stu-id="6c316-106">**Event Monitoring and Service Debugging**: to configure logging behavior and to investigate/manage collected information for system administrators and other IT professionals</span></span>  
  
 <span data-ttu-id="6c316-107">Fonctionnalités d’audit avec le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)], vous pouvez optimiser l’efficacité opérationnelle, de sécurité et de performances pour assurer la conformité aux réglementations de HL7.</span><span class="sxs-lookup"><span data-stu-id="6c316-107">With the enhanced auditing features in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)], you can optimize your operational efficiency, security, and performance to ensure compliance with HL7 regulations.</span></span>  
  
## <a name="types-of-data"></a><span data-ttu-id="6c316-108">Types de données</span><span class="sxs-lookup"><span data-stu-id="6c316-108">Types of Data</span></span>  
 <span data-ttu-id="6c316-109">Cette rubrique décrit les différents types de données de journalisation utilisées par la fonctionnalité de journalisation et où ces données sont stockées :</span><span class="sxs-lookup"><span data-stu-id="6c316-109">This topic describes different types of logging data used by the logging feature and where this data is stored:</span></span>  
  
-   <span data-ttu-id="6c316-110">Données de configuration : enregistrement de données de configuration sont stockée dans la base de données de Configuration (également appelée la base de données BizTalk Management) et inclut des informations et audit des données d’audit de SQL ([!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)] Observateur d’événements, la base de données centralisée WMI) emplacement.</span><span class="sxs-lookup"><span data-stu-id="6c316-110">Configuration data: Logging configuration data is stored in the Configuration database (also known as the BizTalk Management database) and includes SQL auditing information and audit data ([!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)] Event viewer, centralized database WMI) location.</span></span>  
  
-   <span data-ttu-id="6c316-111">Données d’archivage : table du journal des événements dans le journal SQL stocke les données de « Enregistrement ».</span><span class="sxs-lookup"><span data-stu-id="6c316-111">Archival data: The EventLog table in the SQL log stores the 'Logging' data.</span></span>  
  
## <a name="how-logging-works"></a><span data-ttu-id="6c316-112">Fonctionne de la journalisation</span><span class="sxs-lookup"><span data-stu-id="6c316-112">How Logging Works</span></span>  
 <span data-ttu-id="6c316-113">Cette rubrique décrit les trois types d’événements se connecte le logiciel, ainsi que les trois emplacements où vous pouvez stocker les données enregistrées.</span><span class="sxs-lookup"><span data-stu-id="6c316-113">This topic describes the three types of events the software logs, as well as the three locations where you can store the logged data.</span></span>  
  
|<span data-ttu-id="6c316-114">Composant</span><span class="sxs-lookup"><span data-stu-id="6c316-114">Component</span></span>|<span data-ttu-id="6c316-115">Fonction</span><span class="sxs-lookup"><span data-stu-id="6c316-115">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="6c316-116">Éditeur de configuration</span><span class="sxs-lookup"><span data-stu-id="6c316-116">Configuration Editor</span></span>|<span data-ttu-id="6c316-117">Pour spécifier l’emplacement où enregistrer les données du journal.</span><span class="sxs-lookup"><span data-stu-id="6c316-117">To specify where to save the log data.</span></span> <span data-ttu-id="6c316-118">BTAHL7 prend en charge la journalisation dans n’importe quelle combinaison des éléments suivants : journalisation de l’Observateur d’événements, WMI et SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6c316-118">BTAHL7 supports logging to any combination of the following: Event Viewer, WMI, and SQL Server logging.</span></span>|  
|<span data-ttu-id="6c316-119">Événement Broker</span><span class="sxs-lookup"><span data-stu-id="6c316-119">Event Broker</span></span>|<span data-ttu-id="6c316-120">Pour recevoir le journal des événements déclenchés par d’autres composants et ouvrir une session en fonction des données de configuration de journalisation.</span><span class="sxs-lookup"><span data-stu-id="6c316-120">To receive log events raised by other components and log them based on logging configuration data.</span></span>|  
|<span data-ttu-id="6c316-121">API de journalisation</span><span class="sxs-lookup"><span data-stu-id="6c316-121">Logging API</span></span>|<span data-ttu-id="6c316-122">Journalisation de l’interface appelée par tous les assemblys de BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="6c316-122">Logging interface called by all BTAHL7 assemblies.</span></span>|  
  
### <a name="types-of-logging"></a><span data-ttu-id="6c316-123">Types de journalisation</span><span class="sxs-lookup"><span data-stu-id="6c316-123">Types of Logging</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="6c316-124">enregistre les trois types d’erreurs :</span><span class="sxs-lookup"><span data-stu-id="6c316-124"> logs three types of errors:</span></span>  
  
-   <span data-ttu-id="6c316-125">Événements d’information, d’un service démarré ou arrêté ou d’un événement a échoué.</span><span class="sxs-lookup"><span data-stu-id="6c316-125">Informational events, such a service started or stopped or an event failed.</span></span>  
  
-   <span data-ttu-id="6c316-126">Événements d’avertissement tels que des erreurs non critiques et avertissements dans [!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)] des journaux des événements.</span><span class="sxs-lookup"><span data-stu-id="6c316-126">Warning events such as non-critical errors and warnings in [!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)] Event logs.</span></span> <span data-ttu-id="6c316-127">Par exemple, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] suspend un message, car la validation des données a échoué.</span><span class="sxs-lookup"><span data-stu-id="6c316-127">For example, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] suspends a message because data validation failed.</span></span>  
  
-   <span data-ttu-id="6c316-128">Événements d’erreur pour les défaillances critiques dans un composant.</span><span class="sxs-lookup"><span data-stu-id="6c316-128">Error events for critical failures in a component.</span></span> <span data-ttu-id="6c316-129">Par exemple, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] suspend un message en raison d’échecs de l’analyseur.</span><span class="sxs-lookup"><span data-stu-id="6c316-129">For example, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] suspends a message because of parser failures.</span></span>  
  
 <span data-ttu-id="6c316-130">Le système peut se connecter [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] des événements dans des emplacements configurables suivants :</span><span class="sxs-lookup"><span data-stu-id="6c316-130">The system can log [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] events into following configurable locations:</span></span>  
  
-   [!INCLUDE[btsWinNTNoVersion](../../includes/btswinntnoversion-md.md)]<span data-ttu-id="6c316-131">Observateur d’événements</span><span class="sxs-lookup"><span data-stu-id="6c316-131"> Event viewer</span></span>  
  
-   <span data-ttu-id="6c316-132">Événements WMI</span><span class="sxs-lookup"><span data-stu-id="6c316-132">WMI events</span></span>  
  
-   <span data-ttu-id="6c316-133">Base de données centralisée (base de données de journalisation SQL)</span><span class="sxs-lookup"><span data-stu-id="6c316-133">Centralized database (SQL logging database)</span></span>  
  
 <span data-ttu-id="6c316-134">Un broker d’événements reçoit tous les [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] journalisation des événements et, selon les informations de configuration, les envoie à l’emplacement approprié.</span><span class="sxs-lookup"><span data-stu-id="6c316-134">An event broker receives all [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] logging events and, based on the configuration information, sends them to the appropriate location.</span></span>  
  
### <a name="overview-of-features"></a><span data-ttu-id="6c316-135">Vue d’ensemble des fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="6c316-135">Overview of Features</span></span>  
 <span data-ttu-id="6c316-136">Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] fournit des fonctionnalités de journalisation :</span><span class="sxs-lookup"><span data-stu-id="6c316-136">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] logging feature provides:</span></span>  
  
-   <span data-ttu-id="6c316-137">Un procédé unifié de la journalisation de tous les messages d’erreur</span><span class="sxs-lookup"><span data-stu-id="6c316-137">A unified way of logging all the error messages</span></span>  
  
-   <span data-ttu-id="6c316-138">Un référentiel centralisé pour stocker tous les détails de l’événement</span><span class="sxs-lookup"><span data-stu-id="6c316-138">A centralized repository for storing all event details</span></span>  
  
-   <span data-ttu-id="6c316-139">Un modèle objet cohérent pour les messages de journalisation à circuler vers les applications métier-discrètes</span><span class="sxs-lookup"><span data-stu-id="6c316-139">A consistent object model for logging messages flowing to discrete line-of-business applications</span></span>  
  
-   <span data-ttu-id="6c316-140">Une combinaison de journalisation et de traçage à mettre en corrélation les administrateurs de système d’aide a enregistré des erreurs avec des documents</span><span class="sxs-lookup"><span data-stu-id="6c316-140">A combination of logging and tracing to help system administrators correlate logged errors with documents</span></span>  
  
## <a name="event-log-data"></a><span data-ttu-id="6c316-141">Données de journal des événements</span><span class="sxs-lookup"><span data-stu-id="6c316-141">Event Log Data</span></span>  
 <span data-ttu-id="6c316-142">Cette rubrique décrit le format et le contenu des données du journal des événements.</span><span class="sxs-lookup"><span data-stu-id="6c316-142">This topic describes the format and content of the event log data.</span></span>  
  
 <span data-ttu-id="6c316-143">Le tableau suivant présente les données enregistrées par défaut pour les partenaires.</span><span class="sxs-lookup"><span data-stu-id="6c316-143">The following table shows typical logged data for partners.</span></span>  
  
|<span data-ttu-id="6c316-144">data</span><span class="sxs-lookup"><span data-stu-id="6c316-144">Data</span></span>|<span data-ttu-id="6c316-145"> Description</span><span class="sxs-lookup"><span data-stu-id="6c316-145">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="6c316-146">Transactionsrestauration</span><span class="sxs-lookup"><span data-stu-id="6c316-146">LogData</span></span>|<span data-ttu-id="6c316-147">Enregistrement des données</span><span class="sxs-lookup"><span data-stu-id="6c316-147">Data log</span></span>|  
|<span data-ttu-id="6c316-148">Numéro_catégorie</span><span class="sxs-lookup"><span data-stu-id="6c316-148">CategoryNumber</span></span>|<span data-ttu-id="6c316-149">Numéro de catégorie</span><span class="sxs-lookup"><span data-stu-id="6c316-149">Category number</span></span>|  
|<span data-ttu-id="6c316-150">EntryType</span><span class="sxs-lookup"><span data-stu-id="6c316-150">EntryType</span></span>|<span data-ttu-id="6c316-151">Type de l'événement</span><span class="sxs-lookup"><span data-stu-id="6c316-151">Type of the event</span></span>|  
|<span data-ttu-id="6c316-152">ID d’événement</span><span class="sxs-lookup"><span data-stu-id="6c316-152">EventId</span></span>|<span data-ttu-id="6c316-153">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="6c316-153">Event ID</span></span>|  
|<span data-ttu-id="6c316-154">MachineName</span><span class="sxs-lookup"><span data-stu-id="6c316-154">MachineName</span></span>|<span data-ttu-id="6c316-155">Nom d'ordinateur</span><span class="sxs-lookup"><span data-stu-id="6c316-155">Computer name</span></span>|  
|<span data-ttu-id="6c316-156">Message</span><span class="sxs-lookup"><span data-stu-id="6c316-156">Message</span></span>|<span data-ttu-id="6c316-157">Détails du message</span><span class="sxs-lookup"><span data-stu-id="6c316-157">Message detail</span></span>|  
|<span data-ttu-id="6c316-158">Source</span><span class="sxs-lookup"><span data-stu-id="6c316-158">Source</span></span>|<span data-ttu-id="6c316-159">Création, mise à jour, lors de la lecture, suppression, le déploiement ou l’archivage des données</span><span class="sxs-lookup"><span data-stu-id="6c316-159">Creating, updating, reading, deleting, deploying, or archiving data</span></span>|  
|<span data-ttu-id="6c316-160">TimeGenerated</span><span class="sxs-lookup"><span data-stu-id="6c316-160">TimeGenerated</span></span>|<span data-ttu-id="6c316-161">Réussite ou l’échec</span><span class="sxs-lookup"><span data-stu-id="6c316-161">Success or Failure</span></span>|  
|<span data-ttu-id="6c316-162">UserName</span><span class="sxs-lookup"><span data-stu-id="6c316-162">UserName</span></span>|<span data-ttu-id="6c316-163">Nom d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="6c316-163">User name</span></span>|  
|<span data-ttu-id="6c316-164">MsgGuid</span><span class="sxs-lookup"><span data-stu-id="6c316-164">MsgGuid</span></span>|<span data-ttu-id="6c316-165">GUID du message</span><span class="sxs-lookup"><span data-stu-id="6c316-165">Message GUID</span></span>|  
|<span data-ttu-id="6c316-166">SvcGuid</span><span class="sxs-lookup"><span data-stu-id="6c316-166">SvcGuid</span></span>|<span data-ttu-id="6c316-167">GUID du service</span><span class="sxs-lookup"><span data-stu-id="6c316-167">Service GUID</span></span>|  
|<span data-ttu-id="6c316-168">Opération</span><span class="sxs-lookup"><span data-stu-id="6c316-168">Operation</span></span>|<span data-ttu-id="6c316-169">Détail de l’opération</span><span class="sxs-lookup"><span data-stu-id="6c316-169">Operation detail</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6c316-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c316-170">See Also</span></span>  
 [<span data-ttu-id="6c316-171">Configuration de la journalisation</span><span class="sxs-lookup"><span data-stu-id="6c316-171">Configuring Logging</span></span>](../../adapters-and-accelerators/accelerator-hl7/configuring-logging.md)