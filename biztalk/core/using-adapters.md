---
title: "À l’aide des adaptateurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: adapters
ms.assetid: afdfa70e-5929-4746-99b4-e76274aa5c88
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18ffc3c198cbd6fc26290908dfcc3a90b2c8a62a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-adapters"></a><span data-ttu-id="cb3ea-102">Utilisation des adaptateurs</span><span class="sxs-lookup"><span data-stu-id="cb3ea-102">Using Adapters</span></span>
<span data-ttu-id="cb3ea-103">Cette section contient des informations complètes sur les adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="cb3ea-103">This section contains comprehensive information about adapters.</span></span> <span data-ttu-id="cb3ea-104">Elle décrit l'utilisation des adaptateurs dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et la configuration des gestionnaires d'adaptateur, ports d'envoi et emplacements de réception pour chaque adaptateur.</span><span class="sxs-lookup"><span data-stu-id="cb3ea-104">It describes how adapters are used in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and how to configure adapter handlers, send ports, and receive locations for each adapter.</span></span> <span data-ttu-id="cb3ea-105">Elle fournit des informations relatives à la prise en charge du traitement par lot décrivant l'utilisation des adaptateurs natifs dans votre solution BizTalk.</span><span class="sxs-lookup"><span data-stu-id="cb3ea-105">It provides batching support information to help you understand and use the native adapters in your BizTalk solution.</span></span>  
  
 <span data-ttu-id="cb3ea-106">Pour plus d’informations sur l’utilisation des raccourcis clavier pour les pages de propriétés de l’adaptateur, consultez [raccourcis clavier de l’adaptateur propriété Page](../core/adapter-property-page-keyboard-shortcuts.md).</span><span class="sxs-lookup"><span data-stu-id="cb3ea-106">For information about using the keyboard shortcuts for the adapter property pages, see [Adapter Property Page Keyboard Shortcuts](../core/adapter-property-page-keyboard-shortcuts.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cb3ea-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="cb3ea-107">In This Section</span></span>  
  
-   [<span data-ttu-id="cb3ea-108">Adaptateurs dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="cb3ea-108">Adapters in BizTalk Server</span></span>](../core/adapters-in-biztalk-server.md)  
  
-   [<span data-ttu-id="cb3ea-109">Le Gestionnaire du Port d’envoi dynamique est Configurable</span><span class="sxs-lookup"><span data-stu-id="cb3ea-109">Dynamic Send Port Handler is Configurable</span></span>](../core/dynamic-send-port-handler-is-configurable.md)  
  
-   [<span data-ttu-id="cb3ea-110">Considérations sur la sécurité pour les cartes</span><span class="sxs-lookup"><span data-stu-id="cb3ea-110">Security Considerations for Adapters</span></span>](../core/security-considerations-for-adapters.md)  
  
-   [<span data-ttu-id="cb3ea-111">Adaptateur SB-Messaging</span><span class="sxs-lookup"><span data-stu-id="cb3ea-111">SB-Messaging adapter</span></span>](../core/sb-messaging-adapter.md)  
  
-   [<span data-ttu-id="cb3ea-112">Adaptateur de fichier</span><span class="sxs-lookup"><span data-stu-id="cb3ea-112">File adapter</span></span>](../core/file-adapter.md)  
  
-   [<span data-ttu-id="cb3ea-113">Adaptateur FTP</span><span class="sxs-lookup"><span data-stu-id="cb3ea-113">FTP adapter</span></span>](../core/ftp-adapter.md)  

- [<span data-ttu-id="cb3ea-114">Adaptateur d’applications logiques</span><span class="sxs-lookup"><span data-stu-id="cb3ea-114">Logic App adapter</span></span>](../core/logic-app-adapter.md)
  
-   [<span data-ttu-id="cb3ea-115">Adaptateur SFTP</span><span class="sxs-lookup"><span data-stu-id="cb3ea-115">SFTP adapter</span></span>](../core/sftp-adapter.md)  
  
-   [<span data-ttu-id="cb3ea-116">Adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="cb3ea-116">HTTP adapter</span></span>](../core/http-adapter.md)  
  
-   [<span data-ttu-id="cb3ea-117">Adaptateur JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="cb3ea-117">JD Edwards EnterpriseOne adapter</span></span>](../core/jd-edwards-enterpriseone-adapter.md) 
  
-   [<span data-ttu-id="cb3ea-118">Adaptateur JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="cb3ea-118">JD Edwards OneWorld adapter</span></span>](../core/jd-edwards-oneworld-adapter.md)  
  
-   [<span data-ttu-id="cb3ea-119">Adaptateur Oracle E-Business Suite ODBC</span><span class="sxs-lookup"><span data-stu-id="cb3ea-119">Oracle E-Business Suite ODBC adapter</span></span>](../core/oracle-e-business-suite-odbc-adapter.md)  
  
-   [<span data-ttu-id="cb3ea-120">Adaptateur de base de données ODBC pour Oracle</span><span class="sxs-lookup"><span data-stu-id="cb3ea-120">Oracle Database ODBC adapter</span></span>](../core/oracle-database-odbc-adapter.md)  
  
-   [<span data-ttu-id="cb3ea-121">Adaptateur PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="cb3ea-121">PeopleSoft Enterprise adapter</span></span>](../core/peoplesoft-enterprise-adapter.md)  
  
-   [<span data-ttu-id="cb3ea-122">Adaptateur Siebel eBusiness Applications</span><span class="sxs-lookup"><span data-stu-id="cb3ea-122">Siebel eBusiness Applications adapter</span></span>](../core/siebel-ebusiness-applications-adapter.md)  
  
-   [<span data-ttu-id="cb3ea-123">Adaptateur TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="cb3ea-123">TIBCO Enterprise Message Service adapter</span></span>](../core/tibco-enterprise-message-service-adapter.md)  
  
-   [<span data-ttu-id="cb3ea-124">Adaptateur TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="cb3ea-124">TIBCO Rendezvous adapter</span></span>](../core/tibco-rendezvous-adapter.md)  
  
-   [<span data-ttu-id="cb3ea-125">Adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="cb3ea-125">MQSeries adapter</span></span>](../core/mqseries-adapter.md)  
  
-   [<span data-ttu-id="cb3ea-126">Adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="cb3ea-126">MSMQ adapter</span></span>](../core/msmq-adapter.md)  
  
-   [<span data-ttu-id="cb3ea-127">Adaptateur POP3</span><span class="sxs-lookup"><span data-stu-id="cb3ea-127">POP3 adapter</span></span>](../core/pop3-adapter.md)  
  
-   [<span data-ttu-id="cb3ea-128">Adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="cb3ea-128">SAP adapter</span></span>](../core/sap-adapter.md)  
  
-   [<span data-ttu-id="cb3ea-129">Adaptateur SMTP</span><span class="sxs-lookup"><span data-stu-id="cb3ea-129">SMTP adapter</span></span>](../core/smtp-adapter.md)  
  
-   [<span data-ttu-id="cb3ea-130">Adaptateur SOAP</span><span class="sxs-lookup"><span data-stu-id="cb3ea-130">SOAP adapter</span></span>](../core/soap-adapter.md)  
  
-   [<span data-ttu-id="cb3ea-131">Adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="cb3ea-131">SQL adapter</span></span>](../core/sql-adapter.md)  
  
-   [<span data-ttu-id="cb3ea-132">Adaptateur Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="cb3ea-132">Windows SharePoint Services adapter</span></span>](../core/windows-sharepoint-services-adapter.md)  
  
-   [<span data-ttu-id="cb3ea-133">Adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="cb3ea-133">WCF adapters</span></span>](../core/wcf-adapters.md)  
  
-   [<span data-ttu-id="cb3ea-134">Création et suppression de gestionnaires d’adaptateur</span><span class="sxs-lookup"><span data-stu-id="cb3ea-134">Creating and Deleting Adapter Handlers</span></span>](../core/creating-and-deleting-adapter-handlers.md)  
  
-   [<span data-ttu-id="cb3ea-135">Paramètres de configuration qui affectent les performances de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="cb3ea-135">Configuration Parameters that Affect Adapter Performance</span></span>](../core/configuration-parameters-that-affect-adapter-performance.md)  
  
-   [<span data-ttu-id="cb3ea-136">Dépannage des adaptateurs BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="cb3ea-136">Troubleshooting BizTalk Server Adapters</span></span>](../core/troubleshooting-biztalk-server-adapters.md)  
  
-   [<span data-ttu-id="cb3ea-137">Informations sur la carte supplémentaires</span><span class="sxs-lookup"><span data-stu-id="cb3ea-137">Additional Adapter Information</span></span>](../core/additional-adapter-information.md)