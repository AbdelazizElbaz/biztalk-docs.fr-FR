---
title: "Validation d’exécution pour le moteur d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating, assemblies
- orchestrations, validating
- validating, orchestration engine
- schemas, validating
- correlations, validating
- validating, schemas
- orchestration engine, runtime validation
- assemblies, validating
- validating, correlations
- validating, orchestrations
- validating
ms.assetid: f6085889-05d6-4eba-a528-9d034c4e4225
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e53adb5aa42c7dfe23df50707754bde200ea838a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="runtime-validation-for-the-orchestration-engine"></a>Validation d'exécution pour le moteur d'orchestration
Vous pouvez configurer le moteur d'orchestration de sorte qu'il effectue plusieurs validations d'exécution qui pourront vous aider à tester votre orchestration et à diagnostiquer les éventuelles erreurs de configuration ou de données.  
  
 Vous pouvez définir des indicateurs dans BTSNTSvc.exe.config, un fichier de configuration que vous pouvez créer ou modifier dans le même répertoire que BTSNTSvc.exe (normalement dans le répertoire de déploiement BizTalk). Vous pouvez définir les indicateurs suivants dans le fichier BTSNTSvc.exe.config :  
  
-   Si vous définissez la **ValidateAssemblies** indicateur `True`, le moteur ne tente de charger tous les assemblys référencés par des assemblys immédiatement dépendants d’une orchestration et lors de la défaillance lève Erreur Microsoft.XLANGs.Core.AssemblyValidationException.  
  
-   Si vous définissez la **ValidateSchemas** indicateur `True`, le moteur utilise System.Xml.XmlValidatingReader pour valider chaque schéma représentant un type de partie de message et en cas d’échec, lève System.Xml.XmlException.  
  
-   Si vous définissez la **ValidateCorrelations** indicateur `True`, le moteur vérifie que dans un convoi parallèle tous les messages qui correspondent à un du convoi reçoit ont les mêmes valeurs de propriété de corrélation et en cas d’échec, lève Erreur Microsoft.XLANGs.Core.CorrelationValidationException.  
  
-   Si vous définissez la **ExtendedLogging** indicateur `True`, le moteur affiche les propriétés promues dans les informations pour Microsoft.XLANGs.BaseTypes.PublishMessageException pour le message d’échec de la publication.  
  
 Si vous souhaitez désactiver une validation, supprimez entièrement l'indicateur du fichier de configuration. Si toutes les validations sont activées, le moteur validera des assemblys, des schémas et une corrélation. Pour plus d’informations et des exemples de BTSNTSvc.exe.config, consultez [Configuration du moteur d’Orchestration](../core/orchestration-engine-configuration.md).  
  
## <a name="validate-assemblies"></a>Validation d'assemblys  
 Le moteur d'orchestration vérifie que tous les assemblys référencés par l'orchestration sont disponibles. Pour que la validation réussisse, tous les assembly référencés doivent se trouver dans le Global Assembly Cache (GAC) lorsque la première instance de l'orchestration est activée. Si la validation échoue, une erreur est consignée dans le journal de l'application et l'orchestration est suspendue.  
  
## <a name="validate-schemas"></a>Validation de schémas  
 À chaque fois qu'une partie XSD est attribuée, le moteur d'orchestration valide ses données en fonction de son schéma. Si la validation échoue, une erreur est consignée dans le journal de l'application et une exception est levée.  
  
## <a name="validate-correlation"></a>Validation d'une corrélation  
 Le moteur d'orchestration confirmera que les valeurs de propriété spécifiées pour être corrélées avec une instance donnée d'une orchestration sont reflétées dans tous les messages envoyés à partir de cette instance d'orchestration. Si **validateCorrelation** n’est pas défini, le moteur supposera que le message envoyé contient les valeurs de corrélation correctes et aucune vérification ne sera effectuée.  
  
 Si une validation de corrélation échoue, le moteur enregistre une erreur dans le journal des applications et lever une exception de type **CorrelationValidationException**.  
  
 Par défaut, **validateCorrelation** n’est pas définie.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage des Orchestrations](../core/debugging-orchestrations.md)   
 [Configuration du moteur d’orchestration](../core/orchestration-engine-configuration.md)