---
title: "Étape 4 : Créer une Application Sharepoint pour accéder à l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2d8c398-370a-4c62-961d-0eab6066ad5a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3360bbdf5ae5a6a8dde9851c544342ea6a6bc1cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-create-a-sharepoint-application-to-access-the-adapter"></a><span data-ttu-id="6fe5d-102">Étape 4 : Créer une Application Sharepoint pour accéder à la carte</span><span class="sxs-lookup"><span data-stu-id="6fe5d-102">Step 4: Create a Sharepoint Application to Access the Adapter</span></span>
<span data-ttu-id="6fe5d-103">![Étape 4 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span><span class="sxs-lookup"><span data-stu-id="6fe5d-103">![Step 4 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")</span></span>  
  
 <span data-ttu-id="6fe5d-104">**Durée :** 15 minutes</span><span class="sxs-lookup"><span data-stu-id="6fe5d-104">**Time to complete:** 15 minutes</span></span>  
  
 <span data-ttu-id="6fe5d-105">Dans cette étape vous prenez le fichier de définition d’application que vous avez créé à l’aide de l’outil Éditeur de définition de catalogue de données métier et l’importer dans Microsoft Office SharePoint Server.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-105">In this step you take the application definition file that you created using the Business Data Catalog Definition Editor tool, and import it into Microsoft Office SharePoint Server.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6fe5d-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="6fe5d-106">Prerequisites</span></span>  
  
-   <span data-ttu-id="6fe5d-107">Vous avez devez créé un fichier d’application comme décrit dans [étape 3 : créer un fichier de définition d’Application](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-create-an-application-definition-file.md).</span><span class="sxs-lookup"><span data-stu-id="6fe5d-107">You should have created an application file as described in [Step 3: Create an Application Definition File](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-create-an-application-definition-file.md).</span></span>  
  
-   <span data-ttu-id="6fe5d-108">Le service Microsoft Single Sign-On doit être en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-108">The Microsoft Single Sign-On service must be running.</span></span>  
  
## <a name="how-to-create-a-sharepoint-application"></a><span data-ttu-id="6fe5d-109">Comment créer une Application SharePoint</span><span class="sxs-lookup"><span data-stu-id="6fe5d-109">How to Create a SharePoint Application</span></span>  
 <span data-ttu-id="6fe5d-110">Création d’une application SharePoint implique les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="6fe5d-110">Creating a SharePoint application involves the following steps:</span></span>  
  
-   <span data-ttu-id="6fe5d-111">Créer une application Single Sign-On (SSO) dans SharePoint.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-111">Create a Single Sign-On (SSO) application in SharePoint.</span></span>  
  
-   <span data-ttu-id="6fe5d-112">Créer un fournisseur de Services partagés et importez le fichier de définition d’application.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-112">Create a Shared Services Provider, and import the application definition file.</span></span>  
  
-   <span data-ttu-id="6fe5d-113">Créer une page Web et ajouter des composants WebPart.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-113">Create a Web Part page, and add Web Parts.</span></span>  
  
 <span data-ttu-id="6fe5d-114">Cette rubrique montre comment effectuer ces étapes.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-114">This topic demonstrates how to perform these steps.</span></span>  
  
## <a name="creating-an-sso-application-in-sharepoint"></a><span data-ttu-id="6fe5d-115">Création d’une Application de l’authentification unique dans SharePoint</span><span class="sxs-lookup"><span data-stu-id="6fe5d-115">Creating an SSO Application in SharePoint</span></span>  
 <span data-ttu-id="6fe5d-116">Pour passer les informations d’identification de l’utilisateur à l’adaptateur d’écho à partir d’une application SharePoint, vous devez configurer une application SSO qui mappe à un compte d’utilisateur ou un groupe.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-116">To pass user credentials to the Echo adapter from a SharePoint application, you must set up an SSO application that maps to a user account or group.</span></span>  
  
#### <a name="manage-server-settings-for-single-sign-on"></a><span data-ttu-id="6fe5d-117">Gérer les paramètres de serveur pour l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="6fe5d-117">Manage server settings for Single Sign-On</span></span>  
  
1.  <span data-ttu-id="6fe5d-118">Démarrez l’Administration centrale de SharePoint 3.0.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-118">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="6fe5d-119">Sur le **Démarrer** menu, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-119">On the **Start** menu, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="6fe5d-120">Dans la barre de navigation supérieure, cliquez sur **Operations**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-120">On the top navigation bar, click **Operations**.</span></span>  
  
3.  <span data-ttu-id="6fe5d-121">Sur la page opérations, dans le **Configuration de la sécurité** , cliquez sur **gérer les paramètres de l’authentification unique sur**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-121">On the Operations page, in the **Security Configuration** section, click **Manage settings for single sign-on**.</span></span>  
  
4.  <span data-ttu-id="6fe5d-122">Sur la gérer les paramètres pour l’authentification unique de la page, dans le **paramètres du serveur** , cliquez sur **gérer les paramètres de serveur**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-122">On the Manage Settings for Single Sign-On page, in the **Server Settings** section, click **Manage Server Settings**.</span></span>  
  
5.  <span data-ttu-id="6fe5d-123">Assurez-vous que les informations de cette page sont correctes pour votre installation de l’authentification unique.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-123">Ensure that the information on this page is correct for your Single Sign-On installation.</span></span> <span data-ttu-id="6fe5d-124">Pour plus d’informations sur ces opérations, consultez « Configurer l’authentification unique (Office SharePoint Server) » à [http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291).</span><span class="sxs-lookup"><span data-stu-id="6fe5d-124">For more information about these operations, see “Configure single sign-on (Office SharePoint Server)” at [http://go.microsoft.com/fwlink/?LinkId=105291](http://go.microsoft.com/fwlink/?LinkId=105291).</span></span>  
  
#### <a name="manage-settings-for-enterprise-application-definitions"></a><span data-ttu-id="6fe5d-125">Gérer les paramètres des définitions d’application d’entreprise</span><span class="sxs-lookup"><span data-stu-id="6fe5d-125">Manage settings for enterprise application definitions</span></span>  
  
1.  <span data-ttu-id="6fe5d-126">Dans l’Administration centrale de SharePoint, dans la barre de navigation supérieure, cliquez sur **Operations**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-126">In SharePoint Central Administration, on the top navigation bar, click **Operations**.</span></span>  
  
2.  <span data-ttu-id="6fe5d-127">Sur la page opérations, dans le **Configuration de la sécurité** , cliquez sur **gérer les paramètres pour l’authentification unique sur**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-127">On the Operations page, in the **Security Configuration** section, click **Manage Settings for single sign-on**.</span></span>  
  
3.  <span data-ttu-id="6fe5d-128">Sur la gérer les paramètres pour l’authentification unique de la page, dans le **définition de paramètres de l’Application Enterprise** , cliquez sur **gérer les paramètres pour les définitions d’application d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-128">On the Manage Settings for Single Sign-On page, in the **Enterprise Application Definition Settings** section, click **Manage Settings for enterprise application definitions**.</span></span>  
  
4.  <span data-ttu-id="6fe5d-129">Dans la page Gérer les définitions d’Application d’entreprise, cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-129">On the Manage Enterprise Application Definitions page, click **New Item**.</span></span>  
  
5.  <span data-ttu-id="6fe5d-130">Sur la créer Enterprise définitions Page Application, définissez la **nom d’affichage** au champ **EchoSSO**, puis définissez le **nom de l’Application** au champ  **EchoSSO**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-130">On the Create Enterprise Application Definitions Page, set the **Display name** field to **EchoSSO**, and then set the **Application name** field to **EchoSSO**.</span></span> <span data-ttu-id="6fe5d-131">Cette valeur doit correspondre à SecondarySsoApplicationId que vous avez spécifié dans [étape 3 : créer un fichier de définition d’Application](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-create-an-application-definition-file.md).</span><span class="sxs-lookup"><span data-stu-id="6fe5d-131">This value should match the SecondarySsoApplicationId you specified in [Step 3: Create an Application Definition File](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-create-an-application-definition-file.md).</span></span>  
  
6.  <span data-ttu-id="6fe5d-132">Dans le **adresse de messagerie du Contact** champ, entrez votre adresse de messagerie, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-132">In the **Contact e-mail address** field, enter your e-mail address, and then click **OK**.</span></span>  
  
#### <a name="manage-account-information-for-enterprise-application-definitions"></a><span data-ttu-id="6fe5d-133">Gérer les informations de compte pour les définitions d’application d’entreprise</span><span class="sxs-lookup"><span data-stu-id="6fe5d-133">Manage account information for enterprise application definitions</span></span>  
  
1.  <span data-ttu-id="6fe5d-134">Dans l’Administration centrale de SharePoint, dans la barre de navigation supérieure, cliquez sur **Operations**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-134">In SharePoint Central Administration, on the top navigation bar, click **Operations**.</span></span>  
  
2.  <span data-ttu-id="6fe5d-135">Sur la page opérations, dans le **Section de Configuration de sécurité**, cliquez sur **gérer les paramètres de l’authentification unique sur**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-135">On the Operations page, in the **Security Configuration Section**, click **Manage settings for single sign-on**.</span></span>  
  
3.  <span data-ttu-id="6fe5d-136">Sur la gérer les paramètres pour l’authentification unique de la page, dans le **définition de paramètres de l’Application Enterprise** , cliquez sur **gérer informations de compte pour entreprise définitions d’application**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-136">On the Manage Settings for Single Sign-On page, in the **Enterprise Application Definition Settings** section, click **Manage account information for enterprise application definitions**.</span></span>  
  
4.  <span data-ttu-id="6fe5d-137">Sur les informations de compte gérer pour une définition d’Application d’entreprise, sélectionnez **EchoSSO** à partir de la **définition d’application d’entreprise** liste.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-137">On the Manage Account Information for an Enterprise Application Definition, select **EchoSSO** from the **Enterprise application definition** list.</span></span>  
  
5.  <span data-ttu-id="6fe5d-138">Dans le **nom de compte de groupe** , tapez le groupe Windows qui permet de sécuriser cette définition d’application.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-138">In the **Group account name** field, type the Windows group that will be used to secure this application definition.</span></span> <span data-ttu-id="6fe5d-139">Par exemple, **les utilisateurs du domaine source\Administrateurs du domaine**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-139">For example, **DOMAIN\Domain Users**.</span></span>  
  
6.  <span data-ttu-id="6fe5d-140">Cliquez sur **Définir**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-140">Click **Set**.</span></span>  
  
7.  <span data-ttu-id="6fe5d-141">Dans la page des informations de compte EchoSSO, dans le **nom d’utilisateur** le type de champ **testuser**, puis, dans le **mot de passe** le type de champ **testpassword**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-141">On the Provide EchoSSO Account Information page, in the **Username** field type **testuser**, and then in the **Password** field type **testpassword**.</span></span>  
  
8.  <span data-ttu-id="6fe5d-142">Cliquez sur **OK**, puis cliquez sur **fait**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-142">Click **OK**, and then click **Done**.</span></span>  
  
## <a name="creating-a-shared-services-provider-and-importing-the-application-definition-file"></a><span data-ttu-id="6fe5d-143">Création d’un fournisseur de Services partagés et l’importation du fichier de définition d’application</span><span class="sxs-lookup"><span data-stu-id="6fe5d-143">Creating a Shared Services Provider and importing the application definition file</span></span>  
 <span data-ttu-id="6fe5d-144">Un fournisseur de Services partagés (SSP) est un regroupement logique des services partagés et leurs ressources de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-144">A Shared Services Provider (SSP) is a logical grouping of shared services and their supporting resources.</span></span> <span data-ttu-id="6fe5d-145">Vous pouvez créer un fournisseur de services partagés à l’aide de la Console d’Administration centrale de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-145">You can create an SSP by using the SharePoint Central Administration Console.</span></span> <span data-ttu-id="6fe5d-146">Cet exemple fonctionne dans n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-146">This example will work in any SSP.</span></span> <span data-ttu-id="6fe5d-147">Pour plus d’informations sur la création d’un fournisseur de services partagés, consultez « Vue d’ensemble : créer et configurer des fournisseurs de Services partagés » à [http://go.microsoft.com/fwlink/?LinkId=105119](http://go.microsoft.com/fwlink/?LinkId=105119).</span><span class="sxs-lookup"><span data-stu-id="6fe5d-147">For more information about creating an SSP, see “Chapter overview: Create and Configure Shared Services Providers” at [http://go.microsoft.com/fwlink/?LinkId=105119](http://go.microsoft.com/fwlink/?LinkId=105119).</span></span>  
  
### <a name="to-import-the-application-definition-file"></a><span data-ttu-id="6fe5d-148">Pour importer le fichier de définition d’application</span><span class="sxs-lookup"><span data-stu-id="6fe5d-148">To import the application definition file</span></span>  
  
1.  <span data-ttu-id="6fe5d-149">Démarrez l’Administration centrale de SharePoint 3.0.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-149">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="6fe5d-150">Sur le **Démarrer** menu, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-150">On the **Start** menu, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="6fe5d-151">Dans le volet de navigation gauche, cliquez sur le nom du fournisseur auquel vous souhaitez importer la définition d’application.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-151">In the left navigation pane, click the name of the SSP to which you want to import the application definition.</span></span>  
  
3.  <span data-ttu-id="6fe5d-152">Dans le **catalogue de données métiers** , cliquez sur **importer la définition d’application**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-152">In the **Business Data Catalog** section, click **Import application definition**.</span></span>  
  
4.  <span data-ttu-id="6fe5d-153">Dans la page de définition d’Application importation, cliquez sur **Parcourir**, puis sélectionnez le fichier EchoWS.xml.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-153">On the Import Application Definition page, click **Browse**, and then select the EchoWS.xml file.</span></span>  
  
5.  <span data-ttu-id="6fe5d-154">Cliquez sur **importation**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-154">Click **Import**, and then click **OK**.</span></span>  
  
## <a name="creating-web-parts"></a><span data-ttu-id="6fe5d-155">Création de composants WebPart</span><span class="sxs-lookup"><span data-stu-id="6fe5d-155">Creating Web Parts</span></span>  
 <span data-ttu-id="6fe5d-156">Vous devez maintenant créer des composants WebPart de votre site SharePoint pour utiliser l’instance de la méthode créée dans l’éditeur de définition du catalogue de données métier.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-156">You must now create Web Parts in your SharePoint site to use the method instance created in the Business Data Catalog Definition Editor.</span></span> <span data-ttu-id="6fe5d-157">Composants WebPart est des composants réutilisables qui peuvent contenir tout type d’informations sur le Web, y compris analytiques, de collaboration et informations de base de données.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-157">Web Parts are reusable components that can contain any kind of Web-based information, including analytical, collaborative, and database information.</span></span>  
  
#### <a name="to-create-a-web-part-page"></a><span data-ttu-id="6fe5d-158">Pour créer une page Web</span><span class="sxs-lookup"><span data-stu-id="6fe5d-158">To create a Web Part page</span></span>  
  
1.  <span data-ttu-id="6fe5d-159">Démarrez l’Administration centrale de SharePoint 3.0.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-159">Start SharePoint 3.0 Central Administration.</span></span> <span data-ttu-id="6fe5d-160">Sur le **Démarrer** menu, pointez sur **tous les programmes**, pointez sur **Microsoft Office Server**, puis cliquez sur **Administration centrale de SharePoint 3.0**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-160">On the **Start** menu, point to **All Programs**, point to **Microsoft Office Server**, and then click **SharePoint 3.0 Central Administration**.</span></span>  
  
2.  <span data-ttu-id="6fe5d-161">Dans le volet de navigation gauche, cliquez sur le nom du fournisseur dans lequel vous avez importé le fichier de définition d’application.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-161">In the left navigation pane, click the name of the SSP in which you imported the application definition file.</span></span>  
  
3.  <span data-ttu-id="6fe5d-162">Dans la page Administration de Services partagés, dans le coin supérieur droit, cliquez sur **Actions du Site**, puis cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-162">On the Shared Services Administration page, in the upper-right corner, click **Site Actions**, and then click **Create**.</span></span>  
  
     <span data-ttu-id="6fe5d-163">![Créer des Actions de Site](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/13f43659-ef61-48db-ac19-2d553367ec7e.gif "13f43659-ef61-48db-ac19-2d553367ec7e")</span><span class="sxs-lookup"><span data-stu-id="6fe5d-163">![Create Site Actions](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/13f43659-ef61-48db-ac19-2d553367ec7e.gif "13f43659-ef61-48db-ac19-2d553367ec7e")</span></span>  
  
4.  <span data-ttu-id="6fe5d-164">Sur le **créer** page, dans le **Pages Web** , cliquez sur **Page WebPart**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-164">On the **Create** page, in the **Web Pages** section, click **Web Part Page**.</span></span>  
  
5.  <span data-ttu-id="6fe5d-165">Dans la page Nouveau composant WebPart, dans le **nom** , tapez **EchoPart**, puis sélectionnez **pleine Page, Vertical** à partir de la **a choisi un modèle de disposition**liste.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-165">On the New Web Part page, in the **Name** field, type **EchoPart**, and then select **Full Page, Vertical** from the **Chose a Layout Template** list.</span></span>  
  
6.  <span data-ttu-id="6fe5d-166">Cliquez sur **Créer**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-166">Click **Create**.</span></span>  
  
#### <a name="to-add-a-business-data-web-part"></a><span data-ttu-id="6fe5d-167">Pour ajouter un composant WebPart données métier</span><span class="sxs-lookup"><span data-stu-id="6fe5d-167">To add a Business Data Web Part</span></span>  
  
1.  <span data-ttu-id="6fe5d-168">Cliquez sur **Ajouter un composant WebPart**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-168">Click **Add a Web Part**.</span></span>  
  
2.  <span data-ttu-id="6fe5d-169">Dans le **ajouter des WebParts** boîte de dialogue, sélectionnez **liste de données métiers**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-169">In the **Add Web Parts** dialog box, select **Business Data List**, and then click **Add**.</span></span>  
  
     <span data-ttu-id="6fe5d-170">![Liste de données métiers](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/cd9e6bc8-c37e-49d2-9eaa-77246bb593df.gif "cd9e6bc8-c37e-49d2-9eaa-77246bb593df")</span><span class="sxs-lookup"><span data-stu-id="6fe5d-170">![Business Data List](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/cd9e6bc8-c37e-49d2-9eaa-77246bb593df.gif "cd9e6bc8-c37e-49d2-9eaa-77246bb593df")</span></span>  
  
3.  <span data-ttu-id="6fe5d-171">Cliquez sur **ouvrir le volet d’outils**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-171">Click **Open the tool pane**.</span></span>  
  
4.  <span data-ttu-id="6fe5d-172">Le volet d’outils liste de données métiers s’ouvre dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-172">The Business Data List tool pane opens in the right pane.</span></span> <span data-ttu-id="6fe5d-173">Dans le **liste de données métiers** section, pour le **Type** , cliquez sur le **Parcourir** bouton.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-173">In the **Business Data List** section, for the **Type** field, click the **Browse** button.</span></span>  
  
     <span data-ttu-id="6fe5d-174">![Sélectionnez le Type](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a054ed0e-0880-4154-9050-a00da356a4f6.gif "a054ed0e-0880-4154-9050-a00da356a4f6")</span><span class="sxs-lookup"><span data-stu-id="6fe5d-174">![Select the Type](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a054ed0e-0880-4154-9050-a00da356a4f6.gif "a054ed0e-0880-4154-9050-a00da356a4f6")</span></span>  
  
5.  <span data-ttu-id="6fe5d-175">Dans le **sélecteur de Type de données métiers** boîte de dialogue, sélectionnez le **EchoWSLob_Instance** application, puis sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-175">In the **Business Data Type Picker** dialog box, select the **EchoWSLob_Instance** application, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="6fe5d-176">Dans le volet d’outils liste de données d’entreprise, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-176">On the Business Data List tool pane, click **OK**.</span></span>  
  
7.  <span data-ttu-id="6fe5d-177">Vous sont présentées avec un champ qui vous permet d’entrer une valeur de message d’accueil à passer à la méthode EchoGreetings.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-177">You are presented with a field that allows you to enter a greeting value to pass to the EchoGreetings method.</span></span> <span data-ttu-id="6fe5d-178">Entrez des données dans le champ de message d’accueil, cliquez sur **récupérer les données**.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-178">Enter data in the greeting field and click **Retrieve Data**.</span></span> <span data-ttu-id="6fe5d-179">Il appelle la méthode EchoGreetings de l’adaptateur d’écho hébergé dans IIS et retourne une réponse.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-179">This invokes the EchoGreetings method of the Echo adapter hosted in IIS and returns a response.</span></span>  
  
     <span data-ttu-id="6fe5d-180">![Liste EchoGreetings](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/f5a22fcd-2ae6-4384-9879-f0abd0255325.gif "f5a22fcd-2ae6-4384-9879-f0abd0255325")</span><span class="sxs-lookup"><span data-stu-id="6fe5d-180">![EchoGreetings List](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/f5a22fcd-2ae6-4384-9879-f0abd0255325.gif "f5a22fcd-2ae6-4384-9879-f0abd0255325")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6fe5d-181">La colonne de nom ne contient-elle pas les informations d’utilisateur, mais affiche uniquement les BDC. Nom.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-181">The name column does not contain the user information, but only displays BDC.Name.</span></span> <span data-ttu-id="6fe5d-182">Cela se produit, car le catalogue de données métiers attend seulement une structure de l’enregistrement simple et n’affiche pas la structure complexe représentée par le champ nom.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-182">This occurs because the BDC expects only a simple record structure, and does not display the complex structure represented by the name field.</span></span>  
  
8.  <span data-ttu-id="6fe5d-183">Cliquez sur **quitter le Mode édition** à partir de l’angle supérieur de la page.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-183">Click **Exit Edit Mode** from the upper corner of the page.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="6fe5d-184">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="6fe5d-184">What did I just do?</span></span>  
 <span data-ttu-id="6fe5d-185">Vous avez utilisé l’Administration centrale de SharePoint 3.0 pour importer une définition d’application et créer des composants WebPart qui utilisent cette définition d’appeler l’opération EchoGreetings de l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-185">You have used the SharePoint 3.0 Central Administration to import an application definition, and create Web Parts that use this definition to invoke the EchoGreetings operation of the Echo adapter.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6fe5d-186">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="6fe5d-186">Next Steps</span></span>  
 <span data-ttu-id="6fe5d-187">Ce didacticiel est terminé.</span><span class="sxs-lookup"><span data-stu-id="6fe5d-187">This tutorial is complete.</span></span> <span data-ttu-id="6fe5d-188">Pour plus d’informations à l’aide du catalogue de données métiers, consultez « Catalogue de données métiers » à [http://go.microsoft.com/fwlink/?LinkId=119921](http://go.microsoft.com/fwlink/?LinkId=119921).</span><span class="sxs-lookup"><span data-stu-id="6fe5d-188">For more information using the Business Data Catalog, see “Business Data Catalog” at [http://go.microsoft.com/fwlink/?LinkId=119921](http://go.microsoft.com/fwlink/?LinkId=119921).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fe5d-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6fe5d-189">See Also</span></span>  
 [<span data-ttu-id="6fe5d-190">Didacticiel 3 : Hébergeant l’adaptateur de l’écho dans IIS</span><span class="sxs-lookup"><span data-stu-id="6fe5d-190">Tutorial 3: Hosting the Echo Adapter in IIS</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md)