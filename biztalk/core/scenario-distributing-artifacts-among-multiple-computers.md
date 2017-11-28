---
title: "Scénario : Distribution d’artefacts sur plusieurs ordinateurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying [artifacts], multiple computers
- examples, distributing
- examples, artifacts
- artifacts, distributing
- artifacts, examples
- deploying [artifacts], examples
- examples, deploying
ms.assetid: 7000cded-1fda-4276-b7f3-3f427f686f64
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: abedc60ad13c7e8b2be3ce4caa7b8d34262b4e5c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-distributing-artifacts-among-multiple-computers"></a><span data-ttu-id="936aa-102">Scénario : Distribution d’artefacts sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="936aa-102">Scenario: Distributing Artifacts Among Multiple Computers</span></span>
<span data-ttu-id="936aa-103">Cette rubrique décrit le scénario de déploiement d'une application lorsque les artefacts sont installés de manière sélective sur différents ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="936aa-103">This topic describes the application deployment scenario when the artifacts in an application are selectively installed on different computers.</span></span> <span data-ttu-id="936aa-104">Vous pouvez adopter cette méthode si vous souhaitez que certains assemblys ou d'autres types d'artefacts d'une application soient installés uniquement sur certains ordinateurs d'un groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="936aa-104">You might want to do this if you want certain assemblies or other types of artifacts in an application to be installed only on specific computers in a BizTalk group.</span></span> <span data-ttu-id="936aa-105">Pour ce faire, vous pouvez exporter les artefacts inclus dans l'application dans plusieurs fichiers .msi, en regroupant dans un même fichier les artefacts que vous voulez installez sur un même ordinateur physique.</span><span class="sxs-lookup"><span data-stu-id="936aa-105">To do this, you can export the artifacts included in an application into multiple .msi files, according to which artifacts you want to install together on a physical computer.</span></span>  
  
 <span data-ttu-id="936aa-106">Le diagramme suivant montre un fichier .msi est importé dans la base de données de gestion BizTalk pour BizTalk groupe 1.</span><span class="sxs-lookup"><span data-stu-id="936aa-106">The following diagram shows an .msi file that is imported into the BizTalk Management database for BizTalk Group 1.</span></span> <span data-ttu-id="936aa-107">Cela crée l’application de traitement des commandes et tous ses artefacts dans ce groupe.</span><span class="sxs-lookup"><span data-stu-id="936aa-107">This creates the Order Processing application and all of its artifacts in that group.</span></span> <span data-ttu-id="936aa-108">Les artefacts de l'application sont alors exportés dans deux fichiers .msi différents.</span><span class="sxs-lookup"><span data-stu-id="936aa-108">The application artifacts are then exported into two different .msi files.</span></span> <span data-ttu-id="936aa-109">Le premier fichier .msi contient Assembly1, Certificat1 et Script1.</span><span class="sxs-lookup"><span data-stu-id="936aa-109">One .msi file contains Assembly1, Certificate1, and Script1.</span></span> <span data-ttu-id="936aa-110">Le second contient Assembly2, Script2 et VirtualDirectory1.</span><span class="sxs-lookup"><span data-stu-id="936aa-110">The other .msi file contains Assembly2, Script2, and VirtualDirectory1.</span></span>  
  
 <span data-ttu-id="936aa-111">Les deux fichiers .msi sont importés dans BizTalk groupe 2.</span><span class="sxs-lookup"><span data-stu-id="936aa-111">Both .msi files are imported into BizTalk Group 2.</span></span> <span data-ttu-id="936aa-112">Étant donné que les deux appartiennent à l’application de traitement des commandes, tous les artefacts dans les deux fichiers .msi sont importés dans la même application nommée traitement des commandes dans le nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="936aa-112">Because they both belong to the Order Processing application, all of the artifacts in both .msi files are imported into the same application named Order Processing in the new group.</span></span>  
  
 <span data-ttu-id="936aa-113">En outre, les artefacts de l'application sont installés à partir des fichiers .msi sur les ordinateurs du groupe qui les exécuteront.</span><span class="sxs-lookup"><span data-stu-id="936aa-113">In addition, the application artifacts are installed from the .msi files onto the computers in the group that will run them.</span></span> <span data-ttu-id="936aa-114">Notez que le fichier .msi contenant le répertoire virtuel est installé sur BizTalk Serveur B et BizTalk Serveur C, qui exécutent tous deux les services IIS.</span><span class="sxs-lookup"><span data-stu-id="936aa-114">Note that the .msi file containing the virtual directory is installed on BizTalk Server B and BizTalk Server C, which are both running IIS.</span></span>  
  
 <span data-ttu-id="936aa-115">![Artefacts installés sur différents ordinateurs](../core/media/distributionofartifacts.gif "DistributionOfArtifacts")</span><span class="sxs-lookup"><span data-stu-id="936aa-115">![Artifacts installed on different computers](../core/media/distributionofartifacts.gif "DistributionOfArtifacts")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="936aa-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="936aa-116">See Also</span></span>  
 <span data-ttu-id="936aa-117">[Déploiement d’applications et scénarios de gestion](../core/application-deployment-and-management-scenarios.md) </span><span class="sxs-lookup"><span data-stu-id="936aa-117">[Application Deployment and Management Scenarios](../core/application-deployment-and-management-scenarios.md) </span></span>  
 <span data-ttu-id="936aa-118">[Comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md) </span><span class="sxs-lookup"><span data-stu-id="936aa-118">[How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md) </span></span>  
 <span data-ttu-id="936aa-119">[Comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md) </span><span class="sxs-lookup"><span data-stu-id="936aa-119">[How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md) </span></span>  
 [<span data-ttu-id="936aa-120">Comment installer une Application BizTalk</span><span class="sxs-lookup"><span data-stu-id="936aa-120">How to Install a BizTalk Application</span></span>](../core/how-to-install-a-biztalk-application.md)