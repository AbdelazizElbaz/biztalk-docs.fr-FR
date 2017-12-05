---
title: "Planification du test de base de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4cf5e1f-a960-4702-a050-a2cdacddcbca
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3849b68af9fdd4e457a8e1e492134a87dc1655bd
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="planning-for-database-testing"></a>Planification du test de base de données
Test de stress/charge complète d’une solution BizTalk les chiffres en premier plan de la réussite ou l’échec de la solution. Étant donné que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performances dépend donc les performances de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, test et l’optimisation d’une solution se concentre fréquemment sur le test de BizTalk et d’optimisation des ordinateurs exécutant [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] qui hébergent le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]bases de données.  
  
## <a name="considerations-when-planning-for-database-testing"></a>Considérations relatives à la planification du test de base de données  
 Considérez les éléments suivants lors de la planification pour le test de la base de données :  
  
1.  **Assurez-vous que l’environnement de test correspond à l’environnement de production aussi fidèlement que possible.** À l’aide d’un environnement virtuel, tels que Microsoft Hyper-V Server 2008 pour les tests unitaires est parfaitement acceptable ; Toutefois, tous les tests de charge/contrainte doivent être effectuée sur le matériel qui correspond à l’environnement de production finale autant que possible.  
  
2.  **Planifier mesurer le débit maximal et le débit de suivi maximal acceptable du système BizTalk Server**. Débit maximal acceptable est mesuré comme la plus grande charge de trafic de message que le système BizTalk Server capable de gérer indéfiniment en production. Suivez les étapes décrites dans les rubriques suivantes dans l’aide de BizTalk Server :  
  
    -   [Mesurer le débit de moteur maximal acceptable](http://go.microsoft.com/fwlink/?LinkID=154388) (http://go.microsoft.com/fwlink/?LinkID=154388).  
  
    -   [Mesurer le débit de suivi maximal acceptable](http://go.microsoft.com/fwlink/?LinkID=153815) (http://go.microsoft.com/fwlink/?LinkID=153815).  
  
     Ces rubriques décrivent la méthodologie utilisée pour la génération de la charge sur le système, les paramètres qui doivent être évalués et les recommandations générales à suivre lorsque vous testez le débit maximal acceptable.  
  
3.  **Comprendre les implications de la façon de BizTalk Server**  
     **implémente la limitation de l’hôte.** Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] algorithme de limitation de l’hôte tente de modéré de la charge de travail de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hébergent des instances de s’assurer que la charge de travail ne dépasse pas la capacité de l’instance d’hôte ou les instances d’hôte en aval. Le mécanisme de limitation est autoréglable et les options de configuration par défaut sont adaptées à la majorité des [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des scénarios de traitement. Toutefois, vous aurez une bonne compréhension du mécanisme de limitation avant d’implémenter le test de charge/contrainte. Pour plus d’informations, consultez [optimisation des ressources d’utilisation via la limitation des hôtes](http://go.microsoft.com/fwlink/?LinkId=155770) (http://go.microsoft.com/fwlink/?LinkId=155770) dans l’aide de BizTalk Server.