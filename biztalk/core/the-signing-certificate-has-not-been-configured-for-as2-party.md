---
title: "Le certificat de signature n’a pas été configuré pour le tiers AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82928a39-3acf-447b-a0e8-f7c25b6f38dc
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61802b5e86319d0fe73f11c22249b72af1441b5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-signing-certificate-has-not-been-configured-for-as2-party"></a><span data-ttu-id="a6bcf-102">Le certificat de signature n'a pas été configurée pour le tiers AS2</span><span class="sxs-lookup"><span data-stu-id="a6bcf-102">The Signing Certificate has not been configured for AS2 party</span></span>
## <a name="details"></a><span data-ttu-id="a6bcf-103">Détails</span><span class="sxs-lookup"><span data-stu-id="a6bcf-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a6bcf-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a6bcf-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="a6bcf-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a6bcf-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="a6bcf-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a6bcf-106">Event ID</span></span>|-|  
|<span data-ttu-id="a6bcf-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a6bcf-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a6bcf-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="a6bcf-108"> EDI</span></span>|  
|<span data-ttu-id="a6bcf-109">Composant</span><span class="sxs-lookup"><span data-stu-id="a6bcf-109">Component</span></span>|<span data-ttu-id="a6bcf-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="a6bcf-110">AS2 Engine</span></span>|  
|<span data-ttu-id="a6bcf-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a6bcf-111">Symbolic Name</span></span>|<span data-ttu-id="a6bcf-112">SigningCertNotConfiguredError</span><span class="sxs-lookup"><span data-stu-id="a6bcf-112">SigningCertNotConfiguredError</span></span>|  
|<span data-ttu-id="a6bcf-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a6bcf-113">Message Text</span></span>|<span data-ttu-id="a6bcf-114">Le certificat de signature n'a pas été configuré pour le tiers AS2.</span><span class="sxs-lookup"><span data-stu-id="a6bcf-114">The Signing Certificate has not been configured for AS2 party.</span></span>  <span data-ttu-id="a6bcf-115">AS2-à partir de : {0} AS2-pour : {1}</span><span class="sxs-lookup"><span data-stu-id="a6bcf-115">AS2-From: {0} AS2-To: {1}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a6bcf-116">Explication</span><span class="sxs-lookup"><span data-stu-id="a6bcf-116">Explanation</span></span>  
 <span data-ttu-id="a6bcf-117">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu traiter le message sortant car le certificat de signature n'était pas configuré pour le groupe.</span><span class="sxs-lookup"><span data-stu-id="a6bcf-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing message because the signing certificate was not configured for the group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a6bcf-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a6bcf-118">User Action</span></span>  
 <span data-ttu-id="a6bcf-119">Pour résoudre cette erreur, configurez le certificat de signature en effectuant l'une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="a6bcf-119">To resolve this error, configure signing certificate by doing the following:</span></span>  
  
1.  <span data-ttu-id="a6bcf-120">Ouvrez la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a6bcf-120">Open the BizTalk Server Administration Console.</span></span>  
  
2.  <span data-ttu-id="a6bcf-121">Accédez au nœud Groupe, puis cliquez sur le nœud Certificat.</span><span class="sxs-lookup"><span data-stu-id="a6bcf-121">Move to the Group node, and click the Certificate node.</span></span>  
  
3.  <span data-ttu-id="a6bcf-122">Entrez le nom commun et l'empreinte du certificat.</span><span class="sxs-lookup"><span data-stu-id="a6bcf-122">Enter the common name and thumbprint of the certificate.</span></span>