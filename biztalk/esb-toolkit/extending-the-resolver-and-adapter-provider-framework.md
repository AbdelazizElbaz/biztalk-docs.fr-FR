---
title: "Étendre l’infrastructure de fournisseur de carte et le programme de résolution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4d5e6f2-b3bc-46e2-b8f7-d7e271d4a8c0
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6ab5caf03d113e313e00a74c11641058e86b886
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="extending-the-resolver-and-adapter-provider-framework"></a><span data-ttu-id="02263-102">Étendre l’infrastructure de fournisseur de carte et le programme de résolution</span><span class="sxs-lookup"><span data-stu-id="02263-102">Extending the Resolver and Adapter Provider Framework</span></span>
<span data-ttu-id="02263-103">Le programme de résolution et l’infrastructure d’adaptateurs fournisseur prend en charge pour le point de terminaison et la résolution de la transformation et le routage, et elle peut également fournir des métadonnées personnalisées pour les services.</span><span class="sxs-lookup"><span data-stu-id="02263-103">The Resolver and Adapter Provider Framework provides support for endpoint and transformation resolution and routing, and it can also provide custom metadata for services.</span></span> <span data-ttu-id="02263-104">L’infrastructure peut résoudre les points de terminaison et définir les propriétés de l’adaptateur de sortie dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="02263-104">The framework can dynamically resolve endpoints and set outbound adapter properties.</span></span> <span data-ttu-id="02263-105">Après un programme de résolution composant résout un point de terminaison (par exemple, pour rechercher une URL sortante à l’aide de Universal Description, Discovery and Integration [UDDI]), un composant du fournisseur d’adaptateur définit des propriétés spécifiques des adaptateurs Microsoft BizTalk Server inscrits.</span><span class="sxs-lookup"><span data-stu-id="02263-105">After a resolver component resolves an endpoint (for example, using Universal Description, Discovery, and Integration [UDDI] to look up an outbound URL), an adapter provider component sets specific properties of registered Microsoft BizTalk Server adapters.</span></span>  
  
 <span data-ttu-id="02263-106">Il existe trois grands domaines où vous pouvez étendre l’infrastructure de fournisseur de carte et de programme de résolution :</span><span class="sxs-lookup"><span data-stu-id="02263-106">There are three main areas where you can extend the Resolver and Adapter Provider Framework:</span></span>  
  
-   [<span data-ttu-id="02263-107">Création d’un programme de résolution personnalisé</span><span class="sxs-lookup"><span data-stu-id="02263-107">Creating a Custom Resolver</span></span>](../esb-toolkit/creating-a-custom-resolver.md)  
  
-   [<span data-ttu-id="02263-108">Création d’un programme de résolution personnalisé avec un conteneur Unity</span><span class="sxs-lookup"><span data-stu-id="02263-108">Creating a Custom Resolver with a Unity Container</span></span>](../esb-toolkit/creating-a-custom-resolver-with-a-unity-container.md)  
  
-   [<span data-ttu-id="02263-109">Création d’un fournisseur de l’adaptateur personnalisé</span><span class="sxs-lookup"><span data-stu-id="02263-109">Creating a Custom Adapter Provider</span></span>](../esb-toolkit/creating-a-custom-adapter-provider.md)