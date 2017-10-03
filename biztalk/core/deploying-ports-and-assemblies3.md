---
title: "Déploiement de Ports et Assemblies3 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, deploying
- Deployment Wizard
- assemblies, deploying
- deployment, ports and assemblies
ms.assetid: 92de8d9f-79d4-4c7a-a66a-12928bce350f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c37a677904143d4a925d035c409f485f43958ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-ports-and-assemblies"></a><span data-ttu-id="9d50d-102">Déploiement des ports et assemblys</span><span class="sxs-lookup"><span data-stu-id="9d50d-102">Deploying Ports and Assemblies</span></span>
<span data-ttu-id="9d50d-103">Avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez dupliquer des ports et des assemblys sur un ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="9d50d-103">With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9d50d-104">Exporte la configuration des emplacements de réception/ports envoi dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="9d50d-104"> exports the send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="9d50d-105">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet d'exécuter les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="9d50d-105">You can use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to do the following tasks:</span></span>  
  
-   <span data-ttu-id="9d50d-106">Déployer ou supprimer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblys dans une base de données de Configuration de BizTalk</span><span class="sxs-lookup"><span data-stu-id="9d50d-106">Deploy or remove [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblies in a BizTalk Configuration database</span></span>  
  
-   <span data-ttu-id="9d50d-107">Installer ou désinstaller des assemblys dans le global assembly cache (GAC)</span><span class="sxs-lookup"><span data-stu-id="9d50d-107">Install or uninstall the assemblies in the global assembly cache (GAC)</span></span>  
  
-   <span data-ttu-id="9d50d-108">Importer ou exporter des [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] informations de liaison d’assembly vers et à partir de fichiers de liaison</span><span class="sxs-lookup"><span data-stu-id="9d50d-108">Import or export [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assembly binding information to and from binding files</span></span>  
  
 <span data-ttu-id="9d50d-109">Pour plus d’informations sur l’utilisation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour déployer des ports et des assemblys, consultez [comment exporter les liaisons d’une Application BizTalk](../core/how-to-export-bindings-for-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="9d50d-109">For information about how to use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d50d-110">L'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne requiert l'installation de Visual Studio sur un ordinateur (de développement) source.</span><span class="sxs-lookup"><span data-stu-id="9d50d-110">The Microsoft BizTalk Adapter for JD Edwards EnterpriseOne only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="9d50d-111">Visual Studio n'est pas requis sur l'ordinateur de production.</span><span class="sxs-lookup"><span data-stu-id="9d50d-111">Visual Studio is not required on the production computer.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9d50d-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9d50d-112">In This Section</span></span>  
  
-   [<span data-ttu-id="9d50d-113">Vérification de la configuration du déploiement</span><span class="sxs-lookup"><span data-stu-id="9d50d-113">Verifying the Deployment Setup</span></span>](../core/verifying-the-deployment-setup1.md)  
  
-   [<span data-ttu-id="9d50d-114">L’importation de fichiers de liaison</span><span class="sxs-lookup"><span data-stu-id="9d50d-114">Importing Binding Files</span></span>](../core/importing-binding-files2.md)  
  
-   [<span data-ttu-id="9d50d-115">Limitations concernant le déploiement</span><span class="sxs-lookup"><span data-stu-id="9d50d-115">Deployment Limitations</span></span>](../core/deployment-limitations4.md)