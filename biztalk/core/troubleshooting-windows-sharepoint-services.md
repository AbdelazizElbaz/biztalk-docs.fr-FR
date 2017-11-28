---
title: "Dépannage de Windows SharePoint Services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9acf9a0d-2c92-4227-80f8-b2d0cca0c232
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51243216f2adb73454477252c7b54358df229610
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-windows-sharepoint-services"></a><span data-ttu-id="ccb6c-102">Dépannage de Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="ccb6c-102">Troubleshooting Windows SharePoint Services</span></span>
<span data-ttu-id="ccb6c-103">Microsoft [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] est utilisé par l'adaptateur Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="ccb6c-103">Microsoft [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] is used by the Windows SharePoint Services adapter.</span></span> <span data-ttu-id="ccb6c-104">Cette rubrique décrit certains des problèmes rencontrés avec Windows SharePoint Services et leurs résolutions possibles.</span><span class="sxs-lookup"><span data-stu-id="ccb6c-104">This topic describes some known issues that may be encountered with Windows SharePoint Services and possible resolutions to these issues.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="ccb6c-105">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="ccb6c-105">Known Issues</span></span>  
  
#### <a name="login-failed-for-user-nt-authoritynetwork-service-error-occurs-when-attempting-to-create-content-database"></a><span data-ttu-id="ccb6c-106">L'erreur Échec de la connexion pour l'utilisateur 'NT AUTHORITY\NETWORK SERVICE' se produit lors d'une tentative de création de la base de données de contenu</span><span class="sxs-lookup"><span data-stu-id="ccb6c-106">Login failed for user 'NT AUTHORITY\NETWORK SERVICE' error occurs when attempting to create content database</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="ccb6c-107">Problème</span><span class="sxs-lookup"><span data-stu-id="ccb6c-107">Problem</span></span>  
 <span data-ttu-id="ccb6c-108">Lorsque vous tentez de créer une base de données de contenu à l'aide du site Web Administration centrale de SharePoint, une erreur similaire à celle indiquée ci-après s'affiche :</span><span class="sxs-lookup"><span data-stu-id="ccb6c-108">When you attempt to create a content database using the SharePoint Central Administration Web site, an error similar to the following is displayed:</span></span>  
  
 <span data-ttu-id="ccb6c-109">Échec de la connexion pour l'utilisateur 'NT AUTHORITY\NETWORK SERVICE'</span><span class="sxs-lookup"><span data-stu-id="ccb6c-109">Login failed for user 'NT AUTHORITY\NETWORK SERVICE'</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="ccb6c-110">Cause</span><span class="sxs-lookup"><span data-stu-id="ccb6c-110">Cause</span></span>  
 <span data-ttu-id="ccb6c-111">Ce problème se produit lorsque le propriétaire de la base de données à laquelle vous vous connectez est différent de l'identité de pool d'applications sous laquelle Windows SharePoint Services s'exécute.</span><span class="sxs-lookup"><span data-stu-id="ccb6c-111">This issue occurs when the database owner of the database that you are connecting to is different from the application pool identity that Windows SharePoint Services is running under.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="ccb6c-112">Résolution</span><span class="sxs-lookup"><span data-stu-id="ccb6c-112">Resolution</span></span>  
 <span data-ttu-id="ccb6c-113">Pour résoudre ce problème, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ccb6c-113">To resolve this issue, do one of the following:</span></span>  
  
-   <span data-ttu-id="ccb6c-114">Octroyez au compte SERVICE RÉSEAU les autorisations de création de base de données dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ccb6c-114">Grant the NETWORK SERVICE account "Database Creation" rights in SQL Server.</span></span>  
  
-   <span data-ttu-id="ccb6c-115">Modifiez le compte d'identité du pool d'applications en un compte doté des autorisations de création de base de données dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ccb6c-115">Change the application pool identity account to an account that has "Database Creation" rights in SQL Server.</span></span>  
  
#### <a name="service-unavailable-error-occurs-when-accessing-the-sharepoint-central-administration-web-site"></a><span data-ttu-id="ccb6c-116">L'erreur « Service non disponible » se produit lors de l'accès au site Web Administration centrale de SharePoint</span><span class="sxs-lookup"><span data-stu-id="ccb6c-116">"Service Unavailable" error occurs when accessing the SharePoint Central Administration Web site</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="ccb6c-117">Problème</span><span class="sxs-lookup"><span data-stu-id="ccb6c-117">Problem</span></span>  
 <span data-ttu-id="ccb6c-118">Lorsque vous tentez d'ouvrir le site Web Administration centrale de SharePoint, une erreur similaire à celle indiquée ci-après s'affiche :</span><span class="sxs-lookup"><span data-stu-id="ccb6c-118">When you attempt to open the SharePoint Central Administration Web site, an error similar to the following is displayed:</span></span>  
  
 <span data-ttu-id="ccb6c-119">Service non disponible</span><span class="sxs-lookup"><span data-stu-id="ccb6c-119">Service Unavailable</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="ccb6c-120">Cause</span><span class="sxs-lookup"><span data-stu-id="ccb6c-120">Cause</span></span>  
 <span data-ttu-id="ccb6c-121">Cette erreur se produit généralement lorsque le pool d'applications (IIS 6.0 ou IIS 7.0) ou l'application COM+ hôte (IIS 5.x) du site Web Administration centrale de SharePoint est arrêté.</span><span class="sxs-lookup"><span data-stu-id="ccb6c-121">The most common cause for this error is that the application pool (IIS 6.0 or IIS 7.0) or hosting COM+ application (IIS 5.x) for the SharePoint Central Administration Web site is stopped.</span></span> <span data-ttu-id="ccb6c-122">Cela survient généralement lorsque le pool d'applications ou l'application COM+ est configurée avec une identité pour laquelle le nom d'utilisateur et/ou le mot de passe spécifiés ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="ccb6c-122">This commonly occurs if the application pool or COM+ application is configured with an identity for which the specified user name and/or password is invalid.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="ccb6c-123">Résolution</span><span class="sxs-lookup"><span data-stu-id="ccb6c-123">Resolution</span></span>  
 <span data-ttu-id="ccb6c-124">Suivez les étapes décrites dans la section « Paramètre IIS Application identité du processus hôte » de la rubrique [des recommandations pour la résolution des problèmes d’autorisation IIS](../core/guidelines-for-resolving-iis-permissions-problems.md) pour définir l’identité du processus hôte approprié.</span><span class="sxs-lookup"><span data-stu-id="ccb6c-124">Follow the steps in the "Setting IIS Application Host Process Identity" section of the topic [Guidelines for Resolving IIS Permissions Problems](../core/guidelines-for-resolving-iis-permissions-problems.md) to set the appropriate host process identity.</span></span>  
  
#### <a name="cannot-connect-to-the-configuration-database-error-occurs-when-attempting-to-extend-and-create-a-content-database"></a><span data-ttu-id="ccb6c-125">L'erreur « Impossible de se connecter à la base de données de configuration » se produit lors d'une tentative d'extension et de création d'une base de données de contenu</span><span class="sxs-lookup"><span data-stu-id="ccb6c-125">"Cannot connect to the configuration database" error occurs when attempting to extend and create a content database</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="ccb6c-126">Problème</span><span class="sxs-lookup"><span data-stu-id="ccb6c-126">Problem</span></span>  
 <span data-ttu-id="ccb6c-127">Lorsque vous tentez d'étendre et de créer une base de données de contenu à l'aide du site Web Administration centrale de SharePoint, une erreur similaire à celle indiquée ci-après s'affiche :</span><span class="sxs-lookup"><span data-stu-id="ccb6c-127">When you attempt to extend and create a content database using the SharePoint Central Administration Web site, an error similar to the following is displayed:</span></span>  
  
 <span data-ttu-id="ccb6c-128">Impossible de se connecter à la base de données de configuration</span><span class="sxs-lookup"><span data-stu-id="ccb6c-128">Cannot connect to the configuration database</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="ccb6c-129">Cause</span><span class="sxs-lookup"><span data-stu-id="ccb6c-129">Cause</span></span>  
 <span data-ttu-id="ccb6c-130">Ce problème se produit lorsque le compte utilisé par le pool d'applications qui exécute le site Web Administration centrale de SharePoint ne dispose pas des autorisations requises pour la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ccb6c-130">This issue occurs when the account that is used by the application pool that is running the SharePoint Central Administration Web site does not have the required permissions to the SQL Server database.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="ccb6c-131">Résolution</span><span class="sxs-lookup"><span data-stu-id="ccb6c-131">Resolution</span></span>  
 <span data-ttu-id="ccb6c-132">Pour résoudre ce problème, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ccb6c-132">To resolve this issue, do one of the following:</span></span>  
  
-   <span data-ttu-id="ccb6c-133">Octroyez au compte utilisé par le pool d'applications du site Web Administration centrale de SharePoint les autorisations de création de base de données dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ccb6c-133">Grant the account that is used by the application pool for the SharePoint Central Administration Web site "Database Creation" rights in SQL Server.</span></span>  
  
-   <span data-ttu-id="ccb6c-134">Modifiez le compte d'identité du pool d'applications en un compte doté des autorisations de création de base de données dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ccb6c-134">Change the application pool identity account to an account that has "Database Creation" rights in SQL Server.</span></span>  
  
#### <a name="the-sharepoint-timer-service-service-failed-to-start-error-is-generated-in-the-application-log-after-rebooting-server"></a><span data-ttu-id="ccb6c-135">Une erreur est générée dans le journal de l'application après le redémarrage du serveur indiquant que le démarrage du service du minuteur SharePoint a échoué</span><span class="sxs-lookup"><span data-stu-id="ccb6c-135">"The SharePoint Timer Service service failed to start" error is generated in the Application log after rebooting server</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="ccb6c-136">Problème</span><span class="sxs-lookup"><span data-stu-id="ccb6c-136">Problem</span></span>  
 <span data-ttu-id="ccb6c-137">Après le redémarrage du serveur, une erreur s'affiche dans les journaux d'événements indiquant que</span><span class="sxs-lookup"><span data-stu-id="ccb6c-137">After restarting the server, you see the following error in the event logs:</span></span>  
  
 <span data-ttu-id="ccb6c-138">le démarrage du service du minuteur SharePoint a échoué</span><span class="sxs-lookup"><span data-stu-id="ccb6c-138">The SharePoint Timer Service service failed to start</span></span>  
  
 <span data-ttu-id="ccb6c-139">L'erreur suivante peut également s'afficher lors de l'ouverture du site Web Administration centrale de SharePoint indiquant que</span><span class="sxs-lookup"><span data-stu-id="ccb6c-139">You may also see the following error when you open the SharePoint Central Administration site:</span></span>  
  
 <span data-ttu-id="ccb6c-140">la connexion à la base de données de configuration WSS STS_Config n'a pas pu être établie.</span><span class="sxs-lookup"><span data-stu-id="ccb6c-140">Unable to connect to the WSS configuration database STS_Config</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="ccb6c-141">Cause</span><span class="sxs-lookup"><span data-stu-id="ccb6c-141">Cause</span></span>  
 <span data-ttu-id="ccb6c-142">Cette erreur se produit lorsque le service du minuteur SharePoint ne parvient pas à contacter la base de données [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] après le redémarrage.</span><span class="sxs-lookup"><span data-stu-id="ccb6c-142">This error occurs when the SharePoint Timer service fails to contact the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] database after rebooting.</span></span> <span data-ttu-id="ccb6c-143">Ce service permet d'envoyer des notifications et d'exécuter des tâches planifiées pour [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ccb6c-143">The SharePoint Timer service is used to send notifications and perform scheduled tasks for [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].</span></span> <span data-ttu-id="ccb6c-144">Cette erreur se produit généralement lorsque le compte utilisé pour exécuter le service est configuré avec une identité pour laquelle le nom d'utilisateur et/ou le mot de passe ne sont plus valides.</span><span class="sxs-lookup"><span data-stu-id="ccb6c-144">The most common reason that the SharePoint Timer service fails to start is that the account used to run the service is configured with an identity for which the user name and/or password are no longer valid.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="ccb6c-145">Résolution</span><span class="sxs-lookup"><span data-stu-id="ccb6c-145">Resolution</span></span>  
 <span data-ttu-id="ccb6c-146">Assurez-vous que le nom d'utilisateur et le mot de passe spécifiés pour le compte de connexion du service du minuteur SharePoint sont corrects et que le service a été démarré.</span><span class="sxs-lookup"><span data-stu-id="ccb6c-146">Ensure that the user name and password specified for the SharePoint Timer service logon account are correct and that the service has been started.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb6c-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccb6c-147">See Also</span></span>  
 <span data-ttu-id="ccb6c-148">[Comment configurer un serveur virtuel Windows SharePoint Services](http://support.microsoft.com/kb/832769) </span><span class="sxs-lookup"><span data-stu-id="ccb6c-148">[How to configure a Windows SharePoint Services virtual server](http://support.microsoft.com/kb/832769) </span></span>  
 <span data-ttu-id="ccb6c-149">[Comment sauvegarder et restaurer des installations de Windows SharePoint Services qui utilisent Microsoft SQL Server 2000 Desktop Engine (Windows)](http://support.microsoft.com/kb/833797) </span><span class="sxs-lookup"><span data-stu-id="ccb6c-149">[How to back up and restore installations of Windows SharePoint Services that use Microsoft SQL Server 2000 Desktop Engine (Windows)](http://support.microsoft.com/kb/833797) </span></span>  
 <span data-ttu-id="ccb6c-150">[Vous recevez un message d’erreur « Impossible de se connecter à la base de données de configuration » lorsque vous vous connectez à votre site Web Windows SharePoint Services](http://support.microsoft.com/kb/823287) </span><span class="sxs-lookup"><span data-stu-id="ccb6c-150">[You receive a "Cannot connect to the configuration database" error message when you connect to your Windows SharePoint Services Web site](http://support.microsoft.com/kb/823287) </span></span>  
 <span data-ttu-id="ccb6c-151">[Le message d’erreur « Service non disponible » s’affiche lorsque vous parcourez un Site Web de Windows SharePoint Services](http://support.microsoft.com/kb/823552) </span><span class="sxs-lookup"><span data-stu-id="ccb6c-151">[You Receive a "Service Unavailable" Error Message When You Browse a Windows SharePoint Services Web Site](http://support.microsoft.com/kb/823552) </span></span>  
 [<span data-ttu-id="ccb6c-152">Le message d’erreur « La base de données < nom_base_de_données > existe déjà » s’affiche lorsque vous gérez votre base de données de contenu de Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="ccb6c-152">You receive a "Database <Database_Name> already exists" error message when you manage your Windows SharePoint Services content database</span></span>](http://support.microsoft.com/kb/828815)