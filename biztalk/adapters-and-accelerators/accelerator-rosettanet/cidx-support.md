---
title: Prise en charge CIDX | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CIDX, procedures
- CIDX, about CIDX
- CIDX, Elemica Exchange Server Provider (ESP)
- CIDX, PIPs
- CIDX
- Elemica Exchange Server Provider (ESP)
- procedures [CIDX]
- PIPs, CIDX
ms.assetid: 58b75ad3-f6b9-47c0-8dbf-506a3eaf010b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 224d2b50d132efa67e1cfc24dda2df77fa7d29e3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cidx-support"></a><span data-ttu-id="d58a0-102">Prise en charge CIDX</span><span class="sxs-lookup"><span data-stu-id="d58a0-102">CIDX Support</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="d58a0-103">[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] prend en charge l’échange de messages XML de CIDX (Chemical Industry Data Exchange).</span><span class="sxs-lookup"><span data-stu-id="d58a0-103"> [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] provides support for CIDX (Chemical Industry Data Exchange) XML message exchange.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="d58a0-104">prend en charge les normes CIDX chem versions 2.0 et 3.0, qui utilisent tous deux le Framework RNIF (RosettaNet Implementation) 1.1.</span><span class="sxs-lookup"><span data-stu-id="d58a0-104"> supports CIDX Chem eStandards versions 2.0 and 3.0, both of which use the RosettaNet Implementation Framework (RNIF) 1.1.</span></span>  
  
 <span data-ttu-id="d58a0-105">Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] processus publics simples asynchrones (prise en charge des messages d’action unique et double action) consommer et acheminer du contenu de service CIDX.</span><span class="sxs-lookup"><span data-stu-id="d58a0-105">The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] asynchronous simple public processes (supporting single-action and double-action messages) consume and route CIDX service content.</span></span>  
  
 <span data-ttu-id="d58a0-106">Pour un contrat basé sur un PIP CIDX, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] validera les éléments suivants dans un message :</span><span class="sxs-lookup"><span data-stu-id="d58a0-106">For an agreement based on a CIDX PIP, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will validate the following in a message:</span></span>  
  
-   <span data-ttu-id="d58a0-107">Version de RNIF 1.1 uniquement</span><span class="sxs-lookup"><span data-stu-id="d58a0-107">RNIF 1.1 version only</span></span>  
  
-   <span data-ttu-id="d58a0-108">Aucun 0 a 1</span><span class="sxs-lookup"><span data-stu-id="d58a0-108">No 0A1</span></span>  
  
-   <span data-ttu-id="d58a0-109">Une seule Action</span><span class="sxs-lookup"><span data-stu-id="d58a0-109">Only Single Action</span></span>  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="d58a0-110">vous empêcheront pas de paramètre de la `Standard` propriété pour une configuration de processus à « CIDX », une fois que vous avez défini le `0A1 agreement` propriété pour un contrat qui utilise ce profil à « 0 a 1 » (qui n’est pas pris en charge pour CIDX).</span><span class="sxs-lookup"><span data-stu-id="d58a0-110"> will not prevent you from setting the `Standard` property for a process configuration to "CIDX", after you have set the `0A1 agreement` property for an agreement that uses that profile to "0A1" (which is not supported for CIDX).</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="d58a0-111">n’effectue pas la validation de champ croisé susceptibles d’empêcher cela.</span><span class="sxs-lookup"><span data-stu-id="d58a0-111"> does not perform the cross-field validation that would prevent this.</span></span>  
  
## <a name="applying-a-pip-to-a-cidx-implementation"></a><span data-ttu-id="d58a0-112">Application d’une adresse PIP à une implémentation CIDX</span><span class="sxs-lookup"><span data-stu-id="d58a0-112">Applying a PIP to a CIDX Implementation</span></span>  
 <span data-ttu-id="d58a0-113">Pour appliquer une adresse PIP à une implémentation CIDX, définissez la `Standard` propriété dans le profil de configuration de processus pour **CIDX**.</span><span class="sxs-lookup"><span data-stu-id="d58a0-113">To apply a PIP to a CIDX implementation, set the `Standard` property in the process configuration profile to **CIDX**.</span></span> <span data-ttu-id="d58a0-114">Une fois que vous avez terminé, vous serez en mesure d’entrer des valeurs pour le Message standard, version Standard et ID de liaison de charge utile.</span><span class="sxs-lookup"><span data-stu-id="d58a0-114">After you have finished, you will be able to enter values for the Message standard, Standard version, and Payload binding ID.</span></span> <span data-ttu-id="d58a0-115">Vous pouvez trouver ces valeurs dans la spécification de chem CIDX normes.</span><span class="sxs-lookup"><span data-stu-id="d58a0-115">You can find these values in the CIDX Chem eStandards specification.</span></span>  
  
## <a name="connecting-to-the-elemica-network"></a><span data-ttu-id="d58a0-116">Connexion au réseau Elemica</span><span class="sxs-lookup"><span data-stu-id="d58a0-116">Connecting to the Elemica Network</span></span>  
 <span data-ttu-id="d58a0-117">Vous pouvez activer une installation de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] pour se connecter à la Elemica [!INCLUDE[btsExchangeSvrNoVersion](../../includes/btsexchangesvrnoversion-md.md)] fournisseur (ESP).</span><span class="sxs-lookup"><span data-stu-id="d58a0-117">You can enable an installation of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] to connect to the Elemica [!INCLUDE[btsExchangeSvrNoVersion](../../includes/btsexchangesvrnoversion-md.md)] Provider (ESP).</span></span> <span data-ttu-id="d58a0-118">Vous pouvez utiliser le réseau Elemica pour l’achat de produits chimiques-secteur, la vente et la gestion de chaîne d’approvisionnement à l’aide de l’échange de messages CIDX.</span><span class="sxs-lookup"><span data-stu-id="d58a0-118">You can use the Elemica network for chemical-industry buying, selling, and supply-chain management using CIDX message exchange.</span></span>  
  
 <span data-ttu-id="d58a0-119">Vous personnalisez [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] pour se connecter à Elemica à l’aide de fichiers de projet dans le Pack de connectivité Elemica.</span><span class="sxs-lookup"><span data-stu-id="d58a0-119">You customize [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] to connect to Elemica using project files in the Elemica Connectivity Pack.</span></span> <span data-ttu-id="d58a0-120">Vous pouvez télécharger le Pack de connectivité à partir de [http://go.microsoft.com/fwlink/?LinkId=46195](http://go.microsoft.com/fwlink/?LinkId=46195).</span><span class="sxs-lookup"><span data-stu-id="d58a0-120">You can download the Connectivity Pack from [http://go.microsoft.com/fwlink/?LinkId=46195](http://go.microsoft.com/fwlink/?LinkId=46195).</span></span> <span data-ttu-id="d58a0-121">Pour plus d’informations, consultez le livre blanc « Connexion au réseau Elemica avec BizTalk Accelerator pour RosettaNet 3.0 » sur MSDN à l’adresse [http://go.microsoft.com/fwlink/?linkid=46539](http://go.microsoft.com/fwlink/?linkid=46539).</span><span class="sxs-lookup"><span data-stu-id="d58a0-121">For more information, see the “Connecting to the Elemica Network with BizTalk Accelerator for RosettaNet 3.0” white paper on MSDN at [http://go.microsoft.com/fwlink/?linkid=46539](http://go.microsoft.com/fwlink/?linkid=46539).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d58a0-122">Les informations contenues dans le livre blanc « Connexion au réseau Elemica avec BizTalk Accelerator pour RosettaNet 3.0 » sont valides pour [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d58a0-122">The information in the "Connecting to the Elemica Network with BizTalk Accelerator for RosettaNet 3.0" white paper is valid for [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)].</span></span>  
  
## <a name="cidx-procedures"></a><span data-ttu-id="d58a0-123">Procédures CIDX</span><span class="sxs-lookup"><span data-stu-id="d58a0-123">CIDX Procedures</span></span>  
 <span data-ttu-id="d58a0-124">Les sections suivantes décrivent comment configurer l’échange de messages CIDX :</span><span class="sxs-lookup"><span data-stu-id="d58a0-124">The following sections described how to set up CIDX message exchange:</span></span>  
  
-   [<span data-ttu-id="d58a0-125">Paramètre des CIDX chem échange de messages</span><span class="sxs-lookup"><span data-stu-id="d58a0-125">Setting Up CIDX eStandards Message Exchange</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md)  
  
-   [<span data-ttu-id="d58a0-126">Création ou modification d’un accord</span><span class="sxs-lookup"><span data-stu-id="d58a0-126">Creating or Editing an Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)  
  
-   [<span data-ttu-id="d58a0-127">L’importation d’un PIP basé sur XSD</span><span class="sxs-lookup"><span data-stu-id="d58a0-127">Importing an XSD-based PIP</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/importing-an-xsd-based-pip.md)  
  
## <a name="see-also"></a><span data-ttu-id="d58a0-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d58a0-128">See Also</span></span>  
 <span data-ttu-id="d58a0-129">[BizTalk Accelerator for RosettaNet ajoutée à BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="d58a0-129">[What BizTalk Accelerator for RosettaNet Adds to BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md) </span></span>  
 [<span data-ttu-id="d58a0-130">Normes de messagerie CIDX</span><span class="sxs-lookup"><span data-stu-id="d58a0-130">CIDX Messaging Standards</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/cidx-messaging-standards.md)