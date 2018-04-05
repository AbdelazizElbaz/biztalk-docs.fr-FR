---
title: 'Étape 2 : Création de schémas Application LOB Contoso pour le prix et la disponibilité de projets à l’aide de l’Éditeur BizTalk | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- private process tutorial, creating LOB schemas
ms.assetid: 70e26dc9-4299-4d30-8f8b-5cc3469a2025
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 441bb90c8fa0f2edb271af384e2540a741150137
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="step-2-creating-the-contoso-lob-application-schemas-for-the-price-and-availability-project-using-biztalk-editor"></a><span data-ttu-id="27f19-102">Étape 2 : Création de schémas Application LOB Contoso pour le prix et le projet de disponibilité à l’aide de l’Éditeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="27f19-102">Step 2: Creating the Contoso LOB Application Schemas for the Price and Availability Project Using BizTalk Editor</span></span>
<span data-ttu-id="27f19-103">Dans cette étape, vous générez le schéma à utiliser pour interroger le système ERP de Contoso pour le prix et la disponibilité d’un produit particulier.</span><span class="sxs-lookup"><span data-stu-id="27f19-103">In this step, you generate the schema to use to query the Contoso ERP system for the price and availability of a particular product.</span></span> <span data-ttu-id="27f19-104">Vous générez ce schéma en utilisant le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® l’adaptateur SQL pour BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="27f19-104">You generate this schema by using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® SQL Adapter for BizTalk Server.</span></span>  
  
### <a name="to-update-the-sql-stored-procedure-for-schema-generation"></a><span data-ttu-id="27f19-105">Pour mettre à jour l’instruction SQL de procédure stockée pour la génération de schéma</span><span class="sxs-lookup"><span data-stu-id="27f19-105">To update the SQL stored procedure for schema generation</span></span>  
  
1.  <span data-ttu-id="27f19-106">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="27f19-106">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="27f19-107">Dans Microsoft SQL Server Management Studio, développez **bases de données**, développez **Contoso**, développez **programmabilité**, puis développez **de procédures stockées** .</span><span class="sxs-lookup"><span data-stu-id="27f19-107">In the Microsoft SQL Server Management Studio, expand **Databases**, expand **Contoso**, expand **Programmability**, and then expand **Stored Procedures**.</span></span>  
  
3.  <span data-ttu-id="27f19-108">Avec le bouton droit **dbo. SP_GetInventoryForProductID**, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="27f19-108">Right-click **dbo.SP_GetInventoryForProductID**, and then click **Modify**.</span></span>  
  
4.  <span data-ttu-id="27f19-109">Dans la fenêtre de requête, insérez une virgule, un espace, puis « xmldata », « for xml auto » qui suit immédiatement.</span><span class="sxs-lookup"><span data-stu-id="27f19-109">In the query window, insert a comma, a space, and then "xmldata" immediately following "for xml auto".</span></span> <span data-ttu-id="27f19-110">La ligne de code doit être la suivante :</span><span class="sxs-lookup"><span data-stu-id="27f19-110">The line of code should be the following:</span></span>  
  
    ```  
    for xml auto, xmldata  
    ```  
  
5.  <span data-ttu-id="27f19-111">Cliquez sur **Execute** pour enregistrer les modifications apportées à la procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="27f19-111">Click **Execute** to save the changes to the stored procedure.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="27f19-112">Microsoft SQL Server Management Studio laissez ouverte pour exécuter la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="27f19-112">Leave the Microsoft SQL Server Management Studio open for the next procedure.</span></span>  
  
### <a name="to-create-the-contoso-price-and-availability-schema"></a><span data-ttu-id="27f19-113">Pour créer le schéma de Contoso Price et la disponibilité</span><span class="sxs-lookup"><span data-stu-id="27f19-113">To create the Contoso Price and Availability schema</span></span>  
  
1.  <span data-ttu-id="27f19-114">Ouvrez la solution Contoso dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="27f19-114">Open the Contoso solution in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="27f19-115">Dans l’Explorateur de solutions, cliquez sur le **ContosoPriceAndAvailability** de projet, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.</span><span class="sxs-lookup"><span data-stu-id="27f19-115">In Solution Explorer, right-click the **ContosoPriceAndAvailability** project, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
3.  <span data-ttu-id="27f19-116">Dans la boîte de dialogue Ajouter un Iems généré avec **ajouter les métadonnées de l’adaptateur** sélectionné dans le volet gauche, cliquez sur **ajouter les métadonnées de l’adaptateur** dans le volet droit, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="27f19-116">In the Add Generated Iems dialog box, with **Add Adapter Metadata** selected in the left pane, click **Add Adapter Metadata** in the right pane, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="27f19-117">Sur le **Assistant Ajout d’adaptateur** page, sélectionnez **SQL** dans la liste des adaptateurs inscrits, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="27f19-117">On the **Add Adapter Wizard** page, select **SQL** from the list of registered adapters, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="27f19-118">Sur le **les informations de base de données** , cliquez sur **définir**.</span><span class="sxs-lookup"><span data-stu-id="27f19-118">On the **Database Information** page, click **Set**.</span></span>  
  
6.  <span data-ttu-id="27f19-119">Dans la boîte de dialogue Propriétés des liaisons de données, dans la zone **Sélectionnez un serveur ou entrez un nom de serveur** , tapez **localhost**.</span><span class="sxs-lookup"><span data-stu-id="27f19-119">In the Data Link Properties dialog box, in the **Select or enter a server name** box, type **localhost**.</span></span> <span data-ttu-id="27f19-120">Sélectionnez **Utiliser la sécurité intégrée de Windows NT**.</span><span class="sxs-lookup"><span data-stu-id="27f19-120">Select **Use Windows NT Integrated security**.</span></span> <span data-ttu-id="27f19-121">Pour **sélectionner la base de données sur le serveur**, sélectionnez le **Contoso** base de données à partir de la liste de la base de données.</span><span class="sxs-lookup"><span data-stu-id="27f19-121">For **Select the database on the server**, select the **Contoso** database from the database list.</span></span> <span data-ttu-id="27f19-122">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="27f19-122">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="27f19-123">Sur le **les informations de base de données** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="27f19-123">On the **Database Information** page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="27f19-124">Sur le **informations de schéma** page, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="27f19-124">On the **Schema Information** page, do the following:</span></span>  
  
    |<span data-ttu-id="27f19-125">Utiliser</span><span class="sxs-lookup"><span data-stu-id="27f19-125">Use this</span></span>|<span data-ttu-id="27f19-126">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="27f19-126">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="27f19-127">**Espace de noms cible**</span><span class="sxs-lookup"><span data-stu-id="27f19-127">**Target namespace**</span></span>|<span data-ttu-id="27f19-128">Type **http://Contoso.com/Price**.</span><span class="sxs-lookup"><span data-stu-id="27f19-128">Type **http://Contoso.com/Price**.</span></span>|  
    |<span data-ttu-id="27f19-129">**Sélectionnez le type de port**</span><span class="sxs-lookup"><span data-stu-id="27f19-129">**Select the port type**</span></span>|<span data-ttu-id="27f19-130">Sélectionnez **port d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="27f19-130">Select **Send port**.</span></span>|  
    |<span data-ttu-id="27f19-131">**Nom de l’élément racine demande de document**</span><span class="sxs-lookup"><span data-stu-id="27f19-131">**Request document root element name**</span></span>|<span data-ttu-id="27f19-132">Type **rootPriceRequest**.</span><span class="sxs-lookup"><span data-stu-id="27f19-132">Type **rootPriceRequest**.</span></span>|  
    |<span data-ttu-id="27f19-133">**Nom d’élément de réponse document racine**</span><span class="sxs-lookup"><span data-stu-id="27f19-133">**Response document root element name**</span></span>|<span data-ttu-id="27f19-134">Type **rootPriceResponse**.</span><span class="sxs-lookup"><span data-stu-id="27f19-134">Type **rootPriceResponse**.</span></span>|  
  
9. <span data-ttu-id="27f19-135">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="27f19-135">Click **Next**.</span></span>  
  
10. <span data-ttu-id="27f19-136">Sur le **informations de type d’instruction** page, sélectionnez **la procédure stockée**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="27f19-136">On the **Statement type information** page, select **Stored Procedure**, and then click **Next**.</span></span>  
  
11. <span data-ttu-id="27f19-137">Sur le **instruction informations** page, pour  **\<sélectionner une procédure stockée\>**, sélectionnez **SP_GetInventoryForProductID** à partir de la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="27f19-137">On the **Statement Information** page, for **\<Select a stored procedure\>**, select **SP_GetInventoryForProductID** from the drop-down list.</span></span> <span data-ttu-id="27f19-138">Cliquez sur **générer**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="27f19-138">Click **Generate**, and then click **Next**.</span></span>  
  
12. <span data-ttu-id="27f19-139">Sur le **fin de l’Assistant génération de schéma de Transport SQL** , cliquez sur **Terminer** pour importer le schéma dans le projet ContosoPriceAndAvailability BizTalk.</span><span class="sxs-lookup"><span data-stu-id="27f19-139">On the **Completing the SQL Transport Schema Generation Wizard** page, click **Finish** to import the schema into the ContosoPriceAndAvailability BizTalk project.</span></span>  
  
13. <span data-ttu-id="27f19-140">Dans l’Explorateur de solutions, cliquez sur le schéma généré (SQLService_Price.xsd), cliquez sur **renommer**et le type **ContosoPriceAndAvailability.xsd** comme nouveau nom pour le schéma.</span><span class="sxs-lookup"><span data-stu-id="27f19-140">In Solution Explorer, right-click the generated schema (SQLService_Price.xsd), click **Rename**, and type **ContosoPriceAndAvailability.xsd** as the new name for the schema.</span></span> <span data-ttu-id="27f19-141">Cliquez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="27f19-141">Click **Enter**.</span></span>  
  
14. <span data-ttu-id="27f19-142">Dans la fenêtre Propriétés pour le schéma ContosoPriceAndAvailability, définissez le **nom de Type** propriété **ContosoPriceSchema**.</span><span class="sxs-lookup"><span data-stu-id="27f19-142">In the Properties window for the ContosoPriceAndAvailability schema, set the **Type Name** property to **ContosoPriceSchema**.</span></span>  
  
15. <span data-ttu-id="27f19-143">Par défaut, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] crée une orchestration BizTalk nommée **Biztalkorchestration.odx**.</span><span class="sxs-lookup"><span data-stu-id="27f19-143">By default, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] creates a BizTalk orchestration named **BizTalk Orchestration.odx**.</span></span> <span data-ttu-id="27f19-144">Avec le bouton droit de cette orchestration, puis cliquez sur **supprimer** , car vous n’avez pas besoin de cette orchestration.</span><span class="sxs-lookup"><span data-stu-id="27f19-144">Right-click this orchestration, and then click **Delete** because you do not need this orchestration.</span></span> <span data-ttu-id="27f19-145">Dans la fenêtre contextuelle indiquant que l’orchestration est définitivement supprimée, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="27f19-145">In the popup indicating that the orchestration will be deleted permanently, click **OK**.</span></span>  
  
16. <span data-ttu-id="27f19-146">Dans Microsoft SQL Server Management Studio, supprimez le `xmldata` prédicat et la virgule à partir de la `SP_GetInventoryForProductID` procédure stockée que vous avez ajouté à l’étape précédente, puis cliquez sur **Execute**.</span><span class="sxs-lookup"><span data-stu-id="27f19-146">In the Microsoft SQL Server Management Studio, remove the `xmldata` predicate and the comma from the `SP_GetInventoryForProductID` stored procedure that you added in the previous step, and then click **Execute**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27f19-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27f19-147">See Also</span></span>  
 [<span data-ttu-id="27f19-148">Étape 3 : Création de mappages d’application LOB Contoso pour le projet de prix et de disponibilité à l’aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="27f19-148">Step 3: Creating the Contoso LOB Application Maps for the Price and Availability Project Using BizTalk Mapper</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-create-contoso-lob-application-map-for-price-and-availability-in-mapper.md)