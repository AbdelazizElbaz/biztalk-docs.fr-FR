---
title: Remove Send Port (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, examples
- examples, send ports
- send ports, deleting
- deleting, send ports
ms.assetid: e6643525-fa9f-4d39-880f-314749a68471
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2bb37ae93b45ac1721da582cc0092bda5d67999
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="remove-send-port-biztalk-server-sample"></a><span data-ttu-id="db534-102">Remove Send Port (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="db534-102">Remove Send Port (BizTalk Server Sample)</span></span>
<span data-ttu-id="db534-103">L'exemple de suppression d'un port d'envoi (Remove Send Port) illustre la désinscription et la suppression d'un ou plusieurs ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="db534-103">The Remove Send Port sample demonstrates how to unenlist and remove one or more send ports.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="db534-104">Les scripts de déploiement devenus inutiles après le déploiement doivent être supprimés.</span><span class="sxs-lookup"><span data-stu-id="db534-104">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="db534-105">Les scripts d'administration et autres scripts conservés doivent être sécurisés à l'aide de listes de contrôle d'accès et étroitement surveillés.</span><span class="sxs-lookup"><span data-stu-id="db534-105">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="db534-106">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="db534-106">What This Sample Does</span></span>  
 <span data-ttu-id="db534-107">Le script Visual Basic Scripting Edition (VBScript) dans le fichier de script de cet exemple décrit l'exécution des opérations suivantes à l'aide du fournisseur WMI BizTalk Server :</span><span class="sxs-lookup"><span data-stu-id="db534-107">The Visual Basic Scripting Edition (VBScript) script in the script file that constitutes this sample shows how to perform the following operations using the BizTalk Server WMI provider:</span></span>  
  
-   <span data-ttu-id="db534-108">pour un nom de port d'envoi, création d'une requête pour obtenir la liste des ports d'envoi correspondants.</span><span class="sxs-lookup"><span data-stu-id="db534-108">Given a send port name, query for a list of matching send ports.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="db534-109">En général, un seul port d'envoi correspond à un nom donné.</span><span class="sxs-lookup"><span data-stu-id="db534-109">Generally, there will only be one send port that matches a given name.</span></span>  
  
-   <span data-ttu-id="db534-110">désinscription de ces ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="db534-110">Unenlist those send ports.</span></span>  
  
-   <span data-ttu-id="db534-111">suppression de ces ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="db534-111">Delete those send ports.</span></span>  
  
-   <span data-ttu-id="db534-112">gestion de toutes erreurs de telle sorte que les informations significatives soient renvoyées à l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="db534-112">Handle any errors such that meaningful information is returned to the user.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="db534-113">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="db534-113">Where to Find This Sample</span></span>  
 <span data-ttu-id="db534-114">L'exemple se trouve dans l'emplacement SDK suivant :</span><span class="sxs-lookup"><span data-stu-id="db534-114">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="db534-115">\<*Exemples de chemin d’accès*> \Admin\WMI\Remove envoyer LPT1\\</span><span class="sxs-lookup"><span data-stu-id="db534-115">\<*Samples Path*>\Admin\WMI\Remove Send Port\\</span></span>  
  
 <span data-ttu-id="db534-116">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="db534-116">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="db534-117">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="db534-117">File(s)</span></span>|<span data-ttu-id="db534-118"> Description</span><span class="sxs-lookup"><span data-stu-id="db534-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db534-119">Dans le dossier \VBScript :</span><span class="sxs-lookup"><span data-stu-id="db534-119">In the \VBScript folder:</span></span><br /><br /> <span data-ttu-id="db534-120">RemoveSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="db534-120">RemoveSendPort.vbs</span></span>|<span data-ttu-id="db534-121">Fichier VBScript qui récupère un paramètre spécifiant un ou plusieurs ports d'envoi à désinscrire et supprimer.</span><span class="sxs-lookup"><span data-stu-id="db534-121">VBScript file that takes a parameter that specifies one or more send ports to unenlist and remove.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="db534-122">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="db534-122">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="db534-123">L'exemple Remove Send Port est constitué d'un seul fichier VBScript que vous ne devez ni créer ni initialiser.</span><span class="sxs-lookup"><span data-stu-id="db534-123">The Remove Send Port sample consists of a single VBScript file that you not need to build or initialize.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="db534-124">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="db534-124">Running This Sample</span></span>  
  
#### <a name="to-run-the-remove-send-port-sample"></a><span data-ttu-id="db534-125">Pour exécuter l'exemple Remove Send Port</span><span class="sxs-lookup"><span data-stu-id="db534-125">To run the Remove Send Port sample</span></span>  
  
1.  <span data-ttu-id="db534-126">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="db534-126">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="db534-127">\<*Exemples de chemin d’accès*> \Admin\WMI\Remove Port\VBScript\ de réception</span><span class="sxs-lookup"><span data-stu-id="db534-127">\<*Samples Path*>\Admin\WMI\Remove Receive Port\VBScript\\</span></span>  
  
2.  <span data-ttu-id="db534-128">Exécutez le fichier RemoveSendPort.vbs à l'aide du programme cscript en transmettant l'argument de ligne de commande suivant :</span><span class="sxs-lookup"><span data-stu-id="db534-128">Run the file RemoveSendPort.vbs using the cscript program, passing the following command-line argument:</span></span>  
  
     **\<**   
     <span data-ttu-id="db534-129">***SendPortName* >.**</span><span class="sxs-lookup"><span data-stu-id="db534-129">***SendPortName* >.**</span></span> <span data-ttu-id="db534-130">Nom du ou des ports d'envoi à supprimer.</span><span class="sxs-lookup"><span data-stu-id="db534-130">The name of the send port(s) to remove.</span></span> <span data-ttu-id="db534-131">Si le nom du port d'envoi contient des espaces, placez-le entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="db534-131">If the send port name contains spaces, enclose the name in quotes.</span></span>  
  
     <span data-ttu-id="db534-132">Exemple :</span><span class="sxs-lookup"><span data-stu-id="db534-132">For example:</span></span>  
  
    ```  
    cscript RemoveSendPort.vbs "My Business Send Port"  
    ```  
  
## <a name="comments"></a><span data-ttu-id="db534-133">Commentaires</span><span class="sxs-lookup"><span data-stu-id="db534-133">Comments</span></span>  
 <span data-ttu-id="db534-134">Toutes les tâches effectuées dans la console Administration de BizTalk Server peuvent également être effectuées à l'aide d'un script qui accède au modèle objet WMI de Windows.</span><span class="sxs-lookup"><span data-stu-id="db534-134">All tasks that you can perform in the BizTalk Server Administration console can also be performed by using script that accesses the Windows WMI object model.</span></span>  
  
 <span data-ttu-id="db534-135">Le fichier de script RemoveSendPort.vbs contient des commentaires détaillés avec davantage d'explications sur les opérations qu'il effectue.</span><span class="sxs-lookup"><span data-stu-id="db534-135">The script file RemoveSendPort.vbs contains detailed comments with further explanation about the operations that it performs.</span></span> <span data-ttu-id="db534-136">Pour plus d’informations, consultez Windows Management Instrumentation à [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span><span class="sxs-lookup"><span data-stu-id="db534-136">For more information, see Windows Management Instrumentation at [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db534-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db534-137">See Also</span></span>  
 [<span data-ttu-id="db534-138">Admin-WMI (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="db534-138">Admin-WMI (BizTalk Server Samples Folder)</span></span>](../core/admin-wmi-biztalk-server-samples-folder.md)