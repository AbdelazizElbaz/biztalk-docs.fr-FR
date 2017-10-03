---
title: "À l’aide de Scripts de pré-traitement et post-traitement pour personnaliser le déploiement d’Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- customizing, applications
- applications, customizing
- scripts, applications
- scripts, customizing
ms.assetid: 47627394-d594-491b-9098-38c5d028a378
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7dc0afd7ed042f475a9a008125c968f401e6df92
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-pre--and-post-processing-scripts-to-customize-application-deployment"></a><span data-ttu-id="5854a-102">Utilisation des scripts de pré-traitement et de post-traitement pour personnaliser le déploiement de l'application</span><span class="sxs-lookup"><span data-stu-id="5854a-102">Using Pre- and Post-processing Scripts to Customize Application Deployment</span></span>
<span data-ttu-id="5854a-103">Les rubriques de cette section expliquent comment créer des scripts de pré-traitement et post-traitement pour réaliser un certain nombre de tâches lors de l'importation, l'installation ou la désinstallation d'une application.</span><span class="sxs-lookup"><span data-stu-id="5854a-103">The topics in this section describe how to create pre- or post-processing scripts to perform actions when an application is imported, installed, or uninstalled.</span></span> <span data-ttu-id="5854a-104">Les scripts de pré-traitement permettent de réaliser ces tâches avant l'importation ou l'installation d'une application et à la fin de la désinstallation,</span><span class="sxs-lookup"><span data-stu-id="5854a-104">Pre-processing scripts perform an action or set of actions before application import or installation starts, and after uninstallation completes.</span></span> <span data-ttu-id="5854a-105">tandis que les scripts de post-traitement permettent de les réaliser après l'importation ou l'installation d'une application et avant la désinstallation.</span><span class="sxs-lookup"><span data-stu-id="5854a-105">Post-processing scripts perform an action or set of actions after application import or installation completes, or before uninstallation starts.</span></span>  
  
 <span data-ttu-id="5854a-106">Un script de pré-traitement peut ainsi vous permettre de sauvegarder des fichiers de ressources avant qu'ils ne soient écrasés au cours de l'installation,</span><span class="sxs-lookup"><span data-stu-id="5854a-106">You might, for example, want to include a pre-processing script that will run before installation to back up resource files before they are overwritten during installation.</span></span> <span data-ttu-id="5854a-107">et un script de post-traitement d'ajouter un certificat au magasin de certificats après l'installation d'une application.</span><span class="sxs-lookup"><span data-stu-id="5854a-107">Or you might want to run a post-processing script to add a certificate to the certificate store after an application is installed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5854a-108">BizTalk Server inclut des exemples de ces deux types de scripts.</span><span class="sxs-lookup"><span data-stu-id="5854a-108">BizTalk Server includes sample pre- and post-processing scripts.</span></span> <span data-ttu-id="5854a-109">Pour plus d’informations sur les exemples de scripts, consultez [(exemple de déploiement d’Application) de modèle](../core/template-application-deployment-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5854a-109">For information about using the sample scripts, see [Template (Application Deployment Sample)](../core/template-application-deployment-sample.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5854a-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5854a-110">In This Section</span></span>  
  
-   [<span data-ttu-id="5854a-111">Création d’un Script de pré-traitement ou post-traitement</span><span class="sxs-lookup"><span data-stu-id="5854a-111">Creating a Pre- or Post-processing Script</span></span>](../core/creating-a-pre-or-post-processing-script.md)  
  
-   [<span data-ttu-id="5854a-112">Comment les Variables d’environnement indiquent état du déploiement</span><span class="sxs-lookup"><span data-stu-id="5854a-112">How Environment Variables Indicate Deployment State</span></span>](../core/how-environment-variables-indicate-deployment-state.md)  
  
-   [<span data-ttu-id="5854a-113">État des artefacts de fichier au cours du déploiement</span><span class="sxs-lookup"><span data-stu-id="5854a-113">Status of File Artifacts During Deployment</span></span>](../core/status-of-file-artifacts-during-deployment.md)  
  
-   [<span data-ttu-id="5854a-114">Variables d’environnement de Script de pré-traitement et de post-traitement</span><span class="sxs-lookup"><span data-stu-id="5854a-114">Pre- and Post-processing Script Environment Variables</span></span>](../core/pre-and-post-processing-script-environment-variables.md)