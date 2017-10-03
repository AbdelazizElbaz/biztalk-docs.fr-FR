---
title: Comment nettoyer les ordinateur1 cible | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, removing
- send ports, removing
- cleaning target computer
ms.assetid: 78986a33-3c77-48dc-88c4-b78f52911c22
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7adf1761b6eb31ce158232c22af457b9c716a812
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-clean-the-target-computer"></a><span data-ttu-id="c9f68-102">Comment nettoyer l’ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="c9f68-102">How to Clean the Target Computer</span></span>
<span data-ttu-id="c9f68-103">Déploiement remplace la configuration d’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="c9f68-103">Deployment overwrites the receive location configuration.</span></span> <span data-ttu-id="c9f68-104">Lorsque vous déployez un fichier de liaison (et un assembly) sur un ordinateur cible, les ports d’envoi et emplacements de réception sont remplacés par ceux dans le fichier de liaison XML lorsqu’ils sont importés.</span><span class="sxs-lookup"><span data-stu-id="c9f68-104">When you deploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
### <a name="to-clean-the-target-computer"></a><span data-ttu-id="c9f68-105">Pour nettoyer l'ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="c9f68-105">To clean the target computer</span></span>  
  
-   <span data-ttu-id="c9f68-106">Supprimez les ports d’envoi et emplacements de réception liés à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="c9f68-106">Remove send ports and receive locations bound to the orchestration.</span></span>  
  
     <span data-ttu-id="c9f68-107">Si vous n’avez pas de Microsoft Visual Studio est installé sur l’ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts :</span><span class="sxs-lookup"><span data-stu-id="c9f68-107">If you do not have Microsoft Visual Studio installed on the target computer, you can remove the ports by running these scripts:</span></span>  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="c9f68-108">SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="c9f68-108">SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span></span>  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="c9f68-109">SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span><span class="sxs-lookup"><span data-stu-id="c9f68-109">SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span></span>  
  
         <span data-ttu-id="c9f68-110">Par exemple, à une invite de commandes, exécutez :</span><span class="sxs-lookup"><span data-stu-id="c9f68-110">For example, at a command prompt, run:</span></span>  
  
         <span data-ttu-id="c9f68-111">**cscript RemoveSendPort.vbs \<nom du port d’envoi >**</span><span class="sxs-lookup"><span data-stu-id="c9f68-111">**cscript RemoveSendPort.vbs \<Send port name>**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9f68-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9f68-112">See Also</span></span>  
 [<span data-ttu-id="c9f68-113">Déploiement de Ports et assemblys</span><span class="sxs-lookup"><span data-stu-id="c9f68-113">Deploying Ports and Assemblies</span></span>](../core/deploying-ports-and-assemblies1.md)