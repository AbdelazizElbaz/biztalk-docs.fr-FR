---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 9e3c0ee8d4aa3e6e3bfaf48db04019cf8680d3ab
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="deploying-ports-and-assemblies"></a><span data-ttu-id="2c9ad-101">Déploiement des ports et assemblys</span><span class="sxs-lookup"><span data-stu-id="2c9ad-101">Deploying Ports and Assemblies</span></span>
<span data-ttu-id="2c9ad-102">Avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez dupliquer des ports et des assemblys sur un ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="2c9ad-102">With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2c9ad-103">Exporte la configuration des emplacements de réception/ports envoi dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="2c9ad-103"> exports the send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="2c9ad-104">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet d'exécuter les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="2c9ad-104">You can use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to do the following tasks:</span></span>  
  
-   <span data-ttu-id="2c9ad-105">Déployer ou supprimer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblys dans une base de données de Configuration de BizTalk</span><span class="sxs-lookup"><span data-stu-id="2c9ad-105">Deploy or remove [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies in a BizTalk Configuration database</span></span>  
  
-   <span data-ttu-id="2c9ad-106">Installer ou désinstaller des assemblys dans le global assembly cache (GAC)</span><span class="sxs-lookup"><span data-stu-id="2c9ad-106">Install or uninstall the assemblies in the global assembly cache (GAC)</span></span>  
  
-   <span data-ttu-id="2c9ad-107">Importer ou exporter des [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] informations de liaison d’assembly vers et à partir de fichiers de liaison</span><span class="sxs-lookup"><span data-stu-id="2c9ad-107">Import or export [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assembly binding information to and from binding files</span></span>  
  
 <span data-ttu-id="2c9ad-108">Pour plus d’informations sur l’utilisation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour déployer des ports et des assemblys, consultez [comment exporter les liaisons d’une Application BizTalk](../core/how-to-export-bindings-for-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="2c9ad-108">For information about how to use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c9ad-109">L'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne requiert l'installation de Visual Studio sur un ordinateur (de développement) source.</span><span class="sxs-lookup"><span data-stu-id="2c9ad-109">The Microsoft BizTalk Adapter for JD Edwards EnterpriseOne only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="2c9ad-110">Visual Studio n'est pas requis sur l'ordinateur de production.</span><span class="sxs-lookup"><span data-stu-id="2c9ad-110">Visual Studio is not required on the production computer.</span></span>  
  
