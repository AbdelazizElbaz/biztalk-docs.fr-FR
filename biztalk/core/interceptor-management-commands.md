---
title: "Commandes de gestion de l’intercepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2be6460-1f81-4bc3-a831-34ff24d65d34
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32392c05f47c00a6c62372acbf8d1ba0bed0da6c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="interceptor-management-commands"></a><span data-ttu-id="4dffb-102">Commandes de gestion des intercepteurs</span><span class="sxs-lookup"><span data-stu-id="4dffb-102">Interceptor Management Commands</span></span>
<span data-ttu-id="4dffb-103">Pour prendre en charge la nouvelle fonctionnalité d'intercepteur BAM, quatre nouvelles commandes ont été ajoutées à l'utilitaire de gestion de l'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="4dffb-103">To support the new BAM interceptor functionality, four new commands have been added to the BAM Management utility.</span></span>  
  
 <span data-ttu-id="4dffb-104">Ces commandes prennent en charge le déploiement, l'extraction et la suppression des intercepteurs.</span><span class="sxs-lookup"><span data-stu-id="4dffb-104">These commands support the deployment, retrieval, and removal of interceptors.</span></span> <span data-ttu-id="4dffb-105">L'une d'entre elles permet également d'afficher la liste des intercepteur configurés.</span><span class="sxs-lookup"><span data-stu-id="4dffb-105">A command is also provided to list the configured interceptors.</span></span>  
  
-   <span data-ttu-id="4dffb-106">intercepteur de déploiement : déploie une configuration d’intercepteur.</span><span class="sxs-lookup"><span data-stu-id="4dffb-106">deploy-interceptor: Deploys an interceptor configuration.</span></span>  
  
-   <span data-ttu-id="4dffb-107">Get-interceptorlist : Obtient une liste d’activités sur lequel l’interception est déployée.</span><span class="sxs-lookup"><span data-stu-id="4dffb-107">get-interceptorlist: Gets a list of activities on which interception is deployed.</span></span>  
  
-   <span data-ttu-id="4dffb-108">Get-interceptor : Obtient la configuration de l’intercepteur.</span><span class="sxs-lookup"><span data-stu-id="4dffb-108">get-interceptor: Gets the interceptor configuration.</span></span>  
  
-   <span data-ttu-id="4dffb-109">l’intercepteur de la suppression : supprime une configuration de l’intercepteur.</span><span class="sxs-lookup"><span data-stu-id="4dffb-109">remove-interceptor: Removes an interceptor configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4dffb-110">Vous pouvez activer le traçage sur n’importe quelle commande d’utilitaire BM en incluant le **-Trace : sur &#124; off** commutateur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="4dffb-110">You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="4dffb-111">L'utilisation du commutateur de suivi remplace les paramètres de suivi du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="4dffb-111">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="4dffb-112">Le commutateur peut être utilisé conjointement avec toute commande BAM classique.</span><span class="sxs-lookup"><span data-stu-id="4dffb-112">The switch can be used in conjunction with any normal BM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4dffb-113">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="4dffb-113">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="deploy-interceptor-command"></a><span data-ttu-id="4dffb-114">Commande deploy-interceptor</span><span class="sxs-lookup"><span data-stu-id="4dffb-114">deploy-interceptor Command</span></span>  
 <span data-ttu-id="4dffb-115">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="4dffb-115">**Usage**</span></span>  
  
 <span data-ttu-id="4dffb-116">**BM.exe déployer-intercepteur - FileName :\<le nom du fichier de Configuration XML\> [-Force : True] [-Server :\<server\>] [-base de données :\<base de données\>]**</span><span class="sxs-lookup"><span data-stu-id="4dffb-116">**bm.exe deploy-interceptor -FileName:\<Configuration XML Filename\> [-Force:True ] [-Server:\<server\>] [-Database:\<database\>]**</span></span>  
  
 <span data-ttu-id="4dffb-117">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="4dffb-117">**Parameters**</span></span>  
  
|<span data-ttu-id="4dffb-118">Paramètre</span><span class="sxs-lookup"><span data-stu-id="4dffb-118">Parameter</span></span>|<span data-ttu-id="4dffb-119"> Description</span><span class="sxs-lookup"><span data-stu-id="4dffb-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4dffb-120">Nom de fichier :\<nom de fichier de Configuration XML\></span><span class="sxs-lookup"><span data-stu-id="4dffb-120">FileName:\<Configuration XML Filename\></span></span>|<span data-ttu-id="4dffb-121">Nom du fichier XML contenant la configuration d'intercepteur.</span><span class="sxs-lookup"><span data-stu-id="4dffb-121">The name of the XML file containing the interceptor configuration.</span></span>|  
|<span data-ttu-id="4dffb-122">Force:True</span><span class="sxs-lookup"><span data-stu-id="4dffb-122">Force:True</span></span>|<span data-ttu-id="4dffb-123">Facultatif : Force le déploiement de la configuration de l’intercepteur lors de la détection des conflits de noms événement source.</span><span class="sxs-lookup"><span data-stu-id="4dffb-123">Optional: Forces deployment of the interceptor configuration when event source name collisions are detected.</span></span>|  
|<span data-ttu-id="4dffb-124">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="4dffb-124">Server:\<server\></span></span>|<span data-ttu-id="4dffb-125">Facultatif : Le nom du serveur sur lequel déployer l’intercepteur.</span><span class="sxs-lookup"><span data-stu-id="4dffb-125">Optional: The name of the server on which to deploy the interceptor.</span></span> <span data-ttu-id="4dffb-126">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="4dffb-126">The server must be in the same domain as the computer from which you are running bm.exe.</span></span>|  
|<span data-ttu-id="4dffb-127">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="4dffb-127">Database:\<database\></span></span>|<span data-ttu-id="4dffb-128">Facultatif : Le nom de la base de données d’importation principale BAM sur laquelle vous pouvez configurer l’intercepteur.</span><span class="sxs-lookup"><span data-stu-id="4dffb-128">Optional: The name of the BAM Primary Import database on which to configure the interceptor.</span></span>|  
  
 <span data-ttu-id="4dffb-129">Cette commande déploie la configuration d'intercepteur sur la base de données et le serveur spécifiés.</span><span class="sxs-lookup"><span data-stu-id="4dffb-129">This command deploys the interceptor configuration to the specified server and database.</span></span> <span data-ttu-id="4dffb-130">Pendant le déploiement, l'utilitaire de gestion de l'analyse BAM effectue les validations suivantes :</span><span class="sxs-lookup"><span data-stu-id="4dffb-130">During deployment, the BAM Management utility performs the following validations:</span></span>  
  
-   <span data-ttu-id="4dffb-131">Validation XSD : la configuration de l’intercepteur est validée par rapport au schéma de configuration de l’intercepteur commun.</span><span class="sxs-lookup"><span data-stu-id="4dffb-131">XSD validation: The interceptor configuration is validated against the common interceptor configuration schema.</span></span>  
  
-   <span data-ttu-id="4dffb-132">Validation de l'existence de l'activité (déploiement dans la base de données d'importation principale) et de la validité des points de contrôle (existence et type de données correspondant).</span><span class="sxs-lookup"><span data-stu-id="4dffb-132">Validation that the activity exists (is deployed in the Primary Import database) and that checkpoints are valid (exist and have a matching data type).</span></span>  
  
 <span data-ttu-id="4dffb-133">En cas de collision dans le nom de la source d'événements, un message d'avertissement décrivant la collision est envoyé.</span><span class="sxs-lookup"><span data-stu-id="4dffb-133">If a collision is detected in the event source name, a warning is thrown describing the collision.</span></span> <span data-ttu-id="4dffb-134">En cas de collision, le déploiement échouera à moins que le **– Force : True** indicateur du paramètre est utilisé.</span><span class="sxs-lookup"><span data-stu-id="4dffb-134">In the case of a collision, the deployment will fail unless the **–Force:True** parameter flag is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4dffb-135">Le **– Force : True** paramètre supprime potentiellement les configurations d’intercepteur qui font référence à des sources d’événements portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="4dffb-135">The **–Force:True** parameter potentially removes interceptor configurations that reference event sources with the same name.</span></span> <span data-ttu-id="4dffb-136">Vous devez utiliser le **get-interceptor** commande pour créer une sauvegarde de la configuration d’intercepteur existante avant d’utiliser le **– Force : True** paramètre.</span><span class="sxs-lookup"><span data-stu-id="4dffb-136">You should use the **get-interceptor** command to create a backup of existing interceptor configurations before using the **–Force:True** parameter.</span></span>  
  
 <span data-ttu-id="4dffb-137">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="4dffb-137">**Examples**</span></span>  
  
```  
bm.exe deploy-interceptor  -FileName:myInceptor.xml  
bm.exe deploy-interceptor  -FileName:myInceptor.xml -Force:True  
```  
  
## <a name="get-interceptorlist-command"></a><span data-ttu-id="4dffb-138">Commande get-interceptorlist</span><span class="sxs-lookup"><span data-stu-id="4dffb-138">get-interceptorlist Command</span></span>  
 <span data-ttu-id="4dffb-139">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="4dffb-139">**Usage**</span></span>  
  
 <span data-ttu-id="4dffb-140">**BM.exe get-interceptorlist [-Server :\<server\>] [-base de données :\<base de données\>]**</span><span class="sxs-lookup"><span data-stu-id="4dffb-140">**bm.exe get-interceptorlist [-Server:\<server\>] [-Database:\<database\>]**</span></span>  
  
 <span data-ttu-id="4dffb-141">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="4dffb-141">**Parameters**</span></span>  
  
|<span data-ttu-id="4dffb-142">Paramètre</span><span class="sxs-lookup"><span data-stu-id="4dffb-142">Parameter</span></span>|<span data-ttu-id="4dffb-143"> Description</span><span class="sxs-lookup"><span data-stu-id="4dffb-143">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4dffb-144">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="4dffb-144">Server:\<server\></span></span>|<span data-ttu-id="4dffb-145">Facultatif : Le nom du serveur à partir de laquelle retourner une liste des intercepteurs déployés.</span><span class="sxs-lookup"><span data-stu-id="4dffb-145">Optional: The name of the server from which to return a list of deployed interceptors.</span></span> <span data-ttu-id="4dffb-146">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="4dffb-146">The server must be in the same domain as the computer from which you are running bm.exe.</span></span>|  
|<span data-ttu-id="4dffb-147">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="4dffb-147">Database:\<database\></span></span>|<span data-ttu-id="4dffb-148">Facultatif : Le nom de la base de données d’importation principale BAM à partir de laquelle extraire les intercepteurs déployés.</span><span class="sxs-lookup"><span data-stu-id="4dffb-148">Optional: The name of the BAM Primary Import database from which to retrieve the deployed interceptors.</span></span>|  
  
 <span data-ttu-id="4dffb-149">Cette commande retourne une liste des activités, et des sources d'événements associés, pour lesquelles l'interception est activée.</span><span class="sxs-lookup"><span data-stu-id="4dffb-149">This command returns a list of the activities, and their associated event sources, for which interception is enabled.</span></span>  
  
 <span data-ttu-id="4dffb-150">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="4dffb-150">**Example**</span></span>  
  
```  
bm.exe get-interceptorlist   
```  
  
## <a name="get-interceptor-command"></a><span data-ttu-id="4dffb-151">Commande get-interceptor</span><span class="sxs-lookup"><span data-stu-id="4dffb-151">get-interceptor Command</span></span>  
 <span data-ttu-id="4dffb-152">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="4dffb-152">**Usage**</span></span>  
  
 <span data-ttu-id="4dffb-153">**BM.exe get-interceptor [-Server :\<server\>] [-base de données :\<base de données\>] - FileName : \<le nom du fichier de Configuration XML\> [-activité : \<nom de l’activité \>] [-EventSource : \<nom Source d’événement\>]**</span><span class="sxs-lookup"><span data-stu-id="4dffb-153">**bm.exe get-interceptor [-Server:\<server\>] [-Database:\<database\>] -FileName: \<Configuration XML Filename\> [ -Activity: \<Activity Name\>] [-EventSource: \<Event Source Name\>]**</span></span>  
  
 <span data-ttu-id="4dffb-154">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="4dffb-154">**Parameters**</span></span>  
  
|<span data-ttu-id="4dffb-155">Paramètre</span><span class="sxs-lookup"><span data-stu-id="4dffb-155">Parameter</span></span>|<span data-ttu-id="4dffb-156"> Description</span><span class="sxs-lookup"><span data-stu-id="4dffb-156">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4dffb-157">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="4dffb-157">Server:\<server\></span></span>|<span data-ttu-id="4dffb-158">Facultatif : Le nom du serveur à partir de laquelle extraire l’intercepteur déployé.</span><span class="sxs-lookup"><span data-stu-id="4dffb-158">Optional: The name of the server from which to retrieve the deployed interceptor.</span></span> <span data-ttu-id="4dffb-159">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="4dffb-159">The server must be in the same domain as the computer from which you are running bm.exe.</span></span>|  
|<span data-ttu-id="4dffb-160">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="4dffb-160">Database:\<database\></span></span>|<span data-ttu-id="4dffb-161">Facultatif : Le nom de la base de données d’importation principale BAM à partir de laquelle extraire l’intercepteur déployé.</span><span class="sxs-lookup"><span data-stu-id="4dffb-161">Optional: The name of the BAM Primary Import database from which to retrieve deployed interceptor.</span></span>|  
|<span data-ttu-id="4dffb-162">Nom de fichier :\<nom de fichier de Configuration XML\></span><span class="sxs-lookup"><span data-stu-id="4dffb-162">FileName:\<Configuration XML Filename\></span></span>|<span data-ttu-id="4dffb-163">Nom du fichier XML dans lequel écrire la configuration d'intercepteur.</span><span class="sxs-lookup"><span data-stu-id="4dffb-163">The name of the XML file to which to write the interceptor configuration.</span></span>|  
|<span data-ttu-id="4dffb-164">Activité :\<nom de l’activité\></span><span class="sxs-lookup"><span data-stu-id="4dffb-164">Activity:\<Activity Name\></span></span>|<span data-ttu-id="4dffb-165">Facultatif : Spécifie l’activité pour laquelle retourner l’intercepteur configuré.</span><span class="sxs-lookup"><span data-stu-id="4dffb-165">Optional: Specifies the activity for which to return the configured interceptor.</span></span> <span data-ttu-id="4dffb-166">Peut être utilisé conjointement avec la **EventSource** paramètre pour spécifier la configuration à retourner.</span><span class="sxs-lookup"><span data-stu-id="4dffb-166">Can be used in conjunction with the **EventSource** parameter to further specify the configuration to return.</span></span>|  
|<span data-ttu-id="4dffb-167">EventSource :\<nom Source d’événement\></span><span class="sxs-lookup"><span data-stu-id="4dffb-167">EventSource:\<Event Source Name\></span></span>|<span data-ttu-id="4dffb-168">Facultatif : Spécifie la source d’événement pour lequel retourner l’intercepteur configuré.</span><span class="sxs-lookup"><span data-stu-id="4dffb-168">Optional: Specifies the event source for which to return the configured interceptor.</span></span> <span data-ttu-id="4dffb-169">Peut être utilisé conjointement avec la **activité** paramètre pour spécifier la configuration à retourner.</span><span class="sxs-lookup"><span data-stu-id="4dffb-169">Can be used in conjunction with the **Activity** parameter to further specify the configuration to return.</span></span>|  
  
 <span data-ttu-id="4dffb-170">Si aucun nom d'activité ou de source d'événements n'est spécifié, la commande retourne un fichier de configuration valide contenant la configuration d'intercepteur pour l'ensemble des activités et sources d'événements.</span><span class="sxs-lookup"><span data-stu-id="4dffb-170">If no activity name or event source name is provided, the command returns a valid configuration file containing the interceptor configurations for all event sources and activities.</span></span>  
  
 <span data-ttu-id="4dffb-171">Si seul un nom d'activité est spécifié, la commande retourne un fichier de configuration d'intercepteur valide pour l'ensemble des sources d'événements associées à cette activité.</span><span class="sxs-lookup"><span data-stu-id="4dffb-171">If only an activity name is provided, the command returns a valid interceptor configuration file for all event sources for that activity.</span></span>  
  
 <span data-ttu-id="4dffb-172">Si seul un nom de source d'événements est spécifié, la commande retourne un fichier de configuration d'intercepteur valide pour cette source d'événements sur l'ensemble des activités.</span><span class="sxs-lookup"><span data-stu-id="4dffb-172">If only an event source name is provided, the command returns a valid interceptor configuration file for that event source across all activities.</span></span>  
  
 <span data-ttu-id="4dffb-173">Si un nom d'activité et un nom de source d'événements sont spécifiés, la commande retourne un fichier de configuration d'intercepteur valide pour cette source d'événements associée à cette activité.</span><span class="sxs-lookup"><span data-stu-id="4dffb-173">If both an activity name and an event source name are provided, then the command returns a valid interceptor configuration file for that event source for that activity.</span></span>  
  
 <span data-ttu-id="4dffb-174">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="4dffb-174">**Examples**</span></span>  
  
```  
bm.exe get-interceptor   
bm.exe get-interceptor  -Activity:ShippingPO  
```  
  
## <a name="remove-interceptor-command"></a><span data-ttu-id="4dffb-175">Commande remove-interceptor</span><span class="sxs-lookup"><span data-stu-id="4dffb-175">remove-interceptor Command</span></span>  
 <span data-ttu-id="4dffb-176">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="4dffb-176">**Usage**</span></span>  
  
 <span data-ttu-id="4dffb-177">**BM.exe remove-interceptor [-Server :\<server\>] [-base de données :\<base de données\>] [-activité : \<nom de l’activité\>] [-EventSource : \<nom de Source d’événement\>]**</span><span class="sxs-lookup"><span data-stu-id="4dffb-177">**bm.exe remove-interceptor [-Server:\<server\>] [-Database:\<database\>] [ -Activity: \<Activity Name\>][-EventSource: \<Event Source Name\>]**</span></span>  
  
 <span data-ttu-id="4dffb-178">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="4dffb-178">**Parameters**</span></span>  
  
|<span data-ttu-id="4dffb-179">Paramètre</span><span class="sxs-lookup"><span data-stu-id="4dffb-179">Parameter</span></span>|<span data-ttu-id="4dffb-180"> Description</span><span class="sxs-lookup"><span data-stu-id="4dffb-180">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4dffb-181">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="4dffb-181">Server:\<server\></span></span>|<span data-ttu-id="4dffb-182">Facultatif : Le nom du serveur sur lequel l’intercepteur est configuré.</span><span class="sxs-lookup"><span data-stu-id="4dffb-182">Optional: The name of the server on which the interceptor is configured.</span></span> <span data-ttu-id="4dffb-183">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="4dffb-183">The server must be in the same domain as the computer from which you are running bm.exe.</span></span>|  
|<span data-ttu-id="4dffb-184">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="4dffb-184">Database:\<database\></span></span>|<span data-ttu-id="4dffb-185">Facultatif : Le nom de la base de données sur lequel l’intercepteur est configuré.</span><span class="sxs-lookup"><span data-stu-id="4dffb-185">Optional: The name of the database on which the interceptor is configured.</span></span>|  
|<span data-ttu-id="4dffb-186">Activité : \<nom de l’activité\></span><span class="sxs-lookup"><span data-stu-id="4dffb-186">Activity: \<Activity Name\></span></span>|<span data-ttu-id="4dffb-187">Facultatif : Spécifie l’activité pour laquelle supprimer l’intercepteur spécifié.</span><span class="sxs-lookup"><span data-stu-id="4dffb-187">Optional: Specifies the activity for which to remove the specified interceptor.</span></span> <span data-ttu-id="4dffb-188">Peut être utilisé conjointement avec la **EventSource** paramètre pour spécifier la configuration à retourner.</span><span class="sxs-lookup"><span data-stu-id="4dffb-188">Can be used in conjunction with the **EventSource** parameter to further specify the configuration to return.</span></span>|  
|<span data-ttu-id="4dffb-189">EventSource : \<nom Source d’événement\></span><span class="sxs-lookup"><span data-stu-id="4dffb-189">EventSource: \<Event Source Name\></span></span>|<span data-ttu-id="4dffb-190">Facultatif : Spécifie la source d’événements pour laquelle supprimer l’intercepteur spécifié.</span><span class="sxs-lookup"><span data-stu-id="4dffb-190">Optional: Specifies the event source for which to remove the specified interceptor.</span></span> <span data-ttu-id="4dffb-191">Peut être utilisé conjointement avec la **activité** paramètre pour spécifier la configuration à retourner.</span><span class="sxs-lookup"><span data-stu-id="4dffb-191">Can be used in conjunction with the **Activity** parameter to further specify the configuration to return.</span></span>|  
  
 <span data-ttu-id="4dffb-192">Si seul un nom d'activité est spécifié, la commande supprime l'intercepteur pour l'ensemble des sources d'événements associées à cette activité.</span><span class="sxs-lookup"><span data-stu-id="4dffb-192">If only an activity name is provided, the command removes the interceptor for all event sources for that activity.</span></span>  
  
 <span data-ttu-id="4dffb-193">Si seul un nom de source d'événements est spécifié, la commande supprime uniquement cette partie de source d'événements pour l'ensemble des activités.</span><span class="sxs-lookup"><span data-stu-id="4dffb-193">If only an event source name is provided, the command removes only that event source portion for all activities.</span></span>  
  
 <span data-ttu-id="4dffb-194">**Exemple**</span><span class="sxs-lookup"><span data-stu-id="4dffb-194">**Example**</span></span>  
  
```  
bm.exe remove-interceptor   
```  
  
## <a name="see-also"></a><span data-ttu-id="4dffb-195">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4dffb-195">See Also</span></span>  
 [<span data-ttu-id="4dffb-196">Utilitaire de gestion de l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="4dffb-196">BAM Management Utility</span></span>](../core/bam-management-utility.md)