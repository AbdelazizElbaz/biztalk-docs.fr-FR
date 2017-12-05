---
title: "Configuration des propriétés de secours communes pour X12 et d’EDIFACT les Messages codés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7393d6ac-b901-43ef-a8d6-c5b0b3033257
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b99d6e60a2a5955a9f0873156dbc5f822b3d519
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="configuring-common-fallback-properties-for-x12-and-edifact-encoded-messages"></a><span data-ttu-id="21226-102">Configuration des propriétés de secours communes pour les messages X12 et EDIFACT</span><span class="sxs-lookup"><span data-stu-id="21226-102">Configuring Common Fallback Properties for X12 and EDIFACT Encoded Messages</span></span>
<span data-ttu-id="21226-103">Les propriétés de secours s'appliquent aux échanges X12 (notamment HIPAA) et EDIFACT.</span><span class="sxs-lookup"><span data-stu-id="21226-103">Fallback properties apply to both X12 (including HIPAA) - and EDIFACT-encoded interchanges.</span></span> <span data-ttu-id="21226-104">À l'instar des autres propriétés d'accord de secours, ces propriétés s'appliquent uniquement lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne parvient pas à identifier l'accord auquel un message entrant ou sortant correspond.</span><span class="sxs-lookup"><span data-stu-id="21226-104">As with all fallback agreement properties, these properties apply only when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] has not determined the agreement to which an incoming our outgoing message resolves to.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="21226-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="21226-105">Prerequisites</span></span>  
 <span data-ttu-id="21226-106">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="21226-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-set-common-global-properties"></a><span data-ttu-id="21226-107">Pour définir les propriétés globales communes</span><span class="sxs-lookup"><span data-stu-id="21226-107">To set common global properties</span></span>  
  
1.  <span data-ttu-id="21226-108">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **X12 paramètres de secours** ou **paramètres de secours EDIFACT**.</span><span class="sxs-lookup"><span data-stu-id="21226-108">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **X12 Fallback Settings** or **EDIFACT Fallback Settings**.</span></span>  
  
2.  <span data-ttu-id="21226-109">Dans le **paramètres de secours** sous l’onglet dans le **général** page, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="21226-109">In the **Fallback Settings General Pages** tab, on the **General** page, do the following:</span></span>  
  
    1.  <span data-ttu-id="21226-110">Cliquez sur **activer les paramètres de secours** pour activer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à utiliser les paramètres de l’accord de secours si aucun accord n’est résolu pour les messages entrants ou sortants.</span><span class="sxs-lookup"><span data-stu-id="21226-110">Click **Enable Fallback Settings** to enable [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to use the fallback agreement settings if no agreement is resolved for incoming or outgoing messages.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="21226-111">Si cette option est désactivée, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'utilisera pas les propriétés définies dans l'accord de secours.</span><span class="sxs-lookup"><span data-stu-id="21226-111">If this option is not checked, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will not use the properties set in the fallback agreement.</span></span>  
  
    2.  <span data-ttu-id="21226-112">Cliquez sur **activer la création de rapports EDI** pour activer la création de rapports pour tous les messages EDI.</span><span class="sxs-lookup"><span data-stu-id="21226-112">Click **Activate EDI Reporting** to activate reporting for all EDI messages.</span></span> <span data-ttu-id="21226-113">Cela garantit que les messages sont affichés dans l’état reporting écrans affichées en cliquant sur les liens en bas de la **Hub du groupe** volet de la Console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="21226-113">This ensures messages are displayed in the status reporting screens displayed by clicking the links at the bottom of the **Group Hub** pane of the BizTalk Server Administration Console.</span></span>  
  
    3.  <span data-ttu-id="21226-114">Si vous avez cliqué sur **activer la création de rapports EDI**, cliquez sur **stocker les transactions/données utiles pour les rapports** pour stocker les documents des jeux dans les tables EDI de la base de données des suivis (BizTalk BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="21226-114">If you clicked **Activate EDI Reporting**, click **Store transaction set/payload for reporting** to store transaction sets in the EDI tables of the tracking (BizTalkDTADb) database.</span></span>  
  
    4.  <span data-ttu-id="21226-115">Cliquez sur **des erreurs de journal EDI et les avertissements générés par le moteur EDI pour le journal des événements Windows** pour enregistrer des messages d’erreur / d’avertissement générés par le moteur EDI (pipelines EDI, l’orchestration, routage orchestration, etc.), avec contextuelles plus d’informations, dans l’Observateur d’événements Windows.</span><span class="sxs-lookup"><span data-stu-id="21226-115">Click **Log EDI errors and warnings generated by EDI engine to Windows event log** to log error/warnings messages generated by the EDI engine (EDI pipelines, batching orchestration, routing orchestration, etc.), with contextual information, to the Windows Event Viewer.</span></span> <span data-ttu-id="21226-116">Si cette case à cocher est désactivée, les messages d'erreur/d'avertissement ne sont pas consignés dans l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="21226-116">If cleared, these error/warning messages will not be logged to the Event Viewer.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="21226-117">Les erreurs système/de traitement sont consignés dans l'Observateur d'événements même si cette case est désactivée.</span><span class="sxs-lookup"><span data-stu-id="21226-117">System/processing errors are logged in the Event Viewer whether or not this checkbox is selected.</span></span>  
  
3.  <span data-ttu-id="21226-118">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider et accepter les modifications et fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="21226-118">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate and accept the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21226-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21226-119">See Also</span></span>  
 [<span data-ttu-id="21226-120">Configuration des propriétés d’un accord global ou de secours</span><span class="sxs-lookup"><span data-stu-id="21226-120">Configuring Global or Fallback Agreement Properties</span></span>](../core/configuring-global-or-fallback-agreement-properties.md)