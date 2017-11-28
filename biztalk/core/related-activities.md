---
title: "Activités connexes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities [BAM], related activities
- Query Builder [BAM portal], related activities
- queries [BAM], related activities
- Query Builder [BAM portal], viewing details
- queries [BAM], viewing details
ms.assetid: 141b7943-d244-4810-aa88-12aa4a2b7658
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fea95a74a15c685f2cff202fcf7f04c86244041b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="related-activities"></a><span data-ttu-id="05614-102">Activités associées</span><span class="sxs-lookup"><span data-stu-id="05614-102">Related Activities</span></span>
<span data-ttu-id="05614-103">La zone Activités associées contient une liste des activités associées à l'activité sur laquelle repose la requête.</span><span class="sxs-lookup"><span data-stu-id="05614-103">The Related Activities area contains a list of activities that are related to the activity on which the query is based.</span></span> <span data-ttu-id="05614-104">Par exemple, plusieurs activités d'expédition peuvent être associées à une activité Bon de commande, car il est possible d'envoyer les éléments d'un même bon de commande par l'intermédiaire de plusieurs expéditions.</span><span class="sxs-lookup"><span data-stu-id="05614-104">An example of a related activity for a Purchase Order activity would be multiple Shipment activities, since items on a single purchase order can be delivered in multiple shipments.</span></span>  
  
## <a name="creating-related-activities"></a><span data-ttu-id="05614-105">Création d'activités associées</span><span class="sxs-lookup"><span data-stu-id="05614-105">Creating related activities</span></span>  
 <span data-ttu-id="05614-106">La liste des activités associées peut être générée de deux façons :</span><span class="sxs-lookup"><span data-stu-id="05614-106">The list of related activities is generated in one of two ways:</span></span>  
  
-   <span data-ttu-id="05614-107">Vous définissez deux activités et créez ensuite une vue les incluant toutes les deux.</span><span class="sxs-lookup"><span data-stu-id="05614-107">You define two activities and then create a single view that includes both of them.</span></span> <span data-ttu-id="05614-108">Votre développeur établit alors une connexion de corrélation entre les deux activités en implémentant les relations de clé, de champ et de valeur entre les activités.</span><span class="sxs-lookup"><span data-stu-id="05614-108">Your developer makes a correlation connection between the two by implementing the key, field, and value relationships between the activities.</span></span>  
  
-   <span data-ttu-id="05614-109">Vous définissez deux activités.</span><span class="sxs-lookup"><span data-stu-id="05614-109">You define two activities.</span></span> <span data-ttu-id="05614-110">Votre développeur établit une connexion de corrélation dans votre application personnalisée en appelant AddRelationship() et en définissant les relations de clé, de champ et de valeur entre les activités.</span><span class="sxs-lookup"><span data-stu-id="05614-110">Your developer makes a correlation connection in your custom application by calling AddRelationship() and defining the key, field, and value relationships between the activities.</span></span>  
  
 <span data-ttu-id="05614-111">Définition des relations d’activité dans une des manières suivantes ajoute une ligne dans le \<nomactivité > _Relationships table.</span><span class="sxs-lookup"><span data-stu-id="05614-111">Defining the activity relationships in either of these ways adds a row in the \<activityname>_Relationships table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05614-112">Seule la première de ces méthodes permet aux activités associées de contenir des liens actifs les reliant les unes aux autres.</span><span class="sxs-lookup"><span data-stu-id="05614-112">Only the first method of defining relationships results in the related activities having live links to each other.</span></span> <span data-ttu-id="05614-113">La seconde méthode ne permet pas de définir une vue d'ensemble et le portail ne peut donc pas avoir connaissance de l'existence de relations entre les deux activités.</span><span class="sxs-lookup"><span data-stu-id="05614-113">The second method does not define a spanning view and therefore the portal cannot know about the relationship between the two activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05614-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05614-114">See Also</span></span>  
 [<span data-ttu-id="05614-115">Comment afficher les résultats d’une recherche d’activité</span><span class="sxs-lookup"><span data-stu-id="05614-115">How to View the Results of an Activity Search</span></span>](../core/how-to-view-the-results-of-an-activity-search.md)