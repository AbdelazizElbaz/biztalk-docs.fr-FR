---
title: Configurer la limite maximale de connexions au serveur SAP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 858ed90e-b219-43cc-ad63-ae8e1eb2159a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 853a3b78b82e242750e30099f847045ff590f125
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-maximum-connection-limit-to-the-sap-server"></a>Configurer la limite maximale de connexions au serveur SAP
Le fournisseur de données pour SAP permet aux clients de l’adaptateur contrôler le nombre maximal de connexions qui peuvent être ouverts en interne par le fournisseur. Vous pouvez le contrôler en définissant la variable d’environnement CPIC_MAX_CONV.  
  
 Par exemple, si CPIC_MAX_CONV est définie sur n’importe quelle valeur numérique, le nombre de connexions RFC ouvert à tout moment sera inférieur ou égal à cette valeur numérique.  
  
> [!NOTE]
>  La valeur numérique s’applique pour chaque serveur individuellement sous le processus/domaine d’application qui définit cette valeur.  
  
 Par exemple, si une application à l’aide du fournisseur de données pour SAP, a défini la variable d’environnement au niveau du processus à « x » et se connecte à deux serveurs différents, A et B, puis le nombre maximal de connexions à la fois pour A et B sera « x » respectivement.