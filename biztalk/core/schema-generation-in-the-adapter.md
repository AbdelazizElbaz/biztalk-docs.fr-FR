---
title: "Génération de schéma dans l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, generating
- writing, schemas
ms.assetid: 43b69383-bae0-401b-9620-d4302db799b2
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d10d927e4ede59e716b3f9838c96bac8cd144a81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schema-generation-in-the-adapter"></a><span data-ttu-id="fb149-102">Génération de schémas dans l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="fb149-102">Schema Generation in the Adapter</span></span>
<span data-ttu-id="fb149-103">Un système TIBCO Rendezvous ne comporte pas de référentiel des types de messages.</span><span class="sxs-lookup"><span data-stu-id="fb149-103">A TIBCO Rendezvous system does not include a message types repository.</span></span> <span data-ttu-id="fb149-104">La construction et l'analyse d'un message sont enfouies au niveau de l'application Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="fb149-104">All the message construction and parsing is buried at the Rendezvous application level.</span></span> <span data-ttu-id="fb149-105">À cause de cette limitation, l'adaptateur Microsoft BizTalk pour TIBCO Rendezvous n'est pas en mesure d'offrir des fonctionnalités de génération de schémas.</span><span class="sxs-lookup"><span data-stu-id="fb149-105">Because of this limitation, Microsoft BizTalk Adapter for TIBCO Rendezvous cannot provide schema-generation capabilities.</span></span>  
  
## <a name="writing-schemas"></a><span data-ttu-id="fb149-106">Écriture de schémas</span><span class="sxs-lookup"><span data-stu-id="fb149-106">Writing Schemas</span></span>  
 <span data-ttu-id="fb149-107">Vous devez écrire un schéma et utiliser **ajouter un élément existant** dans Visual Studio pour l’importer pour une utilisation dans les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="fb149-107">You must write a schema and use **Add Existing Item** in Visual Studio to import it for use in orchestrations.</span></span> <span data-ttu-id="fb149-108">Les schémas sont essentiels aux outils de développement BizTalk Server et à l'intégration dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fb149-108">Schemas are very important for BizTalk Server development tools and for integration in Visual Studio.</span></span> <span data-ttu-id="fb149-109">Les développeurs BizTalk Server peuvent choisir de fournir un schéma complet, minimum ou une version intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="fb149-109">BizTalk Server developers can choose to provide a complete schema, a minimalist schema, or a version somewhere in between.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb149-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb149-110">See Also</span></span>  
 [<span data-ttu-id="fb149-111">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="fb149-111">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)