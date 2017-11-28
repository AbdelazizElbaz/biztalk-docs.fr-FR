---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-tibco-enterprise-message-service/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 93cb3a1420b60183ff42108c32224cf4707b9cd7
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-clean-the-target-computer"></a><span data-ttu-id="0ac3b-101">Comment nettoyer l’ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="0ac3b-101">How to Clean the Target Computer</span></span>
<span data-ttu-id="0ac3b-102">Déploiement remplace la configuration d’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="0ac3b-102">Deployment overwrites the receive location configuration.</span></span> <span data-ttu-id="0ac3b-103">Lorsque vous déployez un fichier de liaison (et un assembly) sur un ordinateur cible, les ports d’envoi et emplacements de réception sont remplacés par ceux dans le fichier de liaison XML lorsqu’ils sont importés.</span><span class="sxs-lookup"><span data-stu-id="0ac3b-103">When you deploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
### <a name="to-clean-the-target-computer"></a><span data-ttu-id="0ac3b-104">Pour nettoyer l'ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="0ac3b-104">To clean the target computer</span></span>  
  
-   <span data-ttu-id="0ac3b-105">Supprimez tous les ports d'envoi et les emplacements de réception liés à l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="0ac3b-105">Remove any send ports and receive locations bound to the orchestration.</span></span>  
  
     <span data-ttu-id="0ac3b-106">Si vous n’avez pas de Microsoft Visual Studio est installé sur l’ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts :</span><span class="sxs-lookup"><span data-stu-id="0ac3b-106">If you do not have Microsoft Visual Studio installed on the target computer, you can remove the ports by running these scripts:</span></span>  
  
     <span data-ttu-id="0ac3b-107">\<Microsoft BizTalk Server > \SDK\Samples\Admin\WMI\Remove envoyer Port\VBScript\RemoveSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="0ac3b-107">\<Microsoft BizTalk Server>\SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span></span>  
  
     <span data-ttu-id="0ac3b-108">\<Microsoft BizTalk Server > \SDK\Samples\Admin\WMI\Remove Port\VBScript\RemoveReceivePort.vbs de réception</span><span class="sxs-lookup"><span data-stu-id="0ac3b-108">\<Microsoft BizTalk Server>\SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span></span>  
  
     <span data-ttu-id="0ac3b-109">Par exemple, à une invite de commandes, exécutez :</span><span class="sxs-lookup"><span data-stu-id="0ac3b-109">For example, at a command prompt, run:</span></span>  
  
     <span data-ttu-id="0ac3b-110">**cscript RemoveSendPort.vbs \<nom du port d’envoi >**</span><span class="sxs-lookup"><span data-stu-id="0ac3b-110">**cscript RemoveSendPort.vbs \<Send port name>**</span></span>  
  
