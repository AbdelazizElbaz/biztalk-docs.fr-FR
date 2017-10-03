---
title: "Exportation de stratégies, les liaisons et les Applications BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, exporting
- exporting, policies
- bindings, exporting
- exporting, applications
- applications, exporting
- exporting, bindings
ms.assetid: ac101206-be49-47c9-a354-4f39e8b77acf
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d6df445b0fefc132940a736870d66c62329ce60
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exporting-biztalk-applications-bindings-and-policies"></a><span data-ttu-id="9b509-102">Exportation d'applications, de liaisons et de stratégies BizTalk</span><span class="sxs-lookup"><span data-stu-id="9b509-102">Exporting BizTalk Applications, Bindings, and Policies</span></span>
<span data-ttu-id="9b509-103">Cette section explique comment exporter une application, des liaisons ou des stratégies BizTalk.</span><span class="sxs-lookup"><span data-stu-id="9b509-103">This section describes how to export a BizTalk application, bindings, or policies.</span></span> <span data-ttu-id="9b509-104">Vous pouvez exporter tout ou partie des artefacts contenus dans une application BizTalk, ou uniquement ses liaisons ou stratégies.</span><span class="sxs-lookup"><span data-stu-id="9b509-104">You can export some or all of the artifacts contained in a BizTalk application, or you can export only its bindings or policies.</span></span> <span data-ttu-id="9b509-105">L'exportation d'une application génère un fichier Windows Installer (.msi) contenant les artefacts qu'elle contient et que vous sélectionnez pour l'exportation.</span><span class="sxs-lookup"><span data-stu-id="9b509-105">Exporting an application creates a Windows Installer (.msi) file containing the application artifacts that you selected for export.</span></span> <span data-ttu-id="9b509-106">L'exportation de liaisons ou de stratégies génère un fichier .xml des liaisons ou stratégies.</span><span class="sxs-lookup"><span data-stu-id="9b509-106">Exporting bindings or policies creates an .xml file of the bindings or policies.</span></span> <span data-ttu-id="9b509-107">Pour plus d’informations sur ce processus, consultez [ce qui se produit lorsque artefacts sont exportées](../core/what-happens-when-artifacts-are-exported.md).</span><span class="sxs-lookup"><span data-stu-id="9b509-107">For background information on this process, see [What Happens When Artifacts Are Exported](../core/what-happens-when-artifacts-are-exported.md).</span></span>  
  
 <span data-ttu-id="9b509-108">Vous pouvez importer le fichier .msi d'une application dans un autre groupe BizTalk pour y créer une nouvelle application contenant les artefacts de l'application.</span><span class="sxs-lookup"><span data-stu-id="9b509-108">You can import an application .msi file into another BizTalk group to create a new application that contains the application's artifacts in that group.</span></span> <span data-ttu-id="9b509-109">Vous pouvez importer un fichier .xml de liaison ou de stratégie dans une autre application BizTalk application afin d'utiliser les liaisons ou stratégies.</span><span class="sxs-lookup"><span data-stu-id="9b509-109">You can import a binding or policy .xml file into another BizTalk application to use the bindings or policies.</span></span> <span data-ttu-id="9b509-110">Décrit comment importer des artefacts dans [l’importation des Applications BizTalk, les liaisons et les stratégies](../core/importing-biztalk-applications-bindings-and-policies.md).</span><span class="sxs-lookup"><span data-stu-id="9b509-110">How to import artifacts is described in [Importing BizTalk Applications, Bindings, and Policies](../core/importing-biztalk-applications-bindings-and-policies.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9b509-111">Stockez les fichiers de liaison dans un emplacement sécurisé, car ils peuvent contenir des données critiques telles que des informations de connexion et de configuration.</span><span class="sxs-lookup"><span data-stu-id="9b509-111">Store binding files in a secure location, as they may contain critical business data such as connectivity and configuration information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b509-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9b509-112">In This Section</span></span>  
  
-   [<span data-ttu-id="9b509-113">Comment exporter une Application BizTalk</span><span class="sxs-lookup"><span data-stu-id="9b509-113">How to Export a BizTalk Application</span></span>](../core/how-to-export-a-biztalk-application.md)  
  
-   [<span data-ttu-id="9b509-114">L’exportation des liaisons</span><span class="sxs-lookup"><span data-stu-id="9b509-114">Exporting Bindings</span></span>](../core/exporting-bindings6.md)  
  
-   [<span data-ttu-id="9b509-115">Comment exporter une stratégie</span><span class="sxs-lookup"><span data-stu-id="9b509-115">How to Export a Policy</span></span>](../core/how-to-export-a-policy.md)