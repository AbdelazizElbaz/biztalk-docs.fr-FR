---
title: "Comment créer des schémas de propriété | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24086dea-62b8-4ef6-8af8-eb4ab7c3c018
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee97f4cb3065fdb201ec19f88a79e7899f03ac49
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-create-property-schemas"></a><span data-ttu-id="59e16-102">Comment créer des schémas de propriété</span><span class="sxs-lookup"><span data-stu-id="59e16-102">How to Create Property Schemas</span></span>
<span data-ttu-id="59e16-103">Si vous choisissez de promouvoir des champs en tant que champs de propriété, vous devez d'abord définir un schéma de propriété.</span><span class="sxs-lookup"><span data-stu-id="59e16-103">If you choose to promote fields as property fields, you will need to define a property schema first.</span></span> <span data-ttu-id="59e16-104">Ce schéma de propriété spécifie un ensemble de champs non structuré dans lequel vous pouvez promouvoir des champs depuis un message d'instance défini par un schéma associé à votre schéma.</span><span class="sxs-lookup"><span data-stu-id="59e16-104">This property schema specifies an unstructured collection of fields into which you can promote fields from within an instance message defined by a schema associated with your property schema.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="59e16-105">Vous ne devez ni copier ni modifier un schéma de propriété existant pour créer un schéma.</span><span class="sxs-lookup"><span data-stu-id="59e16-105">Do not copy and edit an existing property schema to create a new schema.</span></span> <span data-ttu-id="59e16-106">Le schéma de propriété contient des données internes propres au schéma.</span><span class="sxs-lookup"><span data-stu-id="59e16-106">The property schema contains schema-specific internal data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59e16-107">Il n'est pas nécessaire de créer un schéma de propriété pour promouvoir des champs distinctifs.</span><span class="sxs-lookup"><span data-stu-id="59e16-107">You do not need to create a property schema to promote distinguished fields.</span></span>  
  
### <a name="to-create-a-property-schema"></a><span data-ttu-id="59e16-108">Pour créer un schéma de propriété</span><span class="sxs-lookup"><span data-stu-id="59e16-108">To create a property schema</span></span>  
  
1.  <span data-ttu-id="59e16-109">Dans **l’Explorateur de solutions**, avec le bouton droit à un projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="59e16-109">In **Solution Explorer**, right-click a BizTalk project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="59e16-110">Dans le **ajouter un nouvel élément** boîte de dialogue le **modèles** , cliquez sur **schéma de propriété**.</span><span class="sxs-lookup"><span data-stu-id="59e16-110">In the **Add New Item** dialog box, in the **Templates** section, click **Property Schema**.</span></span>  
  
3.  <span data-ttu-id="59e16-111">Dans le **nom** zone, tapez un nom pour le schéma, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="59e16-111">In the **Name** box, type a name for the schema, and then click **Add**.</span></span>  
  
     <span data-ttu-id="59e16-112">Le nouveau schéma de propriété s’ouvre, et il contient déjà un **élément de champ** nœud nommé Property1.</span><span class="sxs-lookup"><span data-stu-id="59e16-112">The new property schema opens, and it already contains a **Field Element** node named Property1.</span></span>  
  
4.  <span data-ttu-id="59e16-113">Dans l’arborescence du schéma, avec le bouton droit qui **Fieldelement** nœud, cliquez sur **renommer**, tapez un nom descriptif pour la première propriété dans le schéma, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="59e16-113">In the schema tree, right-click that **Field Element** node, click **Rename**, type a descriptive name for the first property in the schema, and then press ENTER.</span></span>  
  
5.  <span data-ttu-id="59e16-114">Définir le **Type de données** et d’autres propriétés pertinentes, comme il convient pour le **élément de champ** nœud dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="59e16-114">Set the **Data Type** and other relevant properties, as appropriate, for the **Field Element** node in the Properties window.</span></span>  
  
6.  <span data-ttu-id="59e16-115">Si vous souhaitez insérer **Fieldelement** nœuds pour les propriétés supplémentaires, cliquez sur le \<schéma\> nœud, cliquez sur **insérer un nœud de schéma**, puis cliquez sur  **Élément de champ enfant**, puis répétez les étapes 4 et 5.</span><span class="sxs-lookup"><span data-stu-id="59e16-115">If you want to insert **Field Element** nodes for additional properties, right-click the \<Schema\> node, click **Insert Schema Node**, and then click **Child Field Element**, and then repeat steps 4 and 5.</span></span> <span data-ttu-id="59e16-116">Répétez l’opération pour créer l’ensemble de **élément de champ** nœuds dans lequel vous avez l’intention de promouvoir les valeurs à partir des messages d’instance.</span><span class="sxs-lookup"><span data-stu-id="59e16-116">Repeat as necessary to create the required set of **Field Element** nodes into which you intend to promote values from instance messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59e16-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59e16-117">See Also</span></span>  
 [<span data-ttu-id="59e16-118">Gestion des schémas dans des projets</span><span class="sxs-lookup"><span data-stu-id="59e16-118">Managing Schemas Within Projects</span></span>](../core/managing-schemas-within-projects.md)