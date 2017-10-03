---
title: "Conditions préalables pour le didacticiel Double Action de RosettaNet dans BizTalk Server | Documents Microsoft"
description: "Conditions préalables pour parcourir le didacticiel Double Action pour l’accélérateur RosettaNet (BTARN) dans BizTalk Server"
ms.custom: 
ms.date: 08/09/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1ce8a122-cd16-450a-84bd-bb6beee7af40
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87e2750a16d2c65b5838b6d61f27cbd2b2ff9885
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="prepare-for-the-double-action-tutorial"></a>Préparer pour le didacticiel Double Action

## <a name="prerequisites"></a>Conditions préalables
Avant de commencer le didacticiel :
  
-   Effectuez une installation complète de BizTalk Server et [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] sur deux ordinateurs. Pour plus d’informations, consultez [installer et configurer](install-configure-biztalk-accelerator-for-rosettanet.md).  
  
    > [!IMPORTANT]
    >  Veillez à configurer entièrement l’accélérateur RosettaNet, y compris le démarrage des orchestrations BTARN. Consultez [installer et configurer](install-configure-biztalk-accelerator-for-rosettanet.md).
  
-   Ce didacticiel simule un scénario réel à l’aide de deux ordinateurs au lieu d’un seul ordinateur avec un accord de bouclage. Chaque fois que ce didacticiel utilise des noms d’ordinateur, il utilise un espace réservé. Remplacez cet espace réservé par le nom réel de l’ordinateur choisi. Par exemple, si l’ordinateur qui exécute votre solution de Contoso est nommé **Contoso**, remplacez toutes les occurrences dans le didacticiel de \\ \\< contoso**_**  *ordinateur*> portant ce nom d’ordinateur.  
  
-   Ce didacticiel favorise une communication sécurisée au moyen de certificats entre Contoso et Fabrikam. Vous devez générer des certificats que vous avez besoin et les installer sur leurs ordinateurs respectifs.  
  
## <a name="next-steps"></a>Étapes suivantes 
  
-   [Étape 1 : Création d’une autorité de Certification](../../adapters-and-accelerators/accelerator-rosettanet/step-1-creating-a-certification-authority.md)  
  
-   [Étape 2 : Création publiques et privées des certificats](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-public-and-private-certificates.md)  
  
-   [Étape 3 : Importation publiques et privées des certificats](../../adapters-and-accelerators/accelerator-rosettanet/step-3-importing-public-and-private-certificates.md)  
  
-   [Étape 4 : Sécurisé Sockets Layer dans IIS](../../adapters-and-accelerators/accelerator-rosettanet/step-4-enabling-secure-sockets-layer-in-iis.md)