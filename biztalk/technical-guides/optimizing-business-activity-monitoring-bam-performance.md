---
title: "Optimisation de l’analyse des performances de (l’analyse BAM) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9ed29b2-0be6-4a37-be68-9476832fd49f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83801a4e147b3e1eaf34c5e264d6adecfbdf8f9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-business-activity-monitoring-bam-performance"></a>Optimisation de l’analyse des performances de l’analyse BAM)
Cette rubrique décrit les facteurs de performances d’analyse BAM (Business Activity).  
  
## <a name="bam-disk-usage-configuration"></a>Configuration de l’utilisation de disque BAM  
 BAM entraîne une surcharge significative lorsqu’un système BizTalk est sous charge en raison de la quantité importante de données qui sont rendue persistante dans la base de données BAM. Par conséquent, une utilisation judicieuse des techniques d’e/s disque pour la base de données BAM est extrêmement importante.  
  
## <a name="bam-eventstream-apis"></a>API EventStream BAM  
 Quatre types de flux d’événements sont disponibles pour une utilisation dans un scénario BizTalk BAM :  
  
-   DirectEventStream (DES)  
  
-   BufferedEventStream (BES)  
  
-   OrchestrationEventStream (OES)  
  
-   MessageEventStream (MES)  
  
 Vous devez choisir une de ces API basées sur les facteurs suivants :  
  
-   Si votre préoccupation est la latence, choisissez DES, les données étant conservées de manière synchrone dans la base de données d'importation principale BAM.  
  
-   Si votre préoccupation est les performances et le débit d’insertion des événements, choisissez une API asynchrone (BES, OES ou MES).  
  
-   Si vous écrivez une application qui s’exécute sur un ordinateur qui n’a pas installé BizTalk Server, utilisez DES et BES ; Ces API peuvent être utilisées dans les applications non-BizTalk.  
  
    > [!NOTE]  
    >  Il existe des scénarios dans lesquels vous pouvez combiner plusieurs types EventStream. Par exemple, pour le traitement de pipeline, il pouvez que vous souhaitez capturer les données spécifiques de l’analyse BAM, indépendamment de si le pipeline est que sa transaction. En particulier, vous pouvez choisir de capturer des données sur le nombre de messages a échoué ou le nombre de tentatives s’est produite lors du traitement du pipeline. Pour capturer les données dans ce cas précis, vous devez utiliser BES.  
  
-   Si votre application s'exécute sur un ordinateur sur lequel BizTalk Server est installé, utilisez MES et OES. (Ces API sont uniquement disponibles à partir des applications BizTalk.)  
  
    > [!NOTE]  
    >  OES est l'équivalent de MES, mais pour les orchestrations BizTalk.  
  
-   Si vous souhaitez la persistance d’événement BAM soit synchronisée avec la transaction de pipeline, vous devez utiliser un flux d’événements de messagerie (MES).  
  
 Tous les flux d’événements asynchrones (BES, MES et OES) conservent les données de tout d’abord la base de données MessageBox de BizTalk. Régulièrement, les données sont traitées et rendues persistantes dans la base de données Importation principale BAM par le service TDDS (Tracking Data Decode Service).  
  
 Pour plus d’informations sur les BAM EventStream APIs, consultez [Classes EventStream](http://go.microsoft.com/fwlink/?LinkId=158046) (http://go.microsoft.com/fwlink/?LinkId=158046) dans la documentation de BizTalk Server.  
  
## <a name="bam-performance-counters"></a>Compteurs de performance BAM  
 Pour obtenir une liste détaillée des compteurs de performance pour l’analyse BAM, consultez [les compteurs de Performance BAM](http://go.microsoft.com/fwlink/?LinkId=158048) (http://go.microsoft.com/fwlink/?LinkId=158048) dans la documentation de BizTalk Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances de BizTalk Server](../technical-guides/optimizing-biztalk-server-performance.md)