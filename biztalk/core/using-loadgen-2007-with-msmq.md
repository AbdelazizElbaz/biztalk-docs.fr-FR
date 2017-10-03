---
title: Utilisation de LoadGen 2007 avec MSMQ | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8f23a86-0e6d-478a-87a3-5b02338c9afb
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55d67628b7863df3f2396cd9b45b55f42a488b8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-loadgen-2007-with-msmq"></a>Utilisation de LoadGen 2007 avec MSMQ
L'outil de génération de charge, Loadgen, vous permet de simuler de lourdes charges sur un système BizTalk Server.  
  
> [!NOTE]
>  L’outil LoadGen 2007 est disponible pour téléchargement à l’adresse [http://go.microsoft.com/fwlink/?LinkId=59841](http://go.microsoft.com/fwlink/?LinkId=59841).  
  
 L'utilisation de LoadGen avec MSMQ est prise en charge, mais nous n'effectuons pas l'enregistrement automatique des composants MSMQ COM pendant l'installation puisque le service d'exécution MSMQ n'est peut-être pas installé sur votre ordinateur.  
  
 Pour utiliser MSMQ et LoadGen, enregistrez manuellement les fichiers MSMQTransmitter.dll et ComMsmqMonitor.dll situés dans le répertoire Bins :  
  
```  
regsvr32 MSMQTransmitter.dll  
```  
  
 Si vous n'enregistrez pas les composants MSMQ COM, vous recevrez les erreurs d'exécution suivantes :  
  
```  
Cannot Load Transport DLL C:\Program Files\LoadGen\Bins\MSMQTransport.dll for Section MSMQRxQTxn   
Exception has been thrown by the target of an invocation.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Scénarios de test pour mesurer le débit maximal acceptable du moteur](../core/test-scenarios-for-measuring-mst-of-the-engine.md)