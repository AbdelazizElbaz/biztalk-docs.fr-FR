---
title: Composant de Pipeline assembleur BizTalk Framework | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, BizTalk Framework Assembler
- BizTalk Framework Assembler [pipeline component]
ms.assetid: 116dff8d-b7f8-4564-a7fb-6440682683dc
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 777e3d98ade5b4e0c54744cea6d37b1e43717e66
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-framework-assembler-pipeline-component"></a>Composant de Pipeline assembleur BizTalk Framework
BizTalk Framework constitue une approche permettant d’effectuer une livraison garantie unique à l'aide des protocoles de transport tels que HTTP ou SMTP. Cette infrastructure existe depuis 1998 et peut être considérée comme un précurseur des initiatives en matière de normes en cours basées sur les services Web, en particulier WSReliable. Le problème de livraison unique garantie des données relevait principalement du domaine de technologies telles que Message Queuing (connu également sous le sigle MSMQ). Toutefois, de telles technologies exigent généralement un logiciel commun aux deux points de terminaison d’un flux de données, et ne gèrent pas l'utilisation des protocoles de transport ouverts basés sur les réseaux publics, par exemple les données qui franchissent les limites de l'entreprise par le biais d'Internet.  
  
 L’infrastructure BizTalk Framework met en œuvre certains des mécanismes qui étaient déjà utilisés lors des premières tentatives de résolution du problème de garantie de livraison unique des données. D'autres solutions existent, comme l’échange de données informatisé (EDI). Dans les échanges EDI, les numéros de contrôle ANSI X12 et les notifications de transactions opérationnelles 997 standard forment la base de la garantie que les données sont reçues une seule fois, et que l’expéditeur est averti en cas de problèmes survenus à la réception.  
  
 BizTalk Framework considère que, malgré la disparité des systèmes et des données d'échange, tous comprennent les exigences suivantes du protocole BizTalk Framework :  
  
-   utiliser un format d'enveloppe prévisible pour les transmissions ;  
  
-   identifier toutes les transmissions sortantes avec un identificateur unique global ;  
  
-   toujours renvoyer à l’expéditeur un accusé de réception comprenant l'identificateur unique global, même pour les données qui ont déjà été reçues, fait l’objet d’un accusé de réception et traitées ;  
  
-   existence de moyens par lesquels l'expéditeur peut renouveler la transmission jusqu’à réception d'un accusé de réception, ou d'une certaine durée après laquelle la transmission n’est plus valide.  
  
 Le composant de pipeline Assembleur BizTalk Framework doit sérialiser l'enveloppe et le contenu BizTalk Framework dans le message avant sa transmission et renvoyer le message lorsque aucun accusé de réception n'est reçu dans les délais impartis. Il est également responsable de la réception et du traitement des accusés ainsi que de la suppression de l'instance du message. (Une copie de l’instance du message envoyé est conservée dans la base de données MessageBox jusqu’à ce que BizTalk reçoive une confirmation de réception du destinataire. Une fois la confirmation de réception reçue, l'instance du message est détruite par le moteur de messagerie.)  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer le composant de Pipeline assembleur BizTalk Framework](../core/how-to-configure-the-biztalk-framework-assembler-pipeline-component.md)   
 [Composants de pipeline](../core/pipeline-components.md)