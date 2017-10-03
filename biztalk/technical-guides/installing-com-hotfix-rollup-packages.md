---
title: Installer les correctifs COM + | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 587ae3da-db65-4da8-9d3b-89effb91b197
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40610c649e00993323adedf0ea29330dd289a0e3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installing-com-hotfix-rollup-packages"></a>Installer les correctifs COM +
> [!NOTE]  
>  Cette rubrique s’applique uniquement pour Windows Server 2003.  
  
 Vous devez installer la dernière version du package de correctifs cumulatifs COM + Windows Server 2003 et la version la plus récente du correctif cumulatif Distributed Transaction Coordinator (DTC). Il s’agit, car les packages incluent plusieurs correctifs de stabilité et de performances.  
  
 Vous devez installer ces correctifs cumulatifs sur tous les ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et sur tous les ordinateurs exécutant SQL Server. Les sélections multiples sont particulièrement importants pour votre solution BizTalk s’exécuter correctement dans les scénarios à débit élevé.  
  
 Les problèmes DTC qui ont été résolus sont les suivantes :  
  
-   Arrêt inattendu de DTC  
  
-   Problèmes de fragmentation de mémoire  
  
-   DTC peut cesser de répondre en charge  
  
-   DTC peut entraîner une fuite de mémoire ou cesser de répondre lorsqu’il est utilisé avec[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   Performances de DTC sous charge ont été améliorées  
  
## <a name="installing-the-com-rollup-package"></a>L’installation du Package du correctif cumulatif de COM +  
 COM + n’est plus en publiant cumulatifs. Suivez ces informations pour installer le dernier package COM + :  
  
-   La version finale du cumul COM + est le « Windows Server 2003 post-Service Pack 2 COM + 1.5 correctif cumulatif Package 12 ». Ce correctif logiciel va installer sur n’importe quelle version de Windows Server 2003, y compris celles sans service pack installé. Vous trouverez plus d’informations sur ce correctif logiciel dans l’article de la Base de connaissances Microsoft 934016, [« disponibilité de Windows Server 2003 post-Service Pack 2 COM + 1.5 correctif cumulatif Package 12 «](http://go.microsoft.com/fwlink/?LinkId=158756) (http://go.microsoft.com/fwlink/?LinkId=158756).  
  
## <a name="installing-the-dtc-rollup-package"></a>Installation du Package de correctif cumulatif DTC  
 DTC publiera cumulatifs indépendantes de COM +. Suivez ces informations pour installer le dernier package DTC :  
  
-   À ce jour, le dernier correctif cumulatif DTC est « Package 16 ». Vous trouverez plus d’informations sur ce correctif logiciel dans l’article de la Base de connaissances Microsoft 958013, [« Liste des problèmes MS DTC qui sont résolus dans Windows Server 2003 MS DTC Package de correctifs cumulatifs 16 »](http://support.microsoft.com/kb/979919) (http://support.microsoft.com/kb/979919) .  
  
     L’article sur le dernier package de correctif cumulatif de correctif logiciel DTC peut être recherché en [http://support.microsoft.com](http://support.microsoft.com/) pour l’expression (y compris les guillemets) :  
  
    ```  
    "MS DTC Hotfix Rollup Package"  
    ```  
  
     La requête suivante effectue cette recherche pour vous. Choisir la plus récente :  
  
     [http://support.Microsoft.com/search/default.aspx?Query= « MS + DTC + + Package correctif cumulatif + »](http://support.microsoft.com/search/default.aspx?query=%22MS+DTC+Hotfix+Rollup+Package%22)