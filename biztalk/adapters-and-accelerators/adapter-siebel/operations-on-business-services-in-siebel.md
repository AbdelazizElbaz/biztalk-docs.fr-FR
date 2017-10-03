---
title: "Opérations sur les Services métier Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- operations, on business services
- business services, operations on
ms.assetid: 29a1a88c-8c7b-46f1-8faf-49ddd32ba2f0
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1ffd133d76b1f8cae3f1732e48f817fe4fb26b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-business-services-in-siebel"></a>Opérations sur les Services métier de Siebel
Un service d’entreprise Siebel est une collection de méthodes d’entreprise qui peuvent être appelées directement dans Siebel. Alors que les composants d’entreprise et les objets métier sont associés à des données spécifiques et des tables dans Siebel, services professionnels appellent les objets pour effectuer des tâches spécifiques.  
  
 Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] met en évidence les méthodes de service métier comme opération noms et prend en charge des IN, OUT et INOUT paramètres. Par exemple, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces le **ATPRunCheck** méthode sous forme d’opération. Cette méthode appartient à la **ATP** service métier.  
  
 Certaines conditions qui le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] impose tout en utilisant les services d’entreprise Siebel :  
  
-   Si une méthode de service d’entreprise Siebel prend un argument qui n’a pas de type de données spécifié, l’adaptateur expose l’argument sous forme de texte.  
  
-   Un argument de méthode de service business Siebel permettre être des types suivants :  
  
    -   Chaîne (exposé comme xsd : String)  
  
    -   Nombre (exposées en tant que xsd : decimal)  
  
    -   Date (exposé comme xsd : DateTime, avec la facette de modèle indiquant que la partie heure doit être défini à 00:00:00)  
  
    -   Hiérarchie (exposé comme xsd : String)  
  
    -   Objet d’intégration (exposé comme xsd : String)  
  
     En outre, la méthode de service business vérifie si la valeur passée pour un argument est compatible avec le type correspondant. Par conséquent, si une méthode de service d’entreprise accepte ou retourne des valeurs qui ne sont pas conformes avec le type d’argument correspondant, l’adaptateur peut lever une exception. Si l’adaptateur parvient à appeler la méthode de service d’entreprise, le schéma de validation peut échouer.  
  
 Pour plus d’informations sur :  
  
-   Exécution d’opérations sur les services d’entreprise à l’aide de BizTalk Server, consultez [appeler Business Service méthodes à l’aide de BizTalk Server et l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter.md).  
  
-   Structures et des actions SOAP pour effectuer des opérations sur les services, consultez des messages [des schémas de Message pour des opérations de Service Business](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-service-operations.md)).  
  
## <a name="see-also"></a>Voir aussi  
 [Se connecter à un système SAP à l’aide de l’adaptateur](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)