---
title: "Implémentation de l’exemple | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd788fd3-b070-40d5-a3d3-ac8e5208cc47
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d2e07078f630852fc14bf8081a4bd1453a0dc7b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="implementing-the-sample"></a><span data-ttu-id="f88fa-102">Implémentation de l’exemple</span><span class="sxs-lookup"><span data-stu-id="f88fa-102">Implementing the Sample</span></span>
<span data-ttu-id="f88fa-103">Pour implémenter l’exemple, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f88fa-103">To implement the sample, proceed as follows:</span></span>  
  
1.  <span data-ttu-id="f88fa-104">Créer un nouveau dossier pour SWIFT schémas (\<DocumentSchemaLocation > dans la syntaxe de l’utilitaire).</span><span class="sxs-lookup"><span data-stu-id="f88fa-104">Create a new folder for SWIFT schemas (\<DocumentSchemaLocation> in the utility syntax).</span></span> <span data-ttu-id="f88fa-105">Tous les schémas pour lesquels vous allez créer/modifier des formulaires InfoPath doivent se trouver dans ce dossier lorsque vous exécutez l’utilitaire.</span><span class="sxs-lookup"><span data-stu-id="f88fa-105">All schemas for which you are going to create/modify the InfoPath forms must be located in this folder when you execute the utility.</span></span>  
  
2.  <span data-ttu-id="f88fa-106">Si vous générez des formulaires InfoPath pour les messages MT, copiez **SWIFT Base Types.xsd** et **Types.xsd de données courantes SWIFT** de  **\<lecteur : > \Program Files\Microsoft BizTalk Accelerator pour SWIFT \<Message Pack Version > Message Pack\SWIFT Messages\A4SWIFT-SRG\<Message Pack Version > \Base schémas** dans le dossier que vous avez créé pour les schémas SWIFT.</span><span class="sxs-lookup"><span data-stu-id="f88fa-106">If you are generating InfoPath forms for MT messages then copy **SWIFT Base Types.xsd** and **SWIFT Common Data Types.xsd** from **\<drive :> \Program Files\Microsoft BizTalk Accelerator for SWIFT \<Message Pack Version> Message Pack\SWIFT Messages\A4SWIFT-SRG\<Message Pack Version>\Base Schemas** into the folder that you created for SWIFT schemas.</span></span>  
  
3.  <span data-ttu-id="f88fa-107">Copie tous les schémas pour lesquels vous allez créer des formulaires InfoPath dans le dossier que vous avez créé pour les schémas SWIFT à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="f88fa-107">Copy all schemas for which you are going to create InfoPath forms into the folder that you created for SWIFT schemas in Step 1.</span></span>  
  
4.  <span data-ttu-id="f88fa-108">Créez ou désignez un dossier pour conserver le formulaire InfoPath créé les fichiers de solution de modèle (\<DestinationFolderPath > dans la syntaxe de l’utilitaire).</span><span class="sxs-lookup"><span data-stu-id="f88fa-108">Create or designate a folder to hold the created InfoPath form template solution files (\<DestinationFolderPath> in the utility syntax).</span></span> <span data-ttu-id="f88fa-109">Si vous ne créez pas le dossier de sortie, l’utilitaire créera le même chemin d’accès et le nom que vous passez sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="f88fa-109">If you do not create the output folder, the utility will create the same with path and name that you pass on the command line.</span></span>  
  
5.  <span data-ttu-id="f88fa-110">[Facultatif]-Créez un fichier texte \<NameOfFileContainingSchemaList > qui répertorie les types de messages pour les messages pour lesquels le formulaire InfoPath doit être généré.</span><span class="sxs-lookup"><span data-stu-id="f88fa-110">[Optional]-  Create a text file \<NameOfFileContainingSchemaList> that lists the message types for messages for which the InfoPath form is to be generated.</span></span> <span data-ttu-id="f88fa-111">Par exemple, Type de Message peut être MT103, etc. de MT102. Les noms de Message peuvent être transmis directement via la ligne de commande au lieu de créer ce fichier texte.</span><span class="sxs-lookup"><span data-stu-id="f88fa-111">For e.g. Message Type can be MT103, MT102 etc. The Message names can directly be passed through the command line instead of creating this text file.</span></span>  
  
## <a name="syntax-of-command-usage-for-formgeneratorexe"></a><span data-ttu-id="f88fa-112">Syntaxe d’utilisation de la commande pour FormGenerator.exe</span><span class="sxs-lookup"><span data-stu-id="f88fa-112">Syntax of Command usage for FormGenerator.exe</span></span>  
  
```csharp  
FormGenerator [-b]   [-#] <TemplateFolderPath> [<TemplateFolderPath2>   
   [...<TemplateFolderPath#>]]  
 <DestinationFolderPath>     <DocumentSchemaLocation>  
   { [<SpaceSeparatedDocumentSchemaList>] |   [-f <NameOfFileContainingSchemaList>] }  
  
```  
  
 <span data-ttu-id="f88fa-113">Où :</span><span class="sxs-lookup"><span data-stu-id="f88fa-113">Where:</span></span>  
  
-   <span data-ttu-id="f88fa-114">-b : s’il est spécifié, les formulaires seront compilés après sa création.</span><span class="sxs-lookup"><span data-stu-id="f88fa-114">-b: If specified, forms will be compiled after creation.</span></span>  
  
-   <span data-ttu-id="f88fa-115">TemplateFolderPath : le dossier contenant les fichiers de modèle utilisées pour créer la solution InfoPath</span><span class="sxs-lookup"><span data-stu-id="f88fa-115">TemplateFolderPath: the folder containing the template files used to create the InfoPath solution</span></span>  
  
-   <span data-ttu-id="f88fa-116">-#: Si spécifié, les modèles sont recherchées dans plusieurs chemins d’accès de modèle (autant que l’entier numéro # spécifie) et dans l’ordre spécifié.</span><span class="sxs-lookup"><span data-stu-id="f88fa-116">-#: If specified, templates will be looked up in multiple template paths (as many as the integer number # specifies) and in the order specified.</span></span>  
  
-   <span data-ttu-id="f88fa-117">DestinationFolderPath : le dossier où les formulaires doivent être créés</span><span class="sxs-lookup"><span data-stu-id="f88fa-117">DestinationFolderPath: the folder where the forms will be created</span></span>  
  
-   <span data-ttu-id="f88fa-118">DocumentSchemaLocation : emplacement des schémas (y compris les schémas de base et courantes pour les messages du serveur cible maître)</span><span class="sxs-lookup"><span data-stu-id="f88fa-118">DocumentSchemaLocation: location of schemas (including base and common schemas for MT messages)</span></span>  
  
-   <span data-ttu-id="f88fa-119">SpaceSeparatedDocumentSchemaList : liste séparée par des espaces de schémas comme MT103 MT300.</span><span class="sxs-lookup"><span data-stu-id="f88fa-119">SpaceSeparatedDocumentSchemaList: space-separated list of schemas like MT103 MT300.</span></span>  
  
-   <span data-ttu-id="f88fa-120">-f: si spécifié, la liste de schéma doit être lue à partir d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="f88fa-120">-f: If specified, the schema list needs to be read from a file.</span></span>  
  
-   <span data-ttu-id="f88fa-121">NameOfFileContainingSchemaList : le nom du fichier contenant la liste.</span><span class="sxs-lookup"><span data-stu-id="f88fa-121">NameOfFileContainingSchemaList: name of file containing the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f88fa-122">La commande ci-dessus est une commande générique pour la catégorie 0, ce dernier et MX messages.</span><span class="sxs-lookup"><span data-stu-id="f88fa-122">The above command is a generic command for MT, MX and Category 0 messages.</span></span> <span data-ttu-id="f88fa-123">Les commandes spécifiques pour générer ces types de formulaires figurent dans le dessous des sections.</span><span class="sxs-lookup"><span data-stu-id="f88fa-123">Specific commands to generate these types of forms are given in the below sections.</span></span>