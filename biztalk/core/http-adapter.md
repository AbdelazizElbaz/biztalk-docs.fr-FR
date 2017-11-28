---
title: Adaptateur HTTP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP adapters, receive adapters
- HTTP adapters, send adapters
- HTTP adapters
- receive adapters, HTTP adapters
- send adapters, HTTP adapters
- HTTP adapters, about HTTP adapters
ms.assetid: a9423052-8392-4006-ab46-79834169c796
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d9be9fac6fdb65c4516c671b6c0e30096e83a27
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="http-adapter"></a><span data-ttu-id="a5785-102">Adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="a5785-102">HTTP Adapter</span></span>
<span data-ttu-id="a5785-103">L'adaptateur HTTP permet d'échanger des informations entre un serveur BizTalk Server et des applications à l'aide du protocole SMTP.</span><span class="sxs-lookup"><span data-stu-id="a5785-103">You use the HTTP adapter to exchange information between Microsoft BizTalk Server and an application by means of the HTTP protocol.</span></span> <span data-ttu-id="a5785-104">HTTP est le principal protocole d'échange de messages entre entreprises.</span><span class="sxs-lookup"><span data-stu-id="a5785-104">HTTP is the primary protocol for interbusiness message exchange.</span></span> <span data-ttu-id="a5785-105">Les applications peuvent envoyer des messages à un serveur en envoyant des requêtes HTTP POST ou HTTP GET à une adresse URL HTTP spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a5785-105">Applications can send messages to a server by sending HTTP POST or HTTP GET requests to a specified HTTP URL.</span></span> <span data-ttu-id="a5785-106">L'adaptateur HTTP reçoit les requêtes HTTP et les soumet à BizTalk Server pour traitement.</span><span class="sxs-lookup"><span data-stu-id="a5785-106">The HTTP adapter receives the HTTP requests and submits them to BizTalk Server for processing.</span></span> <span data-ttu-id="a5785-107">De même, BizTalk Server peut transmettre des messages à des applications distantes en envoyant des requêtes HTTP POST à une URL HTTP spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a5785-107">Similarly, BizTalk Server can transmit messages to remote applications by sending HTTP POST requests to a specified HTTP URL.</span></span>  
  
 <span data-ttu-id="a5785-108">L'adaptateur HTTP est constitué de deux adaptateurs : un adaptateur de réception et un adaptateur d'envoi.</span><span class="sxs-lookup"><span data-stu-id="a5785-108">The HTTP adapter consists of two adapters—a receive adapter and a send adapter.</span></span> <span data-ttu-id="a5785-109">L'adaptateur de réception HTTP est une extension ISAPI (Internet Server Application Programming Interface) de Microsoft Internet Information Services (IIS) que le processus IIS héberge, et qui contrôle les emplacements de réception qui utilisent l'adaptateur HTTP.</span><span class="sxs-lookup"><span data-stu-id="a5785-109">The HTTP receive adapter is a Microsoft Internet Information Services (IIS) Internet Server Application Programming Interface (ISAPI) extension that the IIS process hosts, and controls the receive locations that use the HTTP adapter.</span></span> <span data-ttu-id="a5785-110">L'adaptateur d'envoi HTTP contrôle les ports d'envoi qui utilisent l'adaptateur HTTP.</span><span class="sxs-lookup"><span data-stu-id="a5785-110">The HTTP send adapter controls the send ports that use the HTTP adapter.</span></span>  
  
 <span data-ttu-id="a5785-111">Cette section décrit la prise en charge des workflows et traitements par lot pour les adaptateurs de réception et d'envoi HTTP.</span><span class="sxs-lookup"><span data-stu-id="a5785-111">This section discusses the workflow and batching support for both the HTTP receive adapter and the HTTP send adapter.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a5785-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a5785-112">In This Section</span></span>  
  
-   [<span data-ttu-id="a5785-113">Adaptateur de réception HTTP</span><span class="sxs-lookup"><span data-stu-id="a5785-113">HTTP Receive Adapter</span></span>](../core/http-receive-adapter.md)  
  
-   [<span data-ttu-id="a5785-114">Adaptateur d’envoi HTTP</span><span class="sxs-lookup"><span data-stu-id="a5785-114">HTTP Send Adapter</span></span>](../core/http-send-adapter.md)  
  
-   [<span data-ttu-id="a5785-115">Configuration de l’adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="a5785-115">Configuring the HTTP Adapter</span></span>](../core/configuring-the-http-adapter.md)  
  
-   [<span data-ttu-id="a5785-116">Recommandations de sécurité de l’adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="a5785-116">HTTP Adapter Security Recommendations</span></span>](../core/http-adapter-security-recommendations.md)