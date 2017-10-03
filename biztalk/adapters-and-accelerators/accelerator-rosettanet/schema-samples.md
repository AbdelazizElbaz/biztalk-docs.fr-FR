---
title: "Les exemples de schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SDK samples, schemas
- examples, schemas
- schemas, examples
ms.assetid: 7d7e696d-935f-4582-b873-c5637673b651
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f346d2e7258c14e09dbcdc5f29ff0f7690cb4a4c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schema-samples"></a>Exemples de schémas
Le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK inclut un ensemble de schémas XSD pour le traitement RNIF et processus PIP (Partner Interface). [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]utilise ces schémas pour traiter les messages. Vous pouvez modifier ces schémas à des fins personnelles, ou les utiliser pour résoudre les problèmes.  
  
 Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK fournit trois types de schémas. Ces schémas sont les schémas XSD associés PIP de RosettaNet, des schémas de nouvelle génération de RosettaNet et des schémas RNIF.  
  
## <a name="xsd-schemas-associated-with-rosettanet-pips"></a>Schémas XSD associés PIP de RosettaNet  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]utilise ces schémas pour valider le contenu de service des instances de message. Vous pouvez modifier ces schémas pour modifier le traitement des messages. Vous pouvez également utiliser les schémas pour valider les instances de message lors de la résolution des erreurs lors du traitement du contenu du service.  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]a compilé les ces schémas dans l’assembly RNPIPs. Vous pouvez modifier l’un de ces schémas à l’annulation du déploiement de l’assembly RNPIPs, modification du schéma, puis redéployer RNPIPs. Vous devez veiller à ne pas modifier le schéma. Si vous modifiez le schéma, vos modifications ne peuvent pas se conformer le PIP RosettaNet correspondant. Vous pouvez également ajouter un schéma à RNPIPs. Pour plus d’informations, consultez [modifiant un PIP existants dans RNPIPs](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md).  
  
 Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] programme d’installation installe ces schémas dans \< *lecteur*> : \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version > Accelerator for RosettaNet\SDK\Schemas.  
  
## <a name="rnif-schemas"></a>Schémas RNIF  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]utilise ces schémas pour valider des parties de message RNIF, tels que le préambule, en-tête de service et en-tête de remise. Cela inclut également les schémas pour les exceptions et les accusés de réception.  
  
 Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] programme d’installation installe ces schémas dans \< *lecteur*> : \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version > Accelerator for RosettaNet\SDK\RNIFSchemas.  
  
## <a name="rosettanet-next-generation-schemas"></a>Schémas de nouvelle génération de RosettaNet  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]utilise ces schémas pour valider les messages conformes aux schémas de nouvelle génération pour RosettaNet. Ces schémas prennent en charge XSD en mode natif, au lieu de la DTD. Pour utiliser ces schémas, les ajouter à l’assembly RNPIPs comme décrit dans [modifiant un PIP existants dans RNPIPs](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md).  
  
 Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] programme d’installation installe ces schémas dans le \< *lecteur*> : \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version > Accelerator for RosettaNet\SDK\Schemas\ Dossiers Domain, \Interchange et \Universal.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’un PIP](../../adapters-and-accelerators/accelerator-rosettanet/pip-implementation.md)   
 [Utilisation des adresses PIP](../../adapters-and-accelerators/accelerator-rosettanet/working-with-pips.md)   
 [Exemples](../../adapters-and-accelerators/accelerator-rosettanet/samples3.md)