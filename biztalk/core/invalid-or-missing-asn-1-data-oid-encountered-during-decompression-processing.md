---
title: "Non valide ou manquante OID de données ASN.1 rencontré lors du traitement de la décompression | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 243062ae-19df-4989-b8d9-109e789f8335
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da26bfb0ff76ec8b78e6572dba14631ff84fd9f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-or-missing-asn1-data-oid-encountered-during-decompression-processing"></a><span data-ttu-id="68312-102">Non valide ou manquante OID de données ASN.1 rencontré lors du traitement de la décompression</span><span class="sxs-lookup"><span data-stu-id="68312-102">Invalid or missing ASN.1 Data OID encountered during decompression processing</span></span>
## <a name="details"></a><span data-ttu-id="68312-103">Détails</span><span class="sxs-lookup"><span data-stu-id="68312-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="68312-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="68312-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="68312-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="68312-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="68312-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="68312-106">Event ID</span></span>|-|  
|<span data-ttu-id="68312-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="68312-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="68312-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="68312-108"> EDI</span></span>|  
|<span data-ttu-id="68312-109">Composant</span><span class="sxs-lookup"><span data-stu-id="68312-109">Component</span></span>|<span data-ttu-id="68312-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="68312-110">AS2 Engine</span></span>|  
|<span data-ttu-id="68312-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="68312-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="68312-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="68312-112">Message Text</span></span>|<span data-ttu-id="68312-113">Non valide ou manquante OID de données ASN.1 rencontré lors du traitement de la décompression</span><span class="sxs-lookup"><span data-stu-id="68312-113">Invalid or missing ASN.1 Data OID encountered during decompression processing</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="68312-114">Explication</span><span class="sxs-lookup"><span data-stu-id="68312-114">Explanation</span></span>  
 <span data-ttu-id="68312-115">Cette erreur fait référence à la structure ASN.1 des données compressées.</span><span class="sxs-lookup"><span data-stu-id="68312-115">This error refers to the ASN.1 structure of the compressed data.</span></span> <span data-ttu-id="68312-116">Elle indique que l'expéditeur des données compressées les a structurées de manière incorrecte ou qu'il y a eu falsification (modification non autorisée) du message.</span><span class="sxs-lookup"><span data-stu-id="68312-116">The error indicates the sender of the compressed data either structured the compressed data incorrectly or there was tampering (unauthorized change) of the message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="68312-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="68312-117">User Action</span></span>  
 <span data-ttu-id="68312-118">Passez en revue la structure des données compressées et recherchez toute falsification du message.</span><span class="sxs-lookup"><span data-stu-id="68312-118">Review the structure of the compressed data and check for tampering with the message.</span></span>