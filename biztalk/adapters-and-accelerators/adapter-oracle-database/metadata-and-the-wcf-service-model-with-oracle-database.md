---
title: "Modèle de base de données Oracle de Service WCF et les métadonnées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service model, metadata
- WCF client class
- WCF service contract
ms.assetid: b55cf4ed-c41a-4986-bbaf-88e80c32b01f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76933dba64e6e8bb75eb0394ab8e6eedd3fb7116
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="metadata-and-the-wcf-service-model-with-oracle-database"></a>Métadonnées et le modèle de Service WCF avec la base de données Oracle
Dans le modèle de service WCF, vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]ou le ServiceModel Metadata Utility Tool (svcutile.exe) pour générer des classes proxy via lequel votre code peut :  
  
-   Appeler des opérations sur la carte (une classe de client WCF)  
  
-   Opérations de réception de l’adaptateur (un contrat de service WCF)  
  
 Ces outils génèrent des classes .NET qui représentent un contrat de service pour les opérations de la cible (ainsi que la prise en charge des contrats de message, contrats d’opération et des contrats de données) à partir des métadonnées exposées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Pour mieux comprendre la structure de ce généré de code, consultez « Description du Code Client généré » à [http://go.microsoft.com/fwlink/?LinkId=98365](http://go.microsoft.com/fwlink/?LinkId=98365). Cette rubrique décrit en particulier le code que svcutil.exe génère, mais son contenu est également applicable au code qui le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère. Pour plus d’informations sur la façon de générer une classe de client WCF ou un contrat de service WCF pour les opérations de la cible et sur les différences entre svcutil.exe et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [générer un Client WCF ou un contrat de Service WCF de base de données Oracle Artefacts de solution](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des Applications de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)