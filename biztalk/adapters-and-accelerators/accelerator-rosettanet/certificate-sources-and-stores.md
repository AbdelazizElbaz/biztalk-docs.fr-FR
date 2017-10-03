---
title: Sources et les magasins de certificats | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, certificate storage
- importing certificates
- certificates, certificate sources
- certificates, importing
ms.assetid: 3e98fb56-4368-46f3-9329-c44fed11f4fb
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3ade897bb51850b4ef9dd6b530f5fc04c6b2601
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="certificate-sources-and-stores"></a><span data-ttu-id="ba5ca-102">Sources de certificat et de magasins</span><span class="sxs-lookup"><span data-stu-id="ba5ca-102">Certificate Sources and Stores</span></span>
<span data-ttu-id="ba5ca-103">Cette rubrique décrit où importer des certificats à partir d’et où stocker les certificats.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-103">This topic describes where to import certificates from, and where to store certificates.</span></span>  
  
## <a name="certificate-sources"></a><span data-ttu-id="ba5ca-104">Sources de certificat</span><span class="sxs-lookup"><span data-stu-id="ba5ca-104">Certificate Sources</span></span>  
 <span data-ttu-id="ba5ca-105">Pour importer des certificats à partir des fichiers suivants :</span><span class="sxs-lookup"><span data-stu-id="ba5ca-105">You import certificates from the following files:</span></span>  
  
-   <span data-ttu-id="ba5ca-106">Certificats privés à partir de fichiers .pfx ou .p12.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-106">Private certificates from .pfx or .p12 files.</span></span> <span data-ttu-id="ba5ca-107">Après avoir importé les certificats, stockez ces fichiers en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-107">After importing the certificates, store these files securely.</span></span> <span data-ttu-id="ba5ca-108">Si vous importez les certificats privés à l’aide de l’utilitaire CertWizard, vous pouvez définir le **/Exportable** basculer vers `False`, qui est le paramètre par défaut, afin que les certificats privés ne peuvent pas être exportées à partir du magasin dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-108">If you import the private certificates using the CertWizard utility, you can set the **/Exportable** switch to `False`, which is the default setting, so that the private certificates cannot be exported from the store into a file.</span></span> <span data-ttu-id="ba5ca-109">Si vous définissez la **/Exportable** basculer vers `True`, vous pouvez exporter ces certificats vers un fichier à partir des certificats [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="ba5ca-109">If you set the **/Exportable** switch to `True`, you can export these certificates to a file from the Certificates [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC).</span></span>  
  
-   <span data-ttu-id="ba5ca-110">Certificats publics des fichiers .cer ou .der.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-110">Public certificates from .cer or .der files.</span></span> <span data-ttu-id="ba5ca-111">Partenaires envoyer leurs certificats pour vous dans ces fichiers.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-111">Partners send their certificates to you in these files.</span></span>  
  
-   <span data-ttu-id="ba5ca-112">Certificats racine à partir de fichiers .cer ou .der.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-112">Root certificates from .cer or .der files.</span></span> <span data-ttu-id="ba5ca-113">Autorités de certification envoient leurs certificats racine à vous dans ces fichiers.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-113">Certification authorities send their root certificates to you in these files.</span></span>  
  
## <a name="certificate-storage"></a><span data-ttu-id="ba5ca-114">Magasin de certificats</span><span class="sxs-lookup"><span data-stu-id="ba5ca-114">Certificate Storage</span></span>  
 <span data-ttu-id="ba5ca-115">Pour importer des certificats dans une des deux magasins de certificats sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-115">You import certificates into one of two Certificates stores on the local computer.</span></span> <span data-ttu-id="ba5ca-116">Vous stockez les certificats publics dans le **certificats (ordinateur Local)** stocker.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-116">You store public certificates in the **Certificates (Local Computer)** store.</span></span> <span data-ttu-id="ba5ca-117">Vous pouvez ouvrir les nœuds de ce magasin en ouvrant le **certificats (ordinateur Local)** nœud dans le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] ([!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]) Console de gestion.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-117">You can open the nodes of this store by opening the **Certificates (Local Computer)** node in the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] ([!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]) Management Console.</span></span> <span data-ttu-id="ba5ca-118">Vous pouvez accéder à la **certificats (ordinateur Local)** stocker si vous disposez des autorisations administratives sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-118">You can access the **Certificates (Local Computer)** store if you have administrative permissions on the computer.</span></span> <span data-ttu-id="ba5ca-119">Stocker les certificats publics dans les dossiers suivants :</span><span class="sxs-lookup"><span data-stu-id="ba5ca-119">Store public certificates in the following folders:</span></span>  
  
-   <span data-ttu-id="ba5ca-120">Les certificats publics dans le dossier personnel d’accueil la **certificats (ordinateur Local)** stocker</span><span class="sxs-lookup"><span data-stu-id="ba5ca-120">Home public certificates in the Personal folder in the **Certificates (Local Computer)** store</span></span>  
  
-   <span data-ttu-id="ba5ca-121">Partenaire certificats publics dans le dossier d’autres personnes de la **certificats (ordinateur Local)** stocker</span><span class="sxs-lookup"><span data-stu-id="ba5ca-121">Partner public certificates in the Other People folder of the **Certificates (Local Computer)** store</span></span>  
  
-   <span data-ttu-id="ba5ca-122">Certificats d’autorités de certification dans le dossier de l’autorité de Certification racine de confiance de la **certificats (ordinateur Local)** stocker</span><span class="sxs-lookup"><span data-stu-id="ba5ca-122">Certificates from certification authorities in the Trusted Root Certification Authority folder of the **Certificates (Local Computer)** store</span></span>  
  
 <span data-ttu-id="ba5ca-123">Magasin de certificats privés dans le **certificats - utilisateur actuel** stocker.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-123">You store private certificates in the **Certificates - Current User** store.</span></span> <span data-ttu-id="ba5ca-124">Vous pouvez ouvrir les nœuds de ce magasin en ouvrant la Console de gestion à l’aide de la **runas** avec l’utilisateur du compte de service hôte.</span><span class="sxs-lookup"><span data-stu-id="ba5ca-124">You can open the nodes of this store by opening the Management Console using the **runas** command with the host service account user.</span></span> <span data-ttu-id="ba5ca-125">Pour plus d’informations, consultez [l’importation des certificats](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="ba5ca-125">For more information, see [Importing Certificates](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba5ca-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba5ca-126">See Also</span></span>  
 <span data-ttu-id="ba5ca-127">[L’importation de certificats à l’aide de l’utilitaire CertWizard](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-the-certwizard-utility.md) </span><span class="sxs-lookup"><span data-stu-id="ba5ca-127">[Importing Certificates Using the CertWizard Utility](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-the-certwizard-utility.md) </span></span>  
 <span data-ttu-id="ba5ca-128">[L’importation de certificats à l’aide de MMC](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-mmc.md) </span><span class="sxs-lookup"><span data-stu-id="ba5ca-128">[Importing Certificates Using MMC](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-mmc.md) </span></span>  
 [<span data-ttu-id="ba5ca-129">L’importation de certificats &#91; RN3 &#93;</span><span class="sxs-lookup"><span data-stu-id="ba5ca-129">Importing Certificates &#91;RN3&#93;</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/certificate-sources-and-stores.md)