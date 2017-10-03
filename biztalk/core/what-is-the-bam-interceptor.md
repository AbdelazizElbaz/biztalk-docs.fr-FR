---
title: "Présentation de l'intercepteur BAM | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM Interceptor object
- BAM, collecting data
- BAM, Interceptor object
- data, collecting [BAM]
ms.assetid: e0213c4e-e2f4-4bb0-bd27-e5810f7e39d9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9400e80a2f8e8acfdeb12e3d6e61a046151d1e7e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-bam-interceptor"></a>Présentation de l'intercepteur BAM
## <a name="overview"></a>Vue d'ensemble 

L'intercepteur de l'analyse BAM est un objet qui vous permet d'instrumenter votre application pour capturer des données d'intérêt. Le diagramme suivant illustre le rôle de l'intercepteur de l'analyse BAM et son interaction avec les autres composants BAM :  
  
 ![](../core/media/bam-config-api.gif "bam_config_api")  
Intercepteur de l'analyse BAM  
  
 Dans chaque étape de votre application où vous pourriez avoir des données d'intérêt, vous appelez Interceptor OnStep, fournissez un identificateur pour l'étape ainsi qu'un objet arbitraire ou de données quelconque que vous utilisez dans votre application.  
  
 Vous devez implémenter une fonction de rappel de manière à ce que votre procédure de rappel obtienne l'ID d'étape actuel et vos objets de données lors du rappel. Essentiellement, l'intercepteur de l'analyse BAM se borne à propager l'objet de données vers le rappel. La logique réelle d'extraction des données réside dans votre application. Par exemple, si vos données prennent la forme de messages XML, le rappel utilisera des XPath. Pour plus d’informations sur XPath, consultez [à l’aide de XPath dans une assignation du Message](../core/using-xpaths-in-message-assignments.md).  
  
 Sur la base d'une configuration que vous pouvez créer de façon programmée, l'intercepteur de l'analyse BAM décide des données à requérir à chaque étape. Il se sert ensuite des données obtenues pour appeler DirectEventStream ou BufferedEventStream, que vous devez conserver et transmettre à chaque fois en tant qu'argument à OnStep.  
  
 L'appel de l'intercepteur à chaque étape ne demande pas beaucoup de ressources. Si, suite à l'appel, vous n'inscrivez rien pour l'étape, l'intercepteur repart immédiatement. Cela signifie que n'a lieu aucune opération disque, aucune transaction et même aucune affectation mémoire, et que cela n'a donc presque aucune incidence sur les performances. Parallèlement, vous avez la possibilité d'extraire toutes les données que vous souhaitez pour l'analyse BAM si nécessaire. L’impact des performances sur les étapes impliquant l’extraction de données et la disponibilité des données dépend de votre implémentation de la `IBAMDataExtractor Interface`.  
  
 Les exemples de code suivants illustrent l'utilisation de l'intercepteur pendant la configuration et l'exécution.  
  
## <a name="configuration-time"></a>Lors de la configuration  
 Le code suivant vous montre comment configurer l'Intercepteur de manière à ce qu'il s'arrête lors de l'étape recvPO de l'application et à ce qu'il demande le nom du client (Customer Name) et son numéro de sécurité sociale (Customer SSN) :  
  
```  
ActivityInterceptorConfiguration cfg= new ActivityInterceptorConfiguration ("PurchaseOrder");  
...  
cfg.RegisterDataExtraction("CustomerName",recvPO,XpathName);  
cfg.RegisterDataExtraction("CustomerSSN",recvPO,XpathSSN);  
...  
BAMInterceptor interceptor=new BAMInterceptor();  
cfg.UpdateInterceptor(interceptor);  
...  
// The interceptor instance is ready.  
```  
  
 Une fois que vous avez créé une instance d'intercepteur, vous pouvez la stocker pour une utilisation ultérieure durant l'exécution.  
  
 Vous pouvez conserver différents intercepteurs pré-créés différents représentant diverses préférences pour les données et étapes majeures destinées à l'analyse BAM. Pour optimiser les performances, sérialisez les instances d'intercepteur à l'aide de la classe BinaryFormatter.  
  
## <a name="run-time"></a>Durée d’exécution  
 Utilisez ce code pour utiliser l'intercepteur lors de l'exécution dans un environnement de production :  
  
```  
// Deserialize the Interceptor that was prepared before  
...  
es=new DirectEventStream(...)  
...  
Interceptor.OnStep(recvPO, data1, es, callback)  
...  
Interceptor.OnStep(approvePO, data2, es, callback)  
...  
```  
  
 Où :  
  
-   *recvPO* et *approvePO* sont des objets arbitraires que vous utilisez pour identifier les étapes dans votre application.  
  
-   *Data1* et *data2* sont des objets arbitraires que vous avez à ce stade et pouvez contenir des données intéressantes, par exemple le document XML du bon de commande.  
  
-   *es* est soit DirectEventStream soit Bufferedeventstream flux selon vos besoins.  
  
-   *rappel* est votre implémentation de la `IBAMDataExtractor Interface`.  
  
 L’exemple du Kit de développement logiciel, [l’API BAM (exemple BizTalk Server)](../core/bam-api-biztalk-server-sample.md), illustre l’utilisation de l’intercepteur, qui contient à la fois un outil et exemple runtime application de configuration.  
  
 Le moteur d'orchestration BizTalk autorise l'interception, ce qui permet de modifier les données à collecter pour l'analyse BAM durant l'exécution à l'aide de l'Éditeur de modèle de suivi.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment déterminer et définir des rôles d’écriture d’événements pour les activités](../core/how-to-determine-and-set-event-writer-roles-for-activities.md)  
  
## <a name="see-also"></a>Voir aussi  
 [API BAM (exemple BizTalk Server)](../core/bam-api-biztalk-server-sample.md)