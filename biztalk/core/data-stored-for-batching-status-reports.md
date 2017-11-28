---
title: "Données stockées pour les rapports d’état de traitement par lots | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d55aa0e1-095f-434e-8530-f1a946ad4430
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db9831aafce56845fe7b75e91f5369a8860d8996
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-stored-for-batching-status-reports"></a><span data-ttu-id="8f02e-102">Données stockées pour des rapports d'état de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="8f02e-102">Data Stored for Batching Status Reports</span></span>
<span data-ttu-id="8f02e-103">Lorsque le **activer la création de rapports** propriété est sélectionnée pour un accord, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stocke l’état de chaque instance de traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="8f02e-103">When the **Turn ON Reporting** property is selected for an agreement, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will store the status of each batching instance.</span></span> <span data-ttu-id="8f02e-104">Cette propriété est en disponible dans le **propriétés générales** page de la **général** onglet dans le **propriétés de l’accord** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8f02e-104">This property is in available in the **General Properties** page of the **General** tab in the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="8f02e-105">Voici les différents états possibles :</span><span class="sxs-lookup"><span data-stu-id="8f02e-105">The status can be any of the following:</span></span>  
  
-   <span data-ttu-id="8f02e-106">**Défini**: l’instance de lot est configurée.</span><span class="sxs-lookup"><span data-stu-id="8f02e-106">**Defined**: The batch instance is configured.</span></span> <span data-ttu-id="8f02e-107">La date et l'heure d'activation du lot sont postérieures à la date et à l'heure actuelles.</span><span class="sxs-lookup"><span data-stu-id="8f02e-107">The batch activation start date time is greater than the current date time.</span></span> <span data-ttu-id="8f02e-108">Tous les paramètres de lot sont définis, mais le lot n'est pas en cours d'exécution (il n'accepte pas de documents).</span><span class="sxs-lookup"><span data-stu-id="8f02e-108">All batch parameters are defined, but the batch is not running (not accepting documents).</span></span>  
  
-   <span data-ttu-id="8f02e-109">**Active**: l’instance du lot a été activée et regroupe des documents informatisés.</span><span class="sxs-lookup"><span data-stu-id="8f02e-109">**Active**: The batch instance has been activated and is aggregating transaction sets.</span></span> <span data-ttu-id="8f02e-110">Vous pouvez voir le nombre de documents informatisés acceptés/rejetés.</span><span class="sxs-lookup"><span data-stu-id="8f02e-110">You can view the number of accepted/rejected transaction sets.</span></span>  
  
-   <span data-ttu-id="8f02e-111">**Publié**: le lot remplies les critères de déclenchement et a été publié dans la MessageBox, mais n’a pas été publié par le pipeline d’envoi ou le lot a été interrompu avant le traitement des messages.</span><span class="sxs-lookup"><span data-stu-id="8f02e-111">**Released**: The batch met the release criteria and was released into the MessageBox, but has not been released by the send pipeline, or that the batch was stopped before processing any messages.</span></span>  
  
-   <span data-ttu-id="8f02e-112">**Terminé**: le lot a été envoyé par le pipeline EdiSend.</span><span class="sxs-lookup"><span data-stu-id="8f02e-112">**Completed**: The batch was sent by the EdiSend pipeline.</span></span>  
  
 <span data-ttu-id="8f02e-113">Si le lot a été envoyé via le pipeline EdiSend, vous pouvez mettre en corrélation l'enregistrement de lot de l'interface utilisateur et un enregistrement de l'échange Edi envoyé, puis afficher les détails des documents informatisés.</span><span class="sxs-lookup"><span data-stu-id="8f02e-113">If the batch was sent by the EdiSend pipeline, you can correlate the batch record in the UI with a record of the sent Edi interchange, and view transaction set details.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f02e-114">De multiples instances de lot peuvent avoir l'état Terminé pour une configuration de lot.</span><span class="sxs-lookup"><span data-stu-id="8f02e-114">There may be multiple batch instances with a status of Completed for a batch configuration.</span></span>  
  
 <span data-ttu-id="8f02e-115">**Mise en corrélation un échange avec un lot**</span><span class="sxs-lookup"><span data-stu-id="8f02e-115">**Correlating an Interchange with a Batch**</span></span>  
  
 <span data-ttu-id="8f02e-116">L'activité BAM BusinessMessageJournal permet à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de mettre en corrélation un échange EDI reçu contenant des documents informatisés et un échange par lot sortant qui contient les mêmes documents informatisés.</span><span class="sxs-lookup"><span data-stu-id="8f02e-116">The BusinessMessageJournal BAM activity enables [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to correlate a received EDI interchange containing a transaction set with an outgoing batched interchange that contains the same transaction set.</span></span> <span data-ttu-id="8f02e-117">Pour plus d’informations sur la façon d’implémenter et utiliser ces informations de corrélation, consultez [corréler un document informatisé entrant avec un lot sortant](../core/correlating-an-incoming-transaction-set-with-an-outgoing-batch.md).</span><span class="sxs-lookup"><span data-stu-id="8f02e-117">For information about how to implement and use this correlation information, see [Correlating an Incoming Transaction Set with an Outgoing Batch](../core/correlating-an-incoming-transaction-set-with-an-outgoing-batch.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f02e-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f02e-118">See Also</span></span>  
 <span data-ttu-id="8f02e-119">[Données stockées pour les rapports d’état AS2 et EDI](../core/data-stored-for-edi-and-as2-status-reports.md) </span><span class="sxs-lookup"><span data-stu-id="8f02e-119">[Data Stored for EDI and AS2 Status Reports](../core/data-stored-for-edi-and-as2-status-reports.md) </span></span>  
 <span data-ttu-id="8f02e-120">[Données stockées pour les rapports d’état EDI](../core/data-stored-for-edi-status-reports.md) </span><span class="sxs-lookup"><span data-stu-id="8f02e-120">[Data Stored for EDI Status Reports](../core/data-stored-for-edi-status-reports.md) </span></span>  
 [<span data-ttu-id="8f02e-121">Données stockées pour les rapports d’état AS2</span><span class="sxs-lookup"><span data-stu-id="8f02e-121">Data Stored for AS2 Status Reports</span></span>](../core/data-stored-for-as2-status-reports.md)