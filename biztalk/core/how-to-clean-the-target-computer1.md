---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-tibco-rendezvous/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 4ceaef21127ec010450082228b765dcbb8e76005
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-clean-the-target-computer"></a><span data-ttu-id="c8f1d-101">Comment nettoyer l’ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="c8f1d-101">How to Clean the Target Computer</span></span>
<span data-ttu-id="c8f1d-102">Déploiement remplace la configuration d’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="c8f1d-102">Deployment overwrites the receive location configuration.</span></span> <span data-ttu-id="c8f1d-103">Lorsque vous déployez un fichier de liaison (et un assembly) sur un ordinateur cible, les ports d’envoi et emplacements de réception sont remplacés par ceux dans le fichier de liaison XML lorsqu’ils sont importés.</span><span class="sxs-lookup"><span data-stu-id="c8f1d-103">When you deploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
### <a name="to-clean-the-target-computer"></a><span data-ttu-id="c8f1d-104">Pour nettoyer l'ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="c8f1d-104">To clean the target computer</span></span>  
  
-   <span data-ttu-id="c8f1d-105">Supprimez les ports d’envoi et emplacements de réception liés à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="c8f1d-105">Remove send ports and receive locations bound to the orchestration.</span></span>  
  
     <span data-ttu-id="c8f1d-106">Si vous n’avez pas de Microsoft Visual Studio est installé sur l’ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts :</span><span class="sxs-lookup"><span data-stu-id="c8f1d-106">If you do not have Microsoft Visual Studio installed on the target computer, you can remove the ports by running these scripts:</span></span>  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="c8f1d-107">SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="c8f1d-107">SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span></span>  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="c8f1d-108">SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span><span class="sxs-lookup"><span data-stu-id="c8f1d-108">SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span></span>  
  
         <span data-ttu-id="c8f1d-109">Par exemple, à une invite de commandes, exécutez :</span><span class="sxs-lookup"><span data-stu-id="c8f1d-109">For example, at a command prompt, run:</span></span>  
  
         <span data-ttu-id="c8f1d-110">**cscript RemoveSendPort.vbs \<nom du port d’envoi >**</span><span class="sxs-lookup"><span data-stu-id="c8f1d-110">**cscript RemoveSendPort.vbs \<Send port name>**</span></span>  
  
