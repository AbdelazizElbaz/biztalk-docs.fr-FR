---
title: "Didacticiel 2 : Migration d’un projet BizTalk RFC SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- migrating, BizTalk project from previous version of the SAP adapter
- migration
- migrating, SAP RFC BizTalk project
ms.assetid: b4943613-23d2-4869-b033-ec07daabfac5
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80b5d53904b96267b1877310aa3480ce34a1bedc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-2-migrating-an-sap-rfc-biztalk-project"></a>Didacticiel 2 : Migration d’un projet BizTalk RFC SAP
La version précédente de l’adaptateur SAP fournis avec Microsoft BizTalk Server est différente de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] dans nombreux aspects, notamment :  
  
-   L’expérience au moment du design de création d’un projet BizTalk.  
  
-   L’expérience de récupération de métadonnées.  
  
-   Nom de fichier de schéma et l’espace de noms.  
  
-   Mappages de type de données.  
  
-   Les opérations qui peuvent être effectuées à l’aide de l’adaptateur.  
  
-   Configuration des ports physiques dans la console Administration de BizTalk Server.  
  
 Ces différences sont expliquées dans les rubriques dans [migration BizTalk projets créés à l’aide de la Version précédente de l’adaptateur SAP](http://msdn.microsoft.com/library/a486bac9-8952-43fd-8099-413f1491de37).  
  
 Toutefois, vous pouvez apporter des modifications au projet BizTalk créé à l’aide de la version précédente de l’adaptateur et qu’il fonctionne avec la base de WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
 Ce didacticiel fournit des instructions sur les modifications que vous devez apporter au projet BizTalk existant créé à l’aide de la version précédente de l’adaptateur.  
  
> [!NOTE]
>  Dans ce didacticiel, par souci de concision, la version précédente de l’adaptateur SAP sera appelée vPrev l’adaptateur SAP. De même, un projet BizTalk qui utilise l’adaptateur SAP vPrev est être appelé en tant que projet de BizTalk vPrev.  
  
## <a name="sample-used-for-the-tutorial"></a>Exemple utilisé pour le didacticiel  
 Ce didacticiel est basé sur un exemple qui montre comment migrer un projet BizTalk vPrev qui appelle une commande RFC dans un système SAP (SAP_RFC_Migration). L’exemple est fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Vous devez disposer d’un projet BizTalk de vPrev. Ce didacticiel implique un projet BizTalk qui appelle la RFC SD_RFC_CUSTOMER_GET.  
  
-   Vous devez disposer d’un message de demande à effectuer pour appeler le RFC SD_RFC_CUSTOMER_GET à l’aide de l’adaptateur SAP vPrev. Le message de demande doit être conforme au schéma de la RFC généré à l’aide de l’adaptateur SAP vPrev. L’exemple fourni pour ce didacticiel contient ce message de demande.  
  
-   [Créer le fichier de clé de nom fort et découvrez les outils](../../adapters-and-accelerators/adapter-sap/prerequisites-to-create-sap-applications.md)
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>Présentation d’un projet BizTalk créée à l’aide de la Version précédente de l’adaptateur  
 Les principaux composants d’un projet BizTalk de vPrev pour appeler une commande RFC sont :  
  
-   **Orchestration BizTalk**. Il s’agit d’une orchestration simple qui Récupère les messages de demande à partir d’un emplacement de fichier, envoie le message de demande au système SAP à l’aide d’un SAP envoi / réception port, reçoit la réponse et l’enregistre dans un autre emplacement de fichier.  
  
-   **Schéma de la RFC que vous souhaitez appeler dans le système SAP**. Ce didacticiel implique un projet BizTalk qui appelle la RFC SD_RFC_CUSTOMER_GET. Le schéma généré pour le document RFC est SD_RFC_CUSTOMER_GET__x32003.xsd. Ce schéma est généré à l’aide de l’adaptateur SAP vPrev.  
  
-   **Message de demande**. Le message de demande pour appeler le RFC SD_RFC_CUSTOMER_GET. Le schéma du message de demande est conforme au schéma de la RFC SD_RFC_CUSTOMER_GET comme exposés par l’adaptateur SAP vPrev.  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>Comment migrer un projet BizTalk créée à l’aide de la Version précédente de l’adaptateur  
 L’objectif de ce didacticiel de migration consiste à vous permettent d’envoyer un message de demande, qui est conforme au schéma généré par l’adaptateur SAP vPrev, à l’aide d’un port personnalisé WCF qui peut traiter uniquement les messages conformes à la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Par conséquent, en bref, l’exercice de migration implique la configuration du port WCF-Custom pour traiter les messages qui ne sont pas conformes à la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]du schéma.  
  
 Toutefois, pour être en mesure de configurer le port WCF-Custom correctement, vous devez effectuer les tâches suivantes :  
  
-   Générer des métadonnées pour la RFC SD_RFC_CUSTOMER_GET à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
-   Mapper le message de demande pour l’appel de la RFC à l’aide de l’adaptateur SAP vPrev à un message de demande pour l’appel de la RFC à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
-   Mapper le message de réponse reçu à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] au message de réponse pour l’adaptateur SAP vPrev.  
  
-   Créer une SAP de WCF-Custom envoi-port de réception dans la console Administration de BizTalk Server.  
  
-   Configurer le port WCF-Custom pour utiliser les mappages de demande et de réponse.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Étape 1 : Modifier le projet BizTalk vPrev pour appeler une commande RFC](../../adapters-and-accelerators/adapter-sap/step-1-modify-the-vprev-biztalk-project-for-invoking-an-rfc.md)  
  
-   [Étape 2 : Configurer l’Orchestration dans la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-sap/step-2-configure-the-orchestration-in-biztalk-server-administration-console1.md)  
  
-   [Étape 3 : Tester l’Application migrée](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application6.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)