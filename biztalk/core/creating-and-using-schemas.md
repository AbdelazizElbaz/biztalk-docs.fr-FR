---
title: "Créer et utiliser des schémas dans TIBCO | Documents Microsoft"
description: "Utiliser l’Éditeur BizTalk pour créer un schéma pour l’adaptateur BizTalk pour TIBCO Enterprise Message Service et définir l’espace de noms cible dans votre schéma pour BizTalk Server"
ms.custom: 
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3927b0b3-db3b-4494-b003-d930af734e58
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 384d140832c123f46ecf531e64b3c1ca11e64f4e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="create-and-use-tibco-schemas"></a><span data-ttu-id="0274a-103">Créer et utiliser des schémas TIBCO</span><span class="sxs-lookup"><span data-stu-id="0274a-103">Create and use TIBCO schemas</span></span>

## <a name="overview"></a><span data-ttu-id="0274a-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="0274a-104">Overview</span></span>
<span data-ttu-id="0274a-105">L'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service (EMS) utilise les schémas que vous créez à l'aide d'un éditeur XML ou de l'Éditeur BizTalk Server dans Visual Studio (uniquement lorsque l'adaptateur est utilisé dans une orchestration).</span><span class="sxs-lookup"><span data-stu-id="0274a-105">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) uses schemas that you create using an XML editor or the BizTalk Server Editor in Visual Studio (only when you use the adapter in an orchestration).</span></span> <span data-ttu-id="0274a-106">Le schéma décrit le type d'informations attendu.</span><span class="sxs-lookup"><span data-stu-id="0274a-106">The schema describes the type of information that you expect.</span></span> <span data-ttu-id="0274a-107">Cette rubrique contient des informations relatives aux gestionnaires d'envoi et de réception.</span><span class="sxs-lookup"><span data-stu-id="0274a-107">This topic contains information for both a send and a receive handler.</span></span>  
  
<span data-ttu-id="0274a-108">Les schémas que vous créez pour être utilisés avec l'adaptateur BizTalk pour TIBCO Enterprise Message Service doivent inclure un espace de noms cible.</span><span class="sxs-lookup"><span data-stu-id="0274a-108">The schemas you create for use with BizTalk Adapter for TIBCO Enterprise Message Service must have a target namespace.</span></span> <span data-ttu-id="0274a-109">Celui-ci est nécessaire car il est la clé qui associe une instance de message donnée à une orchestration donnée.</span><span class="sxs-lookup"><span data-stu-id="0274a-109">BizTalk Server requires the target namespace because it is the key that associates a given message instance with a given orchestration.</span></span> <span data-ttu-id="0274a-110">En d'autres termes, une orchestration s'abonne aux messages associés à un espace de noms cible spécifique et un message XML entrant associé à cet espace de noms cible est transmis à chaque orchestration abonnée au message.</span><span class="sxs-lookup"><span data-stu-id="0274a-110">In other words, an orchestration subscribes to any message that has a specific target namespace, and an incoming XML message that has that target namespace is given to every orchestration that subscribed to the message.</span></span> <span data-ttu-id="0274a-111">Si un schéma de document XML n'inclut pas d'espace de noms cible, BizTalk Server utilise le nom de l'élément racine comme clé.</span><span class="sxs-lookup"><span data-stu-id="0274a-111">If an XML document schema does not have a target namespace, BizTalk Server uses the name of the root element as a key.</span></span>  

<span data-ttu-id="0274a-112">Les étapes suivantes montrent comment générer un schéma et comment définir l’espace de noms cible.</span><span class="sxs-lookup"><span data-stu-id="0274a-112">The following steps show how to generate a schema, and how to set the target namespace.</span></span>  
  
## <a name="generate-a-schema"></a><span data-ttu-id="0274a-113">Générer un schéma</span><span class="sxs-lookup"><span data-stu-id="0274a-113">Generate a Schema</span></span>    
 
1.  <span data-ttu-id="0274a-114">Dans l'Éditeur BizTalk, ouvrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="0274a-114">In the BizTalk Editor, open your project.</span></span>  
  
2.  <span data-ttu-id="0274a-115">Dans l’Explorateur de solutions dans l’angle supérieur droit, sélectionnez **ajouter**, puis sélectionnez **ajouter les éléments générés**.</span><span class="sxs-lookup"><span data-stu-id="0274a-115">Under Solution Explorer in the upper-right, select **Add**, and then select **Add Generated Items**.</span></span>  
  
3.  <span data-ttu-id="0274a-116">Dans le **modèles** volet, sélectionnez **générer les schémas**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="0274a-116">In the **Templates** pane, select **Generate Schemas**, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="0274a-117">Dans le **générer les schémas** boîte de dialogue le **type de Document** liste, sélectionnez **XML bien formé**.</span><span class="sxs-lookup"><span data-stu-id="0274a-117">In the **Generate Schemas** dialog box, in the **Document type** list, select **Well-Formed XML**.</span></span>  
  
5.  <span data-ttu-id="0274a-118">Cliquez sur **Parcourir** pour localiser le fichier d’entrée pour laquelle vous souhaitez générer un schéma, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0274a-118">Click **Browse** to locate the input file for which you want to generate a schema, and then click **OK**.</span></span>  
  
<span data-ttu-id="0274a-119">Ensuite, affectez à l’espace de noms cible.</span><span class="sxs-lookup"><span data-stu-id="0274a-119">Next, set the target namespace.</span></span>  
  
## <a name="set-the-target-namespace"></a><span data-ttu-id="0274a-120">L’espace de noms cible</span><span class="sxs-lookup"><span data-stu-id="0274a-120">Set the target namespace</span></span>  
  
1.  <span data-ttu-id="0274a-121">Dans l’Éditeur BizTalk, ouvrez votre fichier de schéma, cliquez sur  **\<schéma\>**, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="0274a-121">In BizTalk Editor, open your schema file, right-click **\<schema\>**, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="0274a-122">Dans le **propriétés** volet, recherchez le **Namespace** champ et tapez un nom, par exemple, `testNameSpace`.</span><span class="sxs-lookup"><span data-stu-id="0274a-122">In the **Properties** pane, locate the **Namespace** field and type a name, for example, `testNameSpace`.</span></span>  
  
 <span data-ttu-id="0274a-123">Vous pouvez ensuite continuer à utiliser votre orchestration avec des messages.</span><span class="sxs-lookup"><span data-stu-id="0274a-123">You can then continue with your orchestration using messages.</span></span> <span data-ttu-id="0274a-124">Lorsqu'un message est récupéré, BizTalk Server recherche une orchestration qui utilise un schéma avec un espace de noms cible défini, et le processus d'orchestration suit son cours.</span><span class="sxs-lookup"><span data-stu-id="0274a-124">When a message is picked up, BizTalk Server finds an orchestration that uses a schema with a set target namespace, and the orchestration process is followed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0274a-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0274a-125">See Also</span></span>  
 [<span data-ttu-id="0274a-126">Développement d’applications</span><span class="sxs-lookup"><span data-stu-id="0274a-126">Developing Applications</span></span>](../core/developing-applications5.md)