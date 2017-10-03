---
title: "Didacticiel 4 : Migration d’un SAP de réception IDOC BizTalk projet | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- migration, SAP Receive IDOC BizTalk project
- migrating, SAP Receive IDOC BizTalk project
- migration
ms.assetid: 74b667d8-2d8c-4c15-9dd2-f13521404b85
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 943c80e84bc192330fd870a45c0b5fb60761a33d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-4-migrating-an-sap-receive-idoc-biztalk-project"></a>Didacticiel 4 : Migration d’un SAP de réception projet BizTalk IDOC
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
 Ce didacticiel est basé sur un exemple qui montre comment migrer un projet BizTalk vPrev qui reçoit un IDOC de fichier plat à partir d’un système SAP (ReceiveIDOC_Migration). L’exemple est fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Vous devez disposer d’un projet BizTalk de vPrev. Ce didacticiel implique un projet BizTalk qui reçoit un IDOC ORDERS03 à partir d’un système SAP.  
  
-   [Créer le fichier de clé de nom fort et découvrez les outils](../../adapters-and-accelerators/adapter-sap/prerequisites-to-create-sap-applications.md)

  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>Présentation d’un projet BizTalk créée à l’aide de la Version précédente de l’adaptateur  
 Les principaux composants d’un projet BizTalk de vPrev pour recevoir un IDOC sont :  
  
-   **Orchestration BizTalk**. Il s’agit d’un simple orchestration qui se compose d’un SAP port de réception qui reçoit un IDOC de fichier plat à partir d’un système SAP. Le projet BizTalk contient un désassembleur de fichier plat pour convertir le format de fichier plat IDOC XML, afin qu’il peut être utilisé dans une orchestration. Avant l’IDOC XML est copié vers un emplacement de fichier via un port de fichier, il est converti en un IDOC de fichier plat à l’aide d’un assembleur de fichier plat.  
  
-   **Schéma pour l’IDOC à envoyer au système SAP**. Ce didacticiel implique un projet BizTalk qui reçoit les IDOC ORDERS03 à partir du système SAP. Le schéma généré pour l’IDOC est ORDERS03.xsd. Ce schéma est généré à l’aide de l’adaptateur SAP vPrev.  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>Comment migrer un projet BizTalk créée à l’aide de la Version précédente de l’adaptateur  
 L’objectif de ce didacticiel de migration est pour vous permettre de recevoir un IDOC de fichier plat à partir d’un système SAP à l’aide d’un port d’envoi WCF-Custom à la place le port d’envoi pour l’adaptateur SAP vPrev. Avant la présentation des paramètres qui sont nécessaires pour le port d’envoi WCF-Custom, vous devez d’abord comprendre quels ports physiques sont requis pour l’orchestration de IDOC vPrev envoi.  
  
-   Une SAP vPrev port de réception qui reçoit un IDOC de fichier plat à partir d’un système SAP. Le port convertit également en un IDOC XML à l’aide d’un désassembleur de fichier plat, qui est disponible dans le cadre de l’application BizTalk vPrev. L’IDOC XML conforme au schéma (ORDERS03.xsd) que vous avez généré à l’aide de l’adaptateur SAP vPrev.  
  
-   Un port d’envoi file qui copie l’IDOC au dossier. Ce port utilise également le pipeline assembleur de fichier plat, disponible dans l’application BizTalk, pour convertir l’IDOC XML en un IDOC de fichier plat.  
  
 Pour migrer votre projet BizTalk de vPrev existant, vous n’avez pas besoin modifier le port d’envoi file qui copie l’IDOC de fichier plat dans un dossier. Vous devez uniquement configurer un nouveau port avec les paramètres de configuration à droite de réception WCF-Custom. Ce didacticiel montre comment configurer WCF-Custom port de réception pour recevoir des IDOC à partir d’un système SAP à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Étape 1 : Créer et déployer le projet BizTalk vPrev pour la réception d’un IDOC](../../adapters-and-accelerators/adapter-sap/step-1-build-and-deploy-the-vprev-biztalk-project-for-receiving-an-idoc.md)  
  
-   [Étape 2 : Configurer un WCF-Custom unidirectionnel Port de réception](../../adapters-and-accelerators/adapter-sap/step-2-configure-a-wcf-custom-one-way-receive-port.md)  
  
-   [Étape 3 : Tester l’Application migrée](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application5.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)