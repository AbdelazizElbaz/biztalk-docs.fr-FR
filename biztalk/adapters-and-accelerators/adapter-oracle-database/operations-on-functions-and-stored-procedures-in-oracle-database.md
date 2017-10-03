---
title: "Opérations sur les fonctions et procédures stockées dans la base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- REF CURSOR
- packaged functions and procedures
- operations, on functions and stored procedures
- stored procedure
- RECORD type
- overloaded functions and procedures
ms.assetid: 18072b58-65b2-4da5-9433-ea0da4e2d4f4
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78181aae7921cad3996e4bd408e604857a2bd15e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-functions-and-stored-procedures-in-oracle-database"></a>Opérations sur les fonctions et procédures stockées dans la base de données Oracle
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] prend en charge des fonctions, des procédures et des packages Oracle dans la manière suivante :  
  
-   **Fonctions** sont signalées en tant qu’opérations. Le nom de l’opération est le nom de la fonction d’Oracle. IN, OUT et dans les paramètres sont pris en charge, ainsient, les valeurs de retour.  
  
-   **Procédures** sont signalées en tant qu’opérations. Le nom de l’opération est le nom de la procédure d’Oracle. IN, OUT et dans les paramètres sont pris en charge.  
  
-   **Empaqueté des fonctions et procédures** sont signalées en tant qu’opérations. Le nom et l’espace de noms de l’opération (fonction ou procédure) est qualifié par le nom du package Oracle. Surcharges sont prises en charge dans les packages (voir ci-après).  
  
-   **Surcharge des fonctions et procédures** dans les packages sont signalées en tant qu’opérations. Chaque fonction surchargée ou apparaît avec une chaîne ajoutée à son nom qui identifie la surcharge de procédure. Cette chaîne est la partie de la séquence « overload1 », « overload2 », « overload3 » et ainsi de suite.  
  
-   **Types de REF CURSOR** sont pris en charge pour IN, OUT et dans les paramètres des procédures et des fonctions, ainsi que pour la fonction valeurs de retour. Pour plus d’informations, consultez [opérations sur les fonctions et procédures avec des paramètres REF CURSOR](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-ref-cursor-parameters1.md).  
  
-   **Types d’enregistrements** sont pris en charge pour IN, OUT et dans les paramètres des procédures et des fonctions, ainsi que pour la fonction valeurs de retour. Types d’enregistrements (imbriquées) à la fois simples et complexes sont pris en charge. [Opérations sur les fonctions et procédures avec des Types d’enregistrements](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-record-types1.md)  
  
 Pour plus d’informations sur :  
  
-   Appeler une procédure Oracle ou une fonction à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [appeler les fonctions et les procédures de base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-biztalk-server.md) et [appeler les fonctions de surcharge et les procédures de base de données Oracle à l’aide BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-overloaded-functions-and-procedures-in-oracle-database-using-biztalk-server.md).  
  
-   Appeler une procédure Oracle ou une fonction en utilisant le modèle de service WCF, consultez [appeler les fonctions et les procédures de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).  
  
-   Appeler une procédure Oracle ou une fonction en utilisant le modèle de canal WCF, consultez [appeler une fonction dans la base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/invoke-a-function-in-oracle-database-using-the-wcf-channel-model.md).  
  
-   Message de structure et les actions de SOAP utilisées pour appeler des fonctions et procédures d’Oracle, consultez [des schémas de Message pour les fonctions et procédures](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-functions-and-procedures.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)