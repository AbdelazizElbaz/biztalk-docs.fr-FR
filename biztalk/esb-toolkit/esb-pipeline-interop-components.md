---
title: "Composants d’interopérabilité ESB Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25f9fb9d-d3d4-4df8-8e81-38b432f42ccf
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ccf4d4353e6928b998d31e8096ee642cd80bb60a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="esb-pipeline-interop-components"></a><span data-ttu-id="33cdd-102">Composants Interop Pipeline ESB</span><span class="sxs-lookup"><span data-stu-id="33cdd-102">ESB Pipeline Interop Components</span></span>
<span data-ttu-id="33cdd-103">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] fournit la prise en charge des composants et services, notamment les suivantes :</span><span class="sxs-lookup"><span data-stu-id="33cdd-103">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] provides support components and services, including the following:</span></span>  
  
-   <span data-ttu-id="33cdd-104">**Composants de pipeline JMS.**</span><span class="sxs-lookup"><span data-stu-id="33cdd-104">**JMS pipeline components.**</span></span> <span data-ttu-id="33cdd-105">Ces composants reconnaîtront, valider et exposent les métadonnées et le contenu des messages conformes au format JMS MQRFH2 utilisé par les systèmes de messagerie IBM MQSeries.</span><span class="sxs-lookup"><span data-stu-id="33cdd-105">These components recognize, validate, and expose metadata and the content of messages that conform to the JMS MQRFH2 format used by IBM MQ Series messaging systems.</span></span> <span data-ttu-id="33cdd-106">Cette fonctionnalité permet une [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] application à recevoir des messages et envoyer des messages aux systèmes JMS via MQ Series.</span><span class="sxs-lookup"><span data-stu-id="33cdd-106">This functionality allows a [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] application to receive messages from and send messages to JMS systems over MQ Series.</span></span> <span data-ttu-id="33cdd-107">Les composants automatiquement promouvoir les informations d’en-tête et rétrograder du contenu du message.</span><span class="sxs-lookup"><span data-stu-id="33cdd-107">The components automatically promote header information into, and demote it from, the message content.</span></span>  
  
-   <span data-ttu-id="33cdd-108">**Composants de pipeline Namespace.**</span><span class="sxs-lookup"><span data-stu-id="33cdd-108">**Namespace pipeline components.**</span></span> <span data-ttu-id="33cdd-109">Ces composants peuvent ajouter ou supprimer des espaces de noms dans le contenu des messages XML.</span><span class="sxs-lookup"><span data-stu-id="33cdd-109">These components can add or remove namespaces in the content of XML messages.</span></span> <span data-ttu-id="33cdd-110">Cela permet aux applications réparer des espaces de noms en conflit ou ajouter des espaces de noms manquant pour éviter les collisions d’espace de noms dans les orchestrations de base de données et application de boîte de Message.</span><span class="sxs-lookup"><span data-stu-id="33cdd-110">This allows applications to repair conflicting namespaces or add missing namespaces to prevent namespace collisions within the Message Box database and application orchestrations.</span></span> <span data-ttu-id="33cdd-111">Les composants permettent également de BizTalk Server consommer POX (Plain Old XML) sans modifier la publication des systèmes externes.</span><span class="sxs-lookup"><span data-stu-id="33cdd-111">The components also allow BizTalk Server to consume POX (Plain Old XML) without modifying external publishing systems.</span></span>  
  
 <span data-ttu-id="33cdd-112">Pour plus d’informations sur les composants de pipeline ESB, consultez [à l’aide de composants de prise en charge du Pipeline](../esb-toolkit/using-the-pipeline-support-components.md).</span><span class="sxs-lookup"><span data-stu-id="33cdd-112">For more information about the ESB pipeline components, see [Using the Pipeline Support Components](../esb-toolkit/using-the-pipeline-support-components.md).</span></span>