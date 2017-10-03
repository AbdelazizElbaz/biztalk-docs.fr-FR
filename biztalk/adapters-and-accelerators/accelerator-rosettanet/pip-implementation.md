---
title: "Implémentation d’un PIP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PIPs
- PIPs, element-level constraints
- Document Type Definitions (DTDs)
- PIPs, schemas
- examples, schemas
- schemas, examples
- PIPs, about PIPs
- element-level constraints
- PIPs, DTDs
- schemas, PIPs
- XML Schema Definition files (XSDs)
- Partner Interface Processes (PIPs)
- DTDs, XSDs
- schemas, XSDs
ms.assetid: 0d964223-e0b6-4377-b26a-5fdc89ec81f4
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70d845aa99910125a64e8a0744c4b3ef42d40f09
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="pip-implementation"></a>Implémentation d’un PIP
Processus d’Interface RosettaNet partenaires (PIP) définissent des processus d’entreprise entre partenaires commerciaux dans une chaîne d’approvisionnement. [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]fournit un ensemble de PIP out of box et que vous pouvez créer des PIP supplémentaires. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]prend en charge toutes les adresses PIP défini par l’organisation RosettaNet.  
  
 Pour plus d’informations, consultez [PIP de RosettaNet](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-pips.md).  
  
## <a name="schemas-in-btarn"></a>Schémas de BTARN  
 RosettaNet Spécifie tous les schémas de message PIP sous la forme d’un Type de Document (DTD). Partenaires commerciaux qui participent à l’échange de documents professionnels doivent respecter ces DTD. Toutefois, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] implémente ces DTD en tant que fichiers de définition de schéma XML (XSD), car Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] représente des documents à l’aide de XSD, pas les DTD. XSD remplacent les DTD en termes de fonctionnalités et peuvent représenter la plupart des informations fournies dans les instructions du message en mode natif.  
  
> [!NOTE]
>  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]prend également en charge des PIP de nouvelle génération, récemment publiées par l’organisation RosettaNet, qui utilisent des spécifications de XSD.  
  
 Pour implémenter un PIP de nouveau, vous devez convertir DTD du PIP dans un fichier XSD. Téléchargement de la DTD associée à l’adresse PIP sur le site Web de RosettaNet à [http://go.microsoft.com/fwlink/?linkid=33859](http://go.microsoft.com/fwlink/?linkid=33859). Vous créez ensuite un [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] traiter le profil de configuration basé sur le PIP. Pour plus d’informations, consultez [comprenant un nouveau Partner Interface Process](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md).  
  
 Vous pouvez créer un nouveau profil de configuration de processus basé sur un profil existant. Pour plus d’informations, consultez [comment créer ou modifier une Configuration de processus](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md). Vous pouvez créer plusieurs contrats basés sur le même profil de configuration de processus entre les partenaires mêmes. Toutefois, vous pouvez activer uniquement un d’eux à la fois. Pour créer et activer un accord, consultez [création ou modification d’un accord](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]implémente XSD avec les contraintes de la règle de message RosettaNet pour les en-têtes de RosettaNet suivants :  
  
-   Préambule pour RNIF 1.1 et RNIF 2.01  
  
-   En-tête de service pour RNIF 1.1 et RNIF 2.0  
  
-   En-tête de remise pour RNIF 2.0  
  
-   Contenu du service pour tous les messages de signal de RNIF 1.1 et RNIF 2.01.  
  
## <a name="sample-schemas"></a>Exemples de schémas  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]le programme d’installation installe un ensemble d’adresses PIP dans \< *lecteur*> : \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\Schemas. Voici à titre d’exemple uniquement. Avant de les utiliser en production, il est recommandé que vous comparez ces schémas par rapport à la dernière version des spécifications PIP RosettaNet publiées et instructions du message. BTARN prend en charge l’implémentation de toutes les adresses PIP de RosettaNet.  
  
## <a name="element-level-constraints-in-btarn"></a>Contraintes au niveau de l’élément dans BTARN  
 Dans BTARN, vous implémentez les contraintes au niveau de l’élément spécifiés dans les documents d’indications de message PIP comme paramètres de configuration de processus. Composants d’exécution utilisent la configuration de processus pour déterminer comment traiter un PIP spécifique.  
  
 Pour implémenter un PIP de nouveau, vous devez appliquer les contraintes d’indications de message pour le PIP en créant un nouveau profil de configuration de processus. Pour cela, dans la Console de gestion BTARN. Pour plus d’informations, consultez [comment créer ou modifier une Configuration de processus](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).  
  
 Le profil de configuration de processus correspond à la spécification PIP RosettaNet, comme indiqué dans [à l’aide de la spécification PIP pour créer une Configuration de processus](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [BizTalk Accelerator for RosettaNet ajoutée à BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md)   
 [Accords de partenariat commercial](../../adapters-and-accelerators/accelerator-rosettanet/trading-partner-agreements.md)   
 [PIP de RosettaNet](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-pips.md)