---
title: "Profils d’identification | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98ac0a0c-91d8-4d12-aa40-2ad2e29ec784
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69fa6c9401f606619b2fb8d22d95ded48c18a092
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-as-profiles"></a>Profils d’identification
Lorsque BizTalk Server Core Library Management Pack est importé tout d’abord, il crée deux nouveaux profils d’identification :  
  
-   **Compte de découverte de BizTalk Server**. Ce profil est associé à toutes les détections des composants de rôles de BizTalk Server.  
  
-   **Compte de surveillance de BizTalk Server**. Ce profil est associé à tous les moniteurs et tâches.  
  
 Par défaut, toutes les découvertes, moniteurs et tâches définies dans la valeur par défaut des packs d’administration de BizTalk Server à l’aide des comptes définis dans le « Compte d’Action par défaut » profil d’identification.  Si le compte d’action par défaut d’un système donné ne dispose pas des autorisations nécessaires pour découvrir ou surveiller BizTalk, ces systèmes peuvent être liés aux informations d’identification plus spécifiques dans les BizTalk Server profils d’identification, qui ont accès à BizTalk Server.  
  
 Voici la procédure générique pour configurer des profils d’identification pour BizTalk Server :  
  
### <a name="to-configure-run-as-profiles"></a>Pour configurer des profils d’identification  
  
1.  Déterminez le nom du ou des ordinateurs cibles où le compte d’action par défaut dispose de droits suffisants pour surveiller BizTalk Server.  
  
2.  Pour chaque système de créer ou utiliser un jeu existant d’informations d’identification qui disposent au moins les privilèges de BizTalk Server décrits dans le [les environnements à faible privilège](../technical-guides/low-privilege-environments.md) section de ce guide du Pack d’administration.  
  
3.  Pour chaque ensemble d’informations d’identification identifié à l’étape 2, assurez-vous que les exécuter en tant que compte correspondant existe dans le groupe d’administration. Créer le compte d’identification s’il est nécessaire.  
  
4.  Configurer les mappages entre les cibles et les exécuter en tant que compte (s) sur le **comptes d’identification** onglet de chacune des profils d’identification.