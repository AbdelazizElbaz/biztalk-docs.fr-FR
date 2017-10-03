---
title: "Rechercher des opérations Oracle E-Business Suite dans la vue basée sur un artefact | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 962ac1cc-826c-46d6-848a-4cd371804596
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3757514839e29d1d9748ffdcf56e7cc97ea075b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="browse-for-oracle-e-business-suite-operations-under-the-artifact-based-view"></a>Rechercher des opérations Oracle E-Business Suite dans la vue basée sur un artefact
Vous pouvez utiliser la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour parcourir les opérations entrantes et sortantes qui peuvent être effectuées sur Oracle E-Business Suite à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Cette rubrique fournit des informations sur la façon de rechercher des opérations sortantes et entrantes sous la vue basée sur l’artefact.  
  
> [!NOTE]
>  Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] présentes essentiellement la même interface lors de la navigation et de la recherche pour les opérations, afin des deux composants sont traités dans les rubriques mêmes.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez vous connecter à Oracle E-Business Suite avant de pouvoir parcourir les métadonnées pour les opérations de la cible. Pour plus d’informations sur la façon de se connecter à Oracle de base de données lorsque vous utilisez la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [se connecter à Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md).  
  
## <a name="browsing-for-outbound-operations"></a>Navigation pour les opérations sortantes  
 Procédez comme suit pour parcourir les opérations sortantes sous la vue basée sur l’artefact.  
  
#### <a name="to-browse-metadata-for-outbound-operations-under-the-artifact-based-view"></a>Pour parcourir les métadonnées pour les opérations sortantes sous la vue basée sur un artefact  
  
1.  Se connecter à Oracle E-Business Suite à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Consultez [se connecter à Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** répertorier, pour les opérations sortantes sélectionnez **Client (Outbound operations)**.  
  
3.  Le **sélectionner une catégorie** zone répertorie les différentes vues sous lequel sont classés les artefacts d’Oracle E-Business Suite.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Le nœud racine (/) est sélectionné, et les nœuds de catégorie générale disponibles sous le nœud racine sont répertoriées dans le **catégories et opérations disponibles** boîte.  
  
     ![Opérations et catégories au niveau racine](../../adapters-and-accelerators/adapter-oracle-ebs/media/559a6652-2d9d-4ecd-a1bb-4f63750c9518.gif "559a6652-2d9d-4ecd-a1bb-4f63750c9518")  
  
    > [!NOTE]
    >  Les opérations standard telles que ExecuteReader, ExecuteScalar et ExecuteNonQuery sont disponibles au niveau racine. Pour plus d’informations sur ces opérations, consultez [prise en charge de ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md). Pour obtenir des instructions sur la façon d’exécuter ces opérations à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [ExecuteReader, ExecuteScalar ou opérations ExecuteNonQuery dans SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md).  
  
4.  Développez le **vue basée sur un artefact** nœud pour afficher la catégorie des artefacts, à la fois pour Oracle E-Business Suite et de la base de données sous-jacente. Chaque catégorie est catégorisée davantage en fonction de l’application qu'auquel il appartient (pour les artefacts d’Oracle E-Business Suite tels que la table d’interface, les vues de l’interface, les programmes simultanés et demande définit) ou le schéma qu'auquel il appartient (pour Oracle base de données artefacts tels que Les API PL-SQL, procédures, fonctions, tables et vues).  
  
    > [!TIP]
    >  Vous pouvez directement accéder à la catégorie « exécution » ou plusieurs nœuds de sous-catégorie dans l’arborescence, en tapant le nom de l’artefact pendant que le focus est sur l’arborescence dans le **sélectionner une catégorie** boîte. Par exemple, pour accéder à la **procédures** nœud, conserver le focus sur le **vue basée sur un artefact** nœud, puis tapez `Procedures`.  
  
5.  Développez le **Tables d’Interface** nœud pour afficher toutes les applications d’Oracle E-Business Suite. Développez une application de la suite Oracle E-Business pour répertorier toutes les tables d’interface appartenant à cette application. Cliquez sur un nom de table d’interface pour afficher les opérations disponibles pour la table dans le **catégories et opérations disponibles** boîte.  
  
    > [!NOTE]
    >  Si une table de l’interface contient des colonnes de type BLOB, CLOB, NCLOB ou BFILE l’adaptateur expose également une opération spécifique pour lire des données à partir de ces colonnes. Le nom de ces opérations sont Read_\<LOBColName >. Par exemple, si la table d’interface possède une colonne, FILE_DATA, de type BLOB, l’adaptateur expose un **Read_FILE_DATA** opération. Si une table d’interface a plus d’une colonne de type BLOB, CLOB, NCLOB et BFILE l’adaptateur expose nombre autant de Read_\<LOBColName > opérations.  
    >   
    >  De même, si une table de l’interface contient des colonnes de type BLOB, CLOB ou NCLOB l’adaptateur expose également une opération spécifique pour mettre à jour des données dans ces colonnes. Le nom de ces opérations sont en attente_\<LOBColName >. Par exemple, si la table d’interface possède une colonne, FILE_DATA, de type BLOB, l’adaptateur expose un **Update_FILE_DATA** opération. Si une table d’interface a plus d’une colonne de type BLOB, CLOB et NCLOB l’adaptateur expose un nombre plus grand nombre d’en attente_\<LOBColName > opérations. Notez que l’opération de mise à jour n’est pas pris en charge sur les colonnes de type BFILE.  
  
6.  Développez le **vues de l’Interface** nœud pour afficher toutes les applications d’Oracle E-Business Suite. Développez une application de la suite Oracle E-Business pour répertorier toutes les vues de l’interface appartenant à cette application. Cliquez sur un nom de vue d’interface pour afficher les opérations disponibles pour l’affichage dans le **catégories et opérations disponibles** boîte.  
  
    > [!NOTE]
    >  Si une vue de l’interface contient des colonnes de type BLOB, CLOB, NCLOB ou BFILE l’adaptateur expose également une opération spécifique pour lire des données à partir de ces colonnes. Les noms de ces opérations sont Read_\<LOBColName >. Par exemple, si la vue de l’interface possède une colonne, FILE_CONTENT, de type BLOB, l’adaptateur expose un **Read_FILE_CONTENT** opération. Si une vue de l’interface possède plus d’une colonne de type BLOB, CLOB, NCLOB ou BFILE l’adaptateur exposera nombre autant de Read_\<LOBColName > opérations. Notez qu’en attente_\<LOBColName > opérations ne sont pas prises en charge sur les vues.  
  
7.  Développez le **programmes simultanés** nœud pour afficher toutes les applications d’Oracle E-Business Suite. Cliquez sur une application de la suite Oracle E-Business pour répertorier tous les programmes simultanés appartenant à cette application dans le **catégories et opérations disponibles** boîte.  
  
    > [!IMPORTANT]
    >  Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] (ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]) affiche les noms conviviaux des programmes simultanés. Toutefois, les métadonnées pour le programme simultanée a le nom réel du programme simultané. Par exemple, l’application des comptes clients contient un programme simultané « Interface client ». Toutefois, les métadonnées a le nom du programme simultanées en tant que RACUST, qui est le nom réel du programme simultané.  
  
8.  Développez le **jeux de demande** nœud pour afficher toutes les applications d’Oracle E-Business Suite. Cliquez sur une application de la suite Oracle E-Business pour répertorier tous les ensembles de requêtes appartenant à cette application dans le **catégories et opérations disponibles** boîte.  
  
    > [!IMPORTANT]
    >  Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] (ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]) affiche les noms conviviaux des ensembles de requêtes. Toutefois, les métadonnées pour l’ensemble de la demande a le nom réel de l’ensemble de la demande. Par exemple, l’application de l’administrateur d’Applications contient un ensemble de la demande « DownloadPatches ». Toutefois, les métadonnées a le nom du jeu de requête en tant que FNDRSSUB1623, qui est le nom réel de l’ensemble de la demande.  
  
9. Développez le **API PL-SQL** nœud pour afficher les nœuds de catégorie pour le schéma utilisateur actuel (à laquelle se connecter) et tous les autres schémas définis dans la base de données Oracle. Développez le **schéma actuel (\<nom de schéma >)** nœud pour afficher tous les packages définis pour ce schéma. Cliquez sur un nom de package pour afficher les fonctions et les procédures dans le package dans le **catégories et opérations disponibles** boîte.  
  
     ![Rechercher les packages dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-ebs/media/7a9dc061-db0b-4a8e-bfc6-3a003ad687d8.gif "7a9dc061-db0b-4a8e-bfc6-3a003ad687d8")  
  
     De même, développez le **tous les schémas** nœud pour afficher la liste de tous les schémas définis dans la base de données Oracle. Développez un nœud de schéma pour afficher la liste des packages définis pour ce schéma. Cliquez sur un nom de package pour afficher les fonctions et les procédures dans le package dans le **catégories et opérations disponibles** boîte.  
  
     ![Rechercher les packages dans la base de données Oracle pour tous les schémas](../../adapters-and-accelerators/adapter-oracle-ebs/media/09a4841b-b88f-490d-a49a-94e392b5493c.gif "09a4841b-b88f-490d-a49a-94e392b5493c")  
  
10. Développez le **procédures** nœud pour afficher les nœuds de catégorie pour le schéma utilisateur actuel (à laquelle se connecter) et tous les autres schémas définis dans la base de données Oracle. Cliquez sur le **schéma actuel (\<nom de schéma >)** nœud pour afficher toutes les procédures définies pour ce schéma dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir les procédures dans la base de données Oracle pour un schéma](../../adapters-and-accelerators/adapter-oracle-ebs/media/6d78563a-53f7-45cc-8652-f40d4703bdf4.gif "6d78563a-53f7-45cc-8652-f40d4703bdf4")  
  
     De même, développez le **tous les schémas** nœud pour afficher la liste de tous les schémas définis dans la base de données Oracle. Cliquez sur un nœud de schéma pour afficher la liste des procédures définies pour ce schéma dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir les procédures dans la base de données Oracle pour les schémas](../../adapters-and-accelerators/adapter-oracle-ebs/media/a514d199-d6c1-44a0-bf6b-28ddf702081a.gif "a514d199-d6c1-44a0-bf6b-28ddf702081a")  
  
11. Développez le **fonctions** nœud pour afficher les nœuds de catégorie pour le schéma utilisateur actuel (à laquelle se connecter) et tous les autres schémas définis dans la base de données Oracle. Cliquez sur le **schéma actuel (\<nom de schéma >)** nœud pour afficher toutes les fonctions définies pour ce schéma dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir les fonctions dans la base de données Oracle pour un schéma](../../adapters-and-accelerators/adapter-oracle-ebs/media/22c1cabf-9754-4ecd-be37-dbeeb7a6a8fd.gif "22c1cabf-9754-4ecd-be37-dbeeb7a6a8fd")  
  
     De même, développez le **tous les schémas** nœud pour afficher la liste de tous les schémas définis dans la base de données Oracle. Cliquez sur un nœud de schéma pour afficher la liste des fonctions définies pour ce schéma dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir les fonctions dans la base de données Oracle pour tous les schémas](../../adapters-and-accelerators/adapter-oracle-ebs/media/b4d29036-3d37-4a50-82c2-3532adbe2875.gif "b4d29036-3d37-4a50-82c2-3532adbe2875")  
  
12. Développez le **Tables** nœud pour afficher les nœuds de catégorie pour le schéma utilisateur actuel (à laquelle se connecter) et tous les autres schémas définis dans la base de données Oracle. Développez le **schéma actuel (\<nom de schéma >)** nœud pour afficher toutes les tables définies pour ce schéma. Cliquez sur un nom de table pour afficher les opérations prises en charge sur la table dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir les tables dans la base de données Oracle pour un schéma](../../adapters-and-accelerators/adapter-oracle-ebs/media/6ba7420f-9893-4b3e-91cb-10f29d725ad3.gif "6ba7420f-9893-4b3e-91cb-10f29d725ad3")  
  
     De même, développez le **tous les schémas** nœud pour afficher la liste de tous les schémas définis dans la base de données Oracle. Développez un nœud de schéma pour afficher la liste des tables définies pour ce schéma. Cliquez sur un nom de table pour afficher les opérations prises en charge sur la table dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir les tables de base de données Oracle pour tous les schémas](../../adapters-and-accelerators/adapter-oracle-ebs/media/d7c52ab4-ba27-404a-9db6-32b2a635ad2f.gif "d7c52ab4-ba27-404a-9db6-32b2a635ad2f")  
  
    > [!NOTE]
    >  Si une table contient des colonnes de type BLOB, CLOB, NCLOB ou BFILE l’adaptateur expose également une opération spécifique pour lire des données à partir de ces colonnes. Le nom de ces opérations sont Read_\<LOBColName >. Par exemple, si la table possède une colonne, photos, de type BLOB, l’adaptateur expose un **Read_PHOTO** opération. Si une table possède plusieurs colonnes de type BLOB, CLOB, NCLOB et BFILE l’adaptateur expose nombre autant de Read_\<LOBColName > opérations.  
    >   
    >  De même, si une table contient des colonnes de type BLOB, CLOB ou NCLOB l’adaptateur expose également une opération spécifique pour mettre à jour des données dans ces colonnes. Le nom de ces opérations sont en attente_\<LOBColName >. Par exemple, si la table possède une colonne, photos, de type BLOB, l’adaptateur expose un **Update_PHOTO** opération. Si une table possède plusieurs colonnes de type BLOB, CLOB et NCLOB l’adaptateur expose un nombre plus grand nombre d’en attente_\<LOBColName > opérations. Notez que l’opération de mise à jour n’est pas pris en charge sur les colonnes de type BFILE.  
  
13. Développez le **vues** nœud pour afficher les nœuds de catégorie pour le schéma utilisateur actuel (à laquelle se connecter) et tous les autres schémas définis dans la base de données Oracle. Développez le **schéma actuel (\<nom de schéma >)** pour voir toutes les vues définies pour ce nœud. Cliquez sur un nom de la vue pour voir les opérations prises en charge sur cette vue dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir les vues dans la base de données Oracle pour le schéma actuel](../../adapters-and-accelerators/adapter-oracle-ebs/media/2a38cfed-007d-431a-af60-c9c8be5369ab.gif "2a38cfed-007d-431a-af60-c9c8be5369ab")  
  
     De même, développez le **tous les schémas** nœud pour afficher la liste de tous les schémas définis dans la base de données Oracle. Développez un nœud de schéma pour afficher la liste de vues définies pour ce schéma. Cliquez sur un nom de la vue pour voir les opérations prises en charge sur cette vue dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir les vues dans la base de données Oracle pour tous les schémas](../../adapters-and-accelerators/adapter-oracle-ebs/media/67ca336c-62ac-4374-87da-07cf331ea4ad.gif "67ca336c-62ac-4374-87da-07cf331ea4ad")  
  
    > [!NOTE]
    >  Si une vue contient des colonnes de type BLOB, CLOB, NCLOB ou BFILE l’adaptateur expose également une opération spécifique pour lire des données à partir de ces colonnes. Le nom de ces opérations sont Read_\<LOBColName >. Par exemple, si la vue a une colonne, la règle, de type BLOB, l’adaptateur expose un **Read_RULE** opération. Si une vue a plus d’une colonne de type BLOB, CLOB, NCLOB ou BFILE l’adaptateur exposera nombre autant de Read_\<LOBColName > opérations. Notez qu’en attente_\<LOBColName > opérations ne sont pas prises en charge sur les vues.  
  
## <a name="browsing-for-inbound-operations"></a>Navigation pour les opérations entrantes  
 Procédez comme suit pour parcourir les opérations entrantes sous la vue basée sur l’artefact.  
  
#### <a name="to-browse-metadata-for-inbound-operations-under-the-artifact-based-view"></a>Pour parcourir les métadonnées pour les opérations entrantes sous la vue basée sur un artefact  
  
1.  Se connecter à Oracle E-Business Suite à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Consultez [se connecter à Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** répertorier, pour les opérations entrantes sélectionnez **Service (opérations entrantes)**.  
  
3.  Le **sélectionner une catégorie** zone répertorie les différentes vues sous lequel sont classés les artefacts d’Oracle E-Business Suite.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Le nœud racine (/) est sélectionné, et les nœuds de catégorie générale disponibles sous le nœud racine sont répertoriées dans le **catégories et opérations disponibles** boîte.  
  
     ![Opération entrante au niveau racine](../../adapters-and-accelerators/adapter-oracle-ebs/media/9f9f95f3-c6cc-415c-b534-d5f1ad1963d5.gif "9f9f95f3-c6cc-415c-b534-d5f1ad1963d5")  
  
     L’opération entrante, **Notification**, est également disponible au niveau racine.  
  
4.  Développez le **vue basée sur un artefact** nœud pour afficher la catégorie des artefacts, à la fois pour Oracle E-Business Suite et de la base de données sous-jacente. Chaque catégorie est catégorisée davantage en fonction de l’application qu'auquel il appartient (pour les artefacts d’Oracle E-Business Suite tels que la table d’interface et les vues de l’interface) ou le schéma qu'auquel il appartient (pour les objets de base de données Oracle telles que les API PL-SQL, des procédures, fonctions, tables et les vues).  
  
    > [!TIP]
    >  Vous pouvez directement accéder à la catégorie « exécution » ou plusieurs nœuds de sous-catégorie dans l’arborescence, en tapant le nom de l’artefact pendant que le focus est sur l’arborescence dans le **sélectionner une catégorie** boîte. Par exemple, pour accéder à la **procédures** nœud, conserver le focus sur le **vue basée sur un artefact** nœud, puis tapez `Procedures`.  
  
    > [!NOTE]
    >  Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne surface programmes simultanés et requête définit les opérations entrantes.  
  
5.  Développez une application Oracle pour afficher des catégories pour les tables d’interface et les vues de l’interface disponibles pour cette application. Développez le **Tables d’Interface** et **vues de l’Interface** nœuds pour afficher les tables d’interface et les vues de l’interface de l’application Oracle. Sélectionnez une table ou interface interface pour afficher l’opération entrante disponible pour la table ou vue dans la **catégories et opérations disponibles** boîte.  
  
     Dans l’illustration suivante, une vue de l’interface est sélectionnée dans le **sélectionner une catégorie** boîte et l’opération entrante pris en charge sur la vue est répertorié dans le **catégories et opérations disponibles** boîte.  
  
     ![Opérations entrantes sur les vues de l’interface](../../adapters-and-accelerators/adapter-oracle-ebs/media/937f46f2-d142-413f-8744-2180c7116fd4.gif "937f46f2-d142-413f-8744-2180c7116fd4")  
  
6.  Développez le **API PL-SQL** nœud pour afficher les nœuds de catégorie pour le schéma utilisateur actuel (à laquelle se connecter) et tous les autres schémas définis dans la base de données Oracle. Développez le **schéma actuel (\<nom de schéma >)** nœud pour afficher tous les packages définis pour ce schéma. Cliquez sur un nom de package pour afficher les fonctions et les procédures dans le package dans le **catégories et opérations disponibles** boîte. Des procédures et des fonctions répertoriées peuvent servir à interroger la base de données Oracle.  
  
     ![Parcourir PL &#45; API SQL dans Oracle de base de données pour l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/media/4b31ea85-9c5a-42b4-82b2-2cb6d3ead35a.gif "4b31ea85-9c5a-42b4-82b2-2cb6d3ead35a")  
  
     De même, développez le **tous les schémas** nœud pour afficher la liste de tous les schémas définis dans la base de données Oracle. Développez un nœud de schéma pour afficher la liste des packages définis pour ce schéma. Cliquez sur un nom de package pour afficher les fonctions et les procédures dans le package dans le **catégories et opérations disponibles** boîte. Des procédures et des fonctions répertoriées peuvent servir à interroger la base de données Oracle.  
  
     ![Parcourir PL &#45; API SQL pour tous les schémas pour l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/media/e28a803e-fcfb-4021-9225-924d54a484c0.gif "e28a803e-fcfb-4021-9225-924d54a484c0")  
  
7.  Développez le **procédures** nœud pour afficher les nœuds de catégorie pour le schéma utilisateur actuel (à laquelle se connecter) et tous les autres schémas définis dans la base de données Oracle. Cliquez sur le **schéma actuel (\<nom de schéma >)** nœud pour afficher toutes les procédures définies pour ce schéma dans le **catégories et opérations disponibles** boîte. Chacune des procédures répertoriées peut être utilisé pour interroger la base de données Oracle.  
  
     ![Parcourir des procédures de tous les schémas pour l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/media/5e78da80-d99a-44d3-8eac-f636828f8ceb.gif "5e78da80-d99a-44d3-8eac-f636828f8ceb")  
  
     De même, développez le **tous les schémas** nœud pour afficher la liste de tous les schémas définis dans la base de données Oracle. Cliquez sur un nœud de schéma pour afficher la liste des procédures définies pour ce schéma dans le **catégories et opérations disponibles** boîte. Chacune des procédures répertoriées peut être utilisé pour interroger la base de données Oracle.  
  
     ![Parcourir les procédures dans la base de données Oracle pour l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/media/22d8e866-ed19-49f4-a6eb-683343b16cf5.gif "22d8e866-ed19-49f4-a6eb-683343b16cf5")  
  
8.  Développez le **fonctions** nœud pour afficher les nœuds de catégorie pour le schéma utilisateur actuel (à laquelle se connecter) et tous les autres schémas définis dans la base de données Oracle. Cliquez sur le **schéma actuel (\<nom de schéma >)** nœud pour afficher toutes les fonctions définies pour ce schéma dans le **catégories et opérations disponibles** boîte. Chacune des fonctions répertoriées permettre servir à interroger la base de données Oracle.  
  
     ![Parcourir les fonctions dans la base de données Oracle pour l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/media/64c0a30d-a2d6-4dee-90cb-a7e7e2bf62cf.gif "64c0a30d-a2d6-4dee-90cb-a7e7e2bf62cf")  
  
     De même, développez le **tous les schémas** nœud pour afficher la liste de tous les schémas définis dans la base de données Oracle. Cliquez sur un nœud de schéma pour afficher la liste des fonctions définies pour ce schéma dans le **catégories et opérations disponibles** boîte.  Chacune des fonctions répertoriées permettre servir à interroger la base de données Oracle.  
  
     ![Parcourir les fonctions dans la base de données Oracle pour l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/media/1d22c3c8-8c24-4905-8144-bdb4840244f1.gif "1d22c3c8-8c24-4905-8144-bdb4840244f1")  
  
9. Développez le **Tables** nœud pour afficher les nœuds de catégorie pour le schéma utilisateur actuel (à laquelle se connecter) et tous les autres schémas définis dans la base de données Oracle. Développez le **schéma actuel (\<nom de schéma >)** nœud pour afficher toutes les tables définies pour ce schéma. Cliquez sur un nom de table pour afficher la **interrogation** entrants opération prise en charge sur la table dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir les tables dans la base de données Oracle pour l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/media/7c60dfbf-3836-4e72-abe8-5f32a0936807.gif "7c60dfbf-3836-4e72-abe8-5f32a0936807")  
  
     De même, développez le **tous les schémas** nœud pour afficher la liste de tous les schémas définis dans la base de données Oracle. Développez un nœud de schéma pour afficher la liste des tables définies pour ce schéma. Cliquez sur un nom de table pour afficher la **interrogation** entrants opération prise en charge sur la table dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir les tables dans la base de données Oracle pour l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/media/c5fbaf59-2e79-4141-8a85-1e1b8eedcea7.gif "c5fbaf59-2e79-4141-8a85-1e1b8eedcea7")  
  
10. Développez le **vues** nœud pour afficher les nœuds de catégorie pour le schéma utilisateur actuel (à laquelle se connecter) et tous les autres schémas définis dans la base de données Oracle. Développez le **schéma actuel (\<nom de schéma >)** pour voir toutes les vues définies pour ce nœud. Cliquez sur un nom d’affichage pour afficher le **interrogation** entrants opération prise en charge sur cette vue dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir les vues dans la base de données Oracle pour l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/media/2299de79-9f50-433d-9e71-164f6d02bd78.gif "2299de79-9f50-433d-9e71-164f6d02bd78")  
  
     De même, développez le **tous les schémas** nœud pour afficher la liste de tous les schémas définis dans la base de données Oracle. Développez un nœud de schéma pour afficher la liste de vues définies pour ce schéma. Cliquez sur un nom d’affichage pour afficher le **interrogation** entrants opération prise en charge sur cette vue dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir les vues dans la base de données Oracle pour l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/media/860e6636-1ef6-42ad-a0e2-d661e632b624.gif "860e6636-1ef6-42ad-a0e2-d661e632b624")  
  
## <a name="see-also"></a>Voir aussi  
 [Parcourir, rechercher et d’obtenir des métadonnées pour des opérations Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)