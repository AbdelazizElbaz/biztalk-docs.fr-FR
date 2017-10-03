---
title: Ajout et suppression des espaces de noms dans un document XML de Document Message | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dbf2f209-13b9-42e0-b0f2-b53ec705e84b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3bb3b28504f92164aca1f66902546f1e04a2290
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-and-removing-namespaces-in-an-xml-message-document"></a><span data-ttu-id="0b7d0-102">Ajout et suppression des espaces de noms dans un Document XML du Message</span><span class="sxs-lookup"><span data-stu-id="0b7d0-102">Adding and Removing Namespaces in an XML Message Document</span></span>
<span data-ttu-id="0b7d0-103">Dans ce cas de figure, le composant Namespace fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] ajoute des espaces de noms, ou supprime les espaces de noms à partir des documents et des messages, comme illustré dans la Figure 1.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-103">In this use case, the Namespace component provided with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] adds namespaces to, or removes namespaces from, documents and messages, as illustrated in Figure 1.</span></span> <span data-ttu-id="0b7d0-104">Cela empêche les conflits d’espace de noms ou les erreurs liées lorsque les documents utilisent des espaces de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-104">This prevents namespace clashes or errors arising when documents use default namespaces.</span></span>  
  
 <span data-ttu-id="0b7d0-105">![Ajout de suppression des espaces de noms](../esb-toolkit/media/ch3-addingremovingnamespaces.gif "Ch3-AddingRemovingNamespaces")</span><span class="sxs-lookup"><span data-stu-id="0b7d0-105">![Adding Removing Namespaces](../esb-toolkit/media/ch3-addingremovingnamespaces.gif "Ch3-AddingRemovingNamespaces")</span></span>  
  
 <span data-ttu-id="0b7d0-106">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="0b7d0-106">**Figure 1**</span></span>  
  
 <span data-ttu-id="0b7d0-107">**Ajout et suppression des espaces de noms XML document et de message**</span><span class="sxs-lookup"><span data-stu-id="0b7d0-107">**Adding and removing XML document and message namespaces**</span></span>  
  
 <span data-ttu-id="0b7d0-108">L’exemple de composant de Namespace inclus avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-108">The Namespace Component sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span> <span data-ttu-id="0b7d0-109">Il montre comment utiliser le composant pour insérer et supprimer des espaces de noms dans un document dans le cadre de l’envoi et le processus de réception.</span><span class="sxs-lookup"><span data-stu-id="0b7d0-109">It shows how to use the component to inject and remove namespaces in a document as part of the send and the receive process.</span></span>  
  
 <span data-ttu-id="0b7d0-110">Pour plus d’informations, consultez [installer et exécuter l’exemple de composant Namespace](../esb-toolkit/installing-and-running-the-namespace-component-sample.md).</span><span class="sxs-lookup"><span data-stu-id="0b7d0-110">For more information, see [Installing and Running the Namespace Component Sample](../esb-toolkit/installing-and-running-the-namespace-component-sample.md).</span></span>