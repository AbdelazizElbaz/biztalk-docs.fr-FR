---
title: "Didacticiel : Migrer des projets BizTalk à l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a393219-bae8-4e08-acc8-76986600d0de
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0948e79b7f236bb20bbff9101195809bcc921a68
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-migrate-biztalk-projects-to-the-oracle-database-adapter"></a>Didacticiel : Migrer des projets BizTalk à l’adaptateur de base de données Oracle
Le ODBC l’adaptateur BizTalk pour base de données Oracle fourni avec Microsoft BizTalk Server diffère de la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] dans nombreux aspects, notamment :  
  
-   L’expérience au moment du design de création d’un projet BizTalk.  
  
-   L’expérience de récupération de métadonnées.  
  
-   Nom de fichier de schéma et l’espace de noms.  
  
-   Mappages de type de données.  
  
-   Les opérations qui peuvent être effectuées à l’aide de l’adaptateur.  
  
-   Configuration des ports physiques dans la console Administration de BizTalk Server  
  
 Ces différences sont expliquées dans les rubriques dans [migration BizTalk projets créés à l’aide de l’adaptateur ODBC pour base de données Oracle pour BizTalk](http://msdn.microsoft.com/library/18f40265-c7f3-44a1-99b6-1b1dc800561e).  
  
 Toutefois, vous pouvez apporter des modifications au projet BizTalk qui a été créé à l’aide de l’adaptateur ODBC pour BizTalk pour base de données Oracle et qu’il fonctionne avec la base de WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
 Ce didacticiel fournit des instructions sur les modifications que vous devez apporter au projet BizTalk existant créé à l’aide de l’adaptateur ODBC pour BizTalk pour base de données Oracle.  
  
> [!NOTE]
>  Dans ce didacticiel, par souci de concision, la ODBC l’adaptateur BizTalk pour base de données Oracle est appelé « adaptateur de base de données Oracle vPrev ». De même, un projet BizTalk qui utilise l’adaptateur de base de données Oracle vPrev sera appelé « projet BizTalk de vPrev. »  
  
## <a name="sample-used-for-the-tutorial"></a>Exemple utilisé pour le didacticiel  
 Ce didacticiel est basé sur un exemple qui montre comment migrer un projet BizTalk de vPrev (Oracle_Migration). L’exemple est fourni avec Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Vous devez disposer d’un projet BizTalk de vPrev. Ce didacticiel implique un projet BizTalk qui effectue une opération d’insertion sur une table. La table CUSTOMER est créée sous le schéma SCOTT en exécutant les scripts SQL fournis avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] exemples.  
  
-   Vous devez disposer d’un message de demande pour effectuer une opération d’insertion sur la base de données Oracle à l’aide de l’adaptateur de base de données Oracle vPrev. Le message de demande doit être conforme au schéma de l’opération d’insertion générée à l’aide de l’adaptateur de base de données Oracle vPrev.  
  
-   Vous devez avoir terminé les étapes de [conditions préalables](../../adapters-and-accelerators/adapter-oracle-database/prerequisites-to-create-oracle-database-applications.md) 
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>Présentation d’un projet BizTalk créée à l’aide de la Version précédente de l’adaptateur  
 Les principaux composants d’un projet BizTalk de vPrev créés sont :  
  
-   **Orchestration BizTalk**. Il s’agit d’une orchestration simple qui Récupère les messages de demande à partir d’un emplacement de fichier, envoie le message de demande à la base de données Oracle à l’aide d’Oracle envoi / réception port, reçoit la réponse et l’enregistre dans un autre emplacement de fichier.  
  
-   **Schéma pour l’opération que vous souhaitez effectuer sur la base de données Oracle**. Ce didacticiel implique un projet BizTalk qui effectue une opération d’insertion sur la table CUSTOMER dans le schéma SCOTT. La table CUSTOMER est créée sous le schéma SCOTT en exécutant les scripts SQL fournis avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] exemples. Le schéma généré pour la table CUSTOMER est CUSTOMERService_CUSTOMER_x5d.xsd. Ce schéma est généré à l’aide de l’adaptateur de base de données Oracle vPrev.  
  
    > [!NOTE]
    >  Contrairement à la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], l’adaptateur de base de données Oracle vPrev ne prend pas en charge la génération de métadonnées pour des opérations spécifiques sur une table de base de données Oracle. Par défaut, l’adaptateur génère le schéma pour toutes les opérations prises en charge sur la table. Plusieurs de ces différences entre l’adaptateur de base de données Oracle vPrev et basée sur le WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [migration BizTalk projets créés à l’aide de l’adaptateur ODBC pour base de données Oracle pour BizTalk](http://msdn.microsoft.com/library/18f40265-c7f3-44a1-99b6-1b1dc800561e).  
  
-   **Message de demande**. Le message de demande pour effectuer une opération d’insertion sur la table CUSTOMER. Le schéma du message de demande est conforme au schéma de l’opération d’insertion, comme exposés par la version précédente de l’adaptateur de base de données Oracle.  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>Comment migrer un projet BizTalk créée à l’aide de la Version précédente de l’adaptateur  
 L’objectif de ce didacticiel de migration consiste à vous permettent d’envoyer un message de demande, qui est conforme au schéma généré par l’adaptateur de base de données Oracle vPrev, à l’aide d’un port personnalisé WCF qui peut traiter uniquement les messages conformes à la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Par conséquent, en bref, l’exercice de migration implique la configuration du port WCF-Custom pour traiter les messages qui ne sont pas conformes à la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]du schéma.  
  
 Toutefois, pour être en mesure de configurer le port WCF-Custom correctement, vous devez effectuer les tâches suivantes :  
  
-   Générer les métadonnées pour l’opération d’insertion sur la SCOTT. Table des clients à l’aide de la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
-   Mapper le message de demande pour effectuer une opération d’insertion à l’aide de l’adaptateur de base de données Oracle vPrev à un message de demande pour effectuer une opération d’insertion à l’aide de la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
-   Mapper le message de réponse reçu à l’aide de la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] au message de réponse pour l’adaptateur de base de données Oracle vPrev.  
  
-   Créer un Oracle WCF-Custom envoi-port de réception dans la console Administration de BizTalk Server.  
  
-   Configurer le port WCF-Custom pour utiliser les mappages de demande et de réponse.  
  
 
  
## <a name="see-also"></a>Voir aussi  
[Prise en main de Biztalk Server](../../core/getting-started-with-biztalk-server.md)