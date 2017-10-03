---
title: Gestion des traitements | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82755840-4e00-4fed-80e0-1a22b248c0bf
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4903cf2722f1938ceb1df92c2a3ac2a88fe6d61e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-batches"></a><span data-ttu-id="b1b35-102">Gestion des traitements</span><span class="sxs-lookup"><span data-stu-id="b1b35-102">Managing Batches</span></span>
<span data-ttu-id="b1b35-103">Comment contrôler manuellement la version de traités par lot des échanges, à l’aide de contrôles en haut de la **Configuration de lot** page de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue (dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’administration) pour X12 et le codage EDIFACT.</span><span class="sxs-lookup"><span data-stu-id="b1b35-103">How to control manually the release of batched interchanges, using the controls at the top of the **Batch Configuration** page of the one-way agreement tab of the **Agreement Properties** dialog box (in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console) for both X12 and EDIFACT encoding.</span></span> <span data-ttu-id="b1b35-104">Cette opération implique les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="b1b35-104">This involves the following controls:</span></span>  
  
-   <span data-ttu-id="b1b35-105">**Démarrage d’un lot**.</span><span class="sxs-lookup"><span data-stu-id="b1b35-105">**Starting a batch**.</span></span> <span data-ttu-id="b1b35-106">Active une instance de l’orchestration de traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="b1b35-106">Activates an instance of the batching orchestration.</span></span> <span data-ttu-id="b1b35-107">Après avoir sélectionné le **Démarrer** bouton, les éléments de traitement par lot sont collectés lorsque l’instance est dans la plage d’activation.</span><span class="sxs-lookup"><span data-stu-id="b1b35-107">After you select the **Start** button, batching elements are collected when the instance is within the activation range.</span></span>  
  
-   <span data-ttu-id="b1b35-108">**Remplacement d’un lot**.</span><span class="sxs-lookup"><span data-stu-id="b1b35-108">**Overriding a batch**.</span></span> <span data-ttu-id="b1b35-109">Crée un lot à l’aide des éléments existants qu’il envoie immédiatement.</span><span class="sxs-lookup"><span data-stu-id="b1b35-109">Creates a batch using existing elements and immediately sends it.</span></span> <span data-ttu-id="b1b35-110">Une fois le lot envoyé, l'orchestration du traitement par lot reprend le traitement par lot conformément aux paramètres définis.</span><span class="sxs-lookup"><span data-stu-id="b1b35-110">After the batch is sent, the batching orchestration resumes batch processing according to the established settings.</span></span>  
  
-   <span data-ttu-id="b1b35-111">**Arrêt d’un lot**.</span><span class="sxs-lookup"><span data-stu-id="b1b35-111">**Stopping a batch**.</span></span> <span data-ttu-id="b1b35-112">Désactive une instance activée de l’orchestration de traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="b1b35-112">Deactivates an activated instance of the batching orchestration.</span></span> <span data-ttu-id="b1b35-113">Après avoir sélectionné le **arrêter** bouton, l’orchestration crée un lot à partir d’éléments de lot existants, transfert l’échange au pipeline d’envoi EDI et s’arrête.</span><span class="sxs-lookup"><span data-stu-id="b1b35-113">After you select the **Stop** button, the orchestration creates a batch from existing batch elements, delivers the interchange to the EDI send pipeline, and terminates.</span></span>  
  
 <span data-ttu-id="b1b35-114">Les commandes agissent sur une configuration du lot.</span><span class="sxs-lookup"><span data-stu-id="b1b35-114">The controls act upon a single batch configuration.</span></span>  
  
 <span data-ttu-id="b1b35-115">Les actions effectuées par BizTalk lorsque vous appuyez sur la **Démarrer** bouton dépendent les **filtre** critères, **version** critères, et **Activation**paramètres de plage sur le **Configuration de lot** page.</span><span class="sxs-lookup"><span data-stu-id="b1b35-115">The actions that BizTalk takes when you press the **Start** button depend upon the **Filter** criteria, **Release** criteria, and **Activation** range settings on the **Batch Configuration** page.</span></span> <span data-ttu-id="b1b35-116">Les critères de filtre déterminent les messages qui seront traités par lot.</span><span class="sxs-lookup"><span data-stu-id="b1b35-116">The filter criteria determine which messages are batched.</span></span> <span data-ttu-id="b1b35-117">Les critères de déclenchement déterminent les moments d'exécution des lots.</span><span class="sxs-lookup"><span data-stu-id="b1b35-117">The release criteria determine when batches are released.</span></span> <span data-ttu-id="b1b35-118">Les propriétés des plages d'activation déterminent si une instance activée de l'orchestration de traitement par lot recueillera des éléments pour le traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="b1b35-118">The activation range properties determine whether an activated instance of the batching orchestration will collect elements for batching.</span></span> <span data-ttu-id="b1b35-119">Pour plus d’informations sur ces paramètres, consultez [configuration d’un lot sortant](../core/configuring-an-outgoing-batch.md).</span><span class="sxs-lookup"><span data-stu-id="b1b35-119">For more information about these settings, see [Configuring an Outgoing Batch](../core/configuring-an-outgoing-batch.md).</span></span>  

<span data-ttu-id="b1b35-120">Cette rubrique vous montre comment démarrer, arrêter, remplacer et supprimer des lots.</span><span class="sxs-lookup"><span data-stu-id="b1b35-120">This topic shows you how to start, stop, override, and delete batches.</span></span>  

> [!NOTE]
>  <span data-ttu-id="b1b35-121">Pour obtenir des instructions sur la configuration des lots, consultez [configuration X12 le traitement par lot](../core/configuring-batching-x12.md) ou [le traitement par lot EDIFACT configuration](../core/configuring-batching-edifact.md).</span><span class="sxs-lookup"><span data-stu-id="b1b35-121">For instructions on how to configure batches, see [Configuring X12 Batching](../core/configuring-batching-x12.md) or [Configuring EDIFACT Batching](../core/configuring-batching-edifact.md).</span></span> 
  
## <a name="prerequisites"></a><span data-ttu-id="b1b35-122">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="b1b35-122">Prerequisites</span></span>  
 <span data-ttu-id="b1b35-123">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b1b35-123">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1b35-124">Un membre du groupe d'opérateurs B2B [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut démarrer, arrêter ou remplacer un lot, mais ne peut pas modifier de paramètre de configuration associé au traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="b1b35-124">A member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group can start, stop, or override a batch, but cannot change any configuration setting related to batching.</span></span> <span data-ttu-id="b1b35-125">Vous devez être connecté en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour modifier la configuration du lot.</span><span class="sxs-lookup"><span data-stu-id="b1b35-125">You must be a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to change batch configuration.</span></span>  
  
## <a name="start-stop-and-override-batches"></a><span data-ttu-id="b1b35-126">Démarrer, arrêter et substituer des lots</span><span class="sxs-lookup"><span data-stu-id="b1b35-126">Start, stop, and override batches</span></span>  
  
1.  <span data-ttu-id="b1b35-127">Ouvrez  **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration**, développez le groupe BizTalk, puis sélectionnez **Parties**.</span><span class="sxs-lookup"><span data-stu-id="b1b35-127">Open **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration**, expand the BizTalk group, and select **Parties**.</span></span>  
  
2.  <span data-ttu-id="b1b35-128">Dans le **tiers et profils d’entreprise** sous le **accords** section, avec le bouton droit de l’accord avec la configuration du lot que vous souhaitez démarrer, arrêter ou remplacer.</span><span class="sxs-lookup"><span data-stu-id="b1b35-128">In the **Parties and Business Profiles** page, under the **Agreements** section, right-click the agreement with the batch configuration that you want to start, stop, or override.</span></span>  
  
3.  <span data-ttu-id="b1b35-129">Dans l’onglet d’accord unidirectionnel de la **propriétés de l’accord**, sélectionnez le **Configuration de lot** page.</span><span class="sxs-lookup"><span data-stu-id="b1b35-129">In the one-way agreement tab of the **Agreement Properties**, select the **Batch Configuration** page.</span></span>  
  
4.  <span data-ttu-id="b1b35-130">Sur le **Configuration de lot** , sélectionnez l’onglet correspondant au lot que vous souhaitez démarrer, arrêter ou remplacer.</span><span class="sxs-lookup"><span data-stu-id="b1b35-130">On the **Batch Configuration** page, select the tab for the batch that you want to start, stop, or override.</span></span>  
  
5.  <span data-ttu-id="b1b35-131">Vérifiez que les critères de filtre, les critères de déclenchement et les propriétés de plages d'activation sont tels qu'ils devraient être.</span><span class="sxs-lookup"><span data-stu-id="b1b35-131">Verify that the filter criteria, release criteria, and activation range properties are as they should be.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b1b35-132">Si vous êtes un membre de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe d’opérateurs, mais pas les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs, vous pouvez démarrer, arrêter ou remplacer des lots.</span><span class="sxs-lookup"><span data-stu-id="b1b35-132">If you are a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operators group, but not the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group, you can start, stop, or override batches.</span></span> <span data-ttu-id="b1b35-133">Toutefois, vous ne pouvez pas modifier les paramètres de configuration de lot.</span><span class="sxs-lookup"><span data-stu-id="b1b35-133">But, you cannot change batch configuration settings.</span></span> <span data-ttu-id="b1b35-134">Les paramètres sont visibles par vous, mais si vous modifiez un paramètre et sélectionnez **OK**, vous obtenez une erreur d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="b1b35-134">The settings are visible to you, but if you change a setting, and then select **OK**, you get a permissions error.</span></span>  
  
6.  <span data-ttu-id="b1b35-135">Si une instance de l’orchestration de traitement par lot n’a pas été activée, sélectionnez **Démarrer** pour activer une instance.</span><span class="sxs-lookup"><span data-stu-id="b1b35-135">If an instance of the batching orchestration has not been activated, select **Start** to activate an instance.</span></span>  
  
    > [!NOTE]
    >  - <span data-ttu-id="b1b35-136">Vous pouvez indiquer qu’une instance de l’orchestration de traitement par lot n’a pas été activée si le **Démarrer** bouton est activé, et **le traitement par lot n’est pas activé** s’affiche juste en dessous du **Démarrer** contrôle.</span><span class="sxs-lookup"><span data-stu-id="b1b35-136">You can tell that an instance of the batching orchestration has not been activated if the **Start** button is enabled, and **Batching is not activated** is displayed just beneath the **Start** control.</span></span>  
    >  - <span data-ttu-id="b1b35-137">Si vous avez cliqué sur le **Démarrer** bouton et une instance de l’orchestration de traitement par lot a été activée, mais Aucuns éléments ne sont collectés pour le lot, puis vérifiez que la valeur datetime dans le **Activation** zone de texte a été dépassé.</span><span class="sxs-lookup"><span data-stu-id="b1b35-137">If you have clicked the **Start** button, and an instance of the batching orchestration has been activated, but no elements are being collected for the batch, then verify that the datetime in the **Activation** text box has transpired.</span></span> <span data-ttu-id="b1b35-138">Si ce n’est pas le cas, le **Activation** date doit être définie à la date actuelle ou une version antérieure.</span><span class="sxs-lookup"><span data-stu-id="b1b35-138">If not, the **Activation** date must be set to the current date or earlier.</span></span>  
  
7.  <span data-ttu-id="b1b35-139">Pour envoyer un échange par lot lorsque les critères de déclenchement n’ont pas été remplies, sélectionnez **remplacer**.</span><span class="sxs-lookup"><span data-stu-id="b1b35-139">To send a batched interchange when the release criteria have not been met, select **Override**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b1b35-140">En sélectionnant **remplacer** aboutit à un échange par lot envoyé, mais n’affecte pas l’état d’activation de l’instance d’orchestration de traitement par lot, les critères d’activation ou les critères de déclenchement.</span><span class="sxs-lookup"><span data-stu-id="b1b35-140">Selecting **Override** results in a batched interchange being sent, but does not affect the activation status of the batching orchestration instance, the activation criteria, or the release criteria.</span></span>  
  
8.  <span data-ttu-id="b1b35-141">Pour désactiver l’instance de l’orchestration de traitement par lot, sélectionnez **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="b1b35-141">To deactivate the instance of the batching orchestration, select **Stop**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b1b35-142">En sélectionnant **arrêter** provoque un échange par lot envoyé et l’instance d’orchestration par lot en cours d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="b1b35-142">Selecting **Stop** results in a batched interchange being sent, and the batching orchestration instance being terminated.</span></span>  
  
9. <span data-ttu-id="b1b35-143">Sélectionnez **OK** ou **Annuler** pour fermer la **propriétés de l’accord**.</span><span class="sxs-lookup"><span data-stu-id="b1b35-143">Select **OK** or **Cancel** to close the **Agreement Properties**.</span></span>  

## <a name="delete-batches"></a><span data-ttu-id="b1b35-144">Supprimer des lots</span><span class="sxs-lookup"><span data-stu-id="b1b35-144">Delete batches</span></span>  
  
1.  <span data-ttu-id="b1b35-145">Dans  **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration**, sélectionnez **Parties**.</span><span class="sxs-lookup"><span data-stu-id="b1b35-145">In **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration**, select **Parties**.</span></span>  
  
2.  <span data-ttu-id="b1b35-146">Dans le **tiers et profils d’entreprise** sous le **accords** section, avec le bouton droit de l’accord avec la configuration du lot que vous souhaitez supprimer.</span><span class="sxs-lookup"><span data-stu-id="b1b35-146">In the **Parties and Business Profiles** page, under the **Agreements** section, right-click the agreement with the batch configuration that you want to delete.</span></span>  
  
3.  <span data-ttu-id="b1b35-147">Dans l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue, sélectionnez le **Configuration de lot** page.</span><span class="sxs-lookup"><span data-stu-id="b1b35-147">In the one-way agreement tab of the **Agreement Properties** dialog box, select the **Batch Configuration** page.</span></span>  
  
4.  <span data-ttu-id="b1b35-148">Sur le **Configuration de lot** , sélectionnez l’onglet correspondant au lot que vous souhaitez supprimer.</span><span class="sxs-lookup"><span data-stu-id="b1b35-148">On the **Batch Configuration** page, select the tab for the batch that you want to delete.</span></span>  
  
5.  <span data-ttu-id="b1b35-149">Dans le coin droit de la page d’onglet, sélectionnez **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="b1b35-149">On the right-hand corner of the tab page, select **Delete**.</span></span>  
  
6.  <span data-ttu-id="b1b35-150">Sélectionnez **OK** pour fermer la **propriétés de l’accord**.</span><span class="sxs-lookup"><span data-stu-id="b1b35-150">Select **OK** to close the **Agreement Properties**.</span></span>  

  
## <a name="see-also"></a><span data-ttu-id="b1b35-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1b35-151">See Also</span></span>  
 [<span data-ttu-id="b1b35-152">Configuration d’un lot sortant</span><span class="sxs-lookup"><span data-stu-id="b1b35-152">Configuring an Outgoing Batch</span></span>](../core/configuring-an-outgoing-batch.md)  
 [<span data-ttu-id="b1b35-153">La gestion des Solutions EDI et AS2</span><span class="sxs-lookup"><span data-stu-id="b1b35-153">Managing EDI and AS2 Solutions</span></span>](../core/managing-edi-and-as2-solutions.md)