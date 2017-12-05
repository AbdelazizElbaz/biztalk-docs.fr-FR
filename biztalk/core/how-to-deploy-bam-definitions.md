---
title: "Comment déployer des définitions BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, definitions [BAM]
- managing [BAM definitions], deploying definitions
- definitions [BAM], deploying
- Deploy-All command [BAM]
ms.assetid: 02b8888c-6f6c-45dd-8445-6e507a02f5f0
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 094a37d90db41e505adeaec3a31ece9128785e04
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-deploy-bam-definitions"></a><span data-ttu-id="8dca5-102">Déploiement de définitions BAM</span><span class="sxs-lookup"><span data-stu-id="8dca5-102">How to Deploy BAM Definitions</span></span>
<span data-ttu-id="8dca5-103">Les administrateurs utilisent la **déployer-all** commande d’utilitaire de gestion BAM pour déployer une définition BAM à partir du classeur Excel ou le fichier de définitions XML exporté à partir du classeur.</span><span class="sxs-lookup"><span data-stu-id="8dca5-103">Administrators use the **deploy-all** BAM Management utility command to deploy a BAM definition from the Excel workbook or the XML definitions file exported from the workbook.</span></span> <span data-ttu-id="8dca5-104">Lorsque vous effectuez une installation complète de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], l'Assistant Configuration configure automatiquement le fichier XML de configuration BAM.</span><span class="sxs-lookup"><span data-stu-id="8dca5-104">When you perform a complete installation of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the Configuration Wizard automatically configures the BAM Configuration XML.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8dca5-105">Si plusieurs utilisateurs travaillent avec le complément BAM pour Excel, ils doivent tous utiliser la même version de Microsoft Data Access Components (MDAC).</span><span class="sxs-lookup"><span data-stu-id="8dca5-105">If multiple users are working with the BAM Add-In for Excel, we recommend that they have the same version of Microsoft Data Access Components (MDAC).</span></span> <span data-ttu-id="8dca5-106">À défaut, des problèmes de compatibilité risquent de se présenter.</span><span class="sxs-lookup"><span data-stu-id="8dca5-106">Otherwise, compatibility issues may arise.</span></span> <span data-ttu-id="8dca5-107">Notamment, si vous créez un modèle sur un ordinateur équipé de la dernière version de MDAC et que vous essayez ensuite de l'ouvrir sur un ordinateur équipé d'une version plus ancienne, une erreur du compilateur se produit.</span><span class="sxs-lookup"><span data-stu-id="8dca5-107">Specifically, if you create a template on a computer with a newer version of MDAC and then attempt to open it on a computer with an older version of MDAC, a compiler error will occur.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8dca5-108">Vous pouvez utiliser un seul élément de données (« ville » par exemple) par dimension de données (« situation géographique » par exemple).</span><span class="sxs-lookup"><span data-stu-id="8dca5-108">You can use only one data item (for example, City) per data dimension (for example, Location).</span></span> <span data-ttu-id="8dca5-109">Ensuite, vous ne pouvez plus utiliser l'élément « ville » dans une autre dimension telle que la dimension « région ».</span><span class="sxs-lookup"><span data-stu-id="8dca5-109">You cannot use City again in another data dimension, such as Region.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8dca5-110">Il est recommandé de vérifier la sécurité des classeurs Excel (.xls) du composant BAM avant de les déployer.</span><span class="sxs-lookup"><span data-stu-id="8dca5-110">We recommend that you verify the security of BAM Excel workbooks (.xls) before you deploy them.</span></span> <span data-ttu-id="8dca5-111">Pour cela, utilisez Excel sur l'ordinateur d'administration.</span><span class="sxs-lookup"><span data-stu-id="8dca5-111">You use Excel on the administration computer to verify the security of BAM Excel workbooks.</span></span> <span data-ttu-id="8dca5-112">Avant de déployer un classeur, ouvrez-le et garantir la sécurité des macros est définie sur élevé, et qu’il n’y a pas d’avertissements.</span><span class="sxs-lookup"><span data-stu-id="8dca5-112">Before you deploy a workbook, open it and ensure the macro security is set to high, and that there are no warnings.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8dca5-113">Dans les bases de données BAM, le « BAM_\<... \>« convention d’affectation de noms est réservée pour toutes les entités SQL (tables, index, procédures stockées, rôles, etc....). *Ne le faites pas* cette convention d’affectation de noms permet de créer des entités SQL ; une telle utilisation peut entraîner un comportement non défini.</span><span class="sxs-lookup"><span data-stu-id="8dca5-113">In BAM databases, the “BAM_\<...\>” naming convention is reserved for all SQL entities (tables, indexes, stored procedures, roles, etc...). *Do not* use this naming convention to create any SQL entities; such a usage might result in an undefined behavior.</span></span>  
  
 <span data-ttu-id="8dca5-114">Avant de déployer un fichier XML de définition BAM, vous devez vous assurer que les paramètres régionaux utilisés lors de sa création correspondent à ceux de l'ordinateur où vous le déployez.</span><span class="sxs-lookup"><span data-stu-id="8dca5-114">Before you can deploy a BAM definition XML file, you must ensure that the locale used to create this file matches the locale of the computer on which you are deploying it.</span></span> <span data-ttu-id="8dca5-115">Par exemple, si vous créez le fichier sur un ordinateur exécutant une version japonaise de Microsoft Windows, les paramètres régionaux de l'ordinateur où vous effectuez le déploiement du fichier doivent également être définis sur Japonais.</span><span class="sxs-lookup"><span data-stu-id="8dca5-115">For example, if you create the file on a computer running a Japanese version of Microsoft Windows, the computer you deploy the file on must be set to the Japanese locale.</span></span> <span data-ttu-id="8dca5-116">Si ces paramètres ne correspondent pas, vous devez modifier en conséquence les paramètres régionaux de l'ordinateur où vous exécutez l'utilitaire de gestion de l'analyse BAM, puis redémarrer l'ordinateur avant de lancer l'utilitaire.</span><span class="sxs-lookup"><span data-stu-id="8dca5-116">If the file and the computer settings do not match, you must switch the computer you use to run the BAM Management utility to the correct locale and you must restart it before running the utility.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8dca5-117">Le fichier XML de définition BAM ne peut pas contenir de texte en plusieurs langues à moins que ces langues utilisent le même codepage, ou que seules deux langues soient utilisées, dont l'anglais.</span><span class="sxs-lookup"><span data-stu-id="8dca5-117">The BAM definition XML file cannot contain text in multiple languages unless the languages all use the same codepage, or only two languages are included and one of them is English.</span></span>  
  
 <span data-ttu-id="8dca5-118">Pour plus d'informations sur la modification des paramètres régionaux de votre ordinateur, reportez-vous à l'aide de votre système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="8dca5-118">For information about changing locale settings on your computer, see the Help for your operating system.</span></span>  
  
### <a name="to-deploy-a-bam-definition"></a><span data-ttu-id="8dca5-119">Pour déployer une définition BAM</span><span class="sxs-lookup"><span data-stu-id="8dca5-119">To deploy a BAM definition</span></span>  
  
1.  <span data-ttu-id="8dca5-120">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8dca5-120">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="8dca5-121">Accédez au dossier des suivis en tapant **C:\Program Files\Microsoft BizTalk Server \<version\>\Tracking** à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="8dca5-121">Navigate to the tracking folder by typing **C:\Program Files\Microsoft BizTalk Server \<version\>\Tracking** at the command prompt.</span></span> <span data-ttu-id="8dca5-122">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="8dca5-122">Press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="8dca5-123">Type **bm déployer-all - DefinitionFile :\<fichier de définition BAM\>**.</span><span class="sxs-lookup"><span data-stu-id="8dca5-123">Type **bm deploy-all -DefinitionFile:\<BAM definition file\>**.</span></span>  
  
4.  <span data-ttu-id="8dca5-124">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="8dca5-124">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dca5-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8dca5-125">See Also</span></span>  
 <span data-ttu-id="8dca5-126">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="8dca5-126">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="8dca5-127">[Utilitaire de gestion BAM](../core/bam-management-utility.md) </span><span class="sxs-lookup"><span data-stu-id="8dca5-127">[BAM Management Utility](../core/bam-management-utility.md) </span></span>  
 [<span data-ttu-id="8dca5-128">Recommandations de sécurité pour les services BAM</span><span class="sxs-lookup"><span data-stu-id="8dca5-128">BAM Security Recommendations</span></span>](../core/bam-security-recommendations.md)