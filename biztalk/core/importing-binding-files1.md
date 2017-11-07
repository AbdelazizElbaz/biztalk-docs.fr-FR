---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-peoplesoft-enterprise/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 8a2b78ee2e8ec75c6ce83a8b78d1e779f012f324
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="import-binding-files"></a><span data-ttu-id="b4a97-101">Importer des fichiers de liaison</span><span class="sxs-lookup"><span data-stu-id="b4a97-101">Import Binding Files</span></span>

## <a name="overview"></a><span data-ttu-id="b4a97-102">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="b4a97-102">Overview</span></span>
<span data-ttu-id="b4a97-103">Avant d'importer un fichier de liaison à l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vérifiez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="b4a97-103">Before you use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to import a binding file, verify the following:</span></span>  
  
-   <span data-ttu-id="b4a97-104">CLASSPATH pointe vers un emplacement particulier pour les fichiers spécifiques à PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="b4a97-104">The CLASSPATH is pointing to a specific location for the PeopleSoft-specific files.</span></span> <span data-ttu-id="b4a97-105">Vérifiez que l’emplacement de ces fichiers est le même sur le nouvel ordinateur, ou modifier le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="b4a97-105">Verify that the location of these files is the same on the new computer—or edit the binding file.</span></span>  
  
-   <span data-ttu-id="b4a97-106">Les dossiers pour les réponses doivent exister et être identiques sur le nouvel ordinateur, ou modifier le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="b4a97-106">The folders for the responses must exist and be identical on the new computer—or edit the binding file.</span></span>  
  
-   <span data-ttu-id="b4a97-107">S'ils sont présents dans la configuration, les mots de passe du système PeopleSoft Enterprise sont enregistrés dans le fichier de liaison sous la forme *****.</span><span class="sxs-lookup"><span data-stu-id="b4a97-107">PeopleSoft Enterprise system passwords, if present in the configuration, are saved as ***** in the binding file.</span></span> 
  
> [!NOTE]
>  <span data-ttu-id="b4a97-108">Le déploiement remplace la configuration de l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="b4a97-108">Deployment overwrites receive location configuration.</span></span> <span data-ttu-id="b4a97-109">Lorsque vous déployez un fichier de liaison et l’assembly sur un ordinateur cible, les ports d’envoi et emplacements de réception sont remplacés par ceux dans le fichier de liaison XML lorsqu’ils sont importés.</span><span class="sxs-lookup"><span data-stu-id="b4a97-109">When you deploy a binding file and assembly on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
 <span data-ttu-id="b4a97-110">Pour obtenir des instructions détaillées sur l'importation des fichiers de liaison, consultez la rubrique « Importation des liaisons dans un groupe BizTalk » dans la documentation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b4a97-110">For step-by-step directions about importing binding files, see the topic "How to Import Bindings into a BizTalk Group" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.</span></span>  
  
## <a name="clean-the-target-computer"></a><span data-ttu-id="b4a97-111">Nettoyer l’ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="b4a97-111">Clean the Target Computer</span></span>  
<span data-ttu-id="b4a97-112">Pour nettoyer l’ordinateur cible pour le déploiement de la nouvelle application, supprimez les ports d’envoi et emplacements de réception liés à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="b4a97-112">To clean the target computer for deploying the new application, remove send ports and receive locations bound to the orchestration.</span></span>  
  
<span data-ttu-id="b4a97-113">Si Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] n'est pas installé sur l'ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts suivants :</span><span class="sxs-lookup"><span data-stu-id="b4a97-113">If you do not have Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] installed on the target computer, you may remove the ports by running these scripts:</span></span>  
  
<span data-ttu-id="b4a97-114">**\<Microsoft BizTalk Server > \SDK\Samples\Admin\WMI\Remove envoyer Port\VBScript\RemoveSendPort.vbs**</span><span class="sxs-lookup"><span data-stu-id="b4a97-114">**\<Microsoft BizTalk Server>\SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs**</span></span>  
  
<span data-ttu-id="b4a97-115">**\<Microsoft BizTalk Server > \SDK\Samples\Admin\WMI\Remove Port\VBScript\RemoveReceivePort.vbs de réception**</span><span class="sxs-lookup"><span data-stu-id="b4a97-115">**\<Microsoft BizTalk Server>\SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs**</span></span>  
  
<span data-ttu-id="b4a97-116">Par exemple, à une invite de commandes, exécutez :</span><span class="sxs-lookup"><span data-stu-id="b4a97-116">For example, at a command prompt, run:</span></span>  
  
<span data-ttu-id="b4a97-117">**cscript RemoveSendPort.vbs \<nom du port d’envoi >**</span><span class="sxs-lookup"><span data-stu-id="b4a97-117">**cscript RemoveSendPort.vbs \<Send port name>**</span></span>  
  
