---
title: Sources et les magasins de certificats | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- certificates, certificate storage
- importing certificates
- certificates, certificate sources
- certificates, importing
ms.assetid: 3e98fb56-4368-46f3-9329-c44fed11f4fb
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3ade897bb51850b4ef9dd6b530f5fc04c6b2601
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="certificate-sources-and-stores"></a>Sources de certificat et de magasins
Cette rubrique décrit où importer des certificats à partir d’et où stocker les certificats.  
  
## <a name="certificate-sources"></a>Sources de certificat  
 Pour importer des certificats à partir des fichiers suivants :  
  
-   Certificats privés à partir de fichiers .pfx ou .p12. Après avoir importé les certificats, stockez ces fichiers en toute sécurité. Si vous importez les certificats privés à l’aide de l’utilitaire CertWizard, vous pouvez définir le **/Exportable** basculer vers `False`, qui est le paramètre par défaut, afin que les certificats privés ne peuvent pas être exportées à partir du magasin dans un fichier. Si vous définissez la **/Exportable** basculer vers `True`, vous pouvez exporter ces certificats vers un fichier à partir des certificats [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC).  
  
-   Certificats publics des fichiers .cer ou .der. Partenaires envoyer leurs certificats pour vous dans ces fichiers.  
  
-   Certificats racine à partir de fichiers .cer ou .der. Autorités de certification envoient leurs certificats racine à vous dans ces fichiers.  
  
## <a name="certificate-storage"></a>Magasin de certificats  
 Pour importer des certificats dans une des deux magasins de certificats sur l’ordinateur local. Vous stockez les certificats publics dans le **certificats (ordinateur Local)** stocker. Vous pouvez ouvrir les nœuds de ce magasin en ouvrant le **certificats (ordinateur Local)** nœud dans le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] ([!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]) Console de gestion. Vous pouvez accéder à la **certificats (ordinateur Local)** stocker si vous disposez des autorisations administratives sur l’ordinateur. Stocker les certificats publics dans les dossiers suivants :  
  
-   Les certificats publics dans le dossier personnel d’accueil la **certificats (ordinateur Local)** stocker  
  
-   Partenaire certificats publics dans le dossier d’autres personnes de la **certificats (ordinateur Local)** stocker  
  
-   Certificats d’autorités de certification dans le dossier de l’autorité de Certification racine de confiance de la **certificats (ordinateur Local)** stocker  
  
 Magasin de certificats privés dans le **certificats - utilisateur actuel** stocker. Vous pouvez ouvrir les nœuds de ce magasin en ouvrant la Console de gestion à l’aide de la **runas** avec l’utilisateur du compte de service hôte. Pour plus d’informations, consultez [l’importation des certificats](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates.md).  
  
## <a name="see-also"></a>Voir aussi  
 [L’importation de certificats à l’aide de l’utilitaire CertWizard](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-the-certwizard-utility.md)   
 [L’importation de certificats à l’aide de MMC](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-mmc.md)   
 [L’importation de certificats &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/certificate-sources-and-stores.md)