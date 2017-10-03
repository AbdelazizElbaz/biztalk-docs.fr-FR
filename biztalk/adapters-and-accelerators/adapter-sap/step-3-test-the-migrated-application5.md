---
title: "Étape 3 : Tester le Application5 migrés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- migration, testing the migrated application (Receive IDOC)
- migration
ms.assetid: 3ad15069-1556-4c0a-8bfd-86704d40c586
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b5e49968e4b0b463b1665d0752689a14039c2da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-test-the-migrated-application"></a>Étape 3 : Tester l’Application migrée
![Étape 3 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")  
  
 **Durée :** 5 minutes  
  
 **Objectif :** dans cette étape, vous allez tester l’application migrée en recevant un IDOC de fichier plat à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Configurer l’application BizTalk en mappant les ports logiques de l’orchestration BizTalk aux ports physiques dans la console Administration de BizTalk Server.  
  
-   Configurer BizTalk application afin d’utiliser WCF-Custom port de réception pour la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
### <a name="to-test-the-migrated-application"></a>Pour tester l’application migrée  
  
1.  Démarrer l’interface GUI SAP et se connecter au système SAP que vous avez spécifié dans l’URI de connexion.  
  
2.  Exécutez SE37 et appeler un module de fonction dans SAP qui envoie un IDOC à un système externe. Assurez-vous de qu'envoyer l’IDOC en utilisant le même ID de programme qui est spécifié dans l’URI de connexion pour le port de réception WCF-Custom.  
  
3.  Recherchez l’IDOC entrant à l’emplacement de fichier spécifié dans le cadre de l’orchestration.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 4 : Migration d’un SAP de réception projet BizTalk IDOC](../../adapters-and-accelerators/adapter-sap/tutorial-4-migrating-an-sap-receive-idoc-biztalk-project.md)