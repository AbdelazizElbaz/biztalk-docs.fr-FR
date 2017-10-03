---
title: "Pour exécuter le Service Solution orientée services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service solution tutorial, client applications
- service solution tutorial, starting solution
- service solution tutorial, sending requests
- service solution tutorial, SOAP transports
ms.assetid: 764a5ddc-e571-41d8-9e2f-6d0fb3361b2f
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27462716832631fc2a36d577b39e3ff5431b858b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-run-the-service-oriented-solution"></a>Exécution de la solution orientée services
Les procédures suivantes décrivent l'exécution et la validation d'une solution orientée services sur un seul ordinateur. Après avoir démarré le simulateur Payment Tracker, vous pouvez envoyer des demandes à l'aide du transport SOAP ou MQSeries (par l'intermédiaire de procédures distinctes pour la version d'adaptateur et pour la version Inline de la solution orientée services).  
  
-   [Envoyer des demandes via le transport SOAP à l’aide de l’application cliente (version stub)](#step1)  
  
-   [Envoyer des demandes à l’aide de l’application cliente (version d’adaptateur)](#step3)  
  
-   [Envoyer des demandes à l’aide de l’application cliente (version inline)](#step5)  
  
##  <a name="step1"></a>Envoyer des demandes via le transport SOAP à l’aide de l’application cliente (version stub)  
  
#### <a name="to-send-requests-by-soap-transport-using-the-client-application-stub-version"></a>Pour envoyer des demandes via le transport SOAP à l'aide de l'application cliente (version stub)  
  
1.  Ouvrez une invite de commandes, accédez au répertoire du \< *répertoire d’installation de BizTalk Server*> \SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release, puis exécutez BTSScnSOSimpleClient.exe.  
  
2.  Tapez des caractères dans le **RequestType**, **RequestSource**, et **RequestID** zones de texte.  
  
3.  Tapez n’importe quel numéro à 16 chiffres dans le **numéro de compte** zone de texte.  
  
4.  Sélectionnez **SOAP (appel WS)** et **Stub** dans les **paramètres et sélectionnez le Transport** zone de groupe.  
  
5.  Tapez l’URL suivante dans le **URL** zone de texte, par exemple :  
  
6.  `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub/CustomerServicePort.asmx`  
  
7.  Type `ZipCode` dans les **nom** zone de texte sous **éléments d’authentification**, puis tapez des caractères dans le **valeur** zone de texte.  
  
8.  Type `CustomerName` dans les **nom** zone de texte sous **éléments d’authentification**, puis tapez des caractères dans le **valeur** zone de texte.  
  
9. Cliquez sur **obtenir le solde**.  
  
10. La réponse est affichée dans le **réponse** zone de texte : **réussite** s’affiche si la demande est traitée correctement ; un message d’erreur s’affiche si la demande échoue.  
  
     ![Exécutez l’application cliente pour la version stub](../core/media/bts-cp-so-deploy-stubversion-success.gif "BTS_CP_SO_Deploy_StubVersion_Success")  
  
##  <a name="step3"></a>Envoyer des demandes à l’aide de l’application cliente (version d’adaptateur)  
  
#### <a name="to-send-requests-using-the-client-application-adapter-version"></a>Pour envoyer des demandes à l'aide de l'application cliente (version d'adaptateur)  
  
1.  Ouvrez une invite de commandes, accédez au répertoire \< *répertoire d’installation de BizTalk Server*> \SDK\Scenarios\SO\BTSSoln\PaymentTracker\bin\Debug, puis exécutez la commande suivante pour démarrer le PaymentTracker Simulateur :  
  
     `BTSScnSOPaymentTracker.exe LastPaymentsInputQueue LastPaymentsOutputQueue <`*Nom du Gestionnaire de file d’attente* `> 5 [<` *définition de canal*`>]`  
  
    > [!NOTE]
    >  La définition de la chaîne est facultative s'il ne s'agit pas d'un serveur MQSeries distant.  
  
    -   N'interrompez pas l'exécution du simulateur Payment Tracker.  
  
2.  Ouvrez une invite de commandes, accédez au répertoire du \< *répertoire d’installation de BizTalk Server*> \SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release, puis exécutez BTSScnSOSimpleClient.exe.  
  
3.  Dans BTSScnSOSimpleClient.exe, envoyez une demande via le transport SOAP en procédant comme suit :  
  
    1.  Tapez des caractères dans le **RequestType**, **RequestSource**, et **RequestID** zones de texte.  
  
    2.  Tapez n’importe quel numéro à 16 chiffres dans le **numéro de compte** zone de texte.  
  
    3.  Sélectionnez **SOAP (appel WS)** et **carte** dans les **paramètres et sélectionnez le Transport** zone de groupe.  
  
    4.  Tapez l’URL suivante dans le **URL** zone de texte, par exemple :  
  
         `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter/CustomerServicePort.asmx`  
  
    5.  Type `ZipCode` dans les **nom** zone de texte sous **éléments d’authentification**, puis tapez des caractères dans le **valeur** zone de texte.  
  
    6.  Type `CustomerName` dans les **nom** zone de texte sous **éléments d’authentification**, puis tapez des caractères dans le **valeur** zone de texte.  
  
    7.  Cliquez sur **obtenir le solde**.  
  
    8.  La réponse est affichée dans le **réponse** zone de texte : **réussite** s’affiche si la demande est traitée correctement ; un message d’erreur s’affiche si la demande échoue.  
  
         ![Exécutez l’application cliente pour la version d’adaptateur](../core/media/soap-transport-adapter-success.gif "SOAP_Transport_adapter_success")  
  
4.  Dans BTSScnSOSimpleClient.exe, envoyez des demandes via le transport MQSeries en procédant comme suit :  
  
    1.  Tapez des caractères dans le **RequestType**, **RequestSource**, et **RequestID** zones de texte.  
  
    2.  Tapez un numéro à 16 chiffres dans le **numéro de compte** zone de texte.  
  
    3.  Sélectionnez **MQSeries** dans les **paramètres et sélectionnez le Transport** zone de groupe.  
  
    4.  Type \< *nom du Gestionnaire de file d’attente*> dans le **Gestionnaire de file d’attente** zone de texte. QM_\<*nom de votre ordinateur*> est la valeur par défaut \< *nom du Gestionnaire de file d’attente*>.  
  
    5.  Type `AdapterSOAInputQueue` dans les **file d’attente d’entrée** zone de texte.  
  
    6.  Type `AdapterSOAOutputQueue` dans les **file d’attente de sortie** zone de texte.  
  
    7.  Type \< *définition de la chaîne*> dans le **définition de la chaîne** boîte. S_\<*nom de votre ordinateur*> /TCP/\<*nom de votre ordinateur*> (1414) est la valeur par défaut \< *définition de la chaîne*>.  
  
    8.  Type `ZipCode` dans les **nom** zone de texte sous **éléments d’authentification**, puis tapez des caractères dans le **valeur** zone de texte.  
  
    9. Type `CustomerName` dans les **nom** zone de texte sous **éléments d’authentification**, puis tapez des caractères dans le **valeur** zone de texte.  
  
    10. Cliquez sur **obtenir le solde**.  
  
    11. La réponse est affichée dans le **réponse** zone de texte : **réussite** s’affiche si la demande est traitée correctement ; un message d’erreur s’affiche si la demande échoue.  
  
         ![Exécutez l’application cliente pour la version d’adaptateur](../core/media/mqseries-transport-adapter.gif "MQSeries_Transport_adapter")  
  
##  <a name="step5"></a>Envoyer des demandes à l’aide de l’application cliente (version inline)  
  
#### <a name="to-send-requests-using-the-client-application-inline-version"></a>Pour envoyer des demandes à l'aide de l'application cliente (version Inline)  
  
1.  Ouvrez une invite de commandes, accédez au répertoire \< *répertoire d’installation de BizTalk Server*> \SDK\Scenarios\SO\BTSSoln\PaymentTracker\bin\Debug, puis exécutez la commande suivante pour démarrer le PaymentTracker Simulateur :  
  
     `BTSScnSOPaymentTracker.exe LastPaymentsInputQueue LastPaymentsOutputQueue <`*Nom du Gestionnaire de file d’attente* `> 5 [<` *définition de canal*`>]`  
  
    > [!NOTE]
    >  La définition de la chaîne est facultative s'il ne s'agit pas d'un serveur MQSeries distant.  
  
    > [!NOTE]
    >  Ignorez cette étape si le simulateur Payment Tracker est déjà en cours d'exécution.  
  
    -   N'interrompez pas l'exécution du simulateur Payment Tracker.  
  
2.  Dans le **Console d’Administration de BizTalk Server**, développez **BTSScn.SO.CustomerService**, cliquez sur **emplacements de réception**, avec le bouton droit  **PaymentTrackingSystemOutputQueue** dans le volet droit, puis cliquez sur **désactiver**.  
  
    > [!NOTE]
    >  La version d'adaptateur et la version Inline utilisent la même file d'attente MQSeries, à savoir LastPaymentsOutputQueue. Pour éviter l'existence d'une condition d'engorgement entre les deux versions, désactivez l'emplacement de réception de la version d'adaptateur qui écoute la file d'attente MQSeries.  
  
3.  Ouvrez une invite de commandes, accédez au répertoire du \< *répertoire d’installation de BizTalk Server*> \SDK\Scenarios\SO\BTSSoln\SimpleClient\bin\Release, puis exécutez BTSScnSOSimpleClient.exe.  
  
4.  Dans BTSScnSOSimpleClient.exe, envoyez une demande via le transport SOAP en procédant comme suit :  
  
    1.  Tapez des caractères dans le **RequestType**, **RequestSource**, et **RequestID** zones de texte.  
  
    2.  Tapez n’importe quel numéro à 16 chiffres dans le **numéro de compte** zone de texte.  
  
    3.  Sélectionnez **SOAP (appel WS)** et **Inline** dans les **paramètres et sélectionnez le Transport** zone de groupe.  
  
    4.  Tapez l’URL suivante dans le **URL** zone de texte, par exemple :  
  
         `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline/CustomerServicePort.asmx`  
  
    5.  Type `ZipCode` dans les **nom** zone de texte sous **éléments d’authentification**, puis tapez des caractères dans le **valeur** zone de texte.  
  
    6.  Type `CustomerName` dans les **nom** zone de texte sous **éléments d’authentification**, puis tapez des caractères dans le **valeur** zone de texte.  
  
    7.  Cliquez sur **obtenir le solde**.  
  
    8.  La réponse est affichée dans le **réponse** zone de texte : **réussite** s’affiche si la demande est traitée correctement ; un message d’erreur s’affiche si la demande échoue.  
  
         ![Exécutez l’application cliente pour la version inline](../core/media/soap-transport-inline.gif "SOAP_Transport_inline")  
  
5.  Dans BTSScnSOSimpleClient.exe, envoyez des demandes via le transport MQSeries en procédant comme suit :  
  
    1.  Tapez des caractères dans le **RequestType**, **RequestSource**, et **RequestID** zones de texte.  
  
    2.  Tapez un numéro à 16 chiffres dans le **numéro de compte** zone de texte.  
  
    3.  Sélectionnez **MQSeries** dans les **paramètres et sélectionnez le Transport** zone de groupe.  
  
    4.  Type \< *nom du Gestionnaire de file d’attente*> dans le **Gestionnaire de file d’attente** zone de texte. QM_\<*nom de votre ordinateur*> est la valeur par défaut \< *nom du Gestionnaire de file d’attente*>.  
  
    5.  Type `InlineSOAInputQueue` dans les **file d’attente d’entrée** zone de texte.  
  
    6.  Type `InlineSOAOutputQueue` dans les **file d’attente de sortie** zone de texte.  
  
    7.  Type \< *définition de la chaîne*> dans le **définition de la chaîne** boîte. S_\<*nom de votre ordinateur*> /TCP/\<*nom de votre ordinateur*> (1414) est la valeur par défaut \< *définition de la chaîne*>.  
  
    8.  Type `ZipCode` dans les **nom** zone de texte sous **éléments d’authentification**, puis tapez des caractères dans le **valeur** zone de texte.  
  
    9. Type `CustomerName` dans les **nom** zone de texte sous **éléments d’authentification**, puis tapez des caractères dans le **valeur** zone de texte.  
  
    10. Cliquez sur **obtenir le solde**.  
  
    11. La réponse est affichée dans le **réponse** zone de texte : **réussite** s’affiche si la demande est traitée correctement ; un message d’erreur s’affiche si la demande échoue.  
  
         ![Exécutez l’application cliente pour la version inline](../core/media/mqseries-transport-inline.gif "MQSeries_Transport_inline")  
  
## <a name="see-also"></a>Voir aussi  
 [Avant d’installer la Solution orientée services](../core/before-installing-the-service-oriented-solution.md)   
 [Pour installer la Version Stub de Service de la Solution orientée services](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md)   
 [Pour installer le Inline et les Versions du Service d’adaptateur Solution orientée services](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md)   
 [Installation d’ordinateur de développeur pour le Service orienté solutions](../core/developer-machine-setup-for-the-service-oriented-solution.md)