---
title: "Configurer la réception HTTP 1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP receive adapter, configuring
- configuring HTTP receive adapter
ms.assetid: e7dbfed3-9dd8-49c9-90b6-a655d7c5446f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed6907a96c3c961a4df7d076ba9307f44627bfa2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-http-receive-adapter"></a><span data-ttu-id="1daf8-102">Comment faire pour configurer l’adaptateur de réception HTTP</span><span class="sxs-lookup"><span data-stu-id="1daf8-102">How to Configure the HTTP Receive Adapter</span></span>
<span data-ttu-id="1daf8-103">L'adaptateur de réception HTTP permet d'envoyer des messages à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1daf8-103">You can use the HTTP receive adapter to submit messages to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="1daf8-104">Cet adaptateur est une extension ISAPI IIS (Internet Information Services) hébergée dans le processus IIS.</span><span class="sxs-lookup"><span data-stu-id="1daf8-104">The HTTP receive adapter is an Internet Information Services (IIS) ISAPI extension that is hosted in the IIS process.</span></span>  
  
### <a name="to-configure-the-http-receive-adapter"></a><span data-ttu-id="1daf8-105">Pour configurer l'adaptateur de réception HTTP</span><span class="sxs-lookup"><span data-stu-id="1daf8-105">To configure the HTTP receive adapter</span></span>  
  
1.  <span data-ttu-id="1daf8-106">Copiez la réception HTTP (BTSHTTPReceive.dll) de l’adaptateur à partir de ** \<BizTalk > \HttpReceive >** vers le dossier qui contient votre projet Single Sign-On (SSO), par exemple :</span><span class="sxs-lookup"><span data-stu-id="1daf8-106">Copy the HTTP receive adapter (BTSHTTPReceive.dll) from **\<BizTalk>\HttpReceive>** to the folder that contains your Single Sign-On (SSO) project, for example:</span></span>  
  
     <span data-ttu-id="1daf8-107">**< Adapter_install > \biztalk\SSO\mySSODemo**</span><span class="sxs-lookup"><span data-stu-id="1daf8-107">**<Adapter_install>\biztalk\SSO\mySSODemo**</span></span>  
  
    1.  <span data-ttu-id="1daf8-108">Ajoutez une nouvelle extension de service Web mySSODemo.</span><span class="sxs-lookup"><span data-stu-id="1daf8-108">Add a new Web service extension mySSODemo.</span></span>  
  
    2.  <span data-ttu-id="1daf8-109">Localisez et copiez **< BizTalk_install > \HttpReceive** dans le dossier qui contient votre projet d’authentification unique, par exemple :</span><span class="sxs-lookup"><span data-stu-id="1daf8-109">Locate and copy **<BizTalk_install>\HttpReceive** to the folder that contains your SSO project, for example:</span></span>  
  
         <span data-ttu-id="1daf8-110">**< Adapter_install > \biztalk\SSO\mySSODemo\BTSHTTPReceive.dll.**</span><span class="sxs-lookup"><span data-stu-id="1daf8-110">**<Adapter_install>\biztalk\SSO\mySSODemo\BTSHTTPReceive.dll.**</span></span>  
  
    3.  <span data-ttu-id="1daf8-111">Définir l’état de l’extension du service Web mySSODemo à **autorisées**.</span><span class="sxs-lookup"><span data-stu-id="1daf8-111">Set the status of mySSODemo Web service extension to **Allowed**.</span></span>  
  
2.  <span data-ttu-id="1daf8-112">Redémarrez IIS pour appliquer les modifications.</span><span class="sxs-lookup"><span data-stu-id="1daf8-112">Restart IIS to apply all changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1daf8-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1daf8-113">See Also</span></span>  
 [<span data-ttu-id="1daf8-114">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="1daf8-114">Using Single Sign-On</span></span>](../core/using-single-sign-on2.md)