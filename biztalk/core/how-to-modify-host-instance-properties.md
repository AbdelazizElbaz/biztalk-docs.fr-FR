---
title: "Modifier les propriétés de l’Instance hôte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a35ca0c8-89b3-483a-b2fc-c8f43a8864d1
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 859170362ce804db6eff5b0e928998f008d0c2c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="update-host-instance-properties"></a><span data-ttu-id="8a5ad-102">Mettre à jour les propriétés de l’Instance hôte</span><span class="sxs-lookup"><span data-stu-id="8a5ad-102">Update Host Instance Properties</span></span>

## <a name="overview"></a><span data-ttu-id="8a5ad-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="8a5ad-103">Overview</span></span>
<span data-ttu-id="8a5ad-104">Vous pouvez utiliser la console Administration de BizTalk Server ou Windows Management Instrumentation (WMI) pour modifier des instances d'hôte.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-104">You can use the BizTalk Server Administration Console or Windows Management Instrumentation (WMI) to modify host instances.</span></span> <span data-ttu-id="8a5ad-105">Vous pouvez modifier le compte de service qui exécute une instance d'hôte.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-105">You can modify the service account running a host instance.</span></span> <span data-ttu-id="8a5ad-106">Vous pouvez également désactiver une instance d'hôte.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-106">You can also disable a host instance.</span></span> <span data-ttu-id="8a5ad-107">Par exemple, si vous voulez conserver les paramètres d'une instance d'hôte et que vous ne voulez pas que cette instance démarre, désactivez-la.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-107">For example, if you want to preserve the settings for a host instance and you do not want it to start, you can disable it.</span></span> <span data-ttu-id="8a5ad-108">Pour plus d’informations sur les instances d’hôte, consultez [Instances d’hôte](../core/host-instances.md).</span><span class="sxs-lookup"><span data-stu-id="8a5ad-108">For more information about host instances, see [Host Instances](../core/host-instances.md).</span></span>  
  
 <span data-ttu-id="8a5ad-109">Vous ne pouvez pas utiliser les mêmes comptes de service pour les instances d'hôtes approuvés et celles d'hôtes non approuvés.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-109">Host instances of trusted hosts and host instances of non-trusted hosts cannot use the same service accounts.</span></span> <span data-ttu-id="8a5ad-110">Pour modifier le paramètre d'approbation d'une instance d'hôte lorsque cette instance utilise un compte de service également associé à d'autres instances d'hôte, effectuez l'une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8a5ad-110">If you want to change the trust setting of a host instance and the host instance uses a service account that other host instances use, you can do one of the following:</span></span>  
  
-   <span data-ttu-id="8a5ad-111">Remplacez le compte de service de l'instance d'hôte dont vous voulez modifier les paramètres d'approbation par un nouveau compte de service.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-111">You can change the service account of the host instance for which you want to change the trust settings to a new service account.</span></span>  
  
-   <span data-ttu-id="8a5ad-112">Remplacez le compte de service de l'instance d'hôte par un compte de service existant, utilisé par d'autres instances d'hôte dont le paramètre d'approbation est identique.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-112">You can change the service account of the host instance to an existing service account that other host instances with the same trust setting use.</span></span>  
  
-   <span data-ttu-id="8a5ad-113">Supprimez l'instance d'hôte et recréez-la avec un paramètre d'approbation et un compte de service différents.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-113">You can delete the host instance, and re-create it with a different trust setting and service account.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="8a5ad-114">Vous devez modifier les informations d'identification d'une instance d'hôte en mettant à jour les propriétés de cette instance.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-114">You must change the credentials for a host instance by updating the properties of the host instance.</span></span> <span data-ttu-id="8a5ad-115">Si vous modifiez les informations d'identification du service correspondant, le compte de service que vous spécifiez pour l'instance de l'hôte doit être membre du groupe sur l'hôte.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-115">If you change the credentials of the corresponding service, the service account you specify for the host instance must be a member of the group on the host.</span></span> <span data-ttu-id="8a5ad-116">N'utilisez pas le composant logiciel enfichable Services ni la console Gestion de l'ordinateur pour modifier les informations d'identification de l'instance d'hôte, cette dernière risquerait de ne pas fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-116">Do not use the Services snap-in or the Computer Management console to change the credentials of host instance, otherwise the host instance may not function properly.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="8a5ad-117">Si vous modifiez les informations d'identification d'une instance d'hôte, vous devez également modifier les informations d'identification SQL Server correspondantes.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-117">If you change the credentials of a host instance, you must also change the corresponding SQL Server credentials.</span></span> <span data-ttu-id="8a5ad-118">Sinon, l'instance d'hôte ne fonctionnera pas correctement.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-118">If you do not update the SQL Server credentials, the host instance will not function properly.</span></span>  
  
 <span data-ttu-id="8a5ad-119">Pour plus d’informations sur l’utilisation de WMI pour modifier une instance d’hôte, consultez **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="8a5ad-119">For information about using WMI to modify a host instance, see **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="8a5ad-120">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="8a5ad-120">Prerequisites</span></span>  
 <span data-ttu-id="8a5ad-121">Pour exécuter cette procédure, vous devez avoir ouvert une session en tant que membre du groupe des administrateurs BizTalk Server ou du groupe des administrateurs Windows.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-121">To perform this procedure, you must be logged on as a member of the Administrators group and the BizTalk Server Administrators group.</span></span>  
  
 <span data-ttu-id="8a5ad-122">Vous devez également être un membre du rôle de la base de données SQL Server db_securityadmin et du rôle SQL Server securityadmin sur les serveurs sur lesquels se trouvent les bases de données suivantes :</span><span class="sxs-lookup"><span data-stu-id="8a5ad-122">In addition, you must also be a member of the db_securityadmin SQL Server Database role and the securityadmin SQL Server Role on the server(s) where the following databases are:</span></span>  
  
-   <span data-ttu-id="8a5ad-123">importation principale BAM (BAMPrimaryImport).</span><span class="sxs-lookup"><span data-stu-id="8a5ad-123">BAM Primary Import (BAMPrimaryImport)</span></span>  
  
-   <span data-ttu-id="8a5ad-124">gestion BizTalk (BizTalkMgmtDb) ;</span><span class="sxs-lookup"><span data-stu-id="8a5ad-124">BizTalk Management (BizTalkMgmtDb)</span></span>  
  
-   <span data-ttu-id="8a5ad-125">MessageBox BizTalk (BizTalkMsgBoxDb) (tout) ;</span><span class="sxs-lookup"><span data-stu-id="8a5ad-125">BizTalk MessageBox (BizTalkMsgBoxDb) (all)</span></span>  
  
-   <span data-ttu-id="8a5ad-126">suivis BizTalk (BizTalkDTADb) ;</span><span class="sxs-lookup"><span data-stu-id="8a5ad-126">BizTalk Tracking (BizTalk DTADb)</span></span>  
  
-   <span data-ttu-id="8a5ad-127">moteur des règles (BizTalkRuleEngineDb) ;</span><span class="sxs-lookup"><span data-stu-id="8a5ad-127">Rule Engine (BizTalkRuleEngineDb)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="8a5ad-128">Nous vous recommandons de mettre à jour les informations de compte des instances d'hôte à l'aide de la console Administration de BizTalk Server ou d'un script WMI (Windows Management Instrumentation).</span><span class="sxs-lookup"><span data-stu-id="8a5ad-128">We recommend that you update account information for host instances by using the BizTalk Server Administration Console or a Windows Management Instrumentation (WMI) script.</span></span> <span data-ttu-id="8a5ad-129">De cette manière, BizTalk Server peut mettre à jour les informations de compte dans les bases de données BizTalk Server et peut synchroniser la configuration de sécurité entre les bases de données et l'instance d'hôte.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-129">This ensures that BizTalk Server can update the account information in the BizTalk Server databases and keep the security configuration between the databases and host instance synchronized.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="8a5ad-130">Étapes</span><span class="sxs-lookup"><span data-stu-id="8a5ad-130">Steps</span></span>
  
1.  <span data-ttu-id="8a5ad-131">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-131">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="8a5ad-132">Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, cliquez sur **paramètres de plateforme**, puis cliquez sur **Instances d’hôte**.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-132">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, click **Platform Settings**, and then click **Host Instances**.</span></span>  
  
3.  <span data-ttu-id="8a5ad-133">Dans le volet de détails, cliquez sur l’instance d’hôte que vous souhaitez modifier, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-133">In the details pane, right-click the host instance you want to modify, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="8a5ad-134">Dans le **propriétés de l’Instance hôte** boîte de dialogue, cliquez sur **configurer** pour modifier les informations de compte de service.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-134">In the **Host Instance Properties** dialog box, click **Configure** to modify the service account information.</span></span>  
  
5.  <span data-ttu-id="8a5ad-135">Dans le **informations d’identification d’ouverture de session** boîte de dialogue, entrez le nom de compte et le mot de passe du compte sous lequel l’instance d’hôte s’exécuter, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-135">In the **Logon Credentials** dialog box, enter the account name and password of the account under which the host instance will run, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="8a5ad-136">Dans le **propriétés de l’Instance hôte** boîte de dialogue, procédez comme suit, puis cliquez sur **OK**:</span><span class="sxs-lookup"><span data-stu-id="8a5ad-136">In the **Host Instance Properties** dialog box, do the following, and then click **OK**:</span></span>  
  
    |<span data-ttu-id="8a5ad-137">Utiliser</span><span class="sxs-lookup"><span data-stu-id="8a5ad-137">Use this</span></span>|<span data-ttu-id="8a5ad-138">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="8a5ad-138">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="8a5ad-139">**Nom d’hôte**</span><span class="sxs-lookup"><span data-stu-id="8a5ad-139">**Host name**</span></span>|<span data-ttu-id="8a5ad-140">Afficher le nom de l'hôte associé au serveur sélectionné.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-140">Displays the name of the host associated with the selected server.</span></span>|  
    |<span data-ttu-id="8a5ad-141">**Server**</span><span class="sxs-lookup"><span data-stu-id="8a5ad-141">**Server**</span></span>|<span data-ttu-id="8a5ad-142">Afficher le serveur associé à l'hôte sélectionné.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-142">Displays the server associated with the selected host.</span></span>|  
    |<span data-ttu-id="8a5ad-143">**Ouverture de session**</span><span class="sxs-lookup"><span data-stu-id="8a5ad-143">**Logon**</span></span>|<span data-ttu-id="8a5ad-144">Afficher le nom de compte du nouveau service sous lequel l'instance de l'hôte doit s'exécuter.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-144">Displays the account name of the new service account under which the host instance will run.</span></span>|  
    |<span data-ttu-id="8a5ad-145">**Configurer**</span><span class="sxs-lookup"><span data-stu-id="8a5ad-145">**Configure**</span></span>|<span data-ttu-id="8a5ad-146">Cliquez pour afficher les **informations d’identification d’ouverture de session** boîte de dialogue, dans lequel vous pouvez entrer le nom de compte et le mot de passe du compte sous lequel s’exécute l’instance d’hôte.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-146">Click to display the **Logon Credentials** dialog box, where you can enter the account name and password of the account under which the host instance will run.</span></span>|  
    |<span data-ttu-id="8a5ad-147">**Désactiver l’instance de l’hôte de démarrer**</span><span class="sxs-lookup"><span data-stu-id="8a5ad-147">**Disable host instance from starting**</span></span>|<span data-ttu-id="8a5ad-148">Activer cette case à cocher pour faire passer l'état de l'hôte sélectionné de « Activé » à « Désactivé ».</span><span class="sxs-lookup"><span data-stu-id="8a5ad-148">Select this check box to change the status of the selected host from enabled to disabled.</span></span> <span data-ttu-id="8a5ad-149">La désactivation d'une instance de l'hôte est utile lorsque vous ne souhaitez pas que l'instance démarre, mais que vous voulez tout de même conserver sa configuration.</span><span class="sxs-lookup"><span data-stu-id="8a5ad-149">Disabling a host instance is useful if you do not want the host instance to start, but you do want to preserve its settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8a5ad-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a5ad-150">See Also</span></span>  
 <span data-ttu-id="8a5ad-151">[La gestion des hôtes BizTalk et les Instances d’hôte](../core/managing-biztalk-hosts-and-host-instances.md) </span><span class="sxs-lookup"><span data-stu-id="8a5ad-151">[Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md) </span></span>  
 <span data-ttu-id="8a5ad-152">[Ajouter une Instance d’hôte](../core/how-to-add-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="8a5ad-152">[Add a Host Instance](../core/how-to-add-a-host-instance.md) </span></span>  
 <span data-ttu-id="8a5ad-153">[Démarrer une Instance d’hôte](../core/how-to-start-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="8a5ad-153">[Start a Host Instance](../core/how-to-start-a-host-instance.md) </span></span>  
 <span data-ttu-id="8a5ad-154">[Arrêter une Instance d’hôte](../core/how-to-stop-a-host-instance.md) </span><span class="sxs-lookup"><span data-stu-id="8a5ad-154">[Stop a Host Instance](../core/how-to-stop-a-host-instance.md) </span></span>  
 [<span data-ttu-id="8a5ad-155">Supprimer une Instance d’hôte</span><span class="sxs-lookup"><span data-stu-id="8a5ad-155">Delete a Host Instance</span></span>](../core/how-to-delete-a-host-instance.md)