---
title: Gestion des Certificates1 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing certificates
- certificates, managing
ms.assetid: ffa60e2b-c131-4a49-ad1e-6c8a7271b05c
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3d74342d15d65082b6d94f252023c3df1d601dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-certificates"></a><span data-ttu-id="a298f-102">La gestion des certificats</span><span class="sxs-lookup"><span data-stu-id="a298f-102">Managing Certificates</span></span>
<span data-ttu-id="a298f-103">Les communications sécurisées dans RosettaNet requièrent l'utilisation de certificats.</span><span class="sxs-lookup"><span data-stu-id="a298f-103">Secure communications in RosettaNet require using certificates.</span></span> [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="a298f-104">® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] utilise des certificats pour chiffrer les messages sortants, signer des messages sortants, déchiffrer les messages entrants et vérifier la signature dans les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="a298f-104">® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] uses certificates to encrypt outgoing messages, sign outgoing messages, decrypt incoming messages, and verify the signature in incoming messages.</span></span>  
  
 <span data-ttu-id="a298f-105">Pour utiliser des certificats, vous devez effectuer une partie ou l'ensemble des étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="a298f-105">To use certificates, you must perform some or all of the following steps:</span></span>  
  
-   <span data-ttu-id="a298f-106">Importer des certificats dans le magasin de certificats du serveur</span><span class="sxs-lookup"><span data-stu-id="a298f-106">Import certificates into the certificates store for the server</span></span>  
  
-   <span data-ttu-id="a298f-107">Configurer l'utilisation de certificats dans les messages</span><span class="sxs-lookup"><span data-stu-id="a298f-107">Configure the use of certificates in messages</span></span>  
  
-   <span data-ttu-id="a298f-108">Exporter des certificats vers des partenaires</span><span class="sxs-lookup"><span data-stu-id="a298f-108">Export certificates to partners</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a298f-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a298f-109">In This Section</span></span>  
  
-   [<span data-ttu-id="a298f-110">L’importation de certificats</span><span class="sxs-lookup"><span data-stu-id="a298f-110">Importing Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates.md)  
  
-   [<span data-ttu-id="a298f-111">Exportation de certificats</span><span class="sxs-lookup"><span data-stu-id="a298f-111">Exporting Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/exporting-certificates.md)