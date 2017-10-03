---
title: "Problèmes connus avec les performances EDI et AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c47294f9-f728-4b6b-abe1-578434eb54df
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e034cf228ee92157c4b29c36660111bb1856c358
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-edi-and-as2-performance"></a><span data-ttu-id="9b158-102">Problèmes connus avec les performances EDI et AS2</span><span class="sxs-lookup"><span data-stu-id="9b158-102">Known Issues with EDI and AS2 Performance</span></span>
<span data-ttu-id="9b158-103">Cette rubrique décrit les problèmes connus liés aux performances des solutions EDI et AS2 de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b158-103">This topic describes known issues with the performance of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI and AS2 solutions.</span></span>  
  
## <a name="performance-considerations-for-edi-and-as2-status-reporting"></a><span data-ttu-id="9b158-104">Considérations relatives aux performances de la création de rapports d'état EDI et AS2</span><span class="sxs-lookup"><span data-stu-id="9b158-104">Performance Considerations for EDI and AS2 Status Reporting</span></span>  
 <span data-ttu-id="9b158-105">Lorsque vous activez la création de rapports d'état EDI ou AS2, les performances du système peuvent être affectées par le nombre de messages traités.</span><span class="sxs-lookup"><span data-stu-id="9b158-105">When you activate EDI or AS2 status reporting, the performance of your system may be affected by the number of messages that status reporting is performed for.</span></span> <span data-ttu-id="9b158-106">Lorsque vous sélectionnez la propriété « Stocker les documents informatisés/données utiles pour la création de rapports » pour le traitement EDI ou AS2, les performances du système peuvent être affectées par la taille des messages traités.</span><span class="sxs-lookup"><span data-stu-id="9b158-106">When you select the "Store transaction set/payload for reporting" property for either EDI or AS2 processing, the performance of your system may be affected by the size of the messages that status reporting is performed for.</span></span>  
  
 <span data-ttu-id="9b158-107">Les tables utilisées dans la base de données BAMPrimaryImport pour la création de rapports d'état EDI ou AS2 sont optimisées.</span><span class="sxs-lookup"><span data-stu-id="9b158-107">The tables used in the BAMPrimaryImport database for EDI or AS2 status reporting are optimized.</span></span> <span data-ttu-id="9b158-108">Aucune optimisation supplémentaire n'est requise.</span><span class="sxs-lookup"><span data-stu-id="9b158-108">No further optimization is required.</span></span> <span data-ttu-id="9b158-109">Vous pouvez toutefois accroître la vitesse d'archivage des données de la base de données d'importation principale BAM en modifiant la fenêtre de temps pour l'archivage des données d'instance d'activité dans la base de données BAMPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="9b158-109">You can, however, increase the rate at which data from the BAM primary import database is archived by changing the time window for archiving activity instance data in the BAMPrimaryImport database.</span></span> <span data-ttu-id="9b158-110">Pour plus d'informations, consultez la rubrique « Archivage des données dans la base de données d'importation principale » dans la documentation relative à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b158-110">For more information, see "Archiving Primary Import Database Data" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.</span></span>  
  
 <span data-ttu-id="9b158-111">Les données relatives aux documents informatisés et aux données utiles sont stockées dans la base de données BizTalkDTADb.</span><span class="sxs-lookup"><span data-stu-id="9b158-111">Transaction set/payload data is stored in the BizTalkDTADb database.</span></span> <span data-ttu-id="9b158-112">Pour plus d'informations sur les performances de cette base de données, consultez la rubrique « Présentation du comportement des performances de suivi DTA » dans la documentation relative à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b158-112">For more information about the performance of this database, see "Understanding DTA Tracking Performance Behavior" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.</span></span>  
  
 <span data-ttu-id="9b158-113">Les performances du système peuvent également être affectées par le degré de création de rapports d'état activé dans la configuration système.</span><span class="sxs-lookup"><span data-stu-id="9b158-113">Performance of your system may also be affected by the degree of status reporting enabled in the configuration of your system.</span></span> <span data-ttu-id="9b158-114">Pour améliorer les performances, désactivez un type spécifique de création de rapports d'état.</span><span class="sxs-lookup"><span data-stu-id="9b158-114">You may be able to improve performance by disabling a specific type of status reporting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b158-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b158-115">See Also</span></span>  
 [<span data-ttu-id="9b158-116">Dépannage des Solutions EDI et AS2</span><span class="sxs-lookup"><span data-stu-id="9b158-116">Troubleshooting EDI and AS2 Solutions</span></span>](../core/troubleshooting-edi-and-as2-solutions.md)