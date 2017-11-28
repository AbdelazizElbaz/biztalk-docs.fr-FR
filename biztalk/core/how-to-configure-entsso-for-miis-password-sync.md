---
title: Comment configurer la synchronisation de mot de passe MIIS ENTSSO | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89438935-37c1-4ac9-9ca2-7af8d9bfd3ae
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a1587c2e3c0d2164a7ffd3842b3d74df5b04685
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-entsso-for-miis-password-sync"></a><span data-ttu-id="77e00-102">Configuration de l'authentification unique de l'entreprise (ENTSSO) pour la synchronisation de mot de passe à partir de MIIS</span><span class="sxs-lookup"><span data-stu-id="77e00-102">How to Configure ENTSSO for MIIS Password Sync</span></span>
<span data-ttu-id="77e00-103">Après avoir configuré le fichier XML et MIIS (Microsoft Identity Integration Server), les étapes de configuration restantes se déroulent au sein du système d'authentification unique de l'entreprise (ENTSSO).</span><span class="sxs-lookup"><span data-stu-id="77e00-103">After configuring the XML file and Microsoft Identity Integration Server (MIIS), the remaining configuration steps take place in the Enterprise Single Sign-On (ENTSSO) system.</span></span>  
  
### <a name="to-allow-password-sync-from-miis"></a><span data-ttu-id="77e00-104">Pour autoriser la synchronisation de mot de passe à partir de MIIS</span><span class="sxs-lookup"><span data-stu-id="77e00-104">To allow Password Sync from MIIS</span></span>  
  
1.  <span data-ttu-id="77e00-105">Dans Enterprise Single Sign-On, cliquez sur le **serveurs** nœud.</span><span class="sxs-lookup"><span data-stu-id="77e00-105">In Enterprise Single Sign-On, click the **Servers** node.</span></span>  
  
2.  <span data-ttu-id="77e00-106">Cliquez sur le serveur approprié, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="77e00-106">Right-click the appropriate server, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="77e00-107">Cliquez sur le **synchronisation de mot de passe** onglet.</span><span class="sxs-lookup"><span data-stu-id="77e00-107">Click the **Password Sync** tab.</span></span>  
  
4.  <span data-ttu-id="77e00-108">Sélectionnez **autoriser la synchronisation du mot de passe à partir de MIIS**.</span><span class="sxs-lookup"><span data-stu-id="77e00-108">Select **Allow password sync from MIIS**.</span></span>  
  
5.  <span data-ttu-id="77e00-109">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="77e00-109">Click **OK**.</span></span>  
  
### <a name="to-enable-password-sync-on-the-system-level"></a><span data-ttu-id="77e00-110">Pour activer la synchronisation de mot de passe au niveau du système</span><span class="sxs-lookup"><span data-stu-id="77e00-110">To enable Password Sync on the system level</span></span>  
  
1.  <span data-ttu-id="77e00-111">Dans Enterprise Single Sign-On, cliquez sur le **système** nœud.</span><span class="sxs-lookup"><span data-stu-id="77e00-111">In Enterprise Single Sign-On, right-click the **System** node.</span></span>  
  
2.  <span data-ttu-id="77e00-112">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="77e00-112">Click **Properties**.</span></span>  
  
     <span data-ttu-id="77e00-113">Le **propriétés** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="77e00-113">The **Properties** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="77e00-114">Cliquez sur le **Options** onglet.</span><span class="sxs-lookup"><span data-stu-id="77e00-114">Click the **Options** tab.</span></span>  
  
4.  <span data-ttu-id="77e00-115">Dans le **activer la synchronisation de mot de passe** champ, sélectionnez **à partir de Windows vers les adaptateurs**.</span><span class="sxs-lookup"><span data-stu-id="77e00-115">In the **Enable Password Sync** field, select **From Windows to Adapters**.</span></span>  
  
     <span data-ttu-id="77e00-116">**Configuration supplémentaire**</span><span class="sxs-lookup"><span data-stu-id="77e00-116">**Additional Configuration**</span></span>  
  
     <span data-ttu-id="77e00-117">Pour terminer, vous devez configurer l'un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="77e00-117">Finally, you must configure one of the following:</span></span>  
  
    -   <span data-ttu-id="77e00-118">un adaptateur de synchronisation de mot de passe compatible avec la synchronisation des mots de passe Windows ;</span><span class="sxs-lookup"><span data-stu-id="77e00-118">A Password Sync Adapter that accepts Windows Password Sync.</span></span>  
  
    -   <span data-ttu-id="77e00-119">la synchronisation de mot de passe directe activée sur au moins une application.</span><span class="sxs-lookup"><span data-stu-id="77e00-119">Direct Password Sync enabled on at least one application.</span></span>  
  
     <span data-ttu-id="77e00-120">Pour plus d'informations sur la manière de procéder, consultez la documentation relative à la synchronisation de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="77e00-120">For information about how to do this, refer to your Password Sync documentation.</span></span>  
  
### <a name="to-configure-the-entsso-ma-for-miis-password-sync"></a><span data-ttu-id="77e00-121">Pour configurer l'agent de gestion ENTSSO pour la synchronisation de mot de passe MIIS</span><span class="sxs-lookup"><span data-stu-id="77e00-121">To configure the EntSSO MA for MIIS Password Sync</span></span>  
  
1.  <span data-ttu-id="77e00-122">Sur l’Agent de gestion ENTSSO **propriétés** , cliquez sur **configurer des Extensions**.</span><span class="sxs-lookup"><span data-stu-id="77e00-122">On the ENTSSO Management Agent **Properties** page, click **Configure Extensions**.</span></span>  
  
2.  <span data-ttu-id="77e00-123">Dans le **les informations de connexion pour l’extension de mot de passe** , cliquez sur **paramètres**.</span><span class="sxs-lookup"><span data-stu-id="77e00-123">In the **Connection information for password extension** field, click **Settings**.</span></span>  
  
3.  <span data-ttu-id="77e00-124">Dans le **Connect To** champ Entrez le nom de l’ordinateur qui reçoit les modifications de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="77e00-124">In the **Connect To** field enter the name of the computer that will receive the password changes.</span></span>  
  
     <span data-ttu-id="77e00-125">Le format du nom de l'ordinateur doit être identique à celui utilisé lors de la création du nom principal de service (SPN) pour le service ENTSSO du domaine.</span><span class="sxs-lookup"><span data-stu-id="77e00-125">The computer name must be in the same format that was used when creating the Service Principal Name (SPN) for the ENTSSO service on the domain.</span></span>  
  
     <span data-ttu-id="77e00-126">Exemple :</span><span class="sxs-lookup"><span data-stu-id="77e00-126">For example:</span></span>  
  
     <span data-ttu-id="77e00-127">Format court - SPN = ENTSSO/ABCD1411, puis entrez ABCD1411</span><span class="sxs-lookup"><span data-stu-id="77e00-127">Short format - SPN = ENTSSO/ABCD1411, then enter ABCD1411</span></span>  
  
4.  <span data-ttu-id="77e00-128">Format long - SPN = ENTSSO/ABCD1411.nom_entreprise.com, puis entrez ABCD1411.nom_entreprise.com</span><span class="sxs-lookup"><span data-stu-id="77e00-128">Long format - SPN = ENTSSO/ABCD1411.CompanyName.com then enter ABCD1411.CompanyName.com</span></span>  
  
### <a name="additional-configuration-steps"></a><span data-ttu-id="77e00-129">Étapes de configuration supplémentaires</span><span class="sxs-lookup"><span data-stu-id="77e00-129">Additional Configuration Steps</span></span>  
  
1.  <span data-ttu-id="77e00-130">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Identity Integration Server**, puis cliquez sur **Identity Manager**.</span><span class="sxs-lookup"><span data-stu-id="77e00-130">Click **Start**, point to **All Programs**, point to **Microsoft Identity Integration Server**, and then click **Identity Manager**.</span></span>  
  
2.  <span data-ttu-id="77e00-131">Dans le menu **Outils** , cliquez sur **Options**.</span><span class="sxs-lookup"><span data-stu-id="77e00-131">On the **Tools** menu, click **Options**.</span></span>  
  
3.  <span data-ttu-id="77e00-132">Sélectionnez **activer la synchronisation de mot de passe**.</span><span class="sxs-lookup"><span data-stu-id="77e00-132">Select **Enable Password Synchronization**.</span></span>  
  
4.  <span data-ttu-id="77e00-133">Dans le **afficher les Agents de gestion**, sélectionnez **ADMA**.</span><span class="sxs-lookup"><span data-stu-id="77e00-133">In the **Management Agents view**, select **ADMA**.</span></span>  
  
5.  <span data-ttu-id="77e00-134">Dans le **Action** volet, sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="77e00-134">In the **Action** pane, select **Properties**.</span></span>  
  
6.  <span data-ttu-id="77e00-135">Sur le **propriétés** page, sélectionnez **configurer des Partitions d’annuaire**, puis sélectionnez **activer cette partition comme source de synchronisation de mot de passe**.</span><span class="sxs-lookup"><span data-stu-id="77e00-135">On the **Properties** page, select **Configure Directory Partitions**, and then select **Enable this partition as a password synchronization source**.</span></span>  
  
7.  <span data-ttu-id="77e00-136">Cliquez sur **cibles**, puis sélectionnez ENTSSOMA2 pour lui permettre de recevoir les modifications de mot de passe à partir de MIIS.</span><span class="sxs-lookup"><span data-stu-id="77e00-136">Click **Targets**, and then select ENTSSOMA2 to enable it to receive password changes from MIIS.</span></span> <span data-ttu-id="77e00-137">Désactivez ENTSSOMA.</span><span class="sxs-lookup"><span data-stu-id="77e00-137">Deselect ENTSSOMA.</span></span> <span data-ttu-id="77e00-138">Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.</span><span class="sxs-lookup"><span data-stu-id="77e00-138">Click **OK**, and then click **OK** again.</span></span>  
  
8.  <span data-ttu-id="77e00-139">Dans le **Agent de gestion** afficher, sélectionnez **ENTSSOMA2**.</span><span class="sxs-lookup"><span data-stu-id="77e00-139">In the **Management Agent** view, select **ENTSSOMA2**.</span></span> <span data-ttu-id="77e00-140">Dans le volet droit, sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="77e00-140">In the right-hand pane, select **Properties**.</span></span> <span data-ttu-id="77e00-141">Sur le **propriétés** , cliquez sur **configurer des Extensions**.</span><span class="sxs-lookup"><span data-stu-id="77e00-141">On the **Properties** page, click **Configure Extensions**.</span></span>  
  
9. <span data-ttu-id="77e00-142">Vérifiez que **activer la gestion de mot de passe** est sélectionné, puis cliquez sur **paramètres**.</span><span class="sxs-lookup"><span data-stu-id="77e00-142">Confirm that **Enable password management** is selected, and then click **Settings**.</span></span>  
  
10. <span data-ttu-id="77e00-143">Dans le **paramètres de connexion** boîte de dialogue, spécifiez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="77e00-143">In the **Connection Settings** dialog, specify the following:</span></span>  
  
    -   <span data-ttu-id="77e00-144">Se connecter à : INTSVR1.fabrikam.com</span><span class="sxs-lookup"><span data-stu-id="77e00-144">Connect To: INTSVR1.fabrikam.com</span></span>  
  
    -   <span data-ttu-id="77e00-145">Utilisateur : fabrikam\ssosvcact</span><span class="sxs-lookup"><span data-stu-id="77e00-145">User: fabrikam\ssosvcact</span></span>  
  
    -   <span data-ttu-id="77e00-146">Mot de passe : ssosvcact</span><span class="sxs-lookup"><span data-stu-id="77e00-146">Password: ssosvcact</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="77e00-147">Ce compte doit correspondre à celui du service ENTSSO configuré sur INTSVR1.fabrikam.com.</span><span class="sxs-lookup"><span data-stu-id="77e00-147">This account should match the ENTSSO service account configured on INTSVR1.fabrikam.com.</span></span>  
  
11. <span data-ttu-id="77e00-148">Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.</span><span class="sxs-lookup"><span data-stu-id="77e00-148">Click **OK**, and then click **OK** again.</span></span>  
  
12. <span data-ttu-id="77e00-149">Vous pouvez également désactiver la synchronisation de mot de passe pour MIIS.</span><span class="sxs-lookup"><span data-stu-id="77e00-149">You can also disable password sync for MIIS.</span></span> <span data-ttu-id="77e00-150">Pour ce faire, dans **Identity Manager**, cliquez sur le **outils** menu, cliquez sur **Options**, puis désélectionnez **activer la synchronisation de mot de passe**.</span><span class="sxs-lookup"><span data-stu-id="77e00-150">To do this, in **Identity Manager**, click the **Tools** menu, click **Options**, and then deselect **Enable Password Synchronization**.</span></span>  
  
     <span data-ttu-id="77e00-151">Les restrictions suivantes seront applique :</span><span class="sxs-lookup"><span data-stu-id="77e00-151">The following restrictions will apply:</span></span>  
  
    -   <span data-ttu-id="77e00-152">Pour que la synchronisation de mot de passe fonctionne correctement, le nom principal de service doit être configuré sur le compte du service ENTSSO avec lequel l'agent de gestion ENTSSO communique.</span><span class="sxs-lookup"><span data-stu-id="77e00-152">For Password Sync to function properly, SPN must be configured on the ENTSSO service account that the ENTSSO Management Agent will communicate with.</span></span>  
  
    -   <span data-ttu-id="77e00-153">Les communications entre MIIS et le serveur ENTSSO requièrent Kerberos.</span><span class="sxs-lookup"><span data-stu-id="77e00-153">Communication between MIIS and the ENTSSO server requires Kerberos.</span></span>  
  
13. <span data-ttu-id="77e00-154">Lors de la configuration de l'extension de mot de passe dans la configuration de la connexion MIIS pour l'agent de gestion ENTSSO, le compte spécifié doit correspondre au compte de service du serveur ENTSSO qui reçoit les mots de passe en provenance de MIIS.</span><span class="sxs-lookup"><span data-stu-id="77e00-154">When configuring Password Extension in the MIIS connection configuration for the ENTSSO Management Agent, the account specified must match the service account for the ENTSSO server that will receive passwords from MIIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77e00-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77e00-155">See Also</span></span>  
 [<span data-ttu-id="77e00-156">L’utilisation de l’Agent de gestion ENTSSO</span><span class="sxs-lookup"><span data-stu-id="77e00-156">How to Use the ENTSSO Management Agent</span></span>](../core/how-to-use-the-entsso-management-agent.md)