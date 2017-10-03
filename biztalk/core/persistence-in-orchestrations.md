---
title: Persistance dans les Orchestrations | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, persistence
- persistence
- BizTalk Server Orchestration Engine
ms.assetid: 2f79d294-f7df-4d84-ba76-50618506b6c6
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af73db551ced1206ac316f0ba15b8c90a7d5053f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="persistence-in-orchestrations"></a>Persistance dans les orchestrations
Le moteur d'orchestration enregistre régulièrement l'intégralité de l'état d'une instance d'orchestration à différents points de persistance pour permettre la réactivation de l’instance d’orchestration. L’état comprend tous les composants .NET qui peuvent être utilisés dans l’orchestration, en plus des messages et variables. Le moteur stocke l’état aux points de persistance suivants :  
  
-   Fin d’une étendue transactionnelle (atomique ou à long terme)  
  
-   Aux points d'arrêt de débogage  
  
-   À l’exécution d’autres orchestrations via la forme Démarrer orchestration  
  
-   À la forme Envoi (sauf dans le cas d’une transaction atomique)  
  
-   Lorsqu’une instance d'orchestration est suspendue.  
  
-   Lorsque le système s'arrête dans des conditions définies.  
  
-   Lorsque le moteur détermine qu’elle doit être mise en attente.  
  
-   Lorsqu’une instance d'orchestration est terminée.  
  
 Le moteur optimise le nombre de points de persistance car ils sont coûteux, en particulier lorsqu’il s’agit de messages volumineux. Comme il est indiqué dans les deux instances d'orchestration ci-dessous, dans l'orchestration associée aux formes Envoi au sein d’une étendue atomique, le moteur détermine un seul point de persistance entre la fin de l'étendue de transaction et la fin de l'orchestration.  Dans les autres orchestrations, il y aura deux points de persistances, un pour la première forme Envoi et un deuxième pour la forme Envoi plus la fin de l'orchestration.  
  
 **Persistance d’orchestration**  
  
 ![Persistance d’orchestration](../core/media/bts-trans-orch-fig2.gif "BTS_Trans_Orch_Fig2")  
  
 Tous les objets .NET que vous utilisez dans les orchestrations, directement ou indirectement, doivent être sérialisables, à moins qu’ils ne soient invoqués dans des étendues atomiques, ou si les objets sont sans état et invoqués uniquement via des méthodes statiques. **System.Xml.XmlDocument** est un cas spécial et ne doit pas être marqué comme sérialisable quelle que soit la propriété de transaction pour une étendue.  
  
 Fonctionnement de ce traitement spécial **System.Xml.XmlDocument** de travail :  
  
 Lorsque l’utilisateur définit une variable **X** de type **T**, où **T** est **System.Xml.XmlDocument** ou une classe dérivée de  **System.Xml.XmlDocument** puis le compilateur traite **X** comme un objet sérialisable.  
  
 Lors de la sérialisation **X**, le runtime conserve les informations suivantes : (a) le type réel **Tr** de l’objet **X** fait référence à (b) la  **OuterXml** chaîne du document.  
  
 Lors de la désérialisation **X**, l’exécution va créer une instance de **Tr** (Cela suppose un constructeur qui ne prend pas de paramètres) et appellera **LoadXml** fournissant le instance avec les **OuterXml.  X** sera alors défini pour pointer vers l’instance nouvellement créée de **Tr**.  
  
## <a name="see-also"></a>Voir aussi  
 [Transactions](../core/transactions.md)