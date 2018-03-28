---
title: L’enregistrement, renommage et fermeture des schémas | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65e15d9e-40ae-4850-9c13-88033cb3b3bb
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a295bacf263e3ecad9a9aa081fb0d5d3be2f635
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-save-rename-and-close-schemas"></a><span data-ttu-id="acb83-102">Enregistrement, renommage et fermeture des schémas</span><span class="sxs-lookup"><span data-stu-id="acb83-102">How to Save, Rename, and Close Schemas</span></span>
<span data-ttu-id="acb83-103">Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les schémas sont des fichiers de langage XSD (XML Schema Definition). Ils résident sur le système de fichiers avec l'extension .xsd.</span><span class="sxs-lookup"><span data-stu-id="acb83-103">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], schemas are XML Schema definition (XSD) language files and reside on the file system with .xsd extensions.</span></span> <span data-ttu-id="acb83-104">Lorsque vous utilisez l'Éditeur BizTalk pour développer des schémas, vous devez systématiquement enregistrer et fermer les fichiers de schéma et devez parfois les renommer.</span><span class="sxs-lookup"><span data-stu-id="acb83-104">When you use BizTalk Editor to develop schemas, you will routinely need to save and close schema files, and occasionally you may need to rename them.</span></span> <span data-ttu-id="acb83-105">Cette rubrique indique les étapes requises pour effectuer ces opérations de base.</span><span class="sxs-lookup"><span data-stu-id="acb83-105">This topic describes the steps required to perform these basic operations.</span></span>  
  
### <a name="to-save-a-schema"></a><span data-ttu-id="acb83-106">Pour enregistrer un schéma</span><span class="sxs-lookup"><span data-stu-id="acb83-106">To save a schema</span></span>  
  
1.  <span data-ttu-id="acb83-107">Si nécessaire, activez l'Éditeur BizTalk pour le schéma à enregistrer en cliquant sur l'onglet approprié en haut de la fenêtre d'édition principale dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="acb83-107">If necessary, activate BizTalk Editor for the schema to be saved by clicking the appropriate tab at the top of the main editing window in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="acb83-108">Sur le **fichier** menu, cliquez sur ** Enregistrer *\<nom de schéma\>***.</span><span class="sxs-lookup"><span data-stu-id="acb83-108">On the **File** menu, click **Save *\<Name of Schema\>***.</span></span>  
  
     <span data-ttu-id="acb83-109">Si le schéma comportait des modifications non enregistrées, son nom tel qu'il s'affiche dans l'onglet en haut de la fenêtre d'édition principale ne se terminera plus par un astérisque (\*). L'astérisque est en effet utilisé pour attirer l'attention sur des modifications non enregistrées.</span><span class="sxs-lookup"><span data-stu-id="acb83-109">If the schema had unsaved changes, its name as displayed on the tab at the top of the main editing window will no longer end with an asterisk (\*), which is used to indicate unsaved changes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="acb83-110">Vous pouvez enregistrer le schéma sous un nouveau nom en cliquant sur **enregistrer *\<nom de schéma\>* en tant que** sur la **fichier** menu.</span><span class="sxs-lookup"><span data-stu-id="acb83-110">You can save the schema under a new name by clicking **Save *\<Name of Schema\>* As** on the **File** menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="acb83-111">Vous pouvez enregistrer le schéma en tant que partie de l’enregistrement de tous les éléments modifiés dans le projet en cliquant sur **Enregistrer tout** sur la **fichier** menu.</span><span class="sxs-lookup"><span data-stu-id="acb83-111">You can save the schema as part of saving all changed items in the project by clicking **Save All** on the **File** menu.</span></span>  
  
#### <a name="to-rename-a-schema"></a><span data-ttu-id="acb83-112">Pour renommer un schéma</span><span class="sxs-lookup"><span data-stu-id="acb83-112">To rename a schema</span></span>  
  
1.  <span data-ttu-id="acb83-113">Dans l’Explorateur de solutions, cliquez sur le schéma que vous souhaitez renommer, puis cliquez sur **renommer**.</span><span class="sxs-lookup"><span data-stu-id="acb83-113">In Solution Explorer, right-click the schema that you want to rename, and then click **Rename**.</span></span>  
  
2.  <span data-ttu-id="acb83-114">Dans la zone d'édition qui apparaît à l'emplacement du schéma dans l'Explorateur de solutions, tapez le nouveau nom du schéma ou modifiez son nom actuel, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="acb83-114">In the editing box that appears in the location of the schema in Solution Explorer, type the new name for the schema, or alter its existing name, and then press ENTER.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="acb83-115">Vous pouvez également modifier le **nom de Type** du schéma lorsque vous renommez.</span><span class="sxs-lookup"><span data-stu-id="acb83-115">You may also want to change the **Type Name** of the schema when you rename.</span></span> <span data-ttu-id="acb83-116">Vous modifiez le **nom de Type** en sélectionnant le **schéma** dans l’Explorateur de solutions et entrer le nouveau nom dans la **nom de Type** dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="acb83-116">You change the **Type Name** by selecting the **schema** in the solution explorer and entering the new name in the **Type Name** in the Properties window.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="acb83-117">Ne renommez pas un schéma utilisé par un autre schéma.</span><span class="sxs-lookup"><span data-stu-id="acb83-117">You should not rename any schema that is being used by another schema.</span></span> <span data-ttu-id="acb83-118">Cela concerne les schémas inclus, importés ou redéfinis par d'autres schémas, ainsi que les schémas de propriété pour lesquels des promotions ont déjà été établies.</span><span class="sxs-lookup"><span data-stu-id="acb83-118">This includes schemas that have been included, imported, or redefined by other schemas, as well as property schemas for which promotions have already been established.</span></span> <span data-ttu-id="acb83-119">Si vous ne respectez pas cette règle, le schéma utilisé ne pourra pas retrouver le schéma renommé, car le nom qu'il contient ne sera plus exact.</span><span class="sxs-lookup"><span data-stu-id="acb83-119">If you do so, the schema that is being used will not be able to find the renamed schema because the name it contains will no longer be accurate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="acb83-120">Certains noms de fichiers de membre de projet tels que les fichiers de schéma peuvent provoquer des erreurs de compilation ultérieures en raison de conflits avec des noms réservés C#  et des noms de type et d'espace de noms .NET Framework (« Système » par exemple).</span><span class="sxs-lookup"><span data-stu-id="acb83-120">Certain name choices for project member files, such as schema files, can cause compilation errors later on due to conflicts with C# reserved words and.NET Framework type and namespace names (such as "System").</span></span> <span data-ttu-id="acb83-121">schema.xsd, XmlContent et RootNodes sont des exemples de schémas.</span><span class="sxs-lookup"><span data-stu-id="acb83-121">Examples for schemas include schema.xsd, XmlContent, and RootNodes.</span></span> <span data-ttu-id="acb83-122">C’est parce que le **nom de Type** propriété valeur par défaut est la partie de base (sans extension) de la **nom de fichier** propriété.</span><span class="sxs-lookup"><span data-stu-id="acb83-122">This is because the **Type Name** property defaults to the base (non-extension) portion of the **Filename** property.</span></span> <span data-ttu-id="acb83-123">Vous pouvez contourner ce type d’erreur de compilation en donnant explicitement la valeur de la **nom de Type** propriété à un élément qui n’est pas en conflit.</span><span class="sxs-lookup"><span data-stu-id="acb83-123">You can work around this type of compilation error by explicitly changing the value of the **Type Name** property to something that does not conflict.</span></span>  
  
#### <a name="to-close-a-schema"></a><span data-ttu-id="acb83-124">Pour fermer un schéma</span><span class="sxs-lookup"><span data-stu-id="acb83-124">To close a schema</span></span>  
  
1.  <span data-ttu-id="acb83-125">Si nécessaire, activez l'Éditeur BizTalk pour le schéma à fermer en cliquant sur l'onglet approprié en haut de la fenêtre d'édition principale dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="acb83-125">If necessary, activate BizTalk Editor for the schema to be closed by clicking the appropriate tab at the top of the main editing window in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="acb83-126">Dans le menu **Fichier** , cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="acb83-126">On the **File** menu, click **Close**.</span></span>  
  
     <span data-ttu-id="acb83-127">L'Éditeur BizTalk se ferme pour le schéma qui a été fermé.</span><span class="sxs-lookup"><span data-stu-id="acb83-127">BizTalk Editor closes for the schema that has been closed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acb83-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="acb83-128">See Also</span></span>  
 [<span data-ttu-id="acb83-129">Gestion des schémas dans des projets</span><span class="sxs-lookup"><span data-stu-id="acb83-129">Managing Schemas Within Projects</span></span>](../core/managing-schemas-within-projects.md)