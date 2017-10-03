---
title: "Étapes d’un cas de Test BizUnit | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed0e725f-2c52-43f7-ae30-343413a703c2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ff435fd1c69118112b0121bf68b38ae3151885f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="stages-of-a-bizunit-test-case"></a>Étapes d’un cas de Test BizUnit
Chaque cas de test BizUnit se compose de trois étapes : **TestSetup**, **TestExecution**, et **TestCleanup**. Chaque étape contient un ou plusieurs étapes de test qui sont chargés d’effectuer une seule unité discrète de travail ; par exemple, le **FileCreateStep** est responsable de la création d’un fichier dans un emplacement que vous spécifiez avec un nom de fichier donné.  BizUnit inclut des étapes de test plus de 70 et fournit également des fonctionnalités d’extension qui permettent d’être aisément ajouté pour l’infrastructure de nouvelles étapes de test. La possibilité d’ajouter de nouvelles étapes de l’infrastructure permet de BizUnit à utiliser sur un large éventail de scénarios. Cette rubrique décrit les étapes de test BizUnit plus en détail.  
  
## <a name="setup-stage"></a>Phase d’installation  
 Cette phase d’installation prépare la plate-forme pour le test. Par exemple, avant de pouvoir exécuter un test particulier, un fichier peut-être à copier sur un dépôt de fichier en vue de l’exécution réelle du test. Vous pouvez également utiliser cette étape pour effectuer un nettoyage des tables de base de données qui seront utilisés dans le test ni d’emplacements de fichiers. Comme avec chaque phase de BizUnit, il n’existe aucune limite au nombre d’étapes de test qui peut être ajouté, qui fournissent la souplesse nécessaire pour gérer les scénarios complexes.  
  
## <a name="execution-stage"></a>Étape d’exécution  
 L’étape d’exécution est où réellement l’exécution du test. Il s’agit où la fonction du système que vous validez est réellement testée.  
  
## <a name="cleanup-stage"></a>Phase de nettoyage  
 L’étape de nettoyage est le conteneur pour les étapes de test qui retourne la plateforme à l’état cohérent où il se trouvait avant d’exécuter le test. Cette étape est toujours exécutée, même si une erreur se produit dans l’étape d’exécution. La raison de que la plateforme doit être retournée à son point de départ est afin d’éviter un cas de test n’entre en conflit avec un autre afin que chaque cas de test est exécuté de manière autonome dans le cadre de la suite de tests. Assurer un nettoyage complet du système à ce stade est un des principes directeurs pour des tests efficaces avec BizUnit.  
  
 Le diagramme suivant illustre le format d’un cas de test d’exemple, qui contient les étapes de test dans les trois étapes : le programme d’installation, l’exécution et le nettoyage. Il est important de toujours faire suivre cette structure lors de la définition des cas de test BizUnit.  
  
 ![Étapes d’un Test BizUnit](../technical-guides/media/0a3e2e30-8329-4e87-ae83-f50f7b6aa0a4.gif "0a3e2e30-8329-4e87-ae83-f50f7b6aa0a4")  
Étapes d’un test BizUnit  
  
## <a name="see-also"></a>Voir aussi  
 [Pour faciliter les tests automatisés à l’aide de BizUnit](../technical-guides/using-bizunit-to-facilitate-automated-testing.md)