---
title: "Didacticiel de 5 : Appeler une Interface REST à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73871ca3-abd0-45ae-b379-6df76a967a80
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fce915ec277b1f73f93a9508a5dd6c92fb0a5c9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-5-invoking-a-rest-interface-using-biztalk-server"></a>Didacticiel de 5 : Appeler une Interface REST à l’aide de BizTalk Server
Cette section décrit une procédure pas à pas d'appel d'un point de terminaison REST à l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Au cours de ce didacticiel, vous allez appeler un point de terminaison REST disponible dans la Place de marché [!INCLUDE[winazure](../includes/winazure-md.md)] qui renvoie les retards des vols des transporteurs aériens américains. Le didacticiel utilise le nouveau **WCF-WebHttp** carte introduite dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour appeler le point de terminaison REST.  
  
##  <a name="BKMK_Scenario"></a>Scénario utilisé dans ce didacticiel  
 La Place de marché [!INCLUDE[winazure](../includes/winazure-md.md)] fournit l'URL de ressource REST pour extraire les retards des vols des transporteurs aériens américains :  
  
```  
https://api.datamarket.azure.com/oakleaf/US_Air_Carrier_Flight_Delays_Incr/On_Time_Performance  
```  
  
 Si vous entrez cette URL dans la barre d'adresses d'un navigateur Web, vous êtes invité à entrer des informations d'identification afin d'accéder à la ressource. Après vous être connecté à la [Windows Azure Marketplace](http://go.microsoft.com/fwlink/p/?LinkId=257913), vous pouvez obtenir les informations d’identification à partir de la **mon compte** onglet de la page web. Les informations d’identification sont répertoriées par rapport à la **ID de client** (nom d’utilisateur) et **clé de compte primaire** les étiquettes (mot de passe).  
  
 Dans ce didacticiel, vous utilisez l’URL de ressource et les informations d’identification pour configurer un bidirectionnelle **WCF-WebHttp** port d’envoi. Le pipeline de réception du port d'envoi bidirectionnel reçoit le message de réponse contenant les détails des vols et publie le message dans la base de données MessageBox [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous configurez un port d'envoi FILE qui s'abonne à tous les messages publiés par le port d'envoi WCF-WebHttp. Le port d'envoi FILE consomme le message en provenance du serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et le copie dans un emplacement de fichier.  
  
 Dans un scénario d'entreprise réel, le port d'envoi WCF-WebHttp peut être déclenché en l'associant à un processus d'entreprise plus important, par exemple, quand un emplacement de réception récupère un message en provenance d'une application professionnelle. Toutefois, dans le cadre de ce didacticiel, étant donné que l'objectif est de présenter la manière d'appeler une interface REST, vous pouvez utiliser un emplacement FILE classique qui reçoit un message factice afin de déclencher le port d'envoi.  
  
 En résumé, vous devez réaliser les étapes suivantes pour configurer cette solution :  
  
1.  configuration d'un emplacement de réception FILE afin de récupérer un message de requête factice ;  
  
2.  configuration d'un port d'envoi WCF-WebHttp bidirectionnel afin d'appeler l'URL de la ressource REST et de recevoir une réponse ;  
  
3.  configuration d'un port d'envoi FILE unidirectionnel pour consommer le message de réponse contenant les détails des vols et le copier dans un emplacement de fichier.  
  
## <a name="set-up-your-includewinazureincludeswinazure-mdmd-marketplace-account"></a>Configuration de votre compte sur la Place de marché [!INCLUDE[winazure](../includes/winazure-md.md)]  
 Pour accéder aux données concernant les retards des vols qui sont exposées via le point de terminaison REST, vous devez d'abord vous abonner au flux de données de l'exemple relatif aux retards des vols des transporteurs aériens américains. Effectuez les étapes suivantes pour ce faire :  
  
#### <a name="to-subscribe-to-the-data-feed"></a>Pour vous abonner au flux de données  
  
1.  Connectez-vous à la Place de marché [!INCLUDE[winazure](../includes/winazure-md.md)] en utilisant votre compte Microsoft.  
  
2.  Dans le **données** onglet, recherchez et cliquez sur le **nous Air transporteur retards des vols des** service.  
  
3.  Dans la page de service de données, cliquez sur **s’inscrire**. Dans la page d’abonnement, acceptez les termes du contrat, puis sur **inscrire** à nouveau.  
  
4.  Dans le **mon compte** , onglet de récupérer les informations d’identification pour accéder au service de données. Les informations d’identification sont répertoriées par rapport à la **ID de client** (nom d’utilisateur) et **clé de compte primaire** les étiquettes (mot de passe). Vous devez ces informations d’identification lors de la configuration du **WCF-WebHttp** port d’envoi.  
  
## <a name="set-up-your-computer"></a>Configuration de votre ordinateur  
 Pour configurer le scénario de ce didacticiel, vous devez avoir installé et configuré [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur votre ordinateur. Si vous voulez configurer un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur sur un ordinateur virtuel Windows Azure, suivez les instructions à [configuration de BizTalk Server sur une machine virtuelle Azure](http://msdn.microsoft.com/library/azure/jj248689.aspx).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Étape 1 : Configurer un fichier de l’emplacement de réception](../core/step-1-configure-a-file-receive-location.md)  
  
-   [Étape 2 : Configurer un Port d’envoi WCF-WebHttp bidirectionnel](../core/step-2-configure-a-two-way-wcf-webhttp-send-port.md)  
  
-   [Étape 3 : Configurer un Port d’envoi FILE unidirectionnel](../core/step-3-configure-a-one-way-file-send-port.md)  
  
-   [Étape 4 : Tester la Solution](../core/step-4-test-the-solution.md)