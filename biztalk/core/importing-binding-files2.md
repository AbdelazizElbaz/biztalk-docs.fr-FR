---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 7dbc9ef8624404b9fa7bdcb7b6a21b2d2a4c69f2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="importing-binding-files"></a><span data-ttu-id="213f0-101">importation des fichiers de liaison</span><span class="sxs-lookup"><span data-stu-id="213f0-101">Importing Binding Files</span></span>
<span data-ttu-id="213f0-102">Cette rubrique fournit des informations sur le processus d'importation lors du déploiement de l'adaptateur BizTalk pour JD Edwards EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="213f0-102">This topic provides some information concerning the import process when you deploy BizTalk Adapter for JD Edwards EnterpriseOne.</span></span> <span data-ttu-id="213f0-103">Lors du redéploiement d'un fichier de liaison (et de l'assembly) sur un ordinateur cible, les ports d'envoi et les emplacements de réception sont remplacés par ceux qui se trouvent dans le fichier de liaison XML lors de leur réimportation.</span><span class="sxs-lookup"><span data-stu-id="213f0-103">When you redeploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are reimported.</span></span>  
  
### <a name="to-clean-the-target-computer"></a><span data-ttu-id="213f0-104">Pour nettoyer l'ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="213f0-104">To clean the target computer</span></span>  
  
-   <span data-ttu-id="213f0-105">Supprimez les ports d’envoi et emplacements de réception liés à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="213f0-105">Remove Send ports and Receive locations bound to the orchestration.</span></span>  
  
     <span data-ttu-id="213f0-106">Si Visual Studio n'est pas installé sur l'ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts suivants :</span><span class="sxs-lookup"><span data-stu-id="213f0-106">If you do not have Visual Studio installed on the target computer, you can remove the ports by running the scripts:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="213f0-107">SDK\Samples\Admin\WMI\\</span><span class="sxs-lookup"><span data-stu-id="213f0-107">SDK\Samples\Admin\WMI\\</span></span>  
  
     <span data-ttu-id="213f0-108">Remove Send Port\VBScript\RemoveSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="213f0-108">Remove Send Port\VBScript\RemoveSendPort.vbs</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="213f0-109">SDK\Samples\Admin\WMI\\</span><span class="sxs-lookup"><span data-stu-id="213f0-109">SDK\Samples\Admin\WMI\\</span></span>  
  
     <span data-ttu-id="213f0-110">Remove Receive Port\VBScript\RemoveReceivePort.vbs</span><span class="sxs-lookup"><span data-stu-id="213f0-110">Remove Receive Port\VBScript\RemoveReceivePort.vbs</span></span>  
  
     <span data-ttu-id="213f0-111">Par exemple, à l'invite de commandes, exécutez :</span><span class="sxs-lookup"><span data-stu-id="213f0-111">For example, from a command prompt run:</span></span>  
  
     <span data-ttu-id="213f0-112">**cscript RemoveSendPort.vbs \<nom du port d’envoi\>**</span><span class="sxs-lookup"><span data-stu-id="213f0-112">**cscript RemoveSendPort.vbs \<Send port name\>**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="213f0-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="213f0-113">See Also</span></span>  
 [<span data-ttu-id="213f0-114">Importer le JD Edwards EnterpriseOne application</span><span class="sxs-lookup"><span data-stu-id="213f0-114">Import the JD Edwards EnterpriseOne app</span></span>](../core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone.md)