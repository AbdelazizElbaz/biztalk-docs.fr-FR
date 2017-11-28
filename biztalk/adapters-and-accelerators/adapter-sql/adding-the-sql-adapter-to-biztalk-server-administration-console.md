---
title: "Ajout de l’adaptateur SQL à la Console Administration de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd974f28-c9cb-46de-95be-83716231ebcd
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3510fb31bffe4c5823593fac34d5d5f1d5849c65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-the-sql-adapter-to-biztalk-server-administration-console"></a><span data-ttu-id="7cb79-102">Ajout de l’adaptateur SQL à la Console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7cb79-102">Adding the SQL Adapter to BizTalk Server Administration Console</span></span>
<span data-ttu-id="7cb79-103">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] peut être utilisé en tant qu’un port WCF-Custom ou WCF-SQL dans BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7cb79-103">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] can be used in BizTalk either as a WCF-Custom port or a WCF-SQL port.</span></span> <span data-ttu-id="7cb79-104">Si vous souhaitez utiliser le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] via un port personnalisé WCF, vous n’avez pas besoin ajouter le port WCF-Custom à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, car le port WCF-Custom est ajouté à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration par défaut.</span><span class="sxs-lookup"><span data-stu-id="7cb79-104">If you want to use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] through a WCF-Custom port, you do not need to add the WCF-Custom port to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console because the WCF-Custom port is added to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by default.</span></span> <span data-ttu-id="7cb79-105">Toutefois, si vous souhaitez utiliser le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] via un port WCF-SQL, vous devez d’abord ajouter l’adaptateur WCF-SQL pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="7cb79-105">However, if you want to use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] through a WCF-SQL port, you must first add the WCF-SQL adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="7cb79-106">Cette rubrique vous montre comment ajouter l’adaptateur WCF-SQL pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="7cb79-106">This topic shows you how to add the WCF-SQL adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7cb79-107">Vous n’avez pas besoin de suivre ces étapes si vous souhaitez configurer un port personnalisé WCF pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7cb79-107">You do not need to follow these steps if you want to configure a WCF-Custom port for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
## <a name="add-the-sql-adapter"></a><span data-ttu-id="7cb79-108">Ajouter l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="7cb79-108">Add the SQL Adapter</span></span>  
  
1.  <span data-ttu-id="7cb79-109">Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="7cb79-109">Open the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="7cb79-110">Développez le **groupe BizTalk**, développez **paramètres de plateforme**, puis sélectionnez **cartes**.</span><span class="sxs-lookup"><span data-stu-id="7cb79-110">Expand the **BizTalk Group**, expand **Platform Settings**, and then select **Adapters**.</span></span>  
  
3.  <span data-ttu-id="7cb79-111">Avec le bouton droit **cartes**, pointez sur **nouveau**, puis sélectionnez **carte**.</span><span class="sxs-lookup"><span data-stu-id="7cb79-111">Right-click **Adapters**, point to **New**, and select **Adapter**.</span></span>  
  
     <span data-ttu-id="7cb79-112">![Ajouter un adaptateur](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span><span class="sxs-lookup"><span data-stu-id="7cb79-112">![Add an adapter](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span></span>  
  
4.  <span data-ttu-id="7cb79-113">Dans le **propriétés de la carte** boîte de dialogue, entrez un nom pour la carte et de la **carte** liste, sélectionnez **WCF-SQL**.</span><span class="sxs-lookup"><span data-stu-id="7cb79-113">In the **Adapter Properties** dialog box, enter a name for the adapter, and from the **Adapter** list, select **WCF-SQL**.</span></span>  
  
     <span data-ttu-id="7cb79-114">![Ajouter WCF &#45; Adaptateur SQL à BizTalk](../../adapters-and-accelerators/adapter-sql/media/4c6e2650-5d3a-4de8-a60a-a136d93a6fcf.gif "4c6e2650-5d3a-4de8-a60a-a136d93a6fcf")</span><span class="sxs-lookup"><span data-stu-id="7cb79-114">![Add WCF&#45;SQL adapter to BizTalk](../../adapters-and-accelerators/adapter-sql/media/4c6e2650-5d3a-4de8-a60a-a136d93a6fcf.gif "4c6e2650-5d3a-4de8-a60a-a136d93a6fcf")</span></span>  
  
5.  <span data-ttu-id="7cb79-115">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="7cb79-115">Select **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cb79-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7cb79-116">See Also</span></span>  
 [<span data-ttu-id="7cb79-117">Blocs de construction pour développer des applications BizTalk à l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="7cb79-117">Building blocks to develop BizTalk applications with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)