---
title: "Étape 3 : Modifier le Partner Interface Process | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying, PIPs
- PIPs, modifying
- loopback tutorial, modifying PIPs
ms.assetid: 4d03c598-8ed4-4135-9748-ede101997fd0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b9640f542a55d028f3df8715c49df0e9e9ad370
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-edit-the-partner-interface-process"></a>Étape 3 : Modifier le Partner Interface Process
Dans cette étape, vous modifiez les paramètres de configuration de processus PIP (Partner Interface) pour désactiver le transport sécurisé si vous n’avez pas d’un certificat SSL Secure Sockets Layer () configuré dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® Internet Information Services (IIS). Étant donné que le scénario de bouclage ne prend pas en charge la signature des messages entrants et sortants, vous devez modifier les paramètres par défaut pour continuer le didacticiel. Vous modifiez le PIP STD_0C1_R01.02.  
  
### <a name="to-edit-the-std0c1r0102-pip"></a>Pour modifier le PIP STD_0C1_R01.02  
  
1.  Dans le  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Management Console, développez **BizTalk \<version > Accelerator for RosettaNet**, cliquez sur **paramètres de Configuration de processus**, avec le bouton droit **STD_0C1_R01.02**, puis cliquez sur **propriétés**.  
  
2.  Dans la boîte de dialogue STD_0C1_R01.02Properties sur le **activité** onglet, définissez la **Transport est sécurisé requis** option `False`. Effectuez cette étape uniquement si vous n’avez pas d’un certificat SSL sur votre serveur Web IIS.  
  
3.  Définir le **non-répudiation requis** à `False`, définissez **autorisation obligatoire** à `False`, définissez **non-répudiation de l’origine et du contenu** à `False`, puis cliquez sur **OK**.  
  
     Cela désactive la non répudiation et l’utilisation de certificats pour la signature des messages.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 4 : Créer un accord commercial](../../adapters-and-accelerators/accelerator-rosettanet/step-4-create-a-trade-agreement.md)   
 [Propriétés d’autorisation et de non-répudiation](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md)