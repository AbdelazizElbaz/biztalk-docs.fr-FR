---
title: Configuration requise de PeopleSoft Enterprise | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PeopleSoft Enterprise, requirements
- send handlers, PeopleSoft requirements
- CLASSPATH environment variable
- custom component interface object
- system requirements
- GET_CI_INFO.pc
ms.assetid: fabd808d-d9b6-43b0-a12a-727189f00a9d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45f267afce09e9c50d732d376fde43beaa1ef39a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="peoplesoft-enterprise-requirements"></a><span data-ttu-id="27034-102">Configuration requise de PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="27034-102">PeopleSoft Enterprise Requirements</span></span>
## <a name="send-handler-peoplesoft-requirements"></a><span data-ttu-id="27034-103">Configuration requise de PeopleSoft relative aux gestionnaires d'envoi</span><span class="sxs-lookup"><span data-stu-id="27034-103">Send Handler PeopleSoft Requirements</span></span>  
 <span data-ttu-id="27034-104">L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise inclut une interface de composant personnalisée accessible via une API Java.</span><span class="sxs-lookup"><span data-stu-id="27034-104">Microsoft BizTalk Adapter for PeopleSoft Enterprise contains a custom component interface (CI) and provides access to it through a Java API.</span></span> <span data-ttu-id="27034-105">Un objet interface de composant personnalisée (`GET_CI_INFO`) est déployé dans le système PeopleSoft à l'aide des outils PeopleSoft pour fournir les informations de métadonnées requises par l'adaptateur BizTalk pour PeopleSoft Enterprise.</span><span class="sxs-lookup"><span data-stu-id="27034-105">A custom CI object, `GET_CI_INFO`, is deployed in the PeopleSoft system using PeopleSoft Tools to provide metadata information that is required by BizTalk Adapter for PeopleSoft Enterprise.</span></span> <span data-ttu-id="27034-106">Pour plus d’informations, consultez [préparation de l’utilisation de PeopleSoft Enterprise](../core/preparing-to-use-peoplesoft-enterprise.md).</span><span class="sxs-lookup"><span data-stu-id="27034-106">For more information, see [Preparing to Use PeopleSoft Enterprise](../core/preparing-to-use-peoplesoft-enterprise.md).</span></span>  
  
 <span data-ttu-id="27034-107">Téléchargement de l’interface de composant personnalisée est une occurrence unique.</span><span class="sxs-lookup"><span data-stu-id="27034-107">Uploading the custom component interface is a one-time occurrence.</span></span> <span data-ttu-id="27034-108">Installé avec le produit, ce fichier (`GET_CI_INFO.pc`) doit être installé avant d'utiliser l'adaptateur pour explorer les interfaces de composant.</span><span class="sxs-lookup"><span data-stu-id="27034-108">This file, `GET_CI_INFO.pc`, installs with the product and must be installed before you can use the adapter to browse CIs.</span></span> <span data-ttu-id="27034-109">Vous devez disposer d'un accès au Concepteur d'applications PeopleSoft. Il n'est toutefois pas nécessaire que l'application du Concepteur d'applications se trouve sur l'ordinateur BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="27034-109">You must have access to the PeopleSoft Application Designer, but the Application Designer application does not have to be on the BizTalk Server computer.</span></span> <span data-ttu-id="27034-110">Le Concepteur d'applications permet de télécharger l'interface de composant personnalisée sur l'ordinateur PeopleSoft que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="27034-110">You use the Application Designer to upload the custom CI onto the PeopleSoft computer that you browse.</span></span>  
  
 <span data-ttu-id="27034-111">Vous devez avoir accès à l’ordinateur PeopleSoft, car vous devez définir la variable d’environnement CLASSPATH (ou définir les informations dans le **propriétés du Transport** écran) pour pointer vers de PeopleSoft `PSJOA/psjoa.jar` fichier.</span><span class="sxs-lookup"><span data-stu-id="27034-111">You must have access to the PeopleSoft computer because you must set the environment variable CLASSPATH (or set the information in the **Transport Properties** screen) to point to PeopleSoft's `PSJOA/psjoa.jar` file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27034-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27034-112">See Also</span></span>  
 <span data-ttu-id="27034-113">[Prise en main](../core/getting-started-with-biztalk-adapter-for-peoplesoft-enterprise.md) </span><span class="sxs-lookup"><span data-stu-id="27034-113">[Getting Started](../core/getting-started-with-biztalk-adapter-for-peoplesoft-enterprise.md) </span></span>  
 [<span data-ttu-id="27034-114">Planification et Architecture</span><span class="sxs-lookup"><span data-stu-id="27034-114">Planning and Architecture</span></span>](../core/planning-and-architecture13.md)