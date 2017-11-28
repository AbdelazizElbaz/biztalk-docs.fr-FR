---
title: "Vue propriété de contexte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking Profile Editor, message schemas
- Context Property view [Tracking Profile Editor]
- Tracking Profile Editor, Context Property view
- message schemas, XML messages
ms.assetid: 17a21b86-995c-4dc2-9a3c-1309837d0b9b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84a0f3a1d507e1440f67cd5f9e4afa18bff0b52a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="context-property-view"></a><span data-ttu-id="cab07-102">Vue Propriété de contexte</span><span class="sxs-lookup"><span data-stu-id="cab07-102">Context Property View</span></span>
<span data-ttu-id="cab07-103">La vue Propriété de contexte affiche le schéma du message XML associé à la propriété.</span><span class="sxs-lookup"><span data-stu-id="cab07-103">The Context Property view displays the schema of the XML message associated with the property.</span></span> <span data-ttu-id="cab07-104">Cette vue peut s'afficher à partir du menu contextuel de certaines des formes de la vue de planification d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="cab07-104">The view is available from the shortcut menu for some of the shapes in the Orchestration Schedule view.</span></span>  
  
## <a name="working-with-the-context-property-view"></a><span data-ttu-id="cab07-105">Utilisation de la vue Propriété de contexte</span><span class="sxs-lookup"><span data-stu-id="cab07-105">Working with the Context Property view</span></span>  
 <span data-ttu-id="cab07-106">Vous sélectionnez votre affichage de la propriété de contexte en cliquant sur le **Source d’événement sélectionnez** bouton et en cliquant sur le **sélectionner la propriété de contexte** élément de menu.</span><span class="sxs-lookup"><span data-stu-id="cab07-106">You select your Context Property view by clicking the **Select Event Source** button and clicking the **Select Context Property** menu item.</span></span> <span data-ttu-id="cab07-107">Sélectionnez ensuite une propriété de contexte dans la liste des propriétés de contexte connues pour charger le schéma correspondant à cette propriété.</span><span class="sxs-lookup"><span data-stu-id="cab07-107">You then choose a context property from the list of known context properties to load the schema for that property.</span></span> <span data-ttu-id="cab07-108">Une fois la propriété sélectionnée, vous pouvez faire glisser des éléments du schéma associé vers les dossiers des éléments de données de l'activité, indiquant ainsi que vous souhaitez extraire ces données de l'expression XPath contenue dans le message associé à l'action.</span><span class="sxs-lookup"><span data-stu-id="cab07-108">Once you select the property, you can drag elements from the associated schema to the data item folders of the activity, thus indicating you want to extract that data from specific XPath expression inside the message at this action.</span></span>  
  
 <span data-ttu-id="cab07-109">Vous pouvez ouvrir les vues de propriété de contexte à partir de la vue de la planification d'orchestration en cliquant avec le bouton droit sur une forme contenant une propriété de contexte.</span><span class="sxs-lookup"><span data-stu-id="cab07-109">You can open context property views from the orchestration schedule view by right-clicking a shape that contains a context property.</span></span> <span data-ttu-id="cab07-110">S’ouvre un menu contextuel à partir de laquelle vous pouvez cliquer sur le **schéma de propriété de contexte** élément de menu à récupérer la liste des propriétés de contexte associé à la forme.</span><span class="sxs-lookup"><span data-stu-id="cab07-110">This will open a context menu from which you can click the **Context Property Schema** menu item to retrieve a list of context properties associated with the shape.</span></span>  
  
 <span data-ttu-id="cab07-111">La liste des propriétés de contexte disponibles peut être longue.</span><span class="sxs-lookup"><span data-stu-id="cab07-111">The list of available context properties can be extensive.</span></span> <span data-ttu-id="cab07-112">Si vous connaissez une partie du nom de la propriété que vous recherchez, vous pouvez la taper dans le **dans la chaîne** zone de texte et cliquez sur le **recherche** bouton.</span><span class="sxs-lookup"><span data-stu-id="cab07-112">If you know part of the name of the property for which you are searching, you can type it in the **In String** text box and click the **Search** button.</span></span> <span data-ttu-id="cab07-113">Ainsi, seules les propriétés contenant la partie de la chaîne que vous avez entrée seront sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="cab07-113">This will select only those properties that contain the partial string you have entered.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cab07-114">Lorsque vous choisissez d'effectuer des mappages de la vue Propriétés de contexte, la liste des schémas de propriété potentiels est une liste complète de tous les schémas de propriété qui ont été configurés dans votre installation BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="cab07-114">When you choose to map from the Context Properties view, the list of potential property schemas is a complete list of every property schema configured in your BizTalk Server installation.</span></span>  <span data-ttu-id="cab07-115">Vous devez savoir que les schémas présentés ne tiennent pas compte des fonctionnalités BizTalk Server utilisées par le processus en cours d'exécution sur lequel vous travaillez.</span><span class="sxs-lookup"><span data-stu-id="cab07-115">You must aware that the schemas presented are not sensitive to which features in BizTalk Server are used by the running process on which you are working.</span></span> <span data-ttu-id="cab07-116">Vous pouvez par exemple sélectionner un schéma pour des propriétés SOAP dans la liste de schémas proposée lors d'un mappage à partir des propriétés de contexte, mais, de son côté, le processus en cours d'exécution ne pourra pas utiliser SOAP.</span><span class="sxs-lookup"><span data-stu-id="cab07-116">For example, you can select a schema for SOAP properties from the list of schemas offered when mapping from Context Properties, but the running process itself may not use SOAP.</span></span> <span data-ttu-id="cab07-117">Tout élément d'activité BAM mappé à partir d'une propriété inutilisée entraîne la capture de données nulles ou vides par l'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="cab07-117">Any BAM activity item mapped from an unused property results in null or empty data being captured by BAM.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cab07-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cab07-118">See Also</span></span>  
 <span data-ttu-id="cab07-119">[Nouveautés de la vue ?](../core/what-is-the-source-event-view.md) </span><span class="sxs-lookup"><span data-stu-id="cab07-119">[What Is the Source Event View?](../core/what-is-the-source-event-view.md) </span></span>  
 [<span data-ttu-id="cab07-120">Éditeur de modèle de suivi</span><span class="sxs-lookup"><span data-stu-id="cab07-120">Tracking Profile Editor</span></span>](../core/tracking-profile-editor.md)