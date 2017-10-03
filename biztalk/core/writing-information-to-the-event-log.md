---
title: "Écrire des informations dans le journal des événements | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d7398dc-29d8-4a7a-bab4-c8f128b47dca
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f848cafd6ee9247511db3b9a6dad7dc5da91236b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="writing-information-to-the-event-log"></a>Écriture d'informations dans le journal des événements
Il est possible de contrôler la progression des divers processus d'entreprise de votre application BizTalk en écrivant des informations dans le journal de l'application ou un journal des événements personnalisé. L'écriture d'informations dans le journal des événements peut s'avérer utile dans les situations suivantes  :  
  
-   vous voulez accéder aux messages de l'application de manière standard à l'aide des outils fournis par Windows ;  
  
-   vous voulez archiver des informations ainsi que d'autres messages de l'environnement serveur afin d'obtenir un historique plus complet ;  
  
-   vous voulez pouvoir contrôler votre application à l'aide d'outils qui interagissent avec le journal des événements.  
  
> [!NOTE]
>  La taille de la méthode System.Diagnostics.EventLog.WriteEntry est limitée sur la chaîne de message. Si cette chaîne dépasse 32 766 octets, un message d'exception s'affiche.  
  
## <a name="writing-to-the-application-log"></a>Écriture dans le journal de l'application  
 Vous pouvez écrire le journal des applications ou de tout autre journal à partir de votre code à l’aide de **System.Diagnostics.EventLog** comme indiqué dans l’exemple suivant :  
  
```  
System.Diagnostics.EventLog.WriteEntry("Orchestration Debug", System.String.Format("The Value = {0}", iResult));  
```  
  
 De la même manière, vous pouvez utiliser :  
  
```  
EventLog appLog = new EventLog();   
appLog.Source = "This Application's Name";  
appLog.WriteEntry("An entry to the Application event log.");  
```  
  
 Si vous utilisez un journal personnalisé, vous devez utiliser le **SourceExists** méthode pour garantir qu’il existe avant d’écrire sur elle.  
  
## <a name="writing-to-a-custom-log"></a>Écriture dans un journal personnalisé  
 L'écriture dans un journal personnalisé est similaire à l'écriture dans le journal de l'application, à ceci près que vous devez d'abord créer le journal personnalisé. Voici le code à utiliser pour créer un journal personnalisé :  
  
```  
// Create the source, if it does not already exist. if(!EventLog.SourceExists("MySource"))   
{   
  //An event log source should not be created and immediately used.  
  //There is a latency time to enable the source, it should be created  
  //prior to executing the application that uses the source.  
  EventLog.CreateEventSource("MySource", "MyNewLog");  
}  
```  
  
 Cependant, votre code ne pourra être exécuté par un compte qui dispose des privilèges de sécurité suffisants pour la création d'un nouveau journal des événements. En effet, la création d'un journal des événements requiert également des privilèges d'administrateur et doit être effectuée dans un utilitaire distinct ou, idéalement, dans le cadre d'une installation .msi. Pour plus d’informations sur l’utilisation de script personnalisé avec une installation .msi exportée, consultez [à l’aide de Scripts de pré-traitement et post-traitement pour personnaliser le déploiement Application](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).