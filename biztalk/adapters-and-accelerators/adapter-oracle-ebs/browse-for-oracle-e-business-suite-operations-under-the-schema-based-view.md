---
title: "Rechercher des opérations Oracle E-Business Suite dans la vue de schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d004a99f-0db1-4cdb-80cd-ea71de4e1098
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b9dedc20103787f449cc8c5ac475ef2ed2e0f82
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="browse-for-oracle-e-business-suite-operations-under-the-schema-based-view"></a>Rechercher des opérations Oracle E-Business Suite dans la vue de schéma
Vous pouvez utiliser la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour parcourir les opérations entrantes et sortantes qui peuvent être effectuées sur Oracle E-Business Suite à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Cette rubrique fournit des informations sur la façon de rechercher des opérations sortantes et entrantes sous la vue de schéma.  
  
> [!NOTE]
>  Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] présentes essentiellement la même interface lors de la navigation et de la recherche pour les opérations, afin des deux composants sont traités dans les rubriques mêmes.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez vous connecter à Oracle E-Business Suite avant de pouvoir parcourir les métadonnées pour les opérations de la cible. Pour plus d’informations sur la façon de se connecter à Oracle de base de données lorsque vous utilisez la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [se connecter à Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md).  
  
## <a name="browsing-for-outbound-operations"></a>Navigation pour les opérations sortantes  
 Procédez comme suit pour parcourir les opérations sortantes sous la vue de schéma.  
  
#### <a name="to-browse-metadata-for-outbound-operations-under-the-schema-based-view"></a>Pour parcourir les métadonnées pour les opérations sortantes sous la vue de schéma  
  
1.  Se connecter à Oracle E-Business Suite à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Consultez [se connecter à Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** répertorier, pour les opérations sortantes sélectionnez **Client (Outbound operations)**.  
  
3.  Le **sélectionner une catégorie** zone répertorie les différentes vues sous lequel sont classés les artefacts d’Oracle E-Business Suite.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Le nœud racine (/) est sélectionné, et les nœuds de catégorie générale disponibles sous le nœud racine sont répertoriées dans le **catégories et opérations disponibles** boîte.  
  
     ![Opérations et catégories au niveau racine](../../adapters-and-accelerators/adapter-oracle-ebs/media/559a6652-2d9d-4ecd-a1bb-4f63750c9518.gif "559a6652-2d9d-4ecd-a1bb-4f63750c9518")  
  
    > [!NOTE]
    >  Les opérations standard telles que ExecuteReader, ExecuteScalar et ExecuteNonQuery sont disponibles au niveau racine. Pour plus d’informations sur ces opérations, consultez [prise en charge de ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md). Pour obtenir des instructions sur la façon d’exécuter ces opérations à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [ExecuteReader, ExecuteScalar ou opérations ExecuteNonQuery dans SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md).  
  
4.  Développez le **basée sur un schéma de vue** nœud pour afficher les schémas définis dans la base de données sous-jacente. Chaque schéma est catégorisée davantage en fonction des API PL-SQL, des procédures, fonctions, tables et vues qu’il contient.  
  
    > [!TIP]
    >  Vous pouvez directement accéder à la catégorie « exécution » ou plusieurs nœuds de sous-catégorie dans l’arborescence, en tapant le nom de l’artefact pendant que le focus est sur l’arborescence dans le **sélectionner une catégorie** boîte. Par exemple, pour accéder à la **SCOTT** schéma, conserver le focus sur le **basée sur un schéma de vue** nœud, puis tapez `SCOTT`.  
  
5.  Développez le **API PL-SQL** nœud pour afficher la liste des packages définis dans la base de données Oracle pour un schéma particulier. Cliquez sur un nom de package pour afficher les fonctions et les procédures définies dans ce package dans le **catégories et opérations disponibles** boîte.  
  
     ![Rechercher les packages dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-ebs/media/582a9bd7-beed-4b36-b465-f5c4ceb6e740.gif "582a9bd7-beed-4b36-b465-f5c4ceb6e740")  
  
6.  Cliquez sur le **procédures** nœud pour afficher la liste des procédures décrites dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir les procédures dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-ebs/media/7213154e-6a26-4fc3-b4ec-1658779f77d3.gif "7213154e-6a26-4fc3-b4ec-1658779f77d3")  
  
7.  Cliquez sur le **fonctions** nœud pour afficher la liste des fonctions dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir les fonctions dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-ebs/media/5df9b42c-9d8b-4c81-a0ae-ba5336445837.gif "5df9b42c-9d8b-4c81-a0ae-ba5336445837")  
  
8.  Développez le **Tables** nœud pour afficher la liste des tables pour un schéma particulier. Cliquez sur un nom de table pour afficher les opérations prises en charge sur la table dans le **catégories et opérations disponibles** boîte.  
  
     ![Rechercher les tables dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-ebs/media/94dd4642-1178-4d88-986b-f0ad409c414c.gif "94dd4642-1178-4d88-986b-f0ad409c414c")  
  
    > [!NOTE]
    >  Si une table contient des colonnes de type BLOB, CLOB, NCLOB ou BFILE l’adaptateur expose également une opération spécifique pour lire des données à partir de ces colonnes. Le nom de ces opérations sont Read_\<LOBColName\>. Par exemple, si la table possède une colonne, photos, de type BLOB, l’adaptateur expose un **Read_PHOTO** opération. Si une table possède plusieurs colonnes de type BLOB, CLOB, NCLOB et BFILE l’adaptateur expose nombre autant de Read_\<LOBColName\> operations.  
    >   
    >  De même, si une table contient des colonnes de type BLOB, CLOB ou NCLOB l’adaptateur expose également une opération spécifique pour mettre à jour des données dans ces colonnes. Le nom de ces opérations sont en attente_\<LOBColName\>. Par exemple, si la table possède une colonne, photos, de type BLOB, l’adaptateur expose un **Update_PHOTO** opération. Si une table possède plusieurs colonnes de type BLOB, CLOB et NCLOB l’adaptateur expose un nombre plus grand nombre d’en attente_\<LOBColName\> operations. Notez que l’opération de mise à jour n’est pas pris en charge sur les colonnes de type BFILE.  
  
9. Développez le **vues** nœud pour afficher la liste des vues pour un schéma particulier. Cliquez sur un nom de la vue pour voir les opérations prises en charge sur la vue dans le **catégories et opérations disponibles** boîte.  
  
     ![Rechercher les vues dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-ebs/media/e1893e48-065c-4642-b076-192758d103db.gif "e1893e48-065c-4642-b076-192758d103db")  
  
    > [!NOTE]
    >  Si une vue contient des colonnes de type BLOB, CLOB, NCLOB ou BFILE l’adaptateur expose également une opération spécifique pour lire des données à partir de ces colonnes. Le nom de ces opérations sont Read_\<LOBColName\>. Par exemple, si la vue a une colonne, la règle, de type BLOB, l’adaptateur expose un **Read_RULE** opération. Si une vue a plus d’une colonne de type BLOB, CLOB, NCLOB ou BFILE l’adaptateur exposera nombre autant de Read_\<LOBColName\> operations. Notez qu’en attente_\<LOBColName\> opérations ne sont pas prises en charge sur les vues.  
  
## <a name="browsing-for-inbound-operations"></a>Navigation pour les opérations entrantes  
 Procédez comme suit pour parcourir les opérations entrantes sous la vue de schéma.  
  
#### <a name="to-browse-metadata-for-inbound-operations-under-the-schema-based-view"></a>Pour parcourir les métadonnées pour les opérations entrantes sous la vue de schéma  
  
1.  Se connecter à Oracle E-Business Suite à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Consultez [se connecter à Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** répertorier, pour les opérations entrantes sélectionnez **Service (opérations entrantes)**.  
  
3.  Le **sélectionner une catégorie** zone répertorie les différentes vues sous lequel sont classés les artefacts d’Oracle E-Business Suite.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Le nœud racine (/) est sélectionné, et les nœuds de catégorie générale disponibles sous le nœud racine sont répertoriées dans le **catégories et opérations disponibles** boîte.  
  
     ![Opération entrante au niveau racine](../../adapters-and-accelerators/adapter-oracle-ebs/media/9f9f95f3-c6cc-415c-b534-d5f1ad1963d5.gif "9f9f95f3-c6cc-415c-b534-d5f1ad1963d5")  
  
     L’opération entrante, **Notification**, est également disponible au niveau racine.  
  
4.  Développez le **basée sur un schéma de vue** nœud pour afficher les schémas définis dans la base de données sous-jacente. Chaque schéma est catégorisée davantage en fonction des API PL-SQL, des procédures, fonctions, tables et vues qu’il contient.  
  
    > [!TIP]
    >  Vous pouvez directement accéder à la catégorie « exécution » ou plusieurs nœuds de sous-catégorie dans l’arborescence, en tapant le nom de l’artefact pendant que le focus est sur l’arborescence dans le **sélectionner une catégorie** boîte. Par exemple, pour accéder à la **SCOTT** schéma, conserver le focus sur le **basée sur un schéma de vue** nœud, puis tapez `SCOTT`.  
  
5.  Développez le **API PL-SQL** nœud pour afficher la liste des packages définis dans la base de données Oracle pour un schéma particulier. Cliquez sur un nom de package pour afficher les fonctions et les procédures définies dans ce package dans le **catégories et opérations disponibles** boîte. Des procédures et des fonctions répertoriées peuvent servir à interroger la base de données Oracle.  
  
     ![Rechercher les packages dans la base de données Oracle pour l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/media/ab45e4a3-1425-4b23-afc2-8aecef546802.gif "ab45e4a3-1425-4b23-afc2-8aecef546802")  
  
6.  Cliquez sur le **procédures** nœud pour afficher la liste des procédures dans **les opérations et catégories disponibles** boîte. Chacune des procédures répertoriées peut être utilisé pour interroger la base de données Oracle.  
  
     ![Parcourir les procédures dans la base de données Oracle pour l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/media/04538693-5abf-4162-82e9-4107b4088b56.gif "04538693-5abf-4162-82e9-4107b4088b56")  
  
7.  Cliquez sur le **fonctions** nœud pour afficher la liste des fonctions dans le **catégories et opérations disponibles** boîte. Chacune des fonctions répertoriées permettre servir à interroger la base de données Oracle.  
  
     ![Parcourir les fonctions dans la base de données Oracle pour l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/media/b3f4ea5b-d03f-4cb5-82b4-8fbf0a8af24b.gif "b3f4ea5b-d03f-4cb5-82b4-8fbf0a8af24b")  
  
8.  Développez le **Tables** nœud pour afficher la liste des tables pour un schéma particulier. Cliquez sur un nom de table pour afficher la **interrogation** entrants opération prise en charge sur la table dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir les tables dans la base de données Oracle pour l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/media/58e9315d-3194-4a01-a505-bd1514e9d7e3.gif "58e9315d-3194-4a01-a505-bd1514e9d7e3")  
  
9. Développez le **vues** nœud pour afficher la liste des vues pour un schéma particulier. Cliquez sur un nom d’affichage pour afficher le **interrogation** entrants opération prise en charge sur la vue dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir les vues dans la base de données Oracle pour l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/media/f1282f17-efbe-43e6-90fa-5676e04051e8.gif "f1282f17-efbe-43e6-90fa-5676e04051e8")  
  
## <a name="see-also"></a>Voir aussi  
 [Parcourir, rechercher et d’obtenir des métadonnées pour des opérations Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)