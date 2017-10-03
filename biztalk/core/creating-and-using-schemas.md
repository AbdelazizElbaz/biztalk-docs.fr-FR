---
title: "Création et utilisation de schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generating schemas
- schemas
- creating schemas
- schemas, generating
ms.assetid: 3927b0b3-db3b-4494-b003-d930af734e58
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f10275c5ed0b887907c7b26b7d1ce8ad5003b099
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-using-schemas"></a><span data-ttu-id="a9c36-102">Création et utilisation de schémas</span><span class="sxs-lookup"><span data-stu-id="a9c36-102">Creating and Using Schemas</span></span>
<span data-ttu-id="a9c36-103">L'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service (EMS) utilise les schémas que vous créez à l'aide d'un éditeur XML ou de l'Éditeur BizTalk Server dans Visual Studio (uniquement lorsque l'adaptateur est utilisé dans une orchestration).</span><span class="sxs-lookup"><span data-stu-id="a9c36-103">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) uses schemas that you create using an XML editor or the BizTalk Server Editor in Visual Studio (only when you use the adapter in an orchestration).</span></span> <span data-ttu-id="a9c36-104">Le schéma décrit le type d'informations attendu.</span><span class="sxs-lookup"><span data-stu-id="a9c36-104">The schema describes the type of information that you expect.</span></span> <span data-ttu-id="a9c36-105">Cette rubrique contient des informations relatives aux gestionnaires d'envoi et de réception.</span><span class="sxs-lookup"><span data-stu-id="a9c36-105">This topic contains information for both a send and a receive handler.</span></span>  
  
 <span data-ttu-id="a9c36-106">Les schémas que vous créez pour être utilisés avec l'adaptateur BizTalk pour TIBCO Enterprise Message Service doivent inclure un espace de noms cible.</span><span class="sxs-lookup"><span data-stu-id="a9c36-106">The schemas you create for use with BizTalk Adapter for TIBCO Enterprise Message Service must have a target namespace.</span></span> <span data-ttu-id="a9c36-107">Celui-ci est nécessaire car il est la clé qui associe une instance de message donnée à une orchestration donnée.</span><span class="sxs-lookup"><span data-stu-id="a9c36-107">BizTalk Server requires the target namespace because it is the key that associates a given message instance with a given orchestration.</span></span> <span data-ttu-id="a9c36-108">En d'autres termes, une orchestration s'abonne aux messages associés à un espace de noms cible spécifique et un message XML entrant associé à cet espace de noms cible est transmis à chaque orchestration abonnée au message.</span><span class="sxs-lookup"><span data-stu-id="a9c36-108">In other words, an orchestration subscribes to any message that has a specific target namespace, and an incoming XML message that has that target namespace is given to every orchestration that subscribed to the message.</span></span> <span data-ttu-id="a9c36-109">Si un schéma de document XML n'inclut pas d'espace de noms cible, BizTalk Server utilise le nom de l'élément racine comme clé.</span><span class="sxs-lookup"><span data-stu-id="a9c36-109">If an XML document schema does not have a target namespace, BizTalk Server uses the name of the root element as a key.</span></span>  
  
## <a name="generating-a-schema"></a><span data-ttu-id="a9c36-110">Génération d'un schéma</span><span class="sxs-lookup"><span data-stu-id="a9c36-110">Generating a Schema</span></span>  
 <span data-ttu-id="a9c36-111">La procédure suivante décrit la génération d'un schéma et la définition de l'espace de noms cible.</span><span class="sxs-lookup"><span data-stu-id="a9c36-111">The following procedures show how to generate a schema and how to set the target namespace.</span></span>  
  
#### <a name="to-generate-a-schema-using-biztalk-editor"></a><span data-ttu-id="a9c36-112">Pour générer un schéma à l'aide de l'Éditeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="a9c36-112">To generate a schema using BizTalk Editor</span></span>  
  
1.  <span data-ttu-id="a9c36-113">Dans l'Éditeur BizTalk, ouvrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="a9c36-113">In the BizTalk Editor, open your project.</span></span>  
  
2.  <span data-ttu-id="a9c36-114">Dans l’Explorateur de solutions dans l’angle supérieur droit, sélectionnez **ajouter**, puis sélectionnez **ajouter les éléments générés**.</span><span class="sxs-lookup"><span data-stu-id="a9c36-114">Under Solution Explorer in the upper-right, select **Add**, and then select **Add Generated Items**.</span></span>  
  
3.  <span data-ttu-id="a9c36-115">Dans le **modèles** volet, sélectionnez **générer les schémas**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="a9c36-115">In the **Templates** pane, select **Generate Schemas**, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="a9c36-116">Dans le **générer les schémas** boîte de dialogue le **type de Document** liste, sélectionnez **XML bien formé**.</span><span class="sxs-lookup"><span data-stu-id="a9c36-116">In the **Generate Schemas** dialog box, in the **Document type** list, select **Well-Formed XML**.</span></span>  
  
5.  <span data-ttu-id="a9c36-117">Cliquez sur **Parcourir** pour localiser le fichier d’entrée pour laquelle vous souhaitez générer un schéma, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a9c36-117">Click **Browse** to locate the input file for which you want to generate a schema, and then click **OK**.</span></span>  
  
     <span data-ttu-id="a9c36-118">Vous devez ensuite définir l'espace de noms cible.</span><span class="sxs-lookup"><span data-stu-id="a9c36-118">Next, you must set the target namespace.</span></span>  
  
#### <a name="to-set-the-target-namespace"></a><span data-ttu-id="a9c36-119">Pour définir l'espace de noms cible</span><span class="sxs-lookup"><span data-stu-id="a9c36-119">To set the target namespace</span></span>  
  
1.  <span data-ttu-id="a9c36-120">Dans l’Éditeur BizTalk, ouvrez votre fichier de schéma, cliquez sur  **\<schéma >**, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="a9c36-120">In BizTalk Editor, open your schema file, right-click **\<schema>**, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="a9c36-121">Dans le **propriétés** volet, recherchez le **Namespace** champ et tapez un nom, par exemple, `testNameSpace`.</span><span class="sxs-lookup"><span data-stu-id="a9c36-121">In the **Properties** pane, locate the **Namespace** field and type a name, for example, `testNameSpace`.</span></span>  
  
 <span data-ttu-id="a9c36-122">Vous pouvez ensuite continuer à utiliser votre orchestration avec des messages.</span><span class="sxs-lookup"><span data-stu-id="a9c36-122">You can then continue with your orchestration using messages.</span></span> <span data-ttu-id="a9c36-123">Lorsqu'un message est récupéré, BizTalk Server recherche une orchestration qui utilise un schéma avec un espace de noms cible défini, et le processus d'orchestration suit son cours.</span><span class="sxs-lookup"><span data-stu-id="a9c36-123">When a message is picked up, BizTalk Server finds an orchestration that uses a schema with a set target namespace, and the orchestration process is followed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9c36-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9c36-124">See Also</span></span>  
 [<span data-ttu-id="a9c36-125">Développement d’applications</span><span class="sxs-lookup"><span data-stu-id="a9c36-125">Developing Applications</span></span>](../core/developing-applications5.md)