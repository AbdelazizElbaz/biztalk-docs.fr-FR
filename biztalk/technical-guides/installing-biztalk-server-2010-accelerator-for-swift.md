---
title: Installation de BizTalk Server 2010 Accelerator pour SWIFT | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78d996ce-40ea-4d01-b083-c55ccace4b26
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8dcec7f25211fac8c99a89ce7ce85840f457971a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installing-biztalk-server-2010-accelerator-for-swift"></a><span data-ttu-id="52f12-102">Installation de BizTalk Server 2010 Accelerator pour SWIFT</span><span class="sxs-lookup"><span data-stu-id="52f12-102">Installing BizTalk Server 2010 Accelerator for SWIFT</span></span>
<span data-ttu-id="52f12-103">![Logo](../technical-guides/media/bts-10-installaccelerator-logo.gif "BTS_10_InstallAccelerator_Logo")</span><span class="sxs-lookup"><span data-stu-id="52f12-103">![Logo](../technical-guides/media/bts-10-installaccelerator-logo.gif "BTS_10_InstallAccelerator_Logo")</span></span>  
  
 <span data-ttu-id="52f12-104">Article de la technique de BizTalk</span><span class="sxs-lookup"><span data-stu-id="52f12-104">BizTalk Technical Article</span></span>  
  
 <span data-ttu-id="52f12-105">**Installation de BizTalk Server 2010 Accelerator pour SWIFT**</span><span class="sxs-lookup"><span data-stu-id="52f12-105">**Installing BizTalk Server 2010 Accelerator for SWIFT**</span></span>  
  
 <span data-ttu-id="52f12-106">**Enregistreur :** Maria Quian, Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="52f12-106">**Writer:** Maria Quian, Microsoft Corporation</span></span>  
  
 <span data-ttu-id="52f12-107">**Réviseurs techniques :** Andres Naranjo, Mandi Ohlinger</span><span class="sxs-lookup"><span data-stu-id="52f12-107">**Technical Reviewers:** Andres Naranjo, Mandi Ohlinger</span></span>  
  
 <span data-ttu-id="52f12-108">**Date de publication :** juin 2012</span><span class="sxs-lookup"><span data-stu-id="52f12-108">**Published:** June 2012</span></span>  
  
 <span data-ttu-id="52f12-109">**S’applique à :** BizTalk Server 2010 Accelerator pour SWIFT</span><span class="sxs-lookup"><span data-stu-id="52f12-109">**Applies To:** BizTalk Server 2010 Accelerator for SWIFT</span></span>  
  
 <span data-ttu-id="52f12-110">**Résumé :** la base de réussite de l’installation de Microsoft BizTalk Server 2010 Accelerator pour SWIFT (A4SWIFT) est de comprendre les fonctionnalités d’A4SWIFT et les composants de BizTalk dont dépend chaque fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="52f12-110">**Summary:** The foundation for a successful installation of Microsoft BizTalk Server 2010 Accelerator for SWIFT (A4SWIFT) is an understanding of the A4SWIFT features and the BizTalk components on which each feature depends.</span></span> <span data-ttu-id="52f12-111">Chaque fonctionnalité A4SWIFT dépend des autres composants BizTalk correctement configurés.</span><span class="sxs-lookup"><span data-stu-id="52f12-111">Each A4SWIFT feature depends on other properly configured BizTalk components.</span></span> <span data-ttu-id="52f12-112">Autres considérations qui affectent la création d’un environnement d’A4SWIFT incluent une infrastructure réseau existante et un environnement BizTalk Server déjà configuré.</span><span class="sxs-lookup"><span data-stu-id="52f12-112">Other considerations that affect building an A4SWIFT environment include an existing network infrastructure and an already configured BizTalk Server environment.</span></span> <span data-ttu-id="52f12-113">Ce document sera voir et utiliser la documentation existante pour la création d’environnements BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="52f12-113">This document will refer and use the existing documentation for building BizTalk Server environments.</span></span> <span data-ttu-id="52f12-114">A4SWIFT hérite de toutes les conditions matérielles et logicielles requises pour BizTalk Server 2010.</span><span class="sxs-lookup"><span data-stu-id="52f12-114">A4SWIFT inherits all software and hardware requirements for BizTalk Server 2010.</span></span>  
  
 <span data-ttu-id="52f12-115">Un guide d’installation est disponible pour chaque composant associé A4SWIFT mais pas un seul document compilé qui présente les étapes d’installation/de configuration.</span><span class="sxs-lookup"><span data-stu-id="52f12-115">An installation guide is available for each A4SWIFT related component but not a single compiled document that elaborates on the installation/configuration steps.</span></span> <span data-ttu-id="52f12-116">Ce document sera les rassembler et identifier certains des problèmes courants rencontrés pendant l’installation et de configuration.</span><span class="sxs-lookup"><span data-stu-id="52f12-116">This document will bring them together and identify some of the common issues encountered during installation and configuration.</span></span>  
  
 <span data-ttu-id="52f12-117">Pour consulter le document, téléchargez le [l’installation de BizTalk Server 2010 Accelerator pour SWIFT](http://go.microsoft.com/fwlink/?LinkId=255118) document Word.</span><span class="sxs-lookup"><span data-stu-id="52f12-117">To review the document, please download the [Installing BizTalk Server 2010 Accelerator for SWIFT](http://go.microsoft.com/fwlink/?LinkId=255118) Word document.</span></span>