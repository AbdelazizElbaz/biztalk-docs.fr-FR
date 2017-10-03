---
title: "Configuration requise pour le didacticiel sur les processus de RosettaNet privé dans BizTalk Server | Documents Microsoft"
description: "Conditions préalables pour parcourir le didacticiel les processus privés pour l’accélérateur RosettaNet (BTARN) dans BizTalk Server"
caps.latest.revision: "7"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 08/09/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89631ce3-f5af-4d30-b22f-6d20f595295f
ms.author: mandia
ms.openlocfilehash: 4da7190c7212f74a90689ca403d899eb1a849cc5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="prepare-for-the-private-process-tutorial"></a>Préparer pour le didacticiel sur les processus privés

## <a name="prerequisites"></a>Conditions préalables
Avant de commencer le didacticiel :
  
-   Effectuez une installation complète de BizTalk Server et [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] sur deux ordinateurs. Pour plus d’informations, consultez [installer et configurer](install-configure-biztalk-accelerator-for-rosettanet.md).  
  
    > [!IMPORTANT]
    >  Veillez à configurer entièrement l’accélérateur RosettaNet, y compris le démarrage des orchestrations BTARN. Consultez [installer et configurer](install-configure-biztalk-accelerator-for-rosettanet.md). Vous devrez peut-être également ajouter le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] des répertoires virtuels (y compris les btarnhttpreceive) à la liste d’exclusion du chemin d’accès géré Microsoft Windows® SharePoint™ Services. 
  
-   Ce didacticiel simule un scénario réel à l’aide de deux ordinateurs au lieu d’un seul ordinateur avec un accord de bouclage. Chaque fois que ce didacticiel utilise des noms d’ordinateur, il utilise un espace réservé comme nom d’ordinateur. Remplacez cet espace réservé par le nom réel de l’ordinateur choisi. Par exemple, si l’ordinateur qui exécute votre solution de Contoso est nommé **Contoso**, remplacez toutes les occurrences dans le didacticiel de \\ \\< contoso**_**  *ordinateur*> portant ce nom d’ordinateur.  
  
 Ce didacticiel favorise une communication sécurisée au moyen de certificats entre Contoso et Fabrikam. Vous devez générer des certificats que vous avez besoin et les installer sur les ordinateurs respectifs.  
  
## <a name="next-steps"></a>Étapes suivantes
  
-   [Restauration de la base de données Contoso](../../adapters-and-accelerators/accelerator-rosettanet/restoring-the-contoso-database.md)  
  
-   [Génération et l’activation de certificats](../../adapters-and-accelerators/accelerator-rosettanet/generating-and-enabling-certificates.md)