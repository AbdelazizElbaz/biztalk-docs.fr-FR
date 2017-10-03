---
title: "Modèle avec Siebel du Service WCF et les métadonnées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, metadata
- metadata, and the WCF service model
ms.assetid: 3aca1835-fb9e-4841-a920-078da0b3fe76
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed348c2ab183960b7af1383768259f67c4ca6270
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="metadata-and-the-wcf-service-model-with-siebel"></a>Métadonnées et le modèle de Service WCF avec Siebel
Dans le modèle de service WCF, vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutile.exe) pour générer une classe proxy, la classe de client WCF, via laquelle votre code peut appeler des opérations sur le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].  
  
 Ces outils permet de générer les métadonnées exposées par l’adaptateur :  
  
-   Une interface .NET annotée qui représente le contrat de service pour les opérations de la cible. Cette interface est appelée le contrat de service WCF.  
  
-   Classes annotés qui représentent la prise en charge des contrats de message, les contrats d’opération et les contrats de données pour le contrat de service.  
  
-   Une classe de client WCF dont les méthodes peuvent être utilisées pour appeler les méthodes de service (opérations) exposées par le contrat de service WCF.  
  
 Pour mieux comprendre la structure de ce généré de code, consultez « Description du Code Client généré » à [http://go.microsoft.com/fwlink/?LinkId=98365](http://go.microsoft.com/fwlink/?LinkId=98365). Cette rubrique décrit en particulier le code que svcutil.exe génère, mais son contenu est également applicable au code qui le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère.  
  
 Pour plus d’informations sur la façon de générer une classe de client WCF pour les opérations de la cible et sur les différences entre svcutil.exe et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [générer un Client WCF ou un contrat de service WCF pour Siebel solution artefacts](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des applications Siebel à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)