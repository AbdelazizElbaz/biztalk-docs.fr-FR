---
title: Résumé de la sécurité | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security
ms.assetid: 357ebf63-a35e-4ce4-a754-be880946f9fc
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5d327de93941278b9b1dcecc9378183c6a2f77a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-summary"></a><span data-ttu-id="55c4c-102">Résumé de la sécurité</span><span class="sxs-lookup"><span data-stu-id="55c4c-102">Security Summary</span></span>
## <a name="overview"></a><span data-ttu-id="55c4c-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="55c4c-103">Overview</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="55c4c-104">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] fournit des composants de développement et d’exécution pour faciliter les applications BizTalk qui fournissent des fonctionnalités de messagerie et d’automatisation de SWIFT.</span><span class="sxs-lookup"><span data-stu-id="55c4c-104"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provides development and runtime components to facilitate BizTalk applications that provide SWIFT messaging and automation functionality.</span></span> <span data-ttu-id="55c4c-105">Les applications développées à l’aide de [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] sont des applications BizTalk et qui sont sécurisés par natif [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)], [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)], [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)]et IIS/ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] fonctionnalités de sécurité.</span><span class="sxs-lookup"><span data-stu-id="55c4c-105">Applications developed by using [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] are BizTalk applications and are secured by native [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)], [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)], [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)], and IIS/ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] security features.</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="55c4c-106">protège la confidentialité des éléments du système à l’aide des protocoles et des normes des communications Internet chiffré de fait.</span><span class="sxs-lookup"><span data-stu-id="55c4c-106"> protects privacy of system elements by using de facto Internet encrypted communications standards and protocols.</span></span> <span data-ttu-id="55c4c-107">Participants de la communication, les processus et les informations sont sécurisées à l’aide de certificats de signature, [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] l’authentification et Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="55c4c-107">Communication participants, processes, and information are secured by using signing certificates, [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Authentication, and Enterprise Single Sign-On.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="55c4c-108">garantit également l’autorisation d’utilisation des ressources avec des mécanismes tels que [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] rôles et [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] l’authentification et la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="55c4c-108"> also enforces authorization of resource usage with mechanisms such as [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] Roles and [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Authentication, and the MessageBox database.</span></span>  
  
 <span data-ttu-id="55c4c-109">En plus de natif [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] fonctionnalités de sécurité, [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] définit et applique une sémantique de sécurité pour la création, de réparation, l’approbation et envoi des messages SWIFT par les utilisateurs professionnels.</span><span class="sxs-lookup"><span data-stu-id="55c4c-109">In addition to native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] security features, [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] defines and enforces security semantics for the creation, repair, approval, and submission of SWIFT messages by business users.</span></span> <span data-ttu-id="55c4c-110">Cette sécurité au niveau utilisateur est appliquée à l’aide de [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] sur la station de travail et les certificats et les données intégrité vérification de l’utilisateur par les technologies de signature numérique [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] services d’exécution sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="55c4c-110">This user-level security is enforced by using [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] digital signing technologies on the user workstation, and certificate and data integrity verification by [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] runtime services on the server.</span></span>  
  
 <span data-ttu-id="55c4c-111">Ensemble, [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] fournissent la plateforme, l’infrastructure et outils de conception, le développement et l’exécution de sécurisent SWIFT systèmes d’automatisation de la messagerie et de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="55c4c-111">Together, [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provide the platform, infrastructure, and tools for designing, developing, and executing secure SWIFT messaging and workflow automation systems.</span></span>  
  
## <a name="more-information"></a><span data-ttu-id="55c4c-112">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="55c4c-112">More information</span></span>  
 <span data-ttu-id="55c4c-113">Pour plus d’informations sur les meilleures pratiques de sécurité, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="55c4c-113">For information about security best practices, see the following:</span></span>  
  
-   <span data-ttu-id="55c4c-114">Centre de ressources de sécurité TechNet :</span><span class="sxs-lookup"><span data-stu-id="55c4c-114">TechNet Security Resource Center:</span></span>  
  
     [<span data-ttu-id="55c4c-115">http://go.Microsoft.com/fwlink/p/?LinkId=27741</span><span class="sxs-lookup"><span data-stu-id="55c4c-115">http://go.microsoft.com/fwlink/p/?LinkId=27741</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=27741)  
  

-   <span data-ttu-id="55c4c-116">Guide de sécurité de Symantec montrant comment utiliser leurs outils pour implémenter les meilleures pratiques décrites dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Guide des opérations de sécurité pour [!INCLUDE[btsWin2kSvr](../../includes/btswin2ksvr-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="55c4c-116">Symantec security guide showing how to use their tools to implement the best practices described in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Security Operations Guide for [!INCLUDE[btsWin2kSvr](../../includes/btswin2ksvr-md.md)]:</span></span>  
  
     [<span data-ttu-id="55c4c-117">http://go.Microsoft.com/fwlink/p/?LinkId=28274</span><span class="sxs-lookup"><span data-stu-id="55c4c-117">http://go.microsoft.com/fwlink/p/?LinkId=28274</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=28274)  

  
-   <span data-ttu-id="55c4c-118">Plus d’informations sur la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Service de Notification de sécurité :</span><span class="sxs-lookup"><span data-stu-id="55c4c-118">Information about the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Security Notification Service:</span></span>  
  
     [<span data-ttu-id="55c4c-119">http://go.Microsoft.com/fwlink/p/?LinkId=27744</span><span class="sxs-lookup"><span data-stu-id="55c4c-119">http://go.microsoft.com/fwlink/p/?LinkId=27744</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=27744)  
  
  
## <a name="see-also"></a><span data-ttu-id="55c4c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55c4c-120">See Also</span></span>  
[<span data-ttu-id="55c4c-121">Runtime, la réparation de messages, la réponse FIN et la messagerie</span><span class="sxs-lookup"><span data-stu-id="55c4c-121">Runtime, message repair, FIN response, and messaging</span></span>](../../adapters-and-accelerators/accelerator-swift/runtime-message-repair-fin-response-and-messaging.md)