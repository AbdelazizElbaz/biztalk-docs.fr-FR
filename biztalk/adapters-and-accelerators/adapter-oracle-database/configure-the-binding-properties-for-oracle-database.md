---
title: "Configurer les propriétés de liaison pour la base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding properties, specifying at run time
- binding properties, specifying at design time
ms.assetid: c59a1b5c-b52b-4161-82de-c4d89bfce5c7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73b7a5205b2fbfe0bc42bf5af0930356a003d5be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-binding-properties-for-oracle-database"></a><span data-ttu-id="46a00-102">Configurer les propriétés de liaison pour la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="46a00-102">Configure the binding properties for Oracle Database</span></span>
<span data-ttu-id="46a00-103">Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] expose plusieurs propriétés de liaison qui vous permettent de contrôler certaines de ses caractéristiques de comportement.</span><span class="sxs-lookup"><span data-stu-id="46a00-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces several binding properties that enable you to control some of its behavioral characteristics.</span></span> <span data-ttu-id="46a00-104">Cette section fournit des informations sur la définition des propriétés de liaison à partir de Visual Studio et à partir de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="46a00-104">This section provides information about setting the binding properties from Visual Studio and from the BizTalk Server Administration console.</span></span> <span data-ttu-id="46a00-105">À partir de Visual Studio, vous devez spécifier les propriétés de liaison lors de la génération de schéma pour des opérations spécifiques.</span><span class="sxs-lookup"><span data-stu-id="46a00-105">From Visual Studio, you must specify the binding properties while generating schema for specific operations.</span></span> <span data-ttu-id="46a00-106">À partir de BizTalk Server, vous devez spécifier les propriétés de liaison dans le cadre de l’envoi ou le port de réception pour envoyer ou recevoir des messages à partir de la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="46a00-106">From BizTalk Server, you must specify the binding properties as part of the send or receive port for sending or receiving messages from the Oracle database.</span></span>  
  
 <span data-ttu-id="46a00-107">Pour plus d’informations sur les propriétés de liaison, notamment une liste de propriétés de liaison pour [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="46a00-107">For information about the binding properties, including a list of binding properties for [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span>  
  
## <a name="specifying-binding-properties-from-visual-studio"></a><span data-ttu-id="46a00-108">Spécification de propriétés de liaison à partir de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="46a00-108">Specifying Binding Properties from Visual Studio</span></span>  
 <span data-ttu-id="46a00-109">À partir de Visual Studio, vous devez spécifier les informations d’identification à l’aide de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46a00-109">From Visual Studio, you must specify the credentials using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span>  
  
#### <a name="to-specify-binding-properties-using-consume-adapter-service-add-in"></a><span data-ttu-id="46a00-110">Pour spécifier les propriétés de liaison à l’aide de complément Consume Adapter Service</span><span class="sxs-lookup"><span data-stu-id="46a00-110">To specify binding properties using Consume Adapter Service Add-in</span></span>  
  
1.  <span data-ttu-id="46a00-111">Avec le bouton droit de votre projet BizTalk, puis sélectionnez **ajouter les éléments générés**.</span><span class="sxs-lookup"><span data-stu-id="46a00-111">Right-click your BizTalk project and then select **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="46a00-112">Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="46a00-112">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="46a00-113">Utiliser</span><span class="sxs-lookup"><span data-stu-id="46a00-113">Use this</span></span>|<span data-ttu-id="46a00-114">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="46a00-114">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="46a00-115">**Catégories**</span><span class="sxs-lookup"><span data-stu-id="46a00-115">**Categories**</span></span>|<span data-ttu-id="46a00-116">Cliquez sur **Consume Adapter Service**.</span><span class="sxs-lookup"><span data-stu-id="46a00-116">Click **Consume Adapter Service**.</span></span>|  
    |<span data-ttu-id="46a00-117">**Modèles**</span><span class="sxs-lookup"><span data-stu-id="46a00-117">**Templates**</span></span>|<span data-ttu-id="46a00-118">Cliquez sur **Consume Adapter Service**.</span><span class="sxs-lookup"><span data-stu-id="46a00-118">Click **Consume Adapter Service**.</span></span>|  
  
3.  <span data-ttu-id="46a00-119">Pour démarrer le **Consume Adapter Service** boîte de dialogue, cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="46a00-119">To start the **Consume Adapter Service** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="46a00-120">Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** liste déroulante, sélectionnez **oracleDBBinding**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="46a00-120">In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list select **oracleDBBinding**, and click **Configure**.</span></span>  
  
5.  <span data-ttu-id="46a00-121">Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **propriétés de liaison** onglet et spécifier les propriétés de liaison différents.</span><span class="sxs-lookup"><span data-stu-id="46a00-121">In the **Configure Adapter** dialog box, click the **Binding Properties** tab and specify the different binding properties.</span></span>  
  
6.  <span data-ttu-id="46a00-122">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="46a00-122">Click **OK**.</span></span>  
  
#### <a name="to-specify-binding-properties-using-add-adapter-metadata-wizard"></a><span data-ttu-id="46a00-123">Pour spécifier les propriétés de liaison à l’aide d’Assistant Ajouter les métadonnées de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="46a00-123">To specify binding properties using Add Adapter Metadata Wizard</span></span>  
  
1.  <span data-ttu-id="46a00-124">Avec le bouton droit de votre projet BizTalk, puis sélectionnez **ajouter les éléments générés**.</span><span class="sxs-lookup"><span data-stu-id="46a00-124">Right-click your BizTalk project and then select **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="46a00-125">Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="46a00-125">In the **Add Generated Items** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="46a00-126">Utiliser</span><span class="sxs-lookup"><span data-stu-id="46a00-126">Use this</span></span>|<span data-ttu-id="46a00-127">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="46a00-127">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="46a00-128">**Catégories**</span><span class="sxs-lookup"><span data-stu-id="46a00-128">**Categories**</span></span>|<span data-ttu-id="46a00-129">Cliquez sur **ajouter l’adaptateur**.</span><span class="sxs-lookup"><span data-stu-id="46a00-129">Click **Add Adapter**.</span></span>|  
    |<span data-ttu-id="46a00-130">**Modèles**</span><span class="sxs-lookup"><span data-stu-id="46a00-130">**Templates**</span></span>|<span data-ttu-id="46a00-131">Cliquez sur **ajouter les métadonnées de l’adaptateur**.</span><span class="sxs-lookup"><span data-stu-id="46a00-131">Click **Add Adapter Metadata**.</span></span>|  
  
3.  <span data-ttu-id="46a00-132">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="46a00-132">Click **Add**.</span></span> <span data-ttu-id="46a00-133">L’Assistant Ajout de métadonnées d’adaptateur s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="46a00-133">The Add Adapter Metadata Wizard opens.</span></span>  
  
4.  <span data-ttu-id="46a00-134">Dans l’Assistant Ajout de métadonnées d’adaptateur, sélectionnez **WCF-OracleDB**.</span><span class="sxs-lookup"><span data-stu-id="46a00-134">In the Add Adapter Metadata Wizard, select **WCF-OracleDB**.</span></span> <span data-ttu-id="46a00-135">Sélectionnez l’ordinateur sur lequel [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] est installé et le nom de la base de données BizTalk.</span><span class="sxs-lookup"><span data-stu-id="46a00-135">Select the computer on which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] is installed and the name of the BizTalk database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="46a00-136">Si vous disposez déjà d’un port WCF-OracleDB configuré dans BizTalk, sélectionnez le port à partir de la **Port** liste.</span><span class="sxs-lookup"><span data-stu-id="46a00-136">If you already have a WCF-OracleDB port configured in BizTalk, select the port from the **Port** list.</span></span>  
  
5.  <span data-ttu-id="46a00-137">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="46a00-137">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="46a00-138">Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** liste déroulante, sélectionnez **oracleDBBinding**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="46a00-138">In the **Consume Adapter Service** dialog box, from the **Select a binding** drop-down list select **oracleDBBinding**, and click **Configure**.</span></span>  
  
7.  <span data-ttu-id="46a00-139">Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **propriétés de liaison** onglet et spécifiez les valeurs de liaison, si elle existe, qui sont nécessaires avant de générer le schéma.</span><span class="sxs-lookup"><span data-stu-id="46a00-139">In the **Configure Adapter** dialog box, click the **Binding Properties** tab, and specify the binding values, if any, which are required before generating the schema.</span></span> <span data-ttu-id="46a00-140">Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="46a00-140">For more information about binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="46a00-141">Si vous avez sélectionné un port d’envoi WCF-OracleDB existant, vous ne devez pas spécifier les propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="46a00-141">If you selected an existing WCF-OracleDB send port, you need not specify the binding properties.</span></span> <span data-ttu-id="46a00-142">Les propriétés de liaison sont récupérées à partir de la configuration du port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="46a00-142">The binding properties are picked from the send port configuration.</span></span> <span data-ttu-id="46a00-143">Toutefois, vous pouvez choisir de spécifier les propriétés de liaison qui sont nécessaires au moment du design, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="46a00-143">However, you may choose to specify the binding properties that are required at design-time, if any.</span></span> <span data-ttu-id="46a00-144">Dans ce cas, les nouvelles valeurs des propriétés de liaison seront utilisées au moment du design lors de la génération de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="46a00-144">In such a case, the new values for binding properties will be used at design-time while generating the metadata.</span></span> <span data-ttu-id="46a00-145">Toutefois, au moment de l’exécution les valeurs spécifiées pour les propriétés de liaison dans la configuration du port d’envoi sera appliquées.</span><span class="sxs-lookup"><span data-stu-id="46a00-145">However, at run-time the values specified for binding properties in the send port configuration will be applicable.</span></span>  
  
8.  <span data-ttu-id="46a00-146">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="46a00-146">Click **OK**.</span></span>  
  
## <a name="specifying-binding-properties-from-the-biztalk-server-administration-console"></a><span data-ttu-id="46a00-147">Spécification de propriétés de liaison à partir de la Console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="46a00-147">Specifying Binding Properties from the BizTalk Server Administration Console</span></span>  
 <span data-ttu-id="46a00-148">Dans la console Administration de BizTalk Server, vous devez spécifier les propriétés de liaison dans le cadre de la configuration du port WCF-Custom ou WCF-OracleDB.</span><span class="sxs-lookup"><span data-stu-id="46a00-148">From the BizTalk Server Administration console, you must specify the binding properties as part of the WCF-Custom or WCF-OracleDB port configuration.</span></span>  
  
#### <a name="to-specify-binding-properties-for-the-wcf-custom-port"></a><span data-ttu-id="46a00-149">Pour spécifier les propriétés de liaison pour le port WCF-Custom</span><span class="sxs-lookup"><span data-stu-id="46a00-149">To specify binding properties for the WCF-Custom port</span></span>  
  
1.  <span data-ttu-id="46a00-150">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="46a00-150">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="46a00-151">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** ou **Ports de réception**.</span><span class="sxs-lookup"><span data-stu-id="46a00-151">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="46a00-152">Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.</span><span class="sxs-lookup"><span data-stu-id="46a00-152">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
3.  <span data-ttu-id="46a00-153">Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="46a00-153">In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="46a00-154">Pour afficher la boîte de dialogue de propriétés emplacement pour un port de réception, cliquez sur le **un emplacement de réception** onglet dans le volet gauche de la boîte de dialogue des propriétés de port, puis cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="46a00-154">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="46a00-155">Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **liaison** onglet.</span><span class="sxs-lookup"><span data-stu-id="46a00-155">In the **WCF-Custom Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
5.  <span data-ttu-id="46a00-156">À partir de la **Type de liaison** la liste déroulante, sélectionnez **oracleDBBinding**.</span><span class="sxs-lookup"><span data-stu-id="46a00-156">From the **Binding Type** drop-down list, select **oracleDBBinding**.</span></span>  
  
6.  <span data-ttu-id="46a00-157">Dans le **Configuration** zone, spécifiez les valeurs pour les propriétés de liaison différente, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="46a00-157">In the **Configuration** box, specify the values for the different binding properties and click **OK**.</span></span>  
  
#### <a name="to-specify-binding-properties-for-the-wcf-oracledb-port"></a><span data-ttu-id="46a00-158">Pour spécifier les propriétés de liaison pour le port WCF-OracleDB</span><span class="sxs-lookup"><span data-stu-id="46a00-158">To specify binding properties for the WCF-OracleDB port</span></span>  
  
1.  <span data-ttu-id="46a00-159">Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="46a00-159">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="46a00-160">Ajouter l’adaptateur WCF-OracleDB à la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="46a00-160">Add the WCF-OracleDB adapter to the BizTalk Server Administration console.</span></span> <span data-ttu-id="46a00-161">Pour obtenir des instructions, consultez [Ajout de l’adaptateur de base de données Oracle à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).</span><span class="sxs-lookup"><span data-stu-id="46a00-161">For instructions, see [Adding the Oracle Database Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).</span></span>  
  
3.  <span data-ttu-id="46a00-162">Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** ou **Ports de réception**.</span><span class="sxs-lookup"><span data-stu-id="46a00-162">In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**.</span></span> <span data-ttu-id="46a00-163">Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.</span><span class="sxs-lookup"><span data-stu-id="46a00-163">In the right pane, you can choose to create a port or select an existing port.</span></span>  
  
4.  <span data-ttu-id="46a00-164">Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez l’adaptateur WCF-OracleDB que vous avez ajouté précédemment, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="46a00-164">In the port properties dialog box, from the **Type** drop-down list, select the WCF-OracleDB adapter you added earlier, and then click **Configure**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="46a00-165">Pour afficher la boîte de dialogue de propriétés emplacement pour un port de réception, cliquez sur le **un emplacement de réception** onglet dans le volet gauche de la boîte de dialogue des propriétés de port, puis cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="46a00-165">To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.</span></span>  
  
5.  <span data-ttu-id="46a00-166">Dans la boîte de dialogue Propriétés du transport, cliquez sur le **liaison** onglet et spécifier les valeurs des propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="46a00-166">In the transport properties dialog box, click the **Binding** tab, and specify values for binding properties.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="46a00-167">Les propriétés de liaison sont affichées selon que vous configurez un port d’envoi ou un port de réception.</span><span class="sxs-lookup"><span data-stu-id="46a00-167">The binding properties are displayed based on whether you are configuring a send port or a receive port.</span></span> <span data-ttu-id="46a00-168">Par exemple, les propriétés de liaison liées notifications ne sont pas disponibles lors de la configuration d’un port d’envoi, car des notifications sont des opérations entrantes et nécessitent une configuration de port de réception.</span><span class="sxs-lookup"><span data-stu-id="46a00-168">For example, binding properties related to notifications are not available while configuring a send port because notifications are inbound operations and require a receive port configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46a00-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46a00-169">See Also</span></span>  
[<span data-ttu-id="46a00-170">Blocs de construction pour développer des Applications BizTalk avec la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="46a00-170">Building Blocks to develop BizTalk Applications with Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)