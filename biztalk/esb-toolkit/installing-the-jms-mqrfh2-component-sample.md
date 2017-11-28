---
title: "Installation de l’exemple de composant JMS MQRFH2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a5bd855-512f-40a4-8038-ae9b847b1097
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b522d986524c77a53cf5a847f749a9ce41e2c50
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installing-the-jms-mqrfh2-component-sample"></a><span data-ttu-id="2935e-102">Installation de l’exemple de composant MQRFH2 JMS</span><span class="sxs-lookup"><span data-stu-id="2935e-102">Installing the JMS MQRFH2 Component Sample</span></span>
<span data-ttu-id="2935e-103">Pour utiliser cet exemple avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], vous devez également installer les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="2935e-103">To use this sample with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], you must also install the following:</span></span>  
  
-   <span data-ttu-id="2935e-104">IBM WebSphere MQ 5.3 (avec CSD12), WebSphere MQ 6.x ou WebSphere MQ 7.0</span><span class="sxs-lookup"><span data-stu-id="2935e-104">IBM WebSphere MQ 5.3 (with CSD12), WebSphere MQ 6.x or WebSphere MQ 7.0</span></span>  
  
-   <span data-ttu-id="2935e-105">Utilitaire pour les files d’attente et la récupération des messages de test de la « RfhUtil » JMS IBM</span><span class="sxs-lookup"><span data-stu-id="2935e-105">The IBM "RfhUtil" JMS test utility for queuing and retrieving messages</span></span>  
  
 <span data-ttu-id="2935e-106">L’exemple de composant de MQRFH2 JMS requiert le composant JMS MQRFH2 doit résider dans le dossier PipelineComponents de votre dossier d’installation de Microsoft BizTalk Server et les schémas correspondants à résider dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="2935e-106">The JMS MQRFH2 Component sample requires the JMS MQRFH2 component to reside in the PipelineComponents folder of your Microsoft BizTalk Server installation folder and the corresponding schemas to reside in the global assembly cache.</span></span> <span data-ttu-id="2935e-107">L’installation de le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] core copie automatiquement et installe les assemblys dans les emplacements corrects.</span><span class="sxs-lookup"><span data-stu-id="2935e-107">Installing the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] core automatically copies and installs the assemblies to the correct locations.</span></span> <span data-ttu-id="2935e-108">Toutefois, si nécessaire, vous pouvez effectuer ces tâches manuellement.</span><span class="sxs-lookup"><span data-stu-id="2935e-108">However, if required, you can manually perform these tasks.</span></span>  
  
 <span data-ttu-id="2935e-109">**Pour installer manuellement le composant de JMS MQRFH2 et des schémas**</span><span class="sxs-lookup"><span data-stu-id="2935e-109">**To manually install the JMS MQRFH2 component and schemas**</span></span>  
  
1.  <span data-ttu-id="2935e-110">Copiez l’assembly Microsoft.Practices.ESB.JMS.PipelineComponents.dll dans le dossier PipelineComponents de votre dossier d’installation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="2935e-110">Copy the assembly Microsoft.Practices.ESB.JMS.PipelineComponents.dll to the PipelineComponents folder of your BizTalk Server installation folder.</span></span>  
  
2.  <span data-ttu-id="2935e-111">Ajoutez l’assembly de schéma Microsoft.Practices.ESB.JMS.Schemas.Property.dll dans le global assembly cache à l’aide de l’outil de Configuration .NET Framework se trouve dans la section Outils d’administration de la **Démarrer** menu.</span><span class="sxs-lookup"><span data-stu-id="2935e-111">Add the schema assembly Microsoft.Practices.ESB.JMS.Schemas.Property.dll to the global assembly cache using the .NET Framework Configuration Tool located in the Administrative Tools section of the **Start** menu.</span></span>  
  
 <span data-ttu-id="2935e-112">Cette section décrit le processus d’installation de l’exemple JMS MQRFH2 dans l’application BizTalk de GlobalBank.JMS.</span><span class="sxs-lookup"><span data-stu-id="2935e-112">This section describes the process for installing the JMS MQRFH2 sample into the GlobalBank.JMS BizTalk application.</span></span> <span data-ttu-id="2935e-113">Avant d’installer cet exemple, vous devez installer le cœur de la boîte à outils ESB comme décrit dans [l’installation de BizTalk ESB Toolkit cœur](http://go.microsoft.com/fwlink/?LinkId=187612) ([http://go.microsoft.com/fwlink/?LinkId=187612](http://go.microsoft.com/fwlink/?LinkId=187612)).</span><span class="sxs-lookup"><span data-stu-id="2935e-113">Before you install this sample, you must install the ESB Toolkit Core as described in [Installing the BizTalk ESB Toolkit Core](http://go.microsoft.com/fwlink/?LinkId=187612) ([http://go.microsoft.com/fwlink/?LinkId=187612](http://go.microsoft.com/fwlink/?LinkId=187612)).</span></span>  
  
 <span data-ttu-id="2935e-114">Vous pouvez installer l’exemple de composant de MQRFH2 JMS à partir du projet de la solution ou utilisez le fichier Windows Installer inclus avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2935e-114">You can install the JMS MQRFH2 Component sample from the solution project or use the Windows Installer file included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span> <span data-ttu-id="2935e-115">Cette section contient les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="2935e-115">This section contains the following topics:</span></span>  
  
-   [<span data-ttu-id="2935e-116">Installer l’exemple de MQRFH2 JMS à l’aide de Scripts d’installation</span><span class="sxs-lookup"><span data-stu-id="2935e-116">Install the JMS MQRFH2 Sample Using the Install Scripts</span></span>](../esb-toolkit/install-the-jms-mqrfh2-sample-using-the-install-scripts.md)  
  
-   [<span data-ttu-id="2935e-117">Assemblys et artefacts installés par l’exemple de composant MQRFH2 JMS</span><span class="sxs-lookup"><span data-stu-id="2935e-117">Assemblies and Artifacts Installed by the JMS MQRFH2 Component Sample</span></span>](../esb-toolkit/assemblies-and-artifacts-installed-by-the-jms-mqrfh2-component-sample.md)  
  
-   [<span data-ttu-id="2935e-118">Testez l’Installation d’exemples de MQRFH2 JMS</span><span class="sxs-lookup"><span data-stu-id="2935e-118">Test the JMS MQRFH2 Sample Installation</span></span>](../esb-toolkit/test-the-jms-mqrfh2-sample-installation.md)