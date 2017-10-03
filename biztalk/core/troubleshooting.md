---
title: "Problèmes connus et dépannage | Documents Microsoft"
description: "Problèmes connus, zombies, résoudre les problèmes de performances, résoudre les problèmes des cartes, résoudre les problèmes d’autorisations, résoudre les problèmes d’EDI et AS2 et bien plus encore dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecb934c6-3efa-40b6-949b-a04a73e60b07
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df13438e641d55de91096b690a8e5e95e26cbfa4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting"></a><span data-ttu-id="38a5e-103">Dépannage</span><span class="sxs-lookup"><span data-stu-id="38a5e-103">Troubleshooting</span></span>

## <a name="overview"></a><span data-ttu-id="38a5e-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="38a5e-104">Overview</span></span>
<span data-ttu-id="38a5e-105">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] exploite ou peut dépendre de plusieurs technologies Microsoft, notamment, mais sans s'y limiter, Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)], Microsoft Internet Information Services (IIS), Microsoft Windows Server Cluster, Microsoft Enterprise Single Sign-On et Windows [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="38a5e-105">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] makes use of or may depend on several different Microsoft technologies including but not limited to Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], the Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)], Internet Information Services (IIS), Microsoft Windows Server Cluster, Enterprise Single Sign-On, and Windows [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].</span></span> <span data-ttu-id="38a5e-106">Étant donné que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] met en œuvre un grand nombre de technologies différentes, la résolution des problèmes dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] implique souvent de s'attaquer à la dépendance ou à la technologie sous-jacente utilisée.</span><span class="sxs-lookup"><span data-stu-id="38a5e-106">Because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is used with so many other technologies, troubleshooting a problem with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] often involves troubleshooting the underlying technology or dependency that is being used.</span></span> <span data-ttu-id="38a5e-107">Cette rubrique propose des informations de dépannage des problèmes spécifiques à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que des informations de résolution des problèmes pouvant survenir dans les logiciels de dépendance de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="38a5e-107">This section provides information about troubleshooting specific [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] problems and information about troubleshooting problems that can occur in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dependency software.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="38a5e-108">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="38a5e-108">Next steps</span></span> 
  
-   [<span data-ttu-id="38a5e-109">Problèmes connus avec BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="38a5e-109">Known Issues with BizTalk Server</span></span>](../core/known-issues-with-biztalk-server.md)  

-   [<span data-ttu-id="38a5e-110">Zombies dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="38a5e-110">Zombies in BizTalk Server</span></span>](zombies-in-biztalk-server.md)
  
-   [<span data-ttu-id="38a5e-111">Résoudre les problèmes d’Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="38a5e-111">Troubleshoot BizTalk Server Administration</span></span>](../core/troubleshooting-biztalk-server-administration.md)  
  
-   [<span data-ttu-id="38a5e-112">Activation de la journalisation de System.Net</span><span class="sxs-lookup"><span data-stu-id="38a5e-112">Enabling System.Net Logging</span></span>](../core/enabling-system-net-logging.md)  
  
-   [<span data-ttu-id="38a5e-113">Résoudre les problèmes d’autorisations BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="38a5e-113">Troubleshoot BizTalk Server Permissions</span></span>](../core/troubleshooting-biztalk-server-permissions.md)  
  
-   [<span data-ttu-id="38a5e-114">Résoudre les problèmes de performances de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="38a5e-114">Troubleshoot BizTalk Server Performance</span></span>](../core/troubleshooting-biztalk-server-performance.md)  
  
-   [<span data-ttu-id="38a5e-115">Résoudre les problèmes d’adaptateurs BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="38a5e-115">Troubleshoot BizTalk Server Adapters</span></span>](../core/troubleshooting-biztalk-server-adapters.md)  
  
-   [<span data-ttu-id="38a5e-116">Résoudre les problèmes des Solutions EDI et AS2</span><span class="sxs-lookup"><span data-stu-id="38a5e-116">Troubleshoot EDI and AS2 Solutions</span></span>](../core/troubleshooting-edi-and-as2-solutions.md)  
  
-   [<span data-ttu-id="38a5e-117">Résoudre les dépendances de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="38a5e-117">Troubleshoot BizTalk Server Dependencies</span></span>](../core/troubleshooting-biztalk-server-dependencies.md)  
  
-   [<span data-ttu-id="38a5e-118">Résoudre les problèmes de Configuration</span><span class="sxs-lookup"><span data-stu-id="38a5e-118">Troubleshoot Configuration</span></span>](../core/troubleshooting-configuration.md)  
  
-   [<span data-ttu-id="38a5e-119">Obtenir une image mémoire d’un processus BizTalk</span><span class="sxs-lookup"><span data-stu-id="38a5e-119">Get a Memory Dump of a BizTalk Process</span></span>](../core/how-to-capture-a-memory-dump-of-a-biztalk-process.md)  
  
-   [<span data-ttu-id="38a5e-120">Outils et utilitaires</span><span class="sxs-lookup"><span data-stu-id="38a5e-120">Tools and Utilities</span></span>](../core/tools-and-utilities-to-use-for-troubleshooting.md)  
  
-   [<span data-ttu-id="38a5e-121">Résoudre les échecs de Validation de Message à l’aide du contenu hexadécimal de Messages de suspendu</span><span class="sxs-lookup"><span data-stu-id="38a5e-121">Troubleshoot Message Validation Failures using the Hexadecimal Contents of Suspended Messages</span></span>](../core/troubleshoot-message-validation-failures-using-the-hexadecimal-contents.md)

- [<span data-ttu-id="38a5e-122">Erreurs et événements</span><span class="sxs-lookup"><span data-stu-id="38a5e-122">Events and Errors</span></span>](events-and-errors2.md)