---
title: "Single Sign-On : Événement 11063 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c84f91de-221d-43c4-8d23-3d1b7fd29cf7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82581dafd58a07ed217a5e9062aa91057a84aed3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11063"></a><span data-ttu-id="02a1b-102">Single Sign-On : Événement 11063</span><span class="sxs-lookup"><span data-stu-id="02a1b-102">Single Sign-On: Event 11063</span></span>
## <a name="details"></a><span data-ttu-id="02a1b-103">Détails</span><span class="sxs-lookup"><span data-stu-id="02a1b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="02a1b-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="02a1b-104">Product Name</span></span>|<span data-ttu-id="02a1b-105">Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="02a1b-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="02a1b-106">Version du produit</span><span class="sxs-lookup"><span data-stu-id="02a1b-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="02a1b-107">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="02a1b-107">Event ID</span></span>|<span data-ttu-id="02a1b-108">11063</span><span class="sxs-lookup"><span data-stu-id="02a1b-108">11063</span></span>|  
|<span data-ttu-id="02a1b-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="02a1b-109">Event Source</span></span>|<span data-ttu-id="02a1b-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="02a1b-110">ENTSSO</span></span>|  
|<span data-ttu-id="02a1b-111">Composant</span><span class="sxs-lookup"><span data-stu-id="02a1b-111">Component</span></span>|<span data-ttu-id="02a1b-112">Néant</span><span class="sxs-lookup"><span data-stu-id="02a1b-112">N/A</span></span>|  
|<span data-ttu-id="02a1b-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="02a1b-113">Symbolic Name</span></span>|<span data-ttu-id="02a1b-114">SSO_ERROR_PS_MIIS_CALLBACK_ACCESS_DENIED</span><span class="sxs-lookup"><span data-stu-id="02a1b-114">SSO_ERROR_PS_MIIS_CALLBACK_ACCESS_DENIED</span></span>|  
|<span data-ttu-id="02a1b-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="02a1b-115">Message Text</span></span>|<span data-ttu-id="02a1b-116">Accès au serveur de synchronisation des mots de passe (pour MIIS) refusé.%r</span><span class="sxs-lookup"><span data-stu-id="02a1b-116">Password sync server (for MIIS) access denied.%r</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="02a1b-117">Explication</span><span class="sxs-lookup"><span data-stu-id="02a1b-117">Explanation</span></span>  
 <span data-ttu-id="02a1b-118">L'accès au rappel MIIS a été refusé.</span><span class="sxs-lookup"><span data-stu-id="02a1b-118">MIIS Callback access has been denied.</span></span> <span data-ttu-id="02a1b-119">La cause la plus probable de cette erreur est l'échec de l'utilisation de l'authentification Kerberos entre le système ENTSSO et MIIS.</span><span class="sxs-lookup"><span data-stu-id="02a1b-119">The most likely cause of this error is failure to use the Kerberos authentication between the ENTSSO system and MIIS.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="02a1b-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="02a1b-120">User Action</span></span>  
 <span data-ttu-id="02a1b-121">Confirmez que votre système ENTSSO utilise l'authentification Kerberos.</span><span class="sxs-lookup"><span data-stu-id="02a1b-121">Confirm that your ENTSSO system is using Kerberos authentication.</span></span> <span data-ttu-id="02a1b-122">Pour plus d’informations, consultez [recommandations de sécurité pour l’authentification unique](../core/sso-security-recommendations.md).</span><span class="sxs-lookup"><span data-stu-id="02a1b-122">For more information, see [SSO Security Recommendations](../core/sso-security-recommendations.md).</span></span>