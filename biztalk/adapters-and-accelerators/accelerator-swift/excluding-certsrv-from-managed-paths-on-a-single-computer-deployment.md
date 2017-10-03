---
title: "À l’exclusion de CertSrv à partir des chemins d’accès sur un déploiement sur un seul ordinateur gérés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed paths
- certificate server (CertSrv)
- certificates, certificate server (CertSrv)
ms.assetid: 39916663-b80e-49d8-ba9b-49276eb564fc
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c77fc1733859cd903bafcebc26162323feff82d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="excluding-certsrv-from-managed-paths-on-a-single-computer-deployment"></a><span data-ttu-id="6f269-102">À l’exclusion de CertSrv à partir de chemins d’accès gérés sur un déploiement sur un seul ordinateur</span><span class="sxs-lookup"><span data-stu-id="6f269-102">Excluding CertSrv from Managed Paths on a Single-Computer Deployment</span></span>
<span data-ttu-id="6f269-103">Si vous avez déployé [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] sur un seul ordinateur et également installé le serveur de certificats sur le même ordinateur, vous devez exclure le serveur de certificats (CertSrv) les chemins d’accès gérés dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Administration centrale de SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="6f269-103">If you have deployed [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] on a single computer and also installed the certificate server on the same computer, you need to exclude the certificate server (CertSrv) from the managed paths in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] SharePoint Server Central Administration.</span></span>  
  
### <a name="to-exclude-certsrv-from-the-managed-paths"></a><span data-ttu-id="6f269-104">Pour exclure les chemins d’accès gérés de CertSrv</span><span class="sxs-lookup"><span data-stu-id="6f269-104">To exclude CertSrv from the managed paths</span></span>  
  
1.  <span data-ttu-id="6f269-105">cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Outils d'administration**, puis cliquez sur **Administration centrale de SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="6f269-105">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration**.</span></span>  
  
2.  <span data-ttu-id="6f269-106">Dans la fenêtre Administration centrale, dans le **Configuration du serveur virtuel** , cliquez sur **configurer les paramètres du serveur virtuel**.</span><span class="sxs-lookup"><span data-stu-id="6f269-106">In the Central Administration window, in the **Virtual Server Configuration** section, click **Configure virtual server settings**.</span></span>  
  
3.  <span data-ttu-id="6f269-107">Dans la fenêtre liste des serveurs virtuels, cliquez sur **Site Web par défaut**.</span><span class="sxs-lookup"><span data-stu-id="6f269-107">In the Virtual Server List window, click **Default Web Site**.</span></span>  
  
4.  <span data-ttu-id="6f269-108">Dans la fenêtre des paramètres du serveur virtuel, dans le **gestion du serveur virtuel** , cliquez sur **définir les chemins d’accès gérés**.</span><span class="sxs-lookup"><span data-stu-id="6f269-108">In the Virtual Server Settings window, in the **Virtual Server Management** section, click **Define managed paths**.</span></span>  
  
5.  <span data-ttu-id="6f269-109">Dans la fenêtre Définir les chemins d’accès gérés, dans le **ajouter un nouveau chemin** section, entrez **CertSrv** dans les **chemin d’accès** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="6f269-109">In the Define Managed Paths window, in the **Add a New Path** section, enter **CertSrv** in the **Path** text box.</span></span> <span data-ttu-id="6f269-110">Dans le **Type** , cliquez sur **chemin d’accès exclu**.</span><span class="sxs-lookup"><span data-stu-id="6f269-110">In the **Type** section, click **Excluded Path**.</span></span> <span data-ttu-id="6f269-111">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6f269-111">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="6f269-112">Fermez la fenêtre Définir les chemins d’accès gérés.</span><span class="sxs-lookup"><span data-stu-id="6f269-112">Close the Define Managed Paths window.</span></span>