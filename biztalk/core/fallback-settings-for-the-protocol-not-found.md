---
title: "Paramètres de secours pour le protocole introuvable | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d93e5db1-16a3-4796-8fa2-fef934508034
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5b3f8ea35f4f29859f5156ff254137ea7a8f8db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fallback-settings-for-the-protocol-not-found"></a><span data-ttu-id="b7f75-102">Les paramètres de secours pour le protocole sont introuvables</span><span class="sxs-lookup"><span data-stu-id="b7f75-102">Fallback Settings for the Protocol not found</span></span>
## <a name="details"></a><span data-ttu-id="b7f75-103">Détails</span><span class="sxs-lookup"><span data-stu-id="b7f75-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b7f75-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="b7f75-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="b7f75-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="b7f75-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="b7f75-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="b7f75-106">Event ID</span></span>|-|  
|<span data-ttu-id="b7f75-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="b7f75-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b7f75-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="b7f75-108"> EDI</span></span>|  
|<span data-ttu-id="b7f75-109">Composant</span><span class="sxs-lookup"><span data-stu-id="b7f75-109">Component</span></span>|<span data-ttu-id="b7f75-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="b7f75-110">EDI Engine</span></span>|  
|<span data-ttu-id="b7f75-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="b7f75-111">Symbolic Name</span></span>|<span data-ttu-id="b7f75-112">AgreementResolutionFallbackSettingsNotFound</span><span class="sxs-lookup"><span data-stu-id="b7f75-112">AgreementResolutionFallbackSettingsNotFound</span></span>|  
|<span data-ttu-id="b7f75-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="b7f75-113">Message Text</span></span>|<span data-ttu-id="b7f75-114">Les paramètres de secours pour le protocole {0} sont introuvables.</span><span class="sxs-lookup"><span data-stu-id="b7f75-114">Fallback Settings for the {0} Protocol not found.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b7f75-115">Explication</span><span class="sxs-lookup"><span data-stu-id="b7f75-115">Explanation</span></span>  
 <span data-ttu-id="b7f75-116">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server a réussi à trouver une correspondance pour un accord et a été redirigé vers les paramètres de secours. Toutefois, les paramètres de secours n'étaient pas présents pour le protocole spécifié.</span><span class="sxs-lookup"><span data-stu-id="b7f75-116">This Error/Warning/Information event indicates BizTalk Server was able to resolve to an agreement and has been redirected to Fallback settings and found that the fallback settings were not there for the particular protocol.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b7f75-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="b7f75-117">User Action</span></span>  
 <span data-ttu-id="b7f75-118">Pour résoudre cette erreur, configurez les paramètres de secours pour le protocole spécifié.</span><span class="sxs-lookup"><span data-stu-id="b7f75-118">To resolve this error, please configure the fallback settings for the particular protocol.</span></span>