---
title: "Étape 1 : Installation de la plate-forme de Base | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- platforms
- installing, base platform
- base platform
ms.assetid: 27da386f-90c7-414f-a4e3-e909f0c18371
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b7551972c14de0bcbd36532d76e3706a762cf48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-installing-the-base-platform"></a><span data-ttu-id="958ae-102">Étape 1 : Installation de la plate-forme de Base</span><span class="sxs-lookup"><span data-stu-id="958ae-102">Step 1: Installing the Base Platform</span></span>
<span data-ttu-id="958ae-103">Pour la plateforme de base, vous devez installer [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsWinSvr2k3](../../includes/btswinsvr2k3-md.md)] et [!INCLUDE[btsWinSvr2k3](../../includes/btswinsvr2k3-md.md)] Service Pack 2 sur chaque serveur en utilisant les options d’installation par défaut.</span><span class="sxs-lookup"><span data-stu-id="958ae-103">For the base platform, install [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsWinSvr2k3](../../includes/btswinsvr2k3-md.md)] and [!INCLUDE[btsWinSvr2k3](../../includes/btswinsvr2k3-md.md)] Service Pack 2 on each server using the default installation options.</span></span> <span data-ttu-id="958ae-104">Suivez ces recommandations :</span><span class="sxs-lookup"><span data-stu-id="958ae-104">Follow these recommendations:</span></span>  
  
## <a name="pre-installation"></a><span data-ttu-id="958ae-105">Avant l’Installation</span><span class="sxs-lookup"><span data-stu-id="958ae-105">Pre-Installation</span></span>  
  
-   <span data-ttu-id="958ae-106">Désactiver tous les logiciels antivirus lors de l’installation du logiciel.</span><span class="sxs-lookup"><span data-stu-id="958ae-106">Disable all antivirus software during software installation.</span></span> <span data-ttu-id="958ae-107">Certains logiciels antivirus peuvent empêcher les composants logiciels requis d’installer correctement.</span><span class="sxs-lookup"><span data-stu-id="958ae-107">Some antivirus software programs might prevent required software components from installing properly.</span></span>  
  
-   <span data-ttu-id="958ae-108">Assurez-vous que vous entrez les informations de licence appropriées (nombre maximal de connexions que vous avez achetées par serveur).</span><span class="sxs-lookup"><span data-stu-id="958ae-108">Make sure that you enter the appropriate licensing information (maximum number of connections you have purchased per server).</span></span> <span data-ttu-id="958ae-109">Performances du système peuvent être affectées par le nombre de connexions disponibles.</span><span class="sxs-lookup"><span data-stu-id="958ae-109">System performance can be affected by the number of available connections.</span></span>  
  
-   <span data-ttu-id="958ae-110">Assurez-vous que vous avez installé tous les logiciels requis pour un [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="958ae-110">Make sure that you have installed all the software prerequisites required for a [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] installation.</span></span> <span data-ttu-id="958ae-111">Pour plus d’informations, consultez les Instructions d’Installation de BizTalk Server à [http://go.microsoft.com/fwlink/?LinkId=81041](http://go.microsoft.com/fwlink/?LinkId=81041).</span><span class="sxs-lookup"><span data-stu-id="958ae-111">For more information, see the BizTalk Server Installation Instructions at [http://go.microsoft.com/fwlink/?LinkId=81041](http://go.microsoft.com/fwlink/?LinkId=81041).</span></span> <span data-ttu-id="958ae-112">[Guide d’installation de BizTalk 2013 R2 Accelerator pour SWIFT](http://msdn.microsoft.com/library/d2b4a9f3-baeb-4fbc-9fda-5e4178832cd1).</span><span class="sxs-lookup"><span data-stu-id="958ae-112">[Installation Guide for BizTalk 2013 R2 Accelerator for SWIFT](http://msdn.microsoft.com/library/d2b4a9f3-baeb-4fbc-9fda-5e4178832cd1).</span></span>  
  
-   <span data-ttu-id="958ae-113">Avant de les installer sur vos serveurs de production, testez toutes les mises à jour critiques dans un environnement hors connexion.</span><span class="sxs-lookup"><span data-stu-id="958ae-113">Test all critical updates in an offline environment before installing them on your production servers.</span></span>  
  
-   <span data-ttu-id="958ae-114">Assurez-vous que vous installez tous les correctifs applicables pour tous les produits que vous installez dans le cadre de votre déploiement.</span><span class="sxs-lookup"><span data-stu-id="958ae-114">Make sure that you install all the applicable hotfixes for all the products that you install as part of your deployment.</span></span> <span data-ttu-id="958ae-115">Pour plus d’informations, consultez les sources suivantes :</span><span class="sxs-lookup"><span data-stu-id="958ae-115">For more information, see the following sources:</span></span>  
  
    -   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="958ae-116">[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Aide en ligne</span><span class="sxs-lookup"><span data-stu-id="958ae-116"> [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Online Help</span></span>  
  
    -   <span data-ttu-id="958ae-117">Instructions d’Installation de BizTalk Server à [http://go.microsoft.com/fwlink/?LinkId=81041](http://go.microsoft.com/fwlink/?LinkId=81041).</span><span class="sxs-lookup"><span data-stu-id="958ae-117">BizTalk Server Installation Instructions at [http://go.microsoft.com/fwlink/?LinkId=81041](http://go.microsoft.com/fwlink/?LinkId=81041).</span></span>  
  
    -   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="958ae-118">[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Site Web à l’adresse [http://go.microsoft.com/fwlink/?linkid=48685](http://go.microsoft.com/fwlink/?linkid=48685).</span><span class="sxs-lookup"><span data-stu-id="958ae-118"> [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Web site at [http://go.microsoft.com/fwlink/?linkid=48685](http://go.microsoft.com/fwlink/?linkid=48685).</span></span>  
  
    -   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="958ae-119">Site Web du centre de téléchargement à [http://go.microsoft.com/fwlink/?linkid=48686](http://go.microsoft.com/fwlink/?linkid=48686).</span><span class="sxs-lookup"><span data-stu-id="958ae-119"> Download Center Web site at [http://go.microsoft.com/fwlink/?linkid=48686](http://go.microsoft.com/fwlink/?linkid=48686).</span></span>  
  
    -   [!INCLUDE[btsWinUpdate](../../includes/btswinupdate-md.md)]<span data-ttu-id="958ae-120">Site Web à l’adresse [http://go.microsoft.com/fwlink/?linkid=48687](http://go.microsoft.com/fwlink/?linkid=48687).</span><span class="sxs-lookup"><span data-stu-id="958ae-120"> Web site at [http://go.microsoft.com/fwlink/?linkid=48687](http://go.microsoft.com/fwlink/?linkid=48687).</span></span>  
  
-   <span data-ttu-id="958ae-121">Pour éviter les attaques de virus, installez la plateforme à partir d’un CD et déconnectez chaque serveur à partir d’Internet en débranchant les câbles et la désactivation de toutes les cartes réseau.</span><span class="sxs-lookup"><span data-stu-id="958ae-121">To avoid virus attacks, install the platform from a CD and disconnect each server from the Internet by unplugging any cables and disabling any network adapters.</span></span>  
  
-   <span data-ttu-id="958ae-122">Mettre en forme une nouvelle partition en utilisant le [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] système de fichiers NTFS.</span><span class="sxs-lookup"><span data-stu-id="958ae-122">Format a clean partition using the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] NTFS file system.</span></span>  
  
## <a name="active-directory"></a><span data-ttu-id="958ae-123">Active Directory</span><span class="sxs-lookup"><span data-stu-id="958ae-123">Active Directory</span></span>  
  
-   <span data-ttu-id="958ae-124">Créez un utilisateur de domaine appelé **Admin** et l’ajouter à la variable locale **administrateurs** groupe sur tous les ordinateurs de votre déploiement.</span><span class="sxs-lookup"><span data-stu-id="958ae-124">Create a domain user called **Admin** and add it to the local **Administrators** group on every computer in your deployment.</span></span> <span data-ttu-id="958ae-125">Au moment de l’installation, ouvrez une session les serveurs de déploiement à l’aide de ce compte de domaine.</span><span class="sxs-lookup"><span data-stu-id="958ae-125">At installation time, log on to the deployment servers using this domain account.</span></span>  
  
-   <span data-ttu-id="958ae-126">Ne pas configurer toutes les cartes réseau ou joindre des domaines pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="958ae-126">Do not configure any network adapters or join any domains at this time.</span></span> <span data-ttu-id="958ae-127">Ce guide décrit comment configurer ces paramètres ultérieurement lorsque vous commencez le processus de déploiement.</span><span class="sxs-lookup"><span data-stu-id="958ae-127">This guide describes how to configure these settings later when you begin the deployment process.</span></span>  
  
## <a name="internal-web-servers-mrsr-site"></a><span data-ttu-id="958ae-128">Serveurs Web interne (site MRSR)</span><span class="sxs-lookup"><span data-stu-id="958ae-128">Internal Web Servers (MRSR site)</span></span>  
  
-   <span data-ttu-id="958ae-129">Assurez-vous que les Internet Information Services (IIS) est installé uniquement sur le serveurs de site MRSR.</span><span class="sxs-lookup"><span data-stu-id="958ae-129">Make sure that Internet Information Services (IIS) is installed only on the MRSR site Servers.</span></span>  
  
-   <span data-ttu-id="958ae-130">Assurez-vous qu’Internet Information Services (IIS) n’est pas installé sur l’Internet Security and Acceleration (ISA) Server.</span><span class="sxs-lookup"><span data-stu-id="958ae-130">Make sure that Internet Information Services (IIS) is not installed on the Internet Security and Acceleration (ISA) Server.</span></span>  
  
-   <span data-ttu-id="958ae-131">Assurez-vous que le service Message Queuing (MSMQ) est installé uniquement sur le serveurs de site MRSR.</span><span class="sxs-lookup"><span data-stu-id="958ae-131">Make sure that the Message Queuing (MSMQ) service is installed only on the MRSR site Servers.</span></span> <span data-ttu-id="958ae-132">Si les serveurs de messagerie BizTalk seront également être utilisés en tant que les serveurs de site MRSR, n’installez pas MSMQ sur ces serveurs.</span><span class="sxs-lookup"><span data-stu-id="958ae-132">If the BizTalk Messaging servers will also be used as the MRSR site Servers, do not install MSMQ on those servers.</span></span>