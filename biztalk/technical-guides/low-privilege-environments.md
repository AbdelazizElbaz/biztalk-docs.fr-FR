---
title: "Les environnements à faible privilège | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: abdc45d0-b63a-4b6c-80c4-1f8e87644cd9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d43f363bd96dd8e3109a8ce21b9565fb43e5f9bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="low-privilege-environments"></a><span data-ttu-id="d8ff1-102">Environnements avec privilèges faibles</span><span class="sxs-lookup"><span data-stu-id="d8ff1-102">Low-Privilege Environments</span></span>
<span data-ttu-id="d8ff1-103">Plusieurs flux de travail qui sont incluses avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration nécessitent des autorisations élevées pour exécuter certaines actions.</span><span class="sxs-lookup"><span data-stu-id="d8ff1-103">Several workflows that are included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack require elevated permissions to perform certain actions.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d8ff1-104">Pack d’administration vous permet de vous permet d’effectuer des fonctionnalités de surveillance de base dans un environnement à faible privilège.</span><span class="sxs-lookup"><span data-stu-id="d8ff1-104"> Management Pack enables you to perform basic monitoring functionalities in a low privilege environment.</span></span> <span data-ttu-id="d8ff1-105">Il existe deux rôles d’administration : l’administrateur du serveur BizTalk et l’opérateur de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d8ff1-105">There are two Administrative Roles: the BizTalk Server Administrator, and the BizTalk Server Operator.</span></span> <span data-ttu-id="d8ff1-106">Le rôle administrateur de BizTalk Server dispose de privilèges élevés lui donnant accès à des données de configuration et de suivi.</span><span class="sxs-lookup"><span data-stu-id="d8ff1-106">The BizTalk Server Administrator is a high privilege role with access to configuration and tracking data.</span></span> <span data-ttu-id="d8ff1-107">L’administrateur du serveur BizTalk peuvent effectuer toutes les tâches administratives clés telle l’inscription et le démarrage des artefacts.</span><span class="sxs-lookup"><span data-stu-id="d8ff1-107">The BizTalk Server Administrator can perform all key administrative tasks such enlisting and starting artifacts.</span></span> <span data-ttu-id="d8ff1-108">Le rôle opérateur de BizTalk Server dispose de privilèges restreints lui donnant uniquement accès aux opérations de surveillance et de dépannage.</span><span class="sxs-lookup"><span data-stu-id="d8ff1-108">The BizTalk Server Operator is a low privilege role with access only to monitoring and troubleshooting actions.</span></span> <span data-ttu-id="d8ff1-109">Pour plus d’informations, consultez [autorisations de sécurité minimales](http://technet.microsoft.com/library/aa559845\(BTS.80\).aspx).</span><span class="sxs-lookup"><span data-stu-id="d8ff1-109">For more information, see [Minimum Security User Rights](http://technet.microsoft.com/library/aa559845\(BTS.80\).aspx).</span></span>  
  
 <span data-ttu-id="d8ff1-110">À l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration :</span><span class="sxs-lookup"><span data-stu-id="d8ff1-110">Using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack:</span></span>  
  
-   <span data-ttu-id="d8ff1-111">Les membres du groupe Opérateurs BizTalk Server peuvent effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d8ff1-111">Members of the BizTalk Server Operators group can do the following:</span></span>  
  
    -   <span data-ttu-id="d8ff1-112">Analyser BizTalk Server pour les erreurs, recherchez des messages ou instances suspendus, afficher la configuration.</span><span class="sxs-lookup"><span data-stu-id="d8ff1-112">Monitor BizTalk Server for errors, query for suspended messages\instances, view configuration.</span></span>  
  
    -   <span data-ttu-id="d8ff1-113">Surveiller les installations de BizTalk Server et les artefacts.</span><span class="sxs-lookup"><span data-stu-id="d8ff1-113">Monitor BizTalk Server installations and artifacts.</span></span>  
  
    -   <span data-ttu-id="d8ff1-114">Afficher l'état et le flux de messages du service.</span><span class="sxs-lookup"><span data-stu-id="d8ff1-114">View service state and message flow.</span></span>  
  
    -   <span data-ttu-id="d8ff1-115">Démarrer ou arrêter des applications et des artefacts tels que les orchestrations, ports d’envoi ou envoyer des groupes de ports qui sont dans un état inscrit.</span><span class="sxs-lookup"><span data-stu-id="d8ff1-115">Start or stop applications and artifacts such as orchestrations, send ports or send port groups that are in an enlisted state.</span></span>  
  
    -   <span data-ttu-id="d8ff1-116">Activer ou désactiver des emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="d8ff1-116">Enable or disable receive locations.</span></span> <span data-ttu-id="d8ff1-117">Les modifications ne sont pas prises en compte avant la fin de l'intervalle d'actualisation du cache de 60 secondes (intervalle par défaut).</span><span class="sxs-lookup"><span data-stu-id="d8ff1-117">The changes do not take effect until the next cache refresh interval of 60 seconds, which is the default.</span></span> <span data-ttu-id="d8ff1-118">Cet intervalle est défini au niveau du groupe BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d8ff1-118">The cache refresh interval is set at the BizTalk Server group level.</span></span>  
  
-   <span data-ttu-id="d8ff1-119">Les membres du groupe Opérateurs BizTalk Server ne peuvent pas effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d8ff1-119">Members of the BizTalk Server Operators group cannot do the following:</span></span>  
  
    -   <span data-ttu-id="d8ff1-120">Modifier la configuration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d8ff1-120">Modify the configuration for BizTalk Server.</span></span>  
  
    -   <span data-ttu-id="d8ff1-121">Afficher les propriétés de contexte de message marquées comme informations d'identification personnelle ou les corps de message.</span><span class="sxs-lookup"><span data-stu-id="d8ff1-121">View message context properties classified as Personally Identifiable Information (PII) or message bodies.</span></span>  
  
    -   <span data-ttu-id="d8ff1-122">Modifier le routage des messages, par exemple supprimer ou ajouter des abonnements au système en cours d'exécution, ou publier des messages dans un composant d'exécution BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d8ff1-122">Modify the course of message routing, such as removing or adding new subscriptions to the running system, including the ability to publish messages into the BizTalk Server runtime.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d8ff1-123">Pour effectuer toutes les tâches de surveillance fournies par le Pack d’administration telles que le redémarrage du service BTSNTSvc.exe, vous devez être membre du groupe Administrateurs local sur les serveurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d8ff1-123">To perform all monitoring tasks provided by the Management Pack such as restarting BTSNTSvc.exe service, you must be a member of the local Administrators group on the BizTalk Servers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d8ff1-124">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="d8ff1-124">In this section</span></span>  
  
-   [<span data-ttu-id="d8ff1-125">Surveillance</span><span class="sxs-lookup"><span data-stu-id="d8ff1-125">Monitoring</span></span>](../technical-guides/monitoring.md)  
  
-   [<span data-ttu-id="d8ff1-126">Découvertes</span><span class="sxs-lookup"><span data-stu-id="d8ff1-126">Discoveries</span></span>](../technical-guides/discoveries.md)