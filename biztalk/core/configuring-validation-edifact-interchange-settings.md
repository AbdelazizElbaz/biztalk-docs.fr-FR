---
title: "Configuration de la Validation (paramètres d’échange EDIFACT) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55820ebc-fe21-48a3-8985-1bf4184176ac
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f87e762177e2938deaa957035e255af3f0d40eab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-validation-edifact-interchange-settings"></a><span data-ttu-id="6cfca-102">Configuration de la validation (paramètres d'échange EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="6cfca-102">Configuring Validation (EDIFACT-Interchange Settings)</span></span>
<span data-ttu-id="6cfca-103">Les instructions de cette section décrivent comment empêcher le traitement des numéros de contrôle en double.</span><span class="sxs-lookup"><span data-stu-id="6cfca-103">This section provides instructions on how to prevent duplicate control numbers from being processed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6cfca-104">Aucuns propriétés ne sont désactivées dans cette page, même si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.</span><span class="sxs-lookup"><span data-stu-id="6cfca-104">No properties are disabled on this page even if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6cfca-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="6cfca-105">Prerequisites</span></span>  
 <span data-ttu-id="6cfca-106">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6cfca-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-duplicate-validation"></a><span data-ttu-id="6cfca-107">Pour configurer la validation des doublons</span><span class="sxs-lookup"><span data-stu-id="6cfca-107">To configure duplicate validation</span></span>  
  
1.  <span data-ttu-id="6cfca-108">Créer un accord le codage comme décrit dans EDIFACT, [paramètres généraux configuration (EDIFACT)](../core/configuring-general-settings-edifact.md).</span><span class="sxs-lookup"><span data-stu-id="6cfca-108">Create an EDIFACT encoding agreement as described in [Configuring General Settings (EDIFACT)](../core/configuring-general-settings-edifact.md).</span></span> <span data-ttu-id="6cfca-109">Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="6cfca-109">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="6cfca-110">Sous l’onglet accord unidirectionnel, sous **paramètres de l’échange** , cliquez sur **Validation**.</span><span class="sxs-lookup"><span data-stu-id="6cfca-110">On a one-way agreement tab, under **Interchange Settings** section, click **Validation**.</span></span>  
  
3.  <span data-ttu-id="6cfca-111">Sélectionnez le **numéro de contrôle d’échange (UNB5)** case à cocher pour activer le pipeline de réception bloquer les échanges en double.</span><span class="sxs-lookup"><span data-stu-id="6cfca-111">Select the **Interchange control number (UNB5)** check box to enable the receive pipeline to block duplicate interchanges.</span></span> <span data-ttu-id="6cfca-112">Lorsque cette option est activée, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vérifie que le numéro de contrôle de l'échange reçu ne correspond pas au numéro de contrôle d'un autre échange reçu.</span><span class="sxs-lookup"><span data-stu-id="6cfca-112">If selected, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will check that the interchange control number for the received interchange does not match the interchange control number of another received interchange.</span></span> <span data-ttu-id="6cfca-113">Si le serveur détecte des doublons, le pipeline de réception ne traite pas l'échange.</span><span class="sxs-lookup"><span data-stu-id="6cfca-113">If a match is detected, the receive pipeline will not process the interchange.</span></span>  
  
4.  <span data-ttu-id="6cfca-114">Si **numéro de contrôle d’échange (UNB5)** est sélectionné, dans le **vérifier les doublons UNB5 dans** , entrez le nombre de jours pour rechercher les doublons.</span><span class="sxs-lookup"><span data-stu-id="6cfca-114">If **Interchange control number (UNB5)** is selected, in the **Check for duplicate UNB5 within** field, enter the number of days to check for a duplicate interchange.</span></span>  
  
5.  <span data-ttu-id="6cfca-115">Sélectionnez **le numéro de contrôle de groupe (UNG5) dans l’échange** pour empêcher le pipeline de réception de traiter des groupes en double.</span><span class="sxs-lookup"><span data-stu-id="6cfca-115">Select **Group control number (UNG5) in interchange** to prevent the receive pipeline from processing duplicate groups.</span></span>  
  
6.  <span data-ttu-id="6cfca-116">Sélectionnez **contrôle numéro du document informatisé (UNH1) dans le groupe** pour empêcher le pipeline de réception à partir de traitement des transactions en double des jeux.</span><span class="sxs-lookup"><span data-stu-id="6cfca-116">Select **Transaction Set Control Number (UNH1) in group** to prevent the receive pipeline from processing duplicate transaction sets.</span></span>  
  
7.  <span data-ttu-id="6cfca-117">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6cfca-117">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cfca-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6cfca-118">See Also</span></span>  
 [<span data-ttu-id="6cfca-119">Configuration des paramètres d’échange (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="6cfca-119">Configuring Interchange Settings (EDIFACT)</span></span>](../core/configuring-interchange-settings-edifact.md)