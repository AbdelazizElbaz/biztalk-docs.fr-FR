---
title: "Configuration d’enveloppes (paramètres X12-Transaction) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9313a7b9-72fa-4071-8c65-007371643179
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 519062fa4647cdc2c7c39dda19373ff888eaf601
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-envelopes-x12-transaction-set-settings"></a><span data-ttu-id="7f01e-102">Configuration des enveloppes (X12 - Paramètres de documents informatisés)</span><span class="sxs-lookup"><span data-stu-id="7f01e-102">Configuring Envelopes (X12-Transaction Set Settings)</span></span>
<span data-ttu-id="7f01e-103">Dans le **enveloppes** page de la **paramètres des documents informatisés** section, vous définissez la façon dont BizTalk Server génère les segments GS et ST pour un échange codé X12 qu’elle envoie au tiers.</span><span class="sxs-lookup"><span data-stu-id="7f01e-103">In the **Envelops** page of the **Transaction Set Settings** section, you define how BizTalk Server generates the GS and ST segments for an X12-encoded interchange that it sends to the party.</span></span> <span data-ttu-id="7f01e-104">Un segment GS identifie et spécifie un groupe fonctionnel pour un échange X12.</span><span class="sxs-lookup"><span data-stu-id="7f01e-104">A GS segment identifies and specifies a functional group for an X12-encoded interchange.</span></span> <span data-ttu-id="7f01e-105">Un segment ST est l'en-tête de message d'un échange X12.</span><span class="sxs-lookup"><span data-stu-id="7f01e-105">An ST segment is the message header for an X12-encoded interchange.</span></span>  
  
 <span data-ttu-id="7f01e-106">Dans cette page, vous associez les valeurs de la **GS1**, **GS2**, **GS3**, **GS4**, **GS5**, **GS7**, et **GS8** des éléments de données avec des valeurs de la **Type de Transaction**, **Version/publication**, et **cible espace de noms** des éléments de données.</span><span class="sxs-lookup"><span data-stu-id="7f01e-106">In this page, you associate values of the **GS1**, **GS2**, **GS3**, **GS4**, **GS5**, **GS7**, and **GS8** data elements with values of the **Transaction Type**, **Version/Release**, and **Target namespace** data elements.</span></span> <span data-ttu-id="7f01e-107">Lorsque BizTalk détermine qu’un message XML BizTalk les valeurs définies pour le **Type de Transaction**, **Version/publication**, et **espace de noms cible** éléments d’une ligne de la grille, Il renseigne le **GS1**, **GS2**, **GS3**, **GS4**, **GS5**, **GS7**, et **GS8** des éléments de données dans l’enveloppe de la sortie de l’échange avec les valeurs de la même ligne de la grille.</span><span class="sxs-lookup"><span data-stu-id="7f01e-107">When BizTalk determines that a BizTalk XML message has the values set for the **Transaction Type**, **Version/Release**, and **Target namespace** elements in a row of the grid, BizTalk will populate the **GS1**, **GS2**, **GS3**, **GS4**, **GS5**, **GS7**, and **GS8** data elements in the envelope of the outgoing interchange with the values from the same row of the grid.</span></span> <span data-ttu-id="7f01e-108">Les valeurs de la **Type de Transaction**, **Version/publication**, et **espace de noms cible** éléments doivent être uniques.</span><span class="sxs-lookup"><span data-stu-id="7f01e-108">The values of the **Transaction Type**, **Version/Release**, and **Target namespace** elements must be unique.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f01e-109">Si vous entrez une valeur pour n'importe quel champ de la grille, puis que vous la supprimez, vous devrez supprimer l'ensemble de la ligne, sinon la validation de la page échouera.</span><span class="sxs-lookup"><span data-stu-id="7f01e-109">If you enter a setting for any of the fields in the grid, and then delete that setting, you will have to delete the entire row or the page will fail validation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f01e-110">Cette rubrique s'applique également aux paramètres liés à HIPAA.</span><span class="sxs-lookup"><span data-stu-id="7f01e-110">This topic applies also to HIPAA-related settings.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7f01e-111">Toutes les propriétés sont désactivées sur **tiers A -> tiers B** onglet d’accord unidirectionnel si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** vérifier boîte pour tiers A. Toutefois, toutes les propriétés sont activées sur la même page dans le **tiers B -> tiers A** onglet si vous avez sélectionné la case à cocher lors de la création du tiers A.</span><span class="sxs-lookup"><span data-stu-id="7f01e-111">All properties are disabled on **Party A->Party B** one-way agreement tab if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box for Party A. However, all the properties are enabled on the same page in the **Party B->Party A** tab if you selected the check box while creating Party A.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7f01e-112">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="7f01e-112">Prerequisites</span></span>  
 <span data-ttu-id="7f01e-113">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7f01e-113">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-define-the-gs-and-st-segments"></a><span data-ttu-id="7f01e-114">Pour définir les segments GS et ST</span><span class="sxs-lookup"><span data-stu-id="7f01e-114">To define the GS and ST segments</span></span>  
  
1.  <span data-ttu-id="7f01e-115">Créer un accord sur comme décrit dans le codage de X12 [configuration des paramètres généraux (X12)](../core/configuring-general-settings-x12.md).</span><span class="sxs-lookup"><span data-stu-id="7f01e-115">Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md).</span></span> <span data-ttu-id="7f01e-116">Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7f01e-116">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="7f01e-117">Sous l’onglet accord unidirectionnel, sous **paramètres des documents informatisés** , cliquez sur **enveloppes**.</span><span class="sxs-lookup"><span data-stu-id="7f01e-117">On a one-way agreement tab, under **Transaction Set Settings** section, click **Envelopes**.</span></span>  
  
3.  <span data-ttu-id="7f01e-118">Dans une ligne de la grille, entrez les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="7f01e-118">In a row of the grid, enter the following:</span></span>  
  
    -   <span data-ttu-id="7f01e-119">Pour le **Type de Transaction** , sélectionnez une valeur pour le code d’identificateur de document informatisé dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="7f01e-119">For the **Transaction Type** field, select a value for the transaction set identifier code from the drop-down list.</span></span>  
  
    -   <span data-ttu-id="7f01e-120">Pour **Version/publication**, entrez une valeur alphanumérique comportant un caractère au minimum et un maximum de 12 caractères.</span><span class="sxs-lookup"><span data-stu-id="7f01e-120">For **Version/Release**, enter an alphanumeric value with a minimum of one character and a maximum of 12 characters.</span></span>  
  
    -   <span data-ttu-id="7f01e-121">Pour **espace de noms cible** éléments, sélectionnez une valeur dans la liste déroulante ou entrez un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="7f01e-121">For **Target namespace** elements, select a value from the drop-down list, or enter a namespace.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="7f01e-122">BizTalk Server compare ces valeurs à celles associées à l'échange qu'il crée.</span><span class="sxs-lookup"><span data-stu-id="7f01e-122">These will be the values that BizTalk Server will compare with the values associated with the interchange it is building.</span></span>  
  
4.  <span data-ttu-id="7f01e-123">Dans la même ligne de la grille, entrez les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="7f01e-123">In the same row of the grid, enter the following:</span></span>  
  
    -   <span data-ttu-id="7f01e-124">Pour **GS1**, sélectionnez une valeur pour le code fonctionnel dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="7f01e-124">For **GS1**, select a value for the functional code from the drop-down list.</span></span> <span data-ttu-id="7f01e-125">Il s’agit d’un champ facultatif.</span><span class="sxs-lookup"><span data-stu-id="7f01e-125">This is an optional field.</span></span>  
  
    -   <span data-ttu-id="7f01e-126">Pour **GS2**, entrez une valeur alphanumérique pour l’application émettrice comportant deux caractères au minimum et un maximum de 15 caractères.</span><span class="sxs-lookup"><span data-stu-id="7f01e-126">For **GS2**, enter an alphanumeric value for the application sender with a minimum of two characters and a maximum of 15 characters.</span></span> <span data-ttu-id="7f01e-127">Ce champ est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="7f01e-127">This is a required field.</span></span>  
  
    -   <span data-ttu-id="7f01e-128">Pour **GS3**, entrez une valeur alphanumérique pour l’application réceptrice avec un minimum de deux caractères et un maximum de 15 caractères.</span><span class="sxs-lookup"><span data-stu-id="7f01e-128">For **GS3**, enter an alphanumeric value for the application receiver with a minimum of two characters and a maximum of 15 characters.</span></span> <span data-ttu-id="7f01e-129">Ce champ est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="7f01e-129">This is a required field.</span></span>  
  
    -   <span data-ttu-id="7f01e-130">Pour **GS4**, sélectionnez **SSAAMMJJ** ou **aammjj**.</span><span class="sxs-lookup"><span data-stu-id="7f01e-130">For **GS4**, select **CCYYMMDD** or **YYMMDD**.</span></span> <span data-ttu-id="7f01e-131">Il s’agit d’un champ facultatif</span><span class="sxs-lookup"><span data-stu-id="7f01e-131">This is an optional field</span></span>  
  
    -   <span data-ttu-id="7f01e-132">Pour **GS5**, sélectionnez **HHMM**, **HHMMSS**, ou **HHMMSSdd**.</span><span class="sxs-lookup"><span data-stu-id="7f01e-132">For **GS5**, select **HHMM**, **HHMMSS**, or **HHMMSSdd**.</span></span> <span data-ttu-id="7f01e-133">Il s’agit d’un champ facultatif</span><span class="sxs-lookup"><span data-stu-id="7f01e-133">This is an optional field</span></span>  
  
    -   <span data-ttu-id="7f01e-134">Pour **GS7**, sélectionnez une valeur pour l’entité responsable dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="7f01e-134">For **GS7**, select a value for the responsible agency from the drop-down list.</span></span> <span data-ttu-id="7f01e-135">Il s’agit d’un champ facultatif.</span><span class="sxs-lookup"><span data-stu-id="7f01e-135">This is an optional field.</span></span>  
  
    -   <span data-ttu-id="7f01e-136">Pour **GS8**, entrez une valeur alphanumérique pour le document identifié avec un caractère au minimum et un maximum de 12 caractères.</span><span class="sxs-lookup"><span data-stu-id="7f01e-136">For **GS8**, enter an alphanumeric value for the document identified with a minimum of one character and a maximum of 12 characters.</span></span> <span data-ttu-id="7f01e-137">Il s’agit d’un champ facultatif.</span><span class="sxs-lookup"><span data-stu-id="7f01e-137">This is an optional field.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="7f01e-138">Ils vous seront les valeurs que BizTalk Server entre dans les champs GS de l’échange qu’il crée si les **Type de Transaction**, **Version/publication**, et **d’espacedenomscible**dans la même ligne, les éléments sont correspondent à ceux associés à l’échange.</span><span class="sxs-lookup"><span data-stu-id="7f01e-138">These will be the values that BizTalk Server will enter in the GS fields of the interchange it is building if the **Transaction Type**, **Version/Release**, and **Target namespace** elements in the same row are a match for those associated with the interchange.</span></span>  
  
5.  <span data-ttu-id="7f01e-139">Répétez les étapes 3 et 4 pour entrer des lignes supplémentaires dans la grille.</span><span class="sxs-lookup"><span data-stu-id="7f01e-139">Repeat steps 3 and 4 to enter additional rows into the grid.</span></span>  
  
6.  <span data-ttu-id="7f01e-140">Pour une ligne dans la grille, cliquez sur **par défaut** pour désigner la ligne par défaut.</span><span class="sxs-lookup"><span data-stu-id="7f01e-140">For one row in the grid, click **Default** to designate it as the default row.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7f01e-141">Si un message n’a pas de correspondance avec la **Type de Transaction**, **Version/publication**, et **espace de noms cible** éléments dans n’importe quelle ligne, BizTalk Server attribue au message avec les valeurs pour le **GS1**, **GS2**, **GS3**, **GS5**, **GS7**et **GS8** éléments de la ligne par défaut.</span><span class="sxs-lookup"><span data-stu-id="7f01e-141">If a message does not have a match with the **Transaction Type**, **Version/Release**, and **Target namespace** elements in any row, BizTalk Server will populate the message with the values for the **GS1**, **GS2**, **GS3**, **GS5**, **GS7**, and **GS8** elements in the default row.</span></span> <span data-ttu-id="7f01e-142">Ces valeurs sont utilisées même si le message n’a pas de correspondance avec la **Type de Transaction**, **Version/publication**, et **espace de noms cible** les éléments de la ligne par défaut.</span><span class="sxs-lookup"><span data-stu-id="7f01e-142">These values will be used even if the message does not have a match with the **Transaction Type**, **Version/Release**, and **Target namespace** elements of the default row.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7f01e-143">Si aucune valeur par défaut n’est sélectionnées, les documents entrants ne correspondant pas à la **Type de Transaction**, **Version/publication**, et **espace de noms cible** éléments des lignes seront suspendus. .</span><span class="sxs-lookup"><span data-stu-id="7f01e-143">If no default is selected, incoming documents that do not match the **Transaction Type**, **Version/Release**, and **Target namespace** elements of any rows will be suspended.</span></span>  
  
7.  <span data-ttu-id="7f01e-144">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="7f01e-144">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f01e-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f01e-145">See Also</span></span>  
 [<span data-ttu-id="7f01e-146">Configuration des paramètres (X12) documents informatisés</span><span class="sxs-lookup"><span data-stu-id="7f01e-146">Configuring Transaction Set Settings (X12)</span></span>](../core/configuring-transaction-set-settings-x12.md)