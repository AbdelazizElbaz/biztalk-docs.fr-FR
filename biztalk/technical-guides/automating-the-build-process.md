---
title: "Automatiser le processus de génération | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 995dac20-82a1-46ed-b8a3-0aa6182cb821
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c0e09e298694a3affd979eacc35ec43a1f92fab5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="automating-the-build-process"></a>Automatiser le processus de génération
Un processus de génération automatisé compile, déploie et exécute alors des tests de vérification de build (BVT) sur le dernier code source pour un projet à intervalles réguliers, prédéterminés. Puis un « rapport build » qui détaille la réussite ou l’échec du processus de génération, est transmis aux parties prenantes du projet. Le rapport de build est analysé pour déterminer les domaines du projet nécessitant une attention et si le projet doit être restauré à une version antérieure et.  
  
 La puissance d’un processus de génération automatisé est que qu’il peut être planifiée à exécuter pendant « off hours ». De cette manière, il peut garantir la stabilité du projet sans effectuer de cycles directement en s’éloignant lors du développement.   
 Cette rubrique fournit une vue d’ensemble du processus de génération, décrit la manière dont le test de vérification de build s’intègre dans le processus de génération, décrit les aspects des tests fonctionnels utilisés pendant les tests de vérification de build et fournit des informations sur l’importance de automatisation du processus de génération.  
  
## <a name="overview-of-the-build-process"></a>Vue d’ensemble du processus de génération  
 Avant de rechercher dans les détails du test, il est important à prendre en compte le contexte du test comment intègre le processus global de la build. Tous les groupes de produits de Microsoft de fonctionnent à partir de la philosophie que le processus de génération est la pulsation d’un projet logiciel. Cette approche est également utilisée par de nombreux haut au monde consultation des entreprises qui génèrent des solutions critiques en haut de la pile de logiciel Microsoft. Sans une pulsation stable et une vérification régulière de celui-ci, il est impossible de connaître l’intégrité du projet. Pour vous assurer que les groupes de produits ont une vision continue de l’intégrité globale du projet, le processus de génération est exécuté quotidiennement, généralement à minuit. Les étapes suivantes récapitulent un processus de génération automatisé classique :  
  
1.  Obtenir la dernière version de code source à partir du référentiel de code source.  
  
2.  Compiler le code source.  
  
3.  Compresser des fichiers binaires pour le déploiement – généralement à l’aide de scripts ou des fichiers de programme d’installation de Microsoft Windows.  
  
4.  Déployer le projet sur un serveur de test.  
  
5.  Exécuter automatiquement un jeu complet de tests de vérification de build (BVT).  
  
6.  Publier un rapport de build détaillé aux membres de l’équipe du projet.  
  
> [!NOTE]  
>  BVT est les tests fonctionnels qui vérifient les principales fonctionnalités de la solution pour tester sa qualité.  Vous devez vous assurer que votre BVT est suffisamment complètes pour évaluer la qualité de build, mais suffisamment petite pour s’exécuter dans le délai imparti de build quotidienne.  
  
> [!NOTE]  
>  Vous devez également considérer le déploiement, l’annulation du déploiement, configuration et installation des scripts ou des processus en tant que partie du projet de logiciel à des fins de test. Les opérations du projet, ainsi que le déploiement et la configuration de celui-ci, doivent être testées.  
  
 Ce processus est généralement effectué par matin environ 6 h 00, ce qui permet des premiers membres de l’équipe de commencer à travailler sur la build du jour. Si un ou plusieurs des BVT à partir de la nuit précédente a échoué, elle est la responsabilité de l’équipe pour résoudre ce problème dès que possible.  
  
 Un processus de build quotidienne présente de nombreux avantages pour le projet. Tout d’abord, il fournit une régulier pulsation (composée de la build quotidienne ainsi que les tests automatisés). En second lieu, à l’aide de tests BVT force l’intégration avec les systèmes qui est une tâche difficile, et cela tôt dans l’et réduit les risques de projet. En raison du délai requis pour les exécuter, les tests de performances et de contrainte sont généralement effectuées en dehors du processus de build quotidienne. Tests de performances et de contrainte sont généralement planifiées pour être effectuées sur une étape majeure build dans le projet.  
  
 Le processus de génération quotidienne peut être et a été utilisé, très efficacement sur des solutions BizTalk. Toutefois, vous devez vous assurer tâches qui sont généralement laissés à la fin dans les projets sont effectuées de manière itérative à partir du début. Par exemple, le déploiement dans BizTalk Server est certainement non trivial. Il est important que les scripts de déploiement automatisé être développée au préalable. Si vous ne le faites pas, vous obtiendrez déploiement manuel et sans déploiement la solution autant de fois dans le projet, ce qui vous coûter plus de temps à la fin. Il existe des outils disponibles pour le processus de génération quotidienne ; Visual Studio Team System et Team Foundation Server sont le choix principal pour de nombreuses personnes. Scripts MSBuild peuvent être utilisés pour piloter les étapes du processus de génération. Une autre solution consiste à ouvrir la source [CruiseControl.NET outil](http://go.microsoft.com/fwlink/?LinkId=116093) (http://go.microsoft.com/fwlink/?LinkId=116093).  
  
> [!NOTE]  
>  Utilisation de cet outil n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ce programme. L'utilisation de ce programme relève de votre seule responsabilité.  
  
 Pour plus d’informations sur l’automatisation de test à l’aide de Microsoft Test manager, consultez la rubrique [en cours d’exécution des Tests automatisés](http://go.microsoft.com/fwlink/?LinkID=208368) (http://go.microsoft.com/fwlink/?LinkID=208368) dans la documentation en ligne de Visual Studio 2010  
  
 Pour plus d’informations sur l’automatisation du processus de génération à l’aide de Visual Studio 2010, consultez [génération de l’Application](http://go.microsoft.com/fwlink/?LinkID=208369) (lien hypertexte « http://go.microsoft.com/fwlink/? LinkID = 208369" http://go.microsoft.com/fwlink/? LinkID = 208369) dans la documentation de Visual Studio 2010.  
  
## <a name="build-verification-testing"></a>Générer le test de vérification  
 Test de vérification de build comprend généralement les éléments suivants :  
  
-   **Tests unitaires** -étant donné que les tests unitaires sont généralement les premiers tests à développer, dans l’idéal, elles doivent être créées avant que le code a réellement été écrit, si vous utilisez réellement une approche du développement piloté par test. En les ajoutant dans BVT pendant les phases préliminaires d’un projet, vous fournissez au moins une certaine la couverture du code immédiatement. Comme le nombre de tests fonctionnels et par conséquent, augmente de la couverture de test, vous pouvez opter pour supprimer les BVT des tests unitaires.  
  
-   **Tests de détection de fumée** -bout en bout pour les tests fonctionnels qui testent les fonctionnalités de base de votre solution. Si elles échouent, pose problème grave. Il peuvent généralement être exécutées assez rapidement.  
  
-   **Les Tests fonctionnels** - ces cibles également des scénarios de bout en bout, mais dans ce cas ils tous les scénarios de test dans le projet. Pour les grands projets, il peut être judicieux de classer vos tests fonctionnels supplémentaire (par exemple, pour activer un composant particulier à tester rapidement, fiable et de manière isolée). Ces tests fonctionnels une fois approuvé sur votre solution comme point de vue fonctionnel correctes doivent être verrouillés.  
  
-   **Tests de vérification de la régression** - chaque fois qu’un bogue de la solution est détecté et résolu, vérification de régression des cas de test doit être ajoutés pour vérifier que le bogue est résolu et qu’il n’est pas réintroduit ultérieurement dans le cycle de vie du projet.  Ces tests seront généralement les cas qui ne sont pas abordées dans les cas de test fonctionnelles. Attendez-vous à ce que vos tests de vérification de régression augmente dans le nombre même après que la solution a été activée, si de nouveaux bogues seront détectés et résolus.  
  
 Sur très grands projets, vous devrez peut-être rendre votre BVT un sous-ensemble de la suite de tests fonctionnelles complètes (en raison d’une longueur de la durée de l’exécution). Pour les projets plus petits, BVT constitue l’intégralité du jeu. Évidemment, si vous vous apprêtez à intégrer les BVT dans le cadre de votre build quotidienne, l’ensemble du processus doit être automatisé. Dans le reste de cette rubrique, nous allons examiner comment vous pouvez utiliser BizUnit et autres outils pour y parvenir.  
  
## <a name="functional-testing"></a>Test fonctionnel  
 Dans le contexte des applications BizTalk les tests fonctionnels, tester un scénario de bout en bout spécifique. Lorsque vous effectuez ce type de test, il est utile d’imaginer que BizTalk Server comme une boîte noire que vous testez le point de vue fonctionnel à partir d’un point de vue externe. Par exemple, un test peut impliquer l’alimentation d’un message d’entrée (avec des valeurs connues) à un point de terminaison d’emplacement de réception (pour un exemple, URL, d’emplacement FTP, tout ce qui est votre choix de transport). Le test est ensuite surveiller le nombre correct de messages avec la sortie correcte qui est généré sur le côté envoi. Cela peut sembler relativement simple. Toutefois, lorsque vous pensez que certains scénarios nécessitent des entrées dans un certain ordre et à un moment donné, et vous cela composée avec d’autres exigences de la solution (par exemple, lors de l’enregistrement des données de suivi dans BAM), il devient évident qu’un outil et le framework peuvent être utilisés pour orchestrer cela.  
  
 Il est essentiel que le test fonctionnel est conçu pour couvrir tous les chemins d’accès possibles via votre solution. Cela doit inclure non seulement ces scénarios vous attendez en production, mais également les chemins d’accès de l’échec et les chemins d’accès de la gestion des exceptions vous avez implémenté mais espérons que jamais à utiliser : une expression couramment utilisée pour décrire ce test pour le scénario « jour incorrect ». Vous devez vous assurer toutes les orchestrations, tous les types de message autorisée, et toutes les branches de code sont testés par la suite de tests fonctionnels. Les sections suivantes décrivent le développement positifs et négatifs des cas de test fonctionnelles pour couvrir tous les chemins de code.  
  
 Pour plus d’informations sur les tests fonctionnels et les autres catégories de tests qui doivent être implémentées avant de placer une solution BizTalk Server en production, consultez la rubrique [liste de vérification : test de disponibilité opérationnelle](http://go.microsoft.com/fwlink/?LinkId=160138) dans le Guide des opérations BizTalk Server 2010 à [http://go.microsoft.com/fwlink/?LinkId=160138](http://go.microsoft.com/fwlink/?LinkId=160138).  
  
### <a name="positive-tests"></a>Tests positifs  
  
-   Il est important lorsque vous effectuez des tests pour vous assurer toutes les combinaisons des orchestrations, des pipelines, des messages positifs, et les points de terminaison sont transmises via la solution afin que tous les flux de message sont testés. Pour vous assurer de tester le code de tous les chemins d’accès nécessiteront probablement que vous traitez des différents messages avec un contenu différent.  
  
-   Lors du test, utilisez le type de transport qui sera utilisé en production. Malheureusement, trop souvent, test fonctionnel est effectuée uniquement à l’aide de l’adaptateur de fichier lorsque certains autres transport sera utilisé en production. Adoptant cette approche consiste à définir vous et l’ensemble du projet pour l’échec de la suite.  
  
-   Valider la charge utile de tous les messages sont envoyés à partir du système. Si les messages sont XML, vous devez valider leur schéma et les champs clés dans le message à l’aide d’expressions XPath.  
  
-   Valider les données de suivi stockées dans l’analyse BAM (si utilisé) ; toutes les autres données qui restent dans les référentiels de données externes doivent être pris en compte.  
  
-   Tester l’exécution de toutes les stratégies du moteur de règles d’entreprise (BRE) et de règles si votre solution utilise le moteur BRE.  
  
### <a name="negative-tests"></a>Tests négatifs  
  
-   Vérifiez que vous testez la gestion des messages non valides sur votre système. Vous devez vérifier que votre stratégie choisie (à rejeter les avant leur dans BizTalk Server, soit les suspendre) a correctement fonctionné.  
  
-   Lorsque vous testez la gestion des messages non valides, assurez-vous de que tester que toutes les orchestrations de la gestion des erreurs du côté réception ont été implémentées pour gérer les messages suspendus.  
  
-   Assurez-vous que vos scénarios d’échec de couvrent tous les blocs d’exception dans vos orchestrations.  Échec de test correctement est un problème courant.  
  
-   Si vous utilisez des transactions à long terme avec le comportement de compensation, tester ces scénarios très attentivement. Il s’agit d’une autre zone dans laquelle un test entraîne des conséquences graves dans un environnement de production.  
  
-   Vérifiez les échecs sont enregistrés correctement dans les journaux d’erreur approprié.  
  
## <a name="automation-is-key"></a>Automation est la clé  
 Pour effectuer toutes ces opérations efficacement, prenez le temps en amont pour automatiser le test. Un test manuel est long, source d’erreurs et coûteuse (en termes de temps et les coûts). Chaque fois que vous exécutez un test manuel, vous ajoutez un autre lot de tâches qui doivent être gérées par les ressources de projet (personnes de l’équipe). Grâce à l’automatisation au préalable, vous êtes en mesure d’obtenir un retour sur investissement initial qui est requis pour développer les tests chaque fois qu’elles sont exécutées. Les tests fonctionnels bon doivent s’exécuter rapidement et efficacement et être renouvelable ; chaque test doit également être autonome (il doit être indépendant de tout autre ; adoptant cette approche vous permet d’exécuter plusieurs tests séquentiellement comme une suite de tests.) Les tests fonctionnels doivent produire toujours le même résultat. Les tests fonctionnels mal écrits ou code mal écrit entraîne les résultats des tests différents entre les séries de tests, conduisant à une confusion et le temps perdu examiner la cause de l’échec.  
  
 Il est important de réduire l’effort de développement pour écrire chaque test fonctionnel. Généralement plus coûteux est pour produire un élément (en termes de temps de développement), les cas de test moins vous êtes susceptible de vous retrouver avec. Cela signifie que vous ont un niveau inférieur de la couverture de test sur votre code. En utilisant une infrastructure de test, vous pouvez développer des cas de test plus rapides et plus faciles et, par conséquent, rendre plus facile d’obtenir la couverture du code complet. La plupart des infrastructures de test bon utiliser une approche déclarative à la définition des tests. (Autrement dit, la configuration d’un test est stockée dans un fichier de configuration, qui est généralement un fichier XML). À l’aide d’un bon test framework vous permet de développer un fonctionnelle complète suite de tests de manière fiable et agile et évite d’avoir à « réinventer la roue », pour ainsi dire.  
  
## <a name="msbuild-support-for-biztalk-server-projects"></a>Prise en charge MSBUILD pour les projets BizTalk Server  
 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]Fournit la prise en charge pour la plateforme Microsoft Build Engine (MSBUILD), qui prend en charge la génération des projets managés dans des environnements lab de génération où Visual Studio n’est pas installé. MSBUILD gère la génération de projets à partir d’une ligne de commande et des fonctionnalités avancées, notamment la journalisation et le traitement par lots de MSBUILD. Pour plus d’informations sur MSBUILD, consultez [vue d’ensemble de MSBuild](http://go.microsoft.com/fwlink/?LinkId=131739) (http://go.microsoft.com/fwlink/?LinkId=131739).  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’un test automatisé](../technical-guides/implementing-automated-testing.md)