---
title: Configuration des alertes BAM | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, alerts
- alerts, timeout values
- Notification Services, configuration tips
- alerts, configuring
- managing [BAM definitions], configuring alerts
ms.assetid: 29327466-c8e9-41e8-bc12-f3ac6b5d3096
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46ddba35a603217660df22668d548ca7c40eb5f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-bam-alerts"></a><span data-ttu-id="b864e-102">Configuration des alertes BAM</span><span class="sxs-lookup"><span data-stu-id="b864e-102">Configuring BAM Alerts</span></span>
<span data-ttu-id="b864e-103">Les administrateurs ont la possibilité de modifier certains éléments de l'infrastructure d'alertes BAM.</span><span class="sxs-lookup"><span data-stu-id="b864e-103">Administrators can modify certain elements of the BAM alert framework.</span></span> <span data-ttu-id="b864e-104">Dans cette rubrique, vous trouverez une description des options de configuration auxquelles ils ont accès.</span><span class="sxs-lookup"><span data-stu-id="b864e-104">This topic describes the configuration options available to administrators.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b864e-105">Lorsque vous créez des alertes, sachez que les données temporelles sont stockées dans un format de fuseau horaire local dans les bases de données de type OLAP, schémas en étoile et services de notification.</span><span class="sxs-lookup"><span data-stu-id="b864e-105">When creating alerts you should be aware that time data is stored in a Local Time format on the OLAP, Star Schema, and Notification Services databases.</span></span> <span data-ttu-id="b864e-106">Cela sous-entend également que les trois bases de données respectent le même fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="b864e-106">It is also assumed that all three databases are in the same time zone.</span></span> <span data-ttu-id="b864e-107">Dans la base de données d'importation principale, les informations sont stockées à l'heure UTC et peuvent utiliser des fuseaux horaires identiques ou différents.</span><span class="sxs-lookup"><span data-stu-id="b864e-107">On the Primary Import database, information is stored in the UTC time format and can be in the same or different time zone.</span></span>  
  
## <a name="changing-the-adf-configuration"></a><span data-ttu-id="b864e-108">Modification de la configuration du fichier de définition d'application (ADF)</span><span class="sxs-lookup"><span data-stu-id="b864e-108">Changing the ADF configuration</span></span>  
 <span data-ttu-id="b864e-109">Lors du déploiement d’une vue de l’utilitaire de gestion BAM utilise la valeur CommandTimeout spécifiée dans le fichier bm.exe.config pour renseigner le fichier de définition d’application Notification Services \<EventRule >\\< ActionTimeout\> élément.</span><span class="sxs-lookup"><span data-stu-id="b864e-109">When deploying a view the BAM Management utility uses the CommandTimeout value specified in the bm.exe.config file to populate Notification Services application definition file \<EventRule>\\<ActionTimeout\> element.</span></span>  
  
 <span data-ttu-id="b864e-110">La modification de la valeur du paramètre CommandTimeout dans le fichier bm.exe.config n'entraîne pas de modification pour cette même valeur si, pour les vues déployées, elle a été définie avant la modification.</span><span class="sxs-lookup"><span data-stu-id="b864e-110">Changing the value of CommandTimeout in bm.exe.config does not change the CommandTimeout value for views deployed prior to the change.</span></span>  
  
 <span data-ttu-id="b864e-111">La procédure suivante utilise le script ProcessBamNSFiles.vbs pour obtenir la configuration et le fichier de définition d'application des services de notification.</span><span class="sxs-lookup"><span data-stu-id="b864e-111">The procedure below uses the ProcessBamNSFiles.vbs to obtain the configuration and the Notification Services application definition file.</span></span> <span data-ttu-id="b864e-112">Pour plus d’informations sur le script, consultez [Script de ligne de commande BAM pour les fichiers de Configuration de Services de Notification](../core/bam-command-line-script-for-notification-services-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="b864e-112">For more information on the script, see [BAM Command-Line Script for Notification Services Configuration Files](../core/bam-command-line-script-for-notification-services-configuration-files.md).</span></span>  
  
 <span data-ttu-id="b864e-113">Méthode à suivre pour modifier l'élément ActionTimeout dans les services de notification pour les vues déjà déployées :</span><span class="sxs-lookup"><span data-stu-id="b864e-113">How to change the ActionTimeout for NS for already deployed views:</span></span>  
  
#### <a name="to-change-the-command-timeout-value"></a><span data-ttu-id="b864e-114">Pour changer la valeur du délai d'attente pour une commande</span><span class="sxs-lookup"><span data-stu-id="b864e-114">To change the command timeout value</span></span>  
  
1.  <span data-ttu-id="b864e-115">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b864e-115">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="b864e-116">Accédez au dossier des suivis en tapant à l’invite de commandes **cd « C:\Program Files\Microsoft BizTalk Server \<version > \Tracking »** ou **cd « C:\Program Files (x86) \Microsoft BizTalk Server \<version > \Tracking «** sur un ordinateur 64 bits.</span><span class="sxs-lookup"><span data-stu-id="b864e-116">Navigate to the tracking folder by typing at the command prompt **cd “C:\Program Files\Microsoft BizTalk Server \<version>\Tracking”** or **cd “C:\Program Files (x86)\Microsoft BizTalk Server \<version>\Tracking”** on a 64 bit computer.</span></span> <span data-ttu-id="b864e-117">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="b864e-117">Press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="b864e-118">Récupérez le fichier ADF.</span><span class="sxs-lookup"><span data-stu-id="b864e-118">Retrieve the ADF file.</span></span> <span data-ttu-id="b864e-119">Type **cscript ProcessBamNSFiles.vbs-Get \<ConfigFilePath > \<Cheminfichieradf > \< Serveurpid > \< base de données PID >**.</span><span class="sxs-lookup"><span data-stu-id="b864e-119">Type **cscript ProcessBamNSFiles.vbs -Get \<ConfigFilePath> \<ADFFilePath> \< PID Server> \< PID database >**.</span></span> <span data-ttu-id="b864e-120">Remplacez les éléments CheminFichierConfig, CheminFichierADF, ServeurPID et BaseDonnéesPID par les valeurs appropriées à votre installation.</span><span class="sxs-lookup"><span data-stu-id="b864e-120">Replacing the ConfigFilePath, ADFFilePath, PID Server, and PID database with the appropriate values for your installation.</span></span>  
  
4.  <span data-ttu-id="b864e-121">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="b864e-121">Press **ENTER**.</span></span>  
  
5.  <span data-ttu-id="b864e-122">Ouvrez le fichier ADF dans un éditeur et recherchez \<ActionTimeout > Veuillez noter que cette valeur est une durée XML et mettre à jour avec la valeur souhaitée.</span><span class="sxs-lookup"><span data-stu-id="b864e-122">Open the ADF file in an editor and search for \<ActionTimeout>, update with desired value & please note that this value is an XML duration.</span></span>  
  
6.  <span data-ttu-id="b864e-123">Enregistrez le fichier ADF.</span><span class="sxs-lookup"><span data-stu-id="b864e-123">Save the ADF file.</span></span> <span data-ttu-id="b864e-124">Type **cscript ProcessBamNSFiles.vbs-mise à jour \<ConfigFilePath > \<Cheminfichieradf > \< Serveurpid > \< base de données PID >**.</span><span class="sxs-lookup"><span data-stu-id="b864e-124">Type **cscript ProcessBamNSFiles.vbs -Update \<ConfigFilePath> \<ADFFilePath> \< PID Server> \< PID database >**.</span></span>  
  
7.  <span data-ttu-id="b864e-125">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="b864e-125">Press **ENTER**.</span></span>  
  
### <a name="notification-service-configuration-tips"></a><span data-ttu-id="b864e-126">Conseils pour la configuration des services de notification</span><span class="sxs-lookup"><span data-stu-id="b864e-126">Notification Service configuration tips</span></span>  
 <span data-ttu-id="b864e-127">Si vous configurez les alertes BAM de sorte que les bases de données d'alertes soient placées sur un ordinateur distant exécutant [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], les composants de base de données des services de notification doivent être installés sur l'instance du serveur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b864e-127">If you configure BAM Alerts in such a way as to place the Alerts databases on a remote computer running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], then the Notification Services Database Components must be installed on the SQL Server instance.</span></span> <span data-ttu-id="b864e-128">Si ces composants ne sont pas présents dans cette instance de serveur SQL, la configuration des alertes BAM échoue et une erreur est générée indiquant que des autorisations n'ont pas pu être accordées aux procédures stockées étendues des services de notification.</span><span class="sxs-lookup"><span data-stu-id="b864e-128">If these components are not present on the SQL instance, then configuration of BAM Alerts will fail with an error indicating that permissions could not be granted to the Notification Services Extended Stored Procedures.</span></span> <span data-ttu-id="b864e-129">Pour plus d’informations sur l’installation du composant de Notification Services, consultez [http://go.microsoft.com/fwlink/?LinkId=61999](http://go.microsoft.com/fwlink/?LinkId=61999).</span><span class="sxs-lookup"><span data-stu-id="b864e-129">For more information on installing the Notification Services component, see [http://go.microsoft.com/fwlink/?LinkId=61999](http://go.microsoft.com/fwlink/?LinkId=61999).</span></span>  
  
 <span data-ttu-id="b864e-130">L'analyse BAM vous permet de modifier le compte qu'elle utilise pour accéder aux services de notification.</span><span class="sxs-lookup"><span data-stu-id="b864e-130">BAM allows you to change the account that BAM uses to access the Notification Services.</span></span> <span data-ttu-id="b864e-131">Si vous modifiez ce compte sans exécuter l'utilitaire NSControl, vous recevez un message d'erreur vous informant de l'utilisation obligatoire de cet utilitaire pour toute modification du compte.</span><span class="sxs-lookup"><span data-stu-id="b864e-131">If you change this account in any way other than running NSControl, you will receive an error informing you to use the NSControl to change the account.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b864e-132">Vous ne pouvez pas utiliser les comptes LocalSystem ou SYSTEM pour installer et configurer les services de notification.</span><span class="sxs-lookup"><span data-stu-id="b864e-132">You cannot use the LocalSystem or SYSTEM accounts for installing and configuring Notification Services.</span></span> <span data-ttu-id="b864e-133">Ce sont des comptes spéciaux auxquels vous ne pouvez pas vous connecter et que vous ne pouvez pas utiliser pour accorder des autorisations sur les fichiers et SQL Server à l'utilisateur d'alertes BAM.</span><span class="sxs-lookup"><span data-stu-id="b864e-133">These are special accounts that you cannot log on to and that you cannot use to grant file and SQL Server permissions to the BAM alerts user.</span></span>  
>   
>  <span data-ttu-id="b864e-134">Pour installer et configurer les services de notification, créez un nouveau compte d'utilisateur sur l'ordinateur local, accordez-lui toutes les autorisations requises et utilisez-le ensuite pour configurer les services de notification.</span><span class="sxs-lookup"><span data-stu-id="b864e-134">To install and configure Notification Services, create a new user account on the local computer, grant it all the requisite permissions, and then use it to configure Notification Services.</span></span>  
  
##### <a name="to-change-ns-user-account-for-bam"></a><span data-ttu-id="b864e-135">Modification d'un compte d'utilisateur des services de notification pour l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="b864e-135">To change NS user account for BAM</span></span>  
  
1.  <span data-ttu-id="b864e-136">Utilisez l'utilitaire NSControl pour mettre à jour le compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b864e-136">Use NSControl to update the user account.</span></span>  
  
2.  <span data-ttu-id="b864e-137">Accordez à l'utilisateur l'accès en lecture, en écriture et en modification à l'emplacement partagé du fichier Alertes BAM.</span><span class="sxs-lookup"><span data-stu-id="b864e-137">Grant the NS user read, write, and change permissions to the BAM Alerts File Location share.</span></span>  
  
3.  <span data-ttu-id="b864e-138">Ajoutez l'utilisateur des services de notification en tant que membre du rôle NSRunService dans l'instance BAMAlerts ainsi que dans les bases de données de l'application.</span><span class="sxs-lookup"><span data-stu-id="b864e-138">Add the NS user as a member of NSRunService role in both the BAMAlerts instance and application databases.</span></span>  
  
4.  <span data-ttu-id="b864e-139">Accorder les droits d’utilisateur sur l’ordinateur local à l’aide de la documentation relative à [http://go.microsoft.com/fwlink/?LinkId=62005](http://go.microsoft.com/fwlink/?LinkId=62005).</span><span class="sxs-lookup"><span data-stu-id="b864e-139">Grant the NS User rights on the local machine using the documentation at [http://go.microsoft.com/fwlink/?LinkId=62005](http://go.microsoft.com/fwlink/?LinkId=62005).</span></span>  
  
5.  <span data-ttu-id="b864e-140">Accorder les droits NS vers les serveurs de noms de base de données en fonction de [http://go.microsoft.com/fwlink/?LinkId=62008](http://go.microsoft.com/fwlink/?LinkId=62008).</span><span class="sxs-lookup"><span data-stu-id="b864e-140">Grant the NS rights to the NS database according to [http://go.microsoft.com/fwlink/?LinkId=62008](http://go.microsoft.com/fwlink/?LinkId=62008).</span></span>  
  
6.  <span data-ttu-id="b864e-141">Accordez à l'utilisateur des services de notification des droits de connexion au serveur SQL ainsi que des droits d'accès à la base de données d'importation principale.</span><span class="sxs-lookup"><span data-stu-id="b864e-141">Grant the NS user login rights to SQL server and database access to the Primary Import database.</span></span>  
  
7.  <span data-ttu-id="b864e-142">Ajoutez l'utilisateur de ces services au rôle SQL BAM_ManagmentNSReader.</span><span class="sxs-lookup"><span data-stu-id="b864e-142">Add the NS user to the BAM_ManagmentNSReader SQL role.</span></span>  
  
8.  <span data-ttu-id="b864e-143">Ajoutez l'utilisateur des services de notification au rôle des alertes BAM dans base de données BamAnalysis.</span><span class="sxs-lookup"><span data-stu-id="b864e-143">Add the NS user to the "BAM Alerts" role in BamAnalysis database.</span></span>  
  
 <span data-ttu-id="b864e-144">Si vous modifiez l'emplacement de dépôt du fichier pour les alertes envoyées sous forme de fichier,</span><span class="sxs-lookup"><span data-stu-id="b864e-144">If you modify the file drop location for alerts delivered by file.</span></span> <span data-ttu-id="b864e-145">vous devez redémarrer les services de notification SQL.</span><span class="sxs-lookup"><span data-stu-id="b864e-145">You must restart the SQL Notifications Services.</span></span>  
  
 <span data-ttu-id="b864e-146">Si ces services ne sont pas redémarrés, les alertes continueront à être envoyées à l'emplacement d'origine destiné au dépôt du fichier.</span><span class="sxs-lookup"><span data-stu-id="b864e-146">If the NS service is not restarted, alerts will continue being delivered to the original file drop location.</span></span>  
  
 <span data-ttu-id="b864e-147">L'emplacement de dépôt du fichier se modifie en changeant la ligne suivante du fichier de configuration BAM et en utilisant la commande update-config de l'utilitaire de gestion de l'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="b864e-147">The file drop location is changed by modifying the following line of the BAM configuration file and using the BAM manangement utility update-config command.</span></span>  
  
 <span data-ttu-id="b864e-148">\<Nom de la propriété = « FileDropUNC » >\\\\< nom de l’ordinateur\>\alerts\<cette propriété ></span><span class="sxs-lookup"><span data-stu-id="b864e-148">\<Property Name="FileDropUNC">\\\\<computer name\>\alerts\</Property></span></span>  
  
 <span data-ttu-id="b864e-149">Pour plus d’informations sur l’utilitaire de gestion de l’analyse BAM, consultez [utilitaire de gestion BAM](../core/bam-management-utility.md).</span><span class="sxs-lookup"><span data-stu-id="b864e-149">For more information on the BAM Management utility, see [BAM Management Utility](../core/bam-management-utility.md).</span></span>