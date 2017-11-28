---
title: "Profils d’identification | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98ac0a0c-91d8-4d12-aa40-2ad2e29ec784
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69fa6c9401f606619b2fb8d22d95ded48c18a092
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-as-profiles"></a><span data-ttu-id="60db6-102">Profils d’identification</span><span class="sxs-lookup"><span data-stu-id="60db6-102">Run As Profiles</span></span>
<span data-ttu-id="60db6-103">Lorsque BizTalk Server Core Library Management Pack est importé tout d’abord, il crée deux nouveaux profils d’identification :</span><span class="sxs-lookup"><span data-stu-id="60db6-103">When the BizTalk Server Core Library Management Pack is first imported, it creates two new Run As Profiles:</span></span>  
  
-   <span data-ttu-id="60db6-104">**Compte de découverte de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="60db6-104">**BizTalk Server Discovery Account**.</span></span> <span data-ttu-id="60db6-105">Ce profil est associé à toutes les détections des composants de rôles de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="60db6-105">This profile is associated with all discoveries of BizTalk Server role components.</span></span>  
  
-   <span data-ttu-id="60db6-106">**Compte de surveillance de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="60db6-106">**BizTalk Server Monitoring Account**.</span></span> <span data-ttu-id="60db6-107">Ce profil est associé à tous les moniteurs et tâches.</span><span class="sxs-lookup"><span data-stu-id="60db6-107">This profile is associated with all monitors and tasks.</span></span>  
  
 <span data-ttu-id="60db6-108">Par défaut, toutes les découvertes, moniteurs et tâches définies dans la valeur par défaut des packs d’administration de BizTalk Server à l’aide des comptes définis dans le « Compte d’Action par défaut » profil d’identification.</span><span class="sxs-lookup"><span data-stu-id="60db6-108">By default, all discoveries, monitors, and tasks defined in the BizTalk Server Management Packs default to using the accounts defined in the “Default Action Account” Run As Profile.</span></span>  <span data-ttu-id="60db6-109">Si le compte d’action par défaut d’un système donné ne dispose pas des autorisations nécessaires pour découvrir ou surveiller BizTalk, ces systèmes peuvent être liés aux informations d’identification plus spécifiques dans les BizTalk Server profils d’identification, qui ont accès à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="60db6-109">If the default action account for a given system does not have the necessary permissions to discover or monitor BizTalk, then those systems can be bound to more specific credentials in the BizTalk Server Run As Profiles, which do have access to BizTalk Server.</span></span>  
  
 <span data-ttu-id="60db6-110">Voici la procédure générique pour configurer des profils d’identification pour BizTalk Server :</span><span class="sxs-lookup"><span data-stu-id="60db6-110">The following are the generic steps to configure Run As Profiles for BizTalk Server:</span></span>  
  
### <a name="to-configure-run-as-profiles"></a><span data-ttu-id="60db6-111">Pour configurer des profils d’identification</span><span class="sxs-lookup"><span data-stu-id="60db6-111">To configure Run As profiles</span></span>  
  
1.  <span data-ttu-id="60db6-112">Déterminez le nom du ou des ordinateurs cibles où le compte d’action par défaut dispose de droits suffisants pour surveiller BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="60db6-112">Identify the name(s) of the target computer(s) where the default action account has insufficient rights to monitor BizTalk Server.</span></span>  
  
2.  <span data-ttu-id="60db6-113">Pour chaque système de créer ou utiliser un jeu existant d’informations d’identification qui disposent au moins les privilèges de BizTalk Server décrits dans le [les environnements à faible privilège](../technical-guides/low-privilege-environments.md) section de ce guide du Pack d’administration.</span><span class="sxs-lookup"><span data-stu-id="60db6-113">For each system create or use an existing set of credentials that have at least the BizTalk Server privileges discussed in the [Low-Privilege Environments](../technical-guides/low-privilege-environments.md) section of this management pack guide.</span></span>  
  
3.  <span data-ttu-id="60db6-114">Pour chaque ensemble d’informations d’identification identifié à l’étape 2, assurez-vous que les exécuter en tant que compte correspondant existe dans le groupe d’administration.</span><span class="sxs-lookup"><span data-stu-id="60db6-114">For each set of credentials identified in step 2, make sure that a corresponding Run As Account exists in the management group.</span></span> <span data-ttu-id="60db6-115">Créer le compte d’identification s’il est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="60db6-115">Create the Run As Account if it is necessary.</span></span>  
  
4.  <span data-ttu-id="60db6-116">Configurer les mappages entre les cibles et les exécuter en tant que compte (s) sur le **comptes d’identification** onglet de chacune des profils d’identification.</span><span class="sxs-lookup"><span data-stu-id="60db6-116">Set up the mappings between the targets and the Run As Account(s) on the **Run As Accounts** tab of each of the Run As Profiles.</span></span>