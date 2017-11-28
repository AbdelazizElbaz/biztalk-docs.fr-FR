---
title: "Magasins de données du rapport État | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6cd40ce8-1ac6-43b4-9cef-7cd045e8893c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da876f1151b641216cf9613f6830ed84049da83d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="status-report-data-stores"></a><span data-ttu-id="09db1-102">Banques de données des rapports d'état</span><span class="sxs-lookup"><span data-stu-id="09db1-102">Status Report Data Stores</span></span>
<span data-ttu-id="09db1-103">Les données de suivi des rapports d'état sont stockées dans la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="09db1-103">Status reporting tracking data is stored in the BAM Primary Import database.</span></span> <span data-ttu-id="09db1-104">Plusieurs tables de cette base de données sont utilisées pour les données des messages EDI et AS2, y compris des tables commençant par dbo.bam_AS2, dbo.bam.batching et dbo.bam.InterchangeStatusActivity.</span><span class="sxs-lookup"><span data-stu-id="09db1-104">A number of tables in this database are used for EDI and AS2 message data, including tables starting with dbo.bam_AS2, dbo.bam.batching, dbo.bam.InterchangeStatusActivity, and others.</span></span> <span data-ttu-id="09db1-105">Les données d'état sont stockées dans la base de données d'importation principale même si la création de rapports EDI est désactivée.</span><span class="sxs-lookup"><span data-stu-id="09db1-105">Status data is stored in the Primary Import even if EDI reporting is disabled.</span></span> <span data-ttu-id="09db1-106">Vous pourrez afficher et effectuer des requêtes sur ces données dans l'interface utilisateur de rapport d'état uniquement si la création de rapports d'état est activée.</span><span class="sxs-lookup"><span data-stu-id="09db1-106">You will only be to view and query this data in the status reporting UI if status reporting is activated.</span></span>  
  
 <span data-ttu-id="09db1-107">Si vous activez le stockage des données de message à des fins de non-répudiation, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stocke les données EDI et/ou AS2 dans la table Contenu du message EDI de la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="09db1-107">If you enable storage of message data for non-repudiation purposes, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will store the EDI and/or AS2 data in the EDI Message Content table of the BizTalk tracking database (BizTalkDTADb).</span></span> <span data-ttu-id="09db1-108">Si vous activez le stockage de contenu pour l’affichage des détails de la charge utile du message (en sélectionnant le **stocker la charge de message de création de rapports** propriété d’accord dans le **propriétés générales** page de la **Générales** onglet dans le **propriétés de l’accord** boîte de dialogue), [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stocke également les documents informatisés dans cette table.</span><span class="sxs-lookup"><span data-stu-id="09db1-108">If you enable storage of message contents for viewing details of the payload (by selecting the **Store message payload for reporting** agreement property in the **General Properties** page of the **General** tab in the **Agreement Properties** dialog box), [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will also store the transaction sets in this table.</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="09db1-109"> archive et supprime les données de la base de données d'importation principale BAM et des bases de données BizTalkDTADb.</span><span class="sxs-lookup"><span data-stu-id="09db1-109"> archives and purges data from the BAM Primary Import and BizTalkDTADb databases.</span></span> <span data-ttu-id="09db1-110">Les tables des bases de données sont régulièrement nettoyées.</span><span class="sxs-lookup"><span data-stu-id="09db1-110">The tables in the databases are cleaned out according to a regular schedule.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09db1-111">La base de données d'importation principale BAM et les bases de données DTA peuvent être désynchronisées si chacune d'elles présente un intervalle d'archivage différent.</span><span class="sxs-lookup"><span data-stu-id="09db1-111">The BAM Primary Import and DTA DB databases could be out of synch if each has a different interval for archiving.</span></span>  
  
 <span data-ttu-id="09db1-112">La création de rapports d'état EDI et AS2 peut avoir un impact sur les performances.</span><span class="sxs-lookup"><span data-stu-id="09db1-112">EDI and AS2 status reporting may have an impact upon performance.</span></span> <span data-ttu-id="09db1-113">Pour plus d’informations, consultez « Performances considérations pour EDI et AS2 rapport d’état » dans [problèmes connus avec les performances EDI et AS2](../core/known-issues-with-edi-and-as2-performance.md).</span><span class="sxs-lookup"><span data-stu-id="09db1-113">For more information, see "Performance Considerations for EDI and AS2 Status Reporting" in [Known Issues with EDI and AS2 Performance](../core/known-issues-with-edi-and-as2-performance.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09db1-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09db1-114">See Also</span></span>  
 [<span data-ttu-id="09db1-115">Stockage des données pour les rapports d’état AS2 et EDI</span><span class="sxs-lookup"><span data-stu-id="09db1-115">How Data Is Stored for EDI and AS2 Status Reports</span></span>](../core/how-data-is-stored-for-edi-and-as2-status-reports.md)