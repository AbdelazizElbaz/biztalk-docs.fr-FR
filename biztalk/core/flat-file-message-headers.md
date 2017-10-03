---
title: "Les en-têtes de Message de fichier plat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1981daaf-149a-426d-9a2f-5fcf64bce185
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 271e9fe74d0a55f4b3ff5271861d24474fffaf37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="flat-file-message-headers"></a>En-têtes de message de fichier plat
L’analyse de l’en-tête de message d’instance fichier plat facultatif par le désassembleur de fichier plat est contrôlée par le schéma de fichier plat que vous avez configuré dans le **schéma d’en-tête** propriété au moment du design du désassembleur de fichier plat ou **XMLNORM. HeaderSpecName** propriété de contexte de message. Si vous n'avez pas spécifié de schéma utilisant une de ces deux méthodes, le désassembleur de fichier plat suppose que le message d'instance de fichier plat ne contient pas d’en-tête.  

## <a name="outbound-messages"></a>Messages sortants  
 Pour les messages d’instance de fichier plat sortants, vous pouvez configurer l’assembleur de fichier plat pour produire un en-tête en spécifiant le schéma approprié dans son **nom de la spécification en-tête** propriété au moment du design ou **XMLNORM. HeaderSpecName** propriété de contexte de message. Pour plus d’informations sur la définition des propriétés de contexte de message, consultez **propriétés de contexte de Message** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  

## <a name="inbound-messages"></a>Les messages entrants  
 Les données figurant dans les en-têtes de message d'instance de fichier plat entrants peuvent être conservées et utilisées de deux façons différentes. D’abord, les en-têtes de message d’instance de fichier plat peuvent être intégralement enregistrés au sein du contexte de message du corps pour être ensuite restaurés en tant qu'en-têtes d'un message d'instance de fichier plat sortant correspondant. Vous pouvez utiliser la **Preserve en-tête** propriété du pipeline de réception pour spécifier que l’en-tête doit être conservé. Si un en-tête est spécifié dans l'assembleur de fichier plat, l'en-tête préservé sera utilisé dans les messages sortants.  
  
 Sinon, vous pouvez copier les éléments de données individuels d’un en-tête de message d'instance de fichier plat dans le contexte de message associé au corps du message de fichier plat en spécifiant la promotion de propriété d'un ou plusieurs champs du schéma correspondant. Pour plus d’informations sur la promotion des propriétés, consultez [promotion des propriétés](../core/promoting-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Corps de Message de fichier plat](../core/flat-file-message-bodies.md)   
 [Codes de Message de fichier plat](../core/flat-file-message-trailers.md)   
 [Structure d’un Message de fichier plat](../core/structure-of-a-flat-file-message.md)   
 [Comment créer des schémas pour les Messages de fichier plat](../core/how-to-create-schemas-for-flat-file-messages.md)