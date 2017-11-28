---
title: "Le schéma ne contient pas l’élément racine | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efc33f2b-9e14-4d2e-8c8a-32b7696f80ea
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c485ce27fc3a1932d7de47557080712e46b654e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-schema-does-not-contain-the-root-element"></a><span data-ttu-id="d298f-102">Le schéma ne contient pas d'élément racine</span><span class="sxs-lookup"><span data-stu-id="d298f-102">The schema does not contain the root element</span></span>
## <a name="details"></a><span data-ttu-id="d298f-103">Détails</span><span class="sxs-lookup"><span data-stu-id="d298f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d298f-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="d298f-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d298f-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="d298f-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d298f-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="d298f-106">Event ID</span></span>|-|  
|<span data-ttu-id="d298f-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="d298f-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d298f-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="d298f-108"> EDI</span></span>|  
|<span data-ttu-id="d298f-109">Composant</span><span class="sxs-lookup"><span data-stu-id="d298f-109">Component</span></span>|<span data-ttu-id="d298f-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="d298f-110">EDI Engine</span></span>|  
|<span data-ttu-id="d298f-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="d298f-111">Symbolic Name</span></span>|<span data-ttu-id="d298f-112">SchemaCode102ENullRootElement</span><span class="sxs-lookup"><span data-stu-id="d298f-112">SchemaCode102ENullRootElement</span></span>|  
|<span data-ttu-id="d298f-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="d298f-113">Message Text</span></span>|<span data-ttu-id="d298f-114">Le schéma ne contient pas l'élément racine {0}</span><span class="sxs-lookup"><span data-stu-id="d298f-114">The schema does not contain the root element {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d298f-115">Explication</span><span class="sxs-lookup"><span data-stu-id="d298f-115">Explanation</span></span>  
 <span data-ttu-id="d298f-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter le message entrant ou que le pipeline d'envoi n'a pas pu traiter le message sortant, car le schéma utilisé pour valider le message ne contient pas d'élément racine.</span><span class="sxs-lookup"><span data-stu-id="d298f-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming message or the send pipeline could not process the outgoing message because the schema used to validate the message did not contain the root element.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d298f-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="d298f-117">User Action</span></span>  
 <span data-ttu-id="d298f-118">Pour résoudre cette erreur, annulez le déploiement du schéma de document, ajoutez l'élément racine au schéma, puis redéployez le schéma.</span><span class="sxs-lookup"><span data-stu-id="d298f-118">To resolve this error, undeploy the document schema, add the root element to the schema, and then redeploy the schema.</span></span>