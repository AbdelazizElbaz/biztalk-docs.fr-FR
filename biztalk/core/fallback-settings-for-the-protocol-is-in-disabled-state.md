---
title: "Paramètres de secours pour le protocole est dans un état désactivé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f14a5e46-1028-4250-af7b-8137fa927d7e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9060dbe2bf3644310d862d4949d2cf944269105d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fallback-settings-for-the-protocol-is-in-disabled-state"></a><span data-ttu-id="c75f8-102">Les paramètres de secours du protocole sont désactivés</span><span class="sxs-lookup"><span data-stu-id="c75f8-102">Fallback Settings for the Protocol is in Disabled state</span></span>
## <a name="details"></a><span data-ttu-id="c75f8-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c75f8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c75f8-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c75f8-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="c75f8-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c75f8-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="c75f8-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c75f8-106">Event ID</span></span>|-|  
|<span data-ttu-id="c75f8-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c75f8-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c75f8-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="c75f8-108"> EDI</span></span>|  
|<span data-ttu-id="c75f8-109">Composant</span><span class="sxs-lookup"><span data-stu-id="c75f8-109">Component</span></span>|<span data-ttu-id="c75f8-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="c75f8-110">EDI Engine</span></span>|  
|<span data-ttu-id="c75f8-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c75f8-111">Symbolic Name</span></span>|<span data-ttu-id="c75f8-112">AgreementResolutionFallbackSettingsDisabled</span><span class="sxs-lookup"><span data-stu-id="c75f8-112">AgreementResolutionFallbackSettingsDisabled</span></span>|  
|<span data-ttu-id="c75f8-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c75f8-113">Message Text</span></span>|<span data-ttu-id="c75f8-114">Les paramètres de secours du protocole {0} sont désactivés.</span><span class="sxs-lookup"><span data-stu-id="c75f8-114">Fallback Settings for the {0} Protocol is in Disabled state.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c75f8-115">Explication</span><span class="sxs-lookup"><span data-stu-id="c75f8-115">Explanation</span></span>  
 <span data-ttu-id="c75f8-116">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server a réussi à trouver une correspondance pour un accord et a été redirigé vers les paramètres de secours, mais que ceux-ci ont été désactivés pour le protocole spécifié.</span><span class="sxs-lookup"><span data-stu-id="c75f8-116">This Error/Warning/Information event indicates BizTalk Server was able to resolve to an agreement and has been redirected to Fallback settings and found that the fallback settings were in disabled state for the particular protocol.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c75f8-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c75f8-117">User Action</span></span>  
 <span data-ttu-id="c75f8-118">Pour résoudre cette erreur, activez les paramètres de secours pour le protocole spécifié.</span><span class="sxs-lookup"><span data-stu-id="c75f8-118">To resolve this error, please enable the fallback settings for the particular protocol.</span></span>