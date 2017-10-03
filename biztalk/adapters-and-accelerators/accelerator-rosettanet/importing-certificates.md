---
title: "L’importation de certificats | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing certificates
- certificates, importing
ms.assetid: c2576f89-b5de-4250-9c54-74c8a218bb39
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c78773d6eb1fc7e51ca80afadfd282d54def80b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importing-certificates"></a>L’importation de certificats
Cette section décrit comment importer des certificats, notamment où les importer à partir de, où les stocker et quels outils pour utiliser pour les importer.  
  
 Il existe deux façons d’importer des certificats. Vous pouvez utiliser l’outil CertWizard ou le composant logiciel enfichable Certificats pour [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC).  
  
-   CertWizard est un Assistant de ligne de commande qui configure l’utilisation du certificat basé sur les paramètres des commutateurs. Cet outil est disponible dans le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] dossier SDK.  
  
-   Avec le composant logiciel enfichable Certificats dans la console MMC, vous pouvez importer un certificat dans le magasin de certificats. Toutefois, ce processus manuel nécessite la configuration séparée de l’utilisation du certificat.  
  
    > [!IMPORTANT]
    >  Pour importer ou travailler avec les certificats privés dans MMC, l’utilisateur qui a ouvert une session doit avoir l’identité de l’utilisateur des hôtes BizTalk. Si non, vous devez exécuter le **runas** avec le commutateur de l’utilisateur et le compte de service d’hôte pour démarrer la console MMC Certificats, par exemple, **runas /user:hostsvc mmc**. En exécutant cette commande, vous supposez l’identité de l’utilisateur des hôtes BizTalk (BizTalkServerApplication et BizTalkServerIsolatedHost).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Sources de certificat et de magasins](../../adapters-and-accelerators/accelerator-rosettanet/certificate-sources-and-stores.md)  
  
-   [L’importation de certificats à l’aide de l’utilitaire CertWizard](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-the-certwizard-utility.md)  
  
-   [L’importation de certificats à l’aide de MMC](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-mmc.md)