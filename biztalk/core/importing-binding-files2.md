---
title: Importation de liaison Files2 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding files, importing
- assemblies, removing from database
- importing binding files
- target computers, cleaning
- BizTalk assemblies, removing from database
ms.assetid: 9e552a4b-06ec-4887-b17b-a625c137699f
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3783b21385c210c454bcd3d4c951f2200a6ec866
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importing-binding-files"></a><span data-ttu-id="bf2bf-102">importation des fichiers de liaison</span><span class="sxs-lookup"><span data-stu-id="bf2bf-102">Importing Binding Files</span></span>
<span data-ttu-id="bf2bf-103">Cette rubrique fournit des informations sur le processus d'importation lors du déploiement de l'adaptateur BizTalk pour JD Edwards EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="bf2bf-103">This topic provides some information concerning the import process when you deploy BizTalk Adapter for JD Edwards EnterpriseOne.</span></span> <span data-ttu-id="bf2bf-104">Lors du redéploiement d'un fichier de liaison (et de l'assembly) sur un ordinateur cible, les ports d'envoi et les emplacements de réception sont remplacés par ceux qui se trouvent dans le fichier de liaison XML lors de leur réimportation.</span><span class="sxs-lookup"><span data-stu-id="bf2bf-104">When you redeploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are reimported.</span></span>  
  
### <a name="to-clean-the-target-computer"></a><span data-ttu-id="bf2bf-105">Pour nettoyer l'ordinateur cible</span><span class="sxs-lookup"><span data-stu-id="bf2bf-105">To clean the target computer</span></span>  
  
-   <span data-ttu-id="bf2bf-106">Supprimez les ports d’envoi et emplacements de réception liés à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="bf2bf-106">Remove Send ports and Receive locations bound to the orchestration.</span></span>  
  
     <span data-ttu-id="bf2bf-107">Si Visual Studio n'est pas installé sur l'ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts suivants :</span><span class="sxs-lookup"><span data-stu-id="bf2bf-107">If you do not have Visual Studio installed on the target computer, you can remove the ports by running the scripts:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="bf2bf-108">SDK\Samples\Admin\WMI\\</span><span class="sxs-lookup"><span data-stu-id="bf2bf-108">SDK\Samples\Admin\WMI\\</span></span>  
  
     <span data-ttu-id="bf2bf-109">Remove Send Port\VBScript\RemoveSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="bf2bf-109">Remove Send Port\VBScript\RemoveSendPort.vbs</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="bf2bf-110">SDK\Samples\Admin\WMI\\</span><span class="sxs-lookup"><span data-stu-id="bf2bf-110">SDK\Samples\Admin\WMI\\</span></span>  
  
     <span data-ttu-id="bf2bf-111">Remove Receive Port\VBScript\RemoveReceivePort.vbs</span><span class="sxs-lookup"><span data-stu-id="bf2bf-111">Remove Receive Port\VBScript\RemoveReceivePort.vbs</span></span>  
  
     <span data-ttu-id="bf2bf-112">Par exemple, à l'invite de commandes, exécutez :</span><span class="sxs-lookup"><span data-stu-id="bf2bf-112">For example, from a command prompt run:</span></span>  
  
     <span data-ttu-id="bf2bf-113">**cscript RemoveSendPort.vbs \<nom du port d’envoi >**</span><span class="sxs-lookup"><span data-stu-id="bf2bf-113">**cscript RemoveSendPort.vbs \<Send port name>**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf2bf-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf2bf-114">See Also</span></span>  
 [<span data-ttu-id="bf2bf-115">Déploiement de Ports et assemblys</span><span class="sxs-lookup"><span data-stu-id="bf2bf-115">Deploying Ports and Assemblies</span></span>](../core/deploying-ports-and-assemblies3.md)