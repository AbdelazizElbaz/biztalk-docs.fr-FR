---
title: "Didacticiel 1 : Migrer des projets BizTalk à l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b4d2dbb-e37c-4d70-831f-3bdac3c28c97
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ca17095841fb154be9ec34766a34f174414cd82
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-1-migrate-biztalk-projects-to-the-sql-adapter"></a>Didacticiel 1 : Migrer des projets BizTalk à l’adaptateur SQL
La version précédente de l’adaptateur SQL fourni avec Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] diffère de la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] dans nombreux aspects, notamment :  
  
-   L’expérience au moment du design de création d’un projet BizTalk.  
  
-   L’expérience de récupération de métadonnées.  
  
-   Nom de fichier de schéma et l’espace de noms.  
  
-   Mappages de type de données.  
  
-   Les opérations qui peuvent être effectuées à l’aide de l’adaptateur.  
  
-   Configuration des ports physiques dans la console Administration de BizTalk Server  
  
 Ces différences sont expliquées dans les rubriques de migration BizTalk projets créés à l’aide de la Version précédente de l’adaptateur SQL.  
  
 Toutefois, vous pouvez apporter des modifications au projet BizTalk qui a été créé à l’aide de la version précédente de l’adaptateur et qu’il fonctionne avec la base de WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
 Ce didacticiel fournit des instructions sur les modifications que vous devez apporter au projet BizTalk existant créé à l’aide de la version précédente de l’adaptateur.  
  
> [!NOTE]
>  Dans ce didacticiel, par souci de concision, la version précédente de l’adaptateur SQL sera appelée vPrev l’adaptateur SQL. De même, un projet BizTalk qui utilise l’adaptateur SQL vPrev est être appelé en tant que projet de BizTalk vPrev.  
  
> [!IMPORTANT]
>  Ce didacticiel fournit des conseils sur la migration d’un projet BizTalk adaptateur SQL vPrev qui effectue une opération d’insertion de base sur une table de base de données SQL Server. Ce didacticiel ne couvre pas tous les scénarios possibles pour la migration à partir de l’adaptateur SQL vPrev vers le nouveau basé sur WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Vous devez utiliser ce didacticiel de migration de base et modifier en conséquence pour apporter des modifications qui s’applique à votre projet existant.  
  
## <a name="sample-used-for-the-tutorial"></a>Exemple utilisé pour le didacticiel  
 Ce didacticiel est basé sur un exemple qui montre comment migrer un projet BizTalk de vPrev (SQL_Migration). L’exemple est fourni avec Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez les exemples.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Vous devez disposer d’un projet BizTalk de vPrev. Ce didacticiel implique un projet BizTalk qui effectue une opération d’insertion sur une table dans la base de données SQL Server. La table Customer a la structure suivante :  
  
    |Nom de la colonne| Description|  
    |-----------------|-----------------|  
    |v_custid|Type entier clé, principal, le champ d’identité|  
    |Nom|type de nchar(10)|  
  
-   Vous devez disposer d’un message de demande pour effectuer une opération d’insertion sur la base de données SQL Server à l’aide de l’adaptateur SQL vPrev. Le message de demande doit être conforme au schéma de l’opération d’insertion générée à l’aide de l’adaptateur SQL vPrev.  
  
-   Vous devez avoir terminé les étapes de [avant de vous développer des Applications BizTalk](http://msdn.microsoft.com/library/3539741d-5266-43d4-9b7b-73e82f0ed4f6).  
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>Présentation d’un projet BizTalk créée à l’aide de la Version précédente de l’adaptateur  
 Les principaux composants d’un projet BizTalk de vPrev créés sont :  
  
-   **Orchestration BizTalk**. Il s’agit d’une orchestration simple qui Récupère les messages de demande à partir d’un emplacement de fichier, envoie le message de demande à la base de données SQL Server à l’aide de WCF-Custom envoi / réception port, reçoit la réponse et l’enregistre dans un autre emplacement de fichier.  
  
-   **Schéma pour l’opération que vous souhaitez effectuer sur la base de données SQL Server**. Ce didacticiel implique un projet BizTalk qui effectue une opération d’insertion sur la table Customer. Le schéma généré pour la table Customer est InsertCustomerService.xsd. Ce schéma est généré à l’aide de l’adaptateur SQL vPrev.  
  
-   **Message de demande**. Le message de demande pour effectuer une opération d’insertion sur la table Customer. Le schéma du message de demande est conforme au schéma de l’opération d’insertion, comme exposés par la version précédente de l’adaptateur SQL.  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>Comment migrer un projet BizTalk créée à l’aide de la Version précédente de l’adaptateur  
 L’objectif de ce didacticiel de migration consiste à vous permettent d’envoyer un message de demande, qui est conforme au schéma généré par l’adaptateur SQL vPrev, à l’aide d’un port personnalisé WCF qui peut traiter uniquement les messages conformes à la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Par conséquent, en bref, l’exercice de migration implique la configuration du port WCF-Custom pour traiter les messages qui ne sont pas conformes à la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]du schéma.  
  
 Toutefois, pour être en mesure de configurer le port WCF-Custom correctement, vous devez effectuer les tâches suivantes :  
  
-   Générer des métadonnées pour l’opération d’insertion sur la table Customer à l’aide de la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
-   Mapper le message de demande pour effectuer une opération d’insertion à l’aide de l’adaptateur SQL vPrev à un message de demande pour effectuer une opération d’insertion à l’aide de la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
-   Mapper le message de réponse reçu à l’aide de la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] au message de réponse de l’adaptateur SQL vPrev.  
  
-   Créer un service WCF-Custom SQL envoi-port de réception dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
-   Configurer le port WCF-Custom pour utiliser les mappages de demande et de réponse.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Étape 1 : Modifier le projet BizTalk à l’aide de l’adaptateur SQL vPrev](../../adapters-and-accelerators/adapter-sql/step-1-modify-the-vprev-biztalk-project-using-the-sql-adapter.md)  
  
-   [Étape 2 : Configurer l’Orchestration dans la Console Administration de BizTalk Server à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-orchestration-to-use-the-sql-adapter-in-biztalk-server.md)  
  
-   [Étape 3 : Tester l’Application migrée qui utilise l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/step-3-test-the-migrated-application-that-uses-the-sql-adapter.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/sql-adapter-tutorials.md)