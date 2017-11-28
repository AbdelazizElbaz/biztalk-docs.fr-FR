---
title: "Sauvegarde d’un ordinateur exécutant BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70f53b41-8083-4b56-8698-e75a13b21a69
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 537ea40b39ecd35127b62f8d96f0175e98a1f3b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="backing-up-a-computer-running-biztalk-server"></a><span data-ttu-id="f36d6-102">Sauvegarde d'un ordinateur exécutant BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="f36d6-102">Backing Up a Computer Running BizTalk Server</span></span>
<span data-ttu-id="f36d6-103">Si un ordinateur BizTalk Server rencontre une défaillance matérielle irrécupérable, vous devez le remplacer par un ordinateur identique.</span><span class="sxs-lookup"><span data-stu-id="f36d6-103">If a computer running BizTalk Server suffers an irrecoverable hardware failure, then you must replace that computer with an identical one.</span></span> <span data-ttu-id="f36d6-104">Vous devez configurer l'ordinateur de remplacement avec la plateforme logicielle de base, les composants logiciels requis, les composants BizTalk Server et des paramètres de configuration identiques.</span><span class="sxs-lookup"><span data-stu-id="f36d6-104">You should set up the replacement computer with the base platform software, software prerequisites, BizTalk Server components, and identical configuration settings.</span></span> <span data-ttu-id="f36d6-105">Ces derniers sont constitués des entrées de Registre, fichiers, dossiers et services Windows associés appropriés, nécessaires au fonctionnement correct de vos applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="f36d6-105">These configuration settings may consist of the appropriate registry entries, files, folders, and related Windows services necessary for the correct operation of your BizTalk applications.</span></span>  
  
 <span data-ttu-id="f36d6-106">Outre la sauvegarde des bases de données BizTalk Server, vous devez sauvegarder les composants BizTalk Server suivants pour permettre la récupération de BizTalk Server suite à une défaillance matérielle :</span><span class="sxs-lookup"><span data-stu-id="f36d6-106">In addition to backing up the BizTalk Server databases, you should back up the following BizTalk Server components to ensure that you can recover BizTalk Server after a hardware failure:</span></span>  
  
-   <span data-ttu-id="f36d6-107">configuration de BizTalk Server ;</span><span class="sxs-lookup"><span data-stu-id="f36d6-107">BizTalk Server configuration</span></span>  
  
-   <span data-ttu-id="f36d6-108">secret principal de l'authentification unique de l'entreprise (SSO) ;</span><span class="sxs-lookup"><span data-stu-id="f36d6-108">Enterprise Single Sign-On (SSO) master secret</span></span>  
  
-   <span data-ttu-id="f36d6-109">portail BAM (Business Activity Monitoring) (non requis, sauf si vous utilisez l'analyse BAM) ;</span><span class="sxs-lookup"><span data-stu-id="f36d6-109">Business Activity Monitoring (BAM) portal (not required unless you're using BAM)</span></span>  
  
-   <span data-ttu-id="f36d6-110">applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="f36d6-110">BizTalk applications</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f36d6-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f36d6-111">In This Section</span></span>  
  
-   [<span data-ttu-id="f36d6-112">Comment faire pour sauvegarder la Configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="f36d6-112">How to Back Up The BizTalk Server Configuration</span></span>](../core/how-to-back-up-the-biztalk-server-configuration.md)  
  
-   [<span data-ttu-id="f36d6-113">Comment sauvegarder le Secret principal</span><span class="sxs-lookup"><span data-stu-id="f36d6-113">How to Back Up the Master Secret</span></span>](../core/how-to-back-up-the-master-secret.md)  
  
-   [<span data-ttu-id="f36d6-114">Comment sauvegarder le portail BAM</span><span class="sxs-lookup"><span data-stu-id="f36d6-114">How to Back Up the BAM Portal</span></span>](../core/how-to-back-up-the-bam-portal.md)  
  
-   [<span data-ttu-id="f36d6-115">Sauvegarde des Applications BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="f36d6-115">Backing Up BizTalk Server Applications</span></span>](../core/backing-up-biztalk-server-applications.md)