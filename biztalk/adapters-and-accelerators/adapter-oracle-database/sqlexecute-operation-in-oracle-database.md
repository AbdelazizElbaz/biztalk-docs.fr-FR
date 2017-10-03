---
title: "Opération SQLEXECUTE dans la base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DML
- data manipulation language
- operations, DML
- SQLEXECUTE
ms.assetid: d7f881e4-c668-4f8e-b08a-ea6614b65910
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ac8d5c8284e1f273d4b9aef17e79e25636dc581
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sqlexecute-operation-in-oracle-database"></a>Opération SQLEXECUTE dans la base de données Oracle
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] expose un ensemble standard d’opérations sur les objets de base de données Oracle. À l’aide de ces opérations, vous pouvez effectuer les opérations appel une fonction Oracle ou une procédure ou effectuer base SQL opérations data manipulation language (DML) sur les tables. Toutefois, il peuvent y avoir scénarios pilotés par votre logique métier, vous devez effectuer les opérations qui les [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] n’a pas été affiché. Par exemple, vous souhaiterez :  
  
-   Effectuer une opération sur les artefacts de base de données qui ne sont pas signalées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; par exemple, obtenir le CURVAL ou NEXTVAL d’une séquence Oracle.  
  
-   Effectuer des opérations de langage de définition de données ; par exemple, créer une table.  
  
-   Effectuer des opérations sur un objet de base de données qui n’était pas présente au moment du design ; par exemple, mettre à jour des enregistrements dans une table temporaire qui est créé par votre logique métier.  
  
-   Effectuer des opérations DML plus complexes sur les tables que les opérations qui les [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces ; par exemple, pour exécuter une requête qui inclut une clause JOIN.  
  
 Pour ces types de scénarios, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] met en évidence l’opération SQLEXECUTE. L’opération SQLEXECUTE apparaît sous le nœud racine (/) dans le **sélectionner une catégorie** volet dans le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] et [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].  
  
 À l’aide de l’opération SQLEXECUTE, vous pouvez effectuer une instruction SQL paramétrable sur la base de données Oracle. L’opération SQLEXECUTE prend en charge un bloc de paramètre d’entrée comprenant des jeux de paramètres qui vous permettent d’exécuter la même instruction SQL une fois pour chaque jeu. L’opération SQLEXECUTE renvoie les résultats de l’instruction SQL dans un jeu d’enregistrements générique.  
  
> [!NOTE]
>  Vous pouvez passer dans et dans les paramètres pour les procédures, fonctions et des packages dans l’opération SQLEXECUTE. L’artefact appelée s’exécute avec les paramètres fournis sur la base de données Oracle ; Toutefois, l’opération SQLEXECUTE ne retourne pas la valeur de sortie et dans les paramètres pour le client. Si vous souhaitez appeler des procédures, fonctions ou des packages, nous vous recommandons de faire en appelant les opérations dédiées qui le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose pour que ces artefacts Oracle.  
  
 Pour plus d’informations sur :  
  
-   Une opération SQLEXECUTE à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [l’opération SQLEXECUTE exécuter par à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-biztalk-server.md).  
  
-   Une opération SQLEXECUTE en utilisant le modèle de service WCF, consultez [l’opération en utilisant le modèle de Service WCF SQLEXECUTE exécuter](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md).  
  
-   L’opération SQLEXECUTE en utilisant le modèle de canal WCF, consultez [l’opération en utilisant le modèle de canal WCF SQLEXECUTE exécuter](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md).  
  
-   Structure et les actions SOAP pour effectuer une opération SQLEXECUTE des messages, consultez [des schémas de Message pour l’opération SQLEXECUTE](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)