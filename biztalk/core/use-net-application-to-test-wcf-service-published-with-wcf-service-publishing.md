---
title: "Comment créer une Application .NET pour tester un Service WCF publié avec l’Assistant Publication de services WCF BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF services, .NET applications
- WCF services, WCF Service Publishing Wizard
- creating, .NET applications [WCF services]
- WCF Service Publishing Wizard
ms.assetid: 17e39db2-8471-4f6f-a7f1-833023cdbc39
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb46847361127a915d06ee74eaed549caf40258a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-net-application-to-test-a-wcf-service-published-with-the-biztalk-wcf-service-publishing-wizard"></a><span data-ttu-id="f7802-102">Procédure pour créer une application .NET afin de tester un service WCF publié à l'aide de l'Assistant Publication de services WCF BizTalk</span><span class="sxs-lookup"><span data-stu-id="f7802-102">How to Create a .NET Application to Test a WCF Service Published with the BizTalk WCF Service Publishing Wizard</span></span>
<span data-ttu-id="f7802-103">Pour tester un service WCF publié, vous pouvez créer une application .NET qui va utiliser celui-ci.</span><span class="sxs-lookup"><span data-stu-id="f7802-103">To test your published WCF service, you can create a .NET application that consumes your published WCF service.</span></span> <span data-ttu-id="f7802-104">Cette rubrique décrit la création d'une application .NET pour tester un service WCF publié.</span><span class="sxs-lookup"><span data-stu-id="f7802-104">This topic describes how to create a .NET application to test a published WCF service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7802-105">La collection d'aide Visual Studio inclut une procédure de création d'une application .NET utilisant les services WCF,</span><span class="sxs-lookup"><span data-stu-id="f7802-105">The Visual Studio Help Collection contains a valuable walkthrough for creating a .NET application that consumes WCF services.</span></span> <span data-ttu-id="f7802-106">qui permet de tester un service WCF publié.</span><span class="sxs-lookup"><span data-stu-id="f7802-106">You can use the walkthrough to test your published WCF service.</span></span> <span data-ttu-id="f7802-107">Pour plus d’informations et des procédures sur la création d’un projet de client WCF, consultez « Procédure pas à pas : accès à un XML Web Service à l’aide de Visual Basic ou Visual c# » dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Collection d’aide à [http://go.microsoft.com/fwlink/?LinkId=62263](http://go.microsoft.com/fwlink/?LinkId=62263).</span><span class="sxs-lookup"><span data-stu-id="f7802-107">For information and procedures about creating a WCF client project, see "Walkthrough: Accessing an XML Web Service Using Visual Basic or Visual C#" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Help Collection at [http://go.microsoft.com/fwlink/?LinkId=62263](http://go.microsoft.com/fwlink/?LinkId=62263).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7802-108">Cette rubrique utilise l'outil Service Model Metadata Utility (SvcUtil.exe) pour créer les classes de proxy WCF et le fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="f7802-108">This topic uses the Service Model Metadata Utility tool (SvcUtil.exe) to create the WCF proxy classes and application configuration file.</span></span> <span data-ttu-id="f7802-109">SvcUtil.exe est inclus dans le Kit de développement logiciel Microsoft Windows de Windows Vista et dans les composants d'exécution .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f7802-109">SvcUtil.exe is included in the Microsoft Windows Software Development Kit (SDK) of Windows Vista and .NET Framework Runtime Components.</span></span>  
  
### <a name="to-create-a-simple-wcf-proxy-class-and-application-configuration-file"></a><span data-ttu-id="f7802-110">Pour créer une classe de proxy WCF simple et un fichier de configuration de l'application</span><span class="sxs-lookup"><span data-stu-id="f7802-110">To create a simple WCF proxy class and application configuration file</span></span>  
  
1.  <span data-ttu-id="f7802-111">Ouvrez l’interface de commande comme suit : cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Windows SDK**, puis cliquez sur **CMD Shell**.</span><span class="sxs-lookup"><span data-stu-id="f7802-111">Open CMD Shell as follows: click **Start**, point to **All Programs**, point to **Microsoft Windows SDK**, and then click **CMD Shell**.</span></span>  
  
2.  <span data-ttu-id="f7802-112">Dans l'interface de commande, accédez au répertoire où vous souhaitez placer la classe de proxy et le fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="f7802-112">In CMD Shell, go to the directory where you want to place the proxy class and application configuration file.</span></span>  
  
3.  <span data-ttu-id="f7802-113">Dans l'interface de commande, exécutez l'outil Service Model Metadata Utility (SvcUtil.exe) pour créer la classe de proxy WCF et le fichier de configuration de l'application pour le service WCF publié comme suit :</span><span class="sxs-lookup"><span data-stu-id="f7802-113">In CMD Shell, run the ServiceModel Metadata Utility Tool (SvcUtil.exe) to create the WCF proxy class and application configuration file for the published WCF service as follows:</span></span>  
  
    ```  
    svcutil <http://servername/apppath/wcfservicename.svc> /config:App.config  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="f7802-114">Cette ligne de commande génère BizTalkServiceInstance.cs pour la classe de proxy et App.config pour la configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="f7802-114">This command line generates BizTalkServiceInstance.cs for the proxy class and App.config for the application configuration.</span></span> <span data-ttu-id="f7802-115">Pour plus d’informations sur Svcutil.exe, consultez « Service Model Metadata utilitaire Tool (Svcutil.exe) » à [http://go.microsoft.com/fwlink/?LinkId=74696](http://go.microsoft.com/fwlink/?LinkId=74696).</span><span class="sxs-lookup"><span data-stu-id="f7802-115">For more information about Svcutil.exe, see "Service Model Metadata Utility Tool (Svcutil.exe)" at [http://go.microsoft.com/fwlink/?LinkId=74696](http://go.microsoft.com/fwlink/?LinkId=74696).</span></span>  
  
### <a name="to-compile-your-net-application-that-consumes-the-published-wcf-service"></a><span data-ttu-id="f7802-116">Pour compiler votre application .NET utilisant le service WCF publié</span><span class="sxs-lookup"><span data-stu-id="f7802-116">To compile your .NET application that consumes the published WCF service</span></span>  
  
1.  <span data-ttu-id="f7802-117">Dans l'Explorateur de solutions [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ajoutez à votre projet les fichiers créés par SvcUtil.exe, BizTalkServiceInstance et App.config.</span><span class="sxs-lookup"><span data-stu-id="f7802-117">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, add the files that SvcUtil.exe creates, BizTalkServiceInstance and App.config, to your project.</span></span>  
  
2.  <span data-ttu-id="f7802-118">Dans l'Explorateur de solutions [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], veillez à ajouter une référence vers System.ServiceModel.dll pour la compilation du code proxy.</span><span class="sxs-lookup"><span data-stu-id="f7802-118">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, make sure to add a reference to the System.ServiceModel.dll to compile the proxy code.</span></span>  
  
3.  <span data-ttu-id="f7802-119">Créez le code pour utiliser le code proxy généré.</span><span class="sxs-lookup"><span data-stu-id="f7802-119">Create the code to use the generated proxy code.</span></span> <span data-ttu-id="f7802-120">Le code suivant présente l'utilisation du proxy généré :</span><span class="sxs-lookup"><span data-stu-id="f7802-120">The following code shows how to use the generated proxy:</span></span>  
  
    ```  
    DeliveryNotification deliveryNotification= new DeliveryNotification();  
    deliveryNotification.TrackingNumber = "001";  
                Microsoft_Samples_BizTalk_WCFBasicHttp_BizTalkApp_DliveryRequestProcess_DeliveryNotificatonReceivePortClient service = new Microsoft_Samples_BizTalk_WCFBasicHttp_BizTalkApp_DliveryRequestProcess_DeliveryNotificatonReceivePortClient("BasicHttpBinding_ITwoWayAsyncVoid");  
    service.Submit(deliveryNotification);  
    ```  
  
4.  <span data-ttu-id="f7802-121">Exécutez votre application .NET pour envoyer des messages vers le service WCF publié.</span><span class="sxs-lookup"><span data-stu-id="f7802-121">Run your .NET application to send messages to the published WCF service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7802-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7802-122">See Also</span></span>  
 [<span data-ttu-id="f7802-123">Considérations relatives à la publication de Services WCF avec WCF des adaptateurs de réception</span><span class="sxs-lookup"><span data-stu-id="f7802-123">Considerations When Publishing WCF Services with the WCF Receive Adapters</span></span>](../core/considerations-when-publishing-wcf-services-with-the-wcf-receive-adapters.md)