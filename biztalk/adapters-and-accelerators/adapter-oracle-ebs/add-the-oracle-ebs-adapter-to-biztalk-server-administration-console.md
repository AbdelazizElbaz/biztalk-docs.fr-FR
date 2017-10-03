---
title: "Ajouter l’adaptateur Oracle E-Business Suite à la console Administration de BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24b126aa-2a05-49fa-80e1-f1d5c21ad60f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 492a99d8835990ee630dfb0ad0603279873eca4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="add-the-oracle-e-business-suite-adapter-to-biztalk-server-administration-console"></a><span data-ttu-id="c6f45-102">Ajouter l’adaptateur Oracle E-Business Suite à la console d’Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="c6f45-102">Add the Oracle E-Business Suite adapter to BizTalk Server Administration console</span></span>
<span data-ttu-id="c6f45-103">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] peut être utilisé en tant qu’un port WCF-Custom ou WCF-OracleEBS dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c6f45-103">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] can be used in BizTalk Server either as a WCF-Custom port or a WCF-OracleEBS port.</span></span> <span data-ttu-id="c6f45-104">Si vous souhaitez utiliser le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] via un port personnalisé WCF, vous n’avez pas besoin ajouter le port WCF-Custom à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, car le port WCF-Custom est ajouté à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration par défaut.</span><span class="sxs-lookup"><span data-stu-id="c6f45-104">If you want to use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] through a WCF-Custom port, you do not need to add the WCF-Custom port to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console because the WCF-Custom port is added to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by default.</span></span> <span data-ttu-id="c6f45-105">Toutefois, si vous souhaitez utiliser le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] via un port WCF-OracleEBS, vous devez d’abord ajouter l’adaptateur WCF-OracleEBS à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="c6f45-105">However, if you want to use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] through a WCF-OracleEBS port, you must first add the WCF-OracleEBS adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="c6f45-106">Cette rubrique fournit des instructions sur l’ajout de l’adaptateur WCF-OracleEBS à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="c6f45-106">This topic provides instructions on how to add the WCF-OracleEBS adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c6f45-107">Si vous voulez configurer un port personnalisé WCF pour le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], vous ne devez pas effectuer cette procédure.</span><span class="sxs-lookup"><span data-stu-id="c6f45-107">If you want to configure a WCF-Custom port for the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], you need not perform this procedure.</span></span>  
  
### <a name="to-add-the-oracle-e-business-suite-adapter"></a><span data-ttu-id="c6f45-108">Pour ajouter l’adaptateur Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="c6f45-108">To add the Oracle E-Business Suite Adapter</span></span>  
  
1.  <span data-ttu-id="c6f45-109">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="c6f45-109">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="c6f45-110">Dans l’arborescence de la console, développez le **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur **cartes**.</span><span class="sxs-lookup"><span data-stu-id="c6f45-110">In the console tree, expand the **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.</span></span>  
  
3.  <span data-ttu-id="c6f45-111">Avec le bouton droit **cartes**, pointez sur **nouveau**, puis cliquez sur **carte**.</span><span class="sxs-lookup"><span data-stu-id="c6f45-111">Right-click **Adapters**, point to **New**, and click **Adapter**.</span></span>  
  
     <span data-ttu-id="c6f45-112">![Ajouter un adaptateur](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span><span class="sxs-lookup"><span data-stu-id="c6f45-112">![Add an adapter](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span></span>  
  
4.  <span data-ttu-id="c6f45-113">Dans le **propriétés de la carte** boîte de dialogue, spécifiez un nom pour l’adaptateur et à partir de la **carte** liste, sélectionnez **WCF-OracleEBS**.</span><span class="sxs-lookup"><span data-stu-id="c6f45-113">In the **Adapter Properties** dialog box, specify a name for the adapter and from the **Adapter** list, select **WCF-OracleEBS**.</span></span>  
  
     <span data-ttu-id="c6f45-114">![Ajouter WCF &#45; un adaptateur OracleEBS à BizTalk](../../adapters-and-accelerators/adapter-oracle-ebs/media/3e2cde5a-9f32-489c-a931-0dd509451e62.gif "3e2cde5a-9f32-489c-a931-0dd509451e62")</span><span class="sxs-lookup"><span data-stu-id="c6f45-114">![Add WCF&#45;OracleEBS adapter to BizTalk](../../adapters-and-accelerators/adapter-oracle-ebs/media/3e2cde5a-9f32-489c-a931-0dd509451e62.gif "3e2cde5a-9f32-489c-a931-0dd509451e62")</span></span>  
  
5.  <span data-ttu-id="c6f45-115">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c6f45-115">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6f45-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6f45-116">See Also</span></span>  
 [<span data-ttu-id="c6f45-117">Blocs de construction pour créer des applications d’Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="c6f45-117">Building blocks to create Oracle E-Business Suite applications</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)