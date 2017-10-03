---
title: Des exceptions DBNETLIB | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5fbee0cf-d249-4d98-8d16-168ded32f9f1
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: decd258c5f4c965c79d9821c82671c6997ac9e3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="avoiding-dbnetlib-exceptions"></a>Contournement des exceptions DBNETLIB
Des erreurs DBNetLib (Database Network Library) se produisent lorsque le composant d'exécution de BizTalk Server ne peut pas communiquer avec la base de données MessageBox ou celle de gestion. Lorsque cela se produit, l'instance d'exécution BizTalk Server qui intercepte l'exception s'arrête et effectue une interrogation toutes les minutes pour voir si la base de données est disponible.  
  
 La cause la plus fréquente d'une erreur DBNetLib est lorsque l'un des serveurs de base de données MessageBox devient occupé. Toute tentative ultérieure de communiquer avec lui se solde alors par un délai d'expiration, causant une exception DBNetLib.  
  
 Outre ce cas de figure, l'erreur DBNetLib peut se produire dans un environnement de production lorsque les serveurs de base de données BizTalk hébergeant une ou plusieurs bases de données MessageBox  deviennent liés aux E/S (Entrées/Sorties).  
  
 Cette rubrique décrit les conditions pouvant conduire à des erreurs DBNetLib et les recommandations permettant de les éviter.  
  
## <a name="cause-and-resolution-for-the-dbnetlib-error"></a>Cause et résolution de l'erreur DBNetLib  
  
### <a name="symptoms-of-a-dbnetlib-error"></a>Symptômes d'une erreur DBNetLib  
 Une instance d'hôte Microsoft BizTalk Server prend fin, puis redémarre d'elle-même, et des erreurs semblables à celles qui suivent sont consignées dans le journal de l'application de BizTalk Server :  
  
```  
Event Type:Warning  
Event Source:BizTalk Server <version>  
Event Category:BizTalk Server <version>   
Event ID:5410  
Computer:BIZTALKSERVER  
Description:  
An error occurred that requires the BizTalk service to terminate. The most common causes are the following:  
 1) An unexpected out of memory error.  
 OR  
 2) An inability to connect or a loss of connectivity to one of the BizTalk databases.   
 The service will shutdown and auto-restart in 1 minute. If the problematic database remains unavailable, this cycle will repeat.  
  
 Error message: [DBNETLIB][ConnectionWrite (send()).]General network error. Check your network documentation.  
 Error source:    
  
 BizTalk host name: BizTalkHost  
 Windows service name: BTSSvc$BizTalkHost   
  
---------------------------------------------------------  
Event Type:Error  
Event Source:BizTalk Server <version>  
Event Category:BizTalk Server <version>   
Event ID:6913  
Computer:BIZTALKSERVER  
Description:  
An attempt to connect to "BizTalkMsgBoxDb" SQL Server database on server "SQLSERVER " failed.  
 Error: "[DBNETLIB][ConnectionWrite (send()).]General network error. Check your network documentation."  
```  
  
### <a name="biztalk-database-servers-hosting-messagebox-databases-becoming-io-bound"></a>Serveurs BizTalk hébergeant les bases de données MessageBox devenant liés aux E/S  
 Les serveurs BizTalk communiquent et agissent directement avec les serveurs hébergeant les bases de données MessageBox. Si l'un des serveurs hébergeant les bases de données MessageBox vient à être trop sollicité et à se trouver lié aux E/S, il risque de ne plus répondre. Un des serveurs BizTalk peut alors perdre à son tour la connectivité avec l'un de ces serveurs, produisant une erreur DBNetLib.  
  
 Nos tests montrent qu'un serveur de base de données hautement utilisé devient lié aux E/S quand la durée d'inactivité (« %Idle time ») de son disque physique diminue jusqu'à atteindre une valeur inférieure à 10 %. Si la durée d'inactivité tombe en dessous de ce niveau, cela signifie que votre serveur de base de données a de grandes chances de ne plus répondre.  
  
#### <a name="cause"></a>Cause  
 Plusieurs situations peuvent faire que les serveurs hébergeant les bases de données MessageBox deviennent liés aux E/S, notamment :  
  
-   Lorsque l'ordinateur hébergeant la base de données MessageBox est limité par des spécifications matérielles faibles telles que : mémoire insuffisante, processeurs insuffisants et pas assez rapides, etc.  
  
-   Lorsque le disque physique de l'ordinateur hébergeant une base de données MessageBox est également employé par d'autres bases de données fortement utilisées. Si plusieurs bases de données (dont la MessageBox) sont fortement utilisées en même temps, le disque physique peut se retrouver tributaire des E/S.  
  
     Voici un exemple d’une telle situation :  
  
     Nos tests montrent que le serveur hébergeant les bases de données BizTalkDTADb et/ou BAM utilise parfois d'importantes ressources lors de la lecture et de l'écriture sur le disque physique. Lorsque le disque du serveur sur lequel réside la base de données MessageBox est également utilisé par une telle base de données, et que vous avez recours aux deux bases en même temps, le disque peut se retrouver tributaire des E/S et ne plus être en mesure de répondre.  
  
-   Lorsque la base de données BizTalkDTADb et une ou plusieurs bases de données MessageBox partagent le même disque physique et que la fréquence d'exécution des archivages et des purges n'est pas suffisante, le disque devient lié aux E/S.  
  
#### <a name="resolution"></a>Résolution  
 Assurez-vous que les serveurs hébergeant les bases de données MessageBox de BizTalk ne soient pas trop sollicités, ce qui aurait pour conséquence de les rendre inaccessibles.  
  
 La section suivante indique certaines des principales situations pouvant entraîner une forte sollicitation du disque du serveur et présente quelques conseils permettant de résoudre le problème.  
  
##### <a name="low-hardware-specs"></a>Spécifications matérielles faibles  
 Nos tests montrent que la sollicitation du serveur devient trop importante lorsque ses spécifications matérielles ne peuvent suivre la charge de travail qu'il tente de traiter. Un système aux spécifications matérielles trop faibles se retrouve vite submergé par la quantité d'activités se produisant sur les bases de données. Les temps de lecture et d'écriture augmentent alors sans cesse, la durée d'inactivité du disque diminue pour tomber sous les 10 %, avec pour résultat un serveur qui ne répond plus.  
  
 En fonction de la quantité d'activités et de la charge utilisée dans votre déploiement BizTalk, s'il arrive que les serveurs de base de données ne répondent plus lors de fortes sollicitations, vous devez envisager de mettre à niveau les composants suivants de vos serveurs de base de données : le nombre d'UC, la quantité de mémoire et la connexion à un SAN. Il est bien sûr conseillé de poser le bon diagnostic pour savoir quel composant de votre matériel (mémoire, nombre d'UC, etc.) est à l'origine de l'engorgement et nécessite d'être mis à niveau.  
  
##### <a name="sharing-one-server-or-disk-for-more-than-one-group-of-biztalk-databases"></a>Plusieurs groupes de bases de données BizTalk partageant un même serveur ou un même disque  
 Comme cela a été dit plus haut, les bases de données autres que MessageBox, telles que les bases de données des suivis BizTalk (BizTalkDTADb) et BAM, peuvent consommer d'importantes ressources sur le disque physique d'un serveur. De ce fait, si ces bases de données et les bases MessageBox devaient partager le même disque physique, ce dernier risquerait d'être trop sollicité et de ne plus être en mesure de répondre. Les serveurs BizTalk pourraient alors connaître des problèmes de connectivité avec les bases MessageBox et générer une erreur DBNetLib.   
  
 Il est fortement recommandé de séparer toute base de données susceptible d'utiliser d'importantes ressources du disque physique du serveur des bases de données MessageBox, de sorte qu'elles partagent plusieurs disques physiques (ou qu'elles soient placées sur différents serveurs). Il est conseillé de placer les bases de données BizTalkDTADb et BAM sur des lecteurs/serveurs qui leur sont propres, distincts des bases de données MessageBox. Chaque base de données MessageBox (si vous en utilisez plusieurs) devrait par ailleurs être hébergée de manière séparée, chacune sur son propre disque.  
  
##### <a name="archiving-and-purging"></a>L'archivage et la purge  
 Si les bases de données BizTalkDTADb et MessageBox partagent le même disque sur le même serveur, vous devez archiver et purger les bases BizTalkDTADb de manière régulière, de façon à éviter que leur volume ne s'accroisse indéfiniment.  
  
 Le test montre qu'il est conseillé de les archiver et de les purger de manière périodique. Toutefois, en cas de charges plus élevées que la normale, vous pouvez être amené à augmenter la fréquence d'archivage et de purge. Sachez que des travaux d'archivage et de purge non effectués régulièrement risquent de prendre beaucoup plus de temps et d'utiliser une grosse partie des ressources disponibles du serveur.