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
ms.openlocfilehash: 313bfb773a94914ed9bebd3930dfd0033ecf4ac3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="publishing-from-the-biztalk-server-administration-console"></a><span data-ttu-id="38437-102">Publication à partir de la Console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="38437-102">Publishing from the BizTalk Server Administration Console</span></span>
<span data-ttu-id="38437-103">Si vous souhaitez gérer la publication de point de terminaison via la [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration au lieu du portail de gestion ESB, vous pouvez le faire en entrant un moniker Universal Description, Discovery and Integration (UDDI) dans le champ de description de la points de terminaison à la publication dans UDDI.</span><span class="sxs-lookup"><span data-stu-id="38437-103">If you want to manage endpoint publishing through the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console instead of the ESB Management Portal, you can do so by entering a Universal Description, Discovery, and Integration (UDDI) moniker in the description field of the endpoints to publish to UDDI.</span></span> <span data-ttu-id="38437-104">Voici un moniker de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="38437-104">The following is an example moniker.</span></span>  
  
```  
uddi://TransportType=other;Status=Published.  
```  
  
 <span data-ttu-id="38437-105">Vous pouvez définir les propriétés suivantes de UDDI à l’aide de la **Description** champ dans le [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration :</span><span class="sxs-lookup"><span data-stu-id="38437-105">You can set the following UDDI properties using the **Description** field in the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console:</span></span>  
  
-   <span data-ttu-id="38437-106">**ModifiedBy**.</span><span class="sxs-lookup"><span data-stu-id="38437-106">**ModifiedBy**.</span></span> <span data-ttu-id="38437-107">Cette propriété facultative comporte le nom du compte d’utilisateur qui a modifié le point de terminaison ; par exemple, MyDomainName\MyUserName.</span><span class="sxs-lookup"><span data-stu-id="38437-107">This optional property contains the account name of the user that modified the endpoint; for example, MyDomainName\MyUserName.</span></span>  
  
-   <span data-ttu-id="38437-108">**UDDIContact**.</span><span class="sxs-lookup"><span data-stu-id="38437-108">**UDDIContact**.</span></span> <span data-ttu-id="38437-109">Cette propriété facultative est le nom du contact de l’utilisateur défini pour le fournisseur d’entreprise UDDI.</span><span class="sxs-lookup"><span data-stu-id="38437-109">This optional property is the contact name of the user defined for the UDDI Business Provider.</span></span>  
  
-   <span data-ttu-id="38437-110">**UDDIUserType**.</span><span class="sxs-lookup"><span data-stu-id="38437-110">**UDDIUserType**.</span></span> <span data-ttu-id="38437-111">Cette propriété facultative est le type d’utilisateur de l’utilisateur défini pour le fournisseur d’entreprise UDDI.</span><span class="sxs-lookup"><span data-stu-id="38437-111">This optional property is the user type of the user defined for the UDDI Business Provider.</span></span>  
  
-   <span data-ttu-id="38437-112">**UDDIEmail**.</span><span class="sxs-lookup"><span data-stu-id="38437-112">**UDDIEmail**.</span></span> <span data-ttu-id="38437-113">Cette propriété facultative est l’adresse de messagerie de l’utilisateur défini pour le fournisseur d’entreprise UDDI.</span><span class="sxs-lookup"><span data-stu-id="38437-113">This optional property is the e-mail address of the user defined for the UDDI Business Provider.</span></span>  
  
-   <span data-ttu-id="38437-114">**Type de transport**.</span><span class="sxs-lookup"><span data-stu-id="38437-114">**TransportType**.</span></span> <span data-ttu-id="38437-115">Cette propriété facultative est le type de carte de point de terminaison, tel que **fichier MQS, WCF-WsHttp, SOAP, HTTP,** ou **FTP**.</span><span class="sxs-lookup"><span data-stu-id="38437-115">This optional property is the endpoint adapter type, such as **FILE, MQS, WCF-WsHttp, SOAP, HTTP,** or **FTP**.</span></span>  
  
-   <span data-ttu-id="38437-116">**État**.</span><span class="sxs-lookup"><span data-stu-id="38437-116">**Status**.</span></span> <span data-ttu-id="38437-117">Cette propriété facultative est l’état du point de terminaison, tel que **publié** ou **en attente**.</span><span class="sxs-lookup"><span data-stu-id="38437-117">This optional property is the status of the endpoint, such as **Published** or **Pending**.</span></span> <span data-ttu-id="38437-118">Le Service de publication UDDI utilise cet attribut pour détecter l’état du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="38437-118">The UDDI Publishing Service uses this attribute to discover the status of the endpoint.</span></span>  
  
-   <span data-ttu-id="38437-119">**BindingType**.</span><span class="sxs-lookup"><span data-stu-id="38437-119">**BindingType**.</span></span> <span data-ttu-id="38437-120">Cette propriété facultative est le protocole spécifique (Type d’URL) prenant en charge la liaison UDDI, tel que **mailto, http, https, ftp, fax, téléphone,** ou **autres**.</span><span class="sxs-lookup"><span data-stu-id="38437-120">This optional property is the specific protocol (URL Type) that the UDDI binding supports, such as **mailto, http, https, ftp, fax, phone,** or **other**.</span></span> <span data-ttu-id="38437-121">Le Service de publication UDDI utilise cet attribut pour créer la liaison de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="38437-121">The UDDI Publishing Service uses this attribute to create the endpoint binding.</span></span>