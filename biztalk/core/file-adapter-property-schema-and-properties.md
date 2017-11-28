---
title: "Propriétés et schéma de propriété de l’adaptateur file | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [File adapters], properties
- schemas, File adapters
- File adapters, schemas
- Password property [File adapters]
- ReceivedFileName property [File adapters]
- configuring [File adapters], schemas
- CopyMode property [File adapters]
- AllowCacheOnWrite property [File adapters]
- FileCreationTime property [File adapters]
- UserName property, File adapters
- File adapters, properties
- UserName property
ms.assetid: c5ae5339-67bf-4fde-a721-5b1aa3b9caca
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37e1c6860b002b41555337a0bf7e8cb931f2c2bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="file-adapter-property-schema-and-properties"></a><span data-ttu-id="b6c41-102">Propriétés et schéma de propriété de l’adaptateur de fichier</span><span class="sxs-lookup"><span data-stu-id="b6c41-102">File adapter property schema and properties</span></span>
<span data-ttu-id="b6c41-103">Le tableau suivant répertorie les propriétés du schéma de propriété de l'adaptateur FILE.</span><span class="sxs-lookup"><span data-stu-id="b6c41-103">The following table contains the properties in the File adapter property schema.</span></span>  
  
 <span data-ttu-id="b6c41-104">**Namespace :** http://schemas.microsoft.com/BizTalk/2003/file-properties</span><span class="sxs-lookup"><span data-stu-id="b6c41-104">**Namespace:** http://schemas.microsoft.com/BizTalk/2003/file-properties</span></span>  
  
|<span data-ttu-id="b6c41-105">Nom</span><span class="sxs-lookup"><span data-stu-id="b6c41-105">Name</span></span>|<span data-ttu-id="b6c41-106">Type</span><span class="sxs-lookup"><span data-stu-id="b6c41-106">Type</span></span>|<span data-ttu-id="b6c41-107"> Description</span><span class="sxs-lookup"><span data-stu-id="b6c41-107">Description</span></span>|  
|----------|----------|-----------------|  
|<span data-ttu-id="b6c41-108">**CopyMode**</span><span class="sxs-lookup"><span data-stu-id="b6c41-108">**CopyMode**</span></span>|<span data-ttu-id="b6c41-109">xs:unsignedInt</span><span class="sxs-lookup"><span data-stu-id="b6c41-109">xs:unsignedInt</span></span>|<span data-ttu-id="b6c41-110">Définit le mode de copie à utiliser lors de l'écriture d'un message dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="b6c41-110">Defines the copy mode to use when writing a message to a file.</span></span> <span data-ttu-id="b6c41-111">Les valeurs valides sont :</span><span class="sxs-lookup"><span data-stu-id="b6c41-111">Valid values are:</span></span><br /><br /> <span data-ttu-id="b6c41-112">**Ajouter (0).**</span><span class="sxs-lookup"><span data-stu-id="b6c41-112">**Append (0).**</span></span> <span data-ttu-id="b6c41-113">le gestionnaire d'envoi FILE ouvre un fichier s'il existe et ajoute un message à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="b6c41-113">The File send handler opens a file if it exists and appends a message to the end of the file.</span></span> <span data-ttu-id="b6c41-114">Si le fichier n'existe pas, il le crée.</span><span class="sxs-lookup"><span data-stu-id="b6c41-114">If the file does not exist, the File send handler creates a new file.</span></span><br /><br /> <span data-ttu-id="b6c41-115">**Créer (1).**</span><span class="sxs-lookup"><span data-stu-id="b6c41-115">**Create new (1).**</span></span> <span data-ttu-id="b6c41-116">si aucun fichier n'existe, le gestionnaire d'envoi FILE en crée un et y enregistre des éléments.</span><span class="sxs-lookup"><span data-stu-id="b6c41-116">If a file does not exist, the File send handler creates a new file and writes to it.</span></span> <span data-ttu-id="b6c41-117">si le fichier existe déjà, il signale une erreur et applique la procédure logique commune pour les nouvelles tentatives sur l'adaptateur pour les ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="b6c41-117">If the file already exists, the File send handler reports an error and then follows common adapter retry logic for send ports.</span></span> <span data-ttu-id="b6c41-118">Il s'agit d'un mode de copie par défaut pour le gestionnaire d'envoi FILE.</span><span class="sxs-lookup"><span data-stu-id="b6c41-118">This is a default copy mode for the File send handler.</span></span><br /><br /> <span data-ttu-id="b6c41-119">**Remplacer (2).**</span><span class="sxs-lookup"><span data-stu-id="b6c41-119">**Overwrite (2).**</span></span> <span data-ttu-id="b6c41-120">le gestionnaire d'envoi FILE ouvre un fichier s'il existe et remplace son contenu.</span><span class="sxs-lookup"><span data-stu-id="b6c41-120">The File send handler opens a file if it exists and overwrites its content.</span></span> <span data-ttu-id="b6c41-121">Si le fichier n'existe pas, il le crée.</span><span class="sxs-lookup"><span data-stu-id="b6c41-121">If the file does not exist, the File send handler creates a new file.</span></span>|  
|<span data-ttu-id="b6c41-122">**AllowCacheOnWrite**</span><span class="sxs-lookup"><span data-stu-id="b6c41-122">**AllowCacheOnWrite**</span></span>|<span data-ttu-id="b6c41-123">xs:Boolean</span><span class="sxs-lookup"><span data-stu-id="b6c41-123">xs:Boolean</span></span>|<span data-ttu-id="b6c41-124">Précise si l'adaptateur FILE utilise la mise en cache du système de fichiers lors de l'écriture de messages dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="b6c41-124">Defines whether the File adapter uses file system caching when writing messages to a file.</span></span>|  
|<span data-ttu-id="b6c41-125">**ReceivedFileName**</span><span class="sxs-lookup"><span data-stu-id="b6c41-125">**ReceivedFileName**</span></span>|<span data-ttu-id="b6c41-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="b6c41-126">xs:string</span></span>|<span data-ttu-id="b6c41-127">Définit le nom complet du fichier à partir duquel l'adaptateur FILE lit le message.</span><span class="sxs-lookup"><span data-stu-id="b6c41-127">Defines the full name of the file from which the File adapter reads the message.</span></span>|  
|<span data-ttu-id="b6c41-128">**FileCreationTime**</span><span class="sxs-lookup"><span data-stu-id="b6c41-128">**FileCreationTime**</span></span>|<span data-ttu-id="b6c41-129">xs:datetime</span><span class="sxs-lookup"><span data-stu-id="b6c41-129">xs:datetime</span></span>|<span data-ttu-id="b6c41-130">Définit l'heure à laquelle le fichier a été écrit dans le dossier surveillé par l'adaptateur de réception FILE.</span><span class="sxs-lookup"><span data-stu-id="b6c41-130">Defines the time that the file was written to the folder that is monitored by the File receive adapter.</span></span>|  
|<span data-ttu-id="b6c41-131">**Nom d’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="b6c41-131">**Username**</span></span>|<span data-ttu-id="b6c41-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="b6c41-132">xs:string</span></span>|<span data-ttu-id="b6c41-133">Définit le nom d'utilisateur du compte utilisé lors de la spécification d'autres informations d'identification pour accéder à un partage réseau.</span><span class="sxs-lookup"><span data-stu-id="b6c41-133">Defines the user name for the account used when specifying alternative credentials to access a network share.</span></span>|  
|<span data-ttu-id="b6c41-134">**Mot de passe**</span><span class="sxs-lookup"><span data-stu-id="b6c41-134">**Password**</span></span>|<span data-ttu-id="b6c41-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="b6c41-135">xs:string</span></span>|<span data-ttu-id="b6c41-136">Définit le mot de passe du compte utilisé lors de la spécification d'autres informations d'identification pour accéder à un partage réseau.</span><span class="sxs-lookup"><span data-stu-id="b6c41-136">Defines the password for the account used when specifying alternative credentials to access a network share.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b6c41-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6c41-137">See Also</span></span>  
 [<span data-ttu-id="b6c41-138">Configuration de l’adaptateur de fichier</span><span class="sxs-lookup"><span data-stu-id="b6c41-138">Configuring the File Adapter</span></span>](../core/configure-the-file-adapter.md)