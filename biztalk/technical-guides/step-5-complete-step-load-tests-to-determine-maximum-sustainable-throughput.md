---
title: "Étape 5 : Effectuer des Tests de modèle de charge étape pour déterminer le débit maximal acceptable | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8056ced6-1f04-4be2-878a-48a427a93dad
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f9794634b5a782ef6d9bce4e819e759fd47ba1a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-perform-step-load-pattern-tests-to-determine-maximum-sustainable-throughput"></a>Étape 5 : Effectuer des Tests de modèle de charge étape pour déterminer le débit maximal acceptable
La méthode la plus simple pour déterminer le nombre maximal durable débit acceptable d’une solution BizTalk Server avec le test de charge Visual Studio consiste à effectuer un modèle de charge d’étape et comparer le nombre total de Documents reçu par seconde au Document total traité par seconde . Tant que le total nombre moyen de documents traité par seconde est supérieur ou égal au total nombre moyen de documents reçu par seconde pour la durée du test, la charge est considéré comme acceptable. Si la moyenne, nombre total de documents reçu par seconde est supérieure au nombre total de documents moyenne traité par seconde pendant la durée du test, puis la charge n’est pas considéré comme acceptable, et cela sera être démontrée par une croissance correspondante dans la valeur de la Compteur de taille de Counters\Spool : général de la MessageBox. Au fil du temps, quand une application BizTalk Server reçoit les documents plus qu’il ne peut traiter, les documents non traités seront accumulent dans la base de données MessageBox, qui sera finalement induire une condition de limitation et nuire considérablement aux performances de la Application de BizTalk Server.  
  
## <a name="configure-the-load-test-with-a-step-load-pattern-appropriate-for-your-application"></a>Configurer le Test de charge avec un modèle de charge étape approprié pour votre Application  
 Suivez les étapes décrites dans la rubrique [étape 3 : créer un Test de charge pour exécuter plusieurs Tests unitaires simultanément](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md) pour créer un test de charge qui utilise un modèle de charge d’étape. Facteurs qui influent sur la capacité de l’Application BizTalk Server pour traiter des documents en temps voulu sont les suivantes :  
  
-   **Nombre d’ordinateurs BizTalk Server dans votre groupe** -serveurs BizTalk supplémentaires permettent de traitement supplémentaire.  
  
-   **Taille des messages en cours de traitement** -messages plus volumineux nécessitent des ressources de traitement supplémentaire.  
  
-   **Quantité de mappage de document effectuée** -mappage nécessite des ressources de traitement supplémentaire.  
  
-   **Réception ou envoi pipelines requis par l’application**. -Pipelines complexes nécessitent un traitement supplémentaire de ressources.  
  
-   **Adaptateurs et/ou des accélérateurs utilisés par l’application BizTalk Server** – certains adaptateurs et/ou les accélérateurs nécessitent plus de ressources de traitement que d’autres.  
  
-   **Quantité de suivi des messages requis** : le suivi des messages sont gourmande en ressources.  
  
-   **Nombre d’et la complexité des Orchestrations en cours d’exécution dans l’Application BizTalk Server** – les Orchestrations peuvent être consomme beaucoup de ressources.  
  
 Lorsque vous configurez le Test de modèle de charge étape, modifiez les valeurs spécifiées pour **démarrer le nombre d’utilisateurs** et **nombre maximal d’utilisateurs** pour vous assurer que le nombre de messages spécifié pour le début du nombre d’utilisateurs peut être facilement géré par le serveur BizTalk application au fil du temps et de même, le nombre de messages spécifiés pour le nombre maximal d’utilisateurs est plus que l’application BizTalk Server peut gérer au fil du temps. Consultez [ajouter un Test de charge et configurer le scénario de Test de charge, les ensembles de compteurs et les paramètres d’exécution](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md#BKMK_StepLoadTest) pour plus d’informations sur la modification des paramètres de modèle de charge pour le test de charge.  
  
## <a name="ensure-that-the-correct-test-settings-are-used-for-the-step-pattern-load-test"></a>Assurez-vous que les paramètres de Test appropriés sont utilisés pour le Test de charge de modèle d’étape  
 Configurer le Test de charge à utiliser le **des paramètres de Test** que vous avez créé dans [ajouter le fichier de paramètres d’un Test à la Solution pour exécuter des Tests et collecter des données à distance](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md#BKMK_TestSettings).  
  
## <a name="configure-the-load-test-with-the-appropriate-performance-counters-and-run-the-step-pattern-load-test"></a>Configurer le Test de charge avec les compteurs de Performance appropriée et exécuter le Test de charge de modèle d’étape  
 Suivez les étapes de [ajouter un ensemble de compteurs personnalisés à mesure de BizTalk Server Performance indicateurs clés (KPI)](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md#BKMK_BTSCounters) pour ajouter les compteurs de performances de BizTalk Server nécessaires qui peuvent être utilisés pour mesurer les performances de BizTalk Server Application et déterminer à quel moment l’Application BizTalk Server n’est plus en mesure de gérer la charge des messages créée par les Agents de Test de charge. Cela sera être démontrée par l’accumulation d’un retard des messages dans la table Spool comme indiqué par une valeur accrue pour le compteur taille de Counters\Spool : général de la MessageBox. Si la valeur de ce compteur commence à augmenter de manière significative vous avez probablement dépassé le débit maximal acceptable de votre Application BizTalk Server. Une fois, vous avez déterminé le nombre de messages à laquelle l’Application BizTalk Server n’est plus en mesure de traiter une grand nombre de messages qu’il reçoit, prenez note des Documents reçus par seconde lorsque cela se produit. Il est important de prenez note de cette valeur, car la rubrique [étape 6 : effectuer constante modèle des Tests de charge pour le débit maximal acceptable vérifier](../technical-guides/step-6-complete-load-pattern-tests-to-verify-maximum-sustainable-throughput.md) décrit comment exécuter un test de charge de modèle de constante avec une valeur de « Nombre Constant d’utilisateur » qui est quelque peu inférieure à la valeur maximale reçus/s de Documents durable. Pour cela, pour vérifier que l’Application BizTalk Server est capable de traiter ce nombre de messages au fil du temps. Pour afficher les valeurs pour les ensembles de compteurs, tout d’abord démarrer le test de charge en cliquant sur le nom du test (par exemple, BTS_Messaging_Step), puis le **exécuter le Test** option de menu. Une fois les compteurs de Performance sont initialisés et le test de charge commence, Visual Studio ne basculent pas automatiquement le focus de la fenêtre de graphiques qui vous permet d’afficher simultanément à partir de 1 à 4 graphiques. Si vous vous intéressez principalement pour afficher uniquement les indicateurs de performance clés, tel que défini dans [ajouter un ensemble de compteurs personnalisés à mesure de BizTalk Server Performance indicateurs clés (KPI)](../technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md#BKMK_BTSCounters), cliquez sur le **panneaux** liste déroulante de liste à partir du menu de test de charge et sélectionnez l’option pour **un panneau**. Puis cliquez sur la liste déroulante en haut du graphique et sélectionnez **indicateurs clés** pour afficher les valeurs pour les indicateurs de Performance clés en temps réel.  
  
> [!NOTE]  
>  Étant donné que certaines valeurs de compteur par défaut seront affichera dans le **indicateurs clés** graphique et vous souhaiterez probablement afficher les valeurs de compteur que vous avez ajouté à votre ensemble de compteurs personnalisé, il est souhaitable démarrer en supprimant manuellement chaque des compteurs affichés dans le **indicateurs clés** graphique et l’ajouter manuellement des compteurs à partir de vos jeux de compteurs personnalisés. Par exemple, au moins, vous pouvez ajouter au moins les compteurs dans le tableau ci-dessous à votre graphique pour déterminer comment l’environnement BizTalk Server gère la charge, et où les goulots d’étranglement peuvent se produire :  
  
|Catégorie de compteur|Compteur|Instance|Ordinateur|  
|----------------------|-------------|--------------|--------------|  
|BizTalk:MessageBox:compteurs généraux|Taille mise en file d'attente|*Base de données MessageBox de BizTalk Server*:*Instance SQL Server qui héberge la base de données MessageBox de BizTalk Server*|N’importe quel serveur BizTalk dans le groupe avec la Console Administration de BizTalk Server est installé.|  
|BizTalk:messagerie|Documents reçus/s|RxHost (ou le nom de l’hôte de réception)|*Ordinateur BizTalk Server #1 dans le groupe BizTalk Server*|  
|BizTalk:messagerie|Documents reçus/s|RxHost (ou le nom de l’hôte de réception)|*Ordinateur BizTalk Server #2 dans le groupe BizTalk Server*|  
|BizTalk:messagerie|Documents reçus/s|RxHost (ou le nom de l’hôte de réception)|*Ordinateur BizTalk Server #n dans le groupe BizTalk Server*|  
|BizTalk:messagerie|Documents traités par seconde|TxHost (ou nom de l’hôte d’envoi)|*Ordinateur BizTalk Server #1 dans le groupe BizTalk Server*|  
|BizTalk:messagerie|Documents traités par seconde|TxHost (ou nom de l’hôte d’envoi)|*Ordinateur BizTalk Server #2 dans le groupe BizTalk Server*|  
|BizTalk:messagerie|Documents traités par seconde|TxHost (ou nom de l’hôte d’envoi)|*Ordinateur BizTalk Server #n dans le groupe BizTalk Server*|  
|Processeur|% temps processeur|_Total|*Ordinateur BizTalk Server #1 dans le groupe BizTalk Server*|  
|Processeur|% temps processeur|_Total|*Ordinateur BizTalk Server #2 dans le groupe BizTalk Server*|  
|Processeur|% temps processeur|_Total|*Ordinateur BizTalk Server #n dans le groupe BizTalk Server*|  
|Processeur|% temps processeur|_Total|*Instance de SQL Server qui héberge les bases de données BizTalk Server*|