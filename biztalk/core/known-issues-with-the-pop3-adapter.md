---
title: "Problèmes connus avec l’adaptateur POP3 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6d621a2-4801-44fe-a266-d4c05ac82633
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bc86b2ae14b04b160f7387f870615116e659b3f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-the-pop3-adapter"></a>Problèmes connus avec l'adaptateur POP3
Cette section contient des informations qui peuvent vous permettre d'éviter certaines erreurs.  
  
## <a name="known-issues"></a>Problèmes connus  
  
#### <a name="the-pop3-adapter-fails-to-process-documents-when-running-on-a-64-bit-operating-system"></a>L'adaptateur POP3 ne parvient pas à traiter des documents lorsqu'il s'exécute sur un système d'exploitation 64 bits  
  
##### <a name="problem"></a>Problème  
 L'adaptateur POP3 ne traitera pas de document s'il s'exécute sur un système d'exploitation 64 bits.  
  
##### <a name="cause"></a>Cause  
 Le gestionnaire de l'adaptateur POP3 n'est pas en mesure d'exécuter une instance d'hôte 64 bits.  
  
##### <a name="resolution"></a>Résolution  
 Si vous exécutez l'adaptateur POP3 sur une machine 64 bits, configurez les gestionnaires correspondants pour qu'ils s'exécutent sur un hôte 32 bits. Cette option se trouve dans la page Propriétés d'hôte accessible à partir de la console Administration de BizTalk.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage de l’adaptateur POP3](../core/troubleshooting-the-pop3-adapter.md)