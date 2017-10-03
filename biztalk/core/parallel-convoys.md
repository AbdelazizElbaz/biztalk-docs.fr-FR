---
title: "Parallèle convois | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Parallel Task shape [Orchestration Designer], concurrent receive tasks
- messages, convoys
- correlation sets, concurrent receive tasks
- correlation sets, Parallel Task shape [Orchestration Designer]
- orchestrations, messages
- messages, correlating to orchestrations
ms.assetid: 036aa8c0-f49c-47f0-ac1e-6c667bca3811
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9c6993aa3c5dd47cb5b554dd8ab2080020ebb80
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="parallel-convoys"></a>Convois parallèles
Un convoi parallèle permet à plusieurs messages distincts d'être assemblés afin d'obtenir le résultat souhaité. L'ensemble des messages connexes peut arriver dans n'importe quel ordre, mais le serveur BizTalk doit tous les recevoir avant de commencer le traitement.  
  
 Par exemple, lorsqu'un hôpital admet un nouveau patient, ce dernier doit fournir diverses informations, notamment concernant sa couverture sociale et ses antécédents médicaux, ainsi que les coordonnées d'une personne à prévenir. Plusieurs personnes différentes collectent ces informations : secrétaire, infirmière, etc. Plusieurs systèmes différents traitent ces informations. L'ordre de collecte et d'envoi de ces informations n'est pas sûr. Par exemple, les personnes qui collectent ces informations peuvent être occupées avec d'autres patients, le service d'enregistrement médical n'est pas une priorité dans leur planification ou le système de liaison à la sécurité sociale ne fonctionne pas correctement. Assembler les informations sur le patient de manière organisée est essentiel tout au long du séjour de celui-ci. Cela permettra au patient de recevoir les soins adéquats et de payer uniquement ce qui est dû.  
  
 Ceci est un exemple de scénario d'entreprise qui requiert un traitement parallèle des messages en convoi. Les obligations commerciales dictent la réception de trois différents types de messages avant que le patient ne soit admis à l'hôpital. Ces trois messages sont les messages de couverture sociale, d'antécédents médicaux et de personne à contacter. N'importe lequel de ces trois messages peut arriver le premier et ceci crée une condition d'engorgement. Pour résoudre ce problème, trois **réception** formes sont placés dans un **Actions parallèles** forme et chaque réception est marquée par activer = True. N'importe lequel des messages peut ainsi démarrer l'orchestration. L'instance d'orchestration attend que les deux autres messages arrivent avant d'effectuer le traitement.  
  
## <a name="implementing-parallel-convoys"></a>Implémentation de convois parallèles  
 Vous avez la possibilité d'implémenter des convois parallèles à l'aide du modèle de conception de message « réceptions parallèles corrélées » dans BizTalk Server. Parallèles corrélées reçoit corrélation entre les instructions de la réception de deux ou plusieurs branches d’un **Actions parallèles** forme. Si une corrélation est démarrée dans plusieurs tâches parallèles, chaque réception corrélée doit initialiser exactement le même ensemble de corrélations. La première tâche qui reçoit un message corrélé effectue l’initialisation réelle et la validation est effectuée sur les autres tâches dans le **Actions parallèles** forme dans une orchestration.  
  
 Pour obtenir un exemple d’implémentation de convoi parallèle, consultez l’exemple du Kit de développement logiciel « Convoi parallèle » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des convois](../core/working-with-convoy-scenarios.md)   
 [Convois séquentiels](../core/sequential-convoys.md)