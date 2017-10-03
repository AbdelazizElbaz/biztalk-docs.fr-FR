---
title: "Configuration des propriétés de Validation de secours (X12) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a64431d-373a-4d63-9b83-cbb323620152
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc6eb44f2ee4c2f9c63011dc14be41380c245996
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-validation-properties-x12"></a><span data-ttu-id="22b1b-102">Configuration des propriétés de validation de secours (X12)</span><span class="sxs-lookup"><span data-stu-id="22b1b-102">Configuring Fallback Validation Properties (X12)</span></span>
<span data-ttu-id="22b1b-103">Les paramètres de secours de génération et de validation d'un échange X12 définissent la manière dont [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vérifie l'existence de numéros de contrôle dupliqués dans l'échange reçu.</span><span class="sxs-lookup"><span data-stu-id="22b1b-103">X12 interchange validation generation fallback settings define how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] checks for duplicate control numbers in the received interchange.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22b1b-104">Les paramètres décrits dans cette rubrique s'appliquent également à la validation de l'échange HIPAA.</span><span class="sxs-lookup"><span data-stu-id="22b1b-104">The settings described here also apply to HIPAA interchange validation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="22b1b-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="22b1b-105">Prerequisites</span></span>  
 <span data-ttu-id="22b1b-106">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="22b1b-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-validation"></a><span data-ttu-id="22b1b-107">Pour configurer la validation</span><span class="sxs-lookup"><span data-stu-id="22b1b-107">To configure validation</span></span>  
  
1.  <span data-ttu-id="22b1b-108">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **X12 paramètres de secours**.</span><span class="sxs-lookup"><span data-stu-id="22b1b-108">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **X12 Fallback Settings**.</span></span>  
  
2.  <span data-ttu-id="22b1b-109">Dans le **X12 paramètres de secours** boîte de dialogue le **X12 page accords** sous l’onglet sous la **paramètres de l’échange** , cliquez sur **Validation**.</span><span class="sxs-lookup"><span data-stu-id="22b1b-109">In the **X12 Fallback Settings** dialog box, in the **X12 Agreement Pages** tab, under the **Interchange Settings** section, click **Validation**.</span></span>  
  
3.  <span data-ttu-id="22b1b-110">Sélectionnez le **numéro de contrôle de l’échange** case à cocher pour activer le pipeline de réception bloquer les échanges en double.</span><span class="sxs-lookup"><span data-stu-id="22b1b-110">Select the **Interchange Control Number** check box to enable the receive pipeline to block duplicate interchanges.</span></span> <span data-ttu-id="22b1b-111">Lorsque cette option est activée, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vérifie que le numéro de contrôle (ISA13) de l'échange reçu ne correspond pas au numéro de contrôle de l'échange.</span><span class="sxs-lookup"><span data-stu-id="22b1b-111">If selected, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will check that the interchange control number (ISA13) for the received interchange does not match the interchange control number.</span></span> <span data-ttu-id="22b1b-112">Si le serveur détecte des doublons, le pipeline de réception ne traite pas l'échange.</span><span class="sxs-lookup"><span data-stu-id="22b1b-112">If a match is detected, the receive pipeline will not process the interchange.</span></span>  
  
4.  <span data-ttu-id="22b1b-113">Si **numéro de contrôle d’échange** est sélectionné, dans le **chercher isa13 en double dans** , entrez le nombre de jours pendant lesquels la vérification d’un échange en double sera effectuée à l’aide d’un spécifique numéro de contrôle d’échange.</span><span class="sxs-lookup"><span data-stu-id="22b1b-113">If **Interchange Control Number** is selected, in the **Check for duplicate ISA13 within** field, enter the number of days that a check for a duplicate interchange will be performed using a specific interchange control number.</span></span>  
  
5.  <span data-ttu-id="22b1b-114">Sélectionnez **numéro de contrôle du groupe** pour empêcher le pipeline de réception de traiter les échanges avec des numéros de contrôle de groupe dupliqués (GS6).</span><span class="sxs-lookup"><span data-stu-id="22b1b-114">Select **Group Control Number** to prevent the receive pipeline from processing interchanges with duplicate group control numbers (GS6).</span></span>  
  
6.  <span data-ttu-id="22b1b-115">Sélectionnez **numéro de contrôle de document informatisé** pour empêcher le pipeline de réception de traiter les échanges avec des numéros de contrôle du document informatisé en double (ST2).</span><span class="sxs-lookup"><span data-stu-id="22b1b-115">Select **Transaction Set Control Number** to prevent the receive pipeline from processing interchanges with duplicate transaction set control numbers (ST2).</span></span>  
  
7.  <span data-ttu-id="22b1b-116">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="22b1b-116">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22b1b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22b1b-117">See Also</span></span>  
 [<span data-ttu-id="22b1b-118">Configuration X12 propriétés d’accord de secours pour le traitement de l’échange</span><span class="sxs-lookup"><span data-stu-id="22b1b-118">Configuring X12 Fallback Agreement Properties for Interchange Processing</span></span>](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)