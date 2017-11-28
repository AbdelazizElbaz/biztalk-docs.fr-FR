---
title: "Données stockées pour les rapports d’état AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6aa4077-3768-436b-99b9-d203a86a7e69
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2341004abe65864b2fceb90985871ecad0cf1e5e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-stored-for-as2-status-reports"></a><span data-ttu-id="eded9-102">Données stockées pour les rapports d'état AS2</span><span class="sxs-lookup"><span data-stu-id="eded9-102">Data Stored for AS2 Status Reports</span></span>
<span data-ttu-id="eded9-103">Deux niveaux de création de rapports sont disponibles dans le rapport d’état AS2 : le premier si les **activer la création de rapports** propriété est sélectionnée pour un accord (à partir de la **propriétés générales** page de la **général**  onglet dans le **propriétés de l’accord** boîte de dialogue) et le second si une propriété de stockage de base de données de non-répudiation est sélectionnée pour un accord.</span><span class="sxs-lookup"><span data-stu-id="eded9-103">Two levels of reporting are available in AS2 status reporting: the first if the **Turn ON Reporting** property is selected for an agreement (from the **General Properties** page of the **General** tab in the **Agreement Properties** dialog box), and the second if a non-repudiation database storage property is selected for an agreement.</span></span>  
  
## <a name="data-stored-if-as2-reporting-is-activated"></a><span data-ttu-id="eded9-104">Les données sont stockées si la création de rapports AS2 a été activée</span><span class="sxs-lookup"><span data-stu-id="eded9-104">Data Stored If AS2 Reporting Is Activated</span></span>  
 <span data-ttu-id="eded9-105">Si le **activer la création de rapports** propriété est sélectionnée pour un accord, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] conserve un enregistrement de tous les envoyé ou reçu les messages AS2 et MDN.</span><span class="sxs-lookup"><span data-stu-id="eded9-105">If the **Turn ON Reporting** property is selected for an agreement, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will keep a record of all sent or received AS2 messages and MDNs.</span></span>  
  
 <span data-ttu-id="eded9-106">Dans le cas d'un message AS2, BizTalk Server conserve les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="eded9-106">For a received AS2 message, BizTalk Server will store the following information:</span></span>  
  
-   <span data-ttu-id="eded9-107">Un enregistrement du message AS2.</span><span class="sxs-lookup"><span data-stu-id="eded9-107">A record of the AS2 message.</span></span>  
  
 <span data-ttu-id="eded9-108">Dans le cas d'un MDN reçu ou envoyé (synchrone ou asynchrone), BizTalk Server conserve les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="eded9-108">For a received or sent MDN (synchronous or asynchronous), BizTalk Server will store the following information:</span></span>  
  
-   <span data-ttu-id="eded9-109">Un enregistrement du MDN.</span><span class="sxs-lookup"><span data-stu-id="eded9-109">A record of the MDN.</span></span>  
  
 <span data-ttu-id="eded9-110">L'interface utilisateur de rapport d'état permet la corrélation de l'enregistrement du message AS2 avec l'enregistrement MDN approprié.</span><span class="sxs-lookup"><span data-stu-id="eded9-110">The status reporting UI enables correlation of the AS2 message record to the appropriate MDN record.</span></span>  
  
## <a name="data-stored-if-resend-as2-message-if-mdn-not-received-is-enabled"></a><span data-ttu-id="eded9-111">Les données sont stockées si Renvoyer le message AS2 si un MDN n'est pas reçu est activé</span><span class="sxs-lookup"><span data-stu-id="eded9-111">Data Stored If Resend AS2 Message If MDN Not Received Is Enabled</span></span>  
 <span data-ttu-id="eded9-112">Si le **renvoyer le message AS2 si MDN non reçu** propriété est sélectionnée pour un accord, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enregistrera les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="eded9-112">If the **Resend AS2 message if MDN not received** property is selected for an agreement, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will record the following information:</span></span>  
  
-   <span data-ttu-id="eded9-113">Heure de chaque nouvelle tentative d'envoi</span><span class="sxs-lookup"><span data-stu-id="eded9-113">Time of each resend attempt</span></span>  
  
-   <span data-ttu-id="eded9-114">État de chaque nouvelle tentative d'envoi</span><span class="sxs-lookup"><span data-stu-id="eded9-114">Status of each resend attempt</span></span>  
  
-   <span data-ttu-id="eded9-115">Index de chaque nouvelle tentative d'envoi</span><span class="sxs-lookup"><span data-stu-id="eded9-115">Index of each resend attempt</span></span>  
  
## <a name="data-stored-if-non-repudiation-database-storage-is-enabled"></a><span data-ttu-id="eded9-116">Les données sont stockées si le stockage dans la base de données de non-répudiation est activé</span><span class="sxs-lookup"><span data-stu-id="eded9-116">Data Stored If Non-Repudiation Database Storage Is Enabled</span></span>  
 <span data-ttu-id="eded9-117">Le stockage dans la base de données de non-répudiation est activé si les propriétés d'accord suivantes sont sélectionnées :</span><span class="sxs-lookup"><span data-stu-id="eded9-117">Non-repudiation database storage is enabled by the following agreement properties is selected:</span></span>  
  
-   <span data-ttu-id="eded9-118">NRR activé pour les messages AS2 codés en sortie</span><span class="sxs-lookup"><span data-stu-id="eded9-118">NRR enabled for outbound encoded AS2 messages</span></span>  
  
-   <span data-ttu-id="eded9-119">NRR activé pour les messages AS2 décodés en sortie</span><span class="sxs-lookup"><span data-stu-id="eded9-119">NRR enabled for outbound decoded AS2 messages</span></span>  
  
-   <span data-ttu-id="eded9-120">NRR activé pour le MDN en entrée</span><span class="sxs-lookup"><span data-stu-id="eded9-120">NRR enabled for inbound MDN</span></span>  
  
-   <span data-ttu-id="eded9-121">NRR activé pour les messages AS2 codés en entrée</span><span class="sxs-lookup"><span data-stu-id="eded9-121">NRR enabled for inbound encoded AS2 messages</span></span>  
  
-   <span data-ttu-id="eded9-122">NRR activé pour les messages AS2 décodés en entrée</span><span class="sxs-lookup"><span data-stu-id="eded9-122">NRR enabled for inbound decoded AS2 messages</span></span>  
  
-   <span data-ttu-id="eded9-123">NRR activé pour le MDN en sortie</span><span class="sxs-lookup"><span data-stu-id="eded9-123">NRR enabled for outbound MDN</span></span>  
  
 <span data-ttu-id="eded9-124">Si au moins une propriété est sélectionnée, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enregistrera les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="eded9-124">If one or more of the above properties is selected, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will store the following information:</span></span>  
  
-   <span data-ttu-id="eded9-125">Le contenu de tout message AS2 et le contenu de n'importe quel MDN (avec ou sans en-têtes AS2).</span><span class="sxs-lookup"><span data-stu-id="eded9-125">The content of any AS2 message and the content of any MDN (with or without AS2 headers).</span></span>  
  
## <a name="data-stored-for-edi-over-as2"></a><span data-ttu-id="eded9-126">Données stockées pour EDI via AS2</span><span class="sxs-lookup"><span data-stu-id="eded9-126">Data Stored For EDI Over AS2</span></span>  
 <span data-ttu-id="eded9-127">Si le **activer la création de rapports** propriété est sélectionnée pour un accord EDI ainsi que d’un accord AS2, puis vous pouvez associer l’enregistrement de message AS2 (contenant la charge EDI) avec un enregistrement de message EDI.</span><span class="sxs-lookup"><span data-stu-id="eded9-127">If the **Turn ON Reporting** property is selected both for an EDI agreement as well as an AS2 agreement, then you can correlate an AS2 message record (containing EDI payload) with an EDI message record.</span></span>  
  
 <span data-ttu-id="eded9-128">Si le stockage des documents informatisés est activé, vous pouvez afficher les documents informatisés et le message AS2 dans l'interface utilisateur du rapport d'état.</span><span class="sxs-lookup"><span data-stu-id="eded9-128">If transaction set storage is enabled, you can display transaction set details and AS2 message content details in the status reporting UI.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eded9-129">Vous devez utiliser le pipeline AS2EdiReceive ou AS2EdiSend pour accéder à ces rapports.</span><span class="sxs-lookup"><span data-stu-id="eded9-129">You must use the AS2EdiReceive or AS2EdiSend pipeline to have access to these reports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eded9-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eded9-130">See Also</span></span>  
 <span data-ttu-id="eded9-131">[Données stockées pour les rapports d’état AS2 et EDI](../core/data-stored-for-edi-and-as2-status-reports.md) </span><span class="sxs-lookup"><span data-stu-id="eded9-131">[Data Stored for EDI and AS2 Status Reports](../core/data-stored-for-edi-and-as2-status-reports.md) </span></span>  
 <span data-ttu-id="eded9-132">[Données stockées pour les rapports d’état EDI](../core/data-stored-for-edi-status-reports.md) </span><span class="sxs-lookup"><span data-stu-id="eded9-132">[Data Stored for EDI Status Reports](../core/data-stored-for-edi-status-reports.md) </span></span>  
 [<span data-ttu-id="eded9-133">Données stockées pour les rapports d’état de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="eded9-133">Data Stored for Batching Status Reports</span></span>](../core/data-stored-for-batching-status-reports.md)