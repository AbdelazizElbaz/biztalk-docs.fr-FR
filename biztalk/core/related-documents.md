---
title: Des Documents relatifs aux | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [BAM], document references
- definition files [BAM], related documents
- Query Builder [BAM portal], viewing details
- document references [BAM]
- Query Builder [BAM portal], document references
- queries [BAM], viewing details
ms.assetid: 9c5f2175-fe7c-40ec-910d-1ac5c8142045
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b87f0d31010a8bf80e09c59f05f2f9302a510e2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="related-documents"></a><span data-ttu-id="c1602-102">Documents associés</span><span class="sxs-lookup"><span data-stu-id="c1602-102">Related Documents</span></span>
<span data-ttu-id="c1602-103">La zone Documents associés des détails des résultats de requête affiche une liste de documents de référence associés à l'activité.</span><span class="sxs-lookup"><span data-stu-id="c1602-103">The Related Documents area of the query results detail displays a list of documents that are reference documents that relate to the activity.</span></span> <span data-ttu-id="c1602-104">Il peut s'agir de documents de tout type : image CAO, fichier .WAV ou bon de commande.</span><span class="sxs-lookup"><span data-stu-id="c1602-104">The documents can be of any type, including a CAD image, a .WAV file, or a purchase order.</span></span> <span data-ttu-id="c1602-105">Par exemple, une activité Bon de commande est généralement associée à un document de base de type Bon de commande.</span><span class="sxs-lookup"><span data-stu-id="c1602-105">For example, a Purchase Order activity will typically have a Purchase Order as a base document type.</span></span> <span data-ttu-id="c1602-106">La liste contient un lien vers le bon de commande.</span><span class="sxs-lookup"><span data-stu-id="c1602-106">The list will contain a link to the purchase order.</span></span>  
  
## <a name="adding-document-references"></a><span data-ttu-id="c1602-107">Ajout de références de document</span><span class="sxs-lookup"><span data-stu-id="c1602-107">Adding document references</span></span>  
 <span data-ttu-id="c1602-108">La liste des documents associés peut être générée de deux façons :</span><span class="sxs-lookup"><span data-stu-id="c1602-108">The list of related documents is generated in one of two ways:</span></span>  
  
-   <span data-ttu-id="c1602-109">Lorsque vous développez votre modèle de suivi, vous incluez un nœud Document Reference URL dans l'arborescence d'activité, puis le mappez à partir d'une source contenant un pointeur de référence vers le document physique.</span><span class="sxs-lookup"><span data-stu-id="c1602-109">When you develop your tracking profile you include a Document Reference URL node in the activity tree and then map it from a source containing a reference pointer to the physical document.</span></span>  
  
-   <span data-ttu-id="c1602-110">Votre développeur d'intégration remplit la liste à l'aide d'un programme en appelant votre application personnalisée.</span><span class="sxs-lookup"><span data-stu-id="c1602-110">Your integration developer programmatically populates the list by calling your custom application.</span></span>  
  
 <span data-ttu-id="c1602-111">Définition de la référence de document à l’aide de ces méthodes ajoute une ligne dans le \<activityname\>_References table avec l’emplacement du document.</span><span class="sxs-lookup"><span data-stu-id="c1602-111">Defining the document reference using either of these methods adds a row in the \<activityname\>_References table with the document location.</span></span>  
  
 <span data-ttu-id="c1602-112">Si aucune de ces tâches n’a été effectuée, le **Document associé** zone est vide.</span><span class="sxs-lookup"><span data-stu-id="c1602-112">If neither of these tasks has been performed, the **Related Document** area is blank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1602-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1602-113">See Also</span></span>  
 [<span data-ttu-id="c1602-114">Éditeur de modèle de suivi</span><span class="sxs-lookup"><span data-stu-id="c1602-114">Tracking Profile Editor</span></span>](../core/tracking-profile-editor.md)