---
title: "Groupes d’adaptateurs et adaptateurs de groupe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e0a9423-99dd-4474-afa1-fd8e1d074cd1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fcf10f50857026893245cc567783b649f614c4f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-groups-and-group-adapters"></a>Groupes d’adaptateurs et adaptateurs de groupe
Un *groupe d’adaptateurs* est un mécanisme d’administration que vous pouvez utiliser pour collecter et organiser un ensemble de cartes. En revanche, un *adaptateur de groupe* est un composant qui dessert tous les adaptateurs dans un groupe d’adaptateurs. Par exemple, vous pouvez écrire un ensemble d'adaptateurs qui utiliseront le même composant COM pour transmettre les synchronisations des mots de passe via TCP/IP. Cet ensemble constitue le groupe d'adaptateurs, tandis que le composant qui les dessert est l'adaptateur de groupe. Les groupes d'adaptateurs sont décrits dans la configuration stockée. Vous pouvez extraire des informations et des mises à jour pour un groupe d'adaptateurs à l'aide d'`ISSOPSAdapter.ReceiveNotification`.  
  
 Un adaptateur de groupe porte le même nom que le groupe d'adaptateurs. En dehors de cette restriction, c'est un adaptateur tout à fait normal. Par exemple, un adaptateur de groupe peut être associé à des propriétés de configuration et à des groupes d'accès indépendants, tel que décrit dans son fichier de configuration. Il réside vraisemblablement sur le même ordinateur que les adaptateurs du groupe. Toutefois, cela n'est pas systématique. De même, on peut s'attendre à ce que tous les adaptateurs d'un groupe résident sur le même ordinateur.  
  
 Avec `ISSOPSAdapter.InitializeAdapter`, vous pouvez accéder à un adaptateur de groupe et l'initialiser pendant le démarrage. Lors de cette initialisation, le système renseigne l'adaptateur sur tous les adaptateurs du groupe qui résident sur le système. De plus, le système envoie des notifications à l'adaptateur de groupe chaque fois qu'un adaptateur est ajouté au groupe, supprimé, activé ou désactivé. Toutefois, l'adaptateur de groupe n'est pas averti des changements de mot de passe.  
  
 Les groupes d'adaptateurs et les adaptateurs de groupe sont facultatifs avec l'outil Administration.  
  
## <a name="see-also"></a>Voir aussi  
 [Adaptateurs de synchronisation de mot de passe](../core/password-sync-adapters.md)