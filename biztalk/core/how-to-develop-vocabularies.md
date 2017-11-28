---
title: "Le développement des vocabulaires | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, vocabularies
- vocabularies, business rules
- business rules, vocabularies
- vocabularies, creating
ms.assetid: 5c16eb98-2257-44f2-8a29-899e02f7e556
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2644cc938cbe5e42f4e124453d863741755d965d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-develop-vocabularies"></a><span data-ttu-id="02763-102">Développement des vocabulaires</span><span class="sxs-lookup"><span data-stu-id="02763-102">How to Develop Vocabularies</span></span>
<span data-ttu-id="02763-103">Les conditions et les actions des règles sont basées sur des sources associées éventuellement à des informations de liaison détaillées et difficiles à lire qui renseignent peu ou pas du tout l'utilisateur sur ce à quoi elles font référence.</span><span class="sxs-lookup"><span data-stu-id="02763-103">Rule conditions and actions are based on sources that may have detailed, difficult-to-read binding information that tells the user little or nothing about what they refer to.</span></span> <span data-ttu-id="02763-104">L'infrastructure de règles d'entreprise vous permet de créer des vocabulaires pour simplifier le développement des règles en offrant aux utilisateurs une terminologie intuitive et spécifique à chaque domaine qu'ils peuvent associer aux conditions et aux actions des règles.</span><span class="sxs-lookup"><span data-stu-id="02763-104">The Business Rules Framework enables you to create vocabularies to simplify the development of rules by offering users intuitive, domain-specific terminology that users can associate with rule conditions and actions.</span></span>  
  
 <span data-ttu-id="02763-105">Vous pouvez identifier des sources de données pour utiliser et créer un vocabulaire ainsi que pour y ajouter des définitions.</span><span class="sxs-lookup"><span data-stu-id="02763-105">You can identify data sources to use, create a new vocabulary, and add vocabulary definitions to it.</span></span> <span data-ttu-id="02763-106">Vous pouvez enregistrer une version de votre vocabulaire dans le magasin de règles et, une fois qu'elle est terminée, la publier afin de fournir aux utilisateurs un ensemble de termes bien définis et immuables liés aux références de données.</span><span class="sxs-lookup"><span data-stu-id="02763-106">You can save a version of your vocabulary to the rule store, and when it is complete, you can publish it to provide users with a well-defined, immutable set of terms that are bound to data references.</span></span>  
  
 <span data-ttu-id="02763-107">Si vous devez apporter des modifications à votre vocabulaire par la suite, il vous suffira de créer une nouvelle version de ce dernier, version qui reflètera ces changements.</span><span class="sxs-lookup"><span data-stu-id="02763-107">If you need to make changes to your vocabulary in the future, you can simply create a new version of the vocabulary that reflects the changes.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="02763-108">Si une nouvelle version d'un vocabulaire est créée, les règles créées à partir d'une version précédente feront toujours référence à cette version.</span><span class="sxs-lookup"><span data-stu-id="02763-108">When a new version of a vocabulary is created, the rules built from a previous version will still point to the previous version.</span></span>  
  
### <a name="to-create-a-vocabulary"></a><span data-ttu-id="02763-109">Pour créer un vocabulaire</span><span class="sxs-lookup"><span data-stu-id="02763-109">To create a vocabulary</span></span>  
  
1.  <span data-ttu-id="02763-110">Dans la fenêtre Explorateur de faits, cliquez sur le **vocabulaires** onglet.</span><span class="sxs-lookup"><span data-stu-id="02763-110">In the Facts Explorer window, click the **Vocabularies** tab.</span></span>  
  
2.  <span data-ttu-id="02763-111">Cliquez sur le **vocabulaires** dossier, puis cliquez sur **ajouter un nouveau vocabulaire**.</span><span class="sxs-lookup"><span data-stu-id="02763-111">Right-click the **Vocabularies** folder, and then click **Add New Vocabulary**.</span></span>  
  
     <span data-ttu-id="02763-112">Un nouveau **vocabulaire** dossier apparaît sous le **vocabulaires** dossier.</span><span class="sxs-lookup"><span data-stu-id="02763-112">A new **vocabulary** folder appears under the **Vocabularies** folder.</span></span>  
  
3.  <span data-ttu-id="02763-113">Cliquez sur la nouvelle **vocabulaire** dossier, puis modifiez son nom dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="02763-113">Click the new **vocabulary** folder, and then edit the name in the Properties window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="02763-114">Vous devez tout enregistrer (toutes les versions des définitions) avant de pouvoir renommer un vocabulaire ou une stratégie.</span><span class="sxs-lookup"><span data-stu-id="02763-114">You must save everything (all versions of the definitions) before you can rename a vocabulary or a policy.</span></span>