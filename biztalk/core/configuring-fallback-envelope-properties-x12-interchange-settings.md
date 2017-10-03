---
title: "Configuration des propriétés de l’enveloppe de secours (paramètres d’échange X12) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e9b05ea-2a0f-42d6-adc2-c1f1f2b7a993
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a2b0c43a43f5b003015378ecc52c05405877c5e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-envelope-properties-x12-interchange-settings"></a><span data-ttu-id="a5c90-102">Configuration des propriétés de l'enveloppe de secours (Paramètres d'échange X12)</span><span class="sxs-lookup"><span data-stu-id="a5c90-102">Configuring Fallback Envelope Properties (X12-Interchange Settings)</span></span>
<span data-ttu-id="a5c90-103">Les paramètres de génération de l'enveloppe de l'échange X12 définissent la façon dont [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] génère l'enveloppe d'un échange X12 à envoyer au tiers récepteur.</span><span class="sxs-lookup"><span data-stu-id="a5c90-103">X12 interchange envelope generation settings define how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generates the envelope of an X12-encoded interchange to be sent to the receiving party.</span></span> <span data-ttu-id="a5c90-104">Dans cet accord de secours, vous définissez la méthode utilisée par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour générer le segment ISA d'un échange X12 envoyé au tiers.</span><span class="sxs-lookup"><span data-stu-id="a5c90-104">In this fallback agreement, you define how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generates the ISA segment for an X12-encoded interchange that it sends to the party.</span></span> <span data-ttu-id="a5c90-105">Le segment ISA est l'en-tête de contrôle d'échange d'un échange X12.</span><span class="sxs-lookup"><span data-stu-id="a5c90-105">An ISA segment is the interchange control header for an X12-encoded interchange.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5c90-106">Pour le composant d'exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], la longueur des champs ISA alphanumériques est fixe.</span><span class="sxs-lookup"><span data-stu-id="a5c90-106">For the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime, the length of alphanumeric ISA fields is fixed.</span></span> <span data-ttu-id="a5c90-107">Toutefois, pour le [!INCLUDE[TPM](../includes/tpm-md.md)] l’interface utilisateur, vous pouvez entrer un caractère unique pour un champ ISA alphanumérique.</span><span class="sxs-lookup"><span data-stu-id="a5c90-107">However, for the [!INCLUDE[TPM](../includes/tpm-md.md)] user interface, you may enter a single character for an alphanumeric ISA field.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a5c90-108">remplira ces champs avec les espaces de fin pour assurer la conformité avec les exigences.</span><span class="sxs-lookup"><span data-stu-id="a5c90-108"> will pad these fields with trailing space characters to ensure compliance with standards requirements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5c90-109">Les paramètres décrits ici s'appliquent également à la génération de l'enveloppe de l'échange HIPAA.</span><span class="sxs-lookup"><span data-stu-id="a5c90-109">The settings described here also apply to HIPAA interchange envelope generation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a5c90-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="a5c90-110">Prerequisites</span></span>  
 <span data-ttu-id="a5c90-111">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5c90-111">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-define-the-envelope"></a><span data-ttu-id="a5c90-112">Pour définir l'enveloppe</span><span class="sxs-lookup"><span data-stu-id="a5c90-112">To define the envelope</span></span>  
  
1.  <span data-ttu-id="a5c90-113">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **X12 paramètres de secours**.</span><span class="sxs-lookup"><span data-stu-id="a5c90-113">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **X12 Fallback Settings**.</span></span>  
  
2.  <span data-ttu-id="a5c90-114">Dans le **X12 paramètres de secours** boîte de dialogue le **X12 page accords** sous l’onglet sous la **paramètres de l’échange** , cliquez sur **enveloppes**.</span><span class="sxs-lookup"><span data-stu-id="a5c90-114">In the **X12 Fallback Settings** dialog box, in the **X12 Agreement Pages** tab, under the **Interchange Settings** section, click **Envelopes**.</span></span>  
  
3.  <span data-ttu-id="a5c90-115">Sous **d’ISA11**, conserver **identificateur Standard** sélectionné pour spécifier un identificateur standard au lieu d’un séparateur de répétition, puis sélectionnez une valeur pour l’identificateur standard dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="a5c90-115">Under **ISA11 usage**, keep **Standard identifier** selected to specify a standard identifier instead of a repetition separator, and then select a value for the standard identifier from the drop-down list.</span></span> <span data-ttu-id="a5c90-116">Sélectionnez **séparateur de répétition** pour spécifier un séparateur de répétition au lieu d’un identificateur standard, puis entrez un caractère unique pour le séparateur de répétition.</span><span class="sxs-lookup"><span data-stu-id="a5c90-116">Select **Repetition separator** to specify a repetition separator instead of a standard identifier, and then enter a single character for the repetition separator.</span></span> <span data-ttu-id="a5c90-117">Le séparateur de répétition, qui permet de séparer les segments qui se répètent dans un document informatisé, est limité aux valeurs du jeu de caractères ASCII.</span><span class="sxs-lookup"><span data-stu-id="a5c90-117">The repetition separator, which is used to separate segments that repeat within a transaction set, is limited to the values in the ASCII character set.</span></span>  
  
4.  <span data-ttu-id="a5c90-118">Pour **contrôler le numéro de version (ISA12)**, sélectionnez la version de la X12 standard à utiliser par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour générer un échange sortant.</span><span class="sxs-lookup"><span data-stu-id="a5c90-118">For **Control version number (ISA12)**, select the version of the X12 standard to be used by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for generating an outgoing interchange.</span></span>  
  
5.  <span data-ttu-id="a5c90-119">Pour **l’indicateur d’utilisation (ISA15)**, sélectionnez cette option pour indiquer si un échange généré par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contient des informations, les données de production, ou des données de test.</span><span class="sxs-lookup"><span data-stu-id="a5c90-119">For **Usage indicator (ISA15)**, select to indicate whether an interchange generated by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is information, production data, or test data.</span></span>  
  
6.  <span data-ttu-id="a5c90-120">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="a5c90-120">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5c90-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5c90-121">See Also</span></span>  
 [<span data-ttu-id="a5c90-122">Configuration X12 propriétés d’accord de secours pour le traitement de l’échange</span><span class="sxs-lookup"><span data-stu-id="a5c90-122">Configuring X12 Fallback Agreement Properties for Interchange Processing</span></span>](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)