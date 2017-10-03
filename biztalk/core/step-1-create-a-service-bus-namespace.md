---
title: "Étape 1 : Créer un Namespace de Bus de Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ede1ac50-bbfb-4aeb-8217-1877ae218f89
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4d7630316f72fd63bac5ce7127b5451683e2f97
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-create-a-service-bus-namespace"></a>Étape 1 : Créer un Namespace de Bus de Service
Dans cette étape, vous allez créer un [!INCLUDE[winazure](../includes/winazure-md.md)] [!INCLUDE[sb](../includes/sb-md.md)] espace de noms. Vous allez utiliser cet espace de noms pour héberger un point de terminaison de relais afin de recevoir des notifications d'opportunité de Salesforce. Plus tard dans le processus de création de cette solution, vous allez utiliser ce point de terminaison de relais pour recevoir le message de notification dans un système [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-create-a-includesbincludessb-mdmd-namespace"></a>Pour créer un espace de noms [!INCLUDE[sb](../includes/sb-md.md)]  
  
1.  Ouvrez une session sur [http://manage.windowsazure.com](http://manage.windowsazure.com) à l’aide de votre compte Microsoft.  
  
2.  Au bas de la page, cliquez sur **nouveau**, **des Services d’application**, **relais Service Bus**, puis **création rapide**.  
  
3.  Entrez l’espace de noms `BtsSalesforce` et sélectionnez une région proche de votre emplacement géographique actuel. Cliquez sur **créer un relais**.  
  
    > [!CAUTION]
    >  Cet espace de noms doit être globalement unique. Ainsi, vous devez utiliser un espace de noms autre que celui mentionné dans ce didacticiel.  
  
    > [!NOTE]
    >  Notez que le relais n'est pas créé dans le cadre de l'opération, seul l'espace l'est. Le point de terminaison de relais est créé ultérieurement dans ce didacticiel lorsque nous configurons un emplacement de réception pour le **SB-Messaging** carte.  
  
4.  Une fois l’espace de noms est créé, l’état est défini sur **Active**. Une fois que l’état est actif, vous pouvez sélectionner l’espace de noms et cliquez sur **clé d’accès** au bas de la page pour obtenir plus d’informations sur la façon de se connecter à la **BtsSalesforce** espace de noms, y compris les valeurs de **Utilisateur par défaut** et **clé par défaut**. Vous aurez besoin de ces détails ultérieurement dans ce didacticiel.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 6 : Intégration de BizTalk Server 2013 avec Salesforce](Tutorial:%20Integrating%20BizTalk%20Server%202013%20with%20Salesforce.md)