---
title: "Création ou modification d’une Configuration de processus | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process configuration, modifying
- process configuration, creating
- creating, process configuration
- modifying, process configuration
ms.assetid: 39cc2c93-0986-48d3-8c6f-4280ec9af4e0
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9130ab7370f8f6e1fcbe75bc7a85a6c74dfe328
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-or-editing-a-process-configuration"></a>Création ou modification d’une Configuration de processus
Cette section décrit comment créer ou modifier une configuration de processus pour implémenter un processus PIP (Partner Interface) dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]. Une adresse PIP RosettaNet définit une boîte de dialogue du processus d’entreprise entre deux partenaires commerciaux. Dans [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], pour créer une adresse PIP avec un partenaire, vous devez d’abord créer une configuration de processus. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]utilise ce profil pour stocker toutes les caractéristiques de configuration du PIP. Vous pouvez ensuite utiliser cette configuration pour créer un accord avec le partenaire.  
  
 Pour plus d’informations sur les propriétés de configuration de processus et procédures pour créer ou modifier une configuration de processus, consultez [comment créer ou modifier une Configuration de processus](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).  
  
 Pour créer une nouvelle configuration de processus, vous devez baser les paramètres sur le document de spécification PIP gérées par l’organisation RosettaNet. Configuration de processus de tous les paramètres proviennent de spécifications PIP, et [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] remplit la plupart des paramètres avec les valeurs par défaut qui sont les valeurs généralement utilisées pour les champs. Vous devez vérifier que les paramètres correspondent aux valeurs dans la spécification PIP appropriée. Pour plus d’informations sur la façon dont les paramètres PIP que vous entrez mappent à l’aide de la spécification PIP, consultez [à l’aide de la spécification PIP pour créer une Configuration de processus](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md).  
  
 La configuration de processus peut être de RosettaNet ou CIDX (Chemical Industry Data Exchange). Pour plus d’informations sur une configuration CIDX, consultez [paramètre des CIDX chem échange de messages](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md).  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]ne prend pas en charge la modification d’une configuration de processus lorsqu’il y a les processus actifs. Si vous le faites, les processus actifs terminera avec des erreurs. Tous les nouveaux processus reprendra correctement les nouveaux paramètres de configuration.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment créer ou modifier une Configuration de processus](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)  
  
-   [Pour créer une Configuration de processus à l’aide de la spécification PIP](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md)  
  
-   [Propriétés d’autorisation et de non-répudiation](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md)  
  
-   [Paramètre des CIDX chem échange de messages](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md)