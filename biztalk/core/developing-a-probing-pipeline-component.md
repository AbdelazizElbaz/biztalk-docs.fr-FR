---
title: "Composant de Pipeline du développement d’une détection | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], probing
- IProbeMessage interface
- pipeline interfaces, IProbeMessage
ms.assetid: c3da467d-5270-4c7f-9c38-ce9989bf1b63
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8081c31fc781cd2d1cbc291587f358376a033d66
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-a-probing-pipeline-component"></a>Développement d’un composant de Pipeline de sonde
Tout composant de pipeline (général, assemblage ou désassemblage) peut implémenter la `IProbeMessage` interface si elle doit prendre en charge les fonctionnalités de sondage des messages. Un composant de sonde est utilisé dans les étapes du pipeline qui ont **PremièreCorrespondance** mode d’exécution. Dans ces étapes, le moteur de messagerie BizTalk transmet le début du message au composant afin de déterminer si ce dernier reconnaît le format du message. Si c'est le cas, la totalité du message est remise au composant pour traitement.  
  
 Le **IProbeMessage** interface expose une méthode unique, **sonde**, ce qui permet au composant vérifier le début du message. La valeur de retour détermine si ce composant est exécuté. Les étapes suivantes donnent un aperçu de la manière dont le moteur de messagerie BizTalk exécute une étape dans laquelle la reconnaissance est requise :  
  
1.  Si l'étape ne contient pas de composants, elle n'est pas exécutée et le message est remis aux étapes suivantes pour traitement.  
  
2.  Vérifiez si le composant implémente le **IProbeMessage** interface. Si ce n'est pas le cas, le moteur de messagerie appelle le composant. Le traitement de l'étape est effectué et le message est transmis à la prochaine étape.  
  
3.  Le **sonde** méthode est appelée. Si la valeur de retour est **True**, le composant est exécuté. Ensuite, le traitement de l'étape est effectué et le message est transmis à une prochaine étape.  
  
4.  Le moteur de messagerie obtient le prochain composant dans l'étape. S'il n'y a plus de composants et qu'aucun des composants n'a été exécuté, il génère une erreur indiquant que le traitement du pipeline a échoué. S'il n'y a plus de composants et qu'au moins un des composants a été exécuté, le traitement est effectué.  
  
 Si une étape ne requiert pas de reconnaissance (par exemple, le mode d’exécution est **tous les**), le moteur de messagerie appelle le composant sans interroger d’abord pour la **IProbeMessage** interface et en appelant le **Sonde** (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un composant de Pipeline général](../core/developing-a-general-pipeline-component.md)   
 [Développement d’un composant de Pipeline d’assemblage](../core/developing-an-assembling-pipeline-component.md)   
 [Développement d’un composant de Pipeline de désassemblage](../core/developing-a-disassembling-pipeline-component.md)   
 [Rapports d’erreurs à partir des composants de Pipeline](../core/reporting-errors-from-pipeline-components.md)   
 [Configuration des composants de Pipeline natifs](../core/configuring-native-pipeline-components.md)   
 [Déploiement des composants de Pipeline](../core/deploying-pipeline-components.md)