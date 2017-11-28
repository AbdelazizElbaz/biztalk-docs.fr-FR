---
title: "Déploiement des composants de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, pipeline components [custom]
- pipeline components [custom], deploying
ms.assetid: 98b47fbf-62c0-4012-a406-58c4d56b305a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84ee3255c38e26c5f5d6d19797cba03ba549668b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-pipeline-components"></a><span data-ttu-id="becf9-102">Déploiement des composants de Pipeline</span><span class="sxs-lookup"><span data-stu-id="becf9-102">Deploying Pipeline Components</span></span>
<span data-ttu-id="becf9-103">Tous les les pipeline composant assemblys .NET (natifs et personnalisés) doivent se trouver dans le \< *répertoire d’installation*> dossier \Pipeline Components doit être exécuté par le serveur.</span><span class="sxs-lookup"><span data-stu-id="becf9-103">All the .NET pipeline component assemblies (native and custom) must be located in the \<*installation directory*>\Pipeline Components folder to be executed by the server.</span></span> <span data-ttu-id="becf9-104">Si le pipeline avec un composant personnalisé est déployé sur plusieurs serveurs, les composants du binaire doivent se trouver dans le dossier spécifié de chaque serveur.</span><span class="sxs-lookup"><span data-stu-id="becf9-104">If the pipeline with a custom component will be deployed across several servers, the component's binaries must be present in the specified folder on every server.</span></span>  
  
 <span data-ttu-id="becf9-105">Il n'est pas nécessaire d'ajouter un composant de pipeline personnalisé que le moteur d'exécution de BizTalk utilisera dans le Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="becf9-105">You do not need to add a custom pipeline component to be used by the BizTalk Runtime to the Global Assembly Cache (GAC).</span></span>  
  
 <span data-ttu-id="becf9-106">Les composants des services COM personnalisés du pipeline apparaîtront dans la boîte à outils, à condition d'être enregistrés sur l'ordinateur en tant que composant des services COM.</span><span class="sxs-lookup"><span data-stu-id="becf9-106">Custom COM components in the pipeline will also appear in the Toolbox, provided they are registered on the computer as a COM component.</span></span> <span data-ttu-id="becf9-107">Les composants de pipeline .NET personnalisés doivent être placés dans le \< *répertoire d’installation*> dossier \Pipeline Components.</span><span class="sxs-lookup"><span data-stu-id="becf9-107">Custom .NET pipeline components must be placed into the \<*installation directory*>\Pipeline Components folder.</span></span>  
  
 <span data-ttu-id="becf9-108">Après avoir installé les fichiers binaires dans l'emplacement approprié, ajoutez le composant à la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="becf9-108">After the binary files are in the correct location, you need to add the component to the Toolbox.</span></span> <span data-ttu-id="becf9-109">Pour obtenir des instructions sur l’ajout du composant de pipeline à la boîte à outils, consultez [l’utilisation de la boîte à outils](../core/how-to-use-the-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="becf9-109">For instructions on adding the pipeline component to the Toolbox, see [How to Use the Toolbox](../core/how-to-use-the-toolbox.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="becf9-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="becf9-110">See Also</span></span>  
 [<span data-ttu-id="becf9-111">Développement de composants de Pipeline personnalisé</span><span class="sxs-lookup"><span data-stu-id="becf9-111">Developing Custom Pipeline Components</span></span>](../core/developing-custom-pipeline-components.md)