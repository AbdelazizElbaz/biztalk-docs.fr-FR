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
ms.openlocfilehash: 2cf5be42a008cadba648739037797160386a42fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="use-the-oracle-database-adapter-with-sharepoint"></a><span data-ttu-id="09645-102">Utilisez l’adaptateur de base de données Oracle avec SharePoint</span><span class="sxs-lookup"><span data-stu-id="09645-102">Use the Oracle Database Adapter with SharePoint</span></span>
<span data-ttu-id="09645-103">L’Assistant de développement de services de l’adaptateur WCF pour [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)] permet à l’adaptateur Microsoft BizTalk pour base de données Oracle et l’adaptateur Microsoft BizTalk pour Oracle E-Business Suite être utilisés directement comme une source de données externe dans Microsoft SharePoint.</span><span class="sxs-lookup"><span data-stu-id="09645-103">The WCF Adapter Service Development Wizard for [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)] enables the Microsoft BizTalk Adapter for Oracle Database and the Microsoft BizTalk Adapter for Oracle E-Business Suite to be directly consumed as an external datasource in Microsoft SharePoint.</span></span> <span data-ttu-id="09645-104">L’Assistant Ajout de développement Service qui prend en charge cette fonctionnalité est lancé avec le **Service d’adaptateur WCF** modèle pour créer un nouveau Visual C# Sites Web dans [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="09645-104">The Add Service Development Wizard that supports this feature is launched with the **WCF Adapter Service** template for creating a new Visual C# Web Sites in [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="09645-105">Le modèle est inclus avec le [!INCLUDE[adapterpacknoversion_md](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="09645-105">The template is included with the [!INCLUDE[adapterpacknoversion_md](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="09645-106">Vous devez également installer le SDK de l’adaptateur de métier (LOB) de Microsoft Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="09645-106">You must also install the Microsoft Windows Communication Foundation (WCF) Line of Business (LOB) Adapter SDK.</span></span>  
  
## <a name="sharepoint-operation-support"></a><span data-ttu-id="09645-107">Prise en charge de SharePoint opération</span><span class="sxs-lookup"><span data-stu-id="09645-107">SharePoint Operation Support</span></span>  
 <span data-ttu-id="09645-108">L’Assistant de développement de services de l’adaptateur génère un contrat de service spéciales pour les adaptateurs Oracle qui est compatible avec Microsoft SharePoint.</span><span class="sxs-lookup"><span data-stu-id="09645-108">The Adapter Service Development wizard generates a special service contract for the Oracle adapters that is compatible with Microsoft SharePoint.</span></span> <span data-ttu-id="09645-109">L’Assistant génère un contrat de service qui inclut les opérations suivantes pour l’intégration de l’adaptateur avec Microsoft SharePoint :</span><span class="sxs-lookup"><span data-stu-id="09645-109">The wizard will generate a service contract which includes the following operations for integrating the adapter with Microsoft SharePoint:</span></span>  
  
-   <span data-ttu-id="09645-110">**Créer :** pris en charge par l’opération CreateItem_.</span><span class="sxs-lookup"><span data-stu-id="09645-110">**Create:** Supported by the CreateItem_ operation.</span></span>  
  
-   <span data-ttu-id="09645-111">**Lecture :** pris en charge par l’opération ReadItem_.</span><span class="sxs-lookup"><span data-stu-id="09645-111">**Read:** Supported by the ReadItem_ operation.</span></span>  
  
-   <span data-ttu-id="09645-112">**Mise à jour :** pris en charge par l’opération UpdateItem_.</span><span class="sxs-lookup"><span data-stu-id="09645-112">**Update:** Supported by the UpdateItem_ operation.</span></span>  
  
-   <span data-ttu-id="09645-113">**Suppression :** pris en charge par l’opération DeleteItem_.</span><span class="sxs-lookup"><span data-stu-id="09645-113">**Delete:** Supported by the DeleteItem_ operation.</span></span>  
  
-   <span data-ttu-id="09645-114">**Requête :** pris en charge par l’opération ReadList.</span><span class="sxs-lookup"><span data-stu-id="09645-114">**Query:** Supported by the ReadList operation.</span></span>  
  
-   <span data-ttu-id="09645-115">**Associer :** pris en charge par l’opération Associate_.</span><span class="sxs-lookup"><span data-stu-id="09645-115">**Associate:** Supported by the Associate_ operation.</span></span>  
  
 <span data-ttu-id="09645-116">Le contrat de service suivant a été généré à l’aide de l’adaptateur Microsoft BizTalk pour base de données Oracle par exemple.</span><span class="sxs-lookup"><span data-stu-id="09645-116">The following service contract was generated using for the Microsoft BizTalk Adapter for Oracle Database as an example.</span></span> <span data-ttu-id="09645-117">L’adaptateur est configuré pour fournir un accès à la table EMP</span><span class="sxs-lookup"><span data-stu-id="09645-117">The adapter is configured to provide access to the EMP table</span></span>  
  
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
  
## <a name="creating-a-new-web-site-to-host-the-microsoft-biztalk-adapter-for-oracle-database-in-iis"></a><span data-ttu-id="09645-118">Création d’un Site Web pour héberger l’adaptateur Microsoft BizTalk pour base de données Oracle dans IIS</span><span class="sxs-lookup"><span data-stu-id="09645-118">Creating a New Web Site to Host the Microsoft BizTalk Adapter for Oracle Database in IIS</span></span>  
 <span data-ttu-id="09645-119">Ces étapes fournissent un exemple d’utilisation de l’Assistant de développement Service de l’adaptateur WCF, pour créer un service web WCF hébergeant l’adaptateur Microsoft BizTalk pour base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="09645-119">These steps provide an example using the WCF Adapter Service Development Wizard, to create a new WCF web service hosting the Microsoft BizTalk Adapter for Oracle Database.</span></span> <span data-ttu-id="09645-120">Le contrat de service inclut des opérations directement compatibles avec Sharepoint.</span><span class="sxs-lookup"><span data-stu-id="09645-120">The service contract will include operations directly compatible with Sharepoint.</span></span> <span data-ttu-id="09645-121">Afin que celles-ci peuvent être directement consommées comme une source de données externe.</span><span class="sxs-lookup"><span data-stu-id="09645-121">So that it can be directly consumed as an external datasource.</span></span> <span data-ttu-id="09645-122">L’adaptateur est configuré pour s’authentifier auprès de la base de données Oracle à l’aide du **SCOTT** compte.</span><span class="sxs-lookup"><span data-stu-id="09645-122">The adapter is configured to authenticate with the Oracle database using the **SCOTT** account.</span></span> <span data-ttu-id="09645-123">Si le **SCOTT** compte est verrouillé, vous pouvez déverrouiller le compte en vous connectant à SQL Plus tant que SYSDBA.</span><span class="sxs-lookup"><span data-stu-id="09645-123">If the **SCOTT** account is locked, you can unlock the account by logging into SQL Plus as SYSDBA.</span></span>  
  
```  
<Oracle Installation Bin Directory>\Sqlplus.exe SYS AS SYSDBA  
```  
  
 <span data-ttu-id="09645-124">Puis exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="09645-124">Then run the following command.</span></span>  
  
```  
SQL> ALTER USER scott ACCOUNT UNLOCK;  
```  
  
#### <a name="creating-the-new-web-site-project"></a><span data-ttu-id="09645-125">Création du nouveau projet de Site Web</span><span class="sxs-lookup"><span data-stu-id="09645-125">Creating the New Web Site Project</span></span>  
  
1.  <span data-ttu-id="09645-126">Démarrer **Microsoft [!INCLUDE[vs2012](../../includes/vs2012-md.md)]** .</span><span class="sxs-lookup"><span data-stu-id="09645-126">Start **Microsoft [!INCLUDE[vs2012](../../includes/vs2012-md.md)]**.</span></span>  
  
2.  <span data-ttu-id="09645-127">Dans [!INCLUDE[vs2010](../../includes/vs2010-md.md)], dans le **fichier** menu, sélectionnez **nouveau** puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="09645-127">In [!INCLUDE[vs2010](../../includes/vs2010-md.md)], on the **File** menu, select **New** and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="09645-128">Dans le **nouveau projet** boîte de dialogue, développez **autres langages** et cliquez sur **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="09645-128">In the **New Project** dialog box, expand **Other Languages** and click **Visual C#**.</span></span> <span data-ttu-id="09645-129">Rechercher les **Service d’adaptateur WCF** dans le modèle de liste et cliquez dessus pour le sélectionner.</span><span class="sxs-lookup"><span data-stu-id="09645-129">Find the **WCF Adapter Service** in the template list and click it to select it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="09645-130">Le **Service d’adaptateur WCF** modèle n’est pas disponible si le [!INCLUDE[adapterpackcurrent](../../includes/adapterpackcurrent-md.md)] n’est pas installé.</span><span class="sxs-lookup"><span data-stu-id="09645-130">The **WCF Adapter Service** template is not available if the [!INCLUDE[adapterpackcurrent](../../includes/adapterpackcurrent-md.md)] is not installed.</span></span> <span data-ttu-id="09645-131">Sur x64 systèmes, installez les versions x86 et x64 de la [!INCLUDE[adapterpackcurrent](../../includes/adapterpackcurrent-md.md)].</span><span class="sxs-lookup"><span data-stu-id="09645-131">On x64 systems, install both the x86 and x64 versions of the [!INCLUDE[adapterpackcurrent](../../includes/adapterpackcurrent-md.md)].</span></span>  
  
4.  <span data-ttu-id="09645-132">Spécifiez **ScottEMP** pour le nom, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="09645-132">Specify **ScottEMP** for the name, and then click **OK**.</span></span> <span data-ttu-id="09645-133">Le **Assistant développement d’adaptateurs WCF** démarre.</span><span class="sxs-lookup"><span data-stu-id="09645-133">The **WCF Adapter Service Development Wizard** starts.</span></span>  
  
5.  <span data-ttu-id="09645-134">Sur le **Introduction** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="09645-134">On the **Introduction** page, click **Next**.</span></span>  
  
6.  <span data-ttu-id="09645-135">Sur le **choisissez les opérations** , spécifiez la **oracleDBBinding** liaison.</span><span class="sxs-lookup"><span data-stu-id="09645-135">On the **Choose Operations** page, specify the **oracleDBBinding** binding.</span></span>  
  
7.  <span data-ttu-id="09645-136">Cliquez sur le **configurer** bouton.</span><span class="sxs-lookup"><span data-stu-id="09645-136">Click the **Configure** button.</span></span> <span data-ttu-id="09645-137">Le **configurer l’adaptateur** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="09645-137">The **Configure Adapter** dialog is displayed.</span></span>  
  
8.  <span data-ttu-id="09645-138">Sur le **sécurité** onglet, sélectionnez **nom d’utilisateur** dans les **type d’informations d’identification du Client** zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="09645-138">On the **Security** tab, select **Username** in the **Client credential type** dropdown list box.</span></span>  
  
9. <span data-ttu-id="09645-139">Entrez **SCOTT** pour l’utilisateur de nom et entrez le mot de passe du compte SCOTT.</span><span class="sxs-lookup"><span data-stu-id="09645-139">Enter **SCOTT** for the User name and enter the correct password for the SCOTT account.</span></span> <span data-ttu-id="09645-140">Le mot de passe pour le compte SCOTT **tiger**.</span><span class="sxs-lookup"><span data-stu-id="09645-140">The default password for the SCOTT account is **tiger**.</span></span>  
  
10. <span data-ttu-id="09645-141">Cliquez sur le **propriétés URI** , entrez le nom d’hôte ou adresse IP de votre serveur Oracle dans la **ServerAddress** boîte.</span><span class="sxs-lookup"><span data-stu-id="09645-141">Click the **URI Properties** tab, enter the IP address or host name for your Oracle server in the **ServerAddress** box.</span></span>  
  
11. <span data-ttu-id="09645-142">Entrez le nom d’instance correct des service de base de données Oracle dans la **ServiceName** boîte.</span><span class="sxs-lookup"><span data-stu-id="09645-142">Enter the correct Oracle database service instance name in the **ServiceName** box.</span></span> <span data-ttu-id="09645-143">Vous pouvez copier les informations de nom d’instance à partir d’Oracle Enterprise Manager.</span><span class="sxs-lookup"><span data-stu-id="09645-143">You can copy the instance name information from Oracle Enterprise Manager.</span></span>  
  
12. <span data-ttu-id="09645-144">Appuyez sur la **OK** bouton sur le **configurer l’adaptateur** boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="09645-144">Press the **OK** button on the **Configure Adapter** dialog</span></span>  
  
13. <span data-ttu-id="09645-145">Sur le **choisissez les opérations** page de l’Assistant, cliquez sur le **Connect** bouton et attendez quelques instants pour les catégories à générer pour la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="09645-145">On the **Choose Operations** page of the wizard, click the **Connect** button and wait a few moments for the categories to be built for the Oracle database.</span></span>  
  
14. <span data-ttu-id="09645-146">Une fois que les catégories sont ajoutés dans le **sélectionner une catégorie** liste, faites défiler jusqu'à **SCOTT** et développez-le.</span><span class="sxs-lookup"><span data-stu-id="09645-146">Once the categories are added in the **Select a category** list, scroll down to **SCOTT** and expand it.</span></span> <span data-ttu-id="09645-147">Puis développez **Table** et cliquez sur le **EMP** entrée de la table.</span><span class="sxs-lookup"><span data-stu-id="09645-147">Then expand **Table** and click the **EMP** table entry.</span></span>  
  
15. <span data-ttu-id="09645-148">Dans le **catégories et opérations disponibles** , sélectionnez toutes les opérations dans la liste et cliquez sur le **ajouter** bouton.</span><span class="sxs-lookup"><span data-stu-id="09645-148">In the **Available categories and operations** list, select all the operations in the list and click the **Add** button.</span></span> <span data-ttu-id="09645-149">Toutes les opérations sont ajoutées à la **ajouté des catégories et opérations** liste.</span><span class="sxs-lookup"><span data-stu-id="09645-149">All the operations are added to the **Added categories and operations** list.</span></span>  
  
16. <span data-ttu-id="09645-150">Sur le **choisissez les opérations** , cliquez sur le **suivant** bouton.</span><span class="sxs-lookup"><span data-stu-id="09645-150">On the **Choose Operations** page, click the **Next** button.</span></span>  
  
17. <span data-ttu-id="09645-151">Sur le **configurer le Service et les comportements de point de terminaison** , définissez le **UseServiceCertificate** comportement de Service **false** pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="09645-151">On the **Configure Service and Endpoint Behaviors** page, set the **UseServiceCertificate** Service behavior to **false** for this example.</span></span> <span data-ttu-id="09645-152">Puis cliquez sur le **suivant** bouton.</span><span class="sxs-lookup"><span data-stu-id="09645-152">Then click the **Next** button.</span></span>  
  
18. <span data-ttu-id="09645-153">Sur le **configurer la liaison de point de terminaison de Service et l’adresse** , cliquez sur le **appliquer** bouton.</span><span class="sxs-lookup"><span data-stu-id="09645-153">On the **Configure Service Endpoint Binding and Address** page, click the **Apply** button.</span></span> <span data-ttu-id="09645-154">Puis cliquez sur le **suivant** bouton.</span><span class="sxs-lookup"><span data-stu-id="09645-154">Then click the **Next** button.</span></span>  
  
19. <span data-ttu-id="09645-155">Sur le **Résumé** , cliquez sur le **Terminer** bouton.</span><span class="sxs-lookup"><span data-stu-id="09645-155">On the **Summary** page, click the **Finish** button.</span></span>  
  
20. <span data-ttu-id="09645-156">Cliquez sur le **générer** option de menu, puis cliquez sur **générer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="09645-156">Click the **Build** menu option and then click **Build Solution**.</span></span> <span data-ttu-id="09645-157">Vérifiez que la génération du projet a réussi sans erreurs.</span><span class="sxs-lookup"><span data-stu-id="09645-157">Verify the project build was successful with no errors.</span></span>  
  
## <a name="publishing-the-new-service-to-iis"></a><span data-ttu-id="09645-158">Le nouveau Service de publication sur le serveur IIS</span><span class="sxs-lookup"><span data-stu-id="09645-158">Publishing the New Service to IIS</span></span>  
 <span data-ttu-id="09645-159">Pour cet exemple, vous allez publier le service hôte de l’adaptateur au serveur web IIS local.</span><span class="sxs-lookup"><span data-stu-id="09645-159">For this example you will publish the adapter host service to the local IIS web server.</span></span>  
  
1.  <span data-ttu-id="09645-160">Dans l’Explorateur de solutions pour [!INCLUDE[vs2010](../../includes/vs2010-md.md)], bouton droit sur le **ScottEmp** projet puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="09645-160">In Solution Explorer for [!INCLUDE[vs2010](../../includes/vs2010-md.md)], right click the **ScottEmp** project and click **Properties**.</span></span> <span data-ttu-id="09645-161">Les onglets du Concepteur de projet sont affichés.</span><span class="sxs-lookup"><span data-stu-id="09645-161">The Project Designer tabs are displayed.</span></span>  
  
2.  <span data-ttu-id="09645-162">Cliquez sur le **Web** onglet, puis cliquez sur le **serveur Web IIS Local d’utilisation** option.</span><span class="sxs-lookup"><span data-stu-id="09645-162">Click the **Web** tab, then click the **Use Local IIS Web server** option.</span></span>  
  
3.  <span data-ttu-id="09645-163">Cliquez sur le **créer un répertoire virtuel** bouton.</span><span class="sxs-lookup"><span data-stu-id="09645-163">Click the **Create Virtual Directory** button.</span></span>  
  
4.  <span data-ttu-id="09645-164">Ouvrez un navigateur web à l’adresse du service **http://localhost/ScottEmp/ISCOTT_EMP.svc**.</span><span class="sxs-lookup"><span data-stu-id="09645-164">Open a web browser to the service address **http://localhost/ScottEmp/ISCOTT_EMP.svc**.</span></span> <span data-ttu-id="09645-165">Vous devez recevoir un message indiquant « Vous avez créé un service » indiquant l’adaptateur est hébergé dans IIS.</span><span class="sxs-lookup"><span data-stu-id="09645-165">You should receive a message stating “You have created a service” indicating the adapter is hosted in IIS.</span></span>  
  
## <a name="adding-the-external-data-source-to-a-sharepoint-site-using-sharepoint-designer"></a><span data-ttu-id="09645-166">Ajout de la Source de données externe sur un SharePoint Site à l’aide de SharePoint Designer</span><span class="sxs-lookup"><span data-stu-id="09645-166">Adding the External Data Source to a SharePoint Site using SharePoint Designer</span></span>  
 <span data-ttu-id="09645-167">Cette section décrit comment ajouter le Service WCF en tant que source de données externe à un nouveau Site Web à l’aide de SharePoint Designer.</span><span class="sxs-lookup"><span data-stu-id="09645-167">This section describes how to add the WCF Service as an external data source to a new Web Site using SharePoint Designer.</span></span>  
  
#### <a name="adding-the-external-data-source"></a><span data-ttu-id="09645-168">Ajout de la source de données externes</span><span class="sxs-lookup"><span data-stu-id="09645-168">Adding the External Data source</span></span>  
  
1.  <span data-ttu-id="09645-169">Ouvrez SharePoint Designer et créer un nouveau Site Web.</span><span class="sxs-lookup"><span data-stu-id="09645-169">Open SharePoint Designer and create a new Web Site.</span></span>  
  
2.  <span data-ttu-id="09645-170">Dans SharePoint Designer, développez **Navigation** et cliquez sur **types de contenu externe** dans les **objets du Site** liste.</span><span class="sxs-lookup"><span data-stu-id="09645-170">In SharePoint Designer, expand **Navigation** and click **External Content types** in the **Site Objects** list.</span></span>  
  
3.  <span data-ttu-id="09645-171">Cliquez sur le **le Type de contenu externe** bouton de menu pour créer un nouveau type de contenu externe.</span><span class="sxs-lookup"><span data-stu-id="09645-171">Click the **External Content Type** menu button to create a new external content type.</span></span>  
  
4.  <span data-ttu-id="09645-172">Cliquez sur le texte en regard de **nom** pour modifier le nom du nouveau type de contenu externe.</span><span class="sxs-lookup"><span data-stu-id="09645-172">Click the text beside **Name** to edit the name of the new external content type.</span></span> <span data-ttu-id="09645-173">Entrez **OracleEMP** pour le nom.</span><span class="sxs-lookup"><span data-stu-id="09645-173">Enter **OracleEMP** for the name.</span></span>  
  
5.  <span data-ttu-id="09645-174">Cliquez sur le lien de texte en regard de **système externe** selon **cliquez ici pour découvrir les sources de données externes et les opérations.**.</span><span class="sxs-lookup"><span data-stu-id="09645-174">Click the text link beside **External System** which says **Click here to discover external data sources and operations.**.</span></span> <span data-ttu-id="09645-175">Le Concepteur de l’opération pour le type de contenu externe OracleEMP s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="09645-175">This opens the Operation Designer for the OracleEMP external content type.</span></span>  
  
6.  <span data-ttu-id="09645-176">Cliquez sur le **ajouter une connexion** bouton sur l’écran de découverte.</span><span class="sxs-lookup"><span data-stu-id="09645-176">Click the **Add Connection** button on the discovery screen.</span></span>  
  
7.  <span data-ttu-id="09645-177">Dans la boîte de dialogue Sélection de Type de Source de données externe, choisissez **Service WCF** et cliquez sur le **OK** bouton.</span><span class="sxs-lookup"><span data-stu-id="09645-177">In the External Data Source Type Selection dialog, choose **WCF Service** and click the **OK** button.</span></span>  
  
8.  <span data-ttu-id="09645-178">Dans la boîte de dialogue de connexion de WCF, dans le **URL des métadonnées de Service** , saisissez **https://localhost/ScottEmp/ISCOTT_EMP.svc?wsdl**</span><span class="sxs-lookup"><span data-stu-id="09645-178">In the WCF Connection dialog, in the **Service Metadata URL** box enter **https://localhost/ScottEmp/ISCOTT_EMP.svc?wsdl**</span></span>  
  
9. <span data-ttu-id="09645-179">Dans le **URL de point de terminaison de Service** , saisissez **https://localhost/ScottEmp/ISCOTT_EMP.svc**</span><span class="sxs-lookup"><span data-stu-id="09645-179">In the **Service Endpoint URL** box enter **https://localhost/ScottEmp/ISCOTT_EMP.svc**</span></span>  
  
10. <span data-ttu-id="09645-180">Cliquez sur le **OK** pour fermer la boîte de dialogue de connexion de WCF.</span><span class="sxs-lookup"><span data-stu-id="09645-180">Click the **OK** button to close the WCF Connection dialog.</span></span>  
  
11. <span data-ttu-id="09645-181">Une fois que les informations de Source de données sont remplies, développez le **https://localhost/ScottEmp/ISCOTT_EMP.svc** source de données et développez **méthodes Web**.</span><span class="sxs-lookup"><span data-stu-id="09645-181">Once the Data Source information is populated, expand the **https://localhost/ScottEmp/ISCOTT_EMP.svc** data source and expand **Web Methods**.</span></span>  
  
12. <span data-ttu-id="09645-182">Bouton droit sur le **ReadList** méthode Web et cliquez sur **nouvelle opération de liste en lecture**.</span><span class="sxs-lookup"><span data-stu-id="09645-182">Right click the **ReadList** Web Method and click **New Read List Operation**.</span></span> <span data-ttu-id="09645-183">La boîte de dialogue de configuration de liste en lecture est lancé.</span><span class="sxs-lookup"><span data-stu-id="09645-183">The Read List configuration dialog is launched.</span></span>  
  
13. <span data-ttu-id="09645-184">Dans la boîte de dialogue liste de lecture, cliquez sur **paramètres de retour** et cliquez sur **MATEMP** dans les éléments de Source de données.</span><span class="sxs-lookup"><span data-stu-id="09645-184">In the Read List dialog click **Return Parameters** and click **EMPNO** in the Data Source Elements.</span></span> <span data-ttu-id="09645-185">Cliquez sur le **carte à identificateur**.</span><span class="sxs-lookup"><span data-stu-id="09645-185">Click the **Map to identifier**.</span></span>  
  
14. <span data-ttu-id="09645-186">Cliquez sur **Terminer** dans la boîte de dialogue liste de lecture.</span><span class="sxs-lookup"><span data-stu-id="09645-186">Click **Finish** in the Read List dialog.</span></span>  
  
15. <span data-ttu-id="09645-187">Enregistrer la nouvelle source de données externe en tapant **Ctrl + s**.</span><span class="sxs-lookup"><span data-stu-id="09645-187">Save the new external data source by typing **Ctrl+s**.</span></span>  
  
#### <a name="testing-the-external-data-source-connection"></a><span data-ttu-id="09645-188">Test de la connexion de Source de données externes</span><span class="sxs-lookup"><span data-stu-id="09645-188">Testing the External Data Source Connection</span></span>  
  
1.  <span data-ttu-id="09645-189">Dans le nouveau site web, cliquez sur le **créer des listes et des formulaires** bouton.</span><span class="sxs-lookup"><span data-stu-id="09645-189">In the new web site, click the **Create Lists and Forms** button.</span></span> <span data-ttu-id="09645-190">Le formulaire de boîte de dialogue OracleEMP et de créer une liste apparaît.</span><span class="sxs-lookup"><span data-stu-id="09645-190">The Create List and Form for OracleEMP dialog appears.</span></span>  
  
2.  <span data-ttu-id="09645-191">Entrez **OracleEMP_List** pour le nom de la liste et cliquez sur le **OK** bouton.</span><span class="sxs-lookup"><span data-stu-id="09645-191">Enter **OracleEMP_List** for the List Name and click the **OK** button.</span></span>  
  
3.  <span data-ttu-id="09645-192">Une fois que la liste est créé, cliquez sur le **mode Résumé** bouton dans le menu.</span><span class="sxs-lookup"><span data-stu-id="09645-192">Once the list is create, click the **Summary View** button on the menu.</span></span>  
  
4.  <span data-ttu-id="09645-193">Cliquez sur **OracleEMP_List** sous listes externes.</span><span class="sxs-lookup"><span data-stu-id="09645-193">Click **OracleEMP_List** under External Lists.</span></span>  
  
5.  <span data-ttu-id="09645-194">Cliquez sur le **Aperçu dans le navigateur** bouton dans le menu pour tester l’opération ReadList de la carte.</span><span class="sxs-lookup"><span data-stu-id="09645-194">Click the **Preview in Browser** button on the menu to test the ReadList operation of the adapter.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="09645-195">Dépannage</span><span class="sxs-lookup"><span data-stu-id="09645-195">Troubleshooting</span></span>  
  
-   <span data-ttu-id="09645-196">Sur les ordinateurs 64 bits, il se peut que vous devez vous assurer que les composants du client Oracle 32 bits sont également installées.</span><span class="sxs-lookup"><span data-stu-id="09645-196">On 64-bit machines you must make sure that 32-bit Oracle client components are also installed.</span></span> <span data-ttu-id="09645-197">C’est parce que [!INCLUDE[vs2010](../../includes/vs2010-md.md)] et exécute ses Assistants comme un processus 32 bits qui demande l’accès à des composants 32 bits pendant le développement.</span><span class="sxs-lookup"><span data-stu-id="09645-197">This is because [!INCLUDE[vs2010](../../includes/vs2010-md.md)] and it’s wizards will be running as a 32-bit process requiring access to 32-bit components during development.</span></span>