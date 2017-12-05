---
title: "Publication à partir de la Console Administration de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b78b1981-b227-4cf5-9435-6fc57963552a
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fbe03b1a8df67581ce73db31cd5ed4b80b7a109c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="publishing-from-the-biztalk-server-administration-console"></a><span data-ttu-id="a38b3-102">Publication à partir de la Console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="a38b3-102">Publishing from the BizTalk Server Administration Console</span></span>
<span data-ttu-id="a38b3-103">Si vous souhaitez gérer le point de terminaison de publication via la Console Administration de BizTalk Server au lieu du portail de gestion ESB, vous pouvez le faire en entrant un moniker Universal Description, Discovery and Integration (UDDI) dans le champ de description des points de terminaison Pour publier dans UDDI.</span><span class="sxs-lookup"><span data-stu-id="a38b3-103">If you want to manage endpoint publishing through the BizTalk Server Administration Console instead of the ESB Management Portal, you can do so by entering a Universal Description, Discovery, and Integration (UDDI) moniker in the description field of the endpoints to publish to UDDI.</span></span> <span data-ttu-id="a38b3-104">Voici un moniker de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="a38b3-104">The following is an example moniker.</span></span>  
  
```  
uddi://TransportType=other;Status=Published.  
```  
  
 <span data-ttu-id="a38b3-105">Vous pouvez définir les propriétés suivantes de UDDI à l’aide de la **Description** champ dans la Console Administration de BizTalk Server :</span><span class="sxs-lookup"><span data-stu-id="a38b3-105">You can set the following UDDI properties using the **Description** field in the BizTalk Server Administration Console:</span></span>  
  
-   <span data-ttu-id="a38b3-106">**ModifiedBy**.</span><span class="sxs-lookup"><span data-stu-id="a38b3-106">**ModifiedBy**.</span></span> <span data-ttu-id="a38b3-107">Cette propriété facultative comporte le nom du compte d’utilisateur qui a modifié le point de terminaison ; par exemple, MyDomainName\MyUserName.</span><span class="sxs-lookup"><span data-stu-id="a38b3-107">This optional property contains the account name of the user that modified the endpoint; for example, MyDomainName\MyUserName.</span></span>  
  
-   <span data-ttu-id="a38b3-108">**UDDIContact**.</span><span class="sxs-lookup"><span data-stu-id="a38b3-108">**UDDIContact**.</span></span> <span data-ttu-id="a38b3-109">Cette propriété facultative est le nom du contact de l’utilisateur défini pour le fournisseur d’entreprise UDDI.</span><span class="sxs-lookup"><span data-stu-id="a38b3-109">This optional property is the contact name of the user defined for the UDDI Business Provider.</span></span>  
  
-   <span data-ttu-id="a38b3-110">**UDDIUserType**.</span><span class="sxs-lookup"><span data-stu-id="a38b3-110">**UDDIUserType**.</span></span> <span data-ttu-id="a38b3-111">Cette propriété facultative est le type d’utilisateur de l’utilisateur défini pour le fournisseur d’entreprise UDDI.</span><span class="sxs-lookup"><span data-stu-id="a38b3-111">This optional property is the user type of the user defined for the UDDI Business Provider.</span></span>  
  
-   <span data-ttu-id="a38b3-112">**UDDIEmail**.</span><span class="sxs-lookup"><span data-stu-id="a38b3-112">**UDDIEmail**.</span></span> <span data-ttu-id="a38b3-113">Cette propriété facultative est l’adresse de messagerie de l’utilisateur défini pour le fournisseur d’entreprise UDDI.</span><span class="sxs-lookup"><span data-stu-id="a38b3-113">This optional property is the e-mail address of the user defined for the UDDI Business Provider.</span></span>  
  
-   <span data-ttu-id="a38b3-114">**Type de transport**.</span><span class="sxs-lookup"><span data-stu-id="a38b3-114">**TransportType**.</span></span> <span data-ttu-id="a38b3-115">Cette propriété facultative est le type de carte de point de terminaison, tel que **fichier MQS, WCF-WsHttp, SOAP, HTTP,** ou **FTP**.</span><span class="sxs-lookup"><span data-stu-id="a38b3-115">This optional property is the endpoint adapter type, such as **FILE, MQS, WCF-WsHttp, SOAP, HTTP,** or **FTP**.</span></span>  
  
-   <span data-ttu-id="a38b3-116">**État**.</span><span class="sxs-lookup"><span data-stu-id="a38b3-116">**Status**.</span></span> <span data-ttu-id="a38b3-117">Cette propriété facultative est l’état du point de terminaison, tel que **publié** ou **en attente**.</span><span class="sxs-lookup"><span data-stu-id="a38b3-117">This optional property is the status of the endpoint, such as **Published** or **Pending**.</span></span> <span data-ttu-id="a38b3-118">Le Service de publication UDDI utilise cet attribut pour détecter l’état du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a38b3-118">The UDDI Publishing Service uses this attribute to discover the status of the endpoint.</span></span>  
  
-   <span data-ttu-id="a38b3-119">**BindingType**.</span><span class="sxs-lookup"><span data-stu-id="a38b3-119">**BindingType**.</span></span> <span data-ttu-id="a38b3-120">Cette propriété facultative est le protocole spécifique (Type d’URL) prenant en charge la liaison UDDI, tel que **mailto, http, https, ftp, fax, téléphone,** ou **autres**.</span><span class="sxs-lookup"><span data-stu-id="a38b3-120">This optional property is the specific protocol (URL Type) that the UDDI binding supports, such as **mailto, http, https, ftp, fax, phone,** or **other**.</span></span> <span data-ttu-id="a38b3-121">Le Service de publication UDDI utilise cet attribut pour créer la liaison de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a38b3-121">The UDDI Publishing Service uses this attribute to create the endpoint binding.</span></span>