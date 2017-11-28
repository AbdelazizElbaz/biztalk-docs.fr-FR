---
title: "Utilisez l’adaptateur de base de données Oracle avec SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 254204e5-3b5d-4e70-97ab-817660d1206a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a5866344e666c9e9cb49af6c6d99211774a2758
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2017
---
# <a name="use-the-oracle-database-adapter-with-sharepoint"></a><span data-ttu-id="6cc41-102">Utilisez l’adaptateur de base de données Oracle avec SharePoint</span><span class="sxs-lookup"><span data-stu-id="6cc41-102">Use the Oracle Database Adapter with SharePoint</span></span>
<span data-ttu-id="6cc41-103">L’Assistant de développement de services de l’adaptateur WCF pour [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)] permet à l’adaptateur Microsoft BizTalk pour base de données Oracle et l’adaptateur Microsoft BizTalk pour Oracle E-Business Suite être utilisés directement comme une source de données externe dans Microsoft SharePoint.</span><span class="sxs-lookup"><span data-stu-id="6cc41-103">The WCF Adapter Service Development Wizard for [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)] enables the Microsoft BizTalk Adapter for Oracle Database and the Microsoft BizTalk Adapter for Oracle E-Business Suite to be directly consumed as an external datasource in Microsoft SharePoint.</span></span> <span data-ttu-id="6cc41-104">L’Assistant Ajout de développement Service qui prend en charge cette fonctionnalité est lancé avec le **Service d’adaptateur WCF** modèle pour créer un nouveau Visual C# Sites Web dans [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6cc41-104">The Add Service Development Wizard that supports this feature is launched with the **WCF Adapter Service** template for creating a new Visual C# Web Sites in [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="6cc41-105">Le modèle est inclus avec le [!INCLUDE[adapterpacknoversion_md](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6cc41-105">The template is included with the [!INCLUDE[adapterpacknoversion_md](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="6cc41-106">Vous devez également installer le SDK de l’adaptateur de métier (LOB) de Microsoft Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6cc41-106">You must also install the Microsoft Windows Communication Foundation (WCF) Line of Business (LOB) Adapter SDK.</span></span>  
  
## <a name="sharepoint-operation-support"></a><span data-ttu-id="6cc41-107">Prise en charge de SharePoint opération</span><span class="sxs-lookup"><span data-stu-id="6cc41-107">SharePoint Operation Support</span></span>  
 <span data-ttu-id="6cc41-108">L’Assistant de développement de services de l’adaptateur génère un contrat de service spéciales pour les adaptateurs Oracle qui est compatible avec Microsoft SharePoint.</span><span class="sxs-lookup"><span data-stu-id="6cc41-108">The Adapter Service Development wizard generates a special service contract for the Oracle adapters that is compatible with Microsoft SharePoint.</span></span> <span data-ttu-id="6cc41-109">L’Assistant génère un contrat de service qui inclut les opérations suivantes pour l’intégration de l’adaptateur avec Microsoft SharePoint :</span><span class="sxs-lookup"><span data-stu-id="6cc41-109">The wizard will generate a service contract which includes the following operations for integrating the adapter with Microsoft SharePoint:</span></span>  
  
-   <span data-ttu-id="6cc41-110">**Créer :** pris en charge par l’opération CreateItem_.</span><span class="sxs-lookup"><span data-stu-id="6cc41-110">**Create:** Supported by the CreateItem_ operation.</span></span>  
  
-   <span data-ttu-id="6cc41-111">**Lecture :** pris en charge par l’opération ReadItem_.</span><span class="sxs-lookup"><span data-stu-id="6cc41-111">**Read:** Supported by the ReadItem_ operation.</span></span>  
  
-   <span data-ttu-id="6cc41-112">**Mise à jour :** pris en charge par l’opération UpdateItem_.</span><span class="sxs-lookup"><span data-stu-id="6cc41-112">**Update:** Supported by the UpdateItem_ operation.</span></span>  
  
-   <span data-ttu-id="6cc41-113">**Suppression :** pris en charge par l’opération DeleteItem_.</span><span class="sxs-lookup"><span data-stu-id="6cc41-113">**Delete:** Supported by the DeleteItem_ operation.</span></span>  
  
-   <span data-ttu-id="6cc41-114">**Requête :** pris en charge par l’opération ReadList.</span><span class="sxs-lookup"><span data-stu-id="6cc41-114">**Query:** Supported by the ReadList operation.</span></span>  
  
-   <span data-ttu-id="6cc41-115">**Associer :** pris en charge par l’opération Associate_.</span><span class="sxs-lookup"><span data-stu-id="6cc41-115">**Associate:** Supported by the Associate_ operation.</span></span>  
  
 <span data-ttu-id="6cc41-116">Le contrat de service suivant a été généré à l’aide de l’adaptateur Microsoft BizTalk pour base de données Oracle par exemple.</span><span class="sxs-lookup"><span data-stu-id="6cc41-116">The following service contract was generated using for the Microsoft BizTalk Adapter for Oracle Database as an example.</span></span> <span data-ttu-id="6cc41-117">L’adaptateur est configuré pour fournir un accès à la table EMP</span><span class="sxs-lookup"><span data-stu-id="6cc41-117">The adapter is configured to provide access to the EMP table</span></span>  
  
```  
    [System.ServiceModel.ServiceContractAttribute()]  
    public interface ISCOTT_EMP {  
  
    [System.ServiceModel.OperationContractAttribute()]  
    SCOTT_EMP_Record[] ReadList(System.Nullable<int> Limit);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    void CreateItem(SCOTT_EMP_Record Input);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    SCOTT_EMP_Record[] ReadItem_EMPNO(System.Nullable<decimal> EMPNO);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    void UpdateItem_EMPNO(SCOTT_EMP_Record Input);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    void DeleteItem_EMPNO(System.Nullable<decimal> EMPNO);  
  
    [System.ServiceModel.OperationContractAttribute()]  
    SCOTT_EMP_Record[] Associate_DEPTNO(System.Nullable<decimal> DEPTNO);  
}  
```  
  
## <a name="create-a-new-web-site-to-host-the-oracle-database-in-iis"></a><span data-ttu-id="6cc41-118">Créer un nouveau Site Web pour héberger la base de données Oracle dans IIS</span><span class="sxs-lookup"><span data-stu-id="6cc41-118">Create a New Web Site to Host the Oracle Database in IIS</span></span>  
 <span data-ttu-id="6cc41-119">Ces étapes fournissent un exemple d’utilisation de l’Assistant de développement Service de l’adaptateur WCF, pour créer un service web WCF hébergeant l’adaptateur Microsoft BizTalk pour base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="6cc41-119">These steps provide an example using the WCF Adapter Service Development Wizard, to create a new WCF web service hosting the Microsoft BizTalk Adapter for Oracle Database.</span></span> <span data-ttu-id="6cc41-120">Le contrat de service inclut des opérations directement compatibles avec Sharepoint.</span><span class="sxs-lookup"><span data-stu-id="6cc41-120">The service contract will include operations directly compatible with Sharepoint.</span></span> <span data-ttu-id="6cc41-121">Afin que celles-ci peuvent être directement consommées comme une source de données externe.</span><span class="sxs-lookup"><span data-stu-id="6cc41-121">So that it can be directly consumed as an external datasource.</span></span> <span data-ttu-id="6cc41-122">L’adaptateur est configuré pour s’authentifier auprès de la base de données Oracle à l’aide du **SCOTT** compte.</span><span class="sxs-lookup"><span data-stu-id="6cc41-122">The adapter is configured to authenticate with the Oracle database using the **SCOTT** account.</span></span> <span data-ttu-id="6cc41-123">Si le **SCOTT** compte est verrouillé, vous pouvez déverrouiller le compte en vous connectant à SQL Plus tant que SYSDBA.</span><span class="sxs-lookup"><span data-stu-id="6cc41-123">If the **SCOTT** account is locked, you can unlock the account by logging into SQL Plus as SYSDBA.</span></span>  
  
```  
<Oracle Installation Bin Directory>\Sqlplus.exe SYS AS SYSDBA  
```  
  
 <span data-ttu-id="6cc41-124">Puis exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="6cc41-124">Then run the following command.</span></span>  
  
```  
SQL> ALTER USER scott ACCOUNT UNLOCK;  
```  
  
#### <a name="create-the-new-web-site-project"></a><span data-ttu-id="6cc41-125">Créer le projet de Site Web</span><span class="sxs-lookup"><span data-stu-id="6cc41-125">Create the New Web Site Project</span></span>  
  
1.  <span data-ttu-id="6cc41-126">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6cc41-126">Open Visual Studio.</span></span>   
  
2.  <span data-ttu-id="6cc41-127">Dans Visual Studio, sur le **fichier** menu, sélectionnez **nouveau** puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="6cc41-127">In Visual Studio, on the **File** menu, select **New** and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="6cc41-128">Dans le **nouveau projet** boîte de dialogue, développez **autres langages** et cliquez sur **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="6cc41-128">In the **New Project** dialog box, expand **Other Languages** and click **Visual C#**.</span></span> <span data-ttu-id="6cc41-129">Rechercher les **Service d’adaptateur WCF** dans le modèle de liste et cliquez dessus pour le sélectionner.</span><span class="sxs-lookup"><span data-stu-id="6cc41-129">Find the **WCF Adapter Service** in the template list and click it to select it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6cc41-130">Le **Service d’adaptateur WCF** modèle n’est pas disponible si le [!INCLUDE[adapterpackcurrent](../../includes/adapterpackcurrent-md.md)] n’est pas installé.</span><span class="sxs-lookup"><span data-stu-id="6cc41-130">The **WCF Adapter Service** template is not available if the [!INCLUDE[adapterpackcurrent](../../includes/adapterpackcurrent-md.md)] is not installed.</span></span> <span data-ttu-id="6cc41-131">Sur x64 systèmes, installez les versions x86 et x64 de la [!INCLUDE[adapterpackcurrent](../../includes/adapterpackcurrent-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6cc41-131">On x64 systems, install both the x86 and x64 versions of the [!INCLUDE[adapterpackcurrent](../../includes/adapterpackcurrent-md.md)].</span></span>  
  
4.  <span data-ttu-id="6cc41-132">Spécifiez **ScottEMP** pour le nom, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6cc41-132">Specify **ScottEMP** for the name, and then click **OK**.</span></span> <span data-ttu-id="6cc41-133">Le **Assistant développement d’adaptateurs WCF** démarre.</span><span class="sxs-lookup"><span data-stu-id="6cc41-133">The **WCF Adapter Service Development Wizard** starts.</span></span>  
  
5.  <span data-ttu-id="6cc41-134">Sur le **Introduction** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6cc41-134">On the **Introduction** page, click **Next**.</span></span>  
  
6.  <span data-ttu-id="6cc41-135">Sur le **choisissez les opérations** , spécifiez la **oracleDBBinding** liaison.</span><span class="sxs-lookup"><span data-stu-id="6cc41-135">On the **Choose Operations** page, specify the **oracleDBBinding** binding.</span></span>  
  
7.  <span data-ttu-id="6cc41-136">Cliquez sur le **configurer** bouton.</span><span class="sxs-lookup"><span data-stu-id="6cc41-136">Click the **Configure** button.</span></span> <span data-ttu-id="6cc41-137">Le **configurer l’adaptateur** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="6cc41-137">The **Configure Adapter** dialog is displayed.</span></span>  
  
8.  <span data-ttu-id="6cc41-138">Sur le **sécurité** onglet, sélectionnez **nom d’utilisateur** dans les **type d’informations d’identification du Client** zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="6cc41-138">On the **Security** tab, select **Username** in the **Client credential type** dropdown list box.</span></span>  
  
9. <span data-ttu-id="6cc41-139">Entrez **SCOTT** pour l’utilisateur de nom et entrez le mot de passe du compte SCOTT.</span><span class="sxs-lookup"><span data-stu-id="6cc41-139">Enter **SCOTT** for the User name and enter the correct password for the SCOTT account.</span></span> <span data-ttu-id="6cc41-140">Le mot de passe pour le compte SCOTT **tiger**.</span><span class="sxs-lookup"><span data-stu-id="6cc41-140">The default password for the SCOTT account is **tiger**.</span></span>  
  
10. <span data-ttu-id="6cc41-141">Cliquez sur le **propriétés URI** , entrez le nom d’hôte ou adresse IP de votre serveur Oracle dans la **ServerAddress** boîte.</span><span class="sxs-lookup"><span data-stu-id="6cc41-141">Click the **URI Properties** tab, enter the IP address or host name for your Oracle server in the **ServerAddress** box.</span></span>  
  
11. <span data-ttu-id="6cc41-142">Entrez le nom d’instance correct des service de base de données Oracle dans la **ServiceName** boîte.</span><span class="sxs-lookup"><span data-stu-id="6cc41-142">Enter the correct Oracle database service instance name in the **ServiceName** box.</span></span> <span data-ttu-id="6cc41-143">Vous pouvez copier les informations de nom d’instance à partir d’Oracle Enterprise Manager.</span><span class="sxs-lookup"><span data-stu-id="6cc41-143">You can copy the instance name information from Oracle Enterprise Manager.</span></span>  
  
12. <span data-ttu-id="6cc41-144">Appuyez sur la **OK** bouton sur le **configurer l’adaptateur** boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="6cc41-144">Press the **OK** button on the **Configure Adapter** dialog</span></span>  
  
13. <span data-ttu-id="6cc41-145">Sur le **choisissez les opérations** page de l’Assistant, cliquez sur le **Connect** bouton et attendez quelques instants pour les catégories à générer pour la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="6cc41-145">On the **Choose Operations** page of the wizard, click the **Connect** button and wait a few moments for the categories to be built for the Oracle database.</span></span>  
  
14. <span data-ttu-id="6cc41-146">Une fois que les catégories sont ajoutés dans le **sélectionner une catégorie** liste, faites défiler jusqu'à **SCOTT** et développez-le.</span><span class="sxs-lookup"><span data-stu-id="6cc41-146">Once the categories are added in the **Select a category** list, scroll down to **SCOTT** and expand it.</span></span> <span data-ttu-id="6cc41-147">Puis développez **Table** et cliquez sur le **EMP** entrée de la table.</span><span class="sxs-lookup"><span data-stu-id="6cc41-147">Then expand **Table** and click the **EMP** table entry.</span></span>  
  
15. <span data-ttu-id="6cc41-148">Dans le **catégories et opérations disponibles** , sélectionnez toutes les opérations dans la liste et cliquez sur le **ajouter** bouton.</span><span class="sxs-lookup"><span data-stu-id="6cc41-148">In the **Available categories and operations** list, select all the operations in the list and click the **Add** button.</span></span> <span data-ttu-id="6cc41-149">Toutes les opérations sont ajoutées à la **ajouté des catégories et opérations** liste.</span><span class="sxs-lookup"><span data-stu-id="6cc41-149">All the operations are added to the **Added categories and operations** list.</span></span>  
  
16. <span data-ttu-id="6cc41-150">Sur le **choisissez les opérations** , cliquez sur le **suivant** bouton.</span><span class="sxs-lookup"><span data-stu-id="6cc41-150">On the **Choose Operations** page, click the **Next** button.</span></span>  
  
17. <span data-ttu-id="6cc41-151">Sur le **configurer le Service et les comportements de point de terminaison** , définissez le **UseServiceCertificate** comportement de Service **false** pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="6cc41-151">On the **Configure Service and Endpoint Behaviors** page, set the **UseServiceCertificate** Service behavior to **false** for this example.</span></span> <span data-ttu-id="6cc41-152">Puis cliquez sur le **suivant** bouton.</span><span class="sxs-lookup"><span data-stu-id="6cc41-152">Then click the **Next** button.</span></span>  
  
18. <span data-ttu-id="6cc41-153">Sur le **configurer la liaison de point de terminaison de Service et l’adresse** , cliquez sur le **appliquer** bouton.</span><span class="sxs-lookup"><span data-stu-id="6cc41-153">On the **Configure Service Endpoint Binding and Address** page, click the **Apply** button.</span></span> <span data-ttu-id="6cc41-154">Puis cliquez sur le **suivant** bouton.</span><span class="sxs-lookup"><span data-stu-id="6cc41-154">Then click the **Next** button.</span></span>  
  
19. <span data-ttu-id="6cc41-155">Sur le **Résumé** , cliquez sur le **Terminer** bouton.</span><span class="sxs-lookup"><span data-stu-id="6cc41-155">On the **Summary** page, click the **Finish** button.</span></span>  
  
20. <span data-ttu-id="6cc41-156">Cliquez sur le **générer** option de menu, puis cliquez sur **générer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="6cc41-156">Click the **Build** menu option and then click **Build Solution**.</span></span> <span data-ttu-id="6cc41-157">Vérifiez que la génération du projet a réussi sans erreurs.</span><span class="sxs-lookup"><span data-stu-id="6cc41-157">Verify the project build was successful with no errors.</span></span>  
  
## <a name="publish-the-new-service-to-iis"></a><span data-ttu-id="6cc41-158">Le nouveau Service de publication à IIS</span><span class="sxs-lookup"><span data-stu-id="6cc41-158">Publish the New Service to IIS</span></span>  
 <span data-ttu-id="6cc41-159">Pour cet exemple, vous allez publier le service hôte de l’adaptateur au serveur web IIS local.</span><span class="sxs-lookup"><span data-stu-id="6cc41-159">For this example you will publish the adapter host service to the local IIS web server.</span></span>  
  
1.  <span data-ttu-id="6cc41-160">Dans l’Explorateur de solutions pour Visual Studio, cliquez droit sur le **ScottEmp** projet puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="6cc41-160">In Solution Explorer for Visual Studio, right click the **ScottEmp** project and click **Properties**.</span></span> <span data-ttu-id="6cc41-161">Les onglets du Concepteur de projet sont affichés.</span><span class="sxs-lookup"><span data-stu-id="6cc41-161">The Project Designer tabs are displayed.</span></span>  
  
2.  <span data-ttu-id="6cc41-162">Cliquez sur le **Web** onglet, puis cliquez sur le **serveur Web IIS Local d’utilisation** option.</span><span class="sxs-lookup"><span data-stu-id="6cc41-162">Click the **Web** tab, then click the **Use Local IIS Web server** option.</span></span>  
  
3.  <span data-ttu-id="6cc41-163">Cliquez sur le **créer un répertoire virtuel** bouton.</span><span class="sxs-lookup"><span data-stu-id="6cc41-163">Click the **Create Virtual Directory** button.</span></span>  
  
4.  <span data-ttu-id="6cc41-164">Ouvrez un navigateur web à l’adresse du service **http://localhost/ScottEmp/ISCOTT_EMP.svc**.</span><span class="sxs-lookup"><span data-stu-id="6cc41-164">Open a web browser to the service address **http://localhost/ScottEmp/ISCOTT_EMP.svc**.</span></span> <span data-ttu-id="6cc41-165">Vous devez recevoir un message indiquant « Vous avez créé un service » indiquant l’adaptateur est hébergé dans IIS.</span><span class="sxs-lookup"><span data-stu-id="6cc41-165">You should receive a message stating “You have created a service” indicating the adapter is hosted in IIS.</span></span>  
  
## <a name="add-the-external-data-source-to-a-sharepoint-site-using-sharepoint-designer"></a><span data-ttu-id="6cc41-166">Ajouter la Source de données externe sur un SharePoint Site à l’aide de SharePoint Designer</span><span class="sxs-lookup"><span data-stu-id="6cc41-166">Add the External Data Source to a SharePoint Site using SharePoint Designer</span></span>  
 <span data-ttu-id="6cc41-167">Cette section décrit comment ajouter le Service WCF en tant que source de données externe à un nouveau Site Web à l’aide de SharePoint Designer.</span><span class="sxs-lookup"><span data-stu-id="6cc41-167">This section describes how to add the WCF Service as an external data source to a new Web Site using SharePoint Designer.</span></span>  
  
  
1.  <span data-ttu-id="6cc41-168">Ouvrez SharePoint Designer et créer un nouveau Site Web.</span><span class="sxs-lookup"><span data-stu-id="6cc41-168">Open SharePoint Designer and create a new Web Site.</span></span>  
  
2.  <span data-ttu-id="6cc41-169">Dans SharePoint Designer, développez **Navigation** et cliquez sur **types de contenu externe** dans les **objets du Site** liste.</span><span class="sxs-lookup"><span data-stu-id="6cc41-169">In SharePoint Designer, expand **Navigation** and click **External Content types** in the **Site Objects** list.</span></span>  
  
3.  <span data-ttu-id="6cc41-170">Cliquez sur le **le Type de contenu externe** bouton de menu pour créer un nouveau type de contenu externe.</span><span class="sxs-lookup"><span data-stu-id="6cc41-170">Click the **External Content Type** menu button to create a new external content type.</span></span>  
  
4.  <span data-ttu-id="6cc41-171">Cliquez sur le texte en regard de **nom** pour modifier le nom du nouveau type de contenu externe.</span><span class="sxs-lookup"><span data-stu-id="6cc41-171">Click the text beside **Name** to edit the name of the new external content type.</span></span> <span data-ttu-id="6cc41-172">Entrez **OracleEMP** pour le nom.</span><span class="sxs-lookup"><span data-stu-id="6cc41-172">Enter **OracleEMP** for the name.</span></span>  
  
5.  <span data-ttu-id="6cc41-173">Cliquez sur le lien de texte en regard de **système externe** selon **cliquez ici pour découvrir les sources de données externes et les opérations.**.</span><span class="sxs-lookup"><span data-stu-id="6cc41-173">Click the text link beside **External System** which says **Click here to discover external data sources and operations.**.</span></span> <span data-ttu-id="6cc41-174">Le Concepteur de l’opération pour le type de contenu externe OracleEMP s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="6cc41-174">This opens the Operation Designer for the OracleEMP external content type.</span></span>  
  
6.  <span data-ttu-id="6cc41-175">Cliquez sur le **ajouter une connexion** bouton sur l’écran de découverte.</span><span class="sxs-lookup"><span data-stu-id="6cc41-175">Click the **Add Connection** button on the discovery screen.</span></span>  
  
7.  <span data-ttu-id="6cc41-176">Dans la boîte de dialogue Sélection de Type de Source de données externe, choisissez **Service WCF** et cliquez sur le **OK** bouton.</span><span class="sxs-lookup"><span data-stu-id="6cc41-176">In the External Data Source Type Selection dialog, choose **WCF Service** and click the **OK** button.</span></span>  
  
8.  <span data-ttu-id="6cc41-177">Dans la boîte de dialogue de connexion de WCF, dans le **URL des métadonnées de Service** , saisissez **https://localhost/ScottEmp/ISCOTT_EMP.svc?wsdl**</span><span class="sxs-lookup"><span data-stu-id="6cc41-177">In the WCF Connection dialog, in the **Service Metadata URL** box enter **https://localhost/ScottEmp/ISCOTT_EMP.svc?wsdl**</span></span>  
  
9. <span data-ttu-id="6cc41-178">Dans le **URL de point de terminaison de Service** , saisissez **https://localhost/ScottEmp/ISCOTT_EMP.svc**</span><span class="sxs-lookup"><span data-stu-id="6cc41-178">In the **Service Endpoint URL** box enter **https://localhost/ScottEmp/ISCOTT_EMP.svc**</span></span>  
  
10. <span data-ttu-id="6cc41-179">Cliquez sur le **OK** pour fermer la boîte de dialogue de connexion de WCF.</span><span class="sxs-lookup"><span data-stu-id="6cc41-179">Click the **OK** button to close the WCF Connection dialog.</span></span>  
  
11. <span data-ttu-id="6cc41-180">Une fois que les informations de Source de données sont remplies, développez le **https://localhost/ScottEmp/ISCOTT_EMP.svc** source de données et développez **méthodes Web**.</span><span class="sxs-lookup"><span data-stu-id="6cc41-180">Once the Data Source information is populated, expand the **https://localhost/ScottEmp/ISCOTT_EMP.svc** data source and expand **Web Methods**.</span></span>  
  
12. <span data-ttu-id="6cc41-181">Bouton droit sur le **ReadList** méthode Web et cliquez sur **nouvelle opération de liste en lecture**.</span><span class="sxs-lookup"><span data-stu-id="6cc41-181">Right click the **ReadList** Web Method and click **New Read List Operation**.</span></span> <span data-ttu-id="6cc41-182">La boîte de dialogue de configuration de liste en lecture est lancé.</span><span class="sxs-lookup"><span data-stu-id="6cc41-182">The Read List configuration dialog is launched.</span></span>  
  
13. <span data-ttu-id="6cc41-183">Dans la boîte de dialogue liste de lecture, cliquez sur **paramètres de retour** et cliquez sur **MATEMP** dans les éléments de Source de données.</span><span class="sxs-lookup"><span data-stu-id="6cc41-183">In the Read List dialog click **Return Parameters** and click **EMPNO** in the Data Source Elements.</span></span> <span data-ttu-id="6cc41-184">Cliquez sur le **carte à identificateur**.</span><span class="sxs-lookup"><span data-stu-id="6cc41-184">Click the **Map to identifier**.</span></span>  
  
14. <span data-ttu-id="6cc41-185">Cliquez sur **Terminer** dans la boîte de dialogue liste de lecture.</span><span class="sxs-lookup"><span data-stu-id="6cc41-185">Click **Finish** in the Read List dialog.</span></span>  
  
15. <span data-ttu-id="6cc41-186">Enregistrer la nouvelle source de données externe en tapant **Ctrl + s**.</span><span class="sxs-lookup"><span data-stu-id="6cc41-186">Save the new external data source by typing **Ctrl+s**.</span></span>  
  
#### <a name="test-the-external-data-source-connection"></a><span data-ttu-id="6cc41-187">Tester la connexion de Source de données externes</span><span class="sxs-lookup"><span data-stu-id="6cc41-187">Test the External Data Source Connection</span></span>  
  
1.  <span data-ttu-id="6cc41-188">Dans le nouveau site web, cliquez sur le **créer des listes et des formulaires** bouton.</span><span class="sxs-lookup"><span data-stu-id="6cc41-188">In the new web site, click the **Create Lists and Forms** button.</span></span> <span data-ttu-id="6cc41-189">Le formulaire de boîte de dialogue OracleEMP et de créer une liste apparaît.</span><span class="sxs-lookup"><span data-stu-id="6cc41-189">The Create List and Form for OracleEMP dialog appears.</span></span>  
  
2.  <span data-ttu-id="6cc41-190">Entrez **OracleEMP_List** pour le nom de la liste et cliquez sur le **OK** bouton.</span><span class="sxs-lookup"><span data-stu-id="6cc41-190">Enter **OracleEMP_List** for the List Name and click the **OK** button.</span></span>  
  
3.  <span data-ttu-id="6cc41-191">Une fois que la liste est créé, cliquez sur le **mode Résumé** bouton dans le menu.</span><span class="sxs-lookup"><span data-stu-id="6cc41-191">Once the list is create, click the **Summary View** button on the menu.</span></span>  
  
4.  <span data-ttu-id="6cc41-192">Cliquez sur **OracleEMP_List** sous listes externes.</span><span class="sxs-lookup"><span data-stu-id="6cc41-192">Click **OracleEMP_List** under External Lists.</span></span>  
  
5.  <span data-ttu-id="6cc41-193">Cliquez sur le **Aperçu dans le navigateur** bouton dans le menu pour tester l’opération ReadList de la carte.</span><span class="sxs-lookup"><span data-stu-id="6cc41-193">Click the **Preview in Browser** button on the menu to test the ReadList operation of the adapter.</span></span>  
  
## <a name="troubleshoot"></a><span data-ttu-id="6cc41-194">Dépanner</span><span class="sxs-lookup"><span data-stu-id="6cc41-194">Troubleshoot</span></span>
  
-   <span data-ttu-id="6cc41-195">Sur les ordinateurs 64 bits, il se peut que vous devez vous assurer que les composants du client Oracle 32 bits sont également installées.</span><span class="sxs-lookup"><span data-stu-id="6cc41-195">On 64-bit machines you must make sure that 32-bit Oracle client components are also installed.</span></span> <span data-ttu-id="6cc41-196">Il s’agit car Visual Studio et ses Assistants ne seront exécuté comme un processus 32 bits qui demande l’accès à des composants 32 bits pendant le développement.</span><span class="sxs-lookup"><span data-stu-id="6cc41-196">This is because Visual Studio and it’s wizards will be running as a 32-bit process requiring access to 32-bit components during development.</span></span>