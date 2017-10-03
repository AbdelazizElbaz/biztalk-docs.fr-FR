---
title: Commande ListTypes | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 94febe8a-4c1e-4581-a6d1-ef579633e745
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: afe2519fc5507ae0975d050a998faec78f2940a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="listtypes-command"></a><span data-ttu-id="b8505-102">Commande ListTypes</span><span class="sxs-lookup"><span data-stu-id="b8505-102">ListTypes Command</span></span>
<span data-ttu-id="b8505-103">Répertorie tous les types d’artefacts que vous pouvez ajouter à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l’aide de la **AddResource** commande.</span><span class="sxs-lookup"><span data-stu-id="b8505-103">Lists all of the artifact types that you can add to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] by using the **AddResource** command.</span></span> <span data-ttu-id="b8505-104">Pour plus d’informations sur la **AddResource** command, consultez [commande AddResource](../core/addresource-command.md).</span><span class="sxs-lookup"><span data-stu-id="b8505-104">For more information about the **AddResource** command, see [AddResource Command](../core/addresource-command.md).</span></span>  
  
 <span data-ttu-id="b8505-105">Les noms complets des types d'artefact pris en charge sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="b8505-105">The fully qualified names of the supported artifact types are as follows:</span></span>  
  
-   <span data-ttu-id="b8505-106">Assembly .NET : System.BizTalk : assembly</span><span class="sxs-lookup"><span data-stu-id="b8505-106">.NET assembly: System.BizTalk:Assembly</span></span>  
  
-   <span data-ttu-id="b8505-107">Définition BAM : System.BizTalk : BAM</span><span class="sxs-lookup"><span data-stu-id="b8505-107">BAM definition: System.BizTalk:Bam</span></span>  
  
-   <span data-ttu-id="b8505-108">L’assembly BizTalk : System.BizTalk : BiztalkAssembly</span><span class="sxs-lookup"><span data-stu-id="b8505-108">BizTalk assembly: System.BizTalk:BizTalkAssembly</span></span>  
  
-   <span data-ttu-id="b8505-109">Fichier de liaison BizTalk : System.BizTalk : biztalkbinding</span><span class="sxs-lookup"><span data-stu-id="b8505-109">BizTalk binding file: System.BizTalk:BizTalkBinding</span></span>  
  
-   <span data-ttu-id="b8505-110">Certificat de sécurité : System.BizTalk : Certificate</span><span class="sxs-lookup"><span data-stu-id="b8505-110">Security certificate: System.BizTalk:Certificate</span></span>  
  
-   <span data-ttu-id="b8505-111">Composant COM : System.BizTalk : com</span><span class="sxs-lookup"><span data-stu-id="b8505-111">COM component: System.BizTalk:Com</span></span>  
  
-   <span data-ttu-id="b8505-112">Fichier ad hoc : System.BizTalk : file</span><span class="sxs-lookup"><span data-stu-id="b8505-112">Ad hoc file: System.BizTalk:File</span></span>  
  
-   <span data-ttu-id="b8505-113">Script de post-traitement : System.BizTalk : postprocessingscript</span><span class="sxs-lookup"><span data-stu-id="b8505-113">Postprocessing script: System.BizTalk:PostProcessingScript</span></span>  
  
-   <span data-ttu-id="b8505-114">Script de prétraitement : System.BizTalk : preprocessingscript</span><span class="sxs-lookup"><span data-stu-id="b8505-114">Preprocessing script: System.BizTalk:PreProcessingScript</span></span>  
  
-   <span data-ttu-id="b8505-115">Stratégie ou règle : System.BizTalk : Rules</span><span class="sxs-lookup"><span data-stu-id="b8505-115">Policy or rule: System.BizTalk:Rules</span></span>  
  
-   <span data-ttu-id="b8505-116">Répertoire virtuel : System.BizTalk : WebDirectory</span><span class="sxs-lookup"><span data-stu-id="b8505-116">Virtual directory: System.BizTalk:WebDirectory</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8505-117">Pour éviter des conflits au niveau des espaces de noms, utilisez systématiquement le nom de type complet (System.BizTalk:Assembly, par exemple) et pas le nom du type uniquement (Assembly).</span><span class="sxs-lookup"><span data-stu-id="b8505-117">To avoid namespace conflicts, you should always use the full type name (such as System.BizTalk:Assembly) rather than the type name alone (such as Assembly).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="b8505-118">Utilisation</span><span class="sxs-lookup"><span data-stu-id="b8505-118">Usage</span></span>  
 <span data-ttu-id="b8505-119">**BTSTask ListTypes**</span><span class="sxs-lookup"><span data-stu-id="b8505-119">**BTSTask ListTypes**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8505-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8505-120">See Also</span></span>  
 [<span data-ttu-id="b8505-121">Référence de ligne de commande BTSTask</span><span class="sxs-lookup"><span data-stu-id="b8505-121">BTSTask Command-Line Reference</span></span>](../core/btstask-command-line-reference.md)