---
title: "Nœuds de référence d’URL de document | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Document Reference URL nodes [Tracking Profile Editor]
- Tracking Profile Editor, node descriptions
- definition files [BAM], related documents
ms.assetid: 38c8ae50-ed56-451c-9549-db852d4770e5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c7939a7e74483b8df192530fd9da2deafeda0681
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="document-reference-url-nodes"></a><span data-ttu-id="d3f9e-102">Nœuds Document Reference URL</span><span class="sxs-lookup"><span data-stu-id="d3f9e-102">Document Reference URL Nodes</span></span>
<span data-ttu-id="d3f9e-103">Il existe, dans le fichier de définition de l'activité, des nœuds Document Reference URL qu'un développeur importe du modèle d'observation créé par le travailleur du savoir.</span><span class="sxs-lookup"><span data-stu-id="d3f9e-103">Document Reference URL nodes exist in the activity definition file that the developer imports from the knowledge worker created observation model.</span></span> <span data-ttu-id="d3f9e-104">Les nœuds Document Reference URL contiennent des références pour un emplacement où se trouve un document associé à la présente activité.</span><span class="sxs-lookup"><span data-stu-id="d3f9e-104">Document Reference URL nodes contain references to a location that contains a document that is related to this activity.</span></span> <span data-ttu-id="d3f9e-105">Ce document peut être de n'importe quel type. Par exemple, pour une activité qui représente un flux de travail d'acceptation d'un bon de commande, le nœud Document Reference URL peut pointer vers le document du bon de commande concerné.</span><span class="sxs-lookup"><span data-stu-id="d3f9e-105">This can be any type of document, for example an activity that represents a purchase order approval work flow, the Document Reference URL might point to the underlying purchase order document.</span></span>  
  
## <a name="working-with-document-reference-url-nodes"></a><span data-ttu-id="d3f9e-106">Utilisation des nœuds Document Reference URL</span><span class="sxs-lookup"><span data-stu-id="d3f9e-106">Working with Document Reference URL nodes</span></span>  
 <span data-ttu-id="d3f9e-107">La source de données pour le nœud Document Reference URL est généralement le **MessageRefURL** propriété système BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d3f9e-107">The data source for the Document Reference URL is typically the **MessageRefURL** BizTalk Server system property.</span></span> <span data-ttu-id="d3f9e-108">Vous pouvez également utiliser des schémas personnalisés pour stocker les URL et effectuer un mappage de la propriété vers le nœud Document Reference URL.</span><span class="sxs-lookup"><span data-stu-id="d3f9e-108">You can also use custom schemas that store URLs and map the property to the Document Reference URL from the custom schema.</span></span>  
  
 <span data-ttu-id="d3f9e-109">Éléments à prendre en compte pour les nœuds Document Reference URL :</span><span class="sxs-lookup"><span data-stu-id="d3f9e-109">Items to note about Document Reference URLs:</span></span>  
  
-   <span data-ttu-id="d3f9e-110">Vous pouvez ajouter un ou plusieurs nœuds Document Reference URL, mais chacun d'entre eux doit être doté d'un nom unique dans l'activité.</span><span class="sxs-lookup"><span data-stu-id="d3f9e-110">You can add one or more Document Reference URLs, but each node must have unique name within the activity.</span></span>  
  
-   <span data-ttu-id="d3f9e-111">Le **MessageRefURL** propriété requis pour remplir un nœud Document Reference URL n’est remplie avec une valeur dans le cas des adaptateurs de transport WSS, le fichier et FTP.</span><span class="sxs-lookup"><span data-stu-id="d3f9e-111">The **MessageRefURL** property needed to populate a Document Reference URL node is only populated with a value in the case of WSS, FILE, and FTP transport adapters.</span></span>  
  
-   <span data-ttu-id="d3f9e-112">Alors que les utilisateurs finaux peuvent afficher cette référence dans le portail BAM, l’objectif principal de l’URL de référence est de permettre aux développeurs d’interface utilisateur personnalisée accéder à des informations de document associé afin qu’ils peuvent présenter à l’utilisateur final.</span><span class="sxs-lookup"><span data-stu-id="d3f9e-112">While business end-users can view this reference in the BAM portal, the primary purpose of the reference URL is to allow custom user interface developers to gain access to associated document information so that they can present it to the end user.</span></span>  <span data-ttu-id="d3f9e-113">Pour plus d’informations sur l’affichage de la référence de document dans le portail BAM, consultez [Documents associés](../core/related-documents.md).</span><span class="sxs-lookup"><span data-stu-id="d3f9e-113">For more information on viewing the document reference in the BAM portal, see [Related Documents](../core/related-documents.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3f9e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3f9e-114">See Also</span></span>  
 [<span data-ttu-id="d3f9e-115">Nœuds de l’activité TPE</span><span class="sxs-lookup"><span data-stu-id="d3f9e-115">TPE Activity View Nodes</span></span>](../core/tpe-activity-view-nodes.md)