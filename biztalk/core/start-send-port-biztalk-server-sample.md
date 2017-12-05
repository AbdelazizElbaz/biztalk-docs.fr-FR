---
title: "Port d’envoi de début (exemple BizTalk Server) | Documents Microsoft"
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
- send ports, starting
ms.assetid: 84e54c9e-e9e8-4bb2-a191-20c29e127dae
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f293d00848c32f6b519349543c8a39824d9bca8c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="start-send-port-biztalk-server-sample"></a><span data-ttu-id="fe04b-102">Port d’envoi de début (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="fe04b-102">Start Send Port (BizTalk Server Sample)</span></span>
<span data-ttu-id="fe04b-103">L'exemple de démarrage d'un port d'envoi (Start Send Port) décrit le démarrage d'un port d'envoi et la définition éventuelle de l'adresse de transport principal lorsque l'adaptateur FILE est utilisé.</span><span class="sxs-lookup"><span data-stu-id="fe04b-103">The Start Send Port sample demonstrates how to start a send port and optionally set the Primary Transport Address when using the FILE adapter.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="fe04b-104">Les scripts de déploiement devenus inutiles après le déploiement doivent être supprimés.</span><span class="sxs-lookup"><span data-stu-id="fe04b-104">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="fe04b-105">Les scripts d'administration et autres scripts conservés doivent être sécurisés à l'aide de listes de contrôle d'accès et étroitement surveillés.</span><span class="sxs-lookup"><span data-stu-id="fe04b-105">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="fe04b-106">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="fe04b-106">What This Sample Does</span></span>  
 <span data-ttu-id="fe04b-107">Le script Visual Basic Scripting Edition (VBScript) dans le fichier de script de cet exemple décrit l'exécution des opérations suivantes à l'aide du fournisseur WMI BizTalk Server :</span><span class="sxs-lookup"><span data-stu-id="fe04b-107">The Visual Basic Scripting Edition (VBScript) script in the script file that constitutes this sample shows how to perform the following operations using the BizTalk Server WMI provider:</span></span>  
  
-   <span data-ttu-id="fe04b-108">pour un nom de port d'envoi, création d'une requête pour obtenir la liste des ports d'envoi correspondants.</span><span class="sxs-lookup"><span data-stu-id="fe04b-108">Given a send port name, query for a list of matching send ports.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fe04b-109">En général, un seul port d'envoi correspond à un nom donné.</span><span class="sxs-lookup"><span data-stu-id="fe04b-109">Generally, there will only be one send port that matches a given name.</span></span>  
  
-   <span data-ttu-id="fe04b-110">définition de l'adresse de transport principal pour ces ports d'envoi (relative au chemin d'installation).</span><span class="sxs-lookup"><span data-stu-id="fe04b-110">Set the Primary Transport Address for those send ports (relative to the installation path).</span></span>  
  
-   <span data-ttu-id="fe04b-111">démarrage de ces ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="fe04b-111">Start those send ports.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="fe04b-112">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="fe04b-112">Where to Find This Sample</span></span>  
 <span data-ttu-id="fe04b-113">Les fichiers de l'exemple se trouvent dans l'emplacement SDK suivant :</span><span class="sxs-lookup"><span data-stu-id="fe04b-113">The sample files are located in the following SDK location:</span></span>  
  
 <span data-ttu-id="fe04b-114">\<*Exemples de chemin d’accès*\>\Admin\WMI\Start LPT1\ d’envoi</span><span class="sxs-lookup"><span data-stu-id="fe04b-114">\<*Samples Path*\>\Admin\WMI\Start Send Port\\</span></span>  
  
 <span data-ttu-id="fe04b-115">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="fe04b-115">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="fe04b-116">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="fe04b-116">File(s)</span></span>|<span data-ttu-id="fe04b-117"> Description</span><span class="sxs-lookup"><span data-stu-id="fe04b-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fe04b-118">Dans le dossier \VBScript :</span><span class="sxs-lookup"><span data-stu-id="fe04b-118">In the \VBScript folder:</span></span><br /><br /> <span data-ttu-id="fe04b-119">StartSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="fe04b-119">StartSendPort.vbs</span></span>|<span data-ttu-id="fe04b-120">Fichier VBScript qui utilise des paramètres spécifiant un port d'envoi à démarrer, et éventuellement, une nouvelle valeur pour l'adresse de transport principal associée à ce port.</span><span class="sxs-lookup"><span data-stu-id="fe04b-120">VBScript file that takes parameters that specify a send port to start, and optionally, a new value for the Primary Transport Address associated with that port.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="fe04b-121">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="fe04b-121">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="fe04b-122">L'exemple Start Send Port est constitué d'un seul fichier VBScript que vous ne devez ni créer ni initialiser.</span><span class="sxs-lookup"><span data-stu-id="fe04b-122">The Start Send Port sample consists of a single VBScript file that you do not need to build or initialize.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="fe04b-123">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="fe04b-123">Running This Sample</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="fe04b-124">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="fe04b-124">To run this sample</span></span>  
  
1.  <span data-ttu-id="fe04b-125">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="fe04b-125">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="fe04b-126">\<*Exemples de chemin d’accès*\>\Admin\WMI\Start Port\VBScript\ d’envoi</span><span class="sxs-lookup"><span data-stu-id="fe04b-126">\<*Samples Path*\>\Admin\WMI\Start Send Port\VBScript\\</span></span>  
  
2.  <span data-ttu-id="fe04b-127">Exécutez le fichier StartSendPort.vbs à l'aide du programme cscript en transmettant les arguments de ligne de commande suivants (le second argument est facultatif) :</span><span class="sxs-lookup"><span data-stu-id="fe04b-127">Run the file StartSendPort.vbs using the cscript program, passing the following command-line arguments, the second of which is optional:</span></span>  
  
    -   <span data-ttu-id="fe04b-128">**\<** ***SendPortName* \>.**</span><span class="sxs-lookup"><span data-stu-id="fe04b-128">**\<** ***SendPortName* \>.**</span></span> <span data-ttu-id="fe04b-129">Nom du port d'envoi à démarrer.</span><span class="sxs-lookup"><span data-stu-id="fe04b-129">The name of the send port to start.</span></span> <span data-ttu-id="fe04b-130">Si le nom du port d'envoi contient des espaces, placez-le entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="fe04b-130">If the send port name contains spaces, enclose the name in quotes.</span></span>  
  
    -   <span data-ttu-id="fe04b-131">**\<** ***PrimaryTransportAddress* \>.**</span><span class="sxs-lookup"><span data-stu-id="fe04b-131">**\<** ***PrimaryTransportAddress* \>.**</span></span> <span data-ttu-id="fe04b-132">Adresse de transport principal, relative à l'emplacement d'installation du produit, que vous pouvez modifier en spécifiant cet argument.</span><span class="sxs-lookup"><span data-stu-id="fe04b-132">The Primary Transport Address, relative to the product installation location, that you can change by specifying this argument.</span></span> <span data-ttu-id="fe04b-133">Si l'adresse de l'adaptateur principal contient des espaces, placez-la entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="fe04b-133">If the primary adapter address contains spaces, enclose the name in quotes.</span></span>  
  
         <span data-ttu-id="fe04b-134">Exemple :</span><span class="sxs-lookup"><span data-stu-id="fe04b-134">For example:</span></span>  
  
        ```  
        cscript StartSendPort.vbs "My Business Send Port" SDK\Samples\HelloWorld\Out\%MessageID%.xml  
        ```  
  
## <a name="comments"></a><span data-ttu-id="fe04b-135">Commentaires</span><span class="sxs-lookup"><span data-stu-id="fe04b-135">Comments</span></span>  
 <span data-ttu-id="fe04b-136">Toutes les tâches effectuées dans la console Administration de BizTalk Server peuvent également être effectuées à l'aide d'un script qui accède au modèle objet WMI de Windows.</span><span class="sxs-lookup"><span data-stu-id="fe04b-136">All tasks that you can perform in the BizTalk Server Administration console can also be performed by using script that accesses the Windows WMI object model.</span></span>  
  
 <span data-ttu-id="fe04b-137">Le fichier de script StartSendPort.vbs contient des commentaires détaillés avec davantage d'explications sur les opérations qu'il effectue.</span><span class="sxs-lookup"><span data-stu-id="fe04b-137">The script file StartSendPort.vbs contains detailed comments with further explanation about the operations that it performs.</span></span> <span data-ttu-id="fe04b-138">Pour plus d’informations, consultez Windows Management Instrumentation à [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span><span class="sxs-lookup"><span data-stu-id="fe04b-138">For more information, see Windows Management Instrumentation at [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe04b-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe04b-139">See Also</span></span>  
 [<span data-ttu-id="fe04b-140">Admin-WMI (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="fe04b-140">Admin-WMI (BizTalk Server Samples Folder)</span></span>](../core/admin-wmi-biztalk-server-samples-folder.md)