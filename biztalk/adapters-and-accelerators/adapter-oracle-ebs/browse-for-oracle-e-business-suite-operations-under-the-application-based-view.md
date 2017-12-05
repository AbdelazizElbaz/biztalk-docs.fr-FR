---
title: "Rechercher des opérations Oracle E-Business Suite dans la vue basée sur une application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb207869-1a19-4e19-ba47-c78d2a29b36d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d4d4d67df9d7463a699b1ec9448feeea0a9c57a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="browse-for-oracle-e-business-suite-operations-under-the-application-based-view"></a>Rechercher des opérations Oracle E-Business Suite dans la vue basée sur l’application
Vous pouvez utiliser la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour parcourir les opérations entrantes et sortantes qui peuvent être effectuées sur Oracle E-Business Suite à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Cette rubrique fournit des informations sur la façon de rechercher des opérations sortantes et entrantes sous la vue basée sur l’application.  
  
> [!NOTE]
>  Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] présentes essentiellement la même interface lors de la navigation et de la recherche pour les opérations, afin des deux composants sont traités dans les rubriques mêmes.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez vous connecter à Oracle E-Business Suite avant de pouvoir parcourir les métadonnées pour les opérations de la cible. Pour plus d’informations sur la façon de se connecter à Oracle de base de données lorsque vous utilisez la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [se connecter à Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md).  
  
## <a name="browsing-for-outbound-operations"></a>Navigation pour les opérations sortantes  
 Procédez comme suit pour parcourir les opérations sortantes sous la vue basée sur l’application.  
  
#### <a name="to-browse-metadata-for-outbound-operations-under-the-application-based-view"></a>Pour parcourir les métadonnées pour les opérations sortantes sous la vue basée sur l’Application  
  
1.  Se connecter à Oracle E-Business Suite à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Consultez [se connecter à Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** , sélectionnez **Client (Outbound operations)**.  
  
3.  Le **sélectionner une catégorie** zone répertorie les différentes vues sous lequel sont classés les artefacts d’Oracle E-Business Suite.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Le nœud racine (/) est sélectionné, et les nœuds de catégorie générale disponibles sous le nœud racine sont répertoriées dans le **catégories et opérations disponibles** boîte.  
  
     ![Opérations et catégories au niveau racine](../../adapters-and-accelerators/adapter-oracle-ebs/media/559a6652-2d9d-4ecd-a1bb-4f63750c9518.gif "559a6652-2d9d-4ecd-a1bb-4f63750c9518")  
  
    > [!NOTE]
    >  Les opérations standard telles que ExecuteReader, ExecuteScalar et ExecuteNonQuery sont disponibles au niveau racine. Pour plus d’informations sur ces opérations, consultez [prise en charge de ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md). Pour obtenir des instructions sur la façon d’exécuter ces opérations à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [ExecuteReader, ExecuteScalar ou opérations ExecuteNonQuery dans SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md).  
  
4.  Développez le **vue basée sur l’Application** nœud pour afficher toutes les Oracle E-Business suite applications disponibles sur le serveur auquel vous connecté. Développez une application pour afficher des catégories pour les tables d’interface, les vues de l’interface, les programmes simultanés et demande définit disponible pour cette application.  
  
    > [!TIP]
    >  Vous pouvez directement accéder à la catégorie « exécution » ou plusieurs nœuds de sous-catégorie dans l’arborescence, en tapant le nom de l’artefact dans tandis que le focus est sur l’arborescence dans le **sélectionner une catégorie** boîte. Par exemple, pour accéder à la **alerte** nœud, conserver le focus sur le **vue basée sur l’Application** nœud, puis tapez `Alert`.  
  
5.  Développez le **Tables d’Interface** nœud pour afficher les tables de l’interface de l’application Oracle. Cliquez sur une table d’interface pour afficher la liste des opérations disponibles pour la table dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir les tables d’interface dans Oracle E &#45; Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/media/fcfbe41c-14e0-43b5-aada-c4c686aecff4.gif "fcfbe41c-14e0-43b5-aada-c4c686aecff4")  
  
    > [!NOTE]
    >  Si une table de l’interface contient des colonnes de type BLOB, CLOB, NCLOB ou BFILE l’adaptateur expose également une opération spécifique pour lire des données à partir de ces colonnes. Le nom de ces opérations sont Read_\<LOBColName\>. Par exemple, si la table d’interface possède une colonne, FILE_DATA, de type BLOB, l’adaptateur expose un **Read_FILE_DATA** opération. Si une table d’interface a plus d’une colonne de type BLOB, CLOB, NCLOB et BFILE l’adaptateur expose nombre autant de Read_\<LOBColName\> operations.  
    >   
    >  De même, si une table de l’interface contient des colonnes de type BLOB, CLOB ou NCLOB l’adaptateur expose également une opération spécifique pour mettre à jour des données dans ces colonnes. Le nom de ces opérations sont en attente_\<LOBColName\>. Par exemple, si la table d’interface possède une colonne, FILE_DATA, de type BLOB, l’adaptateur expose un **Update_FILE_DATA** opération. Si une table d’interface a plus d’une colonne de type BLOB, CLOB et NCLOB l’adaptateur expose un nombre plus grand nombre d’en attente_\<LOBColName\> operations. Notez que l’opération de mise à jour n’est pas pris en charge sur les colonnes de type BFILE.  
  
6.  Développez le **vues de l’Interface** nœud pour afficher les vues de l’interface de l’application Oracle. Cliquez sur une vue de l’interface pour afficher la liste des opérations disponibles pour l’affichage dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir les vues de l’interface dans Oracle E &#45; Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/media/f1dc14cc-ad77-47ed-b0b0-b5fc78ed545b.gif "f1dc14cc-ad77-47ed-b0b0-b5fc78ed545b")  
  
    > [!NOTE]
    >  Si une vue de l’interface contient des colonnes de type BLOB, CLOB, NCLOB ou BFILE l’adaptateur expose également une opération spécifique pour lire des données à partir de ces colonnes. Le nom de ces opérations sont Read_\<LOBColName\>. Par exemple, si la vue de l’interface possède une colonne, FILE_CONTENT, de type BLOB, l’adaptateur expose un **Read_FILE_CONTENT** opération. Si une vue de l’interface possède plus d’une colonne de type BLOB, CLOB, NCLOB ou BFILE l’adaptateur exposera nombre autant de Read_\<LOBColName\> operations. Notez qu’en attente_\<LOBColName\> opérations ne sont pas prises en charge sur les vues.  
  
7.  Cliquez sur le **programmes simultanés** nœud pour afficher les programmes simultanés pour une application dans le **catégories et opérations disponibles** boîte.  
  
     ![Rechercher les programmes simultanés pour une application Oracle](../../adapters-and-accelerators/adapter-oracle-ebs/media/71173055-4250-4406-838b-c5e9d6bf9e8c.gif "71173055-4250-4406-838b-c5e9d6bf9e8c")  
  
     Cette figure illustre les programmes simultanés spécifiques à une application Oracle et les programmes simultanés standards pour toutes les applications d’Oracle.  
  
    > [!IMPORTANT]
    >  Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] (ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]) affiche les noms conviviaux des programmes simultanés. Toutefois, les métadonnées pour le programme simultanée a le nom réel du programme simultané. Par exemple, l’application des comptes clients contient un programme simultané « Interface client ». Toutefois, les métadonnées a le nom du programme simultanées en tant que RACUST, qui est le nom réel du programme simultané.  
  
8.  Cliquez sur le **demande définit** nœud pour afficher la demande définit pour une application dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir des jeux de demande d’une application Oracle](../../adapters-and-accelerators/adapter-oracle-ebs/media/0934f6f5-0d7a-4dad-a550-e7a4f524551b.gif "0934f6f5-0d7a-4dad-a550-e7a4f524551b")  
  
    > [!IMPORTANT]
    >  Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] (ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]) affiche les noms conviviaux des ensembles de requêtes. Toutefois, les métadonnées pour l’ensemble de la demande a le nom réel de l’ensemble de la demande. Par exemple, l’application de l’administrateur d’Applications contient un ensemble de la demande « DownloadPatches ». Toutefois, les métadonnées a le nom du jeu de requête en tant que FNDRSSUB1623, qui est le nom réel de l’ensemble de la demande.  
  
## <a name="browsing-for-inbound-operations"></a>Navigation pour les opérations entrantes  
 Procédez comme suit pour parcourir les opérations entrantes sous la vue basée sur l’application.  
  
#### <a name="to-browse-metadata-for-inbound-operations-under-the-application-based-view"></a>Pour parcourir les métadonnées pour les opérations entrantes sous la vue basée sur l’Application  
  
1.  Se connecter à Oracle E-Business Suite à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Consultez [se connecter à Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** répertorier, pour les opérations entrantes sélectionnez **Service (opérations entrantes)**.  
  
3.  Le **sélectionner une catégorie** zone répertorie les différentes vues sous lequel sont classés les artefacts d’Oracle E-Business Suite.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Le nœud racine (/) est sélectionné, et les nœuds de catégorie générale disponibles sous le nœud racine sont répertoriées dans le **catégories et opérations disponibles** boîte.  
  
     ![Opération entrante au niveau racine](../../adapters-and-accelerators/adapter-oracle-ebs/media/9f9f95f3-c6cc-415c-b534-d5f1ad1963d5.gif "9f9f95f3-c6cc-415c-b534-d5f1ad1963d5")  
  
     L’opération entrante, **Notification**, est également disponible au niveau racine.  
  
4.  Développez le **vue basée sur l’Application** nœud pour afficher toutes les Oracle E-Business suite applications disponibles sur le serveur auquel vous connecté. Développez une application pour afficher des catégories pour les tables d’interface et les vues de l’interface.  
  
    > [!TIP]
    >  Vous pouvez directement accéder à la catégorie « exécution » ou plusieurs nœuds de sous-catégorie dans l’arborescence, en tapant le nom de l’artefact dans tandis que le focus est sur l’arborescence dans le **sélectionner une catégorie** boîte. Par exemple, pour accéder à la **alerte** nœud, conserver le focus sur le **vue basée sur l’Application** nœud, puis tapez `Alert`.  
  
5.  Développez une application Oracle pour afficher des catégories pour les tables d’interface et les vues de l’interface disponibles pour cette application. Développez le **Tables d’Interface** et **vues de l’Interface** nœuds pour afficher les tables d’interface et les vues de l’interface de l’application Oracle. Sélectionnez une table ou interface interface pour afficher l’opération entrante disponible pour la table ou vue dans la **catégories et opérations disponibles** boîte.  
  
     Dans l’illustration suivante, une vue de l’interface est sélectionnée dans le **sélectionner une catégorie** boîte et l’opération entrante pris en charge sur la vue est répertorié dans le **catégories et opérations disponibles** boîte.  
  
     ![Opérations entrantes sur les vues de l’interface](../../adapters-and-accelerators/adapter-oracle-ebs/media/937f46f2-d142-413f-8744-2180c7116fd4.gif "937f46f2-d142-413f-8744-2180c7116fd4")  
  
    > [!NOTE]
    >  Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne surface programmes simultanés et requête définit les opérations entrantes.  
  
## <a name="see-also"></a>Voir aussi  
 [Parcourir, rechercher et d’obtenir des métadonnées pour des opérations Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)