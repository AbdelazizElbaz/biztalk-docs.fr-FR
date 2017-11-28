---
title: "Comment : implémenter en fonction du contenu routage à l’aide d’une entreprise règles de stratégie pour un Type connu | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44451c85-929a-4d13-b0dd-53ea600d0859
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b384c63b26f98a866390a001c7d7c2ec6f3f7cb2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-implement-content-based-routing-using-a-business-rules-policy-for-a-known-message-type"></a><span data-ttu-id="22762-102">Comment : implémenter en fonction du contenu routage à l’aide d’une entreprise règles de stratégie pour un Type connu</span><span class="sxs-lookup"><span data-stu-id="22762-102">How to: Implement Content-Based Routing Using a Business Rules Policy for a Known Message Type</span></span>
## <a name="goal"></a><span data-ttu-id="22762-103">Objectif</span><span class="sxs-lookup"><span data-stu-id="22762-103">Goal</span></span>  
 <span data-ttu-id="22762-104">Cette section montre comment créer un itinéraire qui dynamiquement achemine un message basé sur le contenu d’un type connu (schéma déployé sur la base de données de Configuration de Microsoft BizTalk Server), une entreprise à l’aide de règles de stratégie.</span><span class="sxs-lookup"><span data-stu-id="22762-104">This section demonstrates how to create an itinerary that dynamically routes a message, based on the content of a known message type (schema deployed to the Microsoft BizTalk Server Configuration database), using a business rules policy.</span></span>  
  
 <span data-ttu-id="22762-105">Dans cette rubrique, vous effectuerez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="22762-105">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="22762-106">Créer une stratégie de règles d’entreprise qui permet de router un message en fonction du contenu.</span><span class="sxs-lookup"><span data-stu-id="22762-106">Create a business rules policy that will be used to route a message based on content.</span></span>  
  
-   <span data-ttu-id="22762-107">Créez un bordereau d’itinéraire de routage avec un programme de résolution BRE d’acheminer un message.</span><span class="sxs-lookup"><span data-stu-id="22762-107">Create an itinerary routing slip with a BRE resolver to dynamically route a message.</span></span>  
  
-   <span data-ttu-id="22762-108">Test de l’itinéraire à l’aide de l’exemple d’application Client de Test d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="22762-108">Test the itinerary using the Itinerary Test Client sample application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="22762-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="22762-109">Prerequisites</span></span>  
 <span data-ttu-id="22762-110">Les procédures de cette rubrique requièrent l’achèvement de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md).</span><span class="sxs-lookup"><span data-stu-id="22762-110">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="22762-111">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="22762-111">Before You Begin</span></span>  
 <span data-ttu-id="22762-112">Effectuez les tâches suivantes avant d’effectuer les étapes plus loin dans cette rubrique :</span><span class="sxs-lookup"><span data-stu-id="22762-112">Complete the following tasks before you perform the steps later in this How-to topic:</span></span>  
  
-   <span data-ttu-id="22762-113">Créer le message de test GlobalBank West.</span><span class="sxs-lookup"><span data-stu-id="22762-113">Create the GlobalBank West test message.</span></span>  
  
-   <span data-ttu-id="22762-114">Créer le message de test est de GlobalBank.</span><span class="sxs-lookup"><span data-stu-id="22762-114">Create the GlobalBank East test message.</span></span>  
  
 <span data-ttu-id="22762-115">Les procédures suivantes décrivent comment effectuer chacune d’elles.</span><span class="sxs-lookup"><span data-stu-id="22762-115">The following procedures describe how to do each of these.</span></span>  
  
#### <a name="to-create-the-globalbank-west-test-message"></a><span data-ttu-id="22762-116">Pour créer le message de test GlobalBank West</span><span class="sxs-lookup"><span data-stu-id="22762-116">To create the GlobalBank West test message</span></span>  
  
1.  <span data-ttu-id="22762-117">Dans l’Explorateur Windows, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="22762-117">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="22762-118">Créer une copie de NAOrderDoc.xml et nommez la copie West.xml.</span><span class="sxs-lookup"><span data-stu-id="22762-118">Create a copy of NAOrderDoc.xml, and then name the copy West.xml.</span></span>  
  
3.  <span data-ttu-id="22762-119">Dans le bloc-notes, ouvrez West.xml et modifiez la valeur de la **customerName** élément **GlobalBankWest**.</span><span class="sxs-lookup"><span data-stu-id="22762-119">In Notepad, open West.xml, and then change the value of the **customerName** element to **GlobalBankWest**.</span></span>  
  
4.  <span data-ttu-id="22762-120">Enregistrer West.xml en UTF-8, puis fermez le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="22762-120">Save West.xml as UTF-8, and then close Notepad.</span></span>  
  
#### <a name="to-create-the-globalbank-east-test-message"></a><span data-ttu-id="22762-121">Pour créer le message de test est de GlobalBank</span><span class="sxs-lookup"><span data-stu-id="22762-121">To create the GlobalBank East test message</span></span>  
  
1.  <span data-ttu-id="22762-122">Dans l’Explorateur Windows, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="22762-122">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="22762-123">Créer une copie de NAOrderDoc.xml et nommez la copie East.xml.</span><span class="sxs-lookup"><span data-stu-id="22762-123">Create a copy of NAOrderDoc.xml, and then name the copy East.xml.</span></span>  
  
3.  <span data-ttu-id="22762-124">Dans le bloc-notes, ouvrez East.xml et modifiez la valeur de la **customerName** élément **GlobalBankEast**.</span><span class="sxs-lookup"><span data-stu-id="22762-124">In Notepad, open East.xml, and then change the value of the **customerName** element to **GlobalBankEast**.</span></span>  
  
4.  <span data-ttu-id="22762-125">Enregistrer East.xml en UTF-8, puis fermez le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="22762-125">Save East.xml as UTF-8, and then close Notepad.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="22762-126">Étapes</span><span class="sxs-lookup"><span data-stu-id="22762-126">Steps</span></span>  
  
#### <a name="to-create-a-bre-policy-to-route-using-custom-message-properties"></a><span data-ttu-id="22762-127">Pour créer une stratégie BRE pour router à l’aide des propriétés de message personnalisées</span><span class="sxs-lookup"><span data-stu-id="22762-127">To create a BRE policy to route using custom message properties</span></span>  
 <span data-ttu-id="22762-128">Cette règle utilisera le nom du client à définir dynamiquement le point de terminaison utilisé pour router le message.</span><span class="sxs-lookup"><span data-stu-id="22762-128">This rule will use the customer's name to dynamically set the endpoint used to route the message.</span></span>  
  
1.  <span data-ttu-id="22762-129">Cliquez sur **Démarrer** dans la barre des tâches, pointez sur **tous les programmes**, pointez sur  **[!INCLUDE[prague](../includes/prague-md.md)]** , puis cliquez sur **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="22762-129">Click **Start** on the taskbar, point to **All Programs**, point to **[!INCLUDE[prague](../includes/prague-md.md)]**, and then click **Business Rule Composer**.</span></span>  
  
2.  <span data-ttu-id="22762-130">Dans l’Explorateur de stratégies, cliquez sur **stratégies**, puis cliquez sur **ajouter une nouvelle stratégie**.</span><span class="sxs-lookup"><span data-stu-id="22762-130">In Policy Explorer, right-click **Policies**, and then click **Add New Policy**.</span></span> <span data-ttu-id="22762-131">Nom de la stratégie **RouteBasedOnCustomerKnownType**.</span><span class="sxs-lookup"><span data-stu-id="22762-131">Name the policy **RouteBasedOnCustomerKnownType**.</span></span>  
  
#### <a name="to-add-a-routing-rule-for-customer-globalbank-west"></a><span data-ttu-id="22762-132">Pour ajouter une règle de routage pour le client GlobalBank West</span><span class="sxs-lookup"><span data-stu-id="22762-132">To add a routing rule for customer GlobalBank West</span></span>  
  
1.  <span data-ttu-id="22762-133">Dans le **RouteBasedOnCustomerKnownType** stratégie, avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **ajouter une nouvelle règle**.</span><span class="sxs-lookup"><span data-stu-id="22762-133">In the **RouteBasedOnCustomerKnownType** policy, right-click **Version 1.0 (not saved)**, and then click **Add New Rule**.</span></span> <span data-ttu-id="22762-134">Nommez la règle **SetWestEndpoint**.</span><span class="sxs-lookup"><span data-stu-id="22762-134">Name the rule **SetWestEndpoint**.</span></span>  
  
2.  <span data-ttu-id="22762-135">Dans l’Explorateur de faits, cliquez sur le **schémas XML** droit **schémas**, puis cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="22762-135">In Facts Explorer, click the **XML Schemas** tab, right-click **Schemas**, and then click **Browse**.</span></span>  
  
3.  <span data-ttu-id="22762-136">Dans le **les fichiers de schéma** boîte de dialogue, accédez à C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB. DynamicResolution.Schemas, sélectionnez **NAOrderDoc.xsd**, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="22762-136">In the **Schema Files** dialog box, browse to C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB.DynamicResolution.Schemas, select **NAOrderDoc.xsd**, and then click **Open**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="22762-137">Voici le schéma qui définit le message NAOrderDoc.xml, qui a été utilisé pour créer les messages ouest / est que vous allez utiliser pour le test.</span><span class="sxs-lookup"><span data-stu-id="22762-137">This is the schema that defines the NAOrderDoc.xml message, which was used to create the West and East messages you will use for testing.</span></span>  
  
4.  <span data-ttu-id="22762-138">Dans l’Explorateur de faits, cliquez sur **NAOrderDoc.xsd**, puis dans le volet Propriétés, cliquez sur le **Type de Document** propriété, puis tapez **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc** .</span><span class="sxs-lookup"><span data-stu-id="22762-138">In Facts Explorer, click **NAOrderDoc.xsd**, and then in the Properties pane, click the **Document Type** property, and then type **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="22762-139">Il s’agit du nom qualifié complet du schéma.</span><span class="sxs-lookup"><span data-stu-id="22762-139">This is the fully qualified name of the schema.</span></span>  
  
5.  <span data-ttu-id="22762-140">Dans l’Explorateur de faits, développez **NAOrderDoc.xsd**, puis développez **OrderDoc**.</span><span class="sxs-lookup"><span data-stu-id="22762-140">In Facts Explorer, expand **NAOrderDoc.xsd**, and then expand **OrderDoc**.</span></span>  
  
6.  <span data-ttu-id="22762-141">Dans la fenêtre de la règle, cliquez sur **Conditions**, pointez sur **prédicats**, puis cliquez sur **égal**.</span><span class="sxs-lookup"><span data-stu-id="22762-141">In the Rule window, right-click **Conditions**, point to **Predicates**, and then click **Equal**.</span></span>  
  
7.  <span data-ttu-id="22762-142">Dans l’Explorateur de faits, faites glisser le **customerName** élément à la **argument1** nœud sous **Conditions**.</span><span class="sxs-lookup"><span data-stu-id="22762-142">From Facts Explorer, drag the **customerName** element to the **argument1** node under **Conditions**.</span></span>  
  
8.  <span data-ttu-id="22762-143">Cliquez sur le **argument2** nœud, puis tapez **GlobalBankWest**.</span><span class="sxs-lookup"><span data-stu-id="22762-143">Click the **argument2** node, and then type **GlobalBankWest**.</span></span>  
  
9. <span data-ttu-id="22762-144">Dans l’Explorateur de faits, cliquez sur le **vocabulaires** onglet, développez **ESB. EndPointInfo**, puis développez **Version 1.0**.</span><span class="sxs-lookup"><span data-stu-id="22762-144">In Facts Explorer, click the **Vocabularies** tab, expand **ESB.EndPointInfo**, and then expand **Version 1.0**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="22762-145">La [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] inclut plusieurs vocabulaires qui peuvent être utilisés pour créer des règles pour l’utilisation dans l’architecture ESB.</span><span class="sxs-lookup"><span data-stu-id="22762-145">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes several vocabularies that can be used for creating rules for use in the ESB.</span></span> <span data-ttu-id="22762-146">Certains d'entre eux doivent être remplacé ou augmentée avec vos propres vocabulaires.</span><span class="sxs-lookup"><span data-stu-id="22762-146">Some of these should be replaced or augmented with your own vocabularies.</span></span> <span data-ttu-id="22762-147">Par exemple, le **DynamicRunTimeMaptypes** a des définitions pour les cartes fournies dans le **GlobalBank** exemples.</span><span class="sxs-lookup"><span data-stu-id="22762-147">For example, the **DynamicRunTimeMaptypes** has definitions for the maps provided in the **GlobalBank** samples.</span></span>  
  
10. <span data-ttu-id="22762-148">Dans l’Explorateur de faits, faites glisser le **définir l’emplacement du Transport Point de terminaison sortants** définition **Actions**.</span><span class="sxs-lookup"><span data-stu-id="22762-148">From Facts Explorer, drag the **Set End Point Outbound Transport Location** definition to **Actions**.</span></span>  
  
11. <span data-ttu-id="22762-149">Cliquez sur  **\<une chaîne vide >** , puis tapez **C:\HowTos\Out\West%MessageID%.xml**.</span><span class="sxs-lookup"><span data-stu-id="22762-149">Click **\<empty string>** and then type **C:\HowTos\Out\West%MessageID%.xml**.</span></span>  
  
12. <span data-ttu-id="22762-150">Dans l’Explorateur de faits, faites glisser le **définir le Type de Transport Point de terminaison sortants** définition **Actions**.</span><span class="sxs-lookup"><span data-stu-id="22762-150">From Facts Explorer, drag the **Set End Point Outbound Transport Type** definition to **Actions**.</span></span>  
  
13. <span data-ttu-id="22762-151">Dans l’Explorateur de faits, développez **ESB. TransportTypes**, développez **Version 1.0**, puis faites glisser le **adaptateur fournisseurs** définition  **\<une chaîne vide >**.</span><span class="sxs-lookup"><span data-stu-id="22762-151">In Facts Explorer, expand **ESB.TransportTypes**, expand **Version 1.0**, and then drag the **Adaptor Providers** definition to **\<empty string>**.</span></span>  
  
14. <span data-ttu-id="22762-152">Dans le **Actions** volet, développez le **adaptateur fournisseurs** liste déroulante, puis cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="22762-152">In the **Actions** pane, expand the **Adaptor Providers** drop-down list, and then click **FILE**.</span></span>  
  
#### <a name="to-add-a-routing-rule-for-customer-globalbank-east"></a><span data-ttu-id="22762-153">Pour ajouter une règle de routage pour le client est de GlobalBank</span><span class="sxs-lookup"><span data-stu-id="22762-153">To add a routing rule for customer GlobalBank East</span></span>  
  
1.  <span data-ttu-id="22762-154">Dans l’Explorateur de stratégies, cliquez sur le **SetWestEndpoint** de règle, puis cliquez sur **copie**.</span><span class="sxs-lookup"><span data-stu-id="22762-154">In Policy Explorer, right-click the **SetWestEndpoint** rule, and then click **Copy**.</span></span>  
  
2.  <span data-ttu-id="22762-155">Avec le bouton droit **Version 1.0 (non enregistrée)**, puis cliquez sur **coller**.</span><span class="sxs-lookup"><span data-stu-id="22762-155">Right-click **Version 1.0 (not saved)**, and then click **Paste**.</span></span>  
  
3.  <span data-ttu-id="22762-156">Dans le **nom de la nouvelle règle** boîte de dialogue, tapez **SetEastEndpoint**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="22762-156">In the **New Rule Name** dialog box, type **SetEastEndpoint**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="22762-157">Dans l’Explorateur de stratégies, cliquez sur le **SetEastEndpoint** règle.</span><span class="sxs-lookup"><span data-stu-id="22762-157">In Policy Explorer, click the **SetEastEndpoint** rule.</span></span>  
  
5.  <span data-ttu-id="22762-158">Dans le **Conditions** section, cliquez sur **GlobalBankWest**, puis cliquez sur **réinitialiser l’argument**.</span><span class="sxs-lookup"><span data-stu-id="22762-158">In the **Conditions** section, right-click **GlobalBankWest**, and then click **Reset argument**.</span></span>  
  
6.  <span data-ttu-id="22762-159">Cliquez sur **argument2**, puis tapez **GlobalBankEast**.</span><span class="sxs-lookup"><span data-stu-id="22762-159">Click **argument2**, and then type **GlobalBankEast**.</span></span>  
  
7.  <span data-ttu-id="22762-160">Dans le **Actions** section, cliquez sur **C:\HowTos\Out\West%MessageID%.xml**, puis cliquez sur **réinitialiser l’argument**.</span><span class="sxs-lookup"><span data-stu-id="22762-160">In the **Actions** section, right-click **C:\HowTos\Out\West%MessageID%.xml**, and then click **Reset argument**.</span></span>  
  
8.  <span data-ttu-id="22762-161">Cliquez sur  **\<une chaîne vide >**, puis tapez **C:\HowTos\Out\East%MessageID%.xml**.</span><span class="sxs-lookup"><span data-stu-id="22762-161">Click **\<empty string>**, and then type **C:\HowTos\Out\East%MessageID%.xml**.</span></span>  
  
#### <a name="to-add-a-routing-rule-for-unknown-customers"></a><span data-ttu-id="22762-162">Pour ajouter une règle de routage pour les clients inconnus</span><span class="sxs-lookup"><span data-stu-id="22762-162">To add a routing rule for unknown customers</span></span>  
  
1.  <span data-ttu-id="22762-163">Dans la stratégie RouteBasedOnCustomerKnownType, avec le bouton droit de la Version 1.0 (non enregistrée), puis cliquez sur Ajouter une nouvelle règle.</span><span class="sxs-lookup"><span data-stu-id="22762-163">In the RouteBasedOnCustomerKnownType policy, right-click Version 1.0 (not saved), and then click Add New Rule.</span></span> <span data-ttu-id="22762-164">Nom de la règle SetUnknownCustomerEndpoint.</span><span class="sxs-lookup"><span data-stu-id="22762-164">Name the rule SetUnknownCustomerEndpoint.</span></span>  
  
2.  <span data-ttu-id="22762-165">Dans la fenêtre de la règle, cliquez sur les Conditions, puis cliquez sur Ajouter et logique.</span><span class="sxs-lookup"><span data-stu-id="22762-165">In the Rule window, right-click Conditions, and then click Add logical AND.</span></span>  
  
3.  <span data-ttu-id="22762-166">Dans la fenêtre de la règle, avec le bouton droit et, pointez sur les prédicats, puis cliquez sur NotEqual.</span><span class="sxs-lookup"><span data-stu-id="22762-166">In the Rule window, right-click AND, point to Predicates, and then click NotEqual.</span></span>  
  
4.  <span data-ttu-id="22762-167">Dans l’Explorateur de faits, cliquez sur l’onglet schémas XML, NAOrderDoc.xsd, puis OrderDoc.</span><span class="sxs-lookup"><span data-stu-id="22762-167">In Facts Explorer, click the XML Schemas tab, expand NAOrderDoc.xsd, and then expand OrderDoc.</span></span>  
  
5.  <span data-ttu-id="22762-168">À partir de l’Explorateur de faits, faites glisser l’élément customerName au nœud argument1 sous Conditions.</span><span class="sxs-lookup"><span data-stu-id="22762-168">From Facts Explorer, drag the customerName element to the argument1 node under Conditions.</span></span>  
  
6.  <span data-ttu-id="22762-169">Cliquez sur le nœud argument2 et tapez GlobalBankWest.</span><span class="sxs-lookup"><span data-stu-id="22762-169">Click the argument2 node, and then type GlobalBankWest.</span></span>  
  
7.  <span data-ttu-id="22762-170">Dans la fenêtre de la règle, avec le bouton droit et, pointez sur les prédicats, puis cliquez sur NotEqual.</span><span class="sxs-lookup"><span data-stu-id="22762-170">In the Rule window, right-click AND, point to Predicates, and then click NotEqual.</span></span>  
  
8.  <span data-ttu-id="22762-171">À partir de l’Explorateur de faits, faites glisser l’élément customerName au nœud argument1 sous Conditions.</span><span class="sxs-lookup"><span data-stu-id="22762-171">From Facts Explorer, drag the customerName element to the argument1 node under Conditions.</span></span>  
  
9. <span data-ttu-id="22762-172">Cliquez sur le nœud argument2 et tapez GlobalBankEast.</span><span class="sxs-lookup"><span data-stu-id="22762-172">Click the argument2 node, and then type GlobalBankEast.</span></span>  
  
10. <span data-ttu-id="22762-173">Dans l’Explorateur de faits, cliquez sur l’onglet vocabulaires, ESB. EndPointInfo, puis développez la Version 1.0.</span><span class="sxs-lookup"><span data-stu-id="22762-173">In Facts Explorer, click the Vocabularies tab, expand ESB.EndPointInfo, and then expand Version 1.0.</span></span>  
  
11. <span data-ttu-id="22762-174">À partir de l’Explorateur de faits, faites glisser la définition de l’emplacement de Transport sortant Point de terminaison défini pour les Actions.</span><span class="sxs-lookup"><span data-stu-id="22762-174">From Facts Explorer, drag the Set End Point Outbound Transport Location definition to Actions.</span></span>  
  
12. <span data-ttu-id="22762-175">Cliquez sur \<une chaîne vide >, puis tapez C:\HowTos\Out\CustomerUnknown%MessageID%.xml.</span><span class="sxs-lookup"><span data-stu-id="22762-175">Click \<empty string>, and then type C:\HowTos\Out\CustomerUnknown%MessageID%.xml.</span></span>  
  
13. <span data-ttu-id="22762-176">À partir de l’Explorateur de faits, faites glisser la définition du Type de Transport sortant Point de terminaison défini pour les Actions.</span><span class="sxs-lookup"><span data-stu-id="22762-176">From Facts Explorer, drag the Set End Point Outbound Transport Type definition to Actions.</span></span>  
  
14. <span data-ttu-id="22762-177">Dans l’Explorateur de faits, développez ESB. TransportTypes, puis Version 1.0, puis faites glisser la définition de fournisseurs de carte à \<une chaîne vide >.</span><span class="sxs-lookup"><span data-stu-id="22762-177">In Facts Explorer, expand ESB.TransportTypes, expand Version 1.0, and then drag the Adaptor Providers definition to \<empty string>.</span></span>  
  
15. <span data-ttu-id="22762-178">Dans le volet Actions, développez la liste déroulante des fournisseurs de carte, puis cliquez sur fichier.</span><span class="sxs-lookup"><span data-stu-id="22762-178">In the Actions pane, expand the Adaptor Providers drop-down list, and then click FILE.</span></span>  
  
#### <a name="to-publish-and-deploy-the-policy"></a><span data-ttu-id="22762-179">Pour publier et déployer la stratégie</span><span class="sxs-lookup"><span data-stu-id="22762-179">To publish and deploy the policy</span></span>  
  
1.  <span data-ttu-id="22762-180">Dans l’Explorateur de stratégies, sous la **RouteBasedOnCustomerKnownType** stratégie, le bouton droit sur **Version 1.0 (non enregistrée)**, puis cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="22762-180">In Policy Explorer, under the **RouteBasedOnCustomerKnownType** policy, right click **Version 1.0 (not saved)**, and then click **Publish**.</span></span>  
  
2.  <span data-ttu-id="22762-181">Dans l’Explorateur de stratégies, sous la **RouteBasedOnCustomerKnownType** stratégie, le bouton droit sur **Version 1.0 - publiée**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="22762-181">In Policy Explorer, under the **RouteBasedOnCustomerKnownType** policy, right click **Version 1.0 - Published**, and then click **Deploy**.</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a><span data-ttu-id="22762-182">Pour créer un modèle DSL de la feuille de route ESB</span><span class="sxs-lookup"><span data-stu-id="22762-182">To create an ESB itinerary DSL model</span></span>  
  
1.  <span data-ttu-id="22762-183">Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez C:\HowTos\Patterns\Patterns.sln.</span><span class="sxs-lookup"><span data-stu-id="22762-183">In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="22762-184">Dans l’Explorateur de solutions, cliquez sur le **ItineraryLibrary** de projet, pointez sur **ajouter**, puis cliquez sur **nouvel itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="22762-184">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="22762-185">Dans le **ajouter un nouvel élément** boîte de dialogue le **nom** , tapez **CbrKnownType**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="22762-185">In the **Add New Item** dialog box, in the **Name** box, type **CbrKnownType**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="22762-186">Pour configurer les propriétés de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="22762-186">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="22762-187">Dans Visual Studio, cliquez sur l’aire de conception de **CbrKnownType.itinerary**.</span><span class="sxs-lookup"><span data-stu-id="22762-187">In Visual Studio, click the design surface of **CbrKnownType.itinerary**.</span></span> <span data-ttu-id="22762-188">Dans le **CbrKnownType** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="22762-188">In the **CbrKnownType** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="22762-189">Dans le **modèle exportateur** la liste déroulante, cliquez sur **XML itinéraire exportateur**.</span><span class="sxs-lookup"><span data-stu-id="22762-189">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="22762-190">Dans le **extendeur paramètres** section à côté du **fichier XML de la feuille de route** propriété, cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="22762-190">In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    3.  <span data-ttu-id="22762-191">Dans le **sélectionner un fichier XML** boîte de dialogue, tapez **C:\HowTos\Itineraries\CbrKnownType** dans les **nom de fichier** zone, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="22762-191">In the **Select XML File** dialog box, type **C:\HowTos\Itineraries\CbrKnownType** in the **File name** box, and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="22762-192">Cette étape vous permet d’exporter la feuille de route en tant que XML vers un emplacement de fichier local.</span><span class="sxs-lookup"><span data-stu-id="22762-192">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="22762-193">En exportant un itinéraire vers un emplacement de fichier local, au lieu de la base de données d’itinéraire, permet de tester de l’itinéraire à l’aide de l’application cliente de Test ESB.</span><span class="sxs-lookup"><span data-stu-id="22762-193">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="22762-194">Vous pourrez terminer cette procédure plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="22762-194">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="22762-195">Pour définir la structure de la feuille de route</span><span class="sxs-lookup"><span data-stu-id="22762-195">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="22762-196">Dans la boîte à outils, faites glisser un **rampe d’entrée** élément de modèle à l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="22762-196">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="22762-197">Dans le **OnRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="22762-197">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="22762-198">Cliquez sur le **nom** propriété, puis tapez **ReceiveNAOrder**.</span><span class="sxs-lookup"><span data-stu-id="22762-198">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="22762-199">Dans le **extendeur** la liste déroulante, cliquez sur **rampe d’entrée ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="22762-199">In the **Extender** drop-down list, click **On-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="22762-200">Dans le **Application BizTalk** la liste déroulante, cliquez sur **Microsoft.Practices.ESB**.</span><span class="sxs-lookup"><span data-stu-id="22762-200">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="22762-201">Dans le **Port de réception** la liste déroulante, cliquez sur **OnRamp.Itinerary**.</span><span class="sxs-lookup"><span data-stu-id="22762-201">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="22762-202">Dans la boîte à outils, faites glisser un **rampe** élément à l’aire de conception de modèle, puis placez-le à droite de la **ReceiveNAOrder** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="22762-202">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **ReceiveNAOrder** model element.</span></span> <span data-ttu-id="22762-203">Dans le **OffRamp1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="22762-203">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="22762-204">Cliquez sur le **nom** propriété, puis tapez **SendRegionalOrders**.</span><span class="sxs-lookup"><span data-stu-id="22762-204">Click the **Name** property, and then type **SendRegionalOrders**.</span></span>  
  
    2.  <span data-ttu-id="22762-205">Dans le **extendeur** la liste déroulante, cliquez sur **rampe ESB extendeur**.</span><span class="sxs-lookup"><span data-stu-id="22762-205">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="22762-206">Dans le **Application BizTalk** la liste déroulante, cliquez sur **GlobalBank.ESB**.</span><span class="sxs-lookup"><span data-stu-id="22762-206">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="22762-207">Dans le **Port d’envoi** la liste déroulante, cliquez sur **DynamicResolutionOneWay**.</span><span class="sxs-lookup"><span data-stu-id="22762-207">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
3.  <span data-ttu-id="22762-208">Dans la boîte à outils, faites glisser un **itinéraire Service** élément à l’aire de conception de modèle, puis les placer entre la **ReceiveNAOrder** élément de modèle et la **SendRegionalOrders**élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="22762-208">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **ReceiveNAOrder** model element and the **SendRegionalOrders** model element.</span></span> <span data-ttu-id="22762-209">Dans le **ItineraryService1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="22762-209">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="22762-210">Cliquez sur le **nom** propriété, puis tapez **SendPortFilter**.</span><span class="sxs-lookup"><span data-stu-id="22762-210">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="22762-211">Dans le **d’extension du Service itinéraire** la liste déroulante, cliquez sur **rampe extendeur**.</span><span class="sxs-lookup"><span data-stu-id="22762-211">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="22762-212">Dans le **rampe** déroulante liste, développez **SendRegionalOrders**, puis cliquez sur **gestionnaires d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="22762-212">In the **Off-Ramp** drop-down list, expand **SendRegionalOrders**, and then click **Send Handlers**.</span></span>  
  
4.  <span data-ttu-id="22762-213">Avec le bouton droit le **résolveur** collection de la **SendPortFilter** élément de modèle, puis cliquez sur **ajouter le nouveau programme de résolution**.</span><span class="sxs-lookup"><span data-stu-id="22762-213">Right-click the **Resolver** collection of the **SendPortFilter** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="22762-214">Dans le **Resolver1** fenêtre Propriétés, configurez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="22762-214">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="22762-215">Cliquez sur le **nom** propriété, puis tapez **RouteRegionalOrders**.</span><span class="sxs-lookup"><span data-stu-id="22762-215">Click the **Name** property, and then type **RouteRegionalOrders**.</span></span>  
  
    2.  <span data-ttu-id="22762-216">Dans le **nom Transport** la liste déroulante, cliquez sur **BRE**.</span><span class="sxs-lookup"><span data-stu-id="22762-216">In the **Transport Name** drop-down list, click **BRE**.</span></span>  
  
    3.  <span data-ttu-id="22762-217">Dans le **implémentation d’un programme de résolution** la liste déroulante, cliquez sur **Extension du programme de résolution Bre**.</span><span class="sxs-lookup"><span data-stu-id="22762-217">In the **Resolver Implementation** drop-down list, click **Bre Resolver Extension**.</span></span>  
  
    4.  <span data-ttu-id="22762-218">Dans le **stratégie** la liste déroulante, cliquez sur **RouteBasedOnCustomerKnownType**.</span><span class="sxs-lookup"><span data-stu-id="22762-218">In the **Policy** drop-down list, click **RouteBasedOnCustomerKnownType**.</span></span>  
  
    5.  <span data-ttu-id="22762-219">Dans le **reconnaît un Format de Message** cliquez sur la liste déroulante **True**.</span><span class="sxs-lookup"><span data-stu-id="22762-219">In the **Recognize Message Format** drop-down list click **True**.</span></span>  
  
    6.  <span data-ttu-id="22762-220">Dans le **UseMsg** la liste déroulante, cliquez sur **True**.</span><span class="sxs-lookup"><span data-stu-id="22762-220">In the **UseMsg** drop-down list, click **True**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="22762-221">Si vous utilisez l’Extension du programme de résolution BRE à partir de l’orchestration, le **recognizeMessageFormat** propriété doit être définie sur **False**.</span><span class="sxs-lookup"><span data-stu-id="22762-221">If you use the BRE Resolver Extension from orchestration, the **recognizeMessageFormat** property must be set to **False**.</span></span>  
  
5.  <span data-ttu-id="22762-222">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="22762-222">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="22762-223">Faites glisser une connexion à partir de la **ReceiveNAOrder** élément de modèle à la **SendPortFilter** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="22762-223">Drag a connection from the **ReceiveNAOrder** model element to the **SendPortFilter** model element.</span></span>  
  
6.  <span data-ttu-id="22762-224">Dans la boîte à outils, cliquez sur **connecteur**.</span><span class="sxs-lookup"><span data-stu-id="22762-224">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="22762-225">Faites glisser une connexion à partir de la **SendPortFilter** élément de modèle à la **SendRegionalOrders** élément de modèle.</span><span class="sxs-lookup"><span data-stu-id="22762-225">Drag a connection from the **SendPortFilter** model element to the **SendRegionalOrders** model element.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="22762-226">Pour exporter le modèle pour une utilisation avec le Client de Test d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="22762-226">To export the model for use with the Itinerary Test Client</span></span>  
  
1.  <span data-ttu-id="22762-227">Dans Visual Studio, cliquez sur l’aire de conception de la **CbrKnownType** itinéraire, puis cliquez sur **exporter le modèle**.</span><span class="sxs-lookup"><span data-stu-id="22762-227">In Visual Studio, right-click the design surface of the **CbrKnownType** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="22762-228">La version XML de l’itinéraire s’ouvre dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="22762-228">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="22762-229">Enregistrez tous les artefacts de projet.</span><span class="sxs-lookup"><span data-stu-id="22762-229">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="22762-230">Dans l’Explorateur Windows, accédez à C:\HowTos\Itineraries et notez la création de votre feuille de route XML (CbrKnownType.xml).</span><span class="sxs-lookup"><span data-stu-id="22762-230">In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (CbrKnownType.xml).</span></span>  
  
#### <a name="to-test-the-itinerary-and-business-rules"></a><span data-ttu-id="22762-231">Pour tester les règles d’itinéraire et d’entreprise</span><span class="sxs-lookup"><span data-stu-id="22762-231">To test the itinerary and business rules</span></span>  
  
1.  <span data-ttu-id="22762-232">Ouvrez l’exemple d’application Client de Test d’itinéraire à l’aide du raccourci créé au cours de la [conditions préalables pour les activités de développement](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB. Itinerary.Test.exe - raccourci).</span><span class="sxs-lookup"><span data-stu-id="22762-232">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="22762-233">Dans le Client de Test d’itinéraire, désactivez le **utiliser le Service WCF** case à cocher, puis cliquez sur **charge itinéraire**.</span><span class="sxs-lookup"><span data-stu-id="22762-233">In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.</span></span>  
  
3.  <span data-ttu-id="22762-234">Dans le **ouvrir le fichier de feuille de route** boîte de dialogue, accédez à C:\HowTos\Itineraries.</span><span class="sxs-lookup"><span data-stu-id="22762-234">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="22762-235">Sélectionnez **CbrKnownType.xml**, puis cliquez sur **ouvrir** pour charger la feuille de route.</span><span class="sxs-lookup"><span data-stu-id="22762-235">Select **CbrKnownType.xml**, and then click **Open** to load the itinerary.</span></span>  
  
4.  <span data-ttu-id="22762-236">Cliquez sur **OK** pour effacer le **itinéraire chargé avec succès** message.</span><span class="sxs-lookup"><span data-stu-id="22762-236">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  
  
5.  <span data-ttu-id="22762-237">Dans le Client de Test d’itinéraire, cliquez sur le bouton de sélection (...) à côté du **charge Message** boîte.</span><span class="sxs-lookup"><span data-stu-id="22762-237">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
6.  <span data-ttu-id="22762-238">Dans le **sélectionner le Document XML à charger** boîte de dialogue, accédez à C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="22762-238">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="22762-239">Sélectionnez **West.xml**, puis cliquez sur **ouvrir** pour le message de test de charge.</span><span class="sxs-lookup"><span data-stu-id="22762-239">Select **West.xml**, and then click **Open** to load the test message.</span></span>  
  
7.  <span data-ttu-id="22762-240">Cliquez sur le **soumettre la demande** bouton.</span><span class="sxs-lookup"><span data-stu-id="22762-240">Click the **Submit Request** button.</span></span> <span data-ttu-id="22762-241">Une fois le test terminé, cliquez sur **OK** pour faire disparaître la confirmation qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="22762-241">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
8.  <span data-ttu-id="22762-242">Dans l’Explorateur Windows, accédez à C:\HowTos\Out. Vérifiez que le message West%MessageID%.xml a été écrit dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="22762-242">In Windows Explorer, browse to C:\HowTos\Out. Verify that the West%MessageID%.xml message has been written to the directory.</span></span>  
  
9. <span data-ttu-id="22762-243">Répétez le processus de test en utilisant le message East.xml.</span><span class="sxs-lookup"><span data-stu-id="22762-243">Repeat the test process using the East.xml message.</span></span>  
  
10. <span data-ttu-id="22762-244">Dans l’Explorateur Windows, accédez à C:\HowTos\Out. Vérifiez que le message East%MessageID%.xml a été écrit dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="22762-244">In Windows Explorer, browse to C:\HowTos\Out. Verify that the East%MessageID%.xml message has been written to the directory.</span></span>  
  
11. <span data-ttu-id="22762-245">Répétez le processus de test en utilisant le message NAOrderDoc.xml.</span><span class="sxs-lookup"><span data-stu-id="22762-245">Repeat the test process using the NAOrderDoc.xml message.</span></span>  
  
12. <span data-ttu-id="22762-246">Dans l’Explorateur Windows, accédez à C:\HowTos\Out. Vérifiez que le message CustomerUnknown%MessageID%.xml a été écrit dans le répertoire.</span><span class="sxs-lookup"><span data-stu-id="22762-246">In Windows Explorer, browse to C:\HowTos\Out. Verify that the CustomerUnknown%MessageID%.xml message has been written to the directory.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="22762-247">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="22762-247">Additional Resources</span></span>  
 <span data-ttu-id="22762-248">Pour plus d'informations, consultez les rubriques connexes suivantes :</span><span class="sxs-lookup"><span data-stu-id="22762-248">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="22762-249">Comment : sélectionner un itinéraire à l’aide d’une stratégie de règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="22762-249">How to: Select an Itinerary Using a Business Rules Policy</span></span>](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [<span data-ttu-id="22762-250">Comment : acheminer un Message basé sur le contexte du Message à l’aide d’une stratégie de règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="22762-250">How to: Dynamically Route a Message Based on Message Context Using a Business Rules Policy</span></span>](../esb-toolkit/dynamically-route-messages-based-on-message-context-using-business-rules-policy.md)  
  
-   [<span data-ttu-id="22762-251">Activités de développement</span><span class="sxs-lookup"><span data-stu-id="22762-251">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="22762-252">Modèles de routage de messages</span><span class="sxs-lookup"><span data-stu-id="22762-252">Message Routing Patterns</span></span>](../esb-toolkit/message-routing-patterns.md)