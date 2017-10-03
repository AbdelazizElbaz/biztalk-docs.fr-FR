---
title: "Étape 4 : Tester la Solution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60c39521-eee2-49f7-a9f9-2dfb9ab468e9
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64f0ae6cb124ea9d8710797790b9176289faafc3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-test-the-solution"></a>Étape 4 : Tester la Solution
Dans cette rubrique, vous allez tester la solution en déposant un message de requête factice dans le dossier que vous avez associé au port de réception FILE. Comme expliqué, vous déposez un message de requête factice uniquement pour appeler le **WCF-WebHttp** port d’envoi. Vous pouvez créer un message de requête factice semblable au suivant :  
  
```  
<Root>  
  <Input>Azure Market Place REST API integration</Input>  
<Root>  
```  
  
### <a name="to-test-the-solution"></a>Pour tester la solution  
  
1.  À partir de la Console Administration de BizTalk Server, démarrez **BizTalk Application 1**. Cette action a pour effet de démarrer tous les ports que vous avez créés lors des étapes précédentes.  
  
2.  Ouvrez l’Explorateur Windows, puis accédez à l’emplacement de réception FILE. À cet emplacement, copiez le message de requête factice.  
  
3.  Lorsque le fichier disparaît, accédez à l’emplacement que vous avez associé au port d’envoi FILE, lequel consomme le message de réponse à partir de l’interface REST. Il doit contenir un message de réponse XML. Ouvrez ce dernier pour afficher les détails des vols des transporteurs aériens qui sont en retard.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel de 5 : Appeler une Interface REST à l’aide de BizTalk Server](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)