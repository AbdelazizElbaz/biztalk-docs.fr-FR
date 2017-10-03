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
# <a name="importing-certificates"></a><span data-ttu-id="4bc7c-102">L’importation de certificats</span><span class="sxs-lookup"><span data-stu-id="4bc7c-102">Importing Certificates</span></span>
<span data-ttu-id="4bc7c-103">Cette section décrit comment importer des certificats, notamment où les importer à partir de, où les stocker et quels outils pour utiliser pour les importer.</span><span class="sxs-lookup"><span data-stu-id="4bc7c-103">This section describes how to import certificates, including where to import them from, where to store them, and what tools to use to import them.</span></span>  
  
 <span data-ttu-id="4bc7c-104">Il existe deux façons d’importer des certificats.</span><span class="sxs-lookup"><span data-stu-id="4bc7c-104">There are two ways to import certificates.</span></span> <span data-ttu-id="4bc7c-105">Vous pouvez utiliser l’outil CertWizard ou le composant logiciel enfichable Certificats pour [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="4bc7c-105">You can use the CertWizard tool or the Certificates snap-in for [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC).</span></span>  
  
-   <span data-ttu-id="4bc7c-106">CertWizard est un Assistant de ligne de commande qui configure l’utilisation du certificat basé sur les paramètres des commutateurs.</span><span class="sxs-lookup"><span data-stu-id="4bc7c-106">CertWizard is a step-by-step command-line wizard that configures the use of the certificate based on the settings of switches.</span></span> <span data-ttu-id="4bc7c-107">Cet outil est disponible dans le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] dossier SDK.</span><span class="sxs-lookup"><span data-stu-id="4bc7c-107">This tool is available in the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK folder.</span></span>  
  
-   <span data-ttu-id="4bc7c-108">Avec le composant logiciel enfichable Certificats dans la console MMC, vous pouvez importer un certificat dans le magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="4bc7c-108">With the Certificates snap-in in MMC, you can import a certificate into the certificate store.</span></span> <span data-ttu-id="4bc7c-109">Toutefois, ce processus manuel nécessite la configuration séparée de l’utilisation du certificat.</span><span class="sxs-lookup"><span data-stu-id="4bc7c-109">However, this manual process requires that you configure the use of the certificate separately.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="4bc7c-110">Pour importer ou travailler avec les certificats privés dans MMC, l’utilisateur qui a ouvert une session doit avoir l’identité de l’utilisateur des hôtes BizTalk.</span><span class="sxs-lookup"><span data-stu-id="4bc7c-110">To import or work with private certificates in MMC, the user who is logged on must have the user identity of the BizTalk Hosts.</span></span> <span data-ttu-id="4bc7c-111">Si non, vous devez exécuter le **runas** avec le commutateur de l’utilisateur et le compte de service d’hôte pour démarrer la console MMC Certificats, par exemple, **runas /user:hostsvc mmc**.</span><span class="sxs-lookup"><span data-stu-id="4bc7c-111">If not, you must run the **runas** command with the user switch and the host service account to start the Certificates MMC, for example, **runas /user:hostsvc mmc**.</span></span> <span data-ttu-id="4bc7c-112">En exécutant cette commande, vous supposez l’identité de l’utilisateur des hôtes BizTalk (BizTalkServerApplication et BizTalkServerIsolatedHost).</span><span class="sxs-lookup"><span data-stu-id="4bc7c-112">By running this command, you assume the user identity of the BizTalk Hosts (BizTalkServerApplication and BizTalkServerIsolatedHost).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4bc7c-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4bc7c-113">In This Section</span></span>  
  
-   [<span data-ttu-id="4bc7c-114">Sources de certificat et de magasins</span><span class="sxs-lookup"><span data-stu-id="4bc7c-114">Certificate Sources and Stores</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/certificate-sources-and-stores.md)  
  
-   [<span data-ttu-id="4bc7c-115">L’importation de certificats à l’aide de l’utilitaire CertWizard</span><span class="sxs-lookup"><span data-stu-id="4bc7c-115">Importing Certificates Using the CertWizard Utility</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-the-certwizard-utility.md)  
  
-   [<span data-ttu-id="4bc7c-116">L’importation de certificats à l’aide de MMC</span><span class="sxs-lookup"><span data-stu-id="4bc7c-116">Importing Certificates Using MMC</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-mmc.md)