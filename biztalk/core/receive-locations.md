---
title: "Emplacements de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, properties
- receive locations, about receive locations
- receive locations
- receive locations, receive location types
ms.assetid: be5f7e5d-b63f-42f6-985e-895ba3912d34
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9866edd5dfa6f953c4e847f191891bd7e6bc25ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-locations"></a>Emplacements de réception
La création d'un emplacement de réception implique la spécification d'une adresse à laquelle parviennent les messages entrants et du pipeline qui traite les messages reçus à cette adresse. Seuls les administrateurs peuvent créer et activer des emplacements de réception.  
  
 Un administrateur utilise la console Administration de BizTalk pour créer des emplacements de réception, les lier à des orchestrations, les activer et les désactiver, et définir leurs propriétés générales.  
  
 Un administrateur (utilisant la console Administration de BizTalk) suit les étapes ci-dessous pour créer un emplacement de réception :  
  
1.  Il crée un emplacement de réception.  
  
2.  Il associe l'emplacement de réception à un hôte.  
  
3.  Il lie l'emplacement de réception à une orchestration.  
  
4.  Il active l'emplacement de réception.  
  
5.  L'emplacement de réception reçoit des messages.  
  
> [!NOTE]
>  Les modifications apportées aux emplacements de réception à l'aide de Windows Management Instrumentation (WMI) ont des répercussions sur l'affichage de ces emplacements dans la console Administration de BizTalk. Par exemple, si un administrateur utilise WMI pour créer un emplacement de réception, celui-ci s'affiche dans la console Administration de BizTalk. De même, si un administrateur supprime un emplacement de réception, celui-ci n'apparaît plus dans la console Administration de BizTalk.  
  
> [!IMPORTANT]
>  Le nom de chaque emplacement de réception doit être unique. Deux emplacements de réception ne peut pas avoir le même nom dans le même [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]déploiement.  
  
> [!IMPORTANT]
>  Il est conseillé de définir des listes de contrôle d'accès renforcées dans l'emplacement de dépôt des emplacements de réception. Par exemple, vous devez définir des listes de contrôle d'accès renforcées pour le répertoire dans lequel l'emplacement de réception des fichiers sélectionne des messages, afin que seuls les utilisateurs autorisés puissent déposer des messages dans cet emplacement.  
  
## <a name="receive-location-types"></a>Types d'emplacements de réception  
 Il existe deux types d'emplacements de réception :  
  
-   Unidirectionnel : utilisé pour les applications qui suppriment un message et n'attendent pas de réponse synchrone.  
  
-   Requête-réponse : utilisé avec les applications qui exigent une réponse à un message.  
  
## <a name="receive-location-properties"></a>Propriétés des emplacements de réception  
 Les emplacements de réception sont associés à des propriétés globales et propres à l'adaptateur. Les administrateurs, à l’aide de la Console Administration de BizTalk, définir des propriétés globales pour tous les emplacements de réception associés à une carte spécifique.  
  
 Les modifications sont apportées de manière séquentielle aux propriétés des emplacements de réception. Si un développeur de solutions modifie une valeur de propriété pour spécifique à un emplacement de réception, la nouvelle valeur remplace la valeur de propriété globale pour cet emplacement de réception que définie par l’administrateur dans la Console Administration de BizTalk.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des emplacements de réception](../core/managing-receive-locations.md)   
 [Artefacts](../core/artifacts.md)