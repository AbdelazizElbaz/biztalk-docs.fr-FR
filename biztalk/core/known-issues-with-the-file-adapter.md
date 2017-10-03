---
title: "Problèmes connus avec l’adaptateur File | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aaf448c-0035-4648-910b-ae2f15106342
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2690803346efc5931a88acd70be9d24af107156f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-the-file-adapter"></a><span data-ttu-id="83215-102">Problèmes connus avec l'adaptateur FILE</span><span class="sxs-lookup"><span data-stu-id="83215-102">Known Issues with the File Adapter</span></span>
<span data-ttu-id="83215-103">Cette section contient des informations qui peuvent vous permettre d'éviter certaines erreurs.</span><span class="sxs-lookup"><span data-stu-id="83215-103">This section contains information that may help you avoid errors.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="83215-104">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="83215-104">Known Issues</span></span>  
  
#### <a name="a-file-receive-location-is-disabled"></a><span data-ttu-id="83215-105">Un emplacement de réception de fichier est désactivé</span><span class="sxs-lookup"><span data-stu-id="83215-105">A File Receive Location is Disabled</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="83215-106">Problème</span><span class="sxs-lookup"><span data-stu-id="83215-106">Problem</span></span>  
 <span data-ttu-id="83215-107">Un emplacement de réception de fichier devient désactivé.</span><span class="sxs-lookup"><span data-stu-id="83215-107">A File receive location becomes disabled.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="83215-108">Cause</span><span class="sxs-lookup"><span data-stu-id="83215-108">Cause</span></span>  
 <span data-ttu-id="83215-109">L'adaptateur de réception FILE désactive l'emplacement de réception si l'un des cas suivants se présente :</span><span class="sxs-lookup"><span data-stu-id="83215-109">The File receive adapter disables the receive location if any of the following occur:</span></span>  
  
-   <span data-ttu-id="83215-110">L'adaptateur de réception FILE ne peut pas accéder à l'emplacement de réception sur le système de fichiers ou le partage réseau, car le chemin spécifié n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="83215-110">The File receive adapter cannot access the receive location on the file system or network share because the specified path does not exist.</span></span> <span data-ttu-id="83215-111">Pour un partage réseau, l'adaptateur de réception FILE désactive l'emplacement de réception lorsque le nombre de tentatives maximal est atteint.</span><span class="sxs-lookup"><span data-stu-id="83215-111">For a network share, the File receive adapter disables the receive location after all retry attempts have been exhausted.</span></span>  
  
-   <span data-ttu-id="83215-112">L'adaptateur de réception FILE ne peut pas accéder à l'emplacement de réception sur le système de fichiers ou le partage réseau, car le compte utilisé par l'instance d'hôte associée ne dispose pas des autorisations en lecture/écriture pour cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="83215-112">The File receive adapter cannot access the receive location on the file system or network share because the account used by the associated host instance does not have read-write permission for that location.</span></span> <span data-ttu-id="83215-113">Pour un partage réseau, l'adaptateur de réception FILE désactive l'emplacement de réception lorsque le nombre de tentatives maximal est atteint.</span><span class="sxs-lookup"><span data-stu-id="83215-113">For a network share, the File receive adapter disables the receive location after all retry attempts have been exhausted.</span></span>  
  
-   <span data-ttu-id="83215-114">Des noms de fichier comportant plus de 256 caractères sont présents dans l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="83215-114">Files with names longer than 256 characters are encountered in the receive location.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="83215-115">Résolution</span><span class="sxs-lookup"><span data-stu-id="83215-115">Resolution</span></span>  
  
-   <span data-ttu-id="83215-116">Assurez-vous que le chemin ou le partage spécifié existe bien.</span><span class="sxs-lookup"><span data-stu-id="83215-116">Ensure that the specified path or share exists.</span></span>  
  
-   <span data-ttu-id="83215-117">Vérifiez que le compte utilisé comme le **ouverture de session :** compte pour le fichier instance hôte du Gestionnaire de réception est en lecture et écriture spécifiée à l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="83215-117">Ensure that the account used as the **Logon:** account for the File receive handler host instance has read and write permissions to the specified receive location.</span></span>  
  
-   <span data-ttu-id="83215-118">Assurez-vous que les noms des fichiers écrits dans le dossier contrôlé par l'adaptateur de réception FILE n'excèdent pas 256 caractères.</span><span class="sxs-lookup"><span data-stu-id="83215-118">Ensure that files written to the folder monitored by the File receive adapter do not have file names exceeding 256 characters.</span></span>  
  
#### <a name="files-are-not-being-read-from-the-specified-receive-location"></a><span data-ttu-id="83215-119">Les fichiers ne sont pas lus à partir de l'emplacement de réception spécifié</span><span class="sxs-lookup"><span data-stu-id="83215-119">Files Are Not Being Read from the Specified Receive Location</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="83215-120">Problème</span><span class="sxs-lookup"><span data-stu-id="83215-120">Problem</span></span>  
 <span data-ttu-id="83215-121">L'adaptateur de réception FILE ne parvient pas à lire un fichier dans l'emplacement de réception indiqué.</span><span class="sxs-lookup"><span data-stu-id="83215-121">The File receive adapter does not read a file from the specified receive location.</span></span> <span data-ttu-id="83215-122">Lorsque l'adaptateur de réception FILE rencontre un tel fichier, il consigne une erreur dans le journal des événements et laisse le fichier dans l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="83215-122">When the File receive adapter encounters such a file, it logs an error in the event log and leaves the file in the receive location.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="83215-123">Cause</span><span class="sxs-lookup"><span data-stu-id="83215-123">Cause</span></span>  
 <span data-ttu-id="83215-124">L'adaptateur de réception FILE ne lit pas un fichier dans l'emplacement de réception si l'une des conditions suivantes est vraie :</span><span class="sxs-lookup"><span data-stu-id="83215-124">The File receive adapter does not read a file from the receive location if any of the following conditions are true:</span></span>  
  
-   <span data-ttu-id="83215-125">Le fichier est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="83215-125">The file is read-only.</span></span>  
  
-   <span data-ttu-id="83215-126">Le fichier comporte un attribut système.</span><span class="sxs-lookup"><span data-stu-id="83215-126">The file has a system attribute.</span></span>  
  
-   <span data-ttu-id="83215-127">L'adaptateur de réception FILE ne dispose pas des autorisations en lecture/écriture pour le fichier.</span><span class="sxs-lookup"><span data-stu-id="83215-127">The File receive adapter does not have permissions to read and write to the file.</span></span>  
  
-   <span data-ttu-id="83215-128">Des noms de fichier comportant plus de 256 caractères sont présents dans l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="83215-128">Files with names longer than 256 characters are encountered in the receive location.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="83215-129">Résolution</span><span class="sxs-lookup"><span data-stu-id="83215-129">Resolution</span></span>  
  
-   <span data-ttu-id="83215-130">Assurez-vous que les fichiers de l'emplacement de réception spécifié ne sont pas marqués en « lecture seule ».</span><span class="sxs-lookup"><span data-stu-id="83215-130">Ensure that the files in the specified receive location are not marked as "read only".</span></span>  
  
-   <span data-ttu-id="83215-131">Assurez-vous que les fichiers de l'emplacement de réception spécifié ne sont pas marqués avec un attribut système.</span><span class="sxs-lookup"><span data-stu-id="83215-131">Ensure that the files in the specified receive location are not marked with a system attribute.</span></span>  
  
-   <span data-ttu-id="83215-132">Vérifiez que le compte utilisé comme le **ouverture de session :** compte pour le fichier instance hôte du Gestionnaire de réception est en lecture et écriture spécifiée à l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="83215-132">Ensure that the account used as the **Logon:** account for the File receive handler host instance has read and write permissions to the specified receive location.</span></span>  
  
-   <span data-ttu-id="83215-133">Assurez-vous que les noms des fichiers écrits dans le dossier contrôlé par l'adaptateur de réception FILE n'excèdent pas 256 caractères.</span><span class="sxs-lookup"><span data-stu-id="83215-133">Ensure that files written to the folder monitored by the File receive adapter do not have file names exceeding 256 characters.</span></span>  
  
#### <a name="messages-are-not-being-sent-by-the-file-send-adapter"></a><span data-ttu-id="83215-134">Messages non envoyés par l'adaptateur d'envoi FILE.</span><span class="sxs-lookup"><span data-stu-id="83215-134">Messages Are Not Being Sent by the File Send Adapter</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="83215-135">Problème</span><span class="sxs-lookup"><span data-stu-id="83215-135">Problem</span></span>  
 <span data-ttu-id="83215-136">L'adaptateur d'envoi FILE ne parvient pas à envoyer un message dans le répertoire ou le partage de fichiers spécifié.</span><span class="sxs-lookup"><span data-stu-id="83215-136">The File send adapter fails to send a message to the specified directory or file share.</span></span>  
  
 <span data-ttu-id="83215-137">En cas d'échec de l'écriture d'un message dans le répertoire ou le partage de fichiers spécifié, une erreur est consignée dans le journal des événements de l'ordinateur BizTalk Server et la séquence d'événements suivante se produit :</span><span class="sxs-lookup"><span data-stu-id="83215-137">If a message fails to be written to the specified directory or file share, an error is written to the Event log of the BizTalk server computer and the following sequence of events occurs:</span></span>  
  
1.  <span data-ttu-id="83215-138">L'adaptateur d'envoi FILE tente à nouveau l'opération d'écriture.</span><span class="sxs-lookup"><span data-stu-id="83215-138">The File send adapter will retry the write operation.</span></span>  
  
2.  <span data-ttu-id="83215-139">L'adaptateur d'envoi FILE tente de remettre le fichier en faisant appel au transport secondaire (s'il a été configuré).</span><span class="sxs-lookup"><span data-stu-id="83215-139">The File adapter will attempt to deliver the file using the backup transport (if configured).</span></span>  
  
3.  <span data-ttu-id="83215-140">Le message est écrit dans la file d'attente des messages interrompus.</span><span class="sxs-lookup"><span data-stu-id="83215-140">The message will be written to the suspended queue.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="83215-141">Cause</span><span class="sxs-lookup"><span data-stu-id="83215-141">Cause</span></span>  
  
-   <span data-ttu-id="83215-142">L'adaptateur d'envoi FILE ne peut pas accéder au répertoire à partir duquel les fichiers sont envoyés sur le système de fichiers ou le partage réseau, car le chemin spécifié n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="83215-142">The File send adapter cannot access the directory that files are sent from on the file system or network share because the specified path does not exist.</span></span>  
  
-   <span data-ttu-id="83215-143">L'adaptateur d'envoi FILE ne peut pas écrire dans un fichier dans l'emplacement de destination sur le système de fichiers ou le partage réseau, car l'instance de l'hôte associée ne dispose pas des autorisations en écriture pour ce fichier ou cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="83215-143">The File send adapter cannot write to a file in the destination location on the file system or network share because the associated host instance does not have write permissions for that file or for that location.</span></span>  
  
-   <span data-ttu-id="83215-144">L’adaptateur d’envoi de fichier ne peut pas écrire dans le fichier spécifié, car il est en lecture seule ou est marqué avec la **système** attribut de fichier.</span><span class="sxs-lookup"><span data-stu-id="83215-144">The File send adapter cannot write to the file specified because it is read-only or is marked with the **system** file attribute.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="83215-145">Résolution</span><span class="sxs-lookup"><span data-stu-id="83215-145">Resolution</span></span>  
  
-   <span data-ttu-id="83215-146">Assurez-vous que le chemin ou le partage spécifié existe bien.</span><span class="sxs-lookup"><span data-stu-id="83215-146">Ensure that the specified path or share exists.</span></span>  
  
-   <span data-ttu-id="83215-147">Vérifiez que le compte utilisé comme le **ouverture de session :** compte pour l’instance de hôte du Gestionnaire d’envoi de fichier a autorisations Lire et écrire sur le partage de fichier ou répertoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="83215-147">Ensure that the account used as the **Logon:** account for the File send handler host instance has read and write permissions to the specified directory or file share.</span></span>  
  
-   <span data-ttu-id="83215-148">Assurez-vous que les fichiers existants dans le répertoire ou le partage de fichiers indiqué ne sont pas marqués avec un attribut système.</span><span class="sxs-lookup"><span data-stu-id="83215-148">Ensure that existing files in the specified directory or file share are not marked with the system attribute.</span></span>  
  
#### <a name="sending-a-file-using-the-file-adapter-is-very-slow"></a><span data-ttu-id="83215-149">L'envoi d'un fichier avec l'adaptateur FILE est très lent.</span><span class="sxs-lookup"><span data-stu-id="83215-149">Sending a file using the File adapter is very slow</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="83215-150">Problème</span><span class="sxs-lookup"><span data-stu-id="83215-150">Problem</span></span>  
 <span data-ttu-id="83215-151">Performances de l’adaptateur d’envoi de fichier est plus lent lorsque la **autoriser le cache lors de l’écriture** est définie sur **False**.</span><span class="sxs-lookup"><span data-stu-id="83215-151">Performance of the File send adapter is slower when the **Allow cache on write** property is set to **False**.</span></span> <span data-ttu-id="83215-152">Le **autoriser le cache lors de l’écriture** est définie sur **False** par défaut.</span><span class="sxs-lookup"><span data-stu-id="83215-152">The **Allow cache on write** property is set to **False** by default.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="83215-153">Cause</span><span class="sxs-lookup"><span data-stu-id="83215-153">Cause</span></span>  
 <span data-ttu-id="83215-154">Définition de la **autoriser le cache lors de l’écriture** propriété **False** peut réduire les performances car ce paramètre désactive l’utilisation de la mise en cache de fichiers par le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="83215-154">Setting the **Allow cache on write** property to **False** can reduce performance as this setting disallows the use of in-memory caching of files by the operating system.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="83215-155">Résolution</span><span class="sxs-lookup"><span data-stu-id="83215-155">Resolution</span></span>  
 <span data-ttu-id="83215-156">Pour augmenter les performances du fichier envoyer la modification de l’adaptateur le **autoriser le cache lors de l’écriture** propriété **True** (cochez la case).</span><span class="sxs-lookup"><span data-stu-id="83215-156">To increase performance of the File send adapter change the **Allow cache on write** property to **True** (check the box).</span></span> <span data-ttu-id="83215-157">Pour plus d’informations sur la **autoriser le cache lors de l’écriture** propriété, consultez [comment configurer un Port d’envoi File](http://msdn.microsoft.com/library/d801c5b7-da0a-4228-af0c-c2d450c251a9).</span><span class="sxs-lookup"><span data-stu-id="83215-157">For more information about the **Allow cache on write** property, see [How to Configure a File Send Port](http://msdn.microsoft.com/library/d801c5b7-da0a-4228-af0c-c2d450c251a9).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83215-158">Définition de la **autoriser le cache lors de l’écriture** propriété **True** augmente le risque de perte de données dans le cas où le système d’exploitation rencontre un échec.</span><span class="sxs-lookup"><span data-stu-id="83215-158">Setting the **Allow cache on write** property to **True** increases the possibility of data loss in the event that the operating system experiences a failure.</span></span> <span data-ttu-id="83215-159">Dans cette situation, toutes les données stockées dans le cache des fichiers en mémoire seraient perdues.</span><span class="sxs-lookup"><span data-stu-id="83215-159">In this scenario, any data that is stored in the in-memory file cache will be lost.</span></span>  
  
#### <a name="zero-byte-files-received-by-the-file-adapter-are-deleted"></a><span data-ttu-id="83215-160">Les fichiers de zéro octet reçus par l'adaptateur FILE sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="83215-160">Zero byte files received by the File adapter are deleted</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="83215-161">Problème</span><span class="sxs-lookup"><span data-stu-id="83215-161">Problem</span></span>  
 <span data-ttu-id="83215-162">Si l'adaptateur de réception FILE reçoit un fichier vide (zéro octet), ce fichier est supprimé et un avertissement similaire à l'avertissement suivant est écrit dans le journal des applications du serveur BizTalk :</span><span class="sxs-lookup"><span data-stu-id="83215-162">If an empty (zero byte) file is picked up by the File receive adapter, the file is deleted and a warning similar to the following is written to the application log of the BizTalk server:</span></span>  
  
```  
Event Type:Warning  
Event Source:BizTalk Server 2009  
Event Category:BizTalk Server 2009   
Event ID:7182  
Date:8/30/2006  
Time:1:32:32 PM  
User:N/A  
Computer:BIZTALKSERVER  
Description:  
The FILE receive adapter deleted the empty file "C:\filesource\emptyfile.xml.BTS-WIP" without performing any processing.  
```  
  
##### <a name="cause"></a><span data-ttu-id="83215-163">Cause</span><span class="sxs-lookup"><span data-stu-id="83215-163">Cause</span></span>  
 <span data-ttu-id="83215-164">Le comportement normal de l'adaptateur de réception FILE est de supprimer les fichiers de zéro octet.</span><span class="sxs-lookup"><span data-stu-id="83215-164">The File receive adapter deletes zero byte files by design.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="83215-165">Résolution</span><span class="sxs-lookup"><span data-stu-id="83215-165">Resolution</span></span>  
 <span data-ttu-id="83215-166">Aucune action n'est requise, ce comportement est normal.</span><span class="sxs-lookup"><span data-stu-id="83215-166">No action is required, this behavior is by design.</span></span>