---
title: "Résolution des problèmes de Internet Information Services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f77084f1-5797-42ab-bbf6-fe815144232e
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 222d034c2dee38f041bb53b3164869712201bc76
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-internet-information-services"></a><span data-ttu-id="fb876-102">Dépannage des Services Internet (IIS)</span><span class="sxs-lookup"><span data-stu-id="fb876-102">Troubleshooting Internet Information Services</span></span>
<span data-ttu-id="fb876-103">Microsoft Internet Information Services (IIS) est très utilisé par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour ses diverses fonctionnalités, notamment les adaptateurs HTTP, SOAP et Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="fb876-103">Microsoft Internet Information Services (IIS) is used extensively by Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for various functionality including the HTTP, SOAP, and Windows SharePoint Services adapters.</span></span> <span data-ttu-id="fb876-104">Cette rubrique décrit certains des problèmes que vous pouvez rencontrer avec les services Internet (IIS), ainsi que leurs résolutions possibles.</span><span class="sxs-lookup"><span data-stu-id="fb876-104">This topic describes some known issues that you may encounter with IIS and possible resolutions to these issues.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="fb876-105">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="fb876-105">Known Issues</span></span>  
 <span data-ttu-id="fb876-106">Les erreurs présentées dans cette rubrique peuvent ne pas s'afficher si vous ne configurez pas Internet Explorer pour désactiver les messages d'erreur HTTP simplifiés.</span><span class="sxs-lookup"><span data-stu-id="fb876-106">The errors documented in this topic may not be displayed unless you configure Internet Explorer to disable friendly HTTP error messages.</span></span>  
  
#### <a name="to-configure-internet-explorer-to-disable-friendly-http-error-messages"></a><span data-ttu-id="fb876-107">Pour configurer Internet Explorer pour désactiver les messages d'erreur HTTP simplifiés</span><span class="sxs-lookup"><span data-stu-id="fb876-107">To configure Internet Explorer to disable friendly HTTP error messages</span></span>  
  
1.  <span data-ttu-id="fb876-108">Sur le **outils** menu, cliquez sur **Options Internet**.</span><span class="sxs-lookup"><span data-stu-id="fb876-108">On the **Tools** menu, click **Internet Options**.</span></span>  
  
2.  <span data-ttu-id="fb876-109">Sur le **avancé** sous l’onglet du **navigation** section, désactivez le **afficher des messages d’erreur HTTP simplifiés** case à cocher, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="fb876-109">On the **Advanced** tab, in the **Browsing** section, clear the **Show friendly HTTP error messages** check box, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="fb876-110">Fermez Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="fb876-110">Close Internet Explorer.</span></span>  
  
#### <a name="http-404---file-not-found-error-occurs-when-accessing-a-web-page-on-an-iis-server"></a><span data-ttu-id="fb876-111">L'erreur « HTTP 404 - Fichier introuvable » se produit lorsque vous essayez d'accéder à une page Web sur un serveur IIS</span><span class="sxs-lookup"><span data-stu-id="fb876-111">"HTTP 404 - File not found" error occurs when accessing a Web page on an IIS server</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="fb876-112">Problème</span><span class="sxs-lookup"><span data-stu-id="fb876-112">Problem</span></span>  
 <span data-ttu-id="fb876-113">Lorsque vous tentez d'accéder à une page Web sur un serveur IIS, une erreur similaire à celle indiquée ci-après s'affiche :</span><span class="sxs-lookup"><span data-stu-id="fb876-113">When you attempt to access a Web page on an IIS server an error similar to the following is displayed:</span></span>  
  
 <span data-ttu-id="fb876-114">Page introuvable</span><span class="sxs-lookup"><span data-stu-id="fb876-114">Page Cannot Be Found</span></span>  
  
 <span data-ttu-id="fb876-115">\- ou -</span><span class="sxs-lookup"><span data-stu-id="fb876-115">\- or -</span></span>  
  
 <span data-ttu-id="fb876-116">HTTP 404 - Fichier introuvable</span><span class="sxs-lookup"><span data-stu-id="fb876-116">HTTP 404 - File not found</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="fb876-117">Cause</span><span class="sxs-lookup"><span data-stu-id="fb876-117">Cause</span></span>  
 <span data-ttu-id="fb876-118">Cette erreur peut se produire pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="fb876-118">This error may occur for the following reasons:</span></span>  
  
-   <span data-ttu-id="fb876-119">Le fichier recherché a été renommé.</span><span class="sxs-lookup"><span data-stu-id="fb876-119">The requested file has been renamed.</span></span>  
  
-   <span data-ttu-id="fb876-120">Le fichier recherché a été déplacé ou supprimé.</span><span class="sxs-lookup"><span data-stu-id="fb876-120">The requested file has been moved to another location or deleted.</span></span>  
  
-   <span data-ttu-id="fb876-121">Le fichier recherché est temporairement inaccessible en raison d'une maintenance, de mises à niveau ou d'autres causes inconnues.</span><span class="sxs-lookup"><span data-stu-id="fb876-121">The requested file is temporarily unavailable due to maintenance, upgrades, or other unknown causes.</span></span>  
  
-   <span data-ttu-id="fb876-122">Le fichier recherché n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="fb876-122">The requested file does not exist.</span></span>  
  
-   <span data-ttu-id="fb876-123">IIS 6.0 : l'extension de service Web ou le type MIME approprié n'est pas activé.</span><span class="sxs-lookup"><span data-stu-id="fb876-123">IIS 6.0: The appropriate Web service extension or MIME type is not enabled.</span></span>  
  
-   <span data-ttu-id="fb876-124">Un répertoire virtuel est mappé sur la racine d'un lecteur qui se trouve sur un autre serveur.</span><span class="sxs-lookup"><span data-stu-id="fb876-124">A virtual directory is mapped to the root of a drive on another server.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="fb876-125">Résolution</span><span class="sxs-lookup"><span data-stu-id="fb876-125">Resolution</span></span>  
 <span data-ttu-id="fb876-126">Suivez les étapes décrites dans la section Résolution de la Base de connaissances Microsoft l’article 248033, « principales causes du serveur IIS retourne l’erreur « HTTP 404 - Fichier introuvable » » disponible à l’adresse [http://support.microsoft.com/kb/248033](http://support.microsoft.com/kb/248033).</span><span class="sxs-lookup"><span data-stu-id="fb876-126">Follow the steps in the RESOLUTION section of Microsoft Knowledge Base article 248033, "Common reasons IIS Server returns "HTTP 404 - File not found" error" available at [http://support.microsoft.com/kb/248033](http://support.microsoft.com/kb/248033).</span></span>  
  
#### <a name="cannot-find-server-or-dns-error-error-occurs-when-accessing-a-web-page-on-an-iis-server"></a><span data-ttu-id="fb876-127">L'erreur « Impossible de trouver le serveur ou erreur DNS » se produit lorsque vous essayez d'accéder à une page Web sur un serveur IIS</span><span class="sxs-lookup"><span data-stu-id="fb876-127">"Cannot find server or DNS Error error" occurs when accessing a Web page on an IIS server</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="fb876-128">Problème</span><span class="sxs-lookup"><span data-stu-id="fb876-128">Problem</span></span>  
 <span data-ttu-id="fb876-129">Lorsque vous tentez d'accéder à une page Web sur un serveur IIS, une erreur similaire à celle indiquée ci-après s'affiche :</span><span class="sxs-lookup"><span data-stu-id="fb876-129">When you attempt to access a Web page on an IIS server an error similar to the following is displayed:</span></span>  
  
 <span data-ttu-id="fb876-130">Impossible d'afficher la page</span><span class="sxs-lookup"><span data-stu-id="fb876-130">The Page Cannot Be Displayed</span></span>  
  
 <span data-ttu-id="fb876-131">\- ou -</span><span class="sxs-lookup"><span data-stu-id="fb876-131">\- or -</span></span>  
  
 <span data-ttu-id="fb876-132">Impossible de trouver le serveur ou erreur DNS</span><span class="sxs-lookup"><span data-stu-id="fb876-132">Cannot find server or DNS Error</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="fb876-133">Cause</span><span class="sxs-lookup"><span data-stu-id="fb876-133">Cause</span></span>  
 <span data-ttu-id="fb876-134">Cette erreur peut se produire pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="fb876-134">This error may occur for the following reasons:</span></span>  
  
-   <span data-ttu-id="fb876-135">Vos paramètres de connexion Internet Explorer sont incorrects.</span><span class="sxs-lookup"><span data-stu-id="fb876-135">Your Internet Explorer connection settings are incorrect.</span></span>  
  
-   <span data-ttu-id="fb876-136">Un pare-feu ou un serveur proxy incorrectement configuré, incompatible ou ne fonctionnant pas a été installé.</span><span class="sxs-lookup"><span data-stu-id="fb876-136">Incorrectly configured, non-functioning, or incompatible firewall or proxy software has been installed.</span></span>  
  
-   <span data-ttu-id="fb876-137">Un fichier Hosts comporte une entrée incorrecte.</span><span class="sxs-lookup"><span data-stu-id="fb876-137">There is an incorrect entry in a Hosts file.</span></span>  
  
-   <span data-ttu-id="fb876-138">Votre carte réseau ne fonctionne pas correctement ou des pilotes incompatibles ont été installés.</span><span class="sxs-lookup"><span data-stu-id="fb876-138">Your network adapter is not functioning correctly or you have incompatible network adapter drivers installed.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="fb876-139">Résolution</span><span class="sxs-lookup"><span data-stu-id="fb876-139">Resolution</span></span>  
 <span data-ttu-id="fb876-140">Suivez les étapes décrites dans la section Résolution de l’article 326155 de la Base de connaissances Microsoft « message d’erreur lorsque vous essayez d’accéder à un site Web dans Internet Explorer : « Impossible d’afficher la Page » » disponible à l’adresse [http://support.microsoft.com/kb/326155](http://support.microsoft.com/kb/326155).</span><span class="sxs-lookup"><span data-stu-id="fb876-140">Follow the steps in the RESOLUTION section of Microsoft Knowledge Base article 326155, "Error message when you try to access a Web site in Internet Explorer: "Page Cannot Be Displayed"" available at [http://support.microsoft.com/kb/326155](http://support.microsoft.com/kb/326155).</span></span>  
  
#### <a name="401---access-denied-error-occurs-when-accessing-a-web-page-on-an-iis-server"></a><span data-ttu-id="fb876-141">L'erreur « 401 Accès refusé » se produit lorsque vous essayez d'accéder à une page Web sur un serveur IIS</span><span class="sxs-lookup"><span data-stu-id="fb876-141">"401 - Access denied" error occurs when accessing a Web page on an IIS server</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="fb876-142">Problème</span><span class="sxs-lookup"><span data-stu-id="fb876-142">Problem</span></span>  
 <span data-ttu-id="fb876-143">Lorsque vous tentez d'accéder à une page Web sur un serveur IIS, une erreur similaire à celle indiquée ci-après s'affiche :</span><span class="sxs-lookup"><span data-stu-id="fb876-143">When you attempt to access a Web page on an IIS server an error similar to the following is displayed:</span></span>  
  
 <span data-ttu-id="fb876-144">401 - Accès refusé</span><span class="sxs-lookup"><span data-stu-id="fb876-144">401 - Access denied</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="fb876-145">Cause</span><span class="sxs-lookup"><span data-stu-id="fb876-145">Cause</span></span>  
 <span data-ttu-id="fb876-146">IIS définit plusieurs erreurs 401 indiquant une cause plus précise de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="fb876-146">IIS defines several different 401 errors that indicate a more specific cause of the error.</span></span> <span data-ttu-id="fb876-147">Ces codes d'erreur spécifiques s'affichent dans le navigateur :</span><span class="sxs-lookup"><span data-stu-id="fb876-147">These specific error codes are displayed in the browser:</span></span>  
  
-   <span data-ttu-id="fb876-148">401.1 - Non autorisé : accès refusé en raison d'informations d'identification non valides.</span><span class="sxs-lookup"><span data-stu-id="fb876-148">401.1 - Logon failed.</span></span>  
  
-   <span data-ttu-id="fb876-149">401.2 - Non autorisé : accès refusé en raison de la configuration du serveur.</span><span class="sxs-lookup"><span data-stu-id="fb876-149">401.2 - Logon failed due to server configuration.</span></span>  
  
-   <span data-ttu-id="fb876-150">401.3 - Non autorisé : accès refusé en raison d'une liste de contrôle d'accès (ACL) définie sur la ressource requise.</span><span class="sxs-lookup"><span data-stu-id="fb876-150">401.3 - Unauthorized due to ACL on resource.</span></span>  
  
-   <span data-ttu-id="fb876-151">401.4 - Non autorisé : échec de l'autorisation en raison du filtre installé sur le serveur Web.</span><span class="sxs-lookup"><span data-stu-id="fb876-151">401.4 - Authorization failed by filter.</span></span>  
  
-   <span data-ttu-id="fb876-152">401.5 - Non autorisé : échec de l'autorisation en raison d'une application ISAPI/CGI.</span><span class="sxs-lookup"><span data-stu-id="fb876-152">401.5 - Authorization failed by ISAPI/CGI application.</span></span>  
  
-   <span data-ttu-id="fb876-153">401.7 – Accès refusé par la stratégie d'autorisation d'URL sur le serveur Web.</span><span class="sxs-lookup"><span data-stu-id="fb876-153">401.7 – Access denied by URL authorization policy on the Web server.</span></span> <span data-ttu-id="fb876-154">Ce code d'erreur est spécifique à IIS 6.0.</span><span class="sxs-lookup"><span data-stu-id="fb876-154">This error code is specific to IIS 6.0.</span></span>  
  
 <span data-ttu-id="fb876-155">Pour obtenir une liste complète des codes d’état IIS 7.0, consultez l’article 943891, de la Base de connaissances Microsoft « Codes d’état HTTP dans IIS 7.0 » disponible à l’adresse [http://support.microsoft.com/kb/943891](http://support.microsoft.com/kb/943891).</span><span class="sxs-lookup"><span data-stu-id="fb876-155">For a complete list of the IIS 7.0 status codes, see Microsoft Knowledge Base article 943891, "The HTTP status codes in IIS 7.0" available at [http://support.microsoft.com/kb/943891](http://support.microsoft.com/kb/943891).</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="fb876-156">Résolution</span><span class="sxs-lookup"><span data-stu-id="fb876-156">Resolution</span></span>  
 <span data-ttu-id="fb876-157">Suivez les étapes de [des recommandations pour la résolution des problèmes d’autorisation IIS](../core/guidelines-for-resolving-iis-permissions-problems.md) pour résoudre les problèmes d’autorisation IIS.</span><span class="sxs-lookup"><span data-stu-id="fb876-157">Follow the steps in [Guidelines for Resolving IIS Permissions Problems](../core/guidelines-for-resolving-iis-permissions-problems.md) to resolve IIS permissions problems.</span></span>  
  
#### <a name="500---internal-server-error-occurs-when-accessing-a-web-page-on-an-iis-server"></a><span data-ttu-id="fb876-158">L'erreur « 500 - Erreur interne au serveur » se produit lorsque vous essayez d'accéder à une page Web sur un serveur IIS</span><span class="sxs-lookup"><span data-stu-id="fb876-158">"500 - Internal server error" occurs when accessing a Web page on an IIS server</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="fb876-159">Problème</span><span class="sxs-lookup"><span data-stu-id="fb876-159">Problem</span></span>  
 <span data-ttu-id="fb876-160">Lorsque vous tentez d'accéder à une page Web sur un serveur IIS, une erreur similaire à celle indiquée ci-après s'affiche :</span><span class="sxs-lookup"><span data-stu-id="fb876-160">When you attempt to access a Web page on an IIS server an error similar to the following is displayed:</span></span>  
  
 <span data-ttu-id="fb876-161">500 - Erreur interne au serveur</span><span class="sxs-lookup"><span data-stu-id="fb876-161">500 - Internal server error</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="fb876-162">Cause</span><span class="sxs-lookup"><span data-stu-id="fb876-162">Cause</span></span>  
 <span data-ttu-id="fb876-163">Ce message d'erreur peut découler de divers problèmes côté serveur.</span><span class="sxs-lookup"><span data-stu-id="fb876-163">This error message can be caused by a wide variety of server-side problems.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="fb876-164">Résolution</span><span class="sxs-lookup"><span data-stu-id="fb876-164">Resolution</span></span>  
 <span data-ttu-id="fb876-165">Pour résoudre ce problème, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="fb876-165">To resolve the issue, do the following:</span></span>  
  
-   <span data-ttu-id="fb876-166">Consultez le journal de l'application du serveur IIS pour obtenir des informations sur la cause de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="fb876-166">Review the Application log of the IIS server for information about why this error occurs.</span></span>  
  
-   <span data-ttu-id="fb876-167">Consultez les fichiers journaux IIS ou HTTPERR pour obtenir des informations pouvant s'avérer utiles pour déterminer la cause de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="fb876-167">Review the IIS log files or HTTPERR log files for information that may be helpful for determining the cause of the error.</span></span> <span data-ttu-id="fb876-168">Les fichiers journaux IIS d'un ordinateur exécutant les systèmes d’exploitation [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] se trouvent par défaut dans le répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="fb876-168">By default the IIS log files on a computer running [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] operating systems are located in the following directory:</span></span>  
  
     <span data-ttu-id="fb876-169">*%Windir%\\*system32\LogFiles\W3SVC1\\</span><span class="sxs-lookup"><span data-stu-id="fb876-169">*%WinDir%\\*system32\LogFiles\W3SVC1\\</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fb876-170">*%Windir%* est un espace réservé pour l’emplacement du répertoire Windows sur le serveur IIS.</span><span class="sxs-lookup"><span data-stu-id="fb876-170">*%WinDir%* is a placeholder for the location of the Windows directory on the IIS server.</span></span>  
  
     <span data-ttu-id="fb876-171">Les fichiers journaux IIS d'un ordinateur exécutant Windows Server 2008 ou Windows Vista se trouvent par défaut dans le répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="fb876-171">By default the IIS log files on a computer running Windows Server 2008 or Windows Vista are located in the following directory:</span></span>  
  
     <span data-ttu-id="fb876-172">C:\inetpub\logs\LogFiles\W3SVC1\\</span><span class="sxs-lookup"><span data-stu-id="fb876-172">C:\inetpub\logs\LogFiles\W3SVC1\\</span></span>  
  
     <span data-ttu-id="fb876-173">Les fichiers journaux HTTPERR sur [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] se trouvent par défaut dans le répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="fb876-173">By default the HTTPERR log files on [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] are located in the following directory:</span></span>  
  
     <span data-ttu-id="fb876-174">*%Windir%*system32LogFilesHTTPERR</span><span class="sxs-lookup"><span data-stu-id="fb876-174">*%WinDir%*system32LogFilesHTTPERR</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fb876-175">Le fichier journal HTTPERR est disponible uniquement sur un ordinateur [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="fb876-175">The HTTPERR log file is only available on a [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], or Windows Vista computer.</span></span>  
  
#### <a name="service-unavailable-error-occurs-when-accessing-a-web-page-on-an-iis-server"></a><span data-ttu-id="fb876-176">L'erreur « Service indisponible » se produit lorsque vous essayez d'accéder à une page Web sur un serveur IIS</span><span class="sxs-lookup"><span data-stu-id="fb876-176">"Service Unavailable" error occurs when accessing a Web page on an IIS server</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="fb876-177">Problème</span><span class="sxs-lookup"><span data-stu-id="fb876-177">Problem</span></span>  
 <span data-ttu-id="fb876-178">Lorsque vous tentez d'accéder à une page Web sur un serveur IIS, une erreur similaire à celle indiquée ci-après s'affiche :</span><span class="sxs-lookup"><span data-stu-id="fb876-178">When you attempt to access a Web page on an IIS server an error similar to the following is displayed:</span></span>  
  
 <span data-ttu-id="fb876-179">Service non disponible</span><span class="sxs-lookup"><span data-stu-id="fb876-179">Service Unavailable</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="fb876-180">Cause</span><span class="sxs-lookup"><span data-stu-id="fb876-180">Cause</span></span>  
 <span data-ttu-id="fb876-181">Cette erreur se produit généralement lorsque le pool d'applications (IIS 6.0 et IIS 7.0) pour la page Web est arrêté.</span><span class="sxs-lookup"><span data-stu-id="fb876-181">The most common cause for this error is that the application pool (IIS 6.0 and IIS 7.0) for the Web page is stopped.</span></span> <span data-ttu-id="fb876-182">Ceci survient généralement lorsque le pool d'applications ou l'application COM+ est configuré avec une identité pour laquelle le nom d'utilisateur et/ou le mot de passe spécifiés ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="fb876-182">This commonly occurs if the application pool or COM+ application is configured with an Identity for which the specified user name and or password is invalid.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="fb876-183">Résolution</span><span class="sxs-lookup"><span data-stu-id="fb876-183">Resolution</span></span>  
 <span data-ttu-id="fb876-184">Suivez les étapes décrites dans la section « Paramètre IIS Application identité du processus hôte » de la rubrique [des recommandations pour la résolution des problèmes d’autorisation IIS](../core/guidelines-for-resolving-iis-permissions-problems.md) pour définir l’identité du processus hôte approprié.</span><span class="sxs-lookup"><span data-stu-id="fb876-184">Follow the steps in the "Setting IIS Application Host Process Identity" section of the topic [Guidelines for Resolving IIS Permissions Problems](../core/guidelines-for-resolving-iis-permissions-problems.md) to set the appropriate host process identity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb876-185">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb876-185">See Also</span></span>  
 [<span data-ttu-id="fb876-186">Instructions pour la résolution des problèmes d’autorisation IIS</span><span class="sxs-lookup"><span data-stu-id="fb876-186">Guidelines for Resolving IIS Permissions Problems</span></span>](../core/guidelines-for-resolving-iis-permissions-problems.md)