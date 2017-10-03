---
title: "Comment éviter de disque Contention1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b4f8e10-16b0-45f9-8787-da16266da980
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 702665046dbaee77412675e4be0edc602dd9e7e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-avoid-disk-contention"></a>Élimination des risques de conflit au niveau des disques
BizTalk Server a été conçu comme un système persistant dans lequel, en cas de scénarios à débit élevé, la base de données MessageBox peut être confrontée à des conflits sévères. Ces conflits peuvent être aggravés par des disques lents. Si les disques sont lents (% d'inactivité du disque faible), SQL risque d'utiliser les verrous plus longtemps que prévu (temps d'attente des verrous élevé et dépassements de délai d'attente des verrous élevé), ce qui peut entraîner l'augmentation des tables de MessageBox (files d'attente du spouleur et de l'application) et provoquer ainsi un encombrement et une limitation se traduisant au final par un débit acceptable global inférieur.  
  
 Pour éviter les conflits au niveau des disques, nous vous recommandons de procéder comme suit :  
  
-   Utilisez des disques haute vitesse (sous-unités multiples).  
  
-   Si possible, déployez les bases de données sur un SAN haute vitesse. Si plusieurs bases de données partagent les mêmes disques, il est recommandé de les configurer sur des disques dédiés distincts. Il est également recommandé de séparer les fichiers MDF et LDF de la base de données MessageBox sur des disques différents.  
  
-   Si l'UC de SQL est insuffisante, installez la base de données MessageBox sur un serveur dédié séparé des bases de données des suivis.  
  
-   Après avoir configuré un serveur dédié pour la base de données MessageBox, envisagez d’évoluer verticalement en ajoutant des UC et/ou de la mise à niveau de l’UC. Surveillez le lecteur local sur le serveur SQL Server comme les journaux MSDTC sont enregistrés sur le disque local (C:\WINDOWS\system32\Msdtc).  
  
-   En cas de conflit dû au journal PageFile ou MSDTC, essayez de le déplacer vers un autre lecteur.