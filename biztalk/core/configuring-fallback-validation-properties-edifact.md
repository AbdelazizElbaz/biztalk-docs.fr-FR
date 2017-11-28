---
title: "Configuration des propriétés de Validation de secours (EDIFACT) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b925d063-e24b-4cfb-acbd-dcadb511011d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf0e103eb2e20bb64973cd207ed2a55c2f91e58d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-validation-properties-edifact"></a><span data-ttu-id="4429e-102">Configuration des propriétés de validation de secours (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="4429e-102">Configuring Fallback Validation Properties (EDIFACT)</span></span>
<span data-ttu-id="4429e-103">Les instructions de cette section décrivent comment empêcher le traitement des numéros de contrôle en double.</span><span class="sxs-lookup"><span data-stu-id="4429e-103">This section provides instructions on how to prevent duplicate control numbers from being processed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4429e-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="4429e-104">Prerequisites</span></span>  
 <span data-ttu-id="4429e-105">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4429e-105">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-duplicate-validation"></a><span data-ttu-id="4429e-106">Pour configurer la validation des doublons</span><span class="sxs-lookup"><span data-stu-id="4429e-106">To configure duplicate validation</span></span>  
  
1.  <span data-ttu-id="4429e-107">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **paramètres de secours EDIFACT**.</span><span class="sxs-lookup"><span data-stu-id="4429e-107">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **EDIFACT Fallback Settings**.</span></span>  
  
2.  <span data-ttu-id="4429e-108">Dans le **paramètres de secours EDIFACT** boîte de dialogue le **accords EDIFACT** sous l’onglet sous la **paramètres de l’échange** , cliquez sur **Validation** .</span><span class="sxs-lookup"><span data-stu-id="4429e-108">In the **EDIFACT Fallback Settings** dialog box, in the **EDIFACT Agreement Pages** tab, under the **Interchange Settings** section, click **Validation**.</span></span>  
  
3.  <span data-ttu-id="4429e-109">Sélectionnez le **numéro de contrôle d’échange (UNB5)** case à cocher pour activer le pipeline de réception bloquer les échanges en double.</span><span class="sxs-lookup"><span data-stu-id="4429e-109">Select the **Interchange control number (UNB5)** check box to enable the receive pipeline to block duplicate interchanges.</span></span> <span data-ttu-id="4429e-110">Lorsque cette option est activée, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vérifie que le numéro de contrôle de l'échange reçu ne correspond pas au numéro de contrôle d'un autre échange reçu.</span><span class="sxs-lookup"><span data-stu-id="4429e-110">If selected, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will check that the interchange control number for the received interchange does not match the interchange control number of another received interchange.</span></span> <span data-ttu-id="4429e-111">Si le serveur détecte des doublons, le pipeline de réception ne traite pas l'échange.</span><span class="sxs-lookup"><span data-stu-id="4429e-111">If a match is detected, the receive pipeline will not process the interchange.</span></span>  
  
4.  <span data-ttu-id="4429e-112">Si **numéro de contrôle d’échange (UNB5)** est sélectionné, dans le **vérifier les doublons UNB5 dans** , entrez le nombre de jours pour rechercher les doublons.</span><span class="sxs-lookup"><span data-stu-id="4429e-112">If **Interchange control number (UNB5)** is selected, in the **Check for duplicate UNB5 within** field, enter the number of days to check for a duplicate interchange.</span></span>  
  
5.  <span data-ttu-id="4429e-113">Sélectionnez **le numéro de contrôle de groupe (UNG5) dans l’échange** pour empêcher le pipeline de réception de traiter des groupes en double.</span><span class="sxs-lookup"><span data-stu-id="4429e-113">Select **Group control number (UNG5) in interchange** to prevent the receive pipeline from processing duplicate groups.</span></span>  
  
6.  <span data-ttu-id="4429e-114">Sélectionnez **contrôle numéro du document informatisé (UNH1) dans le groupe** pour empêcher le pipeline de réception à partir de traitement des transactions en double des jeux.</span><span class="sxs-lookup"><span data-stu-id="4429e-114">Select **Transaction Set Control Number (UNH1) in group** to prevent the receive pipeline from processing duplicate transaction sets.</span></span>  
  
7.  <span data-ttu-id="4429e-115">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="4429e-115">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4429e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4429e-116">See Also</span></span>  
 [<span data-ttu-id="4429e-117">Configuration des propriétés de l’accord de secours EDIFACT pour le traitement des échanges</span><span class="sxs-lookup"><span data-stu-id="4429e-117">Configuring EDIFACT Fallback Agreement Properties for Interchange Processing</span></span>](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)