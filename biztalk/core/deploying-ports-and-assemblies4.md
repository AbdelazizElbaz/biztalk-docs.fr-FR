---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-jd-edwards-oneworld/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: ac85aec2f1153d5117c95627e573ec563d58dbc2
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="deploying-ports-and-assemblies"></a><span data-ttu-id="1149b-101">Déploiement des ports et assemblys</span><span class="sxs-lookup"><span data-stu-id="1149b-101">Deploying Ports and Assemblies</span></span>
<span data-ttu-id="1149b-102">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de dupliquer des ports et des assemblys sur un ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="1149b-102">Using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> <span data-ttu-id="1149b-103">BizTalk Server exporte la configuration des ports d'envoi/emplacements de réception dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="1149b-103">BizTalk Server exports the send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="1149b-104">Vous pouvez utiliser BizTalk Server pour effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="1149b-104">You can use BizTalk Server to do the following tasks:</span></span>  
  
-   <span data-ttu-id="1149b-105">déploiement ou suppression des assemblys BizTalk Server dans une base de données de configuration BizTalk ;</span><span class="sxs-lookup"><span data-stu-id="1149b-105">Deploy or remove BizTalk Server assemblies in a BizTalk Configuration database</span></span>  
  
-   <span data-ttu-id="1149b-106">Installer ou désinstaller des assemblys dans le global assembly cache (GAC)</span><span class="sxs-lookup"><span data-stu-id="1149b-106">Install or uninstall the assemblies in the global assembly cache (GAC)</span></span>  
  
-   <span data-ttu-id="1149b-107">importation/exportation des informations de liaison des assemblys BizTalk Server vers/à partir de fichiers de liaison.</span><span class="sxs-lookup"><span data-stu-id="1149b-107">Import or export BizTalk Server assembly binding information to and from binding files</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1149b-108">L'adaptateur Microsoft BizTalk pour JD Edwards OneWorld requiert l'installation de Visual Studio sur un ordinateur (de développement) source.</span><span class="sxs-lookup"><span data-stu-id="1149b-108">The Microsoft BizTalk Adapter for JD Edwards OneWorld only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="1149b-109">Visual Studio n'est pas requis sur l'ordinateur de production.</span><span class="sxs-lookup"><span data-stu-id="1149b-109">Visual Studio is not required on the production computer.</span></span>  
  
