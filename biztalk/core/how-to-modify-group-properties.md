---
title: "Comment modifier les propriétés du groupe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying, groups
- configuring, groups
- groups, configuring
- managing [groups], properties
- groups, modifying
- managing [groups], modifying
- groups, properties
ms.assetid: 59e0853d-81b0-43f9-85bf-099868e25fad
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a191011b6824086e26c72ce5e5a182a167ca0e37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-group-properties"></a><span data-ttu-id="6f179-102">Modification des propriétés du groupe</span><span class="sxs-lookup"><span data-stu-id="6f179-102">How to Modify Group Properties</span></span>
<span data-ttu-id="6f179-103">Cette procédure vous permet de configurer les propriétés globales pour le groupe BizTalk Server de manière à pouvoir sélectionner un certificat de signature, modifier l'intervalle d'actualisation du cache et déterminer la façon dont BizTalk Server gérera les messages volumineux.</span><span class="sxs-lookup"><span data-stu-id="6f179-103">You can use this procedure to configure global properties for your BizTalk Server group so that you can select a signing certificate, modify the cache refresh interval, and determine how BizTalk Server will handle large messages.</span></span> <span data-ttu-id="6f179-104">Pour plus d’informations sur les propriétés du groupe BizTalk Server, consultez [groupes BizTalk](../core/biztalk-groups.md).</span><span class="sxs-lookup"><span data-stu-id="6f179-104">For more information about BizTalk Server group properties, see [BizTalk Groups](../core/biztalk-groups.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6f179-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="6f179-105">Prerequisites</span></span>  
 <span data-ttu-id="6f179-106">Pour exécuter cette procédure, vous devez être connecté en tant que membre du groupe des administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="6f179-106">To perform this procedure, you must be logged on as a member of the BizTalk Server Administrators group.</span></span>  
  
### <a name="to-configure-biztalk-group-properties"></a><span data-ttu-id="6f179-107">Pour configurer les propriétés du groupe BizTalk</span><span class="sxs-lookup"><span data-stu-id="6f179-107">To configure BizTalk group properties</span></span>  
  
1.  <span data-ttu-id="6f179-108">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="6f179-108">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="6f179-109">Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, cliquez sur **groupe BizTalk**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="6f179-109">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, right-click **BizTalk Group**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="6f179-110">Dans le **propriétés d’un groupe** boîte de dialogue le **général** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="6f179-110">In the **Group Properties** dialog box, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="6f179-111">Utiliser</span><span class="sxs-lookup"><span data-stu-id="6f179-111">Use this</span></span>|<span data-ttu-id="6f179-112">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="6f179-112">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="6f179-113">**Nom**</span><span class="sxs-lookup"><span data-stu-id="6f179-113">**Name**</span></span>|<span data-ttu-id="6f179-114">Entrer le nom du groupe.</span><span class="sxs-lookup"><span data-stu-id="6f179-114">Type the group name.</span></span> <span data-ttu-id="6f179-115">Le nom d'un tel groupe ne doit pas comporter plus de 128 caractères.</span><span class="sxs-lookup"><span data-stu-id="6f179-115">The group name cannot exceed 128 characters in length.</span></span> <span data-ttu-id="6f179-116">Le nom dans cette zone s’affiche en regard du **groupe** nœud dans l’arborescence de la console, ainsi que le nom du serveur et le nom de base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6f179-116">The name in this box appears next to the **Group** node in the console tree, along with the server name and the BizTalk Management database name.</span></span>|  
    |<span data-ttu-id="6f179-117">**Server**</span><span class="sxs-lookup"><span data-stu-id="6f179-117">**Server**</span></span>|<span data-ttu-id="6f179-118">Afficher le serveur sur lequel la base de données de gestion BizTalk est stockée.</span><span class="sxs-lookup"><span data-stu-id="6f179-118">Displays the server on which the BizTalk Management database is physically stored.</span></span>|  
    |<span data-ttu-id="6f179-119">**Base de données**</span><span class="sxs-lookup"><span data-stu-id="6f179-119">**Database**</span></span>|<span data-ttu-id="6f179-120">Afficher la base de données de gestion BizTalk dans laquelle les paramètres de configuration de ce groupe sont stockés.</span><span class="sxs-lookup"><span data-stu-id="6f179-120">Displays the BizTalk Management database on which all configuration settings for this group are stored.</span></span>|  
    |<span data-ttu-id="6f179-121">**Nom du serveur de l’authentification unique**</span><span class="sxs-lookup"><span data-stu-id="6f179-121">**SSO Server name**</span></span>|<span data-ttu-id="6f179-122">Entrer le nom du serveur de l'authentification unique de l'entreprise que cet ordinateur doit utiliser pour stocker les informations spécifiques aux adaptateurs et y accéder.</span><span class="sxs-lookup"><span data-stu-id="6f179-122">Type the name of the Enterprise Single Sign-On (SSO) server that this computer will use to store and access adapter-specific information.</span></span> <span data-ttu-id="6f179-123">Il s'agit du nom du serveur d'authentification unique utilisé pour établir la connexion à la base de données d'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="6f179-123">This is the name of the SSO server used to connect to the SSO database.</span></span>|  
    |<span data-ttu-id="6f179-124">**Groupe d’administrateurs BizTalk**</span><span class="sxs-lookup"><span data-stu-id="6f179-124">**BizTalk Administrator Group**</span></span>|<span data-ttu-id="6f179-125">Afficher le nom du groupe d'administrateurs disposant des droits nécessaires à la gestion de l'environnement BizTalk Server après installation.</span><span class="sxs-lookup"><span data-stu-id="6f179-125">Displays the name of the administrators group that has rights to manage the BizTalk Server environment after installation.</span></span>|  
    |<span data-ttu-id="6f179-126">**Groupe des opérateurs BizTalk**</span><span class="sxs-lookup"><span data-stu-id="6f179-126">**BizTalk Operators Group**</span></span>|<span data-ttu-id="6f179-127">Afficher le nom du groupe d'opérateurs disposant des droits nécessaires à l'affichage de la configuration, l'exécution de requêtes, la maintenance des ordinateurs et l'analyse de base des applications.</span><span class="sxs-lookup"><span data-stu-id="6f179-127">Displays the name of the operators group that has rights to view configuration, run queries, and perform computer maintenance and basic application monitoring.</span></span>|  
    |<span data-ttu-id="6f179-128">**Opérateurs B2B de BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="6f179-128">**BizTalk Server B2B Operators**</span></span>|<span data-ttu-id="6f179-129">Afficher le nom du groupe des opérateurs interentreprises.</span><span class="sxs-lookup"><span data-stu-id="6f179-129">Displays the name of the B2B operators group.</span></span>|  
  
4.  <span data-ttu-id="6f179-130">Sur le **bases de données** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="6f179-130">On the **Databases** tab, do the following:</span></span>  
  
    |<span data-ttu-id="6f179-131">Utiliser</span><span class="sxs-lookup"><span data-stu-id="6f179-131">Use this</span></span>|<span data-ttu-id="6f179-132">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="6f179-132">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="6f179-133">**Bases de données**</span><span class="sxs-lookup"><span data-stu-id="6f179-133">**Databases**</span></span>|<span data-ttu-id="6f179-134">Afficher le nom de toutes les bases de données dans l'application et sur les serveurs où elles résident, tel que spécifié lors de la configuration.</span><span class="sxs-lookup"><span data-stu-id="6f179-134">Displays the names of all databases in the application and the servers on which they reside, as specified during configuration.</span></span>|  
  
5.  <span data-ttu-id="6f179-135">Sur le **certificat** onglet, procédez comme suit, puis cliquez sur **OK**:</span><span class="sxs-lookup"><span data-stu-id="6f179-135">On the **Certificate** tab, do the following, and then click **OK**:</span></span>  
  
    |<span data-ttu-id="6f179-136">Utiliser</span><span class="sxs-lookup"><span data-stu-id="6f179-136">Use this</span></span>|<span data-ttu-id="6f179-137">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="6f179-137">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="6f179-138">**Nom commun**</span><span class="sxs-lookup"><span data-stu-id="6f179-138">**Common Name**</span></span>|<span data-ttu-id="6f179-139">Afficher une description du certificat sélectionné.</span><span class="sxs-lookup"><span data-stu-id="6f179-139">Displays a description of the selected certificate.</span></span>|  
    |<span data-ttu-id="6f179-140">**Empreinte numérique**</span><span class="sxs-lookup"><span data-stu-id="6f179-140">**Thumbprint**</span></span>|<span data-ttu-id="6f179-141">Afficher l'empreinte du certificat de clé privée utilisé pour appliquer une signature numérique aux messages sortants de ce groupe.</span><span class="sxs-lookup"><span data-stu-id="6f179-141">Displays the thumbprint of the private key certificate that is used to digitally sign outbound messages from this group.</span></span> <span data-ttu-id="6f179-142">Le format de l'empreinte de certificat est HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, où H est une valeur hexadécimale (nombre de 0 à 9 ou lettre de A à F).</span><span class="sxs-lookup"><span data-stu-id="6f179-142">The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit (a number from 0 through 9 or a letter from A through F).</span></span>|  
    |<span data-ttu-id="6f179-143">**Supprimer le certificat**</span><span class="sxs-lookup"><span data-stu-id="6f179-143">**Remove certificate**</span></span>|<span data-ttu-id="6f179-144">Cliquer pour supprimer le certificat affiché.</span><span class="sxs-lookup"><span data-stu-id="6f179-144">Click to remove the displayed certificate.</span></span>|  
    |<span data-ttu-id="6f179-145">**Parcourir**</span><span class="sxs-lookup"><span data-stu-id="6f179-145">**Browse**</span></span>|<span data-ttu-id="6f179-146">Cliquez pour afficher les **sélectionner un certificat** boîte de dialogue, dans laquelle vous sélectionnez le certificat de signature pour l’utilisateur actuel ou le magasin personnel à utiliser avec le groupe.</span><span class="sxs-lookup"><span data-stu-id="6f179-146">Click to display the **Select Certificate** dialog box, where you select the signature certificate for the current user or personal store you want to use with the group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6f179-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f179-147">See Also</span></span>  
 <span data-ttu-id="6f179-148">[Gestion des groupes](../core/managing-groups.md) </span><span class="sxs-lookup"><span data-stu-id="6f179-148">[Managing Groups](../core/managing-groups.md) </span></span>  
 <span data-ttu-id="6f179-149">[Groupes BizTalk](../core/biztalk-groups.md) </span><span class="sxs-lookup"><span data-stu-id="6f179-149">[BizTalk Groups](../core/biztalk-groups.md) </span></span>  
 <span data-ttu-id="6f179-150">[Comment ajouter un serveur à un groupe](../core/how-to-add-a-server-to-a-group.md) </span><span class="sxs-lookup"><span data-stu-id="6f179-150">[How to Add a Server to a Group](../core/how-to-add-a-server-to-a-group.md) </span></span>  
 <span data-ttu-id="6f179-151">[Comment déplacer un serveur à partir d’un groupe à un autre](../core/how-to-move-a-server-from-one-group-to-another.md) </span><span class="sxs-lookup"><span data-stu-id="6f179-151">[How to Move a Server from One Group to Another](../core/how-to-move-a-server-from-one-group-to-another.md) </span></span>  
 [<span data-ttu-id="6f179-152">Comment supprimer un serveur d’un groupe</span><span class="sxs-lookup"><span data-stu-id="6f179-152">How to Remove a Server from a Group</span></span>](../core/how-to-remove-a-server-from-a-group.md)