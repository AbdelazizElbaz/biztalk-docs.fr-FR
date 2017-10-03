---
title: "Composant de Pipeline Désassembleur BizTalk Framework | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, BizTalk Framework Disassembler
- BizTalk Framework Disassembler [pipeline component]
ms.assetid: 48d6c530-5c02-4c70-ad11-0ea6c3c808f8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1ab54ddb9ef0b5fa389e6716fc4426978dcbd7a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-framework-disassembler-pipeline-component"></a>Composant de Pipeline Désassembleur BizTalk Framework
Le composant de pipeline Désassembleur BizTalk Framework analyse les données XML et détermine si elles contiennent une charge de message basée sur BizTalk Framework. Le composant de pipeline enregistre le contexte du message et en crée un nouveau avec la propriété BizTalk Framework qui doit être générée. La propriété est utilisée pour acheminer le message au gestionnaire d’entrée BizTalk Framework, lui permettant de recevoir le message à traiter.  
  
 Le composant de pipeline Désassembleur BizTalk Framework génère un accusé de réception pour le message généré si l'expéditeur en a fait la demande avec l'en-tête deliverReceiptRequest dans l’enveloppe BizTalk Framework. Cette opération est contrôlée par la propriété de génération d’accusé de réception dans le composant de pipeline Assembleur BizTalk Framework. Pour plus d’informations sur BizTalk Framework, consultez [composant de Pipeline assembleur BizTalk Framework](../core/biztalk-framework-assembler-pipeline-component.md).  
  
 Pour plus d’informations sur la configuration du composant de pipeline Désassembleur BizTalk Framework et la création de l’orchestration, consultez [comment configurer le composant de Pipeline Désassembleur BizTalk Framework](../core/how-to-configure-the-biztalk-framework-disassembler-pipeline-component.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer le composant de Pipeline Désassembleur BizTalk Framework](../core/how-to-configure-the-biztalk-framework-disassembler-pipeline-component.md)   
 [Composants de pipeline](../core/pipeline-components.md)