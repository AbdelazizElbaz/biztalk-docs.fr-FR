---
title: "Métadonnées et le modèle de Service WCF avec l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4353ce67-f0e8-4f96-b1d9-95deeee7f3e6
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c95ed3188c01f0f6d568bd745decd9e601e6ee3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="metadata-and-the-wcf-service-model-with-the-sql-adapter"></a>Métadonnées et le modèle de Service WCF avec l’adaptateur SQL
Dans le modèle de service WCF, vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutile.exe) pour effectuer les opérations suivantes :  
  
-   Générer un contrat de service, le contrat de service WCF, via laquelle votre code peut recevoir des opérations à partir de l’adaptateur. Cette interface .NET représente le contrat de service pour les opérations de la cible.  
  
-   Générer des classes proxy, la classe de client WCF, via laquelle votre code peut appeler des opérations sur la carte.  
  
-   Classes annotés qui représentent la prise en charge des contrats de message, les contrats d’opération et les contrats de données pour le contrat de service.  
  
 Pour mieux comprendre la structure de ce code généré, consultez [compréhension du Code Client généré](https://msdn.microsoft.com/library/ms733881.aspx). Cette rubrique décrit en particulier le code que svcutil.exe génère, mais son contenu est également applicable au code qui le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère.  
  
 Pour plus d’informations sur la façon de générer une classe de client WCF ou un contrat de service WCF pour les opérations de la cible et sur les différences entre svcutil.exe et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server ](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications SQL à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)