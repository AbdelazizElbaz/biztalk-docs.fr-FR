---
title: Installation de certificats | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, installing
- installing, certificates
ms.assetid: 7525f771-623c-420f-99ca-c834e819829d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5ded26548303dfe9c9a095c24396b4e2683ca4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installing-certificates"></a>Installation de certificats
Pour envoyer, réparer ou envoyer des messages, vous devez disposer les certificats appropriés installés. Cette rubrique décrit comment ajouter des certificats. Dans un environnement de production, consultez votre service informatique pour les certificats.  
  
 **Résumé**  
  
 Cette section fournit des instructions sur la façon de créer et stocker les certificats suivants :  
  
-   Magasin de certificats pour chaque Message Repair et rôles de la nouvelle soumission dans le dossier personnel des certificats - utilisateur actuel sur chaque ordinateur client  
  
-   Magasin de certificats pour chaque Message Repair et rôles de la nouvelle soumission dans le dossier d’autres personnes de certificats (ordinateur Local) sur chaque ordinateur du serveur d’orchestration BizTalk  
  
-   Certificat d’autorité de certification dans le dossier autorités de Certification racines de confiance dans le magasin de certificats (ordinateur Local) sur chaque ordinateur client  
  
 Si vous avez déployé [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] sur un ordinateur unique et également un serveur de certificats installé sur le même ordinateur, vous devez exclure le serveur de certificats les chemins d’accès gérés pour [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] SharePoint Server.  
  
 Contenu de cette section :  
  
-   [Ajout de certificats dans le magasin de certificats sur le Client](../../adapters-and-accelerators/accelerator-swift/adding-certificates-to-the-certificates-store-on-the-client.md)  
  
-   [Ajout de certificats dans le magasin de certificats sur le serveur](../../adapters-and-accelerators/accelerator-swift/adding-certificates-to-the-certificates-store-on-the-server.md)  
  
-   [À l’exclusion de CertSrv à partir de chemins d’accès gérés sur un déploiement sur un seul ordinateur](../../adapters-and-accelerators/accelerator-swift/excluding-certsrv-from-managed-paths-on-a-single-computer-deployment.md)