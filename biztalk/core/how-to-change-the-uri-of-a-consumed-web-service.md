---
title: "Comment modifier l’URI d’un Service Web utilisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services, modifying
- Web services, consuming
- consuming [Web services]
- modifying, Web services
ms.assetid: 907de565-8c99-4d34-939f-fd3dba37dd11
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b9ae7d7178fc24c5f16b28325fb627045e5273a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-change-the-uri-of-a-consumed-web-service"></a><span data-ttu-id="3a59a-102">Modification de l'URI d'un service web utilisé</span><span class="sxs-lookup"><span data-stu-id="3a59a-102">How to Change the URI of a Consumed Web Service</span></span>
<span data-ttu-id="3a59a-103">Suite au déploiement de votre orchestration, BizTalk Server configure un port d'envoi pour chaque service Web qu'elle référence.</span><span class="sxs-lookup"><span data-stu-id="3a59a-103">After you deploy your orchestration, BizTalk Server configures a send port for each Web service that the orchestration references.</span></span> <span data-ttu-id="3a59a-104">Par défaut, BizTalk utilise l'URL du service Web au moment de l'exécution pour la même URL associée au service Web importé.</span><span class="sxs-lookup"><span data-stu-id="3a59a-104">By default, BizTalk uses the URL of the Web service at run time for the same URL for the imported Web service.</span></span> <span data-ttu-id="3a59a-105">Vous pouvez modifier cette URL à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="3a59a-105">You can change this URL using BizTalk Server Administration console.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a59a-106">Vous devez déployer votre orchestration avant de modifier l'URI d'un service Web utilisé.</span><span class="sxs-lookup"><span data-stu-id="3a59a-106">You must deploy your orchestration before you change the URI of a consumed Web service.</span></span> <span data-ttu-id="3a59a-107">Pour plus d’informations sur le déploiement de l’orchestration, consultez [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="3a59a-107">For more information on deploying your orchestration, see [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span></span>  
  
### <a name="to-change-the-uri-of-a-consumed-web-service-using-biztalk-server-administration-console"></a><span data-ttu-id="3a59a-108">Pour modifier l'URI d'un service Web utilisé à l'aide de la console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="3a59a-108">To change the URI of a consumed Web service using BizTalk Server Administration Console</span></span>  
  
1.  <span data-ttu-id="3a59a-109">Dans la console Administration de BizTalk Server, développez une application BizTalk, puis développez le **Ports d’envoi** nœud.</span><span class="sxs-lookup"><span data-stu-id="3a59a-109">In BizTalk Server Administration console, expand a BizTalk application, and then expand the **Send Ports** node.</span></span>  
  
2.  <span data-ttu-id="3a59a-110">Sur un port d’envoi configuré avec l’adaptateur SOAP, cliquez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="3a59a-110">Right-click a send port configured with SOAP adapter, click **Properties**.</span></span>  
  
3.  <span data-ttu-id="3a59a-111">Si vous n’avez pas de ports physiques, vous pouvez créer des ports d’envoi et emplacements de réception à l’aide de la console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="3a59a-111">If you do not have physical ports, you can create send ports and receive locations by using BizTalk Administration console.</span></span> <span data-ttu-id="3a59a-112">Pour plus d’informations, consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md).</span><span class="sxs-lookup"><span data-stu-id="3a59a-112">For information, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md).</span></span>  
  
4.  <span data-ttu-id="3a59a-113">Sur le **propriétés d’envoi** boîte de dialogue, cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="3a59a-113">On the **Send Properties** dialog box, click **Configure**.</span></span>  
  
5.  <span data-ttu-id="3a59a-114">Dans le **propriétés du Transport SOAP** boîte de dialogue le **URL du Service Web** zone, tapez l’URL complète de l’emplacement du service Web, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3a59a-114">In the **SOAP Transport Properties** dialog box, in the **Web Service URL** box, type the full URL for the location of the Web service, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3a59a-115">Vous devez vous assurer qu'un service Web existe pour l'URL que vous avez spécifiée.</span><span class="sxs-lookup"><span data-stu-id="3a59a-115">You should ensure that a Web service exists for the URL that you specify.</span></span> <span data-ttu-id="3a59a-116">BizTalk Server ne valide pas l'adresse de l'URL.</span><span class="sxs-lookup"><span data-stu-id="3a59a-116">BizTalk Server does not validate the URL location.</span></span>  
  
6.  <span data-ttu-id="3a59a-117">Cliquez sur OK pour quitter le **propriétés d’envoi** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="3a59a-117">Click OK to exit the **Send Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a59a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a59a-118">See Also</span></span>  
 <span data-ttu-id="3a59a-119">[À l’aide de la Console Administration de BizTalk Server](../core/using-the-biztalk-server-administration-console.md) </span><span class="sxs-lookup"><span data-stu-id="3a59a-119">[Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md) </span></span>  
 <span data-ttu-id="3a59a-120">[Comment configurer un Port d’envoi SOAP](../core/how-to-configure-a-soap-send-port.md) </span><span class="sxs-lookup"><span data-stu-id="3a59a-120">[How to Configure a SOAP Send Port](../core/how-to-configure-a-soap-send-port.md) </span></span>  
 <span data-ttu-id="3a59a-121">[En-têtes SOAP avec les Services Web utilisés](../core/soap-headers-with-consumed-web-services.md) </span><span class="sxs-lookup"><span data-stu-id="3a59a-121">[SOAP Headers with Consumed Web Services](../core/soap-headers-with-consumed-web-services.md) </span></span>  
 [<span data-ttu-id="3a59a-122">Création de Ports Web</span><span class="sxs-lookup"><span data-stu-id="3a59a-122">Creating Web Ports</span></span>](../core/creating-web-ports.md)