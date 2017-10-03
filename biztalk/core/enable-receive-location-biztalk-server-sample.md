---
title: "Activer la réception emplacement (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, examples
- receive locations, enabling
- examples, receive locations
ms.assetid: dd04b38a-634d-4c9a-b31a-2f226fa91d19
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99923c3029b72dae660bee4b4089336e90e2e4e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="enable-receive-location-biztalk-server-sample"></a><span data-ttu-id="753fb-102">Activer la réception emplacement (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="753fb-102">Enable Receive Location (BizTalk Server Sample)</span></span>
<span data-ttu-id="753fb-103">L'exemple d'activation d'un emplacement de réception (Enable Receive Location) décrit l'activation d'un emplacement de réception, et éventuellement, la définition de l'URL de transport entrant pour cet emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="753fb-103">The Enable Receive Location sample demonstrates how to enable a receive location and optionally set the Inbound Transport URL for that receive location.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="753fb-104">Les scripts de déploiement devenus inutiles après le déploiement doivent être supprimés.</span><span class="sxs-lookup"><span data-stu-id="753fb-104">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="753fb-105">Les scripts d'administration et autres scripts conservés doivent être sécurisés à l'aide de listes de contrôle d'accès et étroitement surveillés.</span><span class="sxs-lookup"><span data-stu-id="753fb-105">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="753fb-106">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="753fb-106">What This Sample Does</span></span>  
 <span data-ttu-id="753fb-107">Le script Microsoft Visual Basic Scripting Edition (VBScript) dans le fichier de script de cet exemple décrit l'exécution des opérations suivantes à l'aide du fournisseur WMI BizTalk Server :</span><span class="sxs-lookup"><span data-stu-id="753fb-107">The Microsoft Visual Basic Scripting Edition (VBScript) script in the script file that constitutes this sample shows how to perform the following operations using the BizTalk Server WMI provider:</span></span>  
  
-   <span data-ttu-id="753fb-108">pour un nom de port de réception et un emplacement de réception, création d'une requête pour obtenir la liste des emplacements de réception correspondants ;</span><span class="sxs-lookup"><span data-stu-id="753fb-108">Given a receive port name and receive location, query for a list of matching receive locations.</span></span>  
  
-   <span data-ttu-id="753fb-109">définition de l'URL de transport entrant pour un emplacement de réception (relative au chemin d'installation) ;</span><span class="sxs-lookup"><span data-stu-id="753fb-109">Set the Inbound Transport URL for a receive location (relative to the installation path).</span></span>  
  
-   <span data-ttu-id="753fb-110">activation d'un emplacement de réception ;</span><span class="sxs-lookup"><span data-stu-id="753fb-110">Enable a receive location.</span></span>  
  
-   <span data-ttu-id="753fb-111">gestion de toutes erreurs de telle sorte que les informations significatives soient renvoyées à l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="753fb-111">Handle any errors such that meaningful information is returned to the user.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="753fb-112">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="753fb-112">Where to Find This Sample</span></span>  
 <span data-ttu-id="753fb-113">L'exemple se trouve dans l'emplacement SDK suivant :</span><span class="sxs-lookup"><span data-stu-id="753fb-113">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="753fb-114">\<*Exemples de chemin d’accès*> \Admin\WMI\Enable Location\ de réception</span><span class="sxs-lookup"><span data-stu-id="753fb-114">\<*Samples Path*>\Admin\WMI\Enable Receive Location\\</span></span>  
  
 <span data-ttu-id="753fb-115">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="753fb-115">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="753fb-116">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="753fb-116">File(s)</span></span>|<span data-ttu-id="753fb-117"> Description</span><span class="sxs-lookup"><span data-stu-id="753fb-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="753fb-118">Dans le dossier \VBScript :</span><span class="sxs-lookup"><span data-stu-id="753fb-118">In the \VBScript folder:</span></span><br /><br /> <span data-ttu-id="753fb-119">EnableRecLoc.vbs</span><span class="sxs-lookup"><span data-stu-id="753fb-119">EnableRecLoc.vbs</span></span>|<span data-ttu-id="753fb-120">Fichier VBScript qui utilise des paramètres spécifiant un emplacement de réception à activer, et éventuellement, une nouvelle valeur pour l'URL de transport entrant associée à cet emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="753fb-120">VBScript file that takes parameters that specify a receive location to be enabled, and optionally, a new value for the Inbound Transport URL associated with that receive location.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="753fb-121">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="753fb-121">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="753fb-122">L'exemple d'activation d'un emplacement de réception est constitué d'un seul fichier VBScript que vous ne devez ni créer ni initialiser.</span><span class="sxs-lookup"><span data-stu-id="753fb-122">The Enable Receive Location sample consists of a single VBScript file that you do not need to build or initialize.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="753fb-123">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="753fb-123">Running This Sample</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="753fb-124">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="753fb-124">To run this sample</span></span>  
  
1.  <span data-ttu-id="753fb-125">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="753fb-125">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="753fb-126">\<*Exemples de chemin d’accès*> \Admin\WMI\Enable Location\VBScript\ de réception</span><span class="sxs-lookup"><span data-stu-id="753fb-126">\<*Samples Path*>\Admin\WMI\Enable Receive Location\VBScript\\</span></span>  
  
2.  <span data-ttu-id="753fb-127">Exécutez le fichier EnableRecLoc.vbs à l'aide du programme cscript en transmettant les arguments de ligne de commande suivants (le troisième argument est facultatif) :</span><span class="sxs-lookup"><span data-stu-id="753fb-127">Run the file EnableRecLoc.vbs using the cscript program, passing the following command-line arguments, of which the third one is optional:</span></span>  
  
    -   **\<**   
         <span data-ttu-id="753fb-128">***ReceivePortName* >.**</span><span class="sxs-lookup"><span data-stu-id="753fb-128">***ReceivePortName* >.**</span></span> <span data-ttu-id="753fb-129">Nom du port de réception contenant l'emplacement de réception à activer.</span><span class="sxs-lookup"><span data-stu-id="753fb-129">The name of the receive port that contains the receive location to be enabled.</span></span> <span data-ttu-id="753fb-130">Si le nom du port de réception contient des espaces, placez-le entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="753fb-130">If the receive port name contains spaces, enclose the name in quotes.</span></span>  
  
    -   **\<**   
         <span data-ttu-id="753fb-131">***ReceiveLocationName* >.**</span><span class="sxs-lookup"><span data-stu-id="753fb-131">***ReceiveLocationName* >.**</span></span> <span data-ttu-id="753fb-132">Nom de l'emplacement de réception à activer au sein du port de réception spécifié.</span><span class="sxs-lookup"><span data-stu-id="753fb-132">The name of the receive location within the specified receive port to be enabled.</span></span> <span data-ttu-id="753fb-133">Si le nom de l'emplacement de réception contient des espaces, placez-le entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="753fb-133">If the receive location name contains spaces, enclose the name in quotes.</span></span>  
  
    -   **\<**   
         <span data-ttu-id="753fb-134">***InboundTransportURI* >.**</span><span class="sxs-lookup"><span data-stu-id="753fb-134">***InboundTransportURI* >.**</span></span> <span data-ttu-id="753fb-135">URI d'adaptateur de réception, relative à l'emplacement d'installation du produit, que vous pouvez modifier en spécifiant cet argument.</span><span class="sxs-lookup"><span data-stu-id="753fb-135">A receive adapter URI, relative to the product installation location, that you can change by specifying this argument.</span></span> <span data-ttu-id="753fb-136">Si l'URI de l'adaptateur entrant contient des espaces, placez-le entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="753fb-136">If the inbound adapter URI contains spaces, enclose the URI in quotes.</span></span>  
  
         <span data-ttu-id="753fb-137">Exemple :</span><span class="sxs-lookup"><span data-stu-id="753fb-137">For example:</span></span>  
  
        ```  
        cscript EnableRecLoc.vbs "My Business Receive Port" MyBusinessReceiveLocation  
        ```  
  
         <span data-ttu-id="753fb-138">-OU-</span><span class="sxs-lookup"><span data-stu-id="753fb-138">-OR-</span></span>  
  
        ```  
        cscript EnableRecLoc.vbs MyBusinessReceivePort "My Business Receive Location" SDK\Samples\HelloWorld\In\*.xml  
        ```  
  
## <a name="comments"></a><span data-ttu-id="753fb-139">Commentaires</span><span class="sxs-lookup"><span data-stu-id="753fb-139">Comments</span></span>  
 <span data-ttu-id="753fb-140">Toutes les tâches effectuées dans la console Administration de BizTalk Server peuvent également être effectuées à l'aide d'un script qui accède au modèle objet WMI de Windows.</span><span class="sxs-lookup"><span data-stu-id="753fb-140">All tasks that you can perform in the BizTalk Server Administration console can also be performed by using script that accesses the Windows WMI object model.</span></span>  
  
 <span data-ttu-id="753fb-141">Le fichier de script EnableRecLoc.vbs contient des commentaires détaillés avec davantage d'explications sur les opérations qu'il effectue.</span><span class="sxs-lookup"><span data-stu-id="753fb-141">The script file EnableRecLoc.vbs contains detailed comments with further explanation about the operations that it performs.</span></span>  
  
 <span data-ttu-id="753fb-142">Pour plus d’informations, consultez Windows Management Instrumentation à [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span><span class="sxs-lookup"><span data-stu-id="753fb-142">For more information, see Windows Management Instrumentation at [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="753fb-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="753fb-143">See Also</span></span>  
 [<span data-ttu-id="753fb-144">Admin-WMI (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="753fb-144">Admin-WMI (BizTalk Server Samples Folder)</span></span>](../core/admin-wmi-biztalk-server-samples-folder.md)