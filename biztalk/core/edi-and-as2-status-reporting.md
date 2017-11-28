---
title: "EDI et AS2 le rapport d’état | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9e58b29-9be0-41d6-ad35-1aae28e1a784
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31b08fd8222cee0cb0f04750eedcb32d06c28820
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-and-as2-status-reporting"></a><span data-ttu-id="9cc37-102">Rapport d'état EDI et AS2</span><span class="sxs-lookup"><span data-stu-id="9cc37-102">EDI and AS2 Status Reporting</span></span>
<span data-ttu-id="9cc37-103">Le rapport d'état EDI permet au personnel de back-office de suivre l'état des transmissions EDI et AS2.</span><span class="sxs-lookup"><span data-stu-id="9cc37-103">EDI status reporting enables operations personnel to track the status of EDI and AS2 transmissions.</span></span> <span data-ttu-id="9cc37-104">S'ils sont activés, les rapports d'état fournissent l'état complet d'une transaction d'échange de documents, notamment l'échange et les accusés de réception corrélés à l'échange.</span><span class="sxs-lookup"><span data-stu-id="9cc37-104">If enabled, status reports provide comprehensive status of a document exchange transaction, including an interchange and any acknowledgments correlated to the interchange.</span></span> <span data-ttu-id="9cc37-105">Ces rapports fournissent des données sur la réception, la validation, le traitement par lot et le traitement des accusés de réception des messages EDI et AS2.</span><span class="sxs-lookup"><span data-stu-id="9cc37-105">These reports provide data on receipt, validation, batching, and acknowledgment processing of EDI and AS2 messages.</span></span>  
  
 <span data-ttu-id="9cc37-106">Vous pouvez les utiliser pour obtenir l'état des échanges en attente et sans accusé de réception, des échanges complets, des scénarios d'erreur ou des scénarios d'application professionnelle.</span><span class="sxs-lookup"><span data-stu-id="9cc37-106">You can use these reports to get the status of pending and unacknowledged interchanges, complete interchanges, error scenarios, or business scenarios.</span></span> <span data-ttu-id="9cc37-107">Ces rapports permettent d'effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="9cc37-107">With these reports, you can do the following:</span></span>  
  
-   <span data-ttu-id="9cc37-108">Confirmer la réception des échanges.</span><span class="sxs-lookup"><span data-stu-id="9cc37-108">Confirm the receipt of interchanges</span></span>  
  
-   <span data-ttu-id="9cc37-109">Répertorier les échanges sortants en attente d'accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="9cc37-109">List outgoing interchanges awaiting acknowledgment</span></span>  
  
-   <span data-ttu-id="9cc37-110">Répertorier les échanges rejetés reçus.</span><span class="sxs-lookup"><span data-stu-id="9cc37-110">List all rejected interchanges received</span></span>  
  
-   <span data-ttu-id="9cc37-111">Répertorier les échanges sortants signalés comme étant rejetés ou partiellement acceptés.</span><span class="sxs-lookup"><span data-stu-id="9cc37-111">List outgoing interchanges that are reported as rejected or partially accepted.</span></span>  
  
 <span data-ttu-id="9cc37-112">Les données incluses dans les rapports d'état sont obtenues à partir des segments de contrôle de l'échange, tels que ISA, TA1, GS, UNB et UNG (à l'exception de l'état de l'accusé de réception fonctionnel).</span><span class="sxs-lookup"><span data-stu-id="9cc37-112">Data included in the status reports is obtained from interchange control segments, such as ISA, TA1, GS, UNB, and UNG (with the exception of the Functional ACK status).</span></span>  
  
 <span data-ttu-id="9cc37-113">**Interface utilisateur de rapport État**</span><span class="sxs-lookup"><span data-stu-id="9cc37-113">**Status Reporting UI**</span></span>  
  
 <span data-ttu-id="9cc37-114">Les rapports d'état EDI et AS2 sont disponibles dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9cc37-114">EDI and AS2 status reports are available from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span> <span data-ttu-id="9cc37-115">À partir de la **Hub du groupe** page de la **groupe BizTalk** nœud, vous avez des liens vers échange EDI et état de l’accusé de réception corrélé, état du lot et message AS2 et état MDN corrélé.</span><span class="sxs-lookup"><span data-stu-id="9cc37-115">From the **Group Hub** page of the **BizTalk Group** node, you have links to EDI interchange and correlated acknowledgment status, batch status, and AS2 message and correlated MDN status.</span></span> <span data-ttu-id="9cc37-116">Chacun de ces rapports fournit une plage de paramètres d'état que vous pouvez inclure ou exclure d'une requête d'expression, ce qui vous permet de créer le rapport d'état nécessaire.</span><span class="sxs-lookup"><span data-stu-id="9cc37-116">Each of these reports provides a range of status parameters that you can include or exclude from a query expression, enabling you to build the status report that they need.</span></span>  
  
 <span data-ttu-id="9cc37-117">Outre l'affichage de l'état d'un échange EDI, vous pouvez aussi consulter les documents informatisés contenus dans un échange.</span><span class="sxs-lookup"><span data-stu-id="9cc37-117">In addition to seeing the status of an EDI interchange, you can also view the transaction sets in an interchange.</span></span> <span data-ttu-id="9cc37-118">Pour cela, activez le stockage des charges de message dans les tables EDI de la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="9cc37-118">You do so by enabling the storage of message payloads in the EDI tables of the tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="9cc37-119">Pour afficher les documents informatisés, utilisez la commande Afficher les détails dans l'interface utilisateur de rapport d'état.</span><span class="sxs-lookup"><span data-stu-id="9cc37-119">You can view the transaction sets by using the view details command in the status reporting UI.</span></span>  
  
 <span data-ttu-id="9cc37-120">Vous pouvez aussi stocker les messages AS2 entrants ou sortants ou les messages MDN dans la base de données de non-répudiation.</span><span class="sxs-lookup"><span data-stu-id="9cc37-120">You can also store inbound or outbound AS2 messages or MDNs in the non-repudiation database.</span></span> <span data-ttu-id="9cc37-121">Pour afficher les documents informatisés ou les messages AS2, cliquez avec le bouton droit sur un message dans le rapport d'état, puis cliquez sur la commande appropriée.</span><span class="sxs-lookup"><span data-stu-id="9cc37-121">You can view the transaction sets or AS2 messages by right-clicking the message in the status report and selecting the appropriate command.</span></span>  
  
 <span data-ttu-id="9cc37-122">**Composants de rapport d’état**</span><span class="sxs-lookup"><span data-stu-id="9cc37-122">**Status Report Components**</span></span>  
  
 <span data-ttu-id="9cc37-123">Les composants [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] impliqués dans le rapport d'état sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="9cc37-123">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] components involved in status reporting are the following:</span></span>  
  
-   <span data-ttu-id="9cc37-124">le Désassembleur EDI dans le pipeline de réception EDI qui crée et met à jour les entrées d'état dans la banque de données pour un échange entrant ;</span><span class="sxs-lookup"><span data-stu-id="9cc37-124">The EDI Disassembler in the EDI receive pipeline that creates and updates status entries in the data store for an incoming interchange</span></span>  
  
-   <span data-ttu-id="9cc37-125">l'Assembleur EDI dans le pipeline d'envoi EDI qui crée et met à jour les entrées d'état dans la banque de données pour un échange sortant ;</span><span class="sxs-lookup"><span data-stu-id="9cc37-125">The EDI Assembler in the EDI send pipeline that creates and updates status entries in the data store for an outgoing interchange</span></span>  
  
-   <span data-ttu-id="9cc37-126">les banques de données qui stockent les entrées du rapport d'état.</span><span class="sxs-lookup"><span data-stu-id="9cc37-126">The data stores that store the status report entries.</span></span> <span data-ttu-id="9cc37-127">Il s'agit de la base de données d'importation principale BAM pour les données de suivi et de la table Contenu du message EDI de la base de données des suivis BizTalk (BizTalkDTADb) pour les documents informatisés et/ou le contenu des messages AS2 ;</span><span class="sxs-lookup"><span data-stu-id="9cc37-127">These are the BAM Primary Import database for tracking data and the EDI Message Content table of the BizTalk tracking database (BizTalkDTADb) for EDI transaction sets and/or AS2 message contents</span></span>  
  
-   <span data-ttu-id="9cc37-128">État de l’interface utilisateur de création de rapports sur le **Hub du groupe** page de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, qui est utilisé pour afficher les données du rapport d’état</span><span class="sxs-lookup"><span data-stu-id="9cc37-128">Status reporting UI on the **Group Hub** page of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, which is used to display status reporting data</span></span>  
  
-   <span data-ttu-id="9cc37-129">les options de propriété d'accord et d'accord de secours dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], qui permettent d'activer et de configurer le rapport d'état ;</span><span class="sxs-lookup"><span data-stu-id="9cc37-129">Agreement property and fallback agreement property options in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, which is used to enable and configure status reporting</span></span>  
  
-   <span data-ttu-id="9cc37-130">DTA et SQL Analysis Server qui exploitent l'infrastructure BAM.</span><span class="sxs-lookup"><span data-stu-id="9cc37-130">DTA and SQL Analysis Server that leverage the BAM infrastructure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9cc37-131">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9cc37-131">In This Section</span></span>  
  
-   [<span data-ttu-id="9cc37-132">Configuration d’EDI et AS2 le rapport d’état</span><span class="sxs-lookup"><span data-stu-id="9cc37-132">Configuration of EDI and AS2 Status Reporting</span></span>](../core/configuration-of-edi-and-as2-status-reporting.md)  
  
-   [<span data-ttu-id="9cc37-133">Types de rapports d’état AS2 et EDI</span><span class="sxs-lookup"><span data-stu-id="9cc37-133">Types of EDI and AS2 Status Reports</span></span>](../core/types-of-edi-and-as2-status-reports.md)  
  
-   [<span data-ttu-id="9cc37-134">Données stockées pour les rapports d’état AS2 et EDI</span><span class="sxs-lookup"><span data-stu-id="9cc37-134">Data Stored for EDI and AS2 Status Reports</span></span>](../core/data-stored-for-edi-and-as2-status-reports.md)  
  
-   [<span data-ttu-id="9cc37-135">Stockage des données pour les rapports d’état AS2 et EDI</span><span class="sxs-lookup"><span data-stu-id="9cc37-135">How Data Is Stored for EDI and AS2 Status Reports</span></span>](../core/how-data-is-stored-for-edi-and-as2-status-reports.md)