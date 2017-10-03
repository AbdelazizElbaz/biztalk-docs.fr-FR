---
title: "Importer le Pack d’administration analyse BizTalk Server 2013 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bee2bfe9-4eb0-46d4-8eee-75182202080c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c6dff55cce17d9b9159a8eca754f91373621929
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="import-the-biztalk-server-2013-monitoring-management-pack"></a>Importer le Pack d’administration analyse BizTalk Server 2013
Pour obtenir des instructions sur l’importation d’un Pack d’administration, consultez Comment importer un Pack d’administration dans [Operations Manager 2007 R2/2012](http://go.microsoft.com/fwlink/?LinkId=142351) (http://go.microsoft.com/fwlink/?LinkId=142351). Après le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration est importé, suivez ces procédures pour terminer la configuration initiale :  
  
### <a name="to-configure-the-management-pack"></a>Pour configurer le Pack d’administration  
  
1.  Créer un pack d’administration dans lequel vous stockez les remplacements et autres personnalisations.  
  
2.  Pour activer le paramètre Agent Proxy, procédez comme suit :  
  
    1.  Ouvrez la console Opérateur, puis sur le bouton Administration.  
  
    2.  Dans le volet administrateur, cliquez sur **géré par Agent**.  
  
    3.  Double-cliquez sur un agent dans la liste.  
  
    4.  Sous l’onglet sécurité, sélectionnez **autoriser cet agent à agir en tant que proxy et détecter des objets gérés sur d’autres ordinateurs**.  
  
    5.  Répétez les étapes 3 et 4 pour chaque agent qui est installé sur un serveur BizTalk Server.