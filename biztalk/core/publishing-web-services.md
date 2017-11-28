---
title: Publication de Services Web | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services, publishing
- BizTalk Server Web Services Publishing Wizard
ms.assetid: eed0717c-b390-492a-a3b9-ae31024805a2
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aca08c1e4fabd833bd6de924e04e6052cd99890b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="publishing-web-services"></a><span data-ttu-id="b73c6-102">Publication de Services Web</span><span class="sxs-lookup"><span data-stu-id="b73c6-102">Publishing Web Services</span></span>
<span data-ttu-id="b73c6-103">La publication des services Web permet de créer un service Web capable d'envoyer des messages vers Microsoft BizTalk Server qui peuvent être utilisés par les orchestrations et d'autres adaptateurs d'envoi.</span><span class="sxs-lookup"><span data-stu-id="b73c6-103">Publishing Web services enables you to create a Web service that can submit messages to Microsoft BizTalk Server for use by orchestrations and other send adapters.</span></span> <span data-ttu-id="b73c6-104">Les services Web publiés sont créés à l'aide de l'Assistant Publication de services Web BizTalk.</span><span class="sxs-lookup"><span data-stu-id="b73c6-104">You create published Web services using the BizTalk Web Services Publishing Wizard.</span></span> <span data-ttu-id="b73c6-105">Pour plus d’informations sur la configuration d’un gestionnaire d’envoi SOAP, consultez [comment configurer un gestionnaire d’envoi SOAP](../core/how-to-configure-a-soap-send-handler.md).</span><span class="sxs-lookup"><span data-stu-id="b73c6-105">For information about configuring a SOAP send handler, see [How to Configure a SOAP Send Handler](../core/how-to-configure-a-soap-send-handler.md).</span></span> <span data-ttu-id="b73c6-106">Pour plus d’informations sur la configuration d’un port d’envoi SOAP, consultez [comment configurer un Port d’envoi SOAP](../core/how-to-configure-a-soap-send-port.md).</span><span class="sxs-lookup"><span data-stu-id="b73c6-106">For information about configuring a SOAP send port, see [How to Configure a SOAP Send Port](../core/how-to-configure-a-soap-send-port.md).</span></span>  
  
 <span data-ttu-id="b73c6-107">L’Assistant de publication des Services Web BizTalk vous offre deux méthodes pour publier des services Web : publication d’une orchestration en tant que service Web et publication de schémas comme un service Web.</span><span class="sxs-lookup"><span data-stu-id="b73c6-107">The BizTalk Web Services Publishing Wizard provides you with two methods to publish Web services: publishing an orchestration as a Web service and publishing schemas as a Web service.</span></span>  
  
 <span data-ttu-id="b73c6-108">Vous devez préalablement installer et activer Microsoft Internet Information Services (IIS) et ASP.NET pour publier les orchestrations et schémas Microsoft BizTalk Server en tant que services Web.</span><span class="sxs-lookup"><span data-stu-id="b73c6-108">You must install and enable Microsoft Internet Information Services (IIS) and ASP.NET before you can publish Microsoft BizTalk Server orchestrations and schemas as Web services.</span></span> <span data-ttu-id="b73c6-109">Pour plus d’informations sur l’installation d’IIS et ASP.NET, consultez Installing Internet Information Services (IIS) dans le Guide d’Installation BizTalk Server situé [lien hypertexte « http://go.microsoft.com/fwlink/? LinkID = 191321" http://go.microsoft.com/fwlink/? LinkID = 191321](http://go.microsoft.com/fwlink/?LinkID=191321).</span><span class="sxs-lookup"><span data-stu-id="b73c6-109">For information about installing IIS and ASP.NET, see Installing Internet Information Services (IIS) in the BizTalk Server Installation Guide located at [HYPERLINK "http://go.microsoft.com/fwlink/?LinkID=191321" http://go.microsoft.com/fwlink/?LinkID=191321](http://go.microsoft.com/fwlink/?LinkID=191321).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b73c6-110">Avant d'exécuter l'Assistant Publication de services Web BizTalk, vous devez activer les services Web.</span><span class="sxs-lookup"><span data-stu-id="b73c6-110">Before running the BizTalk Web Services Publishing Wizard, you must enable Web services.</span></span> <span data-ttu-id="b73c6-111">Pour plus d’informations sur l’activation des services Web pour votre système, consultez [activation des Services Web](../core/enabling-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="b73c6-111">For more information about enabling Web services for your system, see [Enabling Web Services](../core/enabling-web-services.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b73c6-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b73c6-112">In This Section</span></span>  
  
-   [<span data-ttu-id="b73c6-113">Planification de la publication de Services Web</span><span class="sxs-lookup"><span data-stu-id="b73c6-113">Planning for Publishing Web Services</span></span>](../core/planning-for-publishing-web-services2.md)  
  
-   [<span data-ttu-id="b73c6-114">Activation des Services Web</span><span class="sxs-lookup"><span data-stu-id="b73c6-114">Enabling Web Services</span></span>](../core/enabling-web-services.md)  
  
-   [<span data-ttu-id="b73c6-115">Publication d’une Orchestration en tant que Service Web</span><span class="sxs-lookup"><span data-stu-id="b73c6-115">Publishing an Orchestration as a Web Service</span></span>](../core/publishing-an-orchestration-as-a-web-service.md)  
  
-   [<span data-ttu-id="b73c6-116">Publication de schémas comme un Service Web</span><span class="sxs-lookup"><span data-stu-id="b73c6-116">Publishing Schemas as a Web Service</span></span>](../core/publishing-schemas-as-a-web-service.md)  
  
-   [<span data-ttu-id="b73c6-117">Considérations relatives à la publication de Services Web</span><span class="sxs-lookup"><span data-stu-id="b73c6-117">Considerations When Publishing Web Services</span></span>](../core/considerations-when-publishing-web-services.md)  
  
-   [<span data-ttu-id="b73c6-118">Débogage de Services Web publiés</span><span class="sxs-lookup"><span data-stu-id="b73c6-118">Debugging Published Web Services</span></span>](../core/debugging-published-web-services.md)  
  
-   [<span data-ttu-id="b73c6-119">Test des Services Web publiés</span><span class="sxs-lookup"><span data-stu-id="b73c6-119">Testing Published Web Services</span></span>](../core/testing-published-web-services.md)  
  
-   [<span data-ttu-id="b73c6-120">Déploiement de Services Web publiés sur un ordinateur Non-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b73c6-120">Deploying Published Web Services on a Non-Visual Studio Computer</span></span>](../core/deploying-published-web-services-on-a-non-visual-studio-computer.md)