---
title: 'Résolution des problèmes : Problèmes et Resolutions3 | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting
ms.assetid: 40f59f54-183e-43db-afb5-0a45b437697f
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68c63e7aeab46436e894d43d77b92a2a061d5b60
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="troubleshooting-issues-and-resolutions"></a><span data-ttu-id="c3098-102">Résolution des problèmes : Problèmes et résolutions</span><span class="sxs-lookup"><span data-stu-id="c3098-102">Troubleshooting: Issues and Resolutions</span></span>
<span data-ttu-id="c3098-103">Cette rubrique traite des problèmes liés à l’exécution [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c3098-103">This topic addresses issues related to running [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span></span> <span data-ttu-id="c3098-104">La personne émet en détail un problème spécifique, des causes possibles et une solution.</span><span class="sxs-lookup"><span data-stu-id="c3098-104">The individual issues detail a specific symptom, a possible cause, and a solution.</span></span>  
  
## <a name="error-publishing-a-batch-of-n-messages"></a><span data-ttu-id="c3098-105">Erreur de publication d’un lot de messages « n »</span><span class="sxs-lookup"><span data-stu-id="c3098-105">Error publishing a batch of "n" messages</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="c3098-106">Symptôme</span><span class="sxs-lookup"><span data-stu-id="c3098-106">Symptom</span></span>  
 <span data-ttu-id="c3098-107">Vous recevez l’erreur suivante ou similaire dans le journal des événements :</span><span class="sxs-lookup"><span data-stu-id="c3098-107">You receive the following or similar error in the event log:</span></span>  
  
 <span data-ttu-id="c3098-108">Le moteur de messagerie a rencontré une erreur de publication d’un lot de messages de « n » à la base de données de la boîte de Message pour l’adaptateur de transport « Récepteur de HTTP BizTalk ».</span><span class="sxs-lookup"><span data-stu-id="c3098-108">The Messaging Engine encountered an error publishing a batch of "n" messages to the Message Box database for the transport adapter "BizTalk HTTP Receiver".</span></span> <span data-ttu-id="c3098-109">Reportez-vous à l’outil suivi des activités et des informations plus détaillées sur ce problème et vérifiez que les liaisons de point de terminaison sont correctement configurés.</span><span class="sxs-lookup"><span data-stu-id="c3098-109">Please refer to Health and Activity Tracking tool for more detailed information on this failure and check the endpoint bindings are correctly configured.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="c3098-110">Cause possible</span><span class="sxs-lookup"><span data-stu-id="c3098-110">Possible Cause</span></span>  
 <span data-ttu-id="c3098-111">Cette erreur peut être causée par l'une des raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="c3098-111">This error could be caused by one of the following reasons:</span></span>  
  
-   <span data-ttu-id="c3098-112">Certificat de déchiffrement manquant</span><span class="sxs-lookup"><span data-stu-id="c3098-112">Missing decryption certificate</span></span>  
  
-   <span data-ttu-id="c3098-113">Incorrectement un message chiffré</span><span class="sxs-lookup"><span data-stu-id="c3098-113">Incorrectly encrypted message</span></span>  
  
-   <span data-ttu-id="c3098-114">Message non autorisé (source ne pas reconnu comme un partenaire valide)</span><span class="sxs-lookup"><span data-stu-id="c3098-114">Unauthorized message (source not recognized as a valid partner)</span></span>  
  
-   <span data-ttu-id="c3098-115">Échec de validation de n’importe quelle partie de l’en-tête de message : préambule, en-tête de remise ou en-tête de service.</span><span class="sxs-lookup"><span data-stu-id="c3098-115">Message failing validation of any header part: preamble, delivery header, or service header.</span></span>  
  
 <span data-ttu-id="c3098-116">Ce message peut être précédé d’un autre message d’erreur qui explique la cause.</span><span class="sxs-lookup"><span data-stu-id="c3098-116">This message may be preceded by another error message that details the cause.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="c3098-117">Solution</span><span class="sxs-lookup"><span data-stu-id="c3098-117">Solution</span></span>  
 <span data-ttu-id="c3098-118">Passez en revue les détails fournis avec le message d’erreur pour obtenir une aide supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="c3098-118">Review the details provided with the error message for additional help.</span></span> <span data-ttu-id="c3098-119">Le redémarrage de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]™ peut résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="c3098-119">Restarting [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]™ may resolve this issue.</span></span>  
  
## <a name="you-cannot-unenlist-all-artifacts"></a><span data-ttu-id="c3098-120">Vous ne pouvez pas désinscrire tous les artefacts</span><span class="sxs-lookup"><span data-stu-id="c3098-120">You cannot unenlist all artifacts</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="c3098-121">Symptôme</span><span class="sxs-lookup"><span data-stu-id="c3098-121">Symptom</span></span>  
 <span data-ttu-id="c3098-122">Exécute la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]utilitaire de nettoyage de ne pas désinscrire tous les artefacts.</span><span class="sxs-lookup"><span data-stu-id="c3098-122">Running the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Clean utility does not unenlist all artifacts.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="c3098-123">Cause possible</span><span class="sxs-lookup"><span data-stu-id="c3098-123">Possible Cause</span></span>  
 <span data-ttu-id="c3098-124">Si vous exécutez le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]nettoyer utilitaire avant de supprimer des contrats et les partenaires à partir de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® Management Console (MMC), l’utilitaire BtarnClean ne pourrez pas désinscrire tous les artefacts car elles sont toujours utilisées.</span><span class="sxs-lookup"><span data-stu-id="c3098-124">If you run the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Clean utility before deleting agreements and partners from the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® Management Console (MMC), the BtarnClean utility will not be able to unenlist all artifacts because they are still used.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="c3098-125">Solution</span><span class="sxs-lookup"><span data-stu-id="c3098-125">Solution</span></span>  
  
##### <a name="to-remove-artifacts-using-the-loopback-utility"></a><span data-ttu-id="c3098-126">Pour supprimer les artefacts à l’aide de l’utilitaire de bouclage</span><span class="sxs-lookup"><span data-stu-id="c3098-126">To remove artifacts using the Loopback utility</span></span>  
  
1.  <span data-ttu-id="c3098-127">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="c3098-127">At the command prompt, type:</span></span>  
  
    ```  
    lookback.exe /disable <home org or partner>  
    ```  
  
2.  <span data-ttu-id="c3098-128">Exécutez le fichier BtarnClean.exe.</span><span class="sxs-lookup"><span data-stu-id="c3098-128">Run the BtarnClean.exe file.</span></span>  
  
3.  <span data-ttu-id="c3098-129">Dans l’Explorateur BizTalk, supprimez les parties.</span><span class="sxs-lookup"><span data-stu-id="c3098-129">In BizTalk Explorer, delete the parties.</span></span>  
  
## <a name="installing-btarn-on-a-computer-without-biztalk-server-causes-missing-files"></a><span data-ttu-id="c3098-130">Installation de BTARN sur un ordinateur sans BizTalk Server provoque des fichiers manquants</span><span class="sxs-lookup"><span data-stu-id="c3098-130">Installing BTARN on a computer without BizTalk Server causes missing files</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="c3098-131">Symptôme</span><span class="sxs-lookup"><span data-stu-id="c3098-131">Symptom</span></span>  
 <span data-ttu-id="c3098-132">L’exécution du fichier ConfigFramework.exe aboutit à aucun résultat sur un ordinateur qui n’a pas [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Server ou [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] installé.</span><span class="sxs-lookup"><span data-stu-id="c3098-132">Running the ConfigFramework.exe file yields no results on a computer that does not have [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Server or [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] installed.</span></span> <span data-ttu-id="c3098-133">Vous pouvez utiliser uniquement cette [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] configuration comme un client HTTP.</span><span class="sxs-lookup"><span data-stu-id="c3098-133">You can only use this [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] configuration as an HTTP client.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="c3098-134">Cause possible</span><span class="sxs-lookup"><span data-stu-id="c3098-134">Possible Cause</span></span>  
 <span data-ttu-id="c3098-135">Deux fichiers DLL sont manquantes dans l’installation.</span><span class="sxs-lookup"><span data-stu-id="c3098-135">Two DLL files are missing from the installation.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="c3098-136">Solution</span><span class="sxs-lookup"><span data-stu-id="c3098-136">Solution</span></span>  
 <span data-ttu-id="c3098-137">Installation de SQLXML sur l’ordinateur et ensuite copier manuellement les fichiers Msxml4.dll et Atl71.dll au dossier du système.</span><span class="sxs-lookup"><span data-stu-id="c3098-137">Install SQLXML on the computer, and then manually copy the Msxml4.dll and Atl71.dll files to the System folder.</span></span>  
  
## <a name="you-receive-an-access-error-when-attempting-to-change-the-btarn-configuration"></a><span data-ttu-id="c3098-138">Vous recevez une erreur d’accès lors de la tentative de modifier la configuration de BTARN</span><span class="sxs-lookup"><span data-stu-id="c3098-138">You receive an access error when attempting to change the BTARN configuration</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="c3098-139">Symptôme</span><span class="sxs-lookup"><span data-stu-id="c3098-139">Symptom</span></span>  
 <span data-ttu-id="c3098-140">Le message d’erreur suivant s’affiche lorsque vous importez un fichier de configuration en utilisant le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion :</span><span class="sxs-lookup"><span data-stu-id="c3098-140">You receive the following error message when you import a configuration file using the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console:</span></span>  
  
 <span data-ttu-id="c3098-141">N’a pas pu les données de type de transport pour le Transport principal du Port d’envoi ' RNSTT. Async » à la banque de configuration.</span><span class="sxs-lookup"><span data-stu-id="c3098-141">Could not store transport type data for Primary Transport of Send Port 'RNSTT.Async' to config store.</span></span> <span data-ttu-id="c3098-142">Accès refusé.</span><span class="sxs-lookup"><span data-stu-id="c3098-142">Access is denied.</span></span>  
  
 <span data-ttu-id="c3098-143">Vous pouvez également recevoir cette erreur lorsque vous essayez de modifier la configuration, par exemple en créant un nouveau partenaire.</span><span class="sxs-lookup"><span data-stu-id="c3098-143">You can also receive this error when you try to change the configuration, such as by creating a new partner.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="c3098-144">Cause possible</span><span class="sxs-lookup"><span data-stu-id="c3098-144">Possible Cause</span></span>  
 <span data-ttu-id="c3098-145">L’utilisateur actuel n’est pas un membre du groupe Administrateurs de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="c3098-145">The current user is not a member of the BizTalk Administrators group.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="c3098-146">Solution</span><span class="sxs-lookup"><span data-stu-id="c3098-146">Solution</span></span>  
 <span data-ttu-id="c3098-147">Assurez-vous que l’utilisateur actuel est membre du groupe Administrateurs de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="c3098-147">Make sure that the current user is a member of the BizTalk Administrators group.</span></span>  
  
## <a name="you-receive-bam-errors"></a><span data-ttu-id="c3098-148">Vous recevez des erreurs d’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="c3098-148">You receive BAM errors</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="c3098-149">Symptôme</span><span class="sxs-lookup"><span data-stu-id="c3098-149">Symptom</span></span>  
 <span data-ttu-id="c3098-150">Vous recevez des messages d’erreur suivants dans l’Observateur d’événements :</span><span class="sxs-lookup"><span data-stu-id="c3098-150">You receive the following error messages in the Event Viewer:</span></span>  
  
 <span data-ttu-id="c3098-151">Erreur s’est produite dans le suivi de l’activité du Message.</span><span class="sxs-lookup"><span data-stu-id="c3098-151">Error happened in tracking Message activity.</span></span> <span data-ttu-id="c3098-152">Message d’erreur est stocké n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="c3098-152">Error message is Stored Procedure Does Not Exist.</span></span>  
  
 <span data-ttu-id="c3098-153">-ou-</span><span class="sxs-lookup"><span data-stu-id="c3098-153">-or-</span></span>  
  
 <span data-ttu-id="c3098-154">Erreur lors de la fin d’activité de message BAM avec l’id  *\<numéro d’identification\>*.</span><span class="sxs-lookup"><span data-stu-id="c3098-154">Error in terminating BAM message activity with id *\<ID number\>*.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="c3098-155">Cause possible</span><span class="sxs-lookup"><span data-stu-id="c3098-155">Possible Cause</span></span>  
 <span data-ttu-id="c3098-156">L’outil de suivi d’analyse BAM (Business Activity) n’est pas installé.</span><span class="sxs-lookup"><span data-stu-id="c3098-156">The Business Activity Monitoring (BAM) tracking tool is not installed.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="c3098-157">Solution</span><span class="sxs-lookup"><span data-stu-id="c3098-157">Solution</span></span>  
 <span data-ttu-id="c3098-158">Installer l’à l’aide de l’outil de suivi BAM le **Installation personnalisée** option.</span><span class="sxs-lookup"><span data-stu-id="c3098-158">Install the BAM tracking tool using the **Custom Installation** option.</span></span> <span data-ttu-id="c3098-159">Si vous n’avez pas besoin de fonctionnalités d’analyse BAM, vous pouvez ignorer ces messages ou désactiver le suivi à l’aide du [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion.</span><span class="sxs-lookup"><span data-stu-id="c3098-159">If you do not need BAM functionality, you can ignore these messages or disable tracking using the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console.</span></span> <span data-ttu-id="c3098-160">Après avoir désactivé le suivi, vous devez redémarrer [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et Internet et les Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="c3098-160">After you disable tracking, you must restart [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and Internet and Information Services (IIS).</span></span>  
  
## <a name="your-xsd-schema-does-not-display-properly-in-biztalk-editor"></a><span data-ttu-id="c3098-161">Votre schéma XSD ne pas s’afficher correctement dans l’Éditeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="c3098-161">Your XSD Schema does not display properly in BizTalk Editor</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="c3098-162">Symptôme</span><span class="sxs-lookup"><span data-stu-id="c3098-162">Symptom</span></span>  
 <span data-ttu-id="c3098-163">Vous ne pouvez pas afficher le contenu d’un schéma correctement dans l’Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="c3098-163">You cannot view the content of a schema properly in BizTalk Editor.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="c3098-164">Cause possible</span><span class="sxs-lookup"><span data-stu-id="c3098-164">Possible Cause</span></span>  
 <span data-ttu-id="c3098-165">Il manque le schéma le `displayroot_reference` d’attribut pour le `schemaInfo` élément.</span><span class="sxs-lookup"><span data-stu-id="c3098-165">The schema is missing the `displayroot_reference` attribute for the `schemaInfo` element.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="c3098-166">Solution</span><span class="sxs-lookup"><span data-stu-id="c3098-166">Solution</span></span>  
 <span data-ttu-id="c3098-167">Ouvrez le schéma dans le bloc-notes ou un autre éditeur de texte et ajoutez le `displayroot_reference` attribut le `schemaInfo` élément.</span><span class="sxs-lookup"><span data-stu-id="c3098-167">Open the schema in Notepad or another text editor and add the `displayroot_reference` attribute to the `schemaInfo` element.</span></span> <span data-ttu-id="c3098-168">La valeur de la `displayroot_reference` attribut doit être le même que le `root_reference` attribut.</span><span class="sxs-lookup"><span data-stu-id="c3098-168">The value of the `displayroot_reference` attribute should be the same as the `root_reference` attribute.</span></span>  
  
 <span data-ttu-id="c3098-169">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c3098-169">For example:</span></span>  
  
 <span data-ttu-id="c3098-170">\<schemaInfo document_type = « 4A1 » version = « V02_00 » xmlns = « http://schemas.microsoft.com/BizTalk/2003 » *displayroot_reference = « Pip4A1StrategicForecastNotification »* root_reference = » Pip4A1StrategicForecastNotification »\></span><span class="sxs-lookup"><span data-stu-id="c3098-170">\<schemaInfo document_type="4A1" version="V02_00" xmlns="http://schemas.microsoft.com/BizTalk/2003" *displayroot_reference="Pip4A1StrategicForecastNotification"* root_reference="Pip4A1StrategicForecastNotification" \></span></span>  
  
## <a name="404-not-found-error-when-sending-a-http-request"></a><span data-ttu-id="c3098-171">Erreur 404 introuvable lors de l’envoi d’une requête HTTP</span><span class="sxs-lookup"><span data-stu-id="c3098-171">404 Not found error when sending a HTTP request</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="c3098-172">Symptôme</span><span class="sxs-lookup"><span data-stu-id="c3098-172">Symptom</span></span>  
 <span data-ttu-id="c3098-173">Vous recevez les erreurs suivantes ou similaires lors de l’envoi d’une requête HTTP :</span><span class="sxs-lookup"><span data-stu-id="c3098-173">You receive the following or similar errors when sending a HTTP request:</span></span>  
  
 <span data-ttu-id="c3098-174">Le serveur distant a retourné une erreur : (404) introuvable.</span><span class="sxs-lookup"><span data-stu-id="c3098-174">The remote server returned an error: (404) Not Found.</span></span>  
  
 <span data-ttu-id="c3098-175">Impossible d’envoyer le message à... / BTSHttpReceive.dll.</span><span class="sxs-lookup"><span data-stu-id="c3098-175">Message cannot be sent to ../BTSHttpReceive.dll.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="c3098-176">Cause possible</span><span class="sxs-lookup"><span data-stu-id="c3098-176">Possible Cause</span></span>  
 <span data-ttu-id="c3098-177">Le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] DLL (BTSHttpReceive.dll) d’extension Internet Server API (ISAPI) n’a pas été configurée dans Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="c3098-177">The [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Internet Server API (ISAPI) extension DLL (BTSHttpReceive.dll) has not been configured in Internet Information Services (IIS).</span></span> <span data-ttu-id="c3098-178">Cela se produit si l’extension du service web HwsMessages HttpReceive n’est pas configurée et si cette extension de service web est configurée, mais non autorisée.</span><span class="sxs-lookup"><span data-stu-id="c3098-178">This occurs if the HwsMessages HttpReceive web service extension is not configured and if this web service extension is configured, but not allowed.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="c3098-179">Solution</span><span class="sxs-lookup"><span data-stu-id="c3098-179">Solution</span></span>  
 <span data-ttu-id="c3098-180">Pour déterminer si l’extension du service web HwsMessages HttpReceive est configurée et si elle n'est pas configurée, afin d’autoriser son, effectuez la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="c3098-180">To determine whether the HwsMessages HttpReceive web service extension is configured, and if it is not configured, to allow it, perform the following procedure.</span></span>  
  
##### <a name="to-configure-the-biztalk-isapi-extension-dll-in-iis"></a><span data-ttu-id="c3098-181">Pour configurer la DLL d’extension ISAPI de BizTalk dans IIS</span><span class="sxs-lookup"><span data-stu-id="c3098-181">To configure the BizTalk ISAPI extension DLL in IIS</span></span>  
  
1.  <span data-ttu-id="c3098-182">Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="c3098-182">Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="c3098-183">Développez  **\<nom de l’ordinateur\> (ordinateur local)**, puis cliquez sur **Extensions du Service Web**.</span><span class="sxs-lookup"><span data-stu-id="c3098-183">Expand **\<computer name\> (local computer)**, and then click **Web Service Extensions**.</span></span>  
  
3.  <span data-ttu-id="c3098-184">Dans le **Extension du Service Web** volet, vérifiez que l’état de HwsMessages HttpReceive est autorisé.</span><span class="sxs-lookup"><span data-stu-id="c3098-184">In the **Web Service Extension** pane, verify that the status for HwsMessages HttpReceive is Allowed.</span></span> <span data-ttu-id="c3098-185">Avec le bouton droit dans le cas contraire, **HwsMessages HttpReceive**, puis cliquez sur **autoriser**.</span><span class="sxs-lookup"><span data-stu-id="c3098-185">If not, right-click **HwsMessages HttpReceive**, and then click **Allow**.</span></span>  
  
 <span data-ttu-id="c3098-186">Si l’extension du service web HwsMessages HttpReceive n’est pas configurée (il n'est pas inclus dans la liste d’Extensions du Service Web dans le Gestionnaire des services Internet), effectuez la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="c3098-186">If the HwsMessages HttpReceive web service extension is not configured (it is not included in the Web Service Extensions list in IIS Manager), perform the following procedure.</span></span>  
  
##### <a name="to-configure-the-biztalk-isapi-extension-dll-in-iis"></a><span data-ttu-id="c3098-187">Pour configurer la DLL d’extension ISAPI de BizTalk dans IIS</span><span class="sxs-lookup"><span data-stu-id="c3098-187">To configure the BizTalk ISAPI extension DLL in IIS</span></span>  
  
1.  <span data-ttu-id="c3098-188">Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="c3098-188">Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="c3098-189">Développez  **\<nom de l’ordinateur\> (ordinateur local)**, avec le bouton droit **Extensions du Service Web**, puis cliquez sur **ajouter une nouvelle extension de service Web** .</span><span class="sxs-lookup"><span data-stu-id="c3098-189">Expand **\<computer name\> (local computer)**, right-click **Web Service Extensions**, and then click **Add a new Web service extension**.</span></span>  
  
3.  <span data-ttu-id="c3098-190">Dans le **nouvelle Extension de Service Web** boîte de dialogue le **nom de l’Extension** , tapez **BizTalk d’Extension ISAPI**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="c3098-190">In the **New Web Service Extension** dialog box, in the **Extension Name** box, type **BizTalk ISAPI Extension**, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="c3098-191">Dans le **ajouter un fichier** boîte de dialogue le **chemin d’accès au fichier** , tapez  **\<lecteur\>: \Program Files\Microsoft BizTalk Server \<version\>\HttpReceive\BTSHttpReceive.dll**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c3098-191">In the **Add File** dialog box, in the **Path to file** box, type **\<drive\>:\Program Files\Microsoft BizTalk Server \<version\>\HttpReceive\BTSHttpReceive.dll**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="c3098-192">Dans le **nouvelle Extension de Service Web** boîte de dialogue, sélectionnez **définir l’état de l’extension à autorisée**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c3098-192">In the **New Web Service Extension** dialog box, select **Set extension status to Allowed**, and then click **OK**.</span></span>  
  
## <a name="an-access-violation-occurs-when-running-the-configuration-wizard"></a><span data-ttu-id="c3098-193">Une violation d’accès se produit lors de l’exécution de l’Assistant Configuration</span><span class="sxs-lookup"><span data-stu-id="c3098-193">An access violation occurs when running the Configuration Wizard</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="c3098-194">Symptôme</span><span class="sxs-lookup"><span data-stu-id="c3098-194">Symptom</span></span>  
 <span data-ttu-id="c3098-195">Vous recevez l’erreur suivante ou similaire dans le journal des événements :</span><span class="sxs-lookup"><span data-stu-id="c3098-195">You receive the following or similar error in the event log:</span></span>  
  
 <span data-ttu-id="c3098-196">Une instance d’hôte BizTalk isolé configurée avec le compte d’utilisateur '\HostSvc' n’est pas exécuté ou n’existe pas sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c3098-196">A BizTalk isolated host instance configured with the user account '\HostSvc' was either not running or does not exist on this computer.</span></span> <span data-ttu-id="c3098-197">Utilisez la Console Administration de BizTalk pour créer un hôte isolé ou reconfigurer un existant pour s’exécuter en tant que '\hostsvc'.</span><span class="sxs-lookup"><span data-stu-id="c3098-197">Use the BizTalk Administration Console to create a new isolated host or reconfigure an existing to run as '\hostsvc'.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="c3098-198">Cause possible</span><span class="sxs-lookup"><span data-stu-id="c3098-198">Possible Cause</span></span>  
 <span data-ttu-id="c3098-199">Pour exécuter l’Assistant Configuration, l’utilisateur doit être configuré comme\<*nom de l’ordinateur*\>\hostsvc', pas '\hostsvc'.</span><span class="sxs-lookup"><span data-stu-id="c3098-199">To run the Configuration Wizard, the user should be configured as '\<*machine name*\>\hostsvc', not '\hostsvc'.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="c3098-200">Solution</span><span class="sxs-lookup"><span data-stu-id="c3098-200">Solution</span></span>  
 <span data-ttu-id="c3098-201">Ouvrez la Console Administration de BizTalk et modifier les hôtes qui sont exécutent sous le compte '\hostsvc', afin qu’ils s’exécutent sous le compte '\<*nom de l’ordinateur*\>\hostsvc'.</span><span class="sxs-lookup"><span data-stu-id="c3098-201">Open the BizTalk Administration Console, and change hosts that are running under the account '\hostsvc', so that they run under the account '\<*machine name*\>\hostsvc'.</span></span>  
  
## <a name="you-receive-an-error-when-importing-and-compiling-a-rosettanet-next-generation-pip-schema"></a><span data-ttu-id="c3098-202">Vous recevez une erreur lors de l’importation et de la compilation d’un schéma d’adresse PIP de RosettaNet prochaine génération</span><span class="sxs-lookup"><span data-stu-id="c3098-202">You receive an error when importing and compiling a RosettaNet Next Generation PIP schema</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="c3098-203">Symptôme</span><span class="sxs-lookup"><span data-stu-id="c3098-203">Symptom</span></span>  
 <span data-ttu-id="c3098-204">Vous recevez l’erreur suivante ou similaire dans le journal des événements :</span><span class="sxs-lookup"><span data-stu-id="c3098-204">You receive the following or similar error in the event log:</span></span>  
  
 <span data-ttu-id="c3098-205">erreur CS0234 : le nom de l’espace de noms ou de type 'SerializableAttribute' n’existe pas dans la classe ou l’espace de noms 'RosettaNet.Schemas.System' (vous manque-t-il une référence d’assembly ?).</span><span class="sxs-lookup"><span data-stu-id="c3098-205">error CS0234: The type or namespace name 'SerializableAttribute' does not exist in the class or namespace 'RosettaNet.Schemas.System' (are you missing an assembly reference?).</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="c3098-206">Cause possible</span><span class="sxs-lookup"><span data-stu-id="c3098-206">Possible Cause</span></span>  
 <span data-ttu-id="c3098-207">Un de vos schémas, par exemple, StandardDocumentHeader.xsd, a un [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] espace de noms de RosettaNet.Schemas.System.</span><span class="sxs-lookup"><span data-stu-id="c3098-207">One of your schemas, for example, StandardDocumentHeader.xsd, has a [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] namespace of RosettaNet.Schemas.System.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="c3098-208">Solution</span><span class="sxs-lookup"><span data-stu-id="c3098-208">Solution</span></span>  
 <span data-ttu-id="c3098-209">Supprimer le « système » de la [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] espace de noms pour le schéma, afin que l’espace de noms est RosettaNet.Schemas.</span><span class="sxs-lookup"><span data-stu-id="c3098-209">Remove the "System" from the [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] namespace for the schema, so that the namespace is RosettaNet.Schemas.</span></span>  
  
## <a name="you-receive-an-error-when-trying-to-manually-deploy-the-bam-package"></a><span data-ttu-id="c3098-210">Vous recevez une erreur lorsque vous tentez de déployer manuellement le Package d’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="c3098-210">You receive an error when trying to manually deploy the BAM Package</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="c3098-211">Symptôme</span><span class="sxs-lookup"><span data-stu-id="c3098-211">Symptom</span></span>  
 <span data-ttu-id="c3098-212">Lorsque vous essayez manuellement déployer le package d’analyse BAM pour [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], vous recevez une erreur indiquant que vous ne pouvez pas déployer le package.</span><span class="sxs-lookup"><span data-stu-id="c3098-212">When you manually try to deploy the BAM package for [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], you receive an error indicating that you cannot deploy the package.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="c3098-213">Cause possible</span><span class="sxs-lookup"><span data-stu-id="c3098-213">Possible Cause</span></span>  
 <span data-ttu-id="c3098-214">Les packages DTS BAM_DM_Process et BAM_DM_Message sont installés sur votre système, ce qui empêche le déploiement du package d’analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="c3098-214">The DTS packages BAM_DM_Process and BAM_DM_Message are installed on your system, preventing deployment of the BAM package.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="c3098-215">Solution</span><span class="sxs-lookup"><span data-stu-id="c3098-215">Solution</span></span>  
  
##### <a name="to-recover-from-the-error-condition-and-deploy-the-bam-package"></a><span data-ttu-id="c3098-216">Pour récupérer à partir de la condition d’erreur et de déployer le package d’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="c3098-216">To recover from the error condition and deploy the BAM package</span></span>  
  
1.  <span data-ttu-id="c3098-217">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft SQL Server**, puis cliquez sur **Enterprise Manager**.</span><span class="sxs-lookup"><span data-stu-id="c3098-217">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **Enterprise Manager**.</span></span>  
  
2.  <span data-ttu-id="c3098-218">Dans Enterprise Manager, développez **serveurs Microsoft SQL Server**, **groupe SQL Server**, **(local) (Windows NT)**, et **Data Transformation Services**.</span><span class="sxs-lookup"><span data-stu-id="c3098-218">In Enterprise Manager, expand **Microsoft SQL Servers**, **SQL Server Group**, **(local) (Windows NT)**, and **Data Transformation Services**.</span></span>  
  
3.  <span data-ttu-id="c3098-219">Cliquez sur **lots locaux**, avec le bouton droit **BAM_DM_Message**, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="c3098-219">Click **Local Packages**, right-click **BAM_DM_Message**, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="c3098-220">Avec le bouton droit **BAM_DM_Process**, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="c3098-220">Right-click **BAM_DM_Process**, and then click **Delete**.</span></span>  
  
5.  <span data-ttu-id="c3098-221">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c3098-221">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="c3098-222">À l’invite de commandes, tapez le code suivant pour déployer le fichier de suivi, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c3098-222">At the command prompt, type the following code to deploy the tracking file, and then click **OK**.</span></span>  
  
    ```  
    cd %ProgramFiles%\Microsoft BizTalk Server <version>\Tracking  
    bm deploy all  "%ProgramFiles%\Microsoft BizTalk <version> Accelerator for RosettaNet\BAMTracking\tracking.xml"  
    ```  
  
## <a name="you-receive-an-error-when-adding-a-new-pip"></a><span data-ttu-id="c3098-223">Vous recevez une erreur lors de l’ajout d’un nouveau PIP</span><span class="sxs-lookup"><span data-stu-id="c3098-223">You receive an error when adding a new PIP</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="c3098-224">Symptôme</span><span class="sxs-lookup"><span data-stu-id="c3098-224">Symptom</span></span>  
 <span data-ttu-id="c3098-225">Vous recevez l’erreur suivante ou similaire dans le journal des événements :</span><span class="sxs-lookup"><span data-stu-id="c3098-225">You receive the following or similar error in the event log:</span></span>  
  
 <span data-ttu-id="c3098-226">UNP. SCON. VALERR : Une erreur s’est produite lors de la validation du contenu du service.</span><span class="sxs-lookup"><span data-stu-id="c3098-226">UNP.SCON.VALERR: A failure occurred while validating the service content.</span></span>  
  
 <span data-ttu-id="c3098-227">Détails : La recherche de spécification de document par type de message a échoué.</span><span class="sxs-lookup"><span data-stu-id="c3098-227">Details: Finding document specification by message type failed.</span></span> <span data-ttu-id="c3098-228">Vérifiez que le schéma est correctement déployé.</span><span class="sxs-lookup"><span data-stu-id="c3098-228">Verify that the schema is deployed properly.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="c3098-229">Cause possible</span><span class="sxs-lookup"><span data-stu-id="c3098-229">Possible Cause</span></span>  
 <span data-ttu-id="c3098-230">L’espace de noms du document ou de la propriété de nœud racine du schéma déployé pour l’instance Pip4A5NotifyofForecastReply est incorrect.</span><span class="sxs-lookup"><span data-stu-id="c3098-230">Either the document namespace or the root node property the deployed schema for the instance Pip4A5NotifyofForecastReply is incorrect.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="c3098-231">Solution</span><span class="sxs-lookup"><span data-stu-id="c3098-231">Solution</span></span>  
 <span data-ttu-id="c3098-232">Vérifiez que l’espace de noms du document et de la propriété de nœud racine pour le schéma déployé Pip4A5NotifyofForecastReply pour l’instance est correct.</span><span class="sxs-lookup"><span data-stu-id="c3098-232">Verify that the document namespace and the root node property for the deployed schema for instance Pip4A5NotifyofForecastReply is correct.</span></span>  
  
## <a name="error-during-the-configuration-of-btarn-at-installation-time-caused-by-presumed-network-connectivity-issues"></a><span data-ttu-id="c3098-233">Erreur lors de la configuration BTARN au moment de l’installation, due supposées réseau des problèmes de connectivité</span><span class="sxs-lookup"><span data-stu-id="c3098-233">Error during the configuration of BTARN at installation time, caused by presumed network connectivity issues</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="c3098-234">Symptôme</span><span class="sxs-lookup"><span data-stu-id="c3098-234">Symptom</span></span>  
 <span data-ttu-id="c3098-235">Pendant le processus de configuration, vous recevez une erreur dans la boîte de dialogue d’erreur indiquant que l’ordinateur n’est pas correctement connecté au réseau, quand il est en fait.</span><span class="sxs-lookup"><span data-stu-id="c3098-235">During the configuration process, you receive an error in the error dialog box indicating that the computer is not properly connected to the network, when in fact it is.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="c3098-236">Cause possible</span><span class="sxs-lookup"><span data-stu-id="c3098-236">Possible Cause</span></span>  
 <span data-ttu-id="c3098-237">Cette erreur peut être dû à la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] programme de configuration IP de mauvaise adresses.</span><span class="sxs-lookup"><span data-stu-id="c3098-237">This error may be caused by the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] configuration program misinterpreting IP addresses.</span></span> <span data-ttu-id="c3098-238">Le fichier hosts à C:\Windows\system32\drivers\etc contient une entrée de mappage du nom d’hôte localhost à l’adresse IP 127.0.0.1.</span><span class="sxs-lookup"><span data-stu-id="c3098-238">The hosts file in C:\Windows\system32\drivers\etc contains an entry mapping the localhost host name to the IP address 127.0.0.1.</span></span> <span data-ttu-id="c3098-239">Le programme de configuration peut confondre cette valeur avec l’adresse de bouclage et supposent que l’ordinateur n’est pas connecté correctement au réseau.</span><span class="sxs-lookup"><span data-stu-id="c3098-239">The configuration program may confuse this value with the loopback address, and assume that the computer is not connected properly to the network.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="c3098-240">Solution</span><span class="sxs-lookup"><span data-stu-id="c3098-240">Solution</span></span>  
  
##### <a name="to-avoid-this-error-and-complete-the-configuration-process"></a><span data-ttu-id="c3098-241">Pour éviter cette erreur et de terminer le processus de configuration</span><span class="sxs-lookup"><span data-stu-id="c3098-241">To avoid this error and complete the configuration process</span></span>  
  
1.  <span data-ttu-id="c3098-242">Dans [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, atteindre C:\Windows\system32\drivers\etc et ouvrez le fichier d’hôtes à l’aide du bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="c3098-242">In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, move to C:\Windows\system32\drivers\etc, and open the hosts file using Notepad.</span></span>  
  
2.  <span data-ttu-id="c3098-243">Commentez la ligne « 127.0.0.1 localhost » en plaçant « # » au début de la ligne.</span><span class="sxs-lookup"><span data-stu-id="c3098-243">Comment out the line "127.0.0.1        localhost" by placing "# " at the start of the line.</span></span> <span data-ttu-id="c3098-244">Enregistrez le fichier hôtes modifié.</span><span class="sxs-lookup"><span data-stu-id="c3098-244">Save the changed hosts file.</span></span>  
  
3.  <span data-ttu-id="c3098-245">Cliquez sur **réessayer** dans la boîte de dialogue d’erreur.</span><span class="sxs-lookup"><span data-stu-id="c3098-245">Click **Retry** in the error dialog box.</span></span>  
  
4.  <span data-ttu-id="c3098-246">Une fois la configuration terminée, ouvrez à nouveau le fichier d’hôtes dans le bloc-notes, supprimer la marque de commentaire au début de l’hôte local mappage de ligne, puis enregistrez le fichier hosts.</span><span class="sxs-lookup"><span data-stu-id="c3098-246">After configuration has completed successfully, re-open the hosts file in Notepad, remove the comment mark at the start of the line mapping localhost, and then save the hosts file.</span></span>  
  
## <a name="you-receive-an-error-regarding-incorrect-signature-length"></a><span data-ttu-id="c3098-247">Vous recevez une erreur concernant la longueur de la signature incorrecte</span><span class="sxs-lookup"><span data-stu-id="c3098-247">You receive an error regarding incorrect signature length</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="c3098-248">Symptôme</span><span class="sxs-lookup"><span data-stu-id="c3098-248">Symptom</span></span>  
 <span data-ttu-id="c3098-249">Vous recevez l’erreur suivante ou similaire dans le journal des événements :</span><span class="sxs-lookup"><span data-stu-id="c3098-249">You receive the following or similar error in the event log:</span></span>  
  
 <span data-ttu-id="c3098-250">Échec de l’exécution du pipeline de réception : « Microsoft.Solutions.BTARN.Pipelines.Receive » Source : « Décodeur MIME/SMIME » emplacement de réception : « / BTARNHttpReceive/BTSHTTPReceive.dll?xRNResponseType=async « raison : longueur de signature incorrecte, valeur = 1935897193.</span><span class="sxs-lookup"><span data-stu-id="c3098-250">There was a failure executing the receive pipeline: "Microsoft.Solutions.BTARN.Pipelines.Receive" Source: "MIME/SMIME decoder" Receive Location: "/BTARNHttpReceive/BTSHTTPReceive.dll?xRNResponseType=async" Reason: Incorrect signature length, value = 1935897193.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="c3098-251">Cause possible</span><span class="sxs-lookup"><span data-stu-id="c3098-251">Possible Cause</span></span>  
 <span data-ttu-id="c3098-252">Ce message d’erreur indique que la longueur de la signature est incorrecte.</span><span class="sxs-lookup"><span data-stu-id="c3098-252">This error message indicates that the signature length is incorrect.</span></span> <span data-ttu-id="c3098-253">En plus de la cause ci-dessus, cette erreur pourrait être également dû à la longueur de contenu incorrecte ou incomplète en-tête prospects vers les octets incorrects de lecture sur la longueur de signature.</span><span class="sxs-lookup"><span data-stu-id="c3098-253">In addition to the above cause, this error could also due to the incorrect or incomplete header content length which leads to the wrong bytes read on the signature length.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="c3098-254">Solution</span><span class="sxs-lookup"><span data-stu-id="c3098-254">Solution</span></span>  
 <span data-ttu-id="c3098-255">Vérifiez que les deux de la longueur de la signature et la longueur de contenu d’en-tête est correct.</span><span class="sxs-lookup"><span data-stu-id="c3098-255">Verify that both of the signature length and header content length is correct.</span></span>  
  
## <a name="you-receive-503-service-unavailable-from-internet-explorer-on-64-bit-machine"></a><span data-ttu-id="c3098-256">Vous recevez « 503 : Service non disponible » à partir d’Internet Explorer sur un ordinateur 64 bits</span><span class="sxs-lookup"><span data-stu-id="c3098-256">You receive "503: Service Unavailable" from Internet Explorer on 64-bit machine</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="c3098-257">Symptôme</span><span class="sxs-lookup"><span data-stu-id="c3098-257">Symptom</span></span>  
 <span data-ttu-id="c3098-258">Après avoir [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] configuration terminée, lorsque vous essayez d’accéder à [http://localhost](http://localhost/) ou [http://localhost/BtarnApp/RnifSend.aspx](http://localhost/BtarnApp/RnifSend.aspx), vous pouvez recevoir l’erreur suivante ou similaire :</span><span class="sxs-lookup"><span data-stu-id="c3098-258">After [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] configuration is completed, when you try to access [http://localhost](http://localhost/) or [http://localhost/BtarnApp/RnifSend.aspx](http://localhost/BtarnApp/RnifSend.aspx), you may receive the following or similar error:</span></span>  
  
 <span data-ttu-id="c3098-259">503 : Service non disponible</span><span class="sxs-lookup"><span data-stu-id="c3098-259">503: Service Unavailable</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="c3098-260">Cause possible</span><span class="sxs-lookup"><span data-stu-id="c3098-260">Possible Cause</span></span>  
 <span data-ttu-id="c3098-261">Cette erreur peut être provoquée par le filtre ISAPI situé sous C:\windows\system32\rpcproxy\rpcproxy.dll définie sur les Sites Web IIS.</span><span class="sxs-lookup"><span data-stu-id="c3098-261">This error may be caused by the ISAPI filter found under C:\windows\system32\rpcproxy\rpcproxy.dll being set on IIS Web Sites.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="c3098-262">Solution</span><span class="sxs-lookup"><span data-stu-id="c3098-262">Solution</span></span>  
  
##### <a name="to-remove-rpcproxy-filter-entry-in-iis"></a><span data-ttu-id="c3098-263">Pour supprimer l’entrée de filtre RpcProxy dans IIS</span><span class="sxs-lookup"><span data-stu-id="c3098-263">To remove RpcProxy filter entry in IIS</span></span>  
  
1.  <span data-ttu-id="c3098-264">Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="c3098-264">Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="c3098-265">Développez  **\<nom de l’ordinateur\> (ordinateur local)**, avec le bouton droit **Sites Web**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="c3098-265">Expand **\<computer name\> (local computer)**, right-click **Web Sites**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="c3098-266">Sélectionnez **filtres ISAPI** onglet.</span><span class="sxs-lookup"><span data-stu-id="c3098-266">Select **ISAPI Filters** tab.</span></span>  
  
4.  <span data-ttu-id="c3098-267">Sélectionnez **RpcProxy filtre**, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="c3098-267">Select **RpcProxy filter**, and click **Remove**.</span></span>  
  
5.  <span data-ttu-id="c3098-268">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c3098-268">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="c3098-269">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c3098-269">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="c3098-270">À l’invite de commandes, tapez le code suivant pour réinitialiser IIS.</span><span class="sxs-lookup"><span data-stu-id="c3098-270">At the command prompt, type the following code to reset IIS.</span></span>  
  
    ```  
    iisreset  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="c3098-271">Si vous essayez d’accéder à http://localhost ou http://localhost/BtarnApp/RnifSend.aspx après les étapes ci-dessus, vous recevrez les messages HTTP 400 à partir d’Internet Explorer, ce qui signifie que IIS fonctionne désormais correctement.</span><span class="sxs-lookup"><span data-stu-id="c3098-271">If you try to access http://localhost or http://localhost/BtarnApp/RnifSend.aspx again after performing the above steps, you will receive HTTP 400 message back from the Internet Explorer which means that IIS is now functioning properly.</span></span>  
  
## <a name="the-hubscenario-sample-will-not-be-installed-correctly-if-the-assembly-key-files-are-not-entered-for-the-projects"></a><span data-ttu-id="c3098-272">L’exemple HubScenario ne sera pas installé correctement si les fichiers de clé d’assembly ne sont pas entrés pour les projets</span><span class="sxs-lookup"><span data-stu-id="c3098-272">The HubScenario sample will not be installed correctly if the assembly key files are not entered for the projects</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="c3098-273">Symptôme</span><span class="sxs-lookup"><span data-stu-id="c3098-273">Symptom</span></span>  
 <span data-ttu-id="c3098-274">Lorsque vous exécutez setup.bat dans  *\<lecteur\>*: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator pour RosettaNet\SDK\HubScenario configurer le L’exemple HubScenario, l’opération échoue.</span><span class="sxs-lookup"><span data-stu-id="c3098-274">When you run setup.bat in *\<drive\>*:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\HubScenario to set up the HubScenario sample, the operation fails.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="c3098-275">Cause possible</span><span class="sxs-lookup"><span data-stu-id="c3098-275">Possible Cause</span></span>  
 <span data-ttu-id="c3098-276">Les assemblys HubScenario et HubHelper ont été pas déployés correctement, car les fichiers de clé d’assembly n’ont pas été définies dans les projets.</span><span class="sxs-lookup"><span data-stu-id="c3098-276">The HubScenario and HubHelper assemblies were not deployed correctly because the assembly key files were not set in the projects.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="c3098-277">Solution</span><span class="sxs-lookup"><span data-stu-id="c3098-277">Solution</span></span>  
 <span data-ttu-id="c3098-278">Définir les fichiers de clé d’assembly pour les projets HubScenario et HubHelper.</span><span class="sxs-lookup"><span data-stu-id="c3098-278">Set the assembly key files for the HubScenario and HubHelper projects.</span></span> <span data-ttu-id="c3098-279">Pour plus d’informations, consultez [exemple HubScenario](../../adapters-and-accelerators/accelerator-rosettanet/hubscenario-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c3098-279">For more information, see [HubScenario Sample](../../adapters-and-accelerators/accelerator-rosettanet/hubscenario-sample.md).</span></span>  
  
## <a name="run-setupx64bat-to-set-up-the-double-action-pipautomation-orchestration-sample-on-sql-server-2008-r22008-sp1"></a><span data-ttu-id="c3098-280">Exécutez setupx64.bat pour installer l’exemple d’Orchestration Double Action PIPAutomation sur SQL Server 2008 R2/2008 SP1</span><span class="sxs-lookup"><span data-stu-id="c3098-280">Run setupx64.bat to set up the Double Action PIPAutomation Orchestration sample on SQL Server 2008 R2/2008 SP1</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="c3098-281">Symptôme</span><span class="sxs-lookup"><span data-stu-id="c3098-281">Symptom</span></span>  
 <span data-ttu-id="c3098-282">Lorsque vous exécutez setup.bat pour créer et initialiser l’exemple d’Orchestration Double Action PIPAutomation, la PipAutomationGetAction procédure stockée dans la base de données n’est pas créé de BTARNData.</span><span class="sxs-lookup"><span data-stu-id="c3098-282">When you run setup.bat to build and initialize the Double Action PIPAutomation Orchestration sample, the PipAutomationGetAction stored procedure in the BTARNData database is not created.</span></span>  
  
### <a name="possible-cause"></a><span data-ttu-id="c3098-283">Cause possible</span><span class="sxs-lookup"><span data-stu-id="c3098-283">Possible Cause</span></span>  
 <span data-ttu-id="c3098-284">Vous avez exécuté setup.bat sur un ordinateur 64 bits ou sur une installation de BizTalk Server est en cours d’exécution sur SQL Server 2008 R2/2008 SP1.</span><span class="sxs-lookup"><span data-stu-id="c3098-284">You ran setup.bat on a 64-bit computer or on a BizTalk Server installation that is running on SQL Server 2008 R2/2008 SP1.</span></span> <span data-ttu-id="c3098-285">Ces deux cas vous amener à exécutez setupx64.bat.</span><span class="sxs-lookup"><span data-stu-id="c3098-285">Both of these instances require you to run setupx64.bat.</span></span>  
  
### <a name="solution"></a><span data-ttu-id="c3098-286">Solution</span><span class="sxs-lookup"><span data-stu-id="c3098-286">Solution</span></span>  
 <span data-ttu-id="c3098-287">Exécutez setupx64.bat pour créer la procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="c3098-287">Run setupx64.bat to create the stored procedure.</span></span> <span data-ttu-id="c3098-288">Pour plus d’informations, consultez [Orchestration Double Action PIPAutomation](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md).</span><span class="sxs-lookup"><span data-stu-id="c3098-288">For more information, see [Double Action PIPAutomation Orchestration](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md).</span></span>  
  
## <a name="enable-the-btarn-application-pools-for-32-bit-on-windows-server-2008-64-bit-windows-operating-system-os"></a><span data-ttu-id="c3098-289">Activer les Pools d’applications BTARN pour 32 bits sur Windows Server 2008, le système d’exploitation de Windows 64 bits (OS)</span><span class="sxs-lookup"><span data-stu-id="c3098-289">Enable the BTARN Application Pools for 32 bit on Windows Server 2008, 64-bit Windows Operating System (OS)</span></span>  
 <span data-ttu-id="c3098-290">Pour exécuter le scénario de bout en bout BTARN sur Windows Server 2008,64 bits système d’exploitation (système d’exploitation Windows), Internet Information Services Manager 7.5/7.0.</span><span class="sxs-lookup"><span data-stu-id="c3098-290">To run the BTARN End to End scenario on Windows Server 2008,64-bit Windows Operating System (OS), Internet Information Services Manager 7.5/7.0.</span></span>  
  
 1. <span data-ttu-id="c3098-291">Activer les Pools d’applications BTARN pour 32 bits.</span><span class="sxs-lookup"><span data-stu-id="c3098-291">Enable the BTARN Application Pools for 32 bit.</span></span>  
  
 2. <span data-ttu-id="c3098-292">Ajoutez un gestionnaire HTTP pour \*.dll référence les filtres IsapiModule.</span><span class="sxs-lookup"><span data-stu-id="c3098-292">Add a HTTP Handler for \*.dll refering the IsapiModule Filters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3098-293">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3098-293">See Also</span></span>  
 <span data-ttu-id="c3098-294">[BtarnClean](../../adapters-and-accelerators/accelerator-rosettanet/btarnclean.md) </span><span class="sxs-lookup"><span data-stu-id="c3098-294">[BtarnClean](../../adapters-and-accelerators/accelerator-rosettanet/btarnclean.md) </span></span>  
 [<span data-ttu-id="c3098-295">Loopback</span><span class="sxs-lookup"><span data-stu-id="c3098-295">Loopback</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/loopback.md)