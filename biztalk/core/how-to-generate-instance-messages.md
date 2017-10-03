---
title: "Comment générer des Messages d’Instance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff74c67a-7e73-4153-9ec4-e6e50464ee92
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a911e4b0f1167e8ec200dad65b8dacb94bb08be3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-generate-instance-messages"></a><span data-ttu-id="8ffb8-102">Comment générer des Messages d’Instance</span><span class="sxs-lookup"><span data-stu-id="8ffb8-102">How to Generate Instance Messages</span></span>
<span data-ttu-id="8ffb8-103">Une fois que vous avez construit un schéma, une manière de vérifier votre travail consiste à générer un exemple de message d'instance à partir de ce schéma.</span><span class="sxs-lookup"><span data-stu-id="8ffb8-103">After you have constructed a schema, one way to check your work is to generate a sample instance message from the schema.</span></span> <span data-ttu-id="8ffb8-104">À bien des égards, il est bien plus facile d'examiner un message d'instance plutôt que l'arborescence de schéma ou la représentation de langage XSD (XML Schema Definition) du schéma.</span><span class="sxs-lookup"><span data-stu-id="8ffb8-104">In many ways, looking at an instance message is much more straightforward than looking at either the schema tree or the XML Schema definition (XSD) language representation of the schema.</span></span> <span data-ttu-id="8ffb8-105">En effet, un schéma doit représenter toutes les variations possibles des messages d'instance correspondants tandis qu'un message d'instance spécifique se borne à fournir certaines données à l'aide du format spécifié par le schéma.</span><span class="sxs-lookup"><span data-stu-id="8ffb8-105">This is because the schema needs to describe all of the possible variations of the corresponding instance messages, and a specific instance message just needs to convey some data by using the format specified by the schema.</span></span> <span data-ttu-id="8ffb8-106">Le message d'instance généré est un exemple et est susceptible de ne pas contenir toutes les structures définies par le schéma correspondant.</span><span class="sxs-lookup"><span data-stu-id="8ffb8-106">The generated instance message is a sample and may not show all of the structures defined by the corresponding schema.</span></span>  
  
### <a name="to-explicitly-specify-a-file-to-contain-the-generated-instance-message"></a><span data-ttu-id="8ffb8-107">Pour imposer explicitement à un fichier de contenir le message d'instance généré</span><span class="sxs-lookup"><span data-stu-id="8ffb8-107">To explicitly specify a file to contain the generated instance message</span></span>  
  
1.  <span data-ttu-id="8ffb8-108">Dans l’Explorateur de solutions, cliquez sur le schéma pour lequel vous souhaitez générer un message d’instance, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="8ffb8-108">In Solution Explorer, right-click the schema for which you want to generate an instance message, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="8ffb8-109">Si nécessaire, dans la fenêtre Propriétés, développez le **général** section de la **général** en cliquant sur son signe plus (+) icône.</span><span class="sxs-lookup"><span data-stu-id="8ffb8-109">If necessary, in the Properties window, expand the **General** section of the **General** tab by clicking its plus (+) icon.</span></span>  
  
3.  <span data-ttu-id="8ffb8-110">Dans le **nom de fichier de sortie Instance** champ de valeur de propriété, tapez le nom d’un fichier ou utilisez le bouton de sélection (**...** ) situé à l’extrémité droite du champ de valeur à rechercher un fichier dans lequel seront placés les messages d’instance généré, puis cliquez **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="8ffb8-110">In the **Output Instance Filename** property value field, either type the name of a file or use the ellipsis (**...**) button at the right end of the value field to browse for a file into which generated instance messages will be placed, and then click **Save**.</span></span>  
  
### <a name="to-specify-the-type-of-the-generated-instance-message"></a><span data-ttu-id="8ffb8-111">Pour spécifier le type du message d'instance généré</span><span class="sxs-lookup"><span data-stu-id="8ffb8-111">To specify the type of the generated instance message</span></span>  
  
1.  <span data-ttu-id="8ffb8-112">Dans l’Explorateur de solutions, cliquez sur le schéma pour lequel vous souhaitez générer un message d’instance, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="8ffb8-112">In Solution Explorer, right-click the schema for which you want to generate an instance message, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="8ffb8-113">Si nécessaire, dans la fenêtre Propriétés, développez le **général** section de la **général** en cliquant sur son signe plus (+) icône.</span><span class="sxs-lookup"><span data-stu-id="8ffb8-113">If necessary, in the Properties window, expand the **General** section of the **General** tab by clicking its plus (+) icon.</span></span>  
  
3.  <span data-ttu-id="8ffb8-114">Dans le **Type sortie générer l’Instance** champ de valeur de propriété, utilisez la liste déroulante de liste pour sélectionner **XML** ou **natif** en tant que le type du message d’instance à générer.</span><span class="sxs-lookup"><span data-stu-id="8ffb8-114">In the **Generate Instance Output Type** property value field, use the drop-down list to select either **XML** or **Native** as the type of the instance message to be generated.</span></span>  
  
     <span data-ttu-id="8ffb8-115">**XML** est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="8ffb8-115">**XML** is the default value.</span></span>  
  
### <a name="to-generate-a-sample-instance-message-for-a-schema"></a><span data-ttu-id="8ffb8-116">Pour générer un exemple de message d'instance pour un schéma</span><span class="sxs-lookup"><span data-stu-id="8ffb8-116">To generate a sample instance message for a schema</span></span>  
  
1.  <span data-ttu-id="8ffb8-117">Dans l’Explorateur de solutions, cliquez sur le schéma pour lequel vous souhaitez générer un message d’instance, puis cliquez sur **générer l’Instance**.</span><span class="sxs-lookup"><span data-stu-id="8ffb8-117">In Solution Explorer, right-click the schema for which you want to generate an instance message, and then click **Generate Instance**.</span></span>  
  
2.  <span data-ttu-id="8ffb8-118">Dans la fenêtre Sortie, affichez les résultats.</span><span class="sxs-lookup"><span data-stu-id="8ffb8-118">In the Output window, view the results.</span></span> <span data-ttu-id="8ffb8-119">Les messages de réussite et d'erreur sont affichés dans cette fenêtre.</span><span class="sxs-lookup"><span data-stu-id="8ffb8-119">Success and error messages are displayed in this window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ffb8-120">Si la fenêtre Sortie et/ou la fenêtre Liste des tâches ne se sont pas ouvertes pour indiquer si la génération de l'instance a réussi ou échoué, vous pouvez les ouvrir manuellement.</span><span class="sxs-lookup"><span data-stu-id="8ffb8-120">If the Output window and/or the Task List window did not open and display information about whether the instance generation succeeded or failed, you can open them manually.</span></span> <span data-ttu-id="8ffb8-121">Pour plus d’informations sur la gestion de ces fenêtres, consultez [la gestion des autres fenêtres Visual Studio](../core/how-to-manage-other-visual-studio-windows.md).</span><span class="sxs-lookup"><span data-stu-id="8ffb8-121">For more information about managing these windows, see [Managing Other Visual Studio Windows](../core/how-to-manage-other-visual-studio-windows.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ffb8-122">Si vous ne spécifiez pas une valeur pour le **référence de racine** propriété, l’Éditeur BizTalk génère un exemple de message d’instance pour le premier nœud racine dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="8ffb8-122">If you do not specify a value for the **Root Reference** property, BizTalk Editor generates a sample instance message for the first root node in the schema.</span></span> <span data-ttu-id="8ffb8-123">Si vous spécifiez une valeur pour le **référence de racine** propriété, l’Éditeur BizTalk génère un exemple de message d’instance pour cette racine.</span><span class="sxs-lookup"><span data-stu-id="8ffb8-123">If you specify a value for the **Root Reference** property, BizTalk Editor generates a sample instance message for that root.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ffb8-124">Dans certains cas, les messages d'instance générés à partir d'un schéma particulier ne peuvent être validés en fonction de ce même schéma.</span><span class="sxs-lookup"><span data-stu-id="8ffb8-124">There are some cases instance messages generated from a particular schema may not pass validation with that same schema.</span></span> <span data-ttu-id="8ffb8-125">Pour plus d’informations sur ces cas, consultez [problèmes connus avec la Validation et génération de schéma](../core/known-issues-with-schema-generation-and-validation.md).</span><span class="sxs-lookup"><span data-stu-id="8ffb8-125">For more information about such cases, see [Known Issues with Schema Generation and Validation](../core/known-issues-with-schema-generation-and-validation.md).</span></span> <span data-ttu-id="8ffb8-126">En règle générale, vous souhaitez modifier un message d’instance généré et modifier les données qu’il contient afin qu’il représente de façon plus réaliste votre scénario.</span><span class="sxs-lookup"><span data-stu-id="8ffb8-126">Generally, you want to edit a generated instance message and change the data it contains so that it more realistically represents your scenario.</span></span> <span data-ttu-id="8ffb8-127">Utilisez ensuite ce message d'instance modifié pour valider votre schéma.</span><span class="sxs-lookup"><span data-stu-id="8ffb8-127">Then use this modified instance message to validate your schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ffb8-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ffb8-128">See Also</span></span>  
 <span data-ttu-id="8ffb8-129">[Test de schémas](../core/testing-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="8ffb8-129">[Testing Schemas](../core/testing-schemas.md) </span></span>  
 <span data-ttu-id="8ffb8-130">[Validation de schéma](../core/schema-validation1.md) </span><span class="sxs-lookup"><span data-stu-id="8ffb8-130">[Schema Validation](../core/schema-validation1.md) </span></span>  
 [<span data-ttu-id="8ffb8-131">Validation et génération de Message d’instance</span><span class="sxs-lookup"><span data-stu-id="8ffb8-131">Instance Message Generation and Validation</span></span>](../core/instance-message-generation-and-validation.md)