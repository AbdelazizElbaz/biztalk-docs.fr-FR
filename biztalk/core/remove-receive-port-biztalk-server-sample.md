---
title: "(Exemple BizTalk Server) de Port de réception de supprimer | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive ports, examples
- deleting, receive ports
- examples, receive ports
- receive ports, deleting
ms.assetid: de97d914-b8e8-4365-8041-3b455c351f86
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b97c3b6fe5e743e6bf19c979b994cc7eb5a942de
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="remove-receive-port-biztalk-server-sample"></a><span data-ttu-id="6d50e-102">Suppression de réception Port (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="6d50e-102">Remove Receive Port (BizTalk Server Sample)</span></span>
<span data-ttu-id="6d50e-103">L'exemple de suppression d'un port de réception (Remove Receive Port) illustre la suppression d'un ou plusieurs ports de réception.</span><span class="sxs-lookup"><span data-stu-id="6d50e-103">The Remove Receive Port sample demonstrates how to remove one or more receive ports.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="6d50e-104">Les scripts de déploiement devenus inutiles après le déploiement doivent être supprimés.</span><span class="sxs-lookup"><span data-stu-id="6d50e-104">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="6d50e-105">Les scripts d'administration et autres scripts conservés doivent être sécurisés à l'aide de listes de contrôle d'accès et étroitement surveillés.</span><span class="sxs-lookup"><span data-stu-id="6d50e-105">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="6d50e-106">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="6d50e-106">What This Sample Does</span></span>  
 <span data-ttu-id="6d50e-107">Le script Visual Basic Scripting Edition (VBScript) dans le fichier de script de cet exemple décrit l'exécution des opérations suivantes à l'aide du fournisseur WMI BizTalk Server :</span><span class="sxs-lookup"><span data-stu-id="6d50e-107">The Visual Basic Scripting Edition (VBScript) script in the script file that constitutes this sample shows how to perform the following operations using the BizTalk Server WMI provider:</span></span>  
  
-   <span data-ttu-id="6d50e-108">pour un nom de port de réception, création d'une requête pour obtenir la liste des ports de réception correspondants ;</span><span class="sxs-lookup"><span data-stu-id="6d50e-108">Given a receive port name, query for a list of matching receive ports.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d50e-109">En général, un seul port de réception correspond à un nom donné.</span><span class="sxs-lookup"><span data-stu-id="6d50e-109">Generally, there will only be one receive port that matches a given name.</span></span>  
  
-   <span data-ttu-id="6d50e-110">suppression de ces ports de réception ;</span><span class="sxs-lookup"><span data-stu-id="6d50e-110">Remove those receive ports.</span></span>  
  
-   <span data-ttu-id="6d50e-111">gestion de toutes erreurs de telle sorte que les informations significatives soient renvoyées à l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6d50e-111">Handle any errors such that meaningful information is returned to the user.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="6d50e-112">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="6d50e-112">Where to Find This Sample</span></span>  
 <span data-ttu-id="6d50e-113">Les exemples se trouvent dans l'emplacement SDK suivant :</span><span class="sxs-lookup"><span data-stu-id="6d50e-113">The samples are located in the following SDK location:</span></span>  
  
 <span data-ttu-id="6d50e-114">\<*Exemples de chemin d’accès*> \Admin\WMI\Remove LPT1\ de réception</span><span class="sxs-lookup"><span data-stu-id="6d50e-114">\<*Samples Path*>\Admin\WMI\Remove Receive Port\\</span></span>  
  
 <span data-ttu-id="6d50e-115">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="6d50e-115">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="6d50e-116">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="6d50e-116">File(s)</span></span>|<span data-ttu-id="6d50e-117"> Description</span><span class="sxs-lookup"><span data-stu-id="6d50e-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6d50e-118">Dans le dossier \VBScript :</span><span class="sxs-lookup"><span data-stu-id="6d50e-118">In the \VBScript folder:</span></span><br /><br /> <span data-ttu-id="6d50e-119">RemoveReceivePort.vbs</span><span class="sxs-lookup"><span data-stu-id="6d50e-119">RemoveReceivePort.vbs</span></span>|<span data-ttu-id="6d50e-120">Fichier VBScript qui récupère un paramètre spécifiant un ou plusieurs ports de réception à supprimer.</span><span class="sxs-lookup"><span data-stu-id="6d50e-120">VBScript file that takes a parameter that specifies one or more receive ports to remove.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="6d50e-121">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="6d50e-121">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="6d50e-122">L'exemple Remove Receive Port est constitué d'un seul fichier VBScript que vous ne devez ni créer ni initialiser.</span><span class="sxs-lookup"><span data-stu-id="6d50e-122">The Remove Receive Port sample consists of a single VBScript file that you do not need to build or initialize.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="6d50e-123">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="6d50e-123">Running This Sample</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="6d50e-124">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="6d50e-124">To run this sample</span></span>  
  
1.  <span data-ttu-id="6d50e-125">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="6d50e-125">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="6d50e-126">\<*Exemples de chemin d’accès*> \Admin\WMI\Remove Port\VBScript\ de réception</span><span class="sxs-lookup"><span data-stu-id="6d50e-126">\<*Samples Path*>\Admin\WMI\Remove Receive Port\VBScript\\</span></span>  
  
2.  <span data-ttu-id="6d50e-127">Exécutez le fichier RemoveReceivePort.vbs à l'aide du programme cscript en transmettant l'argument de ligne de commande suivant :</span><span class="sxs-lookup"><span data-stu-id="6d50e-127">Run the file RemoveReceivePort.vbs using the cscript program, passing the following command-line argument:</span></span>  
  
     **\<**   
     <span data-ttu-id="6d50e-128">***ReceivePortName* >**.</span><span class="sxs-lookup"><span data-stu-id="6d50e-128">***ReceivePortName* >**.</span></span> <span data-ttu-id="6d50e-129">Nom du ou des ports de réception à supprimer.</span><span class="sxs-lookup"><span data-stu-id="6d50e-129">The name of the receive port(s) to remove.</span></span> <span data-ttu-id="6d50e-130">Si le nom du port de réception contient des espaces, placez-le entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="6d50e-130">If the receive port name contains spaces, enclose the name in quotes.</span></span>  
  
     <span data-ttu-id="6d50e-131">Exemple :</span><span class="sxs-lookup"><span data-stu-id="6d50e-131">For example:</span></span>  
  
    ```  
    cscript RemoveReceivePort.vbs "My Business Receive Port"  
    ```  
  
## <a name="comments"></a><span data-ttu-id="6d50e-132">Commentaires</span><span class="sxs-lookup"><span data-stu-id="6d50e-132">Comments</span></span>  
 <span data-ttu-id="6d50e-133">Toutes les tâches effectuées dans la console Administration de BizTalk Server peuvent également être effectuées à l'aide d'un script qui accède au modèle objet WMI de Windows.</span><span class="sxs-lookup"><span data-stu-id="6d50e-133">All tasks that you can perform in the BizTalk Server Administration console can also be performed by using script that accesses the Windows WMI object model.</span></span>  
  
 <span data-ttu-id="6d50e-134">Le fichier de script RemoveReceivePort.vbs contient des commentaires détaillés avec davantage d'explications sur les opérations qu'il effectue.</span><span class="sxs-lookup"><span data-stu-id="6d50e-134">The script file RemoveReceivePort.vbs contains detailed comments with further explanation about the operations that it performs.</span></span> <span data-ttu-id="6d50e-135">Pour plus d’informations, consultez Windows Management Instrumentation à [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span><span class="sxs-lookup"><span data-stu-id="6d50e-135">For more information, see Windows Management Instrumentation at [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d50e-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d50e-136">See Also</span></span>  
 [<span data-ttu-id="6d50e-137">Admin-WMI (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="6d50e-137">Admin-WMI (BizTalk Server Samples Folder)</span></span>](../core/admin-wmi-biztalk-server-samples-folder.md)