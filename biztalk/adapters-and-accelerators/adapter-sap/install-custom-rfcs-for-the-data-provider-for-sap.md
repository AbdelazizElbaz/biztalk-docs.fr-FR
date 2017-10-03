---
title: "Installez les RFC personnalisés pour le fournisseur de données pour SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation, custom RFCs for the Data Provider for SAP
- installing, custom RFCs for the Data Provider for SAP
- installing custom RFCs, how to
ms.assetid: 7a99db70-fa5a-4c04-9dc7-b71613d4364e
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c295834f00781cc92a6aa47d01374c80b485149d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="install-custom-rfcs-for-the-data-provider-for-sap"></a><span data-ttu-id="8dc40-102">Installez les RFC personnalisés pour le fournisseur de données pour SAP</span><span class="sxs-lookup"><span data-stu-id="8dc40-102">Install Custom RFCs for the Data Provider for SAP</span></span>
<span data-ttu-id="8dc40-103">Installez les RFC personnalisés si vous souhaitez utiliser le fournisseur de données .NET Framework pour mySAP Business Suite pour accéder au système SAP.</span><span class="sxs-lookup"><span data-stu-id="8dc40-103">Install the custom RFCs if you want to use the .NET Framework Data Provider for mySAP Business Suite to access the SAP system.</span></span>

<span data-ttu-id="8dc40-104">Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requiert les RFC personnalisés à effectuer certaines opérations sur le système SAP pour :</span><span class="sxs-lookup"><span data-stu-id="8dc40-104">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requires custom RFCs to perform some operations on the SAP system to:</span></span>
  
-   <span data-ttu-id="8dc40-105">Exécuter l’opération de sélection, le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requiert Z_EXTRACT_DATA_OO RFC.</span><span class="sxs-lookup"><span data-stu-id="8dc40-105">Run the SELECT operation, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requires Z_EXTRACT_DATA_OO RFC.</span></span>  
  
-   <span data-ttu-id="8dc40-106">Exécutez l’opération EXECQUERY, le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requiert Z_EXECUTE_SAP_QUERY RFC.</span><span class="sxs-lookup"><span data-stu-id="8dc40-106">Run the EXECQUERY operation, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requires Z_EXECUTE_SAP_QUERY RFC.</span></span>  
  
<span data-ttu-id="8dc40-107">Pour effectuer ces opérations sur le système SAP, vous devez installer ces RFC personnalisés sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="8dc40-107">To perform these operations on the SAP system, you must install these custom RFCs on the SAP system.</span></span> <span data-ttu-id="8dc40-108">Si vous avez choisi d’installer le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] avec la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], le programme d’installation copie le transport RFC pour les [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] comme un fichier compressé (customRFC.zip) sur le système sur lequel vous installez l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="8dc40-108">If you chose to install the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] along with the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], the Setup program copies the RFC transport for the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] as a compressed file (customRFC.zip) on the system where you install the adapter.</span></span> <span data-ttu-id="8dc40-109">Le fichier zip est généralement installé sur  *\<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Microsoft .NET Framework Data Provider pour mySAP Business Suite*.</span><span class="sxs-lookup"><span data-stu-id="8dc40-109">The zip file is typically installed at *\<installation drive>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Microsoft .NET Framework Data Provider for mySAP Business Suite*.</span></span> 
  
 <span data-ttu-id="8dc40-110">Après avoir extrait le fichier zip, vous trouverez les quatre fichiers de données, deux après l’attribution de noms de modèle K9 *. BI1 (par exemple, semblable à K900534. BI1) et les deux autres suivant le modèle R9\*. BI1 (par exemple, semblable à R900534. BI1).</span><span class="sxs-lookup"><span data-stu-id="8dc40-110">After extracting the zip file, you will find four data files, two following the naming pattern K9*.BI1 (for example, similar to K900534.BI1), and the other two following the pattern R9\*.BI1 (for example, similar to R900534.BI1).</span></span>  
  

  
1.  <span data-ttu-id="8dc40-111">Copiez les fichiers extraits à partir de l’ordinateur qui exécute les adaptateurs au serveur d’applications SAP.</span><span class="sxs-lookup"><span data-stu-id="8dc40-111">Copy the extracted files from the computer running the adapters to the SAP application server.</span></span>  
  
    1.  <span data-ttu-id="8dc40-112">Ouvrez une session en tant que l’administrateur du système SAP r/3 au serveur d’applications SAP de votre système de développement.</span><span class="sxs-lookup"><span data-stu-id="8dc40-112">Log in as the SAP R/3 system administrator to the SAP application server of your development system.</span></span>  
  
    2.  <span data-ttu-id="8dc40-113">Copiez les fichiers de deux transport avec le modèle d’affectation de noms K9 *. BI1 du répertoire d’installation sur l’ordinateur qui exécute les adaptateurs dans le répertoire suivant sur le serveur d’applications SAP :</span><span class="sxs-lookup"><span data-stu-id="8dc40-113">Copy the two transport files with the naming pattern K9*.BI1 from the installation directory on the computer running the adapters to the following directory on the SAP application server:</span></span>  
  
         `<drive>:\usr\sap\trans\cofiles`  
  
    3.  <span data-ttu-id="8dc40-114">Copiez les fichiers de deux transport avec le modèle d’affectation de noms R9 *. BI1 du répertoire d’installation sur l’ordinateur qui exécute les adaptateurs dans le répertoire suivant sur le serveur d’applications SAP :</span><span class="sxs-lookup"><span data-stu-id="8dc40-114">Copy the two transport files with the naming pattern R9*.BI1 from the installation directory on the computer running the adapters to the following directory on the SAP application server:</span></span>  
  
         `<drive>:\usr\sap\trans\data`  
  
2.  <span data-ttu-id="8dc40-115">Chargez le transport dans la mémoire tampon de transport sur le serveur d’applications SAP.</span><span class="sxs-lookup"><span data-stu-id="8dc40-115">Load the transport into the transport buffer on the SAP application server.</span></span>  
  
    1.  <span data-ttu-id="8dc40-116">À l’invite de commandes, accédez au répertoire de programme de transport sur le serveur d’applications SAP :</span><span class="sxs-lookup"><span data-stu-id="8dc40-116">At the command prompt, navigate to the transport program directory on the SAP application server:</span></span>  
  
         `<drive>:\usr\sap\trans\bin`  
  
    2.  <span data-ttu-id="8dc40-117">Pour charger le transport dans la mémoire tampon de transport, exécutez la commande suivante à la `\usr\sap\trans\bin` active et remplacer *sysid* avec l’ID système de votre système de développement :</span><span class="sxs-lookup"><span data-stu-id="8dc40-117">To load the transport into the transport buffer, execute the following command at the `\usr\sap\trans\bin` directory and replace *sysid* with the system ID of your development system:</span></span>  
  
        ```  
        tp addtobuffer <TransportNumber> <sysid> pf=TP_DOMAIN_<sysid>.PFL  
        ```  
  
         <span data-ttu-id="8dc40-118">WHERE, *TransportNumber* est le nombre réel de transport (par exemple BI1K900534).</span><span class="sxs-lookup"><span data-stu-id="8dc40-118">where, *TransportNumber* is the actual transport number (for example BI1K900534).</span></span>  
  
    3.  <span data-ttu-id="8dc40-119">Après le `tp` commande terminée, vous verrez un rapport similaire à la suivante :</span><span class="sxs-lookup"><span data-stu-id="8dc40-119">After the `tp` command finishes, you will see a report similar to the following:</span></span>  
  
        ```  
        This is tp version 320.56.66 (release 620)  
        Addtobuffer successful for TransportNumber  
        tp finished with return code: 0  
        ```  
  
         <span data-ttu-id="8dc40-120">Code de retour « 0 » signifie que l’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="8dc40-120">Return code "0" means that the operation succeeded.</span></span>  
  
         <span data-ttu-id="8dc40-121">Un code de retour de 0 ou 4 est acceptable.</span><span class="sxs-lookup"><span data-stu-id="8dc40-121">A return code of 0 or 4 is acceptable.</span></span> <span data-ttu-id="8dc40-122">Contactez le Service clientèle Microsoft et la prise en charge, si vous recevez un code de retour de 8 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="8dc40-122">Contact Microsoft Customer Service and Support, if you receive a return code of 8 or above.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="8dc40-123">Répétez les étapes (b) et (c) pour le deuxième ensemble de fichiers de transport.</span><span class="sxs-lookup"><span data-stu-id="8dc40-123">Repeat steps (b) and (c) for the second set of transport files.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="8dc40-124">Vous pouvez facilement déterminer le nombre réel de transport à partir du nom de fichier cofile.</span><span class="sxs-lookup"><span data-stu-id="8dc40-124">You can easily derive the actual transport number from the cofile file name.</span></span> <span data-ttu-id="8dc40-125">Par exemple, un cofile nommé K900534. BI1 fournit un nombre de transport de BI1K900534.</span><span class="sxs-lookup"><span data-stu-id="8dc40-125">For example, a cofile named K900534.BI1 provides a transport number of BI1K900534.</span></span>  
  
3.  <span data-ttu-id="8dc40-126">Importer le transport SAP.</span><span class="sxs-lookup"><span data-stu-id="8dc40-126">Import the transport into SAP.</span></span>  
  
    1.  <span data-ttu-id="8dc40-127">Exécutez la commande suivante à l’invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="8dc40-127">Execute the following command at the command prompt:</span></span>  
  
        ```  
        tp import <TransportNumber> <sysid> client=<clientnumber> pf=TP_DOMAIN_<sysid>.PFL  
        ```  
  
         <span data-ttu-id="8dc40-128">Remplacez *sysid* avec l’ID système de votre système de développement.</span><span class="sxs-lookup"><span data-stu-id="8dc40-128">Replace *sysid* with the system ID of your development system.</span></span> <span data-ttu-id="8dc40-129">Remplacez *clientnumber* avec le nombre de clients de votre système de développement.</span><span class="sxs-lookup"><span data-stu-id="8dc40-129">Replace *clientnumber* with the client number of your development system.</span></span>  
  
         <span data-ttu-id="8dc40-130">Vous pouvez utiliser le paramètre U2 pour remplacer des objets précédemment installés, comme suit :</span><span class="sxs-lookup"><span data-stu-id="8dc40-130">You can use the U2 parameter to overwrite previously installed objects, as follows:</span></span>  
  
        ```  
        tp import <TransportNumber> <sysid> client=<clientnumber> U2  
        ```  
  
         <span data-ttu-id="8dc40-131">ou</span><span class="sxs-lookup"><span data-stu-id="8dc40-131">or</span></span>  
  
        ```  
        tp import <TransportNumber> <sysid> client=<clientnumber> pf=TP_DOMAIN_<sysid>.PFL U2  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="8dc40-132">Vous pouvez facilement déterminer le nombre réel de transport à partir du nom de fichier cofile.</span><span class="sxs-lookup"><span data-stu-id="8dc40-132">You can easily derive the actual transport number from the cofile file name.</span></span> <span data-ttu-id="8dc40-133">Par exemple, un cofile nommé K900534. BI1 fournit un nombre de transport de BI1K900534.</span><span class="sxs-lookup"><span data-stu-id="8dc40-133">For example, a cofile named K900534.BI1 provides a transport number of BI1K900534.</span></span>  
  
    2.  <span data-ttu-id="8dc40-134">Après le `tp` commande terminée, vous verrez un rapport similaire à la suivante :</span><span class="sxs-lookup"><span data-stu-id="8dc40-134">After the `tp` command finishes, you will see a report similar to the following:</span></span>  
  
        ```  
        This is tp version 320.56.66 (release 620)  
        This is R3trans.exe version 6.08 (release 620 - 04.02.03 - 14:54:00).  
        R3trans.exe finished (0000).  
        This is R3trans.exe version 6.08 (release 620 - 04.02.03 - 14:54:00).  
        R3trans.exe finished (0000).  
        tp finished with return code: 0  
        ```  
  
         <span data-ttu-id="8dc40-135">Code de retour « 0 » signifie que l’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="8dc40-135">Return code "0" means that the operation succeeded.</span></span>  
  
         <span data-ttu-id="8dc40-136">Un code de retour de 0 ou 4 est acceptable.</span><span class="sxs-lookup"><span data-stu-id="8dc40-136">A return code of 0 or 4 is acceptable.</span></span> <span data-ttu-id="8dc40-137">Si vous recevez un code de retour de 8 ou version ultérieure, contactez le support technique et Service clientèle Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8dc40-137">Contact Microsoft Customer Service and Support if you receive a return code of 8 or above.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="8dc40-138">Répétez les étapes (a) et (b) pour le deuxième ensemble de fichiers de transport.</span><span class="sxs-lookup"><span data-stu-id="8dc40-138">Repeat steps (a) and (b) for the second set of transport files.</span></span>  
  
4.  <span data-ttu-id="8dc40-139">Vérifiez le journal de transport.</span><span class="sxs-lookup"><span data-stu-id="8dc40-139">Check the transport log.</span></span>  
  
5.  <span data-ttu-id="8dc40-140">Vérifiez le journal de transport dans l’organisateur de Transport d’interface utilisateur graphique SAP à l’aide de la transaction SE09 pour vérifier qu’il n’y a aucune erreur.</span><span class="sxs-lookup"><span data-stu-id="8dc40-140">Check the transport log in SAP GUI Transport Organizer using transaction SE09 to verify that there are no errors.</span></span>  
  
 <span data-ttu-id="8dc40-141">Paramètre d’autorisation de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="8dc40-141">Setting User Authorization</span></span>  
 <span data-ttu-id="8dc40-142">Le document RFC Z_EXTRACT_DATA_OO requiert l’ID d’utilisateur avec des objets d’autorisation spécifique.</span><span class="sxs-lookup"><span data-stu-id="8dc40-142">The Z_EXTRACT_DATA_OO RFC requires user IDs with specific authorization objects.</span></span> <span data-ttu-id="8dc40-143">Utilisez les outils d’administration de l’interface graphique utilisateur SAP d’autorisation pour définir les restrictions minimales sur l’exécution de la RFC :</span><span class="sxs-lookup"><span data-stu-id="8dc40-143">Use the SAP GUI authorization administration tools to set the minimum restrictions on the execution of the RFC:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8dc40-144">Vous n’avez pas besoin définir l’autorisation pour le document RFC Z_EXECUTE_SAP_QUERY.</span><span class="sxs-lookup"><span data-stu-id="8dc40-144">You do not need to set the authorization for the Z_EXECUTE_SAP_QUERY RFC.</span></span>  
  
-   <span data-ttu-id="8dc40-145">Z_EXTRACT_DATA_OO requiert S_TABU_DIS et Z_EIP_TABL.</span><span class="sxs-lookup"><span data-stu-id="8dc40-145">Z_EXTRACT_DATA_OO requires both S_TABU_DIS and Z_EIP_TABL.</span></span> <span data-ttu-id="8dc40-146">Les valeurs suivantes fournissent les restrictions minimales pour S_TABU_DIS, qui permettent aux utilisateurs d’afficher les métadonnées pour n’importe quelle table dans le système.</span><span class="sxs-lookup"><span data-stu-id="8dc40-146">The following values provide the minimum restrictions for S_TABU_DIS, which allow users to view metadata for any table in the system.</span></span>  
  
    -   <span data-ttu-id="8dc40-147">ACTVT : 03</span><span class="sxs-lookup"><span data-stu-id="8dc40-147">ACTVT: 03</span></span>  
  
    -   <span data-ttu-id="8dc40-148">DICBERCLS : *</span><span class="sxs-lookup"><span data-stu-id="8dc40-148">DICBERCLS: *</span></span>  
  
     <span data-ttu-id="8dc40-149">Vous pouvez utiliser DICBERCLS pour restreindre l’autorisation aux tables par classe d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="8dc40-149">You can use DICBERCLS to restrict authorization to tables by authorization class.</span></span>  
  
     <span data-ttu-id="8dc40-150">Vous pouvez utiliser le tableau TDDAT pour afficher la classe d’autorisation pour les tables.</span><span class="sxs-lookup"><span data-stu-id="8dc40-150">You can use the TDDAT table to view the authorization class for tables.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8dc40-151">Pour empêcher les modifications aux tables par les transactions de maintenance de table, vous ne devez octroyer des privilèges d’affichage dans un environnement de production (ACTVT : 03 définit l’activité autorisée à afficher).</span><span class="sxs-lookup"><span data-stu-id="8dc40-151">To prevent changes to tables by table maintenance transactions, you should only grant display privileges in a production environment (ACTVT: 03 sets the permissible activity to display).</span></span>  
  
     <span data-ttu-id="8dc40-152">Les valeurs minimales pour Z_EIP_TABL sont :</span><span class="sxs-lookup"><span data-stu-id="8dc40-152">The minimum values for Z_EIP_TABL are:</span></span>  
  
    -   <span data-ttu-id="8dc40-153">ACTVT : 03</span><span class="sxs-lookup"><span data-stu-id="8dc40-153">ACTVT: 03</span></span>  
  
    -   <span data-ttu-id="8dc40-154">TABLE : *</span><span class="sxs-lookup"><span data-stu-id="8dc40-154">TABLE: *</span></span>  
  
     <span data-ttu-id="8dc40-155">Vous pouvez utiliser la TABLE pour définir explicitement les tables autorisés.</span><span class="sxs-lookup"><span data-stu-id="8dc40-155">You can use TABLE to explicitly define the authorized tables.</span></span> <span data-ttu-id="8dc40-156">Notez que S_TABU_DIS est également utilisée dans d’autres transactions.</span><span class="sxs-lookup"><span data-stu-id="8dc40-156">Note, too, that S_TABU_DIS is also used in other transactions.</span></span>  
  
##### <a name="to-set-user-authorization"></a><span data-ttu-id="8dc40-157">Pour définir l’autorisation de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="8dc40-157">To set user authorization</span></span>  
  
1.  <span data-ttu-id="8dc40-158">Démarrez l’interface utilisateur graphique SAP.</span><span class="sxs-lookup"><span data-stu-id="8dc40-158">Start the SAP GUI.</span></span> <span data-ttu-id="8dc40-159">Atteindre le code T, type `pfcg`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="8dc40-159">Go to T-code, type `pfcg`, and press ENTER.</span></span>  
  
2.  <span data-ttu-id="8dc40-160">Dans le **rôle** texte, entrez un nom de rôle que vous souhaitez créer, par exemple, `ZTEST`, puis cliquez sur **rôle**.</span><span class="sxs-lookup"><span data-stu-id="8dc40-160">In the **Role** text box, enter a role name you want to create, for example, `ZTEST`, and then click **Role**.</span></span>  
  
3.  <span data-ttu-id="8dc40-161">Dans le **Create Role** , cliquez sur le **autorisations** onglet.</span><span class="sxs-lookup"><span data-stu-id="8dc40-161">In the **Create Role** page, click the **Authorizations** tab.</span></span>  
  
     <span data-ttu-id="8dc40-162">Si vous êtes invité à enregistrer le rôle, cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="8dc40-162">If prompted to save the role, click **Yes**.</span></span>  
  
4.  <span data-ttu-id="8dc40-163">Dans le **modifier les rôles** , cliquez sur le **modifier les données d’autorisation** bouton.</span><span class="sxs-lookup"><span data-stu-id="8dc40-163">In the **Change Roles** page, click the **Change Authorization Data** button.</span></span>  
  
5.  <span data-ttu-id="8dc40-164">Si vous êtes invité à sélectionner un modèle à partir de la **choisir un modèle** boîte de dialogue, cliquez sur **ne sélectionnez pas de modèles**.</span><span class="sxs-lookup"><span data-stu-id="8dc40-164">If you are prompted to select a template from the **Choose Template** dialog box, click **Do not select templates**.</span></span>  
  
6.  <span data-ttu-id="8dc40-165">Dans le **modification du rôle : autorisations** , cliquez sur le **manuellement** bouton.</span><span class="sxs-lookup"><span data-stu-id="8dc40-165">In the **Change role: Authorizations** page, click the **Manually** button.</span></span>  
  
7.  <span data-ttu-id="8dc40-166">Dans le **sélection manuelle des autorisations** , entrez le nom de l’objet d’autorisation `Z_EIP_TABL` et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="8dc40-166">In the **Manual selection of authorizations** box, enter the name of the authorization object `Z_EIP_TABL` and press ENTER.</span></span>  
  
8.  <span data-ttu-id="8dc40-167">Dans le **modification du rôle : autorisations** page, développez les nœuds jusqu'à ce que les zones de texte pour **activité** et **nom de la Table**.</span><span class="sxs-lookup"><span data-stu-id="8dc40-167">In the **Change role: Authorizations** page, expand the nodes until you see the text boxes for **Activity** and **Table Name**.</span></span> <span data-ttu-id="8dc40-168">Pour le **activité** texte, entrez la valeur `03`.</span><span class="sxs-lookup"><span data-stu-id="8dc40-168">For the **Activity** text box, enter the value `03`.</span></span> <span data-ttu-id="8dc40-169">Pour le **nom de la Table** texte, entrez la valeur `*`.</span><span class="sxs-lookup"><span data-stu-id="8dc40-169">For the **Table Name** text box, enter the value `*`.</span></span>  
  
9. <span data-ttu-id="8dc40-170">Cliquez sur le **enregistrer** bouton pour générer le profil.</span><span class="sxs-lookup"><span data-stu-id="8dc40-170">Click the **Save** button to generate the profile.</span></span>  
  
10. <span data-ttu-id="8dc40-171">Revenez à la **modifier les rôles** page, puis cliquez sur le **utilisateur** onglet.</span><span class="sxs-lookup"><span data-stu-id="8dc40-171">Go back to the **Change Roles** page and click the **User** tab.</span></span>  
  
11. <span data-ttu-id="8dc40-172">Dans le **utilisateur** onglet, affectez un ID utilisateur pour le rôle en entrant le nom d’utilisateur dans le **ID utilisateur** colonne, puis cliquez sur le **comparaison de l’utilisateur** bouton.</span><span class="sxs-lookup"><span data-stu-id="8dc40-172">In the **User** tab, assign a user ID for the role by entering the user name in the **User ID** column, and click the **User comparison** button.</span></span>  
  
12. <span data-ttu-id="8dc40-173">Dans le **comparer un enregistrement de rôle d’utilisateur principal**, cliquez sur **effectuer la comparaison** pour mettre à jour l’enregistrement principal.</span><span class="sxs-lookup"><span data-stu-id="8dc40-173">In the **Compare Role User Master Record**, click **Complete comparison** to update the master record.</span></span> <span data-ttu-id="8dc40-174">Lorsque vous êtes invité à enregistrer le rôle, cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="8dc40-174">When prompted to save the role, click **Yes**.</span></span>  
  
13. <span data-ttu-id="8dc40-175">Enregistrez et quittez.</span><span class="sxs-lookup"><span data-stu-id="8dc40-175">Save and exit.</span></span>  
  
<span data-ttu-id="8dc40-176">Vérification de l’Installation de la RFC personnalisés</span><span class="sxs-lookup"><span data-stu-id="8dc40-176">Verifying Custom RFC Installation</span></span>  
 <span data-ttu-id="8dc40-177">Après avoir installé les RFC personnalisés, vous pouvez vérifier si les documents RFC a été installé correctement.</span><span class="sxs-lookup"><span data-stu-id="8dc40-177">After you install the custom RFCs, you can verify whether the RFCs installed correctly.</span></span>  
  
-   <span data-ttu-id="8dc40-178">Pour les RFC Z_EXECUTE_SAP_QUERY, vous pouvez le faire en exécutant une requête prédéfinie à l’aide du système SAP le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8dc40-178">For Z_EXECUTE_SAP_QUERY RFC, you can do so by executing a pre-defined query in SAP system using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  
  
-   <span data-ttu-id="8dc40-179">Pour Z_EXTRACT_DATA_OO RFC, vous pouvez le faire en effectuant les tests suivants pour vérifier que le document RFC fonctionne et est prêt à être utilisé dans votre système.</span><span class="sxs-lookup"><span data-stu-id="8dc40-179">For Z_EXTRACT_DATA_OO RFC, you can do so by performing the following tests to confirm that the RFC operates and is ready for use in your system.</span></span>  
  
##### <a name="to-test-the-installation-of-zextractdataoo"></a><span data-ttu-id="8dc40-180">Pour tester l’installation de Z_EXTRACT_DATA_OO</span><span class="sxs-lookup"><span data-stu-id="8dc40-180">To test the installation of Z_EXTRACT_DATA_OO</span></span>  
  
1.  <span data-ttu-id="8dc40-181">Dans les outils d’administration d’autorisation interface GUI SAP, exécutez SE37, le module de fonction Z_EXTRACT_DATA_OO, et puis exécutez la RFC en mode test en appuyant sur `F8`.</span><span class="sxs-lookup"><span data-stu-id="8dc40-181">In the SAP GUI authorization administration tools, execute SE37, function module Z_EXTRACT_DATA_OO, and then run the RFC in test mode by pressing `F8`.</span></span> <span data-ttu-id="8dc40-182">Remplir les paramètres comme suit.</span><span class="sxs-lookup"><span data-stu-id="8dc40-182">Populate the parameters as follows.</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="8dc40-183">IN_METADATA_ONLY</span><span class="sxs-lookup"><span data-stu-id="8dc40-183">IN_METADATA_ONLY</span></span>||  
    |<span data-ttu-id="8dc40-184">IN_METADATA_LANGUAGE</span><span class="sxs-lookup"><span data-stu-id="8dc40-184">IN_METADATA_LANGUAGE</span></span>|<span data-ttu-id="8dc40-185">EN</span><span class="sxs-lookup"><span data-stu-id="8dc40-185">EN</span></span>|  
    |<span data-ttu-id="8dc40-186">IN_FROM_TABLE</span><span class="sxs-lookup"><span data-stu-id="8dc40-186">IN_FROM_TABLE</span></span>|<span data-ttu-id="8dc40-187">T000</span><span class="sxs-lookup"><span data-stu-id="8dc40-187">T000</span></span>|  
    |<span data-ttu-id="8dc40-188">IN_OUTPUT_MODE</span><span class="sxs-lookup"><span data-stu-id="8dc40-188">IN_OUTPUT_MODE</span></span>|<span data-ttu-id="8dc40-189">S</span><span class="sxs-lookup"><span data-stu-id="8dc40-189">S</span></span>|  
    |<span data-ttu-id="8dc40-190">IN_OUTPUT_FILENAME</span><span class="sxs-lookup"><span data-stu-id="8dc40-190">IN_OUTPUT_FILENAME</span></span>||  
    |<span data-ttu-id="8dc40-191">IN_USE_FIELD_EXITS</span><span class="sxs-lookup"><span data-stu-id="8dc40-191">IN_USE_FIELD_EXITS</span></span>|<span data-ttu-id="8dc40-192">X</span><span class="sxs-lookup"><span data-stu-id="8dc40-192">X</span></span>|  
    |<span data-ttu-id="8dc40-193">IN_SET_ROWCOUNT</span><span class="sxs-lookup"><span data-stu-id="8dc40-193">IN_SET_ROWCOUNT</span></span>|<span data-ttu-id="8dc40-194">0</span><span class="sxs-lookup"><span data-stu-id="8dc40-194">0</span></span>|  
    |<span data-ttu-id="8dc40-195">IN_DELIMITER</span><span class="sxs-lookup"><span data-stu-id="8dc40-195">IN_DELIMITER</span></span>||  
    |<span data-ttu-id="8dc40-196">IN_PACKET_SIZE</span><span class="sxs-lookup"><span data-stu-id="8dc40-196">IN_PACKET_SIZE</span></span>|<span data-ttu-id="8dc40-197">50,000</span><span class="sxs-lookup"><span data-stu-id="8dc40-197">50,000</span></span>|  
    |<span data-ttu-id="8dc40-198">IN_MAX_WRITE_ATTEMPTS</span><span class="sxs-lookup"><span data-stu-id="8dc40-198">IN_MAX_WRITE_ATTEMPTS</span></span>|<span data-ttu-id="8dc40-199">4</span><span class="sxs-lookup"><span data-stu-id="8dc40-199">4</span></span>|  
    |<span data-ttu-id="8dc40-200">IN_RETRY_DELAY</span><span class="sxs-lookup"><span data-stu-id="8dc40-200">IN_RETRY_DELAY</span></span>|<span data-ttu-id="8dc40-201">30</span><span class="sxs-lookup"><span data-stu-id="8dc40-201">30</span></span>|  
    |<span data-ttu-id="8dc40-202">IN_SQL_DATES_ON</span><span class="sxs-lookup"><span data-stu-id="8dc40-202">IN_SQL_DATES_ON</span></span>||  
  
2.  <span data-ttu-id="8dc40-203">Cliquez sur **Execute** ou appuyez sur `F8`.</span><span class="sxs-lookup"><span data-stu-id="8dc40-203">Click **Execute** or press `F8`.</span></span>  
  
3.  <span data-ttu-id="8dc40-204">Dans le volet de résultats, vérifiez les points suivants.</span><span class="sxs-lookup"><span data-stu-id="8dc40-204">In the results pane, check the following.</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="8dc40-205">OUT_TABLEHEADER</span><span class="sxs-lookup"><span data-stu-id="8dc40-205">OUT_TABLEHEADER</span></span>|<span data-ttu-id="8dc40-206">\<Les métadonnées générales T000 ></span><span class="sxs-lookup"><span data-stu-id="8dc40-206">\<T000 general metadata></span></span>|  
    |<span data-ttu-id="8dc40-207">OUT_TECHNICALSETTINGS</span><span class="sxs-lookup"><span data-stu-id="8dc40-207">OUT_TECHNICALSETTINGS</span></span>|<span data-ttu-id="8dc40-208">\<Les métadonnées de niveau de base de données techniques T000 ></span><span class="sxs-lookup"><span data-stu-id="8dc40-208">\<T000 technical database level metadata></span></span>|  
    |<span data-ttu-id="8dc40-209">OUT_RECORDLENGTH</span><span class="sxs-lookup"><span data-stu-id="8dc40-209">OUT_RECORDLENGTH</span></span>|<span data-ttu-id="8dc40-210">\<varie selon la version SAP ></span><span class="sxs-lookup"><span data-stu-id="8dc40-210">\<depends on SAP version></span></span>|  
    |<span data-ttu-id="8dc40-211">OUT_RECORDCOUNT</span><span class="sxs-lookup"><span data-stu-id="8dc40-211">OUT_RECORDCOUNT</span></span>|<span data-ttu-id="8dc40-212">\<Vérifiez le nombre de clients dans votre système avec SE16 sur T000 ></span><span class="sxs-lookup"><span data-stu-id="8dc40-212">\<confirm the number of clients in your system with SE16 on T000></span></span>|  
    |<span data-ttu-id="8dc40-213">OUT_ZDATATABLE</span><span class="sxs-lookup"><span data-stu-id="8dc40-213">OUT_ZDATATABLE</span></span>|<span data-ttu-id="8dc40-214">\<vérifier ce résultat avec les données sources à l’aide de SE 16 sur T000 ></span><span class="sxs-lookup"><span data-stu-id="8dc40-214">\<confirm this result with the source data using SE 16 on T000></span></span>|  
    |<span data-ttu-id="8dc40-215">OUT_RETURN_TAB</span><span class="sxs-lookup"><span data-stu-id="8dc40-215">OUT_RETURN_TAB</span></span>|<span data-ttu-id="8dc40-216">S 001 réussite</span><span class="sxs-lookup"><span data-stu-id="8dc40-216">S 001 Success</span></span>|  
  
## <a name="remove-the-rfc-for-the-data-provider-for-sap"></a><span data-ttu-id="8dc40-217">Supprimer la demande de changement pour le fournisseur de données pour SAP</span><span class="sxs-lookup"><span data-stu-id="8dc40-217">Remove the RFC for the Data Provider for SAP</span></span>  
  
1.  <span data-ttu-id="8dc40-218">Dans le navigateur d’objet interface utilisateur graphique SAP (SE80), rechercher tous les objets avec la classe de développement ZMSBI.</span><span class="sxs-lookup"><span data-stu-id="8dc40-218">In the SAP GUI Object Navigator (SE80), find all the objects with the ZMSBI development class.</span></span>  
  
2.  <span data-ttu-id="8dc40-219">Supprimer tous les objets avec la classe de développement ZMSBI les dossiers d’objets suivants :</span><span class="sxs-lookup"><span data-stu-id="8dc40-219">Delete all objects with the ZMSBI development class from the following Dictionary Objects folders:</span></span>  
  
    -   <span data-ttu-id="8dc40-220">Structures</span><span class="sxs-lookup"><span data-stu-id="8dc40-220">Structures</span></span>  
  
    -   <span data-ttu-id="8dc40-221">Groupes de fonctions</span><span class="sxs-lookup"><span data-stu-id="8dc40-221">Function Groups</span></span>  
  
    -   <span data-ttu-id="8dc40-222">Objet autorisé</span><span class="sxs-lookup"><span data-stu-id="8dc40-222">Authorized Object</span></span>  
  
3.  <span data-ttu-id="8dc40-223">Déclencher un transport et migrez-le à chaque système où vous avez installé une commande RFC (développement, test et production systèmes, par exemple).</span><span class="sxs-lookup"><span data-stu-id="8dc40-223">Raise a transport, and migrate it through each system where you installed an RFC (development, test, and production systems, for example).</span></span>  
  
     <span data-ttu-id="8dc40-224">Pour obtenir une assistance, contactez votre administrateur de base de SAP.</span><span class="sxs-lookup"><span data-stu-id="8dc40-224">For further assistance, contact your SAP Basis Administrator.</span></span>  
     
## <a name="next"></a><span data-ttu-id="8dc40-225">Suivant</span><span class="sxs-lookup"><span data-stu-id="8dc40-225">Next</span></span>
[<span data-ttu-id="8dc40-226">Comprendre l’adaptateur BizTalk pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="8dc40-226">Understand BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)  
[<span data-ttu-id="8dc40-227">Didacticiels de l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="8dc40-227">SAP Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)