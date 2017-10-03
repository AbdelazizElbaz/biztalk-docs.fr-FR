---
title: "Création d’envoi et Ports de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards OneWorld adapters, receive ports
- adapters [JD Edwards OneWorld adapters], receive ports
- creating, receive ports [JD Edwards OneWorld adapters]
- send ports, creating [JD Edwards OneWorld adapters]
- adapters [JD Edwards OneWorld adapters], send ports
- adapters [JD Edwards OneWorld adapters], transport properties
- JD Edwards OneWorld adapters, send ports
- JD Edwards OneWorld adapters, transport properties
- receive ports, creating [JD Edwards OneWorld adapters]
- creating, send ports [JD Edwards OneWorld adapters]
ms.assetid: fb4ca8b1-40d9-4beb-a791-554086f8ca98
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 217a1d79dc4079c8f092985e00a1cd5636788e7b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-send-and-receive-ports"></a>Création d’envoi et Ports de réception
Les procédures suivantes permettent de créer des ports d'envoi et de réception [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour l'adaptateur Microsoft BizTalk pour JD Edwards OneWorld.  
  
## <a name="creating-a-port"></a>Création d'un port  
  
#### <a name="to-create-a-send-port"></a>Pour créer un port d’envoi  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk Server**, puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez le application pour laquelle vous souhaitez créer un port d’envoi.  
  
3.  Avec le bouton droit **Ports d’envoi** et cliquez sur **nouveau**, puis cliquez sur **Port statique avec sollicitation-réponse**.  
  
4.  Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :  
  
    -   Dans le **nom** , tapez le nom du port d’envoi (par exemple, `SSOSendToJDE OneWorld`).  
  
    -   À partir de la **Type** la liste déroulante, sélectionnez **JDEdwards**.  
  
    -   À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’adresse du Gestionnaire d’envoi.  
  
    -   Pour le **Pipeline d’envoi**, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.  
  
    -   Pour le **Pipeline de réception**, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.  
  
5.  Cliquez sur **OK**.  
  
## <a name="creating-a-receive-port"></a>Création d'un port de réception  
  
#### <a name="to-create-a-receive-port"></a>Pour créer un port de réception  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk Server**, puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez le application pour laquelle vous souhaitez créer un port d’envoi.  
  
3.  Avec le bouton droit **Ports de réception** et cliquez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.  
  
     Sur le **propriétés du Port de réception unidirectionnel** écran, dans le **nom** , tapez `ReceiveFromHttp`, puis cliquez sur **OK**.  
  
4.  Entrez les informations suivantes dans le **propriétés du Port de réception unidirectionnel** fenêtre :  
  
    -   Dans le **nom** , tapez `ReceiveFromHTTP`.  
  
    -   Pour le **Type de Transport**, sélectionnez **HTTP**.  
  
5.  Cliquez sur le bouton représentant des points de suspension (...) dans l'adresse (URI).  
  
     ![](../core/media/siebeladapter-32-ssodemo-httptransport.gif "SiebelAdapter_32_SSODemo_HTTPTransport")  
  
    1.  Définissez le répertoire virtuel assorti de l'extension ISAPI, /mySSODemo/BTSHTTPReceive.dll.  
  
    2.  Sélectionnez **un descripteur de corrélation de retour en cas de réussite**.  
  
    3.  Sélectionnez **utilisez Single Sign-On**, puis cliquez sur **OK**.  
  
6.  Dans le **Gestionnaire de réception** la liste déroulante, sélectionnez **BizTalkServerIsolatedHost**.  
  
     ![](../core/media/siebeladapter-33-ssodemo-receivelocationproperty.gif "SiebelAdapter_33_SSODemo_ReceiveLocationProperty")  
  
7.  Pour le **Pipeline de réception**, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de gestionnaires de JD Edwards OneWorld envoi](../core/creating-jd-edwards-oneworld-send-handlers.md)   
 [Comment définir les propriétés de JD Edwards OneWorld Transport](../core/how-to-set-jd-edwards-oneworld-transport-properties.md)   
 [À l’aide de l’authentification unique](../core/using-single-sign-on3.md)