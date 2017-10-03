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
# <a name="how-to-create-a-net-application-to-test-a-wcf-service-published-with-the-biztalk-wcf-service-publishing-wizard"></a>Procédure pour créer une application .NET afin de tester un service WCF publié à l'aide de l'Assistant Publication de services WCF BizTalk
Pour tester un service WCF publié, vous pouvez créer une application .NET qui va utiliser celui-ci. Cette rubrique décrit la création d'une application .NET pour tester un service WCF publié.  
  
> [!NOTE]
>  La collection d'aide Visual Studio inclut une procédure de création d'une application .NET utilisant les services WCF, qui permet de tester un service WCF publié. Pour plus d’informations et des procédures sur la création d’un projet de client WCF, consultez « Procédure pas à pas : accès à un XML Web Service à l’aide de Visual Basic ou Visual c# » dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Collection d’aide à [http://go.microsoft.com/fwlink/?LinkId=62263](http://go.microsoft.com/fwlink/?LinkId=62263).  
  
> [!NOTE]
>  Cette rubrique utilise l'outil Service Model Metadata Utility (SvcUtil.exe) pour créer les classes de proxy WCF et le fichier de configuration de l'application. SvcUtil.exe est inclus dans le Kit de développement logiciel Microsoft Windows de Windows Vista et dans les composants d'exécution .NET Framework.  
  
### <a name="to-create-a-simple-wcf-proxy-class-and-application-configuration-file"></a>Pour créer une classe de proxy WCF simple et un fichier de configuration de l'application  
  
1.  Ouvrez l’interface de commande comme suit : cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Windows SDK**, puis cliquez sur **CMD Shell**.  
  
2.  Dans l'interface de commande, accédez au répertoire où vous souhaitez placer la classe de proxy et le fichier de configuration de l'application.  
  
3.  Dans l'interface de commande, exécutez l'outil Service Model Metadata Utility (SvcUtil.exe) pour créer la classe de proxy WCF et le fichier de configuration de l'application pour le service WCF publié comme suit :  
  
    ```  
    svcutil <http://servername/apppath/wcfservicename.svc> /config:App.config  
    ```  
  
    > [!NOTE]
    >  Cette ligne de commande génère BizTalkServiceInstance.cs pour la classe de proxy et App.config pour la configuration de l'application. Pour plus d’informations sur Svcutil.exe, consultez « Service Model Metadata utilitaire Tool (Svcutil.exe) » à [http://go.microsoft.com/fwlink/?LinkId=74696](http://go.microsoft.com/fwlink/?LinkId=74696).  
  
### <a name="to-compile-your-net-application-that-consumes-the-published-wcf-service"></a>Pour compiler votre application .NET utilisant le service WCF publié  
  
1.  Dans l'Explorateur de solutions [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ajoutez à votre projet les fichiers créés par SvcUtil.exe, BizTalkServiceInstance et App.config.  
  
2.  Dans l'Explorateur de solutions [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], veillez à ajouter une référence vers System.ServiceModel.dll pour la compilation du code proxy.  
  
3.  Créez le code pour utiliser le code proxy généré. Le code suivant présente l'utilisation du proxy généré :  
  
    ```  
    DeliveryNotification deliveryNotification= new DeliveryNotification();  
    deliveryNotification.TrackingNumber = "001";  
                Microsoft_Samples_BizTalk_WCFBasicHttp_BizTalkApp_DliveryRequestProcess_DeliveryNotificatonReceivePortClient service = new Microsoft_Samples_BizTalk_WCFBasicHttp_BizTalkApp_DliveryRequestProcess_DeliveryNotificatonReceivePortClient("BasicHttpBinding_ITwoWayAsyncVoid");  
    service.Submit(deliveryNotification);  
    ```  
  
4.  Exécutez votre application .NET pour envoyer des messages vers le service WCF publié.  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations relatives à la publication de Services WCF avec WCF des adaptateurs de réception](../core/considerations-when-publishing-wcf-services-with-the-wcf-receive-adapters.md)