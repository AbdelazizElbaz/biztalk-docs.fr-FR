---
title: "Problèmes connus avec l’adaptateur FTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e58f2db-9ec5-41fe-af02-9a7d60a217db
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c12b6f1693fe475a1b123a6163a11b35fd96932
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-the-ftp-adapter"></a><span data-ttu-id="ca96a-102">Problèmes connus avec l'adaptateur FTP</span><span class="sxs-lookup"><span data-stu-id="ca96a-102">Known Issues with the FTP Adapter</span></span>
<span data-ttu-id="ca96a-103">Cette section contient des informations qui peuvent vous permettre d'éviter certaines erreurs.</span><span class="sxs-lookup"><span data-stu-id="ca96a-103">This section contains information that may help you avoid errors.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="ca96a-104">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="ca96a-104">Known Issues</span></span>  
  
#### <a name="data-may-be-duplicated-or-lost-when-you-receive-data-in-biztalk-server-by-using-the-ftp-adapter"></a><span data-ttu-id="ca96a-105">Certaines données peuvent être dupliquées ou perdues lors de la réception de données dans BizTalk Server à l'aide de l'adaptateur FTP.</span><span class="sxs-lookup"><span data-stu-id="ca96a-105">Data may be duplicated or lost when you receive data in BizTalk Server by using the FTP adapter</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="ca96a-106">Problème</span><span class="sxs-lookup"><span data-stu-id="ca96a-106">Problem</span></span>  
 <span data-ttu-id="ca96a-107">Certaines données sont dupliquées ou perdues lors de la réception de données dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'aide de l'adaptateur FTP.</span><span class="sxs-lookup"><span data-stu-id="ca96a-107">Data is duplicated or lost when you receive data in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] by using the FTP Adapter.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="ca96a-108">Cause</span><span class="sxs-lookup"><span data-stu-id="ca96a-108">Cause</span></span>  
 <span data-ttu-id="ca96a-109">L'adaptateur FTP de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise le protocole FTP client pour interroger le serveur FTP désigné et extraire des données du serveur en l'état.</span><span class="sxs-lookup"><span data-stu-id="ca96a-109">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] FTP adapter uses the FTP client protocol to poll the designated FTP server and retrieves data from the server "as is."</span></span> <span data-ttu-id="ca96a-110">L'adaptateur FTP ne valide pas les données qu'il extrait.</span><span class="sxs-lookup"><span data-stu-id="ca96a-110">The FTP adapter does not validate any data that it retrieves.</span></span> <span data-ttu-id="ca96a-111">Il transmet le document extrait au moteur de messagerie BizTalk pour traitement, puis supprime le document d'origine du serveur FTP.</span><span class="sxs-lookup"><span data-stu-id="ca96a-111">The FTP adapter sends the retrieved document to the BizTalk Messaging Engine for processing and then it deletes the original document from the FTP server.</span></span> <span data-ttu-id="ca96a-112">Si l'adaptateur FTP extrait du serveur FTP un document encore en cours d'écriture par l'application hôte, ce document sera incomplet.</span><span class="sxs-lookup"><span data-stu-id="ca96a-112">If the FTP adapter retrieves a document from the FTP server that is still being written to by the host application, the retrieved document will be incomplete.</span></span> <span data-ttu-id="ca96a-113">S'il extrait une copie incomplète du document d'origine, des données risquent d'être dupliquées ou perdues dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="ca96a-113">If the FTP adapter retrieves an incomplete copy of the original document, data duplication or data loss may occur in the following scenarios:</span></span>  
  
-   <span data-ttu-id="ca96a-114">Si le document d'origine est encore en cours d'écriture par l'application hôte sur le serveur FTP, l'adaptateur FTP ne sera pas en mesure de le supprimer et extraira une autre copie du document à l'intervalle d'interrogation suivant configuré pour l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="ca96a-114">If the original document is still being written to the FTP server by the host application, the FTP adapter cannot delete the document and will retrieve another copy of the document at the next polling interval that is configured for the receive location.</span></span> <span data-ttu-id="ca96a-115">Cela entraînera la duplication du document.</span><span class="sxs-lookup"><span data-stu-id="ca96a-115">This behavior causes document duplication to occur.</span></span>  
  
-   <span data-ttu-id="ca96a-116">Si l'application hôte a terminé d'écrire le document sur le serveur FTP, le document sera supprimé.</span><span class="sxs-lookup"><span data-stu-id="ca96a-116">If the host application has finished writing the document to the FTP server, the document will be deleted.</span></span> <span data-ttu-id="ca96a-117">Cela provoquera la perte de données.</span><span class="sxs-lookup"><span data-stu-id="ca96a-117">This behavior will cause data loss to occur.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="ca96a-118">Résolution</span><span class="sxs-lookup"><span data-stu-id="ca96a-118">Resolution</span></span>  
 <span data-ttu-id="ca96a-119">Pour contourner cette erreur, effectuez l'une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ca96a-119">To work around this behavior, use one of the following methods:</span></span>  
  
-   <span data-ttu-id="ca96a-120">Configurez l'application hôte pour qu'elle écrive dans un dossier temporaire du disque dur où réside le dossier FTP public et pour qu'elle transfère régulièrement le contenu du dossier temporaire vers le dossier FTP.</span><span class="sxs-lookup"><span data-stu-id="ca96a-120">Configure the host application to write to a temporary folder on the same hard disk as the public FTP folder and to periodically move the contents of the temporary folder to the FTP folder.</span></span> <span data-ttu-id="ca96a-121">Le dossier temporaire doit se trouver sur le même disque dur que le dossier FTP public, pour garantir une opération de transfert atomique.</span><span class="sxs-lookup"><span data-stu-id="ca96a-121">The temporary folder should be on the same hard disk as the public FTP folder to make sure that the move operation is atomic.</span></span> <span data-ttu-id="ca96a-122">Une opération atomique est une opération fonctionnelle indivisible.</span><span class="sxs-lookup"><span data-stu-id="ca96a-122">An atomic operation is an operation that is functionally indivisible.</span></span> <span data-ttu-id="ca96a-123">Si vous écrivez des données dans le dossier FTP public avec l'adaptateur FTP de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez spécifier une propriété de dossier temporaire dans la boîte de dialogue Propriétés du transport FTP lors de la configuration du port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="ca96a-123">If you write data to the public FTP folder by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] FTP adapter, you can do this by specifying a Temporary Folder property in the FTP Transport Properties dialog box when you configure a send port.</span></span> <span data-ttu-id="ca96a-124">Dans ce cas, assurez-vous que ce dossier réside sur le même disque physique que le dossier FTP public.</span><span class="sxs-lookup"><span data-stu-id="ca96a-124">If you specify a Temporary Folder property, make sure that this folder is on the same physical disk as the public FTP folder.</span></span>  
  
-   <span data-ttu-id="ca96a-125">Configurez l'emplacement de réception FTP pour qu'il fonctionne dans une fenêtre de service lorsque l'application hôte n'écrit pas de données vers le serveur FTP.</span><span class="sxs-lookup"><span data-stu-id="ca96a-125">Configure the FTP receive location to operate within a service window when the host application is not writing data to the FTP server.</span></span> <span data-ttu-id="ca96a-126">Vous pouvez configurer cette fenêtre lors de la configuration des propriétés de l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="ca96a-126">You can specify the service window when you configure the receive location properties.</span></span>  
  
#### <a name="ftp-adapter-does-not-support-revocation-checks-on-the-server-certificates"></a><span data-ttu-id="ca96a-127">L'adaptateur FTP ne prend pas en charge les vérifications de révocation sur les certificats de serveur</span><span class="sxs-lookup"><span data-stu-id="ca96a-127">FTP Adapter does not support revocation checks on the server certificates</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="ca96a-128">Problème</span><span class="sxs-lookup"><span data-stu-id="ca96a-128">Problem</span></span>  
 <span data-ttu-id="ca96a-129">L'adaptateur FTP dans [!INCLUDE[prague](../includes/prague-md.md)] a été amélioré de manière à prendre en charge le transfert (envoi et réception) de fichiers sécurisé sur un serveur FTPS via SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="ca96a-129">The FTP adapter in [!INCLUDE[prague](../includes/prague-md.md)] is enhanced to support secure file transfer to and from an FTPS server using SSL/TLS.</span></span> <span data-ttu-id="ca96a-130">La liste de révocation des certificats contient une liste des certificats qui ont été révoqués et ne sont plus valides.</span><span class="sxs-lookup"><span data-stu-id="ca96a-130">The Certificate Revocation List (CRL) contains a list of certificates that have been revoked and are no longer valid.</span></span> <span data-ttu-id="ca96a-131">L'adaptateur FTP ne consulte pas cette liste pour authentifier le certificat de serveur.</span><span class="sxs-lookup"><span data-stu-id="ca96a-131">The FTP adapter does not consult the CRL for authenticating the server certificate.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="ca96a-132">Cause</span><span class="sxs-lookup"><span data-stu-id="ca96a-132">Cause</span></span>  
 <span data-ttu-id="ca96a-133">Par défaut, l'adaptateur FTP ne consulte pas la liste de révocation des certificats avant d'accepter un certificat de serveur.</span><span class="sxs-lookup"><span data-stu-id="ca96a-133">By design, the FTP adapter does not consult the CRL before accepting a server certificate.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="ca96a-134">Résolution</span><span class="sxs-lookup"><span data-stu-id="ca96a-134">Resolution</span></span>  
 <span data-ttu-id="ca96a-135">Aucune action n’est requise ; Ce comportement est normal.</span><span class="sxs-lookup"><span data-stu-id="ca96a-135">No action is required; this behavior is by design.</span></span>  
  
#### <a name="ftp-adapter-downloads-files-larger-than-max-file-size"></a><span data-ttu-id="ca96a-136">L'adaptateur FTP télécharge les fichiers dont la taille est supérieure à la taille de fichier maximale</span><span class="sxs-lookup"><span data-stu-id="ca96a-136">FTP Adapter downloads files larger than Max File Size</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="ca96a-137">Problème</span><span class="sxs-lookup"><span data-stu-id="ca96a-137">Problem</span></span>  
 <span data-ttu-id="ca96a-138">L'adaptateur de réception FTP télécharge les fichiers dont la taille est supérieure à la valeur de la propriété Taille maximale des fichiers des serveurs FTP suivants :</span><span class="sxs-lookup"><span data-stu-id="ca96a-138">The FTP receive adapter downloads files whose size is larger than the specified Max File Size property from the following FTP servers:</span></span>  
  
-   <span data-ttu-id="ca96a-139">AIX</span><span class="sxs-lookup"><span data-stu-id="ca96a-139">AIX</span></span>  
  
-   <span data-ttu-id="ca96a-140">MVS</span><span class="sxs-lookup"><span data-stu-id="ca96a-140">MVS</span></span>  
  
-   <span data-ttu-id="ca96a-141">AS400</span><span class="sxs-lookup"><span data-stu-id="ca96a-141">AS400</span></span>  
  
-   <span data-ttu-id="ca96a-142">GXS</span><span class="sxs-lookup"><span data-stu-id="ca96a-142">GXS</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="ca96a-143">Cause</span><span class="sxs-lookup"><span data-stu-id="ca96a-143">Cause</span></span>  
 <span data-ttu-id="ca96a-144">Par défaut, l'adaptateur FTP ne respecte pas la taille maximale des fichiers lors du téléchargement de fichiers à partir de ces serveurs FTP.</span><span class="sxs-lookup"><span data-stu-id="ca96a-144">By design, the FTP adapter does not respect the maximum file size when downloading files from these FTP servers.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="ca96a-145">Résolution</span><span class="sxs-lookup"><span data-stu-id="ca96a-145">Resolution</span></span>  
 <span data-ttu-id="ca96a-146">Aucune action n’est requise ; Ce comportement est normal.</span><span class="sxs-lookup"><span data-stu-id="ca96a-146">No action is required; this behavior is by design.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca96a-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca96a-147">See Also</span></span>  
 <span data-ttu-id="ca96a-148">[Pour configurer les emplacement de réception FTP](http://msdn.microsoft.com/library/1d8fde35-f787-4a5e-a8bd-8c418d0f75c3) </span><span class="sxs-lookup"><span data-stu-id="ca96a-148">[How to Configure an FTP Receive Location](http://msdn.microsoft.com/library/1d8fde35-f787-4a5e-a8bd-8c418d0f75c3) </span></span>  
 [<span data-ttu-id="ca96a-149">Dépannage de l’adaptateur FTP</span><span class="sxs-lookup"><span data-stu-id="ca96a-149">Troubleshooting the FTP Adapter</span></span>](../core/troubleshooting-the-ftp-adapter.md)