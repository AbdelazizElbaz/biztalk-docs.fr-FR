---
title: "À l’aide de l’analyse BAM intercepteurs WCF et WF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8a87a643-8e15-47d1-8d2a-3d899a1494ff
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ea631ed3a9058128a71373b6e6c7eb55ebad6c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-bam-wcf-and-wf-interceptors"></a><span data-ttu-id="8cfad-102">Utilisation des intercepteurs WCF et WF BAM</span><span class="sxs-lookup"><span data-stu-id="8cfad-102">Using the BAM WCF and WF Interceptors</span></span>
<span data-ttu-id="8cfad-103">Les intercepteurs BAM étendent les fonctionnalités de l'intercepteur BAM pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans Windows Workflow Foundation (WF), Windows Communication Foundation (WCF) et d'autres environnements d'exécution.</span><span class="sxs-lookup"><span data-stu-id="8cfad-103">BAM interceptors extend the BAM interceptor functionality for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] into Windows Workflow Foundation (WF), Windows Communication Framework (WCF), and other runtime environments.</span></span> <span data-ttu-id="8cfad-104">Ils permettent de suivre vos processus d'entreprise sans recompiler votre solution WF ou WCF : l'intégration est effectuée via un fichier de configuration à l'aide d'un fichier XML et d'une série d'éléments qui mappent les événements de l'application aux activités BAM et définissent les données, l'ID de corrélation, le jeton de continuation et d'autres artefacts requis et facultatifs.</span><span class="sxs-lookup"><span data-stu-id="8cfad-104">By using a BAM interceptor, you can track your business processes without recompiling your WF or WCF solution — integration is done through a configuration file using XML and a series of elements that map application events to BAM activities and define the data, correlation ID, continuation token and other required and optional artifacts.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8cfad-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8cfad-105">In This Section</span></span>  
  
-   [<span data-ttu-id="8cfad-106">Quelles sont les BAM intercepteurs WCF et WF ?</span><span class="sxs-lookup"><span data-stu-id="8cfad-106">What Are the BAM WCF and WF Interceptors?</span></span>](../core/what-are-the-bam-wcf-and-wf-interceptors.md)  
  
-   [<span data-ttu-id="8cfad-107">Problèmes connus avec l’analyse BAM intercepteurs WCF et WF</span><span class="sxs-lookup"><span data-stu-id="8cfad-107">Known Issues with the BAM WCF and WF Interceptors</span></span>](../core/known-issues-with-the-bam-wcf-and-wf-interceptors.md)  
  
-   [<span data-ttu-id="8cfad-108">Intercepteurs BAM dans un environnement à haute disponibilité</span><span class="sxs-lookup"><span data-stu-id="8cfad-108">BAM Interceptors in a High Availability Environment</span></span>](../core/bam-interceptors-in-a-high-availability-environment.md)  
  
-   [<span data-ttu-id="8cfad-109">Compteurs de Performance de l’intercepteur BAM</span><span class="sxs-lookup"><span data-stu-id="8cfad-109">BAM Interceptor Performance Counters</span></span>](../core/bam-interceptor-performance-counters.md)  
  
-   [<span data-ttu-id="8cfad-110">Chargement des intercepteurs BAM à l’aide de l’API BAM</span><span class="sxs-lookup"><span data-stu-id="8cfad-110">Loading BAM Interceptors Using the BAM API</span></span>](../core/loading-bam-interceptors-using-the-bam-api.md)  
  
-   [<span data-ttu-id="8cfad-111">Dépannage des intercepteurs BAM</span><span class="sxs-lookup"><span data-stu-id="8cfad-111">Troubleshooting BAM Interceptors</span></span>](../core/troubleshooting-bam-interceptors.md)  
  
-   [<span data-ttu-id="8cfad-112">Considérations de sécurité pour les intercepteurs BAM</span><span class="sxs-lookup"><span data-stu-id="8cfad-112">Security Considerations for BAM Interceptors</span></span>](../core/security-considerations-for-bam-interceptors.md)  
  
-   [<span data-ttu-id="8cfad-113">Fichier de Configuration de l’intercepteur</span><span class="sxs-lookup"><span data-stu-id="8cfad-113">Interceptor Configuration File</span></span>](../core/interceptor-configuration-file.md)  
  
-   [<span data-ttu-id="8cfad-114">Intercepteur WF BAM</span><span class="sxs-lookup"><span data-stu-id="8cfad-114">BAM WF Interceptor</span></span>](../core/bam-wf-interceptor.md)  
  
-   [<span data-ttu-id="8cfad-115">Configuration de l’adaptateur WCF pour intercepter les données BAM</span><span class="sxs-lookup"><span data-stu-id="8cfad-115">Configuring the WCF Adapter to Intercept BAM Data</span></span>](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)  
  
-   [<span data-ttu-id="8cfad-116">Intercepteur WCF BAM</span><span class="sxs-lookup"><span data-stu-id="8cfad-116">BAM WCF Interceptor</span></span>](../core/bam-wcf-interceptor.md)