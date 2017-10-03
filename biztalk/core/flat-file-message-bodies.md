---
title: Corps de Message de fichier plat | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 097e49a1-75d2-44a4-9372-d78de7b7597c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2de8748d9a36c817f7db8fed96a59c8d2bd7dda2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="flat-file-message-bodies"></a>Corps de message de fichier plat
Le corps de message d’instance de fichier plat est obligatoire. Il correspond à ce que le désassembleur de fichier plat traite en tant qu’un ou plusieurs messages d’instance XML. Pour connaître les données attendues dans un corps de message d’instance de fichier plat entrant, vous devez configurer le désassembleur de fichier plat avec le schéma de fichier plat correspondant au corps. Vous pouvez spécifier le schéma à l’aide de la **schéma de Document** propriété au moment du design du désassembleur de fichier plat ou **XMLNORM. DocumentSpecName** propriété de contexte de message. Les messages d’instance de fichier plat devant obligatoirement contenir une partie corps, vous devez configurer le schéma approprié à l'aide d'une de ces deux méthodes.  
  
 Pour les messages d’instance de fichier plat sortants, l’assembleur de fichier plat peut déterminer dynamiquement le schéma de fichier plat approprié pour le corps du message d'instance. L’assembleur de fichier plat détermine le schéma approprié d’après le type du message, qui correspond à une combinaison de l'espace de noms cible et du nom de l'élément racine, les deux devant figurer dans la version XML du message sortant. Vous pouvez également configurer explicitement le schéma de fichier plat à utiliser en configurant le **schéma de Document** propriété au moment du design de l’assembleur de fichier plat ou **XMLNORM. DocumentSpecName** propriété de contexte de message.  
  
 Vous pouvez copier les données contenues dans les corps de messages d'instance de fichier plat entrants dans le contexte de message correspondant en spécifiant la promotion des propriétés dans le schéma de fichier plat utilisé par le désassembleur pour traiter le message d’instance entrant. De la même façon, vous pouvez à nouveau copier les données figurant dans le contexte du message dans les messages d'instance de fichier plat sortants en spécifiant la rétrogradation des propriétés dans le schéma de fichier plat utilisé par l’assembleur de fichier plat pour traiter le message sortant.  
  
## <a name="see-also"></a>Voir aussi  
 [En-têtes de Message de fichier plat](../core/flat-file-message-headers.md)   
 [Codes de Message de fichier plat](../core/flat-file-message-trailers.md)   
 [Structure d’un Message de fichier plat](../core/structure-of-a-flat-file-message.md)   
 [Comment créer des schémas pour les Messages de fichier plat](../core/how-to-create-schemas-for-flat-file-messages.md)