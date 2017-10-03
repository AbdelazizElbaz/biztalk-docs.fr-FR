---
title: "Étape 3 : Créer un Test de charge pour exécuter plusieurs Tests unitaires simultanément | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5dd7e31-7188-4edf-9513-ea2725950b47
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8c9a99c0efaacac233c339d9279c837744892fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously"></a>Étape 3 : Créer un Test de charge pour exécuter plusieurs Tests unitaires simultanément
Tests de charge exécutent plusieurs instances de l’un ou des tests unitaires plus afin que vous pouvez mesurer les performances et la capacité de gérer la charge de votre application. Les composants principaux d’un test de charge Visual Studio 2010 sont les suivantes :  
  
-   **Scénarios** – la section d’un test de charge, dans laquelle vous permet de configurer le modèle de test de charge, modèle de combinaison de tests, la combinaison de tests, la combinaison de réseaux et de la combinaison de navigateurs Web. Scénarios de prendre en compte la complexité de la simulation de profils de charge de travail complexe monde réel. Pour une liste complète de tous les charger les propriétés du scénario de test, consultez [propriétés de scénario de Test de charge](http://go.microsoft.com/fwlink/?LinkId=208327) (http://go.microsoft.com/fwlink/?LinkId=208327).  
  
-   **Ensembles de compteurs** – la section où vous créez des regroupements particuliers ou « Ensembles » des compteurs de performance à collecter pendant le test de charge est en cours d’exécution d’un test de charge. Plusieurs ensembles de compteurs prédéfinis sont fournis par défaut et ensembles de compteurs personnalisés peuvent être ajoutés. Par exemple, pour évaluer le réseau performances, vous pouvez créer un compteur personnalisé défini, ajouter les compteurs de performance réseau pertinentes et enregistrer dans la liste des ensembles de compteurs disponibles. Pour plus d’informations sur la création et l’enregistrement des ensembles de compteurs pour les tests de charge, consultez [spécifiant les ensembles de compteurs pour les ordinateurs dans un Test de charge](http://go.microsoft.com/fwlink/?LinkId=208328) (http://go.microsoft.com/fwlink/?LinkId=208328).  
  
-   **Paramètres d’exécution** : définissent des paramètres d’exécution différents aspects d’un test de charge, y compris la durée du test, les ensembles de compteurs qui sont associées à différents ordinateurs pendant le test de charge, différentes options de validation de test et les options de stockage des résultats des tests. Vous pouvez créer et stocker plusieurs paramètres d’exécution pour chaque test de charge, puis sélectionnez un paramètre particulier à utiliser lorsque vous exécutez le test. Un paramètre d’exécution initial est ajouté à votre test de charge lorsque vous créez votre test de charge avec l’Assistant Nouveau Test de charge. Pour une liste complète de tous les tests de charge les propriétés de paramètre d’exécution, consultez [propriétés Test de charge exécuté paramètre](http://go.microsoft.com/fwlink/?LinkId=208329) (http://go.microsoft.com/fwlink/?LinkId=208329).  
  
 Tests de charge sont créés à l’aide du nouvel Assistant Test de charge, de le modifier avec l’éditeur de Test de charge et analysés dans l’Analyseur de Test de charge. Tous ces outils sont inclus dans les éditions de Microsoft Visual Studio Ultimate. Pour plus d’informations sur la création et modification de tests de charge dans Visual Studio 2010 Ultimate Édition, consultez [création et modification des Tests de charge](http://go.microsoft.com/fwlink/?LinkId=208308) (http://go.microsoft.com/fwlink/?LinkId=208308).  
  
 Suivez les étapes décrites dans les sections ci-dessous pour ajouter une charge de test au projet de test décrit dans [étape 1 : créer un Test unitaire pour envoyer des Documents à BizTalk Server](../technical-guides/step-1-create-a-unit-test-to-submit-documents-to-biztalk-server.md). Ces étapes décrivent également comment configurer le **scénarios**, **les ensembles de compteurs**, et **paramètres d’exécution** pour un test de charge.  
  
##  <a name="BKMK_StepLoadTest"></a>Ajouter un Test de charge et configurer le scénario de Test de charge, ensembles de compteurs et paramètres d’exécution  
 Cette rubrique explique comment utiliser le **Assistant Nouveau Test de charge** pour ajouter une charge de test à un projet de test et la configuration de la charge de test pour répondre aux besoins spécifiques.  
  
### <a name="use-the-new-load-test-wizard-to-add-a-load-test-to-the-test-project"></a>Utilisez l’Assistant Nouveau Test de charge pour ajouter un Test de charge au projet de Test  
 Suivez ces étapes pour ajouter un test de charge à un projet de test à l’aide de l’Assistant Nouveau Test de charge.  
  
1.  Ouvrez le **Test de charge** solution dans Visual Studio 2010, s’il n’est pas déjà ouvert.  
  
2.  Ajouter un dossier dans le projet BTSLoad ; ce dossier contiendra les tests de charge qui sont créés dans le cadre de ce projet. Dans l’Explorateur de solutions, cliquez sur le projet BTSLoad, pointez sur **ajouter**, puis cliquez sur **nouveau dossier**. Une icône de dossier avec le texte mis en surbrillance **Nouveaudossier1** s’affiche sous le projet BTSLoad, type **LoadTests** pour modifier le texte en surbrillance et appuyez sur ENTRÉE pour terminer la création du dossier C:\ Projects\LoadTest\BTSLoad\LoadTests.  
  
3.  Dans l’Explorateur de solutions, cliquez sur le **BTSLoad** de projet, pointez sur **ajouter**, puis cliquez sur **Test de charge** pour démarrer le **nouvel Assistant de Test de charge**.  
  
4.  Cliquez sur **Suivant**.  
  
5.  Sur le **modifier les paramètres pour un scénario de Test de charge** page sous **Entrez un nom pour le scénario de test de charge :** type **BTS_Messaging_Step**. Sous **profil de temps de réflexion** sélectionnez **n’utilisent pas les temps de réflexion** puis cliquez sur **suivant**.  
  
6.  Sur le **scénario de test de modifier les paramètres de modèle de charge pour une charge** page Sélectionnez **charge par étape**, entrez les valeurs ci-dessous, puis sur **suivant**.  
  
    -   **Nombre d’utilisateurs de démarrer :** 30 utilisateurs  
  
    -   **Durée de l’étape :** 60 secondes  
  
    -   **Nombre d’utilisateurs dans l’étape :** 10 utilisateurs  
  
    -   **Nombre maximal d’utilisateurs** aux 80 utilisateurs  
  
    > [!NOTE]  
    >  Lors de l’application des paramètres pour un modèle de charge par étape, vous devez calculer la quantité de temps nécessaire pour tous les incréments terminer. Par exemple, en utilisant les paramètres de modèle de charge spécifiés ci-dessus le test de charge doivent 5 minutes pour effectuer toutes les 60 secondes pas incréments lorsqu’en identifiant de 30 à 80 utilisateurs. Dans la dernière page de l’Assistant Test de charge s’affiche avec les options de spécification de la longueur du test de charge, qui sera de **durée de Test de charge**. Si vous avez déjà calculé le temps nécessaire pour tous les incréments pour terminer, il s’agit d’une tâche simple à taper la valeur (5 minutes dans le cas présent) pas à pas pour **durée du Test de charge**.  
  
7.  Sur le **sélectionner un modèle de combinaison de tests pour le test de charge** page Sélectionnez **en fonction du nombre d’utilisateurs virtuels** puis cliquez sur **suivant**.  
  
8.  Sur le **ajouter des tests pour le scénario de test de charge et modifier la combinaison de tests** page, cliquez sur le **ajouter** bouton.  
  
9. Sous **tests disponibles** double-cliquez sur **BTSMessaging** et **BTSMessaging2** pour ajouter ces tests unitaires à la liste des **des tests sélectionnés**. Cliquez sur **OK** puis cliquez sur **suivant**.  
  
10. Sur le **ajouter des types de réseaux à un scénario de test de charge et modifier la combinaison de réseaux** vérification de page **Type de réseau** a la valeur **LAN** avec un **Distribution** de **100 %** puis cliquez sur **suivant**.  
  
11. Sur le **permet de spécifier les ordinateurs à surveiller avec des ensembles de compteurs durant la série de tests de charge** page, cliquez sur **suivant**.  
  
    > [!NOTE]  
    >  N’ajoutez pas d’ordinateurs pour le test de charge pour l’instant. L’Assistant Nouveau Test de charge vous permet uniquement d’associer des ordinateurs avec des ensembles de compteurs prédéfinis, et ce test de charge requiert l’utilisation des deux prédéfinies et *personnalisé* ensembles de compteurs. Une fois que l’Assistant est terminé et le test de charge est enregistré, vous pouvez modifier le test de charge pour ajouter des ensembles de compteurs personnalisés et de configurer le test de charge pour surveiller des ordinateurs à l’aide de deux prédéfinies *et* ensembles de compteurs personnalisés.  
  
     Sur le **réviser et modifier des paramètres pour un test de charge d’exécution** page Entrez les valeurs suivantes :  
  
    1.  Sélectionnez **durée du test de charge**.  
  
    2.  **Durée de préchauffage (hh mm ss)** 30 secondes  
  
    3.  **Exécuter la durée (hh mm ss)** 5 minutes  
  
        > [!NOTE]  
        >  Le temps alloué pour **durée d’exécution** doit être égal à la quantité de temps nécessaire pour tous les incréments pour terminer comme décrit à l’étape 5 ci-dessus, ou 5 minutes pour cet exemple pas à pas.  
  
    4.  **Taux d’échantillonnage** 5 secondes  
  
    5.  **Description** (facultatif), entrez une description pour le test de charge ici.  
  
    6.  **Enregistrer le journal en cas d’échec du Test** True  
  
    7.  **Niveau de validation** faible – invoquer les règles de validation marquées comme basses  
  
12. Cliquez sur **Terminer** pour fermer l’Assistant Nouveau Test de charge.  
  
13. Cliquez sur le **fichier** menu et sélectionnez **enregistrer \<nom du Test de charge > .loadtest comme**.  
  
    > [!NOTE]  
    >  Dans cet exemple, <Load Test Name> sera le nom attribué au fichier de test de charge par Visual Studio 2010, généralement loadtestx.loadtest, sauf si le nom du fichier a déjà été modifié manuellement.  
  
14. Enregistrez le fichier dans le répertoire C:\Projects\LoadTest\BTSLoad\LoadTests créé précédemment. Il peut être utile enregistrer le fichier avec le nom utilisé pour le scénario ; Dans cet exemple le nom du scénario étant BTS_Messaging_Step serait enregistré en tant que C:\Projects\LoadTest\BTSLoad\LoadTests\BTS_Messaging_Step.loadtest le fichier de test de charge.  
  
###  <a name="BKMK_BTSCounters"></a>Ajouter un compteur personnalisé pour mesurer de BizTalk Server, indicateurs de Performance clés (KPI)  
 Suivez ces étapes pour ajouter un compteur des compteurs de performance qui mesurent les KPI de serveur BizTalk nécessaires à la détermination maximale acceptable débit acceptable de l’application BizTalk Server :  
  
1.  Dans le double-clic de l’Explorateur de solutions le test de charge que vous avez créé dans la section précédente pour afficher le test de charge dans l’éditeur de Test de charge.  
  
2.  Dans l’éditeur de Test de charge, cliquez pour développer **les ensembles de compteurs**. Notez qu’il n’existe aucun ensemble de compteurs prédéfinis pour BizTalk Server, par conséquent ensemble de compteurs « BizTalk Server » doit être ajouté à la liste de compteurs personnalisé définit.  
  
3.  Avec le bouton droit **les ensembles de compteurs** et sélectionnez **ajouter un ensemble de compteurs personnalisés**. Par défaut, cette action va créer un compteur personnalisé défini par le nom **Custom1**.  
  
4.  Avec le bouton droit le **Custom1** ensemble au compteur et sélectionnez **propriétés** pour définir le focus sur le **propriétés** boîte de dialogue pour l’ensemble de compteurs Custom1.  
  
5.  Double-cliquez sur le nom **Custom1** dans les **propriétés** boîte de dialogue, tapez **BizTalk** et appuyez sur la touche entrée pour renommer le compteur personnalisé, la valeur **BizTalk** .  
  
6.  Avec le bouton droit dans l’éditeur de Test de charge, le **BizTalk** ensemble au compteur et sélectionnez **ajouter des compteurs**.  
  
7.  Sous **ordinateur**, tapez le nom de l’un des ordinateurs BizTalk Server dans le groupe BizTalk Server pour afficher les catégories de moniteur de performances qui comprennent les compteurs de performance de BizTalk Server.  
  
    > [!IMPORTANT]  
    >  Pour garantir que toutes les catégories de performances de BizTalk Server et les compteurs de performance sont répertoriés, vous devrez peut-être taper dans le nom de domaine complet (ou adresse IP) d’un serveur BizTalk dans le groupe et vous devrez également démarrer les instances d’ordinateurs hôtes suivants sur le Ordinateur BizTalk Server.  
    >   
    >  -   Instances d’hôtes BizTalk qui sont liés aux orchestrations qui seront exécuteront pendant le test de charge.  
    > -   Instances des hôtes BizTalk comme envoyer ou recevoir des gestionnaires pour les adaptateurs qui seront exécuteront pendant le test de charge.  
  
8.  BizTalk Server fournit un ensemble complet des compteurs de performance. Pour déterminer le maximale acceptable Performance acceptable d’un serveur BizTalk application, vous devez uniquement ajouter les performances de BizTalk Server suivants compteurs à la **BizTalk** ensemble de compteurs personnalisé :  
  
    |Catégorie de performance|Compteur de performances|  
    |--------------------------|-------------------------|  
    |Processeur|% Temps processeur pour l’instance _Total du compteur.|  
    |Boîte de BizTalk : MessageBox : Compteurs généraux|Spool de taille pour le  *\<nom de base de données MessageBox de BizTalk >*:*\<nom de l’instance SQL Server >* instance de compteur. **Remarque :***\<nom de base de données MessageBox de BizTalk >* et  *\<nom de l’instance SQL Server >* sont seulement des espaces réservés pour les noms réels de BizTalk Base de données MessageBox et l’instance de SQL Server qui héberge la base de données MessageBox de BizTalk.   Ces espaces réservés doivent être remplacés par les noms réels de la base de données BizTalk MessageBox et instance associée de SQL Server.|  
    |BizTalk:messagerie|Documents reçus/s pour l’instance de compteur de hôte de réception.<br /><br /> Documents traités par seconde pour l’instance de compteur de transmission hôte.|  
    |BizTalk:agent des messages|Hôte de réception vitesse entrant de remise de messages pour le document.|  
    |BizTalk:agent des messages|Vitesse de sortie de publication du message pour l’hôte de transmission du document.|  
    |Orchestrations XLANG/s|Orchestrations réussies par seconde pour l’hôte de traitement de l’Orchestration|  
  
### <a name="modify-run-settings-to-map-counter-sets-to-appropriate-computers"></a>Modifier les paramètres d’exécution pour mapper des ensembles de compteurs pour les ordinateurs appropriés  
 Suivez ces étapes pour mapper les ensembles de compteurs approprié avec les ordinateurs appropriés pour le test de charge :  
  
1.  Dans **éditeur de Test de charge**, avec le bouton droit **paramètres d’exécution** et sélectionnez **gérer les ensembles de compteurs**.  
  
2.  Cliquez sur **ajouter l’ordinateur** pour ajouter un nouvel ordinateur à la liste. Une icône avec le texte mis en surbrillance **nouvel ordinateur** s’affiche sous **ordinateurs et ensembles de compteurs à surveiller**. Remplacez le texte mis en surbrillance en tapant le nom de l’ordinateur que vous souhaitez ajouter à la liste.  
  
3.  Après avoir ajouté l’ordinateur à la liste, cliquez pour développer la liste des ensembles de compteurs disponibles et activez le compteur disponible définit pour associer les ou les jeux de compteur à l’ordinateur.  
  
4.  Répétez les étapes 2 et 3 jusqu'à ce que vous avez associé des ensembles de compteurs à tous les ordinateurs pour lesquels vous souhaitez collecter des données de performances.  
  
###  <a name="BKMK_TestSettings"></a>Ajouter un fichier de paramètres de Test à la Solution pour exécuter des Tests et collecter des données à distance  
 Pour configurer le test de charge pour utiliser les ordinateurs de contrôleur de Test et l’Agent de Test que vous avez créé dans [étape 2 : configurer le contrôleur de Test de charge et les ordinateurs agents](../technical-guides/step-2-configure-load-test-controller-and-agent-computers.md), suivez les étapes de [ajouter des paramètres de test pour l’exécution à distance ou une collection de données à votre solution](http://go.microsoft.com/fwlink/?LinkId=209182)(http://go.microsoft.com/fwlink/?LinkId=209182) comme indiqué ci-dessous :  
  
1.  À l’étape 3, entrez le nom **BizTalkLoadTest**  
  
2.  Ignorer l’étape 6, car vous avez déjà entré un nom à l’étape 3.  
  
3.  Pour l’étape 7, entrez « Il s’agit des paramètres de test par défaut pour une série de tests à distance » sous **Description**.  
  
4.  Pour l’étape 8, sélectionnez le schéma d’affectation de noms par défaut.  
  
5.  Pour l’étape 9, sous **méthode d’exécution de Test** sélectionnez **l’exécution à distance**, sous **contrôleur** sélectionnez l’ordinateur de contrôleur de test et de laisser les propriétés restantes sur le **Rôles** page à leurs paramètres par défaut.  
  
6.  Pour l’étape 24, sélectionnez l’option **à exécuter l’hôte par défaut**, sélectionnez un **héberger type** de **par défaut**et sous **exécuter des tests dans un processus 32 ou 64 bits**, Sélectionnez l’option de **exécuter des tests dans un processus 64 bits sur un ordinateur 64 bits**.  
  
7.  Pour l’étape 25, sélectionnez **marquer un test comme ayant échoué si sa durée d’exécution dépasse** et laissez la valeur par défaut de 30 minutes sélectionné.  
  
8.  Pour l’étape 27b, sélectionnez la case à cocher **utiliser le contexte de chargement des assemblys dans le répertoire de test**, puis cliquez sur **Enregistrer sous**.  
  
9. Dans le **enregistrer en tant que** boîte de dialogue zone, vérifiez que le nom **BizTalkLoadTest** est entré en regard **nom de fichier**, puis cliquez sur **enregistrer**. Vous avez maintenant ajouté un fichier de paramètres de test à votre solution.