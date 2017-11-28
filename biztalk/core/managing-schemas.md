---
title: "Gérer des schémas | Documents Microsoft"
description: "Utiliser l’Administration de BizTalk pour utiliser des schémas dans BizTalk Server, y compris l’affichage et masquage des propriétés, afficher le langage XSD, activer le suivi"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5632e79-b182-41c9-9138-eb88b44e3172
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0d7fe3eee97cf81c668ffe90fd9c0897af23cc1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-schemas"></a><span data-ttu-id="ebec5-103">Gérer des schémas</span><span class="sxs-lookup"><span data-stu-id="ebec5-103">Manage Schemas</span></span>

## <a name="overiew"></a><span data-ttu-id="ebec5-104">Présentation</span><span class="sxs-lookup"><span data-stu-id="ebec5-104">Overiew</span></span>
<span data-ttu-id="ebec5-105">Cette section fournit des instructions sur la gestion des orchestrations à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ebec5-105">This section provides instructions on using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to manage schemas.</span></span> <span data-ttu-id="ebec5-106">Les schémas sont utilisés par les pipelines et les orchestrations pour représenter le message qui sera traité.</span><span class="sxs-lookup"><span data-stu-id="ebec5-106">Schemas are used by pipelines and orchestrations to represent the message that will be processed.</span></span>  
  
 <span data-ttu-id="ebec5-107">Ils sont créés dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et compilés dans les assemblys BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ebec5-107">Schemas are created in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and compiled into BizTalk assemblies.</span></span> <span data-ttu-id="ebec5-108">Vous ne pouvez pas ajouter un schéma de manière individuelle à une application. L'ajout s'effectue dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="ebec5-108">You cannot add a schema to an application individually; a schema is added to an application as follows:</span></span>  
  
-   <span data-ttu-id="ebec5-109">Lorsque vous ajoutez un assembly BizTalk contenant un schéma à l’application, comme décrit dans [l’ajout d’un BizTalk Assembly à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="ebec5-109">When you add a BizTalk assembly containing a schema to the application, as described in [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span></span>  
  
-   <span data-ttu-id="ebec5-110">Lorsque vous importez un fichier .msi dans une application qui comprend un assembly BizTalk contenant un schéma, comme décrit dans [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="ebec5-110">When you import an .msi file into an application that includes a BizTalk assembly containing a schema, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).</span></span>  
  
-   <span data-ttu-id="ebec5-111">Lorsqu’un développeur déploie dans une application d’un assembly contenant un schéma à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], comme décrit dans [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="ebec5-111">When a developer deploys into an application an assembly containing a schema from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], as described in [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span></span>  
  
 <span data-ttu-id="ebec5-112">Pour des informations générales sur les schémas, consultez [schémas](../core/schemas.md).</span><span class="sxs-lookup"><span data-stu-id="ebec5-112">For background information about schemas, see [Schemas](../core/schemas.md).</span></span> <span data-ttu-id="ebec5-113">Pour plus d’informations sur le développement des schémas, consultez [création de schémas à l’aide de l’Éditeur BizTalk](../core/creating-schemas-using-biztalk-editor.md).</span><span class="sxs-lookup"><span data-stu-id="ebec5-113">For information about developing schemas, see [Creating Schemas Using BizTalk Editor](../core/creating-schemas-using-biztalk-editor.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebec5-114">Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives.</span><span class="sxs-lookup"><span data-stu-id="ebec5-114">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="ebec5-115">Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="ebec5-115">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="ebec5-116">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ebec5-116">Next steps</span></span> 
  
-   [<span data-ttu-id="ebec5-117">Afficher et masquer les schémas de propriété</span><span class="sxs-lookup"><span data-stu-id="ebec5-117">Show and Hide Property Schemas</span></span>](../core/how-to-show-and-hide-property-schemas.md)  
  
-   [<span data-ttu-id="ebec5-118">Afficher la définition de schéma (XSD) d’un schéma</span><span class="sxs-lookup"><span data-stu-id="ebec5-118">View the Schema Definition (XSD) of a Schema</span></span>](../core/how-to-view-the-schema-definition-xsd-of-a-schema.md)  
  
-   [<span data-ttu-id="ebec5-119">Configurer le suivi d’un schéma</span><span class="sxs-lookup"><span data-stu-id="ebec5-119">Configure Tracking for a Schema</span></span>](../core/how-to-configure-tracking-for-a-schema.md)  
  
-   [<span data-ttu-id="ebec5-120">Supprimer un schéma à partir d’une Application</span><span class="sxs-lookup"><span data-stu-id="ebec5-120">Remove a Schema from an Application</span></span>](../core/how-to-remove-a-schema-from-an-application.md)