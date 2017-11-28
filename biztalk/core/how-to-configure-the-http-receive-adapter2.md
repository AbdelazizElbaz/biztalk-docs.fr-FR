---
title: "Configurer la réception HTTP 2 | Documents Microsoft"
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
ms.assetid: dd26fd57-90d8-4ffe-b56f-8de55ecc6f68
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed6e40036308aa872a2d6ba23da8209ee9f80cfc
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-configure-the-http-receive-adapter"></a><span data-ttu-id="6e3ff-102">Comment faire pour configurer l’adaptateur de réception HTTP</span><span class="sxs-lookup"><span data-stu-id="6e3ff-102">How to Configure the HTTP Receive Adapter</span></span>
<span data-ttu-id="6e3ff-103">Vous pouvez utiliser l'adaptateur de réception HTTP pour envoyer les messages à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="6e3ff-103">You can use the HTTP receive adapter to submit messages to BizTalk Server.</span></span> <span data-ttu-id="6e3ff-104">Cet adaptateur est une extension ISAPI IIS (Internet Information Services) hébergée dans le processus IIS.</span><span class="sxs-lookup"><span data-stu-id="6e3ff-104">The HTTP receive adapter is an Internet Information Services (IIS) ISAPI extension that is hosted in the IIS process.</span></span>  
  
### <a name="to-configure-the-http-receive-adapter"></a><span data-ttu-id="6e3ff-105">Pour configurer l'adaptateur de réception HTTP</span><span class="sxs-lookup"><span data-stu-id="6e3ff-105">To configure the HTTP receive adapter</span></span>  
  
1.  <span data-ttu-id="6e3ff-106">Copiez la réception HTTP (BTSHTTPReceive.dll) de l’adaptateur à partir de  **\<BizTalk2010 > \HttpReceive >** au dossier contenant votre projet Single Sign-On (SSO) (par exemple, **< Adapter_install > \ biztalk2010\SSO\mySSODemo**).</span><span class="sxs-lookup"><span data-stu-id="6e3ff-106">Copy the HTTP receive adapter (BTSHTTPReceive.dll) from **\<BizTalk2010>\HttpReceive>** to the folder containing your Single Sign-On (SSO) project (for example, **<Adapter_install>\biztalk2010\SSO\mySSODemo**).</span></span>  
  
    1.  <span data-ttu-id="6e3ff-107">Ajoutez une nouvelle extension de service Web mySSODemo.</span><span class="sxs-lookup"><span data-stu-id="6e3ff-107">Add a new Web service extension mySSODemo.</span></span>  
  
    2.  <span data-ttu-id="6e3ff-108">Accédez au fichier <BizTalk_install>\HttpReceive et copiez-le dans le dossier contenant votre projet d'authentification unique (par exemple,</span><span class="sxs-lookup"><span data-stu-id="6e3ff-108">Browse to and copy <BizTalk_install>\HttpReceive to the folder containing your SSO project, for example,</span></span>  
  
         <span data-ttu-id="6e3ff-109"><Installation_adaptateur>\biztalk2010\SSO\mySSODemo\BTSHTTPReceive.dll.</span><span class="sxs-lookup"><span data-stu-id="6e3ff-109"><Adapter_install>\biztalk2010\SSO\mySSODemo\BTSHTTPReceive.dll.</span></span>  
  
    3.  <span data-ttu-id="6e3ff-110">Définir le statut de l’extension du service Web mySSODemo à **autorisées**.</span><span class="sxs-lookup"><span data-stu-id="6e3ff-110">Set status of mySSODemo Web service extension to **Allowed**.</span></span>  
  
2.  <span data-ttu-id="6e3ff-111">Redémarrez IIS pour que ces modifications prennent effet.</span><span class="sxs-lookup"><span data-stu-id="6e3ff-111">Restart IIS to ensure that all changes are in effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e3ff-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e3ff-112">See Also</span></span>  
 [<span data-ttu-id="6e3ff-113">Sécurité de la carte</span><span class="sxs-lookup"><span data-stu-id="6e3ff-113">Security in the adapter</span></span>](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)