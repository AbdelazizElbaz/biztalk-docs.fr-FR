---
title: "Créer par programme le fichier de port d’envoi ou emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 558a414c-60bc-4f62-9397-a023ed4937fb
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 92737ca115e95c5cd66fdf0e03cf05296ef16088
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="programmatically-create-the-file-receive-location-or-send-port"></a><span data-ttu-id="be2d4-102">Créer par programme le fichier de l’emplacement de réception ou port d’envoi</span><span class="sxs-lookup"><span data-stu-id="be2d4-102">Programmatically create the File receive location or send port</span></span>
<span data-ttu-id="be2d4-103">Comment créer un fichier de port de réception et le port d’envoi par programme.</span><span class="sxs-lookup"><span data-stu-id="be2d4-103">How to create a File receive port and send port programmatically.</span></span> <span data-ttu-id="be2d4-104">Pour utiliser le [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], accédez à [configurer l’adaptateur File](../core/configure-the-file-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="be2d4-104">To use the [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], go to [Configure the File adapter](../core/configure-the-file-adapter.md).</span></span>

<span data-ttu-id="be2d4-105">L'adaptateur FILE stocke ses informations de configuration dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="be2d4-105">The File adapter stores its configuration information in the SSO database.</span></span> <span data-ttu-id="be2d4-106">Vous pouvez configurer les emplacements de réception et le modèle objet de programmation à l’aide de l’Explorateur BizTalk de ports d’envoi.</span><span class="sxs-lookup"><span data-stu-id="be2d4-106">You can configure the receive locations and send ports programmatically using the BizTalk Explorer object model.</span></span> 
 
## <a name="create-the-receive-location"></a><span data-ttu-id="be2d4-107">Pour créer un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="be2d4-107">Create the receive location</span></span>

<span data-ttu-id="be2d4-108">Le modèle d’objet de l’Explorateur BizTalk expose le **IReceiveLocation** interface de configuration qui contient la **TransportTypeData** propriété en lecture/écriture.</span><span class="sxs-lookup"><span data-stu-id="be2d4-108">The BizTalk Explorer object model exposes the **IReceiveLocation** configuration interface that contains the **TransportTypeData** read/write property.</span></span> <span data-ttu-id="be2d4-109">Cette propriété accepte le jeu de propriétés de configuration de l'emplacement de réception FILE sous la forme d'une chaîne XML composée d'une paire nom/valeur.</span><span class="sxs-lookup"><span data-stu-id="be2d4-109">This property accepts the File receive location configuration property bag in the form of a name/value pair XML string.</span></span>  
  
<span data-ttu-id="be2d4-110">Le **TransportTypeData** propriété de la **IReceiveLocation** interface n’a pas à définir.</span><span class="sxs-lookup"><span data-stu-id="be2d4-110">The **TransportTypeData** property of the **IReceiveLocation** interface does not have to be set.</span></span> <span data-ttu-id="be2d4-111">Si elle n'est pas définie, les valeurs par défaut de configuration de l'emplacement de réception FILE sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="be2d4-111">If it is not set, default values for the File receive location configuration are used.</span></span>  
  
 <span data-ttu-id="be2d4-112">Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir pour l'emplacement de réception FILE.</span><span class="sxs-lookup"><span data-stu-id="be2d4-112">The following table lists the configuration properties that you can set programmatically for the File receive location.</span></span>  
  
|<span data-ttu-id="be2d4-113">Nom de la propriété</span><span class="sxs-lookup"><span data-stu-id="be2d4-113">Property name</span></span>|<span data-ttu-id="be2d4-114">Type</span><span class="sxs-lookup"><span data-stu-id="be2d4-114">Type</span></span>|<span data-ttu-id="be2d4-115"> Description</span><span class="sxs-lookup"><span data-stu-id="be2d4-115">Description</span></span>|<span data-ttu-id="be2d4-116">Restrictions</span><span class="sxs-lookup"><span data-stu-id="be2d4-116">Restrictions</span></span>|<span data-ttu-id="be2d4-117">Commentaires</span><span class="sxs-lookup"><span data-stu-id="be2d4-117">Comments</span></span>|  
|-------------------|----------|-----------------|------------------|--------------|  
|<span data-ttu-id="be2d4-118">**FileNetFailRetryCount**</span><span class="sxs-lookup"><span data-stu-id="be2d4-118">**FileNetFailRetryCount**</span></span>|<span data-ttu-id="be2d4-119">Long</span><span class="sxs-lookup"><span data-stu-id="be2d4-119">Long</span></span>|<span data-ttu-id="be2d4-120">Nombre de tentatives d'accès à l'emplacement de réception sur le partage réseau en cas d'indisponibilité temporaire.</span><span class="sxs-lookup"><span data-stu-id="be2d4-120">The number of attempts to access the receive location on the network share if it is temporarily unavailable.</span></span>|<span data-ttu-id="be2d4-121">Entier</span><span class="sxs-lookup"><span data-stu-id="be2d4-121">Integer</span></span><br /><br /> <span data-ttu-id="be2d4-122">Valeur minimale : 0</span><span class="sxs-lookup"><span data-stu-id="be2d4-122">Minimum value: 0</span></span><br /><br /> <span data-ttu-id="be2d4-123">Valeur maximale : MAX_LONG</span><span class="sxs-lookup"><span data-stu-id="be2d4-123">Maximum value: MAX_LONG</span></span>|<span data-ttu-id="be2d4-124">Si cette propriété n'est pas définie, la valeur par défaut est définie sur 5 fois.</span><span class="sxs-lookup"><span data-stu-id="be2d4-124">If not specified, the default value is set to 5 times.</span></span>|  
|<span data-ttu-id="be2d4-125">**FileNetFailRetryInterval**</span><span class="sxs-lookup"><span data-stu-id="be2d4-125">**FileNetFailRetryInterval**</span></span>|<span data-ttu-id="be2d4-126">Long</span><span class="sxs-lookup"><span data-stu-id="be2d4-126">Long</span></span>|<span data-ttu-id="be2d4-127">Intervalle en minutes devant séparer chaque tentative d'accès à l'emplacement de réception sur le partage réseau en cas d'indisponibilité temporaire.</span><span class="sxs-lookup"><span data-stu-id="be2d4-127">The retry interval in minutes between attempts to access the receive location on the network share if it is temporarily unavailable.</span></span>|<span data-ttu-id="be2d4-128">Entier</span><span class="sxs-lookup"><span data-stu-id="be2d4-128">Integer</span></span><br /><br /> <span data-ttu-id="be2d4-129">MinimumValue : 0</span><span class="sxs-lookup"><span data-stu-id="be2d4-129">Minimumvalue: 0</span></span><br /><br /> <span data-ttu-id="be2d4-130">Valeur maximale : MAX_LONG</span><span class="sxs-lookup"><span data-stu-id="be2d4-130">Maximum value: MAX_LONG</span></span>|<span data-ttu-id="be2d4-131">Si cette propriété n'est pas définie, la valeur par défaut est définie sur 5 minutes.</span><span class="sxs-lookup"><span data-stu-id="be2d4-131">If not specified, the default value is set to 5 minutes.</span></span>|  
|<span data-ttu-id="be2d4-132">**BatchSize**</span><span class="sxs-lookup"><span data-stu-id="be2d4-132">**BatchSize**</span></span>|<span data-ttu-id="be2d4-133">Long</span><span class="sxs-lookup"><span data-stu-id="be2d4-133">Long</span></span>|<span data-ttu-id="be2d4-134">Nombre de fichiers que l'emplacement de réception peut envoyer au serveur en une fois.</span><span class="sxs-lookup"><span data-stu-id="be2d4-134">The number of files this receive location can submit to the server at one time.</span></span>|<span data-ttu-id="be2d4-135">Entier</span><span class="sxs-lookup"><span data-stu-id="be2d4-135">Integer</span></span><br /><br /> <span data-ttu-id="be2d4-136">Valeur minimale : 1</span><span class="sxs-lookup"><span data-stu-id="be2d4-136">Minimum value: 1</span></span><br /><br /> <span data-ttu-id="be2d4-137">Valeur maximale : 256</span><span class="sxs-lookup"><span data-stu-id="be2d4-137">Maximum value: 256</span></span>|<span data-ttu-id="be2d4-138">Si cette propriété n'est pas définie, la valeur par défaut est définie sur 20 fichiers.</span><span class="sxs-lookup"><span data-stu-id="be2d4-138">If not specified, the default value is set to 20 files.</span></span>|  
|<span data-ttu-id="be2d4-139">**FileMask**</span><span class="sxs-lookup"><span data-stu-id="be2d4-139">**FileMask**</span></span>|<span data-ttu-id="be2d4-140">Chaîne</span><span class="sxs-lookup"><span data-stu-id="be2d4-140">String</span></span>|<span data-ttu-id="be2d4-141">Masque de fichier utilisé par l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="be2d4-141">The file mask used by the receive location.</span></span>|<span data-ttu-id="be2d4-142">Chaîne</span><span class="sxs-lookup"><span data-stu-id="be2d4-142">String</span></span><br /><br /> <span data-ttu-id="be2d4-143">La longueur combinée de FilePAth et FileMask est limitée à 256 caractères.</span><span class="sxs-lookup"><span data-stu-id="be2d4-143">The length of the FilePath and FileMask combined cannot exceed 256 characters.</span></span>|<span data-ttu-id="be2d4-144">Si cette propriété n'est pas définie, la valeur par défaut est définie sur *.xml.</span><span class="sxs-lookup"><span data-stu-id="be2d4-144">If not specified, the default value is set to *.xml.</span></span>|  
|<span data-ttu-id="be2d4-145">**Chemin d’accès**</span><span class="sxs-lookup"><span data-stu-id="be2d4-145">**FilePath**</span></span>|<span data-ttu-id="be2d4-146">Chaîne</span><span class="sxs-lookup"><span data-stu-id="be2d4-146">String</span></span>|<span data-ttu-id="be2d4-147">Chemin d'accès du dossier surveillé par l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="be2d4-147">The path of the folder monitored by the receive location.</span></span>|<span data-ttu-id="be2d4-148">Chaîne</span><span class="sxs-lookup"><span data-stu-id="be2d4-148">String</span></span><br /><br /> <span data-ttu-id="be2d4-149">Requis</span><span class="sxs-lookup"><span data-stu-id="be2d4-149">Required</span></span><br /><br /> <span data-ttu-id="be2d4-150">La longueur combinée de FilePAth et FileMask est limitée à 256 caractères.</span><span class="sxs-lookup"><span data-stu-id="be2d4-150">The length of the FilePath and FileMask combined cannot exceed 256 characters.</span></span>|<span data-ttu-id="be2d4-151">Vous devez spécifier **Important :** le dossier de fichiers créé pour l’emplacement de réception doit avoir l’autorisation d’écriture pour les informations d’identification du Gestionnaire de réception configuré sur l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="be2d4-151">Must be specified **Important:**  The file folder created for the receive location must have write permission for the receive handler credentials configured on the receive location.</span></span>|  
|<span data-ttu-id="be2d4-152">**Nom d’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="be2d4-152">**Username**</span></span>|<span data-ttu-id="be2d4-153">Chaîne</span><span class="sxs-lookup"><span data-stu-id="be2d4-153">String</span></span>|<span data-ttu-id="be2d4-154">Nom d'utilisateur du compte utilisé pour accéder au dossier.</span><span class="sxs-lookup"><span data-stu-id="be2d4-154">User name for account used to access folder.</span></span>|<span data-ttu-id="be2d4-155">La longueur minimale : 0</span><span class="sxs-lookup"><span data-stu-id="be2d4-155">Min length: 0</span></span><br /><br /> <span data-ttu-id="be2d4-156">Longueur maximale : 256</span><span class="sxs-lookup"><span data-stu-id="be2d4-156">Max length: 256</span></span>|<span data-ttu-id="be2d4-157">Si ni le nom d'utilisateur ni le mot de passe ne sont spécifiés, les informations d'identification de l'hôte sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="be2d4-157">If neither username or password are specified, host credentials are used.</span></span><br /><br /> <span data-ttu-id="be2d4-158">Si la propriété a la valeur Null (vt=”1”), la valeur stockée dans la base de données de configuration est utilisée.</span><span class="sxs-lookup"><span data-stu-id="be2d4-158">If null (vt=”1”) then the value stored in configuration database is used.</span></span>|  
|<span data-ttu-id="be2d4-159">**Mot de passe**</span><span class="sxs-lookup"><span data-stu-id="be2d4-159">**Password**</span></span>|<span data-ttu-id="be2d4-160">Chaîne</span><span class="sxs-lookup"><span data-stu-id="be2d4-160">String</span></span>|<span data-ttu-id="be2d4-161">Mot de passe du compte utilisé pour accéder au dossier.</span><span class="sxs-lookup"><span data-stu-id="be2d4-161">Password for account used to access folder.</span></span>|<span data-ttu-id="be2d4-162">La longueur minimale : 0</span><span class="sxs-lookup"><span data-stu-id="be2d4-162">Min length: 0</span></span><br /><br /> <span data-ttu-id="be2d4-163">Longueur maximale : 256</span><span class="sxs-lookup"><span data-stu-id="be2d4-163">Max length: 256</span></span>|<span data-ttu-id="be2d4-164">Si ni le nom d'utilisateur ni le mot de passe ne sont spécifiés, les informations d'identification de l'hôte sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="be2d4-164">If neither username or password are specified, host credentials are used.</span></span><br /><br /> <span data-ttu-id="be2d4-165">Si la propriété a la valeur Null (vt=”1”), la valeur stockée dans la base de données de configuration est utilisée.</span><span class="sxs-lookup"><span data-stu-id="be2d4-165">If null (vt=”1”) then the value stored in configuration database is used.</span></span>|  
  
 <span data-ttu-id="be2d4-166">Le code suivant illustre le format de la chaîne XML que vous devez utiliser pour définir les propriétés :</span><span class="sxs-lookup"><span data-stu-id="be2d4-166">The following code shows the format of the XML string you use to set the properties:</span></span>  
  
```  
<CustomProps>  
   <FilePath vt="8">C:\Temp</FilePath>  
   <BatchSize vt="19">20</BatchSize>  
   <FileMask vt="8">*.xml</FileMask>  
   <FileNetFailRetryCount vt="19">5</FileNetFailRetryCount>  
   <FileNetFailRetryInterval vt="19">5</FileNetFailRetryInterval>  
   \<Username vt=”8”>MyDomain\MyUsername</Username>  
   \<Password vt=”8”>PASSWORD</Password>  
</CustomProps>  
  
```  

## <a name="create-the-send-port"></a><span data-ttu-id="be2d4-167">Pour créer un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="be2d4-167">Create the send port</span></span>

<span data-ttu-id="be2d4-168">Elles sont stockées dans un jeu de propriétés XML personnalisé.</span><span class="sxs-lookup"><span data-stu-id="be2d4-168">Configuration information is stored in a custom XML property bag.</span></span> <span data-ttu-id="be2d4-169">Le `bts_file_properties.xsd` schéma de propriété de fichier envoi gestionnaire définit les propriétés spécifiques à l’adaptateur de fichier.</span><span class="sxs-lookup"><span data-stu-id="be2d4-169">The `bts_file_properties.xsd` File send handler property schema defines the File adapter-specific properties.</span></span> <span data-ttu-id="be2d4-170">Ces propriétés permettent de configurer les ports d'envoi FILE et de transmettre des informations spécifiques à l'adaptateur au sein du serveur.</span><span class="sxs-lookup"><span data-stu-id="be2d4-170">You use these properties to configure the File send ports, as well as for passing adapter-specific information within the server.</span></span>  
  
<span data-ttu-id="be2d4-171">Le modèle d’objet de l’Explorateur BizTalk expose le **ITransportInfo** interface configuration adaptateur pour les ports d’envoi File, qui contient le **TransportTypeData** propriété en lecture/écriture.</span><span class="sxs-lookup"><span data-stu-id="be2d4-171">The BizTalk Explorer object model exposes the **ITransportInfo** adapter configuration interface for File send ports, which contains the **TransportTypeData** read/write property.</span></span> <span data-ttu-id="be2d4-172">Cette propriété accepte le jeu de propriétés de configuration du gestionnaire d'envoi FILE sous la forme d'une chaîne XML composée d'une paire nom/valeur.</span><span class="sxs-lookup"><span data-stu-id="be2d4-172">This property accepts the File send handler configuration property bag as a name/value pair XML string.</span></span>  
  
 <span data-ttu-id="be2d4-173">Définition de la **TransportTypeData** propriété de la **ITransportInfo** interface n’est pas requise.</span><span class="sxs-lookup"><span data-stu-id="be2d4-173">Setting the **TransportTypeData** property of the **ITransportInfo** interface is not required.</span></span> <span data-ttu-id="be2d4-174">Si elle n'est pas définie, les valeurs par défaut de configuration du gestionnaire d'envoi FILE sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="be2d4-174">If it is not set, the default values for the File send handler configuration are used.</span></span>  
  
 <span data-ttu-id="be2d4-175">Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir par programme dans le modèle objet de l'Explorateur BizTalk pour l'emplacement du gestionnaire d'envoi FILE.</span><span class="sxs-lookup"><span data-stu-id="be2d4-175">The following table lists the configuration properties you can set programmatically in the BizTalk Explorer object model for the File send handler location.</span></span>  
  
|<span data-ttu-id="be2d4-176">Nom de la propriété</span><span class="sxs-lookup"><span data-stu-id="be2d4-176">Property name</span></span>|<span data-ttu-id="be2d4-177">Type</span><span class="sxs-lookup"><span data-stu-id="be2d4-177">Type</span></span>|<span data-ttu-id="be2d4-178"> Description</span><span class="sxs-lookup"><span data-stu-id="be2d4-178">Description</span></span>|  
|-------------------|----------|-----------------|  
|<span data-ttu-id="be2d4-179">**CopyMode**</span><span class="sxs-lookup"><span data-stu-id="be2d4-179">**CopyMode**</span></span>|<span data-ttu-id="be2d4-180">Long</span><span class="sxs-lookup"><span data-stu-id="be2d4-180">Long</span></span>|<span data-ttu-id="be2d4-181">Définir le mode de copie à utiliser lors de l’écriture d’un message dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="be2d4-181">Define the copy mode to use when writing a message to a file.</span></span> <span data-ttu-id="be2d4-182">Les valeurs valides sont :</span><span class="sxs-lookup"><span data-stu-id="be2d4-182">Valid values are:</span></span><br /><br /> <span data-ttu-id="be2d4-183">**Ajouter (0).**</span><span class="sxs-lookup"><span data-stu-id="be2d4-183">**Append (0).**</span></span> <span data-ttu-id="be2d4-184">le gestionnaire d'envoi FILE ouvre un fichier s'il existe et ajoute un message à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="be2d4-184">The File send handler opens a file if it exists and appends a message to the end of the file.</span></span> <span data-ttu-id="be2d4-185">Si le fichier n'existe pas, il le crée.</span><span class="sxs-lookup"><span data-stu-id="be2d4-185">If the file does not exist, the File send handler creates a new file.</span></span><br /><br /> <span data-ttu-id="be2d4-186">**Créer (1).**</span><span class="sxs-lookup"><span data-stu-id="be2d4-186">**Create new (1).**</span></span> <span data-ttu-id="be2d4-187">si le fichier n'existe pas, le gestionnaire d'envoi FILE le crée et y enregistre des éléments.</span><span class="sxs-lookup"><span data-stu-id="be2d4-187">If the file does not exist, the File send handler creates a new file and writes to it.</span></span> <span data-ttu-id="be2d4-188">si le fichier existe déjà, il signale une erreur et applique la procédure logique commune pour les nouvelles tentatives sur l'adaptateur pour les ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="be2d4-188">If the file already exists, the File send handler reports an error and then follows common adapter retry logic for send ports.</span></span> <span data-ttu-id="be2d4-189">Il s'agit d'un mode de copie par défaut pour le gestionnaire d'envoi FILE.</span><span class="sxs-lookup"><span data-stu-id="be2d4-189">This is a default copy mode for the File send handler.</span></span><br /><br /> <span data-ttu-id="be2d4-190">**Remplacer (2).**</span><span class="sxs-lookup"><span data-stu-id="be2d4-190">**Overwrite (2).**</span></span> <span data-ttu-id="be2d4-191">le gestionnaire d'envoi FILE ouvre un fichier s'il existe et remplace son contenu.</span><span class="sxs-lookup"><span data-stu-id="be2d4-191">The File send handler opens a file if it exists and overwrites its content.</span></span> <span data-ttu-id="be2d4-192">Si le fichier n'existe pas, il le crée.</span><span class="sxs-lookup"><span data-stu-id="be2d4-192">If the file does not exist, the File send handler creates a new file.</span></span>|  
|<span data-ttu-id="be2d4-193">**AllowCacheOnWrite**</span><span class="sxs-lookup"><span data-stu-id="be2d4-193">**AllowCacheOnWrite**</span></span>|<span data-ttu-id="be2d4-194">Booléen</span><span class="sxs-lookup"><span data-stu-id="be2d4-194">Boolean</span></span>|<span data-ttu-id="be2d4-195">Précise si l'adaptateur FILE utilise la mise en cache du système de fichiers lors de l'écriture de messages dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="be2d4-195">Defines whether the File adapter uses file system caching when writing messages to a file.</span></span><br /><br /> <span data-ttu-id="be2d4-196">Les valeurs valides sont :</span><span class="sxs-lookup"><span data-stu-id="be2d4-196">Valid values are:</span></span><br /><br /> <span data-ttu-id="be2d4-197">**True (-1)** l’adaptateur File utilise le fichier système mise en cache lors de l’écriture du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="be2d4-197">**True (-1)** The File adapter uses file system caching when writing the output file.</span></span><br /><br /> <span data-ttu-id="be2d4-198">**False (0)** Gestionnaire d’envoi du fichier n’utilise pas le fichier système mise en cache lors de l’écriture du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="be2d4-198">**False (0)** The File send handler does not use file system caching when writing the output file.</span></span>|  
|<span data-ttu-id="be2d4-199">**Utiliser un fichier temporaire lors de l’écriture**</span><span class="sxs-lookup"><span data-stu-id="be2d4-199">**Use temporary file while writing**</span></span>|<span data-ttu-id="be2d4-200">Booléen</span><span class="sxs-lookup"><span data-stu-id="be2d4-200">Boolean</span></span>|<span data-ttu-id="be2d4-201">Définit si vous souhaitez écrire le fichier de sortie dans un fichier temporaire tout d’abord, puis renommez le fichier une fois l’opération d’écriture est terminée.</span><span class="sxs-lookup"><span data-stu-id="be2d4-201">Defines whether to write the output file to a temporary file first and then rename the file once the write operation has completed.</span></span> <span data-ttu-id="be2d4-202">Si cette option est activée, le fichier temporaire doit être créé avec l’extension **BTS-WIP**.</span><span class="sxs-lookup"><span data-stu-id="be2d4-202">If this option is enabled then the temporary file will be created with the extension **BTS-WIP**.</span></span><br /><br /> <span data-ttu-id="be2d4-203">Les valeurs valides sont :</span><span class="sxs-lookup"><span data-stu-id="be2d4-203">Valid values are:</span></span><br /><br /> <span data-ttu-id="be2d4-204">**True (-1)** l’adaptateur File crée un fichier temporaire lors de l’écriture dans le dossier cible.</span><span class="sxs-lookup"><span data-stu-id="be2d4-204">**True (-1)** The File adapter creates a temporary file when writing to the target folder.</span></span><br /><br /> <span data-ttu-id="be2d4-205">**False (0)** l’adaptateur File ne crée pas un fichier temporaire lors de l’écriture dans le dossier cible.</span><span class="sxs-lookup"><span data-stu-id="be2d4-205">**False (0)** The File adapter does not create a temporary file when writing to the target folder.</span></span> <span data-ttu-id="be2d4-206">**Remarque :** cette option est disponible uniquement lorsque le **CopyMode** est définie sur une valeur de **créer nouveau (1)**.</span><span class="sxs-lookup"><span data-stu-id="be2d4-206">**Note:**  This option is only available when the **CopyMode** property is set to a value of **Create new (1)**.</span></span>|  
  
 <span data-ttu-id="be2d4-207">Si l'une des propriétés de configuration n'a pas de valeur dans le contexte du message, le gestionnaire d'envoi FILE utilise sa valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="be2d4-207">If any of the configuration properties do not have a value on the message context, the File send handler uses its default value.</span></span>  
  
 <span data-ttu-id="be2d4-208">Vous pouvez définir les propriétés de configuration par programme dans un contexte de message.</span><span class="sxs-lookup"><span data-stu-id="be2d4-208">You can set configuration properties programmatically on a message context.</span></span> <span data-ttu-id="be2d4-209">Vous pouvez les définir dans une orchestration ou dans un composant de pipeline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="be2d4-209">You can set these properties in an orchestration or in a custom pipeline component.</span></span> <span data-ttu-id="be2d4-210">Les règles suivantes s'appliquent dans le cadre de l'utilisation de ces propriétés :</span><span class="sxs-lookup"><span data-stu-id="be2d4-210">The following rules apply when using these properties:</span></span>  
  
-   <span data-ttu-id="be2d4-211">Si la propriété de configuration est définie dans une orchestration ou un composant de pipeline personnalisé dans un pipeline de réception, alors :</span><span class="sxs-lookup"><span data-stu-id="be2d4-211">If the configuration property is set in an orchestration or in a custom pipeline component in a receive pipeline, then:</span></span>  
  
    -   <span data-ttu-id="be2d4-212">Si un message est envoyé à un port d'envoi statique, la valeur de la propriété est remplacée par la valeur configurée pour ce port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="be2d4-212">If a message is sent to a static send port, the property value will be overwritten with the value configured for that send port.</span></span>  
  
    -   <span data-ttu-id="be2d4-213">Si un message est envoyé à un port d'envoi dynamique, la valeur de la propriété n'est pas remplacée.</span><span class="sxs-lookup"><span data-stu-id="be2d4-213">If a message is sent to a dynamic send port, the property value will not be overwritten.</span></span>  
  
-   <span data-ttu-id="be2d4-214">Si une propriété de configuration est définie dans un composant de pipeline personnalisé dans un pipeline d'envoi, alors :</span><span class="sxs-lookup"><span data-stu-id="be2d4-214">If a configuration property is set in a custom pipeline component in a send pipeline, then:</span></span>  
  
    -   <span data-ttu-id="be2d4-215">La valeur n'est pas remplacée, que le message soit envoyé à un port d'envoi statique ou dynamique.</span><span class="sxs-lookup"><span data-stu-id="be2d4-215">The value will not be overwritten regardless of whether the message is sent to a static or dynamic send port.</span></span>  
  
 <span data-ttu-id="be2d4-216">Le code suivant illustre le format de la chaîne XML que vous pouvez utiliser pour définir les propriétés :</span><span class="sxs-lookup"><span data-stu-id="be2d4-216">The following code shows the format of the XML string you can use to set the properties:</span></span>  
  
```  
<CustomProps>  
   <CopyMode vt="19">0</CopyMode>  
   <AllowCacheOnWrite vt="11">-1</AllowCacheOnWrite>  
   <UseTempFileOnWrite vt="11">-1</UseTempFileOnWrite>  
</CustomProps>  
```  

