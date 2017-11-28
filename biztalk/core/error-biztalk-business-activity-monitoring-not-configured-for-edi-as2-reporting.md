---
title: "BizTalk Business Activity Monitoring n’a pas été configuré pour le rapport d’état EDI-AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f46c1c8-2771-4b16-8fb1-71952792ac4a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e84301e55cd6fbdcb74467758c7e338e61b727f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-business-activity-monitoring-has-not-been-configured-for-edi-as2-status-reporting"></a><span data-ttu-id="9bfd9-102">BizTalk Business Activity Monitoring n’a pas été configuré pour le rapport d’état EDI-AS2</span><span class="sxs-lookup"><span data-stu-id="9bfd9-102">BizTalk Business Activity Monitoring has not been configured for EDI-AS2 status reporting</span></span>
## <a name="details"></a><span data-ttu-id="9bfd9-103">Détails</span><span class="sxs-lookup"><span data-stu-id="9bfd9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9bfd9-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="9bfd9-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="9bfd9-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="9bfd9-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="9bfd9-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="9bfd9-106">Event ID</span></span>|-|  
|<span data-ttu-id="9bfd9-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="9bfd9-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9bfd9-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="9bfd9-108"> EDI</span></span>|  
|<span data-ttu-id="9bfd9-109">Composant</span><span class="sxs-lookup"><span data-stu-id="9bfd9-109">Component</span></span>|<span data-ttu-id="9bfd9-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="9bfd9-110">AS2 Engine</span></span>|  
|<span data-ttu-id="9bfd9-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="9bfd9-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="9bfd9-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="9bfd9-112">Message Text</span></span>|<span data-ttu-id="9bfd9-113">BizTalk Business Activity Monitoring n’a pas été configuré pour le rapport d’état EDI/AS2.</span><span class="sxs-lookup"><span data-stu-id="9bfd9-113">BizTalk Business Activity Monitoring has not been configured for EDI/AS2 status reporting.</span></span> <span data-ttu-id="9bfd9-114">La fonction de création de rapports d'état va donc être désactivée.</span><span class="sxs-lookup"><span data-stu-id="9bfd9-114">Hence status reporting feature will be disabled.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9bfd9-115">Explication</span><span class="sxs-lookup"><span data-stu-id="9bfd9-115">Explanation</span></span>  
 <span data-ttu-id="9bfd9-116">Cet avertissement, erreur ou information indique que la création de rapports d'état EDI/AS2 n'est pas activée car l'analyse BAM (Business Activity Monitoring) n'a pas été configurée via l'Assistant Configuration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="9bfd9-116">This Error/Warning/Information event indicates that EDI/AS2 status reporting is not enabled because Business Activity Monitoring (BAM) has not been configured through the BizTalk Configuration Wizard.</span></span> <span data-ttu-id="9bfd9-117">L'infrastructure BAM est une condition préalable à la création de rapports d'état EDI/AS2.</span><span class="sxs-lookup"><span data-stu-id="9bfd9-117">The BAM infrastructure is a prerequisite for EDI/AS2 status reporting.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9bfd9-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="9bfd9-118">User Action</span></span>  
 <span data-ttu-id="9bfd9-119">Pour résoudre cette erreur, exécutez l'Assistant Configuration de BizTalk et configurez l'analyse BAM (Business Activity Monitoring).</span><span class="sxs-lookup"><span data-stu-id="9bfd9-119">To resolve this error, run the BizTalk Configuration Wizard and configure Business Activity Monitoring.</span></span>