---
title: "L’utilisation de l’Agent de gestion ENTSSO | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c89b494-db12-4d2a-a030-6acd34489cab
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03c0f7d2c04a2707cf965f64ff7a559d8642a12c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-entsso-management-agent"></a><span data-ttu-id="df469-102">Utilisation de l'agent de gestion ENTSSO</span><span class="sxs-lookup"><span data-stu-id="df469-102">How to Use the ENTSSO Management Agent</span></span>
<span data-ttu-id="df469-103">Cette version de l'authentification unique de l'entreprise contient un agent de gestion pour Microsoft Identity Integration Server (MIIS), qui intègre l'authentification unique de l'entreprise aux fonctionnalités de synchronisation de comptes de MIIS.</span><span class="sxs-lookup"><span data-stu-id="df469-103">This version of Enterprise Single Sign-On (SSO) contains a Management Agent (MA) for Microsoft Identity Integration Server (MIIS), which integrates Enterprise SSO with the account synchronization capabilities of MIIS.</span></span> <span data-ttu-id="df469-104">Un administrateur MIIS est ainsi en mesure de gérer les mappages SSO dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="df469-104">This enables an MIIS administrator to manage SSO mappings in the SSO Database.</span></span>  
  
 <span data-ttu-id="df469-105">Dans l’authentification unique de l’entreprise, les mappages sont créés entre les comptes de domaine Windows (*domainname\username*) et les informations d’identification externes.</span><span class="sxs-lookup"><span data-stu-id="df469-105">In Enterprise SSO, mappings are created between Windows Domain accounts (*domainname\username*) and external credentials.</span></span> <span data-ttu-id="df469-106">Si vous avez un Agent de gestion Active Directory et l’Agent de gestion pour la Source de données externe (exemple : agent de gestion RACF), vous pouvez utiliser l’agent de gestion (agent de gestion ENTSSO) de Enterprise SSO pour gérer les mappages dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="df469-106">If you have an Active Directory Management Agent, and the Management Agent for the external Data Source (example: RACF MA), you can use the Enterprise SSO MA (ENTSSO MA) to manage mappings in the SSO Database.</span></span> <span data-ttu-id="df469-107">Agent de gestion ENTSSO est un *exportation appel* Agent de gestion uniquement.</span><span class="sxs-lookup"><span data-stu-id="df469-107">ENTSSO MA is a *Call-Based Export* Management Agent only.</span></span>  
  
 <span data-ttu-id="df469-108">Vous configurez l'agent de gestion en trois parties distinctes :</span><span class="sxs-lookup"><span data-stu-id="df469-108">You configure the Management Agent in three separate parts:</span></span>  
  
-   <span data-ttu-id="df469-109">un fichier de configuration (ENTSSO.xml) ;</span><span class="sxs-lookup"><span data-stu-id="df469-109">A configuration file (ENTSSO.xml)</span></span>  
  
-   <span data-ttu-id="df469-110">l'interface utilisateur MIIS ;</span><span class="sxs-lookup"><span data-stu-id="df469-110">The MIIS user interface</span></span>  
  
-   <span data-ttu-id="df469-111">l'interface utilisateur de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="df469-111">The ENTSSO user interface</span></span>  
  
 <span data-ttu-id="df469-112">Les rubriques de cette section décrivent le processus de configuration.</span><span class="sxs-lookup"><span data-stu-id="df469-112">The topics in this section describe the configuration process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="df469-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="df469-113">In This Section</span></span>  
  
-   [<span data-ttu-id="df469-114">Configuration du fichier XML</span><span class="sxs-lookup"><span data-stu-id="df469-114">Configuring the XML File</span></span>](../core/configuring-the-xml-file.md)  
  
-   [<span data-ttu-id="df469-115">Comment configurer MIIS pour l’agent de gestion ENTSSO</span><span class="sxs-lookup"><span data-stu-id="df469-115">How to Configure MIIS for ENTSSO MA</span></span>](../core/how-to-configure-miis-for-entsso-ma.md)  
  
-   [<span data-ttu-id="df469-116">Comment configurer le service ENTSSO pour la synchronisation de mot de passe MIIS</span><span class="sxs-lookup"><span data-stu-id="df469-116">How to Configure ENTSSO for MIIS Password Sync</span></span>](../core/how-to-configure-entsso-for-miis-password-sync.md)