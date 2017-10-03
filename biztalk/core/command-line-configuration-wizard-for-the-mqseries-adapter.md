---
title: "Assistant de Configuration de ligne de commande pour l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [MQSeries adapters], silent configuration
- MQSeries adapters, silent configuration
- configuring [MQSeries adapters], Command-Line Configuration Wizard
- Command-Line Configuration Wizard
- MQSeries adapters, Command-Line Configuration Wizard
ms.assetid: cab905d1-fe19-4d6a-be1b-f561e133e1d2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee73b890fca43a3651f22092486e5898862b0b72
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="command-line-configuration-wizard-for-the-mqseries-adapter"></a><span data-ttu-id="d7a1b-102">Assistant de Configuration de ligne de commande pour l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="d7a1b-102">Command-Line Configuration Wizard for the MQSeries Adapter</span></span>
<span data-ttu-id="d7a1b-103">L'Assistant inclut quatre options pour les actions d'installation, de désinstallation et de journalisation.</span><span class="sxs-lookup"><span data-stu-id="d7a1b-103">The wizard has four options for installing, uninstalling, and logging actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7a1b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7a1b-104">Syntax</span></span>  
 <span data-ttu-id="d7a1b-105">**mqsconfigwiz [/u] [/i config.xml] [/l logfile] [/?]**</span><span class="sxs-lookup"><span data-stu-id="d7a1b-105">**mqsconfigwiz [/u] [/i config.xml] [/l logfile] [/?]**</span></span>  
  
|<span data-ttu-id="d7a1b-106">Option</span><span class="sxs-lookup"><span data-stu-id="d7a1b-106">Option</span></span>|<span data-ttu-id="d7a1b-107"> Description</span><span class="sxs-lookup"><span data-stu-id="d7a1b-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d7a1b-108">**/u**</span><span class="sxs-lookup"><span data-stu-id="d7a1b-108">**/u**</span></span>|<span data-ttu-id="d7a1b-109">Désinstalle MQSAgent.</span><span class="sxs-lookup"><span data-stu-id="d7a1b-109">Uninstalls the MQSAgent.</span></span>|  
|<span data-ttu-id="d7a1b-110">**/i** *config.xml*</span><span class="sxs-lookup"><span data-stu-id="d7a1b-110">**/i** *config.xml*</span></span>|<span data-ttu-id="d7a1b-111">Installe MQSAgent à l’aide des informations dans le fichier *config.xml*.</span><span class="sxs-lookup"><span data-stu-id="d7a1b-111">Installs the MQSAgent using the information in the file *config.xml*.</span></span>|  
|<span data-ttu-id="d7a1b-112">**/l** *logfile*</span><span class="sxs-lookup"><span data-stu-id="d7a1b-112">**/l** *logfile*</span></span>|<span data-ttu-id="d7a1b-113">Enregistre les actions dans le fichier *logfile*.</span><span class="sxs-lookup"><span data-stu-id="d7a1b-113">Logs actions to the file *logfile*.</span></span>|  
|<span data-ttu-id="d7a1b-114">**/?**</span><span class="sxs-lookup"><span data-stu-id="d7a1b-114">**/?**</span></span>|<span data-ttu-id="d7a1b-115">Affiche une boîte de dialogue décrivant les options de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="d7a1b-115">Displays a dialog box describing the command-line options.</span></span>|  
  
 <span data-ttu-id="d7a1b-116">Le contenu du fichier XML incluant les informations de configuration peut varier, selon la version de Windows que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="d7a1b-116">The contents of the XML file that contains the configuration information may vary, depending on the version of Windows you are using.</span></span> <span data-ttu-id="d7a1b-117">Pour plus d’informations sur le format de fichier de configuration, consultez [le fichier de Configuration XML de l’adaptateur MQSeries](../core/xml-configuration-file-for-the-mqseries-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="d7a1b-117">For more information about the configuration file format, see [XML Configuration File for the MQSeries Adapter](../core/xml-configuration-file-for-the-mqseries-adapter.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d7a1b-118">L'adaptateur ne fonctionne pas pendant l'exécution de l'Assistant Configuration.</span><span class="sxs-lookup"><span data-stu-id="d7a1b-118">The adapter does not work while the configuration wizard is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7a1b-119">Vous ne pouvez pas reconfigurer MQSAgent à l'aide de l'Assistant Configuration de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="d7a1b-119">You cannot reconfigure MQSAgent with the command-line configuration wizard.</span></span> <span data-ttu-id="d7a1b-120">Vous devez d’abord exécuter l’Assistant pour désinstaller l’agent (**/u**), puis l’exécuter pour configurer (**/i**).</span><span class="sxs-lookup"><span data-stu-id="d7a1b-120">You must first run the wizard to uninstall the agent (**/u**), and then run it to configure (**/i**).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7a1b-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7a1b-121">See Also</span></span>  
 [<span data-ttu-id="d7a1b-122">Configuration silencieuse de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="d7a1b-122">Silent Configuration of the MQSeries Adapter</span></span>](../core/silent-configuration-of-the-mqseries-adapter.md)