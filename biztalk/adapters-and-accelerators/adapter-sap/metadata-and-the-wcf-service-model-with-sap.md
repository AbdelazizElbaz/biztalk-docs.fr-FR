---
title: "Modèle avec SAP du Service WCF et les métadonnées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1900cf66-a0d0-46f4-896b-7f6de3b51875
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f06cd33c0776df70e5ff2554d355915908012abb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="metadata-and-the-wcf-service-model-with-sap"></a>Métadonnées et le modèle de Service WCF avec SAP
Dans le modèle de service WCF, vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]ou le ServiceModel Metadata Utility Tool (svcutile.exe) pour générer des classes proxy via lequel votre code peut :  
  
-   Appeler des opérations sur la carte (une classe de client WCF)  
  
-   Opérations de réception de l’adaptateur (un contrat de service WCF)  
  
 Ces outils génèrent des classes .NET qui représentent un contrat de service pour les opérations de la cible (ainsi que la prise en charge des contrats de message, contrats d’opération et des contrats de données) à partir des métadonnées exposées par le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]. Pour mieux comprendre la structure de ce code généré, consultez [compréhension du Code Client généré](https://msdn.microsoft.com/library/ms733881.aspx). Cette rubrique décrit en particulier le code que svcutil.exe génère, mais son contenu est également applicable au code qui le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère. Pour plus d’informations sur la façon de générer une classe de client WCF ou un contrat de service WCF (interface) pour les opérations de la cible et sur les différences entre svcutil.exe et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [générer un client WCF ou un contrat de service WCF pour SAP artefacts de solution](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)