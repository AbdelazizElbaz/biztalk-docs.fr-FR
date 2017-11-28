---
title: "Étape 2 : Configurer le système Salesforce | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a4b09fb-70a7-4eec-b1e3-f05de0e84df1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d65a1c741103b9c8f1e9493b7bd2aa56eef8cf18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-set-up-the-salesforce-system"></a><span data-ttu-id="792ec-102">Étape 2 : Configurer le système Salesforce</span><span class="sxs-lookup"><span data-stu-id="792ec-102">Step 2: Set up the Salesforce System</span></span>
<span data-ttu-id="792ec-103">Au cours de cette étape, vous allez configurer Salesforce pour envoyer des notifications lorsqu'une opportunité est clôturée avec succès.</span><span class="sxs-lookup"><span data-stu-id="792ec-103">In this step, you configure Salesforce to send notifications when an opportunity is successfully closed.</span></span> <span data-ttu-id="792ec-104">Avant de pouvoir envoyer des notifications, vous devez effectuer les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="792ec-104">Before you can send notifications, you need to perform the following steps:</span></span>  
  
-   <span data-ttu-id="792ec-105">Créer un compte dans Salesforce.</span><span class="sxs-lookup"><span data-stu-id="792ec-105">Create an account in Salesforce.</span></span> <span data-ttu-id="792ec-106">Un compte représente un client pour Northwind.</span><span class="sxs-lookup"><span data-stu-id="792ec-106">An account represents a customer for Northwind.</span></span>  
  
-   <span data-ttu-id="792ec-107">Créer une opportunité pour le compte.</span><span class="sxs-lookup"><span data-stu-id="792ec-107">Create an opportunity for the account.</span></span> <span data-ttu-id="792ec-108">Une opportunité représente une opportunité de vente potentielle au client.</span><span class="sxs-lookup"><span data-stu-id="792ec-108">An opportunity represents a prospective sales opportunity with the customer.</span></span> <span data-ttu-id="792ec-109">Dans le cadre de l'opportunité, vous pouvez également ajouter des détails sur le produit qui intéresse le client.</span><span class="sxs-lookup"><span data-stu-id="792ec-109">As part of the opportunity, you also add the product details that the customer is interested in.</span></span>  
  
-   <span data-ttu-id="792ec-110">Créer un workflow dans Salesforce.</span><span class="sxs-lookup"><span data-stu-id="792ec-110">Create a workflow in Salesforce.</span></span>  
  
-   <span data-ttu-id="792ec-111">Créer une définition d'application connectée Salesforce.</span><span class="sxs-lookup"><span data-stu-id="792ec-111">Create a Salesforce connected application definition.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="792ec-112">Les étapes de cette rubrique supposent que vous possédez déjà un compte de développeur Salesforce.</span><span class="sxs-lookup"><span data-stu-id="792ec-112">The steps in this topic assume that you already have a Salesforce developer account.</span></span> <span data-ttu-id="792ec-113">Pour créer un nouveau compte de développeur dans Salesforce, accédez à [http://go.microsoft.com/fwlink/?LinkId=296424](http://go.microsoft.com/fwlink/?LinkId=296424).</span><span class="sxs-lookup"><span data-stu-id="792ec-113">To create a new developer account in Salesforce, go to [http://go.microsoft.com/fwlink/?LinkId=296424](http://go.microsoft.com/fwlink/?LinkId=296424).</span></span>  
  
### <a name="to-create-an-account-in-salesforce"></a><span data-ttu-id="792ec-114">Pour créer un compte dans Salesforce</span><span class="sxs-lookup"><span data-stu-id="792ec-114">To create an Account in Salesforce</span></span>  
  
1.  <span data-ttu-id="792ec-115">Connectez-vous au portail Salesforce.com à l'aide de vos informations d'identification développeur.</span><span class="sxs-lookup"><span data-stu-id="792ec-115">Log on to the Salesforce.com portal using your developer credentials.</span></span>  
  
2.  <span data-ttu-id="792ec-116">Dans le portail, cliquez sur le **comptes** onglet, puis cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="792ec-116">On the portal, click the **Accounts** tab, and then click **New**.</span></span>  
  
3.  <span data-ttu-id="792ec-117">Sur le **nouveau compte** , fournissez des valeurs pour les différents champs.</span><span class="sxs-lookup"><span data-stu-id="792ec-117">On the **New Account** page, provide values for the various fields.</span></span> <span data-ttu-id="792ec-118">En spécifiant une valeur pour **nom de compte** est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="792ec-118">Specifying a value for **Account Name** is mandatory.</span></span> <span data-ttu-id="792ec-119">Pour ce didacticiel, spécifiez le nom du compte en tant que `Customer1`.</span><span class="sxs-lookup"><span data-stu-id="792ec-119">For this tutorial, specify the account name as `Customer1`.</span></span>  
  
4.  <span data-ttu-id="792ec-120">Cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="792ec-120">Click **Save**.</span></span>  
  
### <a name="to-create-an-opportunity-for-the-customer"></a><span data-ttu-id="792ec-121">Pour créer une opportunité pour le client</span><span class="sxs-lookup"><span data-stu-id="792ec-121">To create an Opportunity for the customer</span></span>  
  
1.  <span data-ttu-id="792ec-122">Dans le portail Salesforce.com, cliquez sur le **opportunités** onglet.</span><span class="sxs-lookup"><span data-stu-id="792ec-122">On the Salesforce.com portal, click the **Opportunities** tab.</span></span>  
  
2.  <span data-ttu-id="792ec-123">Dans le **opportunités récentes** , cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="792ec-123">In the **Recent Opportunities** section, click **New**.</span></span>  
  
3.  <span data-ttu-id="792ec-124">Dans la page Nouvelle opportunité, spécifiez les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="792ec-124">In the New Opportunity page, specify the following values:</span></span>  
  
    1.  <span data-ttu-id="792ec-125">Spécifiez un **nom d’opportunité**, par exemple, `Opportunity with Customer 1`.</span><span class="sxs-lookup"><span data-stu-id="792ec-125">Specify an **Opportunity Name**, for example, `Opportunity with Customer 1`.</span></span>  
  
    2.  <span data-ttu-id="792ec-126">Spécifiez le **nom de compte**.</span><span class="sxs-lookup"><span data-stu-id="792ec-126">Specify the **Account Name**.</span></span> <span data-ttu-id="792ec-127">Cette valeur représente le compte auquel cette opportunité est associée.</span><span class="sxs-lookup"><span data-stu-id="792ec-127">This represents the account with which this opportunity is associated.</span></span> <span data-ttu-id="792ec-128">Pour ce didacticiel, définissez le compte `Customer1`.</span><span class="sxs-lookup"><span data-stu-id="792ec-128">For this tutorial, set the Account to `Customer1`.</span></span> <span data-ttu-id="792ec-129">Vous avez créé ce compte lors de la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="792ec-129">You created this account in the previous procedure.</span></span>  
  
    3.  <span data-ttu-id="792ec-130">Spécifiez un **Date de clôture**.</span><span class="sxs-lookup"><span data-stu-id="792ec-130">Specify a **Close Date**.</span></span> <span data-ttu-id="792ec-131">Il s'agit de la date à laquelle l'opportunité doit être clôturée.</span><span class="sxs-lookup"><span data-stu-id="792ec-131">This represents the date by which the opportunity should be closed.</span></span>  
  
    4.  <span data-ttu-id="792ec-132">Spécifiez un **étape**.</span><span class="sxs-lookup"><span data-stu-id="792ec-132">Specify a **Stage**.</span></span> <span data-ttu-id="792ec-133">Il s'agit du stade actuel de l'opportunité.</span><span class="sxs-lookup"><span data-stu-id="792ec-133">This denotes the current stage for the opportunity.</span></span> <span data-ttu-id="792ec-134">Pour commencer, vous pouvez définir la possibilité d’une autre manière, par exemple, **nécessite une analyse**.</span><span class="sxs-lookup"><span data-stu-id="792ec-134">To start with, you can set the opportunity to anything, for example, **Needs Analysis**.</span></span>  
  
         <span data-ttu-id="792ec-135">![Créer une opportunité dans Salesforce](../core/media/bts-sf-create-opp.jpg "BTS_SF_Create_Opp")</span><span class="sxs-lookup"><span data-stu-id="792ec-135">![Create an opportunity in Salesforce](../core/media/bts-sf-create-opp.jpg "BTS_SF_Create_Opp")</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="792ec-136">Assurez-vous que vous ne définissez pas l’étape **fermées/gagnées** pour commencer.</span><span class="sxs-lookup"><span data-stu-id="792ec-136">Make sure you do not set the stage to **Closed Won** to start with.</span></span> <span data-ttu-id="792ec-137">Pour le scénario de ce didacticiel, chaque fois que l’étape est définie sur **fermées/gagnées** une notification est envoyée à un point de terminaison de relais [!INCLUDE[winazure](../includes/winazure-md.md)] [!INCLUDE[sb](../includes/sb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="792ec-137">For the scenario in this tutorial, every time the stage is set to **Closed Won** a notification is sent to a relay endpoint on [!INCLUDE[winazure](../includes/winazure-md.md)][!INCLUDE[sb](../includes/sb-md.md)].</span></span> <span data-ttu-id="792ec-138">Nous n’avons pas cette partie de la solution encore configuré, vous devez donc pas affecter l’étape **fermées/gagnées**.</span><span class="sxs-lookup"><span data-stu-id="792ec-138">We haven’t set up that part of the solution yet, so you should not set the stage to **Closed Won**.</span></span>  
  
    5.  <span data-ttu-id="792ec-139">Spécifiez des valeurs pour les autres champs facultatifs, puis cliquez **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="792ec-139">Specify values for other optional fields and then click **Save**.</span></span>  
  
    6.  <span data-ttu-id="792ec-140">Sur la page opportunité de Customer1, sous le **produits** , cliquez sur **ajouter un produit**.</span><span class="sxs-lookup"><span data-stu-id="792ec-140">On the Opportunity page for Customer1, under the **Products** section, click **Add Product**.</span></span>  
  
    7.  <span data-ttu-id="792ec-141">Dans la liste de produits, sélectionnez les produits que le client s’intéresse, puis cliquez sur **sélectionnez**.</span><span class="sxs-lookup"><span data-stu-id="792ec-141">From the list of products, select the products that the customer is interested in, and then click **Select**.</span></span>  
  
    8.  <span data-ttu-id="792ec-142">Pour chaque produit sélectionné, spécifiez une quantité voulue par le client, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="792ec-142">For each selected product, specify a quantity that the customer wants, and then click **Save**.</span></span>  
  
         <span data-ttu-id="792ec-143">![Ajouter des produits à une opportunité](../core/media/bts-sf-add-product.gif "BTS_SF_Add_Product")</span><span class="sxs-lookup"><span data-stu-id="792ec-143">![Add products to an opportunity](../core/media/bts-sf-add-product.gif "BTS_SF_Add_Product")</span></span>  
  
## <a name="create-a-salesforce-workflow"></a><span data-ttu-id="792ec-144">Créer un workflow Salesforce</span><span class="sxs-lookup"><span data-stu-id="792ec-144">Create a Salesforce Workflow</span></span>  
 <span data-ttu-id="792ec-145">Dans cette étape, nous créons un workflow pour envoyer une notification chaque fois qu'une opportunité est clôturée avec succès.</span><span class="sxs-lookup"><span data-stu-id="792ec-145">In this step we create a workflow to send out a notification every time an opportunity is closed successfully.</span></span> <span data-ttu-id="792ec-146">La notification est sous la forme d’un message SOAP et est envoyée à un point de terminaison de relais hébergé sur [!INCLUDE[winazure](../includes/winazure-md.md)] [!INCLUDE[sb](../includes/sb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="792ec-146">The notification is in the form of a SOAP message and is sent to a relay endpoint hosted on [!INCLUDE[winazure](../includes/winazure-md.md)][!INCLUDE[sb](../includes/sb-md.md)].</span></span>  
  
#### <a name="to-create-a-workflow-for-opportunities"></a><span data-ttu-id="792ec-147">Pour créer un workflow pour les opportunités</span><span class="sxs-lookup"><span data-stu-id="792ec-147">To create a workflow for opportunities</span></span>  
  
1.  <span data-ttu-id="792ec-148">Dans le portail Salesforce, cliquez sur votre nom de connexion à l’angle supérieur droit de la page, puis cliquez sur **le programme d’installation**.</span><span class="sxs-lookup"><span data-stu-id="792ec-148">On the Salesforce portal, click your login name at the top right corner of the page, and then click **Setup**.</span></span>  
  
2.  <span data-ttu-id="792ec-149">Dans le volet gauche, sous **programme d’installation de l’application**, développez **créer**, développez **Workflow & approbations**, puis cliquez sur **les règles de flux de travail**.</span><span class="sxs-lookup"><span data-stu-id="792ec-149">In the left pane, under **App Setup**, expand **Create**, expand **Workflow & Approvals**, and then click **Workflow Rules**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="792ec-150">Si vous ouvrez la page Règles de workflow pour la première fois, le système vous présente des informations pour vous permettre de comprendre comment fonctionnent les workflows dans Salesforce.</span><span class="sxs-lookup"><span data-stu-id="792ec-150">If you are opening the Workflow Rules page for the first time, you will be presented with some information to understand how workflows work in Salesforce.</span></span> <span data-ttu-id="792ec-151">Lisez les informations, puis **continuer**.</span><span class="sxs-lookup"><span data-stu-id="792ec-151">Read through the information and then click **Continue**.</span></span>  
  
3.  <span data-ttu-id="792ec-152">Sur le **toutes les règles de flux de travail** , cliquez sur **nouvelle règle**.</span><span class="sxs-lookup"><span data-stu-id="792ec-152">On the **All Workflow Rules** page, click **New Rule**.</span></span>  
  
4.  <span data-ttu-id="792ec-153">À partir de la **sélectionner un objet** , cliquez sur **opportunité**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="792ec-153">From the **Select Object** list, click **Opportunity**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="792ec-154">Dans la page suivante, spécifiez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="792ec-154">In the next page, specify the following:</span></span>  
  
    1.  <span data-ttu-id="792ec-155">Définir le **nom de règle** comme `Closed Opportunity`.</span><span class="sxs-lookup"><span data-stu-id="792ec-155">Set the **Rule Name** as `Closed Opportunity`.</span></span>  
  
    2.  <span data-ttu-id="792ec-156">Définir le **les critères d’évaluation** en tant que **créé et chaque fois qu’il est modifié pour répondre ensuite aux critères**.</span><span class="sxs-lookup"><span data-stu-id="792ec-156">Set the **Evaluation Criteria** as **created, and any time it’s edited to subsequently meet criteria**.</span></span>  
  
    3.  <span data-ttu-id="792ec-157">Pour le **critères de règles**, configuré pour s’exécuter la règle lorsque le **critères**.</span><span class="sxs-lookup"><span data-stu-id="792ec-157">For the **Rule Criteria**, set to run the rule when the **criteria are met**.</span></span>  
  
    4.  <span data-ttu-id="792ec-158">Définissez **champ** à **opportunité : étape**, **opérateur** à **est égal à**, et **valeur** à `Closed Won`.</span><span class="sxs-lookup"><span data-stu-id="792ec-158">Set **Field** to **Opportunity: Stage**, **Operator** to **equals**, and **Value** to `Closed Won`.</span></span>  
  
         <span data-ttu-id="792ec-159">![Créer un workflow Salesforce](../core/media/bts-sf-create-workflow.jpg "BTS_SF_Create_Workflow")</span><span class="sxs-lookup"><span data-stu-id="792ec-159">![Create a Salesforce workflow](../core/media/bts-sf-create-workflow.jpg "BTS_SF_Create_Workflow")</span></span>  
  
    5.  <span data-ttu-id="792ec-160">Cliquez sur **enregistrer et suivant**.</span><span class="sxs-lookup"><span data-stu-id="792ec-160">Click **Save & Next**.</span></span>  
  
6.  <span data-ttu-id="792ec-161">Définissez l'action de workflow pour la nouvelle règle :</span><span class="sxs-lookup"><span data-stu-id="792ec-161">Define the workflow action for the new rule:</span></span>  
  
    1.  <span data-ttu-id="792ec-162">Sur le **spécifier des Actions de flux de travail** , cliquez sur **ajouter une Action de flux de travail** puis cliquez sur **nouveau Message sortant**.</span><span class="sxs-lookup"><span data-stu-id="792ec-162">On the **Specify Workflow Actions** page, click **Add Workflow Action** button and then click **New Outbound Message**.</span></span>  
  
    2.  <span data-ttu-id="792ec-163">Définir le **nom** et **nom Unique** champs à `NewOp1`.</span><span class="sxs-lookup"><span data-stu-id="792ec-163">Set the **Name** and **Unique Name** fields to `NewOp1`.</span></span>  
  
    3.  <span data-ttu-id="792ec-164">Spécifiez une description, tels que le `Message sent when an opportunity is successfully closed`.</span><span class="sxs-lookup"><span data-stu-id="792ec-164">Specify a description, such as, the `Message sent when an opportunity is successfully closed`.</span></span>  
  
    4.  <span data-ttu-id="792ec-165">Spécifiez le **URL de point de terminaison** comme `https://btssalesforce.servicebus.windows.net/notifications/opportunity`.</span><span class="sxs-lookup"><span data-stu-id="792ec-165">Specify the **Endpoint URL** as `https://btssalesforce.servicebus.windows.net/notifications/opportunity`.</span></span>  
  
         <span data-ttu-id="792ec-166">Ici, **btssalesforce** est votre [!INCLUDE[sb](../includes/sb-md.md)] espace de noms que vous avez créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="792ec-166">Here, **btssalesforce** is your [!INCLUDE[sb](../includes/sb-md.md)] namespace that you created in earlier steps.</span></span> <span data-ttu-id="792ec-167">**/notifications/opportunity/** représente le relais que nous allons créer dans les étapes ultérieures de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="792ec-167">**/notifications/opportunity/** represents the relay that we will create in later steps of this tutorial.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="792ec-168">Vous devez spécifier l'espace de noms [!INCLUDE[sb](../includes/sb-md.md)] que vous avez créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="792ec-168">You must specify the [!INCLUDE[sb](../includes/sb-md.md)] namespace that you created earlier.</span></span>  
  
    5.  <span data-ttu-id="792ec-169">Assurez-vous que le **composant protégé** case à cocher est désactivée et la **envoyer un ID de Session** case à cocher est activée.</span><span class="sxs-lookup"><span data-stu-id="792ec-169">Make sure the **Protected Component** check box is clear and the **Send Session ID** check box is checked.</span></span>  
  
    6.  <span data-ttu-id="792ec-170">Pour **opportunité aux champs pour envoyer** sélectionner à partir de la **champs disponibles** liste, puis cliquez sur le **ajouter** bouton.</span><span class="sxs-lookup"><span data-stu-id="792ec-170">For **Opportunity fields to send** select the relevant fields from the **Available Fields** list and then click the **Add** button.</span></span>  
  
    7.  <span data-ttu-id="792ec-171">Cliquez sur **enregistrer** puis cliquez sur **fait**.</span><span class="sxs-lookup"><span data-stu-id="792ec-171">Click **Save** and then click **Done**.</span></span>  
  
    8.  <span data-ttu-id="792ec-172">Dans le volet gauche, sous **programme d’installation de l’application**, développez **créer**, développez **Workflow & approbations**, puis cliquez sur **les règles de flux de travail**.</span><span class="sxs-lookup"><span data-stu-id="792ec-172">In the left pane, under **App Setup**, expand **Create**, expand **Workflow & Approvals**, and then click **Workflow Rules**.</span></span> <span data-ttu-id="792ec-173">Vérifiez que le **opportunité fermée** règle y sont répertoriée.</span><span class="sxs-lookup"><span data-stu-id="792ec-173">Verify that the **Closed Opportunity** rule is listed there.</span></span> <span data-ttu-id="792ec-174">Sous le **Action** colonne pour le **opportunité fermée** de règles, cliquez sur **activer** pour activer la règle.</span><span class="sxs-lookup"><span data-stu-id="792ec-174">Under the **Action** column for the **Closed Opportunity** rule, click **Activate** to activate the rule.</span></span>  
  
## <a name="create-a-salesforce-connected-application"></a><span data-ttu-id="792ec-175">Créer une application connectée Salesforce</span><span class="sxs-lookup"><span data-stu-id="792ec-175">Create a Salesforce Connected Application</span></span>  
 <span data-ttu-id="792ec-176">La création d'une définition d'application connectée génère un jeu de clés nécessaires pour demander des jetons OAuth pour accéder à la connexion à Salesforce.</span><span class="sxs-lookup"><span data-stu-id="792ec-176">Creating a connected application definition generates a set of keys required to request OAuth tokens to access to connect to Salesforce.</span></span> <span data-ttu-id="792ec-177">Dans les phases ultérieures de ce didacticiel, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sera l'application connectée qui servira à interroger Salesforce à l'aide de la définition d'application connectée.</span><span class="sxs-lookup"><span data-stu-id="792ec-177">In the later stages of this tutorial, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will be the connected application that queries Salesforce using the connected application definition.</span></span>  
  
#### <a name="to-create-a-connected-application-for-salesforce"></a><span data-ttu-id="792ec-178">Pour créer une application connectée pour Salesforce</span><span class="sxs-lookup"><span data-stu-id="792ec-178">To create a connected application for Salesforce</span></span>  
  
1.  <span data-ttu-id="792ec-179">Dans le portail Salesforce, cliquez sur votre nom de connexion à l’angle supérieur droit de la page, puis cliquez sur **le programme d’installation**.</span><span class="sxs-lookup"><span data-stu-id="792ec-179">On the Salesforce portal, click your login name at the top right corner of the page, and then click **Setup**.</span></span>  
  
2.  <span data-ttu-id="792ec-180">Dans le volet gauche, sous **programme d’installation de l’application**, développez **créer**, puis développez **applications**.</span><span class="sxs-lookup"><span data-stu-id="792ec-180">In the left pane, under **App Setup**, expand **Create**, and then expand **Apps**.</span></span> <span data-ttu-id="792ec-181">Sur le **applications** sous le **applications connectées** , cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="792ec-181">On the **Apps** page, under the **Connected Apps** section, click **New**.</span></span>  
  
3.  <span data-ttu-id="792ec-182">Dans le **nouvelle application de connexion** , spécifiez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="792ec-182">In the **New Connection App** page, specify the following:</span></span>  
  
    1.  <span data-ttu-id="792ec-183">Pour **nom d’application connectée**, spécifiez `BizTalk_Salesforce`.</span><span class="sxs-lookup"><span data-stu-id="792ec-183">For **Connected App Name**, specify `BizTalk_Salesforce`.</span></span>  
  
    2.  <span data-ttu-id="792ec-184">Pour **nom du développeur**, spécifier votre journal sur le nom.</span><span class="sxs-lookup"><span data-stu-id="792ec-184">For **Developer Name**, specify your log on name.</span></span>  
  
    3.  <span data-ttu-id="792ec-185">Pour **messagerie du Contact**, spécifiez votre adresse de messagerie.</span><span class="sxs-lookup"><span data-stu-id="792ec-185">For **Contact Email**, specify your e-mail.</span></span>  
  
    4.  <span data-ttu-id="792ec-186">Pour **URL de rappel**, spécifiez une URL valide.</span><span class="sxs-lookup"><span data-stu-id="792ec-186">For **Callback URL**, specify a valid URL.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="792ec-187">Compte tenu de la façon dont nous nous authentifions auprès de Salesforce dans ce scénario, la valeur que vous indiquez ici n'est pas utilisée.</span><span class="sxs-lookup"><span data-stu-id="792ec-187">Because of the way we authenticate with Salesforce in this scenario, the value you specify here is not used.</span></span>  
  
    5.  <span data-ttu-id="792ec-188">Sous **portées OAuth disponibles**, sélectionnez **accès complet**, **effectue des demandes à votre place à tout moment**, et **accès et de gérer vos données**puis cliquez sur le **ajouter** bouton pour les déplacer vers le **portées OAuth sélectionnées**.</span><span class="sxs-lookup"><span data-stu-id="792ec-188">Under **Available OAuth Scopes**, select **Full access**, **Perform requests on your behalf at any time**, and **Access and manage your data** and then click the **Add** button to move them into the **Selected OAuth Scopes**.</span></span>  
  
    6.  <span data-ttu-id="792ec-189">Cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="792ec-189">Click **Save**.</span></span> <span data-ttu-id="792ec-190">La page qui apparaît contient des informations sur la **clé de consommateur** et **Secret de consommateur**.</span><span class="sxs-lookup"><span data-stu-id="792ec-190">The page that appears contains information about the **Consumer Key** and **Consumer Secret**.</span></span> <span data-ttu-id="792ec-191">Vous devez prendre note de ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="792ec-191">You must make a note of these values.</span></span> <span data-ttu-id="792ec-192">Vous en aurez besoin lors de la connexion à Salesforce à partir de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="792ec-192">You will need these values while connecting to Salesforce from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
         <span data-ttu-id="792ec-193">![Touches d’accès de la force de vente](../core/media/bts-sf-consumer-keys.jpg "BTS_SF_Consumer_Keys")</span><span class="sxs-lookup"><span data-stu-id="792ec-193">![Keys for Salesforce access](../core/media/bts-sf-consumer-keys.jpg "BTS_SF_Consumer_Keys")</span></span>  
  
4.  <span data-ttu-id="792ec-194">Enfin, générez un jeton de sécurité requis pour la connexion à Salesforce à partir de sites réseau inconnus.</span><span class="sxs-lookup"><span data-stu-id="792ec-194">Finally, generate a security token required for connecting to Salesforce from unknown network locations.</span></span>  
  
    1.  <span data-ttu-id="792ec-195">Dans le volet gauche du portail Salesforce, sous **configuration personnel**, développez **personnelles**, puis cliquez sur **Reset My Security Token**.</span><span class="sxs-lookup"><span data-stu-id="792ec-195">On the left pane of the Salesforce portal, under **Personal Setup**, expand **Personal Information**, and then click **Reset My Security Token**.</span></span>  
  
    2.  <span data-ttu-id="792ec-196">Lisez l’avertissement, puis cliquez sur **Reset Security Token**.</span><span class="sxs-lookup"><span data-stu-id="792ec-196">Read the warning and then click **Reset Security Token**.</span></span>  
  
    3.  <span data-ttu-id="792ec-197">Vous devriez recevoir le jeton de sécurité à l'adresse e-mail que vous avez spécifiée lors de la création de votre compte Salesforce.</span><span class="sxs-lookup"><span data-stu-id="792ec-197">You should receive the security token at the e-mail address you specified while creating your Salesforce account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="792ec-198">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="792ec-198">See Also</span></span>  
 [<span data-ttu-id="792ec-199">Didacticiel 6 : Intégration de BizTalk Server 2013 avec Salesforce</span><span class="sxs-lookup"><span data-stu-id="792ec-199">Tutorial 6: Integrating BizTalk Server 2013 with Salesforce</span></span>](Tutorial:%20Integrating%20BizTalk%20Server%202013%20with%20Salesforce.md)