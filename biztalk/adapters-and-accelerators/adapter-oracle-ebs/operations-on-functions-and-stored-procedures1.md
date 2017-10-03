---
title: "Opérations sur les fonctions et stockée Procedures1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e6bdaa7-ed3c-43bc-bed5-70fe43f9c2d1
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfe5f705c8e432c920c8fae41a2b2f050c188047
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-functions-and-stored-procedures"></a>Opérations sur les fonctions et procédures stockées
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] prend en charge des procédures et des fonctions d’Oracle.

## <a name="functions-and-procedures"></a>Fonctions et procédures

Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] prend en charge les fonctions d’Oracle et les procédures de la manière suivante :  
  
-   **Fonctions** sont signalées en tant qu’opérations. Le nom de l’opération est le nom de la fonction d’Oracle. IN, OUT et dans les paramètres sont pris en charge, ainsient, les valeurs de retour.  
  
    > [!IMPORTANT]
    >  Si vous passez un paramètre non valide dans une fonction (autrement dit, passez une valeur de chaîne pour un champ numérique), le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] peut lever une exception en fonction du comportement ODP.NET. C’est parce que le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] utilise ODP.NET pour communiquer avec Oracle E-Business Suite.  
  
-   **Procédures** sont signalées en tant qu’opérations. Le nom de l’opération est le nom de la procédure d’Oracle. IN, OUT et dans les paramètres sont pris en charge.  
  
    > [!IMPORTANT]
    >  Dans le cadre d’une procédure, si vous insérez ou mettez à jour une valeur décimale (par exemple, 15,2) dans un champ numérique d’une table de l’interface ou de la table de base de données, le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] lève une exception. C’est parce que le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] utilise ODP.NET pour communiquer avec Oracle E-Business Suite et ODP.NET ne prend pas en charge en acceptant les valeurs décimales pour les champs numériques.  
  
-   **Types de REF CURSOR** sont prises en charge dans et les paramètres des procédures et des fonctions, ainsi que pour la fonction de sortie des valeurs de retour. Pour plus d’informations, consultez [opérations sur les fonctions et procédures avec des paramètres REF CURSOR](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-ref-cursor-parameters1.md).  
  
-   **Types d’enregistrements** sont pris en charge pour IN, OUT et dans les paramètres des procédures et des fonctions, ainsi que pour la fonction valeurs de retour. Types d’enregistrements (imbriquées) à la fois simples et complexes sont pris en charge. [Opérations sur les fonctions et procédures avec des Types d’enregistrements](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-record-types1.md)  
  
> [!NOTE]
>  Vous pouvez également définir le contexte d’application pour les fonctions et procédures stockées dans [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Pour plus d’informations sur le contexte de l’application et comment le configurer, consultez [définir le contexte Application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)