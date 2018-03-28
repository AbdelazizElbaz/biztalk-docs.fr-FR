---
title: Propriétés d’autorisation et de Non répudiation | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- authorization properties
- non-repudiation, properties
ms.assetid: e752b95b-9dae-4403-8f3e-3a0a50acd519
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7018ac2d66455359215db78b17e80414d176f99f
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="authorization-and-non-repudiation-properties"></a>Propriétés d'autorisation et de non-répudiation
Cette rubrique décrit le comportement des propriétés `Is Authorization Required`, `Non-Repudiation of Origin and Content`et `Non-Repudiation Required (Acknowledgement of Receipt)` des processus PIP (Partner Interface Processes). Elle décrit également les combinaisons de ces propriétés qui [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] prend en charge.  
  
 Vous définissez ces propriétés sur le **activité** onglet des propriétés de Configuration de processus dans la section Paramètres de Configuration de processus de le [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] Console de gestion. Pour plus d’informations, consultez [comment créer ou modifier une Configuration de processus](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).  
  
## <a name="property-behavior"></a>Comportement de la propriété  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] présente le comportement suivant en fonction des paramètres de la `Is Authorization Required`, `Non-Repudiation of Origin and Content`, et `Non-Repudiation Required (Acknowledgement of Receipt)` propriétés.  
  
|Propriété|Comportement quand le paramètre est Vrai|Comportement quand le paramètre est Faux|  
|--------------|------------------------|-------------------------|  
|`Is Authorization Required`|Les messages d’action ou de signal entrants doivent être signées ; dans le cas contraire, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] rejette le message. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] n’accepte pas le document commercial si la personne/le rôle n’est pas autorisé à effectuer l’activité.|Les messages d'action ou de signal entrants n'ont pas à être signés. Une autorisation simple est toujours appliquée avec le numéro DUNS du partenaire à partir des parties d'en-tête RNIF du message.|  
|`Non-Repudiation of Origin and Content`|Les messages d'action ou de signal sortants sont signés. Les messages d'action sont stockés sous leur forme d'origine reçue dans la table MessageStorageOut de la base de données BTARNDATA.|Les messages d'action ou de signal sortants ne sont pas stockés.|  
|`Non-Repudiation Required (Acknowledgement of Receipt)`|Les messages d'action ou de signal entrants doivent être signés. Le message entrant est stocké dans la table MessageStorageIn de la base de données BTARNDATA. Une synthèse du message doit être incluse dans l'accusé de réception.|Les messages d'action ou de signal entrants ne sont pas stockés.|  
  
## <a name="property-support"></a>Prise en charge des propriétés  
 Le tableau suivant présente [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] prise en charge pour les combinaisons de le `Is Authorization Required`, `Non-Repudiation of Origin and Content`, et `Non-Repudiation Required (Acknowledgement of Receipt)` propriétés.  
  
> [!IMPORTANT]
>  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] doit soit signer les messages d’action et les messages de signal, ou les messages d’action ni messages uniques. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] est pas prise en charge des actions de signature, mais ne pas la signature des signaux, ou vice versa.  
  
> [!IMPORTANT]
>  Si [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] se connecte à un message sortant, il doit enregistrer le message dans la table MessageStorageOut de la base de données BTARNArchive.  
  
|Is Authorization Required|Non-Repudiation of Origin and Content|Non-Repudiation Required (Acknowledgement of Receipt)|Prise en charge par BTARN ?|  
|-------------------------------|--------------------------------------------|--------------------------------------------------------------|-------------------------|  
|`False`|`False`|`False`|Oui|  
|`False`|`False`|`True`|Non*|  
|`False`|`True`|`False`|Non**|  
|`False`|`True`|`True`|Non***|  
|`True`|`False`|`False`|Oui****|  
|`True`|`False`|`True`|Oui****|  
|`True`|`True`|`False`|Oui|  
|`True`|`True`|`True`|Oui|  
  
 \* [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] ne prend pas en charge cette combinaison, car elle requiert que les signaux soient signés et actions ne pas signé.  
  
 ** [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] ne prend pas en charge cette combinaison, car elle requiert que les actions être signé et ne pas les signaux soient signés.  
  
 *** [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] ne prend pas en charge cette combinaison, car la définition de non répudiation sur `True` pour les actions et les signaux signifie que [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] effectue une autorisation. Cette combinaison n'est donc pas valide.  
  
 Lorsque vous définissez `Is Authorization Required` à `True` et `Non-Repudiation of Origin and Content` à `False`, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] stocke le message dans la table de non répudiation.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour créer ou modifier une configuration de processus](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)