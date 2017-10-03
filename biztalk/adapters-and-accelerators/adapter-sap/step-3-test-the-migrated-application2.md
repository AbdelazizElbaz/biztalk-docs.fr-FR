---
title: "Étape 3 : Tester l’Application2 migrés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- migration, testing the migrated application (Send IDOC)
- migration
ms.assetid: 8dc0d127-71ce-4668-a3bf-c893a8f6848d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6dbf6154337dc9daf5dcfe75b3f5b7299ae843ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-test-the-migrated-application"></a>Étape 3 : Tester l’Application migrée
![Étape 3 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")  
  
 **Durée :** 5 minutes  
  
 **Objectif :** dans cette étape, vous allez tester l’application migrée en envoyant un IDOC de fichier plat à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Configurer l’application BizTalk en mappant les ports logiques de l’orchestration BizTalk aux ports physiques dans la console Administration de BizTalk Server.  
  
-   Configurer l’application BizTalk à utiliser le port d’envoi WCF-custom pour la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
### <a name="to-test-the-migrated-application"></a>Pour tester l’application migrée  
  
1.  Dans le dossier SendIDOC_Migration, copiez le fichier BOMDOC.txt. Il s’agit de l’IDOC de fichier plat à envoyer au système SAP.  
  
2.  Emplacement de réception de coller l’IDOC de fichier plat dans le dossier qui est mappé au fichier.  
  
3.  L’orchestration utilise le fichier et envoie l’IDOC au système SAP. Vérifiez s’il existe des erreurs dans l’Observateur d’événements.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 3 : Migration d’un projet BizTalk SAP envoi IDOC](../../adapters-and-accelerators/adapter-sap/tutorial-3-migrating-an-sap-send-idoc-biztalk-project.md)