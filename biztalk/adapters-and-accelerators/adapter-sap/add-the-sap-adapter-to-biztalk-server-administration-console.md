---
title: "Ajouter l’adaptateur SAP à la Console Administration de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95fc925d-0aac-4f0d-a19d-ad27469e4b3c
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19870e69dc502f9635f34b578c2853aaf8897e00
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="add-the-sap-adapter-to-biztalk-server-administration-console"></a><span data-ttu-id="6e3fc-102">Ajouter l’adaptateur SAP à la Console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="6e3fc-102">Add the SAP Adapter to BizTalk Server Administration Console</span></span>
<span data-ttu-id="6e3fc-103">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] peut être utilisé en tant qu’un port WCF-Custom ou WCF-SAP dans BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6e3fc-103">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] can be used in BizTalk either as a WCF-Custom port or a WCF-SAP port.</span></span> <span data-ttu-id="6e3fc-104">Si vous souhaitez utiliser le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] via un port personnalisé WCF, vous n’avez pas besoin ajouter le port WCF-Custom à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, car le port WCF-Custom est ajouté à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration par défaut.</span><span class="sxs-lookup"><span data-stu-id="6e3fc-104">If you want to use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] through a WCF-Custom port, you do not need to add the WCF-Custom port to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console because the WCF-Custom port is added to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by default.</span></span> <span data-ttu-id="6e3fc-105">Toutefois, si vous souhaitez utiliser le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] via un port WCF SAP, vous devez d’abord ajouter l’adaptateur WCF-SAP pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="6e3fc-105">However, if you want to use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] through a WCF-SAP port, you must first add the WCF-SAP adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="6e3fc-106">Cette rubrique fournit des instructions sur l’ajout de l’adaptateur WCF-SAP pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="6e3fc-106">This topic provides instructions on how to add the WCF-SAP adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6e3fc-107">Vous ne devez pas effectuer ces tâches si vous souhaitez configurer un port personnalisé WCF pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6e3fc-107">You need not perform these tasks if you want to configure a WCF-Custom port for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="add-the-sap-adapter"></a><span data-ttu-id="6e3fc-108">Ajouter l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="6e3fc-108">Add the SAP Adapter</span></span>  
  
1.  <span data-ttu-id="6e3fc-109">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="6e3fc-109">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="6e3fc-110">Dans l’arborescence de la console, développez le **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur **cartes**.</span><span class="sxs-lookup"><span data-stu-id="6e3fc-110">In the console tree, expand the **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.</span></span>  
  
3.  <span data-ttu-id="6e3fc-111">Avec le bouton droit **cartes**, pointez sur **nouveau**, puis cliquez sur **carte**.</span><span class="sxs-lookup"><span data-stu-id="6e3fc-111">Right-click **Adapters**, point to **New**, and click **Adapter**.</span></span>  
  
     <span data-ttu-id="6e3fc-112">![Ajouter un adaptateur](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span><span class="sxs-lookup"><span data-stu-id="6e3fc-112">![Add an adapter](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span></span>  
  
4.  <span data-ttu-id="6e3fc-113">Dans le **propriétés de la carte** boîte de dialogue, spécifiez un nom pour l’adaptateur et à partir de la **carte** liste, sélectionnez **WCF SAP**.</span><span class="sxs-lookup"><span data-stu-id="6e3fc-113">In the **Adapter Properties** dialog box, specify a name for the adapter and from the **Adapter** list, select **WCF-SAP**.</span></span>  
  
     <span data-ttu-id="6e3fc-114">![Ajouter un adaptateur SAP à BizTalk](../../adapters-and-accelerators/media/a1235b38-ab93-4233-924d-42710540b951.gif "a1235b38-ab93-4233-924d-42710540b951")</span><span class="sxs-lookup"><span data-stu-id="6e3fc-114">![Add SAP Adapter to BizTalk](../../adapters-and-accelerators/media/a1235b38-ab93-4233-924d-42710540b951.gif "a1235b38-ab93-4233-924d-42710540b951")</span></span>  
  
5.  <span data-ttu-id="6e3fc-115">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6e3fc-115">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e3fc-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e3fc-116">See Also</span></span>  
[<span data-ttu-id="6e3fc-117">Blocs de construction pour créer des applications SAP</span><span class="sxs-lookup"><span data-stu-id="6e3fc-117">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)