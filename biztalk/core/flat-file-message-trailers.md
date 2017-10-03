---
title: Codes de fin de fichier plat Message | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfe115a5-4fdc-4779-94f3-437b5a06fbd4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7cbeaef3f23de3cb89d873413964cd331ec23f43
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="flat-file-message-trailers"></a>Codes de fin de message de fichier plat
Comme avec les en-têtes de message d’instance de fichier plat, l’analyse du code de fin de message d’instance fichier plat facultatif par le désassembleur de fichier plat est contrôlée par le schéma de fichier plat que vous avez configuré dans le **schéma de code de fin** au moment du design propriété désassembleur de fichier plat ou **XMLNORM. TrailerSpecName** propriété de contexte de message. Si vous n'avez pas spécifié de schéma utilisant une de ces deux méthodes, le désassembleur de fichier plat supposera que le message d'instance de fichier plat ne contient pas de code de fin.  
  
 À la différence des en-têtes de message d'instance de fichier plat, les codes de fin de message d'instance de fichier plat ne peuvent ni être enregistrés et restaurés en tant qu'unité unique, ni utiliser la promotion de propriété pour copier des éléments individuels de données dans le contexte de message associé au corps de message d'instance de fichier plat. Toutefois, un code de fin peut être ajouté à un message d’instance de fichier plat sortants en spécifiant le schéma approprié dans le **schéma de code de fin** propriété au moment du design de l’assembleur de fichier plat ou **XMLNORM. TrailerSpecName** propriété de contexte de message. Les données qui constituent la partie variable du code de fin peuvent être spécifiées en utilisant la rétrogradation de propriétés du contexte de message du corps de message d'instance de fichier plat ou en spécifiant des valeurs par défaut ou fixes dans le schéma correspondant.  
  
## <a name="see-also"></a>Voir aussi  
 [En-têtes de Message de fichier plat](../core/flat-file-message-headers.md)   
 [Corps de Message de fichier plat](../core/flat-file-message-bodies.md)   
 [Structure d’un Message de fichier plat](../core/structure-of-a-flat-file-message.md)   
 [Comment créer des schémas pour les Messages de fichier plat](../core/how-to-create-schemas-for-flat-file-messages.md)