---
title: "Génération d’instance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14060dca-5e14-474a-bf2c-4e8bc56e3c61
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46bd3d2bc6852ec0c73fbbe4ffc55924a8012ce5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="instance-generation"></a><span data-ttu-id="fa888-102">Génération d’instance</span><span class="sxs-lookup"><span data-stu-id="fa888-102">Instance Generation</span></span>
<span data-ttu-id="fa888-103">L’Éditeur BizTalk appelle la **IInstanceGenerator.GenerateInstance** méthode d’extension lorsque les conditions suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="fa888-103">BizTalk Editor invokes the **IInstanceGenerator.GenerateInstance** method of an extension when the following conditions are met:</span></span>  
  
-   <span data-ttu-id="fa888-104">L’extension est définie comme norme à l’aide de la **Standard** propriété de la **schéma** nœud.</span><span class="sxs-lookup"><span data-stu-id="fa888-104">The extension is set as standard by using the **Standard** property of the **Schema** node.</span></span>  
  
-   <span data-ttu-id="fa888-105">Sur le **Pages de propriétés** boîte de dialogue associé au schéma, le **Type sortie générer l’Instance** est définie sur **natif.**</span><span class="sxs-lookup"><span data-stu-id="fa888-105">On the **Property Pages** dialog box associated with the schema, the **Generate Instance Output Type** property is set to **Native.**</span></span>  
  
-   <span data-ttu-id="fa888-106">Sur le **Pages de propriétés** boîte de dialogue associé au schéma, le **nom de fichier de sortie Instance** est définie sur le nom du fichier qui sera enregistré dans l’instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="fa888-106">On the **Property Pages** dialog box associated with the schema, the **Output Instance Filename** property is set to the name of the file that the output instance will be saved to.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa888-107">Si le **nom de fichier de sortie Instance** propriété n’est pas définie, un nom de fichier par défaut dans un dossier temporaire est utilisé pour le message d’instance généré et un lien vers celle-ci est fourni dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="fa888-107">If the **Output Instance Filename** property is not set, a default file name in a temporary folder is used for the generated instance message, and a link to it is provided in the Output window.</span></span>  
  
 <span data-ttu-id="fa888-108">Avant du **IInstanceValidator.ValidateInstance** méthode est appelée, l’Éditeur BizTalk génère un message d’instance XML exemple et elle passe ensuite et le fichier spécifié dans le **nom de fichier de sortie Instance** propriété ou un nom de fichier par défaut à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="fa888-108">Before the **IInstanceValidator.ValidateInstance** method is called, BizTalk Editor generates a sample XML instance message, and then passes it and the file specified in the **Output Instance Filename** property, or a default file name, to that method.</span></span>  
  
 <span data-ttu-id="fa888-109">En cas d’erreurs, les messages d’erreur sont retournées sous forme de tableau de **IValidationInfo** objets et s’affichent dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre liste des tâches.</span><span class="sxs-lookup"><span data-stu-id="fa888-109">If errors occur, error messages are returned as an array of **IValidationInfo** objects, and are displayed in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Task List window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa888-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa888-110">See Also</span></span>  
 [<span data-ttu-id="fa888-111">Extension de l’Éditeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="fa888-111">Extending BizTalk Editor</span></span>](../core/extending-biztalk-editor.md)