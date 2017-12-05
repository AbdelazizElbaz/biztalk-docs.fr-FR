---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-tibco-rendezvous/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 8e187233b8755eb84d6169192542d48ce2e86ec3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-clean-the-target-computer"></a><span data-ttu-id="25ed4-101">Comment nettoyer l’ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="25ed4-101">How to Clean the Target Computer</span></span>
<span data-ttu-id="25ed4-102">Déploiement remplace la configuration d’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="25ed4-102">Deployment overwrites the receive location configuration.</span></span> <span data-ttu-id="25ed4-103">Lorsque vous déployez un fichier de liaison (et un assembly) sur un ordinateur cible, les ports d’envoi et emplacements de réception sont remplacés par ceux dans le fichier de liaison XML lorsqu’ils sont importés.</span><span class="sxs-lookup"><span data-stu-id="25ed4-103">When you deploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
### <a name="to-clean-the-target-computer"></a><span data-ttu-id="25ed4-104">Pour nettoyer l'ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="25ed4-104">To clean the target computer</span></span>  
  
-   <span data-ttu-id="25ed4-105">Supprimez les ports d’envoi et emplacements de réception liés à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="25ed4-105">Remove send ports and receive locations bound to the orchestration.</span></span>  
  
     <span data-ttu-id="25ed4-106">Si vous n’avez pas de Microsoft Visual Studio est installé sur l’ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts :</span><span class="sxs-lookup"><span data-stu-id="25ed4-106">If you do not have Microsoft Visual Studio installed on the target computer, you can remove the ports by running these scripts:</span></span>  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="25ed4-107">SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="25ed4-107">SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span></span>  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="25ed4-108">SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span><span class="sxs-lookup"><span data-stu-id="25ed4-108">SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span></span>  
  
         <span data-ttu-id="25ed4-109">Par exemple, à une invite de commandes, exécutez :</span><span class="sxs-lookup"><span data-stu-id="25ed4-109">For example, at a command prompt, run:</span></span>  
  
         <span data-ttu-id="25ed4-110">**cscript RemoveSendPort.vbs \<nom du port d’envoi\>**</span><span class="sxs-lookup"><span data-stu-id="25ed4-110">**cscript RemoveSendPort.vbs \<Send port name\>**</span></span>  
  
