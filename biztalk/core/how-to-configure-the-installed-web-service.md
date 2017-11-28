---
title: "Comment configurer le Service Web installé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services, configuring
- deploying, Web services
- Web services, deploying
ms.assetid: 5a281daa-9e1c-47b0-9002-66ea18ed6caf
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f54d5fd99bfa9f5a7440202848c4d43259d0a42
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-installed-web-service"></a><span data-ttu-id="670b3-102">Configuration du service Web installé</span><span class="sxs-lookup"><span data-stu-id="670b3-102">How to Configure the Installed Web Service</span></span>
<span data-ttu-id="670b3-103">Après avoir installé les fichiers du service Web, vous devez configurer BizTalk Server de sorte qu'il reçoive des messages en provenance du service Web.</span><span class="sxs-lookup"><span data-stu-id="670b3-103">After you install the Web service files, you must configure BizTalk Server to receive messages from the Web service.</span></span>  
  
### <a name="to-configure-the-web-service"></a><span data-ttu-id="670b3-104">Pour configurer le service Web</span><span class="sxs-lookup"><span data-stu-id="670b3-104">To configure the Web service</span></span>  
  
1.  <span data-ttu-id="670b3-105">Dans la console Administration de BizTalk Server, développez **groupe BizTalk**, développez **Applications**, puis cliquez sur l’application que vous souhaitez configurer le Service Web.</span><span class="sxs-lookup"><span data-stu-id="670b3-105">In BizTalk Server Administration console, expand **BizTalk Group**, expand **Applications**, and then right-click the application that you want to configure the Web Service.</span></span>  
  
2.  <span data-ttu-id="670b3-106">Pointez sur **importation**, puis cliquez sur **liaisons**.</span><span class="sxs-lookup"><span data-stu-id="670b3-106">Point to **Import**, and then click **Bindings**.</span></span>  
  
3.  <span data-ttu-id="670b3-107">Sélectionnez le fichier BindingInfo.xml dans le dossier de distribution, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="670b3-107">Select the BindingInfo.xml file in the distribution folder, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="670b3-108">Démarrez les orchestrations et activez les emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="670b3-108">Start your orchestrations and enable receive locations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="670b3-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="670b3-109">See Also</span></span>  
 <span data-ttu-id="670b3-110">[Comment importer des liaisons dans une Application BizTalk](../core/how-to-import-bindings-into-a-biztalk-application.md) </span><span class="sxs-lookup"><span data-stu-id="670b3-110">[How to Import Bindings into a BizTalk Application](../core/how-to-import-bindings-into-a-biztalk-application.md) </span></span>  
 [<span data-ttu-id="670b3-111">Déploiement de Services Web publiés sur un ordinateur Non-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="670b3-111">Deploying Published Web Services on a Non-Visual Studio Computer</span></span>](../core/deploying-published-web-services-on-a-non-visual-studio-computer.md)