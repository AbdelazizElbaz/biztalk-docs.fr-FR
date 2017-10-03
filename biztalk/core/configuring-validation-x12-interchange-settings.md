---
title: "Configuration de la Validation (paramètres d’échange X12) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fdad7016-1d66-4d11-b620-c28368f00133
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0edfe66791fa5c041c66a3adddde61730afe54ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-validation-x12-interchange-settings"></a><span data-ttu-id="f114f-102">Configuration de la validation (Paramètres d'échange X12)</span><span class="sxs-lookup"><span data-stu-id="f114f-102">Configuring Validation (X12-Interchange Settings)</span></span>
<span data-ttu-id="f114f-103">Les paramètres de génération et de validation d'un échange X12 définissent la manière dont [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vérifie l'existence de numéros de contrôle dupliqués dans l'échange reçu.</span><span class="sxs-lookup"><span data-stu-id="f114f-103">X12 interchange validation generation settings define how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] checks for duplicate control numbers in the received interchange.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f114f-104">Les paramètres décrits dans cette rubrique s'appliquent également à la validation de l'échange HIPAA.</span><span class="sxs-lookup"><span data-stu-id="f114f-104">The settings described here also apply to HIPAA interchange validation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f114f-105">Aucuns propriétés ne sont désactivées dans cette page, même si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.</span><span class="sxs-lookup"><span data-stu-id="f114f-105">No properties are disabled on this page even if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f114f-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f114f-106">Prerequisites</span></span>  
 <span data-ttu-id="f114f-107">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f114f-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-validation"></a><span data-ttu-id="f114f-108">Pour configurer la validation</span><span class="sxs-lookup"><span data-stu-id="f114f-108">To configure validation</span></span>  
  
1.  <span data-ttu-id="f114f-109">Créer un accord sur comme décrit dans le codage de X12 [configuration des paramètres généraux (X12)](../core/configuring-general-settings-x12.md).</span><span class="sxs-lookup"><span data-stu-id="f114f-109">Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md).</span></span> <span data-ttu-id="f114f-110">Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f114f-110">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="f114f-111">Sous l’onglet accord unidirectionnel, sous **paramètres de l’échange** , cliquez sur **Validation**.</span><span class="sxs-lookup"><span data-stu-id="f114f-111">On a one-way agreement tab, under **Interchange Settings** section, click **Validation**.</span></span>  
  
3.  <span data-ttu-id="f114f-112">Sélectionnez le **numéro de contrôle de l’échange** case à cocher pour activer le pipeline de réception bloquer les échanges en double.</span><span class="sxs-lookup"><span data-stu-id="f114f-112">Select the **Interchange Control Number** check box to enable the receive pipeline to block duplicate interchanges.</span></span> <span data-ttu-id="f114f-113">Lorsque cette option est activée, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vérifie que le numéro de contrôle (ISA13) de l'échange reçu ne correspond pas au numéro de contrôle de l'échange.</span><span class="sxs-lookup"><span data-stu-id="f114f-113">If selected, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will check that the interchange control number (ISA13) for the received interchange does not match the interchange control number.</span></span> <span data-ttu-id="f114f-114">Si le serveur détecte des doublons, le pipeline de réception ne traite pas l'échange.</span><span class="sxs-lookup"><span data-stu-id="f114f-114">If a match is detected, the receive pipeline will not process the interchange.</span></span>  
  
4.  <span data-ttu-id="f114f-115">Si **numéro de contrôle d’échange** est sélectionné, dans le **chercher isa13 en double dans** , entrez le nombre de jours pendant lesquels la vérification d’un échange en double sera effectuée à l’aide d’un spécifique numéro de contrôle d’échange.</span><span class="sxs-lookup"><span data-stu-id="f114f-115">If **Interchange Control Number** is selected, in the **Check for duplicate ISA13 within** field, enter the number of days that a check for a duplicate interchange will be performed using a specific interchange control number.</span></span>  
  
5.  <span data-ttu-id="f114f-116">Sélectionnez **numéro de contrôle du groupe** pour empêcher le pipeline de réception de traiter les échanges avec des numéros de contrôle de groupe dupliqués (GS6).</span><span class="sxs-lookup"><span data-stu-id="f114f-116">Select **Group Control Number** to prevent the receive pipeline from processing interchanges with duplicate group control numbers (GS6).</span></span>  
  
6.  <span data-ttu-id="f114f-117">Sélectionnez **numéro de contrôle de document informatisé** pour empêcher le pipeline de réception de traiter les échanges avec des numéros de contrôle du document informatisé en double (ST2).</span><span class="sxs-lookup"><span data-stu-id="f114f-117">Select **Transaction Set Control Number** to prevent the receive pipeline from processing interchanges with duplicate transaction set control numbers (ST2).</span></span>  
  
7.  <span data-ttu-id="f114f-118">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="f114f-118">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f114f-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f114f-119">See Also</span></span>  
 [<span data-ttu-id="f114f-120">Configuration des paramètres d’échange (X12)</span><span class="sxs-lookup"><span data-stu-id="f114f-120">Configuring Interchange Settings (X12)</span></span>](../core/configuring-interchange-settings-x12.md)