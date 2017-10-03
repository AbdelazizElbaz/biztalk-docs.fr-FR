---
title: Importation de liaison Files1 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding files, importing
- CLASSPATH environment variable
- importing binding files
- cleaning target computer
ms.assetid: b2a9b19b-2d3d-45ea-bd92-a2501791b86a
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12fca64580b692f01834b48085aa2d88085fb743
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importing-binding-files"></a><span data-ttu-id="c464a-102">importation des fichiers de liaison</span><span class="sxs-lookup"><span data-stu-id="c464a-102">Importing Binding Files</span></span>
<span data-ttu-id="c464a-103">Avant d'importer un fichier de liaison à l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vérifiez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="c464a-103">Before you use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to import a binding file, verify the following:</span></span>  
  
-   <span data-ttu-id="c464a-104">CLASSPATH pointe vers un emplacement particulier pour les fichiers spécifiques à PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="c464a-104">The CLASSPATH is pointing to a specific location for the PeopleSoft-specific files.</span></span> <span data-ttu-id="c464a-105">Vérifiez que l’emplacement de ces fichiers est le même sur le nouvel ordinateur, ou modifier le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="c464a-105">Verify that the location of these files is the same on the new computer—or edit the binding file.</span></span>  
  
-   <span data-ttu-id="c464a-106">Les dossiers pour les réponses doivent exister et être identiques sur le nouvel ordinateur, ou modifier le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="c464a-106">The folders for the responses must exist and be identical on the new computer—or edit the binding file.</span></span>  
  
-   <span data-ttu-id="c464a-107">S'ils sont présents dans la configuration, les mots de passe du système PeopleSoft Enterprise sont enregistrés dans le fichier de liaison sous la forme *****.</span><span class="sxs-lookup"><span data-stu-id="c464a-107">PeopleSoft Enterprise system passwords, if present in the configuration, are saved as ***** in the binding file.</span></span> <span data-ttu-id="c464a-108">Pour plus d’informations, consultez [limitations concernant le déploiement](../core/deployment-limitations3.md).</span><span class="sxs-lookup"><span data-stu-id="c464a-108">For more information, see [Deployment Limitations](../core/deployment-limitations3.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c464a-109">Le déploiement remplace la configuration de l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="c464a-109">Deployment overwrites receive location configuration.</span></span> <span data-ttu-id="c464a-110">Lorsque vous déployez un fichier de liaison et l’assembly sur un ordinateur cible, les ports d’envoi et emplacements de réception sont remplacés par ceux dans le fichier de liaison XML lorsqu’ils sont importés.</span><span class="sxs-lookup"><span data-stu-id="c464a-110">When you deploy a binding file and assembly on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
 <span data-ttu-id="c464a-111">Pour obtenir des instructions détaillées sur l'importation des fichiers de liaison, consultez la rubrique « Importation des liaisons dans un groupe BizTalk » dans la documentation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c464a-111">For step-by-step directions about importing binding files, see the topic "How to Import Bindings into a BizTalk Group" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.</span></span>  
  
## <a name="cleaning-the-target-computer"></a><span data-ttu-id="c464a-112">Nettoyage de l'ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="c464a-112">Cleaning the Target Computer</span></span>  
 <span data-ttu-id="c464a-113">Pour nettoyer l'ordinateur cible afin de déployer la nouvelle application, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="c464a-113">Follow these steps to clean the target computer for deploying the new application.</span></span>  
  
#### <a name="to-clean-the-target-computer"></a><span data-ttu-id="c464a-114">Pour nettoyer l'ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="c464a-114">To clean the target computer</span></span>  
  
-   <span data-ttu-id="c464a-115">Supprimez les ports d’envoi et emplacements de réception liés à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="c464a-115">Remove send ports and receive locations bound to the orchestration.</span></span>  
  
     <span data-ttu-id="c464a-116">Si Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] n'est pas installé sur l'ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts suivants :</span><span class="sxs-lookup"><span data-stu-id="c464a-116">If you do not have Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] installed on the target computer, you may remove the ports by running these scripts:</span></span>  
  
     <span data-ttu-id="c464a-117">**\<Microsoft BizTalk Server > \SDK\Samples\Admin\WMI\Remove envoyer Port\VBScript\RemoveSendPort.vbs**</span><span class="sxs-lookup"><span data-stu-id="c464a-117">**\<Microsoft BizTalk Server>\SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs**</span></span>  
  
     <span data-ttu-id="c464a-118">**\<Microsoft BizTalk Server > \SDK\Samples\Admin\WMI\Remove Port\VBScript\RemoveReceivePort.vbs de réception**</span><span class="sxs-lookup"><span data-stu-id="c464a-118">**\<Microsoft BizTalk Server>\SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs**</span></span>  
  
     <span data-ttu-id="c464a-119">Par exemple, à une invite de commandes, exécutez :</span><span class="sxs-lookup"><span data-stu-id="c464a-119">For example, at a command prompt, run:</span></span>  
  
     <span data-ttu-id="c464a-120">**cscript RemoveSendPort.vbs \<nom du port d’envoi >**</span><span class="sxs-lookup"><span data-stu-id="c464a-120">**cscript RemoveSendPort.vbs \<Send port name>**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c464a-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c464a-121">See Also</span></span>  
 [<span data-ttu-id="c464a-122">Déploiement de Ports et assemblys</span><span class="sxs-lookup"><span data-stu-id="c464a-122">Deploying Ports and Assemblies</span></span>](../core/deploying-ports-and-assemblies5.md)