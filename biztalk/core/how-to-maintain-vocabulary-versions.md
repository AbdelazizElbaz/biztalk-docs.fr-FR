---
title: "Comment mettre à jour les Versions de vocabulaire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, vocabularies
- vocabularies, creating
- vocabularies, versioning
- vocabularies, publishing
- versioning, vocabularies
- updating, vocabularies
- vocabularies, updating
ms.assetid: 43593c6f-4590-4940-ac17-4015928e5838
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b3c67d79878c59e3b0dcba6dcd15955f34ad97c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-maintain-vocabulary-versions"></a><span data-ttu-id="5c237-102">Comment mettre à jour les Versions de vocabulaire</span><span class="sxs-lookup"><span data-stu-id="5c237-102">How to Maintain Vocabulary Versions</span></span>
<span data-ttu-id="5c237-103">Lorsque vous avez ajouté des définitions de vocabulaire à une version de votre vocabulaire, vous pouvez enregistrer la version dans le magasin de règles en vue de la développer, ou la publier afin de fournir aux utilisateurs un ensemble de termes bien définis et immuables à ajouter aux règles pendant qu'ils développent leurs stratégies.</span><span class="sxs-lookup"><span data-stu-id="5c237-103">When you have added vocabulary definitions to a version of your vocabulary, you can save the version to the rule store for further development, or you can publish the version to create a well-defined, immutable set of data-bound terms that are available to users to add to rules as they develop their policies.</span></span> <span data-ttu-id="5c237-104">Notez que les règles existantes pointeront toujours vers les anciennes versions.</span><span class="sxs-lookup"><span data-stu-id="5c237-104">Note that fact that existing rules will still point to the old versions.</span></span>  
  
 <span data-ttu-id="5c237-105">Cette rubrique contient les procédures des tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="5c237-105">This topic contains procedures for the following tasks:</span></span>  
  
-   <span data-ttu-id="5c237-106">Pour enregistrer une version de vocabulaire</span><span class="sxs-lookup"><span data-stu-id="5c237-106">To save a vocabulary version</span></span>  
  
-   <span data-ttu-id="5c237-107">Pour publier une version de vocabulaire</span><span class="sxs-lookup"><span data-stu-id="5c237-107">To publish a vocabulary version</span></span>  
  
-   <span data-ttu-id="5c237-108">Pour créer une version mise à jour d'un vocabulaire</span><span class="sxs-lookup"><span data-stu-id="5c237-108">To create an updated version of a vocabulary</span></span>  
  
-   <span data-ttu-id="5c237-109">Pour créer une version vide d'un vocabulaire</span><span class="sxs-lookup"><span data-stu-id="5c237-109">To create an empty new version of a vocabulary</span></span>  
  
### <a name="to-save-a-vocabulary-version"></a><span data-ttu-id="5c237-110">Pour enregistrer une version de vocabulaire</span><span class="sxs-lookup"><span data-stu-id="5c237-110">To save a vocabulary version</span></span>  
  
-   <span data-ttu-id="5c237-111">Avec le bouton droit de la version, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="5c237-111">Right-click the version, and then click **Save**.</span></span>  
  
### <a name="to-publish-a-vocabulary-version"></a><span data-ttu-id="5c237-112">Pour publier une version de vocabulaire</span><span class="sxs-lookup"><span data-stu-id="5c237-112">To publish a vocabulary version</span></span>  
  
-   <span data-ttu-id="5c237-113">Avec le bouton droit de la version, puis cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="5c237-113">Right-click the version, and then click **Publish**.</span></span>  
  
### <a name="to-create-an-updated-version-of-a-vocabulary"></a><span data-ttu-id="5c237-114">Pour créer une version mise à jour d'un vocabulaire</span><span class="sxs-lookup"><span data-stu-id="5c237-114">To create an updated version of a vocabulary</span></span>  
  
1.  <span data-ttu-id="5c237-115">Cliquez sur une version existante, puis cliquez sur **copie**.</span><span class="sxs-lookup"><span data-stu-id="5c237-115">Right-click an existing version, and then click **Copy**.</span></span>  
  
2.  <span data-ttu-id="5c237-116">Cliquez sur le dossier de vocabulaire, puis cliquez sur **coller**.</span><span class="sxs-lookup"><span data-stu-id="5c237-116">Right-click the vocabulary folder, and then click **Paste**.</span></span>  
  
     <span data-ttu-id="5c237-117">Une nouvelle version est alors créée. Ses éléments sont les mêmes que ceux de la version copiée.</span><span class="sxs-lookup"><span data-stu-id="5c237-117">A new version is created, with the same elements as the copied version.</span></span>  
  
### <a name="to-create-an-empty-new-version-of-a-vocabulary"></a><span data-ttu-id="5c237-118">Pour créer une version vide d'un vocabulaire</span><span class="sxs-lookup"><span data-stu-id="5c237-118">To create an empty new version of a vocabulary</span></span>  
  
-   <span data-ttu-id="5c237-119">Cliquez sur le dossier de vocabulaire, puis cliquez sur **ajouter une nouvelle Version**.</span><span class="sxs-lookup"><span data-stu-id="5c237-119">Right-click the vocabulary folder, and then click **Add New Version**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5c237-120">Vous ne pouvez utiliser que des définitions de vocabulaire issues de vocabulaires publiés.</span><span class="sxs-lookup"><span data-stu-id="5c237-120">You can only use vocabulary definitions from published vocabularies.</span></span>