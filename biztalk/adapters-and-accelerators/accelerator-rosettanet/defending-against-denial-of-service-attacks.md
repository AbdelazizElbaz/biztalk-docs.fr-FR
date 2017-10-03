---
title: "Protection contre les attaques par déni de Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, denial-of-service attacks
- denial-of-service attacks
ms.assetid: 63342d7a-a5df-4e11-9037-93175d8f7ea7
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 667b9d321f7703f770297b001ef2a99be2bf4902
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="defending-against-denial-of-service-attacks"></a>Protection contre les attaques par déni de Service
Une personne a pu démarrer une attaque par déni de service par rapport à une installation de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] en mettant l’accent sur le fichier RNIFReceive.aspx reçoit la page. Il peuvent le faire en envoyant un grand nombre de messages vides à cette page. Si la page de gauche est désactivé, qu'une telle attaque peut inonder le journal des événements avec des événements publiés par le ASPX s’affiche.  
  
## <a name="defending-against-an-attack"></a>Protection contre une attaque  
 Pour protéger le serveur contre les attaques de déni de service, il est recommandé de mettre à jour le journal des événements à une taille raisonnable et de prendre des mesures pour traiter un nombre excessif d’événements. Pour cela en définissant la taille maximale du journal, en sélectionnant un moyen de remplacement des événements, ou à l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]® Management Instrumentation (WMI) pour gérer la taille du journal. Pour plus d’informations, consultez l’aide de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsWinSvrNoVersion](../../includes/btswinsvrnoversion-md.md)]™.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer la configuration, les certificats, les bases de données et la sécurité](manage-configuration-certificates-databases-security.md)