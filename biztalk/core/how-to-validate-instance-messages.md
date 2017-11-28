---
title: "Comment valider les Messages d’Instance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f6302c6-b56b-4572-aa76-0f4c4599672a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd0baa898f801c924cffc5a446aa1a22d063a8fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-validate-instance-messages"></a><span data-ttu-id="e4426-102">Comment valider les Messages d’Instance</span><span class="sxs-lookup"><span data-stu-id="e4426-102">How to Validate Instance Messages</span></span>
<span data-ttu-id="e4426-103">Après avoir construit un schéma, vous pouvez vérifier votre travail en validant, en fonction de ce schéma, un message d'instance préexistant constituant de source sûre un bon exemple des messages d'instance de ce type.</span><span class="sxs-lookup"><span data-stu-id="e4426-103">After you have constructed a schema, you can check your work by validating a pre-existing instance message that you know is a good representation of such instance messages against the schema.</span></span>  
  
 <span data-ttu-id="e4426-104">Cette rubrique contient des instructions détaillées concernant cette tâche de validation.</span><span class="sxs-lookup"><span data-stu-id="e4426-104">This topic provides step-by-step instructions for this validation task.</span></span>  
  
### <a name="to-validate-an-instance-message-against-a-schema"></a><span data-ttu-id="e4426-105">Pour valider un message d'instance en fonction d'un schéma</span><span class="sxs-lookup"><span data-stu-id="e4426-105">To validate an instance message against a schema</span></span>  
  
1.  <span data-ttu-id="e4426-106">Dans l’Explorateur de solutions, cliquez sur le schéma, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e4426-106">In Solution Explorer, right-click the schema, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="e4426-107">Si nécessaire, dans la fenêtre Propriétés, développez le **général** section de la **général** en cliquant sur son signe plus (+) icône.</span><span class="sxs-lookup"><span data-stu-id="e4426-107">If necessary, in the Properties window, expand the **General** section of the **General** tab by clicking its plus (+) icon.</span></span>  
  
3.  <span data-ttu-id="e4426-108">Dans le **nom d’Instance d’entrée** champ de valeur de propriété, tapez le nom d’un fichier ou utilisez le bouton de sélection (**...** ) situé à l’extrémité droite du champ de valeur pour accéder à un fichier qui contient le message d’instance à valider par rapport au schéma, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="e4426-108">In the **Input Instance Filename** property value field, either type the name of a file or use the ellipsis (**...**) button at the right end of the value field to browse for a file that contains the instance message to be validated against the schema, and then click **Open**.</span></span>  
  
4.  <span data-ttu-id="e4426-109">Dans **l’Explorateur de solutions**, cliquez sur le nom de schéma, puis cliquez sur **valider l’Instance**.</span><span class="sxs-lookup"><span data-stu-id="e4426-109">In **Solution Explorer**, right-click the schema name, and then click **Validate Instance**.</span></span>  
  
5.  <span data-ttu-id="e4426-110">Dans la fenêtre Sortie, affichez les résultats.</span><span class="sxs-lookup"><span data-stu-id="e4426-110">In the Output window, view the results.</span></span> <span data-ttu-id="e4426-111">Les messages de réussite et d'erreur sont affichés dans cette fenêtre.</span><span class="sxs-lookup"><span data-stu-id="e4426-111">Success and error messages are displayed in this window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4426-112">Dans certains cas, les messages d'instance générés à partir d'un schéma particulier ne peuvent être validés en fonction de ce même schéma.</span><span class="sxs-lookup"><span data-stu-id="e4426-112">There are some cases instance messages generated from a particular schema may not pass validation with that same schema.</span></span> <span data-ttu-id="e4426-113">Pour plus d’informations sur ces cas, consultez [problèmes connus avec la Validation et génération de schéma](../core/known-issues-with-schema-generation-and-validation.md).</span><span class="sxs-lookup"><span data-stu-id="e4426-113">For more information about such cases, see [Known Issues with Schema Generation and Validation](../core/known-issues-with-schema-generation-and-validation.md).</span></span> <span data-ttu-id="e4426-114">Généralement, vous souhaiterez modifier un message d'instance généré et modifier les données qu'il contient de sorte qu'il représente votre scénario de façon plus réaliste.</span><span class="sxs-lookup"><span data-stu-id="e4426-114">Generally, you will want to edit a generated instance message and change the data it contains so that it more realistically represents your scenario.</span></span> <span data-ttu-id="e4426-115">Utilisez ensuite ce message d'instance modifié pour valider votre schéma.</span><span class="sxs-lookup"><span data-stu-id="e4426-115">Then use this modified instance message to validate your schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4426-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4426-116">See Also</span></span>  
 <span data-ttu-id="e4426-117">[Test de schémas](../core/testing-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="e4426-117">[Testing Schemas](../core/testing-schemas.md) </span></span>  
 <span data-ttu-id="e4426-118">[Validation de schéma](../core/schema-validation1.md) </span><span class="sxs-lookup"><span data-stu-id="e4426-118">[Schema Validation](../core/schema-validation1.md) </span></span>  
 [<span data-ttu-id="e4426-119">Validation et génération de Message d’instance</span><span class="sxs-lookup"><span data-stu-id="e4426-119">Instance Message Generation and Validation</span></span>](../core/instance-message-generation-and-validation.md)