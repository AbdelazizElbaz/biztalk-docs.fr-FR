---
title: "Didacticiel 3 : Migrer un SAP envoyer l’IDOC BizTalk projet | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- migrating, SAP Send IDOC BizTalk project
- migration
ms.assetid: c0a11432-5388-4054-8996-08a957cc02eb
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52f8bc638d1adefe952ce055542706d11e0ca61f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-3-migrating-an-sap-send-idoc-biztalk-project"></a>Didacticiel 3 : Migration d’un projet BizTalk SAP envoi IDOC
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
 Ce didacticiel est basé sur un exemple qui montre comment migrer un projet BizTalk vPrev qui envoie un IDOC à un système SAP (SendIDOC_Migration). L’exemple est fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Vous devez disposer d’un projet BizTalk de vPrev. Ce didacticiel implique un projet BizTalk qui envoie un IDOC BOMDOC à un système SAP.  
  
-   Vous devez disposer d’un format de fichier plat BOMDOC IDOC pour envoyer au système SAP à l’aide de l’adaptateur SAP vPrev. L’exemple fourni pour ce didacticiel contient cet IDOC de fichier plat.  
  
-   [Créer le fichier de clé de nom fort et découvrez les outils](../../adapters-and-accelerators/adapter-sap/prerequisites-to-create-sap-applications.md)
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>Présentation d’un projet BizTalk créée à l’aide de la Version précédente de l’adaptateur  
 Les principaux composants d’un projet BizTalk de vPrev pour envoyer un IDOC sont :  
  
-   **Orchestration BizTalk**. Il s’agit d’une orchestration simple qui sélectionne un IDOC de fichier plat à partir d’un emplacement de fichier et envoie le port d’envoi l’IDOC au système SAP à l’aide d’un SAP. Le projet BizTalk contient un désassembleur de fichier plat pour convertir le format de fichier plat IDOC XML, afin qu’il peut être utilisé dans une orchestration. Avant l’IDOC XML est consommé par le port d’envoi de SAP de vPrev, il est converti en un IDOC de fichier plat à l’aide d’un assembleur de fichier plat.  
  
-   **Schéma pour l’IDOC à envoyer au système SAP**. Pour ce didacticiel, vous prenez un projet BizTalk qui envoie BOMDOC01 IDOC au système SAP. Le schéma généré pour l’IDOC est BOMDOC01.xsd. Ce schéma est généré à l’aide de l’adaptateur SAP vPrev.  
  
-   **Le format de fichier plat IDOC**. Il s’agit de l’IDOC de fichier plat envoyé au système SAP.  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>Comment migrer un projet BizTalk créée à l’aide de la Version précédente de l’adaptateur  
 L’objectif de ce didacticiel de migration est pour vous permettre d’envoyer un IDOC de fichier plat à un système SAP à l’aide d’un port d’envoi WCF-Custom à la place le port d’envoi pour l’adaptateur SAP vPrev. Avant la présentation des paramètres qui sont nécessaires pour le port d’envoi WCF-Custom, vous devez d’abord comprendre quels ports physiques sont requis pour l’orchestration de IDOC vPrev envoi :  
  
-   Un fichier de port de réception qui Récupère l’IDOC de fichier plat. Ce port utilise le pipeline désassembleur de fichier plat, disponible dans l’application BizTalk, pour convertir le format de fichier plat dans un document XML conforme au schéma (BOMDOC01.xsd) généré à l’aide de l’adaptateur SAP vPrev.  
  
-   Une SAP vPrev port d’envoi qui envoie l’IDOC de fichier plat au système SAP. Avant d’envoyer le format de fichier plat, le port utilise l’assembleur de fichier plat pour convertir l’IDOC XML en un IDOC de fichier plat.  
  
 Pour migrer votre projet BizTalk de vPrev existant, vous n’avez pas besoin de modifier le fichier port de réception qui Récupère l’IDOC de fichier plat et convertit l’IDOC de fichier plat au format XML à l’aide d’un désassembleur de fichier plat. Vous devez uniquement configurer un port d’envoi WCF-Custom avec les paramètres de configuration de droite. Ce didacticiel montre comment configurer le port d’envoi WCF-Custom pour envoyer des IDOC à un système SAP à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Étape 1 : Créer et déployer le projet BizTalk vPrev pour envoyer un IDOC](../../adapters-and-accelerators/adapter-sap/step-1-build-and-deploy-the-vprev-biztalk-project-for-sending-an-idoc.md)  
  
-   [Étape 2 : Configurer un Port d’envoi unidirectionnel WCF-Custom](../../adapters-and-accelerators/adapter-sap/step-2-configure-a-wcf-custom-one-way-send-port.md)  
  
-   [Étape 3 : Tester l’Application migrée](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application2.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)