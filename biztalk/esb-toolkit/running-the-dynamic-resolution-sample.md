---
title: "Exécution de l’exemple de résolution dynamique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c933839f-13e6-4b49-9838-2773e3f99b64
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e613934c44db03cf29edbf3fff4ef34d6b946577
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-dynamic-resolution-sample"></a><span data-ttu-id="c71f4-102">Exécution de l’exemple de résolution dynamique</span><span class="sxs-lookup"><span data-stu-id="c71f4-102">Running the Dynamic Resolution Sample</span></span>
<span data-ttu-id="c71f4-103">Pour exécuter un des exemples de cas d’utilisation, vous importez le fichier de liaison de Microsoft BizTalk approprié dans l’application BizTalk de GlobalBank.ESB puis déposez un message approprié dans le dossier d’exemples d’entrée ou appelez l’exemple de service Web.</span><span class="sxs-lookup"><span data-stu-id="c71f4-103">To execute one of the use case examples, you import the appropriate Microsoft BizTalk binding file into the GlobalBank.ESB BizTalk application and then either drop a suitable message into the sample input folder or call the sample Web service.</span></span> <span data-ttu-id="c71f4-104">L’exemple de résolution dynamique prend en charge deux scénarios principaux :</span><span class="sxs-lookup"><span data-stu-id="c71f4-104">The Dynamic Resolution sample supports two main scenarios:</span></span>  
  
-   <span data-ttu-id="c71f4-105">[Les scénarios de messagerie unidirectionnels pour l’exemple de résolution dynamique](../esb-toolkit/one-way-messaging-scenarios-for-the-dynamic-resolution-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c71f4-105">[One-Way Messaging Scenarios for the Dynamic Resolution Sample](../esb-toolkit/one-way-messaging-scenarios-for-the-dynamic-resolution-sample.md).</span></span> <span data-ttu-id="c71f4-106">Résolution dynamique exemple prend en charge ce scénario à l’aide d’un dossier de dépôt du fichier en tant que la publication pointent tous dans Microsoft BizTalk.</span><span class="sxs-lookup"><span data-stu-id="c71f4-106">The Dynamic Resolution sample supports this scenario using a file drop folder as the publication point into Microsoft BizTalk.</span></span>  
  
-   <span data-ttu-id="c71f4-107">[Les scénarios de messagerie bidirectionnelles pour l’exemple de résolution dynamique](../esb-toolkit/two-way-messaging-scenarios-for-the-dynamic-resolution-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c71f4-107">[Two-Way Messaging Scenarios for the Dynamic Resolution Sample](../esb-toolkit/two-way-messaging-scenarios-for-the-dynamic-resolution-sample.md).</span></span> <span data-ttu-id="c71f4-108">L’exemple de résolution dynamique prend en charge ce scénario en utilisant le service de NorthAmerican Web situé à http://localhost/ESB.NorthAmericanServices/CustomerOrder.asmx que la publication point dans BizTalk.</span><span class="sxs-lookup"><span data-stu-id="c71f4-108">The Dynamic Resolution sample supports this scenario using the NorthAmerican Web service located at http://localhost/ESB.NorthAmericanServices/CustomerOrder.asmx as the publication point into BizTalk.</span></span>  
  
 <span data-ttu-id="c71f4-109">Pour comprendre comment l’exemple utilise le répartiteur d’ESB et les composants de pipeline désassembleur de répartiteur ESB, consultez [dynamique résolution exemple fonctionnement](../esb-toolkit/how-the-dynamic-resolution-sample-works.md).</span><span class="sxs-lookup"><span data-stu-id="c71f4-109">To understand how the sample uses the ESB Dispatcher and ESB Dispatcher Disassembler pipeline components, see [How the Dynamic Resolution Sample Works](../esb-toolkit/how-the-dynamic-resolution-sample-works.md).</span></span>