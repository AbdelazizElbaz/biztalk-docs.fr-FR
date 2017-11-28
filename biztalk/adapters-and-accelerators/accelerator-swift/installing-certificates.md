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
# <a name="installing-certificates"></a><span data-ttu-id="b32e9-102">Installation de certificats</span><span class="sxs-lookup"><span data-stu-id="b32e9-102">Installing Certificates</span></span>
<span data-ttu-id="b32e9-103">Pour envoyer, réparer ou envoyer des messages, vous devez disposer les certificats appropriés installés.</span><span class="sxs-lookup"><span data-stu-id="b32e9-103">To send, repair, or submit messages, you must have the proper certificates installed.</span></span> <span data-ttu-id="b32e9-104">Cette rubrique décrit comment ajouter des certificats.</span><span class="sxs-lookup"><span data-stu-id="b32e9-104">This topic describes how to add certificates.</span></span> <span data-ttu-id="b32e9-105">Dans un environnement de production, consultez votre service informatique pour les certificats.</span><span class="sxs-lookup"><span data-stu-id="b32e9-105">In a production environment, see your IT department for certificates.</span></span>  
  
 <span data-ttu-id="b32e9-106">**Résumé**</span><span class="sxs-lookup"><span data-stu-id="b32e9-106">**Summary**</span></span>  
  
 <span data-ttu-id="b32e9-107">Cette section fournit des instructions sur la façon de créer et stocker les certificats suivants :</span><span class="sxs-lookup"><span data-stu-id="b32e9-107">This section provides instructions on how to create and store the following certificates:</span></span>  
  
-   <span data-ttu-id="b32e9-108">Magasin de certificats pour chaque Message Repair et rôles de la nouvelle soumission dans le dossier personnel des certificats - utilisateur actuel sur chaque ordinateur client</span><span class="sxs-lookup"><span data-stu-id="b32e9-108">Certificates for each of the Message Repair and New Submission roles in the Personal folder of the Certificates - Current User store on each client computer</span></span>  
  
-   <span data-ttu-id="b32e9-109">Magasin de certificats pour chaque Message Repair et rôles de la nouvelle soumission dans le dossier d’autres personnes de certificats (ordinateur Local) sur chaque ordinateur du serveur d’orchestration BizTalk</span><span class="sxs-lookup"><span data-stu-id="b32e9-109">Certificates for each of the Message Repair and New Submission roles in the Other People folder of the Certificates (Local Computer) store on each BizTalk orchestration server computer</span></span>  
  
-   <span data-ttu-id="b32e9-110">Certificat d’autorité de certification dans le dossier autorités de Certification racines de confiance dans le magasin de certificats (ordinateur Local) sur chaque ordinateur client</span><span class="sxs-lookup"><span data-stu-id="b32e9-110">Certification Authority's certificate into the Trusted Root Certification Authorities folder in the Certificates (Local Computer) store on each client computer</span></span>  
  
 <span data-ttu-id="b32e9-111">Si vous avez déployé [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] sur un ordinateur unique et également un serveur de certificats installé sur le même ordinateur, vous devez exclure le serveur de certificats les chemins d’accès gérés pour [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="b32e9-111">If you have deployed [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] on a single computer, and also have a certificate server installed on the same computer, you need to exclude the certificate server from the managed paths for [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] SharePoint Server.</span></span>  
  
 <span data-ttu-id="b32e9-112">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="b32e9-112">This section contains:</span></span>  
  
-   [<span data-ttu-id="b32e9-113">Ajout de certificats dans le magasin de certificats sur le Client</span><span class="sxs-lookup"><span data-stu-id="b32e9-113">Adding Certificates to the Certificates Store on the Client</span></span>](../../adapters-and-accelerators/accelerator-swift/adding-certificates-to-the-certificates-store-on-the-client.md)  
  
-   [<span data-ttu-id="b32e9-114">Ajout de certificats dans le magasin de certificats sur le serveur</span><span class="sxs-lookup"><span data-stu-id="b32e9-114">Adding Certificates to the Certificates Store on the Server</span></span>](../../adapters-and-accelerators/accelerator-swift/adding-certificates-to-the-certificates-store-on-the-server.md)  
  
-   [<span data-ttu-id="b32e9-115">À l’exclusion de CertSrv à partir de chemins d’accès gérés sur un déploiement sur un seul ordinateur</span><span class="sxs-lookup"><span data-stu-id="b32e9-115">Excluding CertSrv from Managed Paths on a Single-Computer Deployment</span></span>](../../adapters-and-accelerators/accelerator-swift/excluding-certsrv-from-managed-paths-on-a-single-computer-deployment.md)