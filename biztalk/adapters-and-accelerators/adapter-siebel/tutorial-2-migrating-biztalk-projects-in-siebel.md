---
title: "Didacticiel 2 : Les projets BizTalk migration dans Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a2a1828-8cc8-4b80-99bd-c083c04e5d04
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b8d138d348e750102d82a4aba2e39bc7d119c8c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-2-migrating-biztalk-projects-in-siebel"></a>Didacticiel 2 : Migration des projets BizTalk dans Siebel
La version précédente de l’adaptateur Siebel fourni avec Microsoft BizTalk Server est différente de la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] dans nombreux aspects, notamment :  
  
-   L’expérience au moment du design de création d’un projet BizTalk.  
  
-   L’expérience de récupération de métadonnées.  
  
-   Nom de fichier de schéma et l’espace de noms.  
  
-   Mappages de type de données.  
  
-   Les opérations qui peuvent être effectuées à l’aide de l’adaptateur.  
  
-   Configuration des ports physiques dans la console Administration de BizTalk Server  
  
 Ces différences sont expliquées dans les rubriques dans [migration BizTalk projets créés à l’aide de la Version précédente de l’adaptateur Siebel](http://msdn.microsoft.com/library/ae61d3df-c5ca-4891-86b1-9f0dd6d3a59e).  
  
 Toutefois, vous pouvez apporter des modifications au projet BizTalk créé à l’aide de la version précédente de l’adaptateur et qu’il fonctionne avec la base de WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
 Ce didacticiel fournit des instructions sur les modifications que vous devez apporter au projet BizTalk existant créé à l’aide de la version précédente de l’adaptateur.  
  
> [!NOTE]
>  Dans ce didacticiel, par souci de concision, la version précédente de l’adaptateur Siebel sera appelée vPrev l’adaptateur Siebel. De même, un projet BizTalk qui utilise l’adaptateur Siebel vPrev est être appelé en tant que projet de BizTalk vPrev.  
  
## <a name="sample-used-for-the-tutorial"></a>Exemple utilisé pour le didacticiel  
 Ce didacticiel est basé sur un exemple qui montre comment migrer un projet BizTalk vPrev qui effectue une opération d’insertion sur le composant de gestion de compte Siebel (Siebel_BussComp_Migration). L’exemple est fourni avec Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemple d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Vous devez disposer d’un projet BizTalk de vPrev. Ce didacticiel implique un projet BizTalk qui effectue une opération d’insertion sur le composant de gestion de compte.  
  
-   Vous devez disposer d’un message de demande pour effectuer une opération d’insertion sur le composant de gestion de compte à l’aide de l’adaptateur Siebel vPrev. Le message de demande doit être conforme au schéma de l’opération d’insertion générée à l’aide de l’adaptateur Siebel vPrev.  
  
-   Vous devez avoir terminé les étapes de [conditions préalables pour créer des applications Siebel](../../adapters-and-accelerators/adapter-siebel/prerequisites-to-create-siebel-applications.md).  
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>Présentation d’un projet BizTalk créée à l’aide de la Version précédente de l’adaptateur  
 Les principaux composants d’un projet BizTalk de vPrev créés sont :  
  
-   **Orchestration BizTalk**. Il s’agit d’une orchestration simple qui Récupère les messages de demande à partir d’un emplacement de fichier, envoie le message de demande au système Siebel à l’aide d’un Siebel envoi / réception port, reçoit la réponse et l’enregistre dans un autre emplacement de fichier.  
  
-   **Schéma pour l’opération que vous souhaitez effectuer sur le composant d’entreprise Siebel**. Ce didacticiel implique un projet BizTalk qui effectue une opération d’insertion sur le composant de gestion de compte. Le schéma généré pour le composant de gestion de compte est AccountService_Account_x5d.xsd. Ce schéma est généré à l’aide de l’adaptateur Siebel vPrev.  
  
    > [!NOTE]
    >  Contrairement à la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], l’adaptateur Siebel vPrev ne prend pas en charge les générer des métadonnées pour des opérations spécifiques sur un composant d’entreprise. Par défaut, l’adaptateur génère le schéma pour toutes les opérations prises en charge sur le composant de gestion. Plusieurs de ces différences entre l’adaptateur Siebel vPrev et basée sur le WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], consultez [migration BizTalk projets créés à l’aide de la Version précédente de l’adaptateur Siebel](http://msdn.microsoft.com/library/ae61d3df-c5ca-4891-86b1-9f0dd6d3a59e).  
  
-   **Message de demande**. Le message de demande pour effectuer une opération d’insertion sur le composant de gestion de compte. Le schéma du message de demande est conforme au schéma de l’opération d’insertion comme exposés par l’adaptateur Siebel vPrev.  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>Comment migrer un projet BizTalk créée à l’aide de la Version précédente de l’adaptateur  
 L’objectif de ce didacticiel de migration consiste à vous permettent d’envoyer un message de demande, qui est conforme au schéma généré par l’adaptateur Siebel vPrev, à l’aide d’un port personnalisé WCF qui peut traiter uniquement les messages conformes à la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. Par conséquent, en bref, l’exercice de migration implique la configuration du port WCF-Custom pour traiter les messages qui ne sont pas conformes à la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]du schéma.  
  
 Toutefois, pour être en mesure de configurer le port WCF-Custom correctement, vous devez effectuer les tâches suivantes :  
  
-   Générer des métadonnées pour l’opération d’insertion sur le composant de gestion de compte à l’aide de la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
-   Mapper le message de demande pour effectuer une opération d’insertion à l’aide de l’adaptateur Siebel vPrev à un message de demande pour effectuer une opération d’insertion à l’aide de la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
-   Mapper le message de réponse reçu à l’aide de la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] au message de réponse pour l’adaptateur Siebel vPrev.  
  
-   Créer un Siebel WCF-Custom envoi-port de réception dans la console Administration de BizTalk Server.  
  
-   Configurer le port WCF-Custom pour utiliser les mappages de demande et de réponse.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Étape 1 : Modifier le projet BizTalk dans la base de données Oracle vPrev](../../adapters-and-accelerators/adapter-oracle-database/step-1-modify-the-vprev-biztalk-project-in-oracle-database.md)  
  
-   [Étape 2 : Configurer l’Orchestration dans la Console Administration de BizTalk Server pour utiliser l’adaptateur de base de données ORacle](../../adapters-and-accelerators/adapter-oracle-database/step-2-configure-an-orchestration-to-use-the-oracle-db-adapter-in-biztalk.md)  
  
-   [Étape 3 : Tester l’Application migrée avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/step-3-test-the-migrated-application-with-the-siebel-adapter.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels de l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/siebel-adapter-tutorials.md)