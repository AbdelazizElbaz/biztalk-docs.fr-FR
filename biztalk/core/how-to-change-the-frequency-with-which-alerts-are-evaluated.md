---
title: "Comment modifier la fréquence à laquelle les alertes sont évaluées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68f326ed-2017-4853-89b9-146cb0785554
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f921699e9a98724c8ca2c36f99d7eb9b9848875
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-change-the-frequency-with-which-alerts-are-evaluated"></a><span data-ttu-id="44f42-102">Modification de la fréquence à laquelle les alertes sont évaluées</span><span class="sxs-lookup"><span data-stu-id="44f42-102">How to Change the Frequency With Which Alerts Are Evaluated</span></span>
<span data-ttu-id="44f42-103">Dans certains cas, le générateur SQL Notifications Services ne parvient pas à suivre le rythme des événements déclenchés par le fournisseur d'événements BAM lorsqu'il est déployé avec les paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="44f42-103">There are cases in which the SQL Notifications services generator may not keep up with events being raised by the BAM event provider when deployed with the default settings.</span></span> <span data-ttu-id="44f42-104">Vous pouvez augmenter la fréquence (durée de quantum) à laquelle les événements sont évalués pour la généraltion d'alertes en modifiant le fichier adf.xml de Notification Services.</span><span class="sxs-lookup"><span data-stu-id="44f42-104">You can increase the frequency (the quantum duration) with which events are evaluated for alerts by modifying the Notification Services adf.xml file.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="44f42-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="44f42-105">Prerequisites</span></span>  
 <span data-ttu-id="44f42-106">Pour effectuer cette procédure, vous devez ouvrir une session en tant que membre d'un groupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] disposant d'autorisations en lecture et écriture sur la base de données d'importation principale (en principe, il s'agit du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="44f42-106">To perform this procedure you must be logged on as a member of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group that has permissions to read and write the Primary Import database, typically this will be a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-modify-the-notification-services-generator-quantum-duration"></a><span data-ttu-id="44f42-107">Pour modifier la durée de quantum du générateur Notification Services</span><span class="sxs-lookup"><span data-stu-id="44f42-107">To modify the Notification Services generator quantum duration</span></span>  
  
1.  <span data-ttu-id="44f42-108">Ouvrez l'Invite de commandes pour Notification Services.</span><span class="sxs-lookup"><span data-stu-id="44f42-108">Open the Notification Services Command prompt.</span></span> <span data-ttu-id="44f42-109">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2005**, cliquez sur **outils de Configuration**, puis cliquez sur **Invite de commandes des Services de notification**.</span><span class="sxs-lookup"><span data-stu-id="44f42-109">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2005**, click **Configuration Tools**, and then click **Notification Services Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="44f42-110">Accédez au fichier de configuration des services de notification.</span><span class="sxs-lookup"><span data-stu-id="44f42-110">Get the Notification Services configuration file.</span></span> <span data-ttu-id="44f42-111">À l’invite de commandes, tapez : **cscript ProcessBamNSFiles.vbs-obtenir le fichier config.xml adf.xml \<serveur de base de données PimaryImport\> \< nom de base de données PimaryImport\>**.</span><span class="sxs-lookup"><span data-stu-id="44f42-111">At the command prompt, type: **cscript ProcessBamNSFiles.vbs -Get config.xml adf.xml \<PimaryImport database server\> \< PimaryImport database name\>**.</span></span>  
  
3.  <span data-ttu-id="44f42-112">Modifier ou ajouter la \<QuantumDuration\> élément sous le \<ApplicationExecutionSettings\> nœud dans le dans le fichier adf.xml.</span><span class="sxs-lookup"><span data-stu-id="44f42-112">Modify or add the \<QuantumDuration\> element under the \<ApplicationExecutionSettings\> node in the in the adf.xml file.</span></span> <span data-ttu-id="44f42-113">Pour plus d’informations sur l’élément QuantumDuration, consultez [http://go.microsoft.com/fwlink/?LinkId=78803](http://go.microsoft.com/fwlink/?LinkId=78803).</span><span class="sxs-lookup"><span data-stu-id="44f42-113">For more information on the QuantumDuration element, see [http://go.microsoft.com/fwlink/?LinkId=78803](http://go.microsoft.com/fwlink/?LinkId=78803).</span></span>  
  
4.  <span data-ttu-id="44f42-114">À l’invite de commandes, tapez : **cscript ProcessBamNSFiles.vbs-mettre à jour le fichier config.xml adf.xml \<serveur de base de données PimaryImport\> \< nom de base de données PimaryImport\>.**</span><span class="sxs-lookup"><span data-stu-id="44f42-114">At the command prompt, type: **cscript ProcessBamNSFiles.vbs -Update  config.xml adf.xml  \<PimaryImport database server\> \< PimaryImport database name\>.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44f42-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44f42-115">See Also</span></span>  
 [<span data-ttu-id="44f42-116">Script de ligne de commande BAM pour des fichiers de configuration des services de notification</span><span class="sxs-lookup"><span data-stu-id="44f42-116">BAM Command-Line Script for Notification Services Configuration Files</span></span>](../core/bam-command-line-script-for-notification-services-configuration-files.md)