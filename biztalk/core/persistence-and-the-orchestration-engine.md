---
title: "Persistance et le moteur d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestration engine, persistence
- persistence
- orchestration engine, serialization
ms.assetid: 088230ef-13b3-440b-9875-6449f29dd5c6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e9e1c8b158d313681a6e1374a586ca957b1aa15
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="persistence-and-the-orchestration-engine"></a>Persistance et moteur d'orchestration
La persistance d'état, sa gestion et sa restauration, sont au cœur de nombreuses fonctionnalités fondamentales du moteur d'orchestration. La persistance est particulièrement essentielle au fonctionnement correct de :  
  
-   La mise en attente et la réactivation  
  
-   L'exécution et la réactivation indépendantes de l'ordinateur  
  
-   Le modèle de compensation  
  
-   L'arrêt contrôlé du système  
  
-   Récupération  
  
 Le moteur d'orchestration enregistre dans un stockage permanent l'état global d'une instance d'orchestration en cours d'exécution à différents stades, de manière à pouvoir ultérieurement restaurer intégralement l'instance. L'état inclut :  
  
-   l'état interne du moteur, y compris sa progression actuelle ;  
  
-   l'état de tous les composants .NET qui contiennent des informations concernant l’état et qui sont utilisés par l'orchestration ;  
  
-   les valeurs des messages et des variables.  
  
## <a name="persistence-points"></a>Points de persistance  
 Le moteur d'orchestration enregistre l'état d'une instance d'orchestration en cours d'exécution en différents points. S'il doit réalimenter l'instance d'orchestration, redémarrer après un arrêt contrôlé ou récupérer après un arrêt inattendu, il exécutera l'instance d'orchestration à partir du dernier point de persistance, comme si rien ne s’était produit. Par exemple, si un message est reçu mais qu’un arrêt inattendu se produise avant que l'état puisse être enregistré, le moteur n'enregistre pas la réception du message et le reçoit de nouveau au redémarrage. Le moteur enregistre l'état d'une orchestration dans les circonstances suivantes :  
  
-   La fin d'une étendue transactionnelle est atteinte.  
  
    -   Le moteur enregistre l'état à la fin d'une étendue transactionnelle afin de définir sans ambiguïté le point à partir duquel reprendre l'orchestration et afin que la compensation puisse être effectuée correctement si nécessaire.  
  
    -   L'orchestration continuera à être exécutée à partir de la fin de l'étendue si la persistance a réussi ; autrement, le gestionnaire d'exceptions approprié sera appelé.  
  
    -   Si l'étendue est transactionnelle et atomique, le moteur enregistre l'état à l'extrémité de l'étendue atomique lorsqu'il est validé.  
  
    -   Si l'étendue est transactionnelle et à long terme, le moteur génère une nouvelle transaction et conserve l'état complet de l’exécution lorsque l'étendue est complète.  
  
-   Un point d'arrêt de débogage est atteint.  
  
-   Un message est envoyé. La seule exception à cet état de fait se produit lorsqu' un message est envoyé depuis une étendue de transaction atomique.  
  
-   L’orchestration démarre une autre orchestration de manière asynchrone, comme avec la **démarrer Orchestration** forme.  
  
-   L'instance d'orchestration est suspendue.  
  
-   Lorsque le moteur d'orchestration est invité à s'arrêter, il tente d'enregistrer les informations de contrôle ainsi que l'état actuel de toutes les instances d'orchestration en cours d'exécution afin de pouvoir reprendre leur exécution lors de son redémarrage. Si le moteur ne parvient pas à enregistrer l'état actuel, il reprendra à la prochaine exécution l'instance d'orchestration à partir du dernier point de persistance qui s'est produit avant l'arrêt. Cela s'applique à l'arrêt contrôlé du système ainsi qu'à l'arrêt anormal.  
  
-   Le moteur détermine que l'instance doit être mise en attente.  
  
-   L'instance d'orchestration est terminée.  
  
## <a name="serialization"></a>Sérialisation  
 Toutes les instances d'objets auxquelles votre orchestration fait directement ou indirectement référence (par le biais d’autres objets) doivent être sérialisables pour que l'état de votre orchestration soit conservé. Il existe deux exceptions à cela :  
  
-   Un objet non sérialisable peut être déclaré dans une transaction atomique. Cette situation est rendue possible, car les étendues atomiques ne contiennent pas de points de persistance.  
  
-   System.Xml.XmlDocument n'est pas une classe sérialisable ; il correspond à un cas particulier et peut être utilisé à n’importe quel endroit.  
  
> [!CAUTION]
>  Pour qu’un objet .NET soit conservé, il doit être marqué comme sérialisable.  
  
> [!NOTE]
>  Les objets COM ne peuvent pas être conservés à l’aide des procédures de sérialisation .NET standard. Si vous voulez appeler un objet COM en dehors d'une transaction atomique, vous devez englober l'objet COM dans un objet .NET sérialisable et pouvant conserver et restaurer l’état de l’objet COM.  
  
## <a name="system-shutdown"></a>Arrêt du système  
 Lorsque le moteur d'orchestration est invité à s'arrêter, il tente d'enregistrer les informations de contrôle ainsi que l'état actuel de toutes les instances d'orchestration en cours d'exécution afin de pouvoir reprendre leur exécution lors de son redémarrage. Si le moteur ne parvient pas à enregistrer l'état actuel, il reprendra à la prochaine exécution l'instance d'orchestration à partir du dernier point de persistance qui s'est produit avant l'arrêt. Cela s'applique à l'arrêt contrôlé du système ainsi qu'à l'arrêt anormal.  
  
## <a name="recovery"></a>Récupération  
 Le moteur enregistre régulièrement les informations d'état d'une instance d'orchestration dans un stockage permanent et enregistre également l'état en cas d'arrêt du système.  
  
 Lorsqu'une instance d'orchestration échoue anormalement pour une raison ou une autre, elle peut être récupérée à partir du dernier état persistant et peut continuer à s'exécuter comme si aucune interruption n'avait eu lieu. Cela sera le cas même si le serveur d'origine sur lequel s'est exécutée l'instance tombe en panne pour une raison quelconque ; l'instance peut simplement reprendre son exécution sur un autre ordinateur. En raison de ce modèle de récupération multi-serveur, vous n'avez plus besoin d'effectuer de mises en cluster.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en attente de l’orchestration et la réactivation](../core/orchestration-dehydration-and-rehydration.md)