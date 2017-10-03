---
title: Surveillance | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7effa38f-f9f2-40b7-8d8b-fa13cf94aa4f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9c45bb70e3f92f4c85def07add4390a0451cb87
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring"></a>Surveillance
Par défaut, tous les surveillance de BizTalk Server et les tâches utilisent le compte d’action par défaut lorsqu’il en existe qu'aucun compte d’identification spécifique ne défini pour la cible dans le profil d’identification du compte d’analyse de BizTalk Server. Pour configurer un compte d’identification avec l’ensemble minimal d’autorisations requis pour BizTalk Server à des fins d’analyse, les autorisations suivantes sont requises :  
  
-   Le compte doit être membre du groupe Administrateurs intégré et le groupe utilisateurs d’analyses de performances de l’ordinateur analysé.  
  
-   Le compte doit être membre du rôle SysAdmin dans l’ou les instances qui héberge les bases de données et les travaux pour le groupe BizTalk en cours d’analyse SQL.  
  
-   Pour que BizTalk Server à des fins d’analyse, le compte doit être une partie du groupe des opérateurs BizTalk.  
  
-   Pour exécuter des tâches via la console SCOM, le compte doit être une partie du groupe d’utilisateurs d’applications BizTalk.  
  
-   Pour effectuer des tâches d’administration, le compte doit être une partie du groupe Administrateurs de BizTalk.