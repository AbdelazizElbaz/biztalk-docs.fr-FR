---
title: "Opérations sur les tables et vues avec des types définis par l’utilisateur à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4006bbe-91ca-4cd9-844d-5ed63142001f
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b09cc02f8f43b589da821924cfdd38bec52160e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter"></a>Opérations sur les tables et vues avec des types définis par l’utilisateur à l’aide de l’adaptateur SQL
Vous pouvez utiliser la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour effectuer des opérations sur des tables ou vues qui possèdent des colonnes de types définis par l’utilisateur (UDT). Vous pouvez utiliser les opérations de table standard (Insert, Update, Delete et Select) pour lire ou écrire des données dans des colonnes sur des types UDT. Vous pouvez également exécuter des fonctions et procédures stockées sur ces tables. Toutefois, vous devez effectuer certaines tâches avant de pouvoir utiliser l’adaptateur de fonctionner sur des tables avec colonnes UDT. Une fois que vous avez effectué ces tâches, vous pouvez utiliser l’adaptateur pour :  
  
-   Exécuter Insert, Delete, Update et opérations de sélection, comme décrit dans [Insert, update, delete ou des opérations select à l’aide de BizTalk Server avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/insert-update-delete-or-select-using-the-sql-adapter-in-biztalk-server.md).  
  
-   Exécuter des procédures stockées, comme décrit dans [exécuter des procédures stockées dans SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-biztalk-server.md).  
  
-   Effectuer des opérations composites sur des tables avec colonnes UDT, comme décrit dans [exécuter des opérations composites sur SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/run-composite-operations-on-sql-server-using-biztalk-server.md)  
  
-   Interroger des tables avec des colonnes UDT, comme décrit dans [Messages basés sur la réception d’interrogation de données modifiées à partir de SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-biztalk.md).  
  
-   Effectuer d’autres opérations, comme décrit dans [développer vos applications BizTalk](../../core/develop-your-biztalk-applications.md).  
  
## <a name="considerations-while-performing-operations-on-tables-with-udts"></a>Considérations lors de l’exécution d’opérations sur les Tables avec UDT  
 Vous devez effectuer les tâches suivantes avant de pouvoir utiliser l’adaptateur pour effectuer des opérations sur les tables avec des colonnes UDT.  
  
-   **Lors de la génération de schéma pour l’opération à l’aide[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]**  
  
    |Type UDT|Emplacement des assemblys|  
    |--------------|----------------------------|  
    |Les UDT livré avec SQL Server, par exemple, Geography|-Vérifiez que Microsoft.SqlServer.Types.dll est ajouté au GAC.<br />-Vérifiez les SqlServerSpatial.dll vraiment est disponible dans le dossier System32.<br /><br /> Vous pouvez installer ces DLL sur l’ordinateur en exécutant le programme d’installation de SQL Server et en sélectionnant **outils de gestion – de base** et **outils de gestion – complet** dans la **sélection des fonctionnalités**page de l’Assistant.|  
    |UDT définis par les utilisateurs, mais ne pas livré avec SQL Server|Assurez-vous que les assemblys respectives pour les UDT sont disponibles au même emplacement que le [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] exécutable, devenv.exe. Le fichier exécutable est généralement disponible dans `<installation drive>:\Program Files\Microsoft Visual Studio <version>\Common7\IDE`.|  
  
-   **Lors de l’exécution de l’opération en utilisant[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]**  
  
    |Type UDT|Emplacement des assemblys|  
    |--------------|----------------------------|  
    |Les UDT livré avec SQL Server, par exemple, Geography|-Vérifiez que Microsoft.SqlServer.Types.dll est ajouté au GAC.<br />-Vérifiez les SqlServerSpatial.dll vraiment est disponible dans le dossier System32.<br /><br /> Vous pouvez installer ces DLL sur l’ordinateur en exécutant le programme d’installation de SQL Server et en sélectionnant **outils de gestion – de base** et **outils de gestion – complet** dans la **sélection des fonctionnalités**page de l’Assistant.|  
    |UDT définis par les utilisateurs, mais ne pas livré avec SQL Server|Assurez-vous que les assemblys respectives pour les UDT sont disponibles sous le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] emplacement d’installation. Pour [!INCLUDE[prague](../../includes/prague-md.md)], il s’agit généralement \<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].|  
  
-   **Lors de l’exécution de l’opération en utilisant[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]**  
  
    |Type UDT|Emplacement des assemblys|  
    |--------------|----------------------------|  
    |Les UDT livré avec SQL Server, par exemple, Geography|-Vérifiez que Microsoft.SqlServer.Types.dll est ajouté au GAC.<br />-Vérifiez les SqlServerSpatial.dll vraiment est disponible dans le dossier System32.<br /><br /> Vous pouvez installer ces DLL sur l’ordinateur en exécutant le programme d’installation de SQL Server et en sélectionnant **outils de gestion – de base** et **outils de gestion – complet** dans la **sélection des fonctionnalités**page de l’Assistant.|  
    |UDT définis par les utilisateurs, mais ne pas livré avec SQL Server|Assurez-vous que les assemblys respectives pour les UDT sont disponibles au même emplacement que le fichier exécutable projet, qui est généralement dans le dossier \bin\Debug du projet.|  
  
 Une fois que vous avez effectué ces tâches, vous sont définis pour effectuer des opérations sur des tables avec UDT.  
  
## <a name="see-also"></a>Voir aussi  
 [Se connecter à un système SAP à l’aide de l’adaptateur](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)