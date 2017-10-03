---
title: "Test de schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2e28b7c-9d0c-4336-8bee-4599d41a57f4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20879925ff98d5c5d6ca7d0c9ebcf11853239bba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="testing-schemas"></a><span data-ttu-id="21fc4-102">Test de schémas</span><span class="sxs-lookup"><span data-stu-id="21fc4-102">Testing Schemas</span></span>
<span data-ttu-id="21fc4-103">Après avoir créé un schéma, vous pourrez souhaiter valider le fait qu'il décrit la structure XML comme vous l'attendez de lui.</span><span class="sxs-lookup"><span data-stu-id="21fc4-103">After you have created your schema, you may want to validate that it describes the XML structure you intend it to describe.</span></span> <span data-ttu-id="21fc4-104">Vous pouvez soumettre votre schéma aux trois opérations suivantes pour le valider :</span><span class="sxs-lookup"><span data-stu-id="21fc4-104">You can perform the following three operations on your schema to validate it:</span></span>  
  
-   <span data-ttu-id="21fc4-105">**Génération d’instance**.</span><span class="sxs-lookup"><span data-stu-id="21fc4-105">**Instance generation**.</span></span> <span data-ttu-id="21fc4-106">cette opération génère un message d'instance à partir d'un schéma, créant des données de test pour accompagner les attributs et éléments XML spécifiés par le schéma.</span><span class="sxs-lookup"><span data-stu-id="21fc4-106">This operation generates an instance message from a schema, creating test data to accompany the XML elements and attributes specified by the schema.</span></span>  
  
-   <span data-ttu-id="21fc4-107">**Validation de schéma**.</span><span class="sxs-lookup"><span data-stu-id="21fc4-107">**Schema validation**.</span></span> <span data-ttu-id="21fc4-108">cette opération valide la cohérence interne d'un schéma, garantissant qu'il est conforme à la norme de schéma XSD (XML Schema Definition).</span><span class="sxs-lookup"><span data-stu-id="21fc4-108">This operation validates the internal consistency of a schema, assuring that it conforms to the XML Schema definition (XSD) language schema standard.</span></span>  
  
-   <span data-ttu-id="21fc4-109">**Validation d’instance**.</span><span class="sxs-lookup"><span data-stu-id="21fc4-109">**Instance validation**.</span></span> <span data-ttu-id="21fc4-110">cette opération valide un message d'instance donné en fonction d'un schéma.</span><span class="sxs-lookup"><span data-stu-id="21fc4-110">This operation validates a given instance message against a schema.</span></span>  
  
 <span data-ttu-id="21fc4-111">Ces trois opérations sont utiles pour tester vos schémas avant de les mettre en pratique dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="21fc4-111">All three of these operations are useful for testing your schemas before putting them into use in a production environment.</span></span>  
  
 <span data-ttu-id="21fc4-112">Cette section décrit ces opérations de façon plus détaillée.</span><span class="sxs-lookup"><span data-stu-id="21fc4-112">This section describes these operations in greater detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="21fc4-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="21fc4-113">In This Section</span></span>  
  
-   [<span data-ttu-id="21fc4-114">Comment valider des schémas dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="21fc4-114">How to Validate Schemas in Visual Studio</span></span>](../core/how-to-validate-schemas-in-visual-studio.md)  
  
-   [<span data-ttu-id="21fc4-115">Comment valider les Messages d’Instance</span><span class="sxs-lookup"><span data-stu-id="21fc4-115">How to Validate Instance Messages</span></span>](../core/how-to-validate-instance-messages.md)  
  
-   [<span data-ttu-id="21fc4-116">Comment générer des Messages d’Instance</span><span class="sxs-lookup"><span data-stu-id="21fc4-116">How to Generate Instance Messages</span></span>](../core/how-to-generate-instance-messages.md)