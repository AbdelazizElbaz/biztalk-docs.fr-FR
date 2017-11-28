---
title: "Définir la propriété du Gestionnaire d’envoi (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SMTP adapters, examples
- examples, SMTP adapters
- send handlers, properties
ms.assetid: eb6ae2f2-528f-44ec-bca4-f37006893ff2
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0e14f58cbdd07a8c13dec6cd44fbc95584f2ecc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="set-send-handler-property-biztalk-server-sample"></a><span data-ttu-id="bcb5f-102">Définir la propriété du Gestionnaire d’envoi (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="bcb5f-102">Set Send Handler Property (BizTalk Server Sample)</span></span>
<span data-ttu-id="bcb5f-103">L'exemple de définition des propriétés du gestionnaire d'envoi (Set Send Handler Property) illustre la définition des informations de configuration XML pour un gestionnaire d'envoi SMTP (Simple Mail Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="bcb5f-103">The Set Send Handler Property sample demonstrates how to set the XML configuration information for a Simple Mail Transfer Protocol (SMTP) send handler.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="bcb5f-104">Les scripts de déploiement devenus inutiles après le déploiement doivent être supprimés.</span><span class="sxs-lookup"><span data-stu-id="bcb5f-104">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="bcb5f-105">Les scripts d'administration et autres scripts conservés doivent être sécurisés à l'aide de listes de contrôle d'accès et étroitement surveillés.</span><span class="sxs-lookup"><span data-stu-id="bcb5f-105">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="bcb5f-106">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="bcb5f-106">What This Sample Does</span></span>  
 <span data-ttu-id="bcb5f-107">Le script Visual Basic Scripting Edition (VBScript) dans le fichier de script de cet exemple décrit l'exécution des opérations suivantes à l'aide du fournisseur WMI BizTalk Server :</span><span class="sxs-lookup"><span data-stu-id="bcb5f-107">The Visual Basic Scripting Edition (VBScript) script in the script file that constitutes this sample shows how to perform the following operations using the BizTalk Server WMI provider:</span></span>  
  
-   <span data-ttu-id="bcb5f-108">pour un nom du gestionnaire d'envoi, création d'une requête pour obtenir la liste des gestionnaires d'envoi correspondants.</span><span class="sxs-lookup"><span data-stu-id="bcb5f-108">Given a send handler name, query for a list of matching send handlers.</span></span>  
  
-   <span data-ttu-id="bcb5f-109">définition des informations de configuration XML pour un gestionnaire d'envoi SMTP.</span><span class="sxs-lookup"><span data-stu-id="bcb5f-109">Set the XML configuration information for an SMTP send handler.</span></span>  
  
-   <span data-ttu-id="bcb5f-110">gestion de toutes erreurs de telle sorte que les informations significatives soient renvoyées à l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bcb5f-110">Handle any errors such that meaningful information is returned to the user.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="bcb5f-111">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="bcb5f-111">Where to Find This Sample</span></span>  
 <span data-ttu-id="bcb5f-112">Les fichiers de l'exemple se trouvent dans l'emplacement SDK suivant :</span><span class="sxs-lookup"><span data-stu-id="bcb5f-112">The sample files are located in the following SDK location:</span></span>  
  
 <span data-ttu-id="bcb5f-113">\<*Exemples de chemin d’accès*> \Admin\WMI\Set Property\ du Gestionnaire d’envoi</span><span class="sxs-lookup"><span data-stu-id="bcb5f-113">\<*Samples Path*>\Admin\WMI\Set Send Handler Property\\</span></span>  
  
 <span data-ttu-id="bcb5f-114">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="bcb5f-114">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="bcb5f-115">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="bcb5f-115">File(s)</span></span>|<span data-ttu-id="bcb5f-116"> Description</span><span class="sxs-lookup"><span data-stu-id="bcb5f-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bcb5f-117">Dans le dossier \VBScript :</span><span class="sxs-lookup"><span data-stu-id="bcb5f-117">In the \VBScript folder:</span></span><br /><br /> <span data-ttu-id="bcb5f-118">ConfigureSMTP.vbs</span><span class="sxs-lookup"><span data-stu-id="bcb5f-118">ConfigureSMTP.vbs</span></span>|<span data-ttu-id="bcb5f-119">Fichier VBScript qui utilise des paramètres spécifiant un gestionnaire d'envoi SMTP et une adresse de messagerie d'expéditeur.</span><span class="sxs-lookup"><span data-stu-id="bcb5f-119">VBScript file that takes parameters that specify an SMTP send handler and a From e-mail address.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="bcb5f-120">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="bcb5f-120">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="bcb5f-121">L'exemple Set Send Handler Property est constitué d'un seul fichier VBScript que vous ne devez ni créer ni initialiser.</span><span class="sxs-lookup"><span data-stu-id="bcb5f-121">The Set Send Handler Property sample consists of a single VBScript file that you do not need to build or initialize.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="bcb5f-122">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="bcb5f-122">Running This Sample</span></span>  
  
#### <a name="to-run-the-set-send-handler-property-sample"></a><span data-ttu-id="bcb5f-123">Pour exécuter l'exemple Set Send Handler Property</span><span class="sxs-lookup"><span data-stu-id="bcb5f-123">To run the Set Send Handler Property sample</span></span>  
  
1.  <span data-ttu-id="bcb5f-124">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="bcb5f-124">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="bcb5f-125">\<*Exemples de chemin d’accès*> \Admin\WMI\Set Property\VBScript\ du Gestionnaire d’envoi</span><span class="sxs-lookup"><span data-stu-id="bcb5f-125">\<*Samples Path*>\Admin\WMI\Set Send Handler Property\VBScript\\</span></span>  
  
2.  <span data-ttu-id="bcb5f-126">Exécutez le fichier ConfigureSMTP.vbs à l'aide du programme cscript en transmettant l'argument de ligne de commande suivant :</span><span class="sxs-lookup"><span data-stu-id="bcb5f-126">Run the file ConfigureSMTP.vbs using the cscript program, passing the following command-line argument:</span></span>  
  
    -   **\<**   
         <span data-ttu-id="bcb5f-127">***SMTPServerName* >.**</span><span class="sxs-lookup"><span data-stu-id="bcb5f-127">***SMTPServerName* >.**</span></span> <span data-ttu-id="bcb5f-128">Nom du serveur SMTP à utiliser pour envoyer le message.</span><span class="sxs-lookup"><span data-stu-id="bcb5f-128">The name of the SMTP server that will be used to send mail.</span></span>  
  
    -   **\<**   
         <span data-ttu-id="bcb5f-129">***FromEmailAddress* >.**</span><span class="sxs-lookup"><span data-stu-id="bcb5f-129">***FromEmailAddress* >.**</span></span> <span data-ttu-id="bcb5f-130">Adresse de messagerie qui sera utilisée comme adresse d'expéditeur.</span><span class="sxs-lookup"><span data-stu-id="bcb5f-130">An e-mail address that will be used as the From address.</span></span>  
  
         <span data-ttu-id="bcb5f-131">Exemple :</span><span class="sxs-lookup"><span data-stu-id="bcb5f-131">For example:</span></span>  
  
        ```  
        cscript ConfigureSMTP.vbs MyBusinessSMTPServer someone@example.com  
        ```  
  
## <a name="comments"></a><span data-ttu-id="bcb5f-132">Commentaires</span><span class="sxs-lookup"><span data-stu-id="bcb5f-132">Comments</span></span>  
 <span data-ttu-id="bcb5f-133">Toutes les tâches effectuées dans la console Administration de BizTalk Server peuvent également être effectuées à l'aide d'un script qui accède au modèle objet WMI de Windows.</span><span class="sxs-lookup"><span data-stu-id="bcb5f-133">All tasks that you can perform in the BizTalk Server Administration console can also be performed by using script that accesses the Windows WMI object model.</span></span>  
  
 <span data-ttu-id="bcb5f-134">Le fichier de script ConfigureSMTP.vbs contient des commentaires détaillés avec davantage d'explications sur les opérations qu'il effectue.</span><span class="sxs-lookup"><span data-stu-id="bcb5f-134">The script file ConfigureSMTP.vbs contains detailed comments with further explanation about the operations that it performs.</span></span> <span data-ttu-id="bcb5f-135">Pour plus d’informations, consultez Windows Management Instrumentation à [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span><span class="sxs-lookup"><span data-stu-id="bcb5f-135">For more information, see Windows Management Instrumentation at [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcb5f-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bcb5f-136">See Also</span></span>  
 [<span data-ttu-id="bcb5f-137">Admin-WMI (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="bcb5f-137">Admin-WMI (BizTalk Server Samples Folder)</span></span>](../core/admin-wmi-biztalk-server-samples-folder.md)