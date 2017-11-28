---
title: "Ajout de l’adaptateur de base de données Oracle à la Console Administration de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d71e161-addc-47d4-9103-3655f3fb0b0d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f004fe7e7355812923f2d218380e4e4ff1f04c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-the-oracle-database-adapter-to-biztalk-server-administration-console"></a><span data-ttu-id="99d47-102">Ajout de l’adaptateur de base de données Oracle à la Console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="99d47-102">Adding the Oracle Database Adapter to BizTalk Server Administration Console</span></span>
<span data-ttu-id="99d47-103">Cette rubrique fournit des instructions sur l’ajout de l’adaptateur WCF-OracleDB à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="99d47-103">This topic provides instructions on how to add the WCF-OracleDB adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="99d47-104">Vous ne devez pas effectuer ces tâches si vous souhaitez configurer un port personnalisé WCF pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99d47-104">You need not perform these tasks if you want to configure a WCF-Custom port for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
## <a name="add-the-oracle-database-adapter"></a><span data-ttu-id="99d47-105">Ajouter l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="99d47-105">Add the Oracle Database Adapter</span></span>  
  
1.  <span data-ttu-id="99d47-106">Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="99d47-106">Open the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="99d47-107">Développez le **groupe BizTalk**, développez **paramètres de plateforme**, puis sélectionnez **cartes**.</span><span class="sxs-lookup"><span data-stu-id="99d47-107">Expand the **BizTalk Group**, expand **Platform Settings**, and then select **Adapters**.</span></span>  
  
3.  <span data-ttu-id="99d47-108">Avec le bouton droit **cartes**, sélectionnez **nouveau**, puis sélectionnez **carte**.</span><span class="sxs-lookup"><span data-stu-id="99d47-108">Right-click **Adapters**, select **New**, and select **Adapter**.</span></span>  
  
     <span data-ttu-id="99d47-109">![Ajouter un adaptateur](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span><span class="sxs-lookup"><span data-stu-id="99d47-109">![Add an adapter](../../adapters-and-accelerators/media/c9610d42-8465-4099-b403-87df6dcd0d99.gif "c9610d42-8465-4099-b403-87df6dcd0d99")</span></span>  
  
4.  <span data-ttu-id="99d47-110">Dans le **propriétés de la carte** boîte de dialogue, entrez un nom pour l’adaptateur et à partir de la **carte** liste, sélectionnez **WCF-OracleDB**.</span><span class="sxs-lookup"><span data-stu-id="99d47-110">In the **Adapter Properties** dialog box, enter a name for the adapter and from the **Adapter** list, select **WCF-OracleDB**.</span></span>  
  
     <span data-ttu-id="99d47-111">![WCF Ajout &#45; carte OracleDB à BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/media/wcf-oracledb.gif "WCF_OracleDB")</span><span class="sxs-lookup"><span data-stu-id="99d47-111">![Adding WCF&#45;OracleDB adapter to BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/media/wcf-oracledb.gif "WCF_OracleDB")</span></span>  
  
5.  <span data-ttu-id="99d47-112">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="99d47-112">Select **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99d47-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99d47-113">See Also</span></span>  
[<span data-ttu-id="99d47-114">Blocs de construction pour développer des Applications BizTalk avec la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="99d47-114">Building Blocks to develop BizTalk Applications with Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)