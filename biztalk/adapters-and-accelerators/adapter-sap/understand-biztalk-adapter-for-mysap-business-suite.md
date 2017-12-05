---
title: "Comprendre l’adaptateur BizTalk pour mySAP Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapter features
- adapters, features
- .NET Framework Data Provider for mySAP Business Suite
- Data Provider for SAP
- features of SAP adapter
- adapters, about SAP ADO Provider
ms.assetid: 136ca828-2724-454b-9d4d-a491d45e1eda
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5d04c435208e316c343ac7b307943e0f91b8af7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="understand-biztalk-adapter-for-mysap-business-suite"></a>Comprendre l’adaptateur BizTalk pour mySAP Business Suite
Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] permet un accès par programmation orientée service pour pouvoir interagir avec un système externe. Les cartes présentent les avantages suivants aux clients :  
  
-   **Expérience de conception cohérente**. Les adaptateurs fournissent une phase de conception commune et convivial pour parcourir, rechercher et récupérer les métadonnées des artefacts LOB.  
  
-   **Diverses options de programmation**. Les adaptateurs fournissent un choix de modèle, y compris le modèle de canal de Windows Communication Foundation (WCF), modèle de service WCF, ADO.NET, les services web ou BizTalk pris en charge les modèles de programmation.  
  
-   **Uniforme d’expérience sur LOB**. Les adaptateurs de normaliser l’utilisation de WCF et [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] et donc fournir une expérience uniforme d’accéder à n’importe quel système LOB.  
  
 Comme indiqué, les adaptateurs sont générés sur le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]. Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] fournit une base commune pour la création d’adaptateurs d’intégration qui consommable une variété d’applications clientes telles que BizTalk Server et Microsoft Office. Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] aligne la stratégie de carte avec la stratégie de Services Microsoft en exposant des adaptateurs d’intégration en tant que les canaux de Windows Communication Foundation (WCF). Pour plus d’informations sur la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], consultez la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation. La documentation est installée avec le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], généralement sous \<lecteur d’installation\>: \Program Files\\[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]\Documents.  
  
 Pour effectuer des opérations sur un système SAP, les clients de l’adaptateur doivent avoir accès aux appels de fonction distants pertinentes (RFC), Business Application Programming Interface (BAPI) et IDOC (ou documents intermédiaires). Un système SAP r/3 expose IDOC, BAPI et RFC pour l’intégration de l’entreprise. RFC sont des modules de fonction distante qui implémentent la logique métier spécifique. Cette logique peut être appelée à partir d’une application externe, telles que BizTalk Server ou une application .NET. Interfaces BAPI sont des interfaces de méthode à des objets métier SAP, qui à son tour exposés par le biais des interfaces RFC standard. IDOC sont un mécanisme d’abstraire la couche de communication electronic data Interchange (EDI) d’échange pour la communication entre SAP et les systèmes non-SAP. Avec [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)], vous pouvez accéder aux RFC, BAPI, et IDOC exposées par un système SAP.  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] inclut également [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)], qui fournit une interface ADO au système SAP.  
  
 Cette section répertorie les fonctionnalités pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] et [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Présentation de l’architecture de l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md)  
  
-   [Fonctionnalités clés de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/key-features-in-the-sap-adapter.md)  
  
-   [Limitations de l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/limitations-of-biztalk-adapter-for-mysap-business-suite.md)  
  
-   [À propos du fournisseur de données .NET Framework pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)  
  
## <a name="see-also"></a>Voir aussi  
[Prise en main l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/get-started-with-the-biztalk-adapter-for-mysap-business-suite.md)