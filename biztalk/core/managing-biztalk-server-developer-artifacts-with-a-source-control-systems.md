---
title: Systèmes de contrôle de la gestion des artefacts de développement de BizTalk Server avec une Source | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ce25b112-38c9-40c8-9a5f-a2855572aabb
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 829749911bd4f3ca6aee1da42578a1aac28db7ae
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="managing-biztalk-server-developer-artifacts-with-a-source-control-systems"></a>Gestion des artefacts de développement BizTalk Server avec un système de contrôle de code source
L'une des priorités essentielles est de protéger votre projet BizTalk de pannes systèmes inattendues. Pour ce faire, l'une des méthodes de protection des fichiers d'un projet consiste à utiliser un système de contrôle de code source, tel que Team Foundation Server Source Control et Microsoft Visual SourceSafe. Cette rubrique décrit certaines stratégies élémentaires concernant l'organisation des projets pour qu'ils fonctionnent au mieux avec tout système de contrôle de code source, et présente des suggestions d'utilisation de Visual SourceSafe.  
  
## <a name="basic-organization-strategies"></a>Stratégies d'organisation élémentaires  
 Vous pouvez suivre certaines stratégies d'organisation quel que soit le système de contrôle de code source que vous utiliserez. Ces stratégies garantissent que la structure de fichiers du projet est organisée à la fois pour le développement et le contrôle du code source.  
  
### <a name="use-a-consistent-folder-structure-for-solutions-and-projects"></a>Utilisation d'une structure de dossiers cohérente pour les solutions et les projets  
 Le développement dans un environnement de travail en équipe est plus simple à gérer si une structure commune de stockage des solutions et projets [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] est adoptée par l'ensemble de l'équipe. Cela est confirmé en particulier lorsque chaque projet BizTalk est généré et utilise des fichiers de liaison dont se serviront les équipes de création, de test et de déploiement.  
  
 Bien souvent, le développement démarre sans que les membres de l'équipe ne prennent le temps de normaliser les structures des dossiers. Ce mode de fonctionnement entraîne inévitablement des conséquences en termes de coût, puisque les liaisons du projet et les ateliers de test doivent être « retouchés » au fur et à mesure du développement de la solution.  
  
### <a name="keep-source-control-and-file-system-structures-identical"></a>Maintien du contrôle du code source et des structures de système de fichiers identiques  
 Pour simplifier la gestion des multiples environnements de développement, créez dans le système de contrôle du code source une structure de dossiers qui corresponde à la structure du système de fichiers local. Un développeur peut ainsi obtenir simplement la version la plus récente et il sait que la structure sur le disque est conforme aux normes de l'équipe.  
  
### <a name="define-and-use-a-common-root-folder"></a>Définition et utilisation d'un dossier racine commun  
 Il est recommandé de conserver tout le code d'un projet ainsi que les éléments livrables dans un même dossier racine qui peut ensuite être créé sur les ordinateurs des développeurs. Il est plus simple de gérer les artefacts de développement et de maintenir une configuration cohérente lorsque tous les développeurs utilisent la même racine. Par exemple, vous créez un dossier racine $/SysInteg2009 dans Visual SourceSafe et tous les développeurs créent le dossier C:\SysInteg2009 sur leur système de fichiers local.  
  
### <a name="create-a-master-solution-that-will-hold-all-projects"></a>Création d'une solution maître hébergeant tous les projets  
 La solution maître est en principe utilisée comme solution principale de création. Elle est recommandée pour les projets BizTalk de complexité moyenne à haute.  
  
### <a name="store-all-biztalk-projects-under-the-master-solution"></a>Stockage de tous les projets BizTalk dans la solution maître  
 Il est très pratique d'organiser tous les projets BizTalk connexes dans la même solution maître. La structure du système de contrôle de code source doit refléter cette hiérarchie.  
  
### <a name="divide-the-folder-structure-into-shared-and-process-specific-sections"></a>Division de la structure de dossiers en sections partagées et en sections spécifiques au processus  
 Lors de la création de la structure de fichiers, vous divisez généralement la structure des dossiers afin de séparer les entités partagées et les entités commerciales spécifiques au processus. Les entités partagées sont communes à plusieurs projets et peuvent contenir des classes Helper.  
  
 Par exemple, les trois premiers dossiers de la liste suivant sont classés par entité partagée, et les deux derniers par processus d'entreprise.  
  
 C:\SysInteg2009\\_Master_Solution\Shared\  
  
 C:\SysInteg2009\\_Master_Solution\Shared\EmailHelper  
  
 C:\SysInteg2009\\_Master_Solution\Shared\SharedSchema  
  
 C:\SysInteg2009\\_Master_Solution\AccountRequest\  
  
 C:\SysInteg2009\\_Master_Solution\AccountValidate\  
  
### <a name="separate-pipeline-projects-into-distinct-projects"></a>Séparation des projets de pipeline en projets distincts  
 Au cours du développement des composants de pipeline, il est courant de devoir modifier et retester un pipeline indépendant du reste de la solution. C'est la raison pour laquelle il est souvent préférable de conserver les solutions de pipeline en tant que projet BizTalk distinct. L'assembly de pipeline qui en résulte peut alors être supprimé et redéployé sans besoin de lier à nouveau le reste de la solution.  
  
 En outre, il est très fréquent de conserver le code qui implémente les interfaces de pipeline réelles et la logique de traitement des pipelines dans un projet distinct avec une référence à partir du projet BizTalk (qui contient les fichiers .btp) vers le projet [!INCLUDE[btsCSharp](../includes/btscsharp-md.md)] ou Microsoft [!INCLUDE[btsVBNet](../includes/btsvbnet-md.md)].  
  
### <a name="keep-deployment-and-test-scripts-with-their-projects"></a>Stockage des scripts de développement et de test avec les projets  
 Pour permettre un processus de création et de déploiement unifié, la création et l'installation des scripts doivent être effectuées par les développeurs, mais ils doivent être accessibles et réutilisables pour la solution. Si les scripts sont écrits dans le but d'être réutilisés, des tâches telles que le déploiement d'un package de solution complète peuvent alors les réutiliser. Par exemple, si les scripts de déploiement et d'annulation de déploiement acceptent des paramètres pour spécifier les emplacements des DLL et des dossiers de fichiers de liaison, ils peuvent être réutilisés lorsque les assemblys [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] compilés se trouvent à un autre emplacement.  
  
 Avec cette méthode, les développeurs ajoutent les scripts d'installation au dossier pour leurs processus spécifiques et peuvent ensuite écrire un seul processus pour réaliser le déploiement de tous les processus.  
  
### <a name="use-unique-strong-name-keys-when-appropriate"></a>Utilisation de clés de noms forts uniques si nécessaire  
 En principe une solution [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] unique utilise un seul fichier de clé, car la solution est considérée comme une entité unique et gérée en tant que telle. Si la solution d'entreprise développée est vraiment composée de plusieurs parties distinctes, déterminez si vous devez utiliser deux fichiers de clés. L'utilisation de plusieurs clés, dans ce cas, permet de traiter chaque partie en tant qu'entité indépendante, par exemple avec des méthodes de mise à niveau différentes.  
  
 En ce qui concerne les projets d'assistance, les mêmes considérations s'appliquent. Si le projet d'assistance est (ou sera) une entité distincte, il doit être créé à l'aide d'une clé de nom fort distincte.  
  
### <a name="put-dependent-dlls-into-a-separate-folder"></a>Installation des DLL dépendantes dans un dossier séparé  
 Lors de la création de la structure de dossiers, il est utile de créer un dossier commun pour y placer toutes les DLL qui sont référencées en tant que dépendances de fichier. Si les développeurs suivent tous la même structure de dossiers, les références aux fichiers ne seront pas interrompues lorsque les solutions seront déplacées entre les développeurs ou les stations de travail.  
  
### <a name="keep-test-messages-in-a-msgs-folder"></a>Stockage des messages de test dans un dossier  « Msgs »  
 Au cours du développement des schémas et de l'utilisation de messages, il est fréquent de consacrer des efforts au test de divers exemples de messages sur le schéma XML et les processus d'orchestration.  
  
 Dans la solution réelle, les exemples de messages sont des éléments de valeur car ils contiennent des données significatives pour la solution d'entreprise. Les valeurs aléatoires ou factices dans le même message entraînent généralement un échec du processus. Il faut par conséquent traiter les exemples de message avec autant de précaution que le code de la solution.  
  
 Pour vous aider à gérer les fichiers de messages, conservez les messages de test dans un dossier spécifique intitulé « msgs ». En cas d'existence à la fois d'« instances générées » et d'« exemples de messages » (messages d'un système existant par exemple), conserver ces messages séparément permet de comparer le schéma développé et les données réelles.  
  
 Dans un projet d'intégration, il existe souvent plusieurs versions des schémas, et donc, plusieurs versions des fichiers de messages. Pour distinguer les exemples de messages, utilisez les numéros de version lorsque vous nommez les fichiers.  
  
### <a name="managing-other-files"></a>Gestion des autres fichiers  
 Il est possible de grouper et de stocker certains types de fichiers dans un dossier distinct, et d'autres types avec d'autres fichiers dans un dossier commun. Établissez une stratégie sur le mode de gestion de chaque type de fichier et suivez-la constamment.  
  
## <a name="working-with-biztalk-server-and-visual-sourcesafe"></a>Utilisation de BizTalk Server et de Visual SourceSafe  
 Cette section traite des considérations relatives à l'utilisation de Visual SourceSafe, y compris la gestion d'Unicode, l'utilisation de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour le contrôle du code source, le moment de l'archivage, le contrôle de la version et d'autres points.  
  
### <a name="solution-character-sets"></a>Jeux de caractères de la solution  
 Il existe une limite connue avec Visual SourceSafe en ce qui concerne la gestion des fichiers Unicode. Lorsque vous utilisez des solutions BizTalk, il est essentiel d'éviter que Visual SourceSafe n'endommage les fichiers Unicode de BizTalk Server.  
  
##### <a name="to-enable-visual-sourcesafe-to-work-with-biztalk-server-unicode-files"></a>Pour permettre à Visual SourceSafe d'utiliser les fichiers Unicode BizTalk Server  
  
1.  Démarrez l'administrateur Visual SourceSafe 8.0.  
  
2.  Sélectionnez la base de données SourceSafe à utiliser.  
  
3.  Dans le menu **Outils** , cliquez sur **Options**.  
  
4.  Cliquez sur le **Types de fichiers** onglet.  
  
5.  Ajoutez les éléments suivants à la fin de la liste des fichiers binaires. Vérifiez que des points-virgules se trouvent bien entre chaque type de fichier.  
  
     *.btm;\*.btp;\*.xsd;\*.odx  
  
6.  Cliquez sur **OK**.  
  
 Visual SourceSafe n'inspectera plus les fichiers BizTalk Server et ne tentera pas de modifier leur format.  
  
### <a name="use-visual-studio-for-source-control-operations"></a>Utilisation de Visual Studio pour des opérations de contrôle du code source  
 Toute création et manipulation de projet dans Visual SourceSafe doivent être réalisées à l'aide des menus de prise en charge intégrés de Visual SourceSafe dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. N'utilisez pas l'Explorateur Visual SourceSafe pour effectuer ces opérations.  
  
### <a name="when-to-check-in-biztalk-server-projects"></a>Quand archiver les projets BizTalk Server  
 En ce qui concerne l'utilisation de Visual SourceSafe, il est recommandé d'archiver le code uniquement une fois qu'il a réussi les tests fonctionnels et que le développeur considère qu'il code sera correctement créé sans endommager du code associé. L'application de cette méthode à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] se traduit par les directives suivantes :  
  
-   Les projets BizTalk qui ne contiennent que des schémas de messages ne doivent pas être archivés tant que ces derniers n'ont pas été testés avec succès avec divers exemples de messages.  
  
-   Les projets BizTalk contenant un processus d'entreprise en doivent pas être archivés tant que la solution n'a pas été testée avec succès à l'aide des messages entrants et sortants adéquats, et à l'aide des ports d'envoi et de réception appropriés.  
  
-   Les projets de service Web ASP.NET ne doivent pas être archivés tant que le code du service Web n'a pas été testé avec le système initiateur ou à l'aide d'un atelier de test.  
  
 Si vous suivez cette méthode, le référentiel Visual SourceSafe comportera toujours une génération qui pourra être créée et testée avec succès. Ce point est important si l'approche de la « génération nocturne » doit être respectée.  
  
### <a name="checking-in-intermediate-versions"></a>Archivage des versions intermédiaires  
 L'autre méthode d'archivage des fichiers est l'archivage des versions « intermédiaires ». Dans cette approche, une version intermédiaire n’a pas encore été atteint les tests fonctionnels et peut être considérée comme « entre les builds ». Cela n’est généralement pas une approche recommandée, car il s’arrête au principe général de toujours disposer d’une version pouvant être générée dans le système de contrôle de code source. En revanche, certaines équipes préfèrent cette approche car elle permet aux développeurs d'utiliser le système de contrôle du code source afin d'archiver et de restaurer des versions sans avoir besoin de répondre aux critères d'archivage d'une génération formelle.  
  
 Si l'archivage des versions intermédiaires est requis, vous ne devez pas supposer que le système de contrôle du code source contient une version pouvant être générée, mais plutôt faire la distinction entre les versions intermédiaires et les versions de génération. Visual SourceSafe vous permet d'effectuer cet archivage soit automatiquement soit à partir du processus. Par exemple :  
  
-   Les développeurs signalent au gestionnaire de génération lorsqu'une version pouvant être générée est ajoutée à Visual SourceSafe.  
  
-   Les développeurs archivent une version testée, prête pour la génération dans une zone promue dans Visual SourceSafe. Cette zone est ensuite utilisée comme source sur laquelle la génération maître est basée.  
  
-   Le code ou script utilisant les interfaces COM Visual SourceSafe peut être rédigé. Par exemple, vous pouvez utiliser une étiquette particulière pour indiquer le code prêt à être généré ; le script recherche alors cette étiquette et « épingle » cette source dans une branche distincte de Visual SourceSafe. Cette dernière est ensuite utilisée comme source pour les générations maîtres.  
  
### <a name="comparing-files"></a>Comparaison de fichiers  
 Vous pouvez vous aider de Visual SourceSafe pour trouver les différences entre deux versions différentes d'un fichier source [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cela est possible avec des artefacts tels que des mappages et des schémas, ainsi que les fichiers associés que sont par exemple les messages de test ou même les fichiers de configuration exportés.  
  
> [!NOTE]
>  Lorsque vous comparez des mappages, vous devez modifier votre mappage avant de le vérifier car Visual SourceSafe réalisera sinon une comparaison binaire au moment de rechercher les différences qui existent avec la version suivante. Cela tient au fait que les informations de codage ne sont pas ajoutées au fichier XML de mappage tant que vous ne l'avez pas modifié.  
  
### <a name="version-controlling-non-biztalk-server-project-files"></a>Fichiers de projet non BizTalk Server de contrôle de version  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise d'autres fichiers qui peuvent comporter des versions et être stockés dans Visual SourceSafe, comme par exemple :  
  
-   Fichiers de liaison (de développement et de test)  
  
-   Assemblys de pipeline personnalisé  
  
-   Données de test (par exemple, messages de test)  
  
-   Faisceaux de test (qui peuvent changer au cours du projet)  
  
-   Scripts de génération, de déploiement, de démarrage et d'arrêt que les équipes de développement et de génération ont besoin de partager  
  
 Si ces fichiers sont associés à un projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk particulier, vous pouvez les inclure dans le projet BizTalk et les gérer à l'aide des fonctions intégrées de contrôle du code source de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
##### <a name="to-include-a-file-or-folder-into-an-existing-visual-studio-project"></a>Pour inclure un fichier ou un dossier dans un projet Visual Studio existant  
  
1.  Dans l’Explorateur de solutions, cliquez sur **afficher tous les fichiers**.  
  
2.  Sélectionnez le dossier ou le fichier à inclure dans la solution.  
  
3.  Cliquez sur le dossier ou fichier, puis cliquez sur **inclure dans le projet**.  
  
> [!NOTE]
>  Vous ne devez EN AUCUN CAS utiliser l'Explorateur Visual SourceSafe Explorer pour gérer des éléments faisant partie d'un projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] sous contrôle du code source.  
  
### <a name="checking-the-visual-sourcesafe-database"></a>Vérification de la base de données Visual SourceSafe  
 Lorsque les bases de données Visual SourceSafe sont volumineuse, utilisées de manière intensive ou que de nombreux utilisateurs y accèdent simultanément, il est recommandé d'exécuter régulièrement la commande Analyse VSS DB à partir du menu Visual SourceSafe. Si l'analyse détecte des erreurs, vous pouvez les résoudre à l'aide de la commande d'analyse et résolution VSS DB. Ces deux commandes demandent le verrouillage de la base de données Visual SourceSafe, donc toutes les personnes doivent être déconnectées de Visual SourceSafe.