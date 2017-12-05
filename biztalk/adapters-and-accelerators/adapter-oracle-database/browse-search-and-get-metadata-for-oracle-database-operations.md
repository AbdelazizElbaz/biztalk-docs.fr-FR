---
title: "Parcourir, rechercher et obtenir des métadonnées pour les opérations de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF client, generating a
- operations, browsing for
- metadata, browsing
- browse, for operations
- schema, generating
- metadata, retrieving
- browse, metadata
- retrieve, metadata
- operations, searching for
- WCF service contract, generating a
- metadata, browsing, searching, and retrieving
ms.assetid: 65bd59e0-771d-40fe-966c-8cc8a629ce47
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7427ab96879c54b5a71435576da8a4610787dd6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="browse-search-and-get-metadata-for-oracle-database-operations"></a>Parcourir, rechercher et obtenir des métadonnées pour les opérations de base de données Oracle
Cette section fournit des informations sur l’utilisation de [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], et [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]. À l’aide de ces [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] composants, vous pouvez :  
  
-   Rechercher des opérations pour lequel récupérer les métadonnées.  
  
-   Rechercher des opérations pour lequel récupérer les métadonnées.  
  
-   Ajouter des schémas de message pour les opérations sélectionnées et le port de fichiers de configuration de liaison à un projet BizTalk server lors de l’utilisation du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  
  
-   Ajouter une classe de client WCF ou un contrat de service WCF (interface) pour les opérations sélectionnées et un fichier de configuration (app.config) à un projet de programmation non-BizTalk en utilisant le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
 Vous devez vous connecter à la base de données Oracle avant de pouvoir parcourir, rechercher ou récupérer les métadonnées pour les opérations de la cible. Pour plus d’informations sur la façon de se connecter à Oracle de base de données lorsque vous utilisez [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [se connecter à la base de données Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio.md).  
  
> [!NOTE]
>  -   Le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], et [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] présentes essentiellement la même interface lors de la navigation et de la recherche pour les opérations, afin des trois composants sont traités dans les rubriques mêmes.  
> -   Vous pouvez sélectionner des nœuds de catégorie pour retourner toutes les opérations dans la sous-arborescence de cette catégorie, par exemple, une table entière ou schéma (ou même toutes les tables dans un schéma).  
  
## <a name="browsing-for-operations"></a>Recherche d’opérations  
 Lors de l’exploration à l’aide de métadonnées [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces :  
  
-   Opérations qui peuvent être effectuées sur les tables, vues, procédures stockées, fonctions et les packages.  
  
-   L’opération SQLEXECUTE, qui permet aux clients d’adaptateur exécuter n’importe quel langage de manipulation de données génériques (DML) ou d’une procédure stockée dans une base de données Oracle.  
  
-   Les opérations POLLINGSTMT et de Notification, qui permettent aux clients d’adaptateur obtenir les données entrantes à partir de la base de données Oracle. Il expose également une liste des procédures stockées, des fonctions et des packages dans les schémas respectifs qui sont exposées en tant qu’opérations pour l’interrogation.  
  
> [!NOTE]
>  -   À l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], vous pouvez parcourir les nœuds de catégorie et l’opération à l’aide d’une interface Windows.  
> -   Les opérations SQLEXECUTE, POLLINGSTMT et de Notification sont présentées directement sous le nœud racine dans l’arborescence de la catégorie. Vous devez sélectionner le nœud racine pour afficher ces opérations sortantes et entrantes.  
  
 Pour plus d’informations sur les métadonnées de navigation, consultez [obtenir les métadonnées pour les opérations de base de données Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)  
  
 Les étapes suivantes pour parcourir les opérations exposées pour différents artefacts dans une base de données Oracle à l’aide du [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
#### <a name="to-browse-metadata-in-an-oracle-database"></a>Pour parcourir les métadonnées dans une base de données Oracle  
  
1.  Se connecter à une base de données Oracle à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Consultez [se connecter à la base de données Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** liste déroulante, sélectionnez le type de contrat, selon que vous allez effectuer les opérations entrantes et sortantes, à l’aide de l’adaptateur.  
  
3.  Le **sélectionner une catégorie** zone répertorie les schémas dans la base de données Oracle. Cliquez sur un schéma pour afficher les tables, procédures, fonctions, packages et les vues accessibles sur le schéma dans le **catégories et opérations disponibles** boîte. Vous pouvez également voir la catégorisation en développant le nœud de schéma.  
  
    > [!TIP]
    >  Vous pouvez directement accéder à la catégorie « exécution » ou plusieurs nœuds de sous-catégorie dans l’arborescence, en tapant le nom de l’artefact dans tandis que le focus est sur l’arborescence dans le **sélectionner une catégorie** boîte. Par exemple, pour accéder à la **SCOTT** nœud, conserver le focus sur le nœud racine, puis tapez `SCOTT`.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Le nœud de schéma SCOTT est sélectionné, et les nœuds de catégorie générale disponibles sous le nœud SCOTT sont répertoriées dans le **catégories et opérations disponibles** boîte.  
  
     ![Rechercher les utilisateurs dans une base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/media/c6e02d12-278b-4419-8c8d-d12d0d64f325.gif "c6e02d12-278b-4419-8c8d-d12d0d64f325")  
  
4.  Cliquez sur le **Table** nœud pour afficher les tables de SCOTT dans le **catégories et opérations disponibles** boîte. Ou bien, vous pouvez voir la liste des tables en développant le **Table** nœud.  
  
5.  Cliquez sur un nom de table pour afficher les opérations prises en charge sur la table.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Les tables disponibles dans le schéma SCOTT sont répertoriées dans le **sélectionner une catégorie** boîte. Les opérations disponibles pour la table EMP sont répertoriées dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir les tables dans une base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/media/6df61a2f-3cd9-486c-9bf5-7968f8f1ce8d.gif "6df61a2f-3cd9-486c-9bf5-7968f8f1ce8d")  
  
6.  Cliquez sur le **procédure** nœud pour répertorier les procédures accessibles au schéma SCOTT dans le **catégories et opérations disponibles** boîte.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Les nœuds de catégorie générale disponibles dans le schéma SCOTT sont répertoriées dans le **sélectionner une catégorie** boîte. Les procédures disponibles dans le schéma SCOTT sont répertoriées dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir les procédures dans une base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/media/9826e160-5295-4fdc-bd82-ccd456d89242.gif "9826e160-5295-4fdc-bd82-ccd456d89242")  
  
7.  Cliquez sur le **fonction** nœud pour afficher les fonctions pour le schéma SCOTT dans le **catégories et opérations disponibles** boîte.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Les nœuds de catégorie générale disponibles dans le schéma SCOTT sont répertoriées dans le **sélectionner une catégorie** boîte. Les fonctions disponibles dans le schéma SCOTT sont répertoriées dans le **catégories et opérations disponibles** boîte.  
  
     ![Parcourir les fonctions dans une base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/media/ae02731e-7f26-4552-8e40-db797885af01.gif "ae02731e-7f26-4552-8e40-db797885af01")  
  
8.  Cliquez sur le **Package** nœud pour afficher les packages pour le schéma SCOTT dans le **catégories et opérations disponibles** boîte. Vous pouvez également voir la liste des packages en développant le **Package** nœud.  
  
9. Cliquez sur un nom de package pour afficher les opérations prises en charge sur le package.  
  
     L’illustration suivante montre [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], qui répertorie les packages et les opérations prises en charge pour un package particulier, pour le schéma SCOTT.  
  
     ![Rechercher les packages dans une base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/media/bts-r2-net-adapter-oracle-tut1-browse-pckgs.gif "bts_R2_NET_Adapter_Oracle_Tut1_Browse_Pckgs")  
  
10. Cliquez sur le **vue** nœud pour afficher les affichages pour le schéma SCOTT dans le **catégories et opérations disponibles** boîte. Vous pouvez également voir la liste des vues en développant le **vue** nœud.  
  
11. Cliquez sur un nom de la vue pour voir les opérations prises en charge sur la vue.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], qui répertorie les vues et les opérations prises en charge pour une vue particulière, pour le schéma SCOTT.  
  
     ![Parcourir les vues dans une base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/media/cc1079bc-c1ca-4c2b-a291-abf87bf1ac4d.gif "cc1079bc-c1ca-4c2b-a291-abf87bf1ac4d")  
  
    > [!NOTE]
    >  Les modèles de canal et le service WCF, les clients de l’adaptateur de spécifier une taille de lot pour effectuer une récupération de lot de métadonnées.  
  
## <a name="searching-for-operations"></a>Recherche d’opérations  
 Lors de la recherche à l’aide de métadonnées Oracle [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]:  
  
-   Prend en charge les caractères génériques et d’échappement dans l’expression de recherche.  
  
-   Permet la recherche immédiatement sous le nœud à partir duquel l’opération de recherche est effectuée. Par exemple, pour rechercher une fonction, vous devez être recherche sous \\[schéma] \Functions. Recherche de plusieurs niveaux n’est pas pris en charge.  
  
 Le tableau suivant répertorie les caractères spéciaux qui peuvent être utilisés pour la recherche et de leur interprétation par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
|Caractère spécial|Interprétation|  
|-----------------------|--------------------|  
|_ (souligné)|Correspond à exactement un caractère<br /><br /> Par exemple, A_ correspond à AB, CA, Active Directory.|  
|% (pourcentage)|Correspond à zéro ou plusieurs caractères.<br /><br /> Par exemple, un % correspond à un, AB, ABC.|  
|\ (échappement)|Remplace une signification spéciale % et _<br /><br /> Par exemple, un\\_B correspond à A_B.|  
  
> [!NOTE]
>  Caractère d’échappement est un caractère qui est placé avant un caractère générique pour indiquer que le caractère générique doit être interprété comme un caractère normal et non comme un caractère générique.  
  
 Pour plus d’informations, consultez [obtenir les métadonnées pour les opérations de base de données Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)  
  
#### <a name="to-search-metadata-in-an-oracle-database"></a>Pour rechercher des métadonnées dans une base de données Oracle  
  
1.  Se connecter à une base de données Oracle à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Consultez [se connecter à la base de données Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio.md) pour obtenir des instructions.  
  
2.  Dans le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], à partir de la **type de contrat Select** liste déroulante, sélectionnez le type de contrat selon si vous recherchent pour les opérations entrantes ou sortantes, à l’aide de l’adaptateur.  
  
3.  Dans le **sélectionner une catégorie** , cliquez sur le schéma contenant des tables, des procédures, fonctions, les packages et les vues que vous souhaitez rechercher. Si vous ne savez pas quel schéma, cliquez sur, cliquez sur le nœud racine.  
  
4.  Dans le **recherche dans la catégorie** texte, entrez une expression de recherche pour rechercher un schéma spécifique. Par exemple, pour rechercher des schémas qui ont « SC » dans leur nom, tapez **% SC** dans la zone de texte.  
  
5.  Cliquez sur le bouton avec l’icône de flèche droite pour démarrer la recherche. Une fois la recherche terminée, le **catégories et opérations disponibles** zone répertorie les schémas qui répondent aux critères de recherche.  
  
6.  Dans le **sélectionner une catégorie** zone, développez le nœud qui correspond au schéma, puis cliquez sur la base de données d’élément que vous souhaitez chercher dans. Dans le **recherche dans la catégorie** texte, entrez une expression de recherche pour rechercher un élément spécifique de la base de données.  
  
     Par exemple, pour rechercher des tables qui ont « EMP » dans leur nom, sélectionnez **Table**, type **% EMP** dans les **recherche dans la catégorie** texte zone, puis cliquez sur le bouton avec le icône de flèche droite.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], qui répertorie les résultats de la recherche.  
  
     ![Rechercher des métadonnées dans une base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/media/1ee912f8-896e-4b45-ba98-1bbd36b56574.gif "1ee912f8-896e-4b45-ba98-1bbd36b56574")  
  
    > [!NOTE]
    >  Les modèles de canal et le service WCF, les clients de l’adaptateur de spécifier une taille de lot pour effectuer une recherche batch-wise de métadonnées.  
  
## <a name="generating-schema-using-the-consume-adapter-service-add-in-or-add-adapter-metadata-wizard"></a>Génération de schéma à l’aide du Consume Adapter Service Add-in ou l’Assistant Ajout d’adaptateur métadonnées  
 Vous pouvez utiliser la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer le schéma pour les artefacts de base de données Oracle sélectionnées. Une fois que vous avez parcouru et rechercher les artefacts que vous voulez appeler, vous pouvez générer le schéma pour ces artefacts et envoyer des messages, conforme au schéma de base de données Oracle. Les étapes suivantes pour récupérer les métadonnées d’une base de données Oracle à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
> [!NOTE]
>  Vous pouvez sélectionner des nœuds de catégorie pour retourner toutes les opérations de cette catégorie sub-Tree, par exemple, vous pouvez sélectionner une table entière (à la génération du schéma pour toutes les opérations dans la table) ou une sélection des opérations spécifiques sur une table (par exemple, Insert et Delete) à génération du schéma pour seulement les opérations sur une table. Pour plus d’informations sur les nœuds, consultez [IDs3 de nœud de métadonnées](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md).  
  
#### <a name="to-retrieve-metadata-from-an-oracle-database"></a>Pour récupérer des métadonnées à partir d’une base de données Oracle  
  
1.  Se connecter à une base de données Oracle à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. Consultez [se connecter à la base de données Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** liste déroulante, sélectionnez le type de contrat, selon que vous allez effectuer les opérations entrantes et sortantes, à l’aide de l’adaptateur.  
  
3.  Dans le **sélectionner une catégorie** , développez un nœud de schéma.  
  
4.  Sélectionnez la catégorie pour laquelle vous souhaitez générer des métadonnées. Par exemple, si vous souhaitez générer des métadonnées pour une table, sélectionnez **Table**.  
  
5.  Développez ce nœud de catégorie et sélectionnez l’élément spécifique au sein de ce nœud pour lequel vous souhaitez générer des métadonnées.  
  
     Par exemple, pour générer des métadonnées pour une table spécifique, développez le **Table** nœud, puis sélectionnez le nom de table spécifique.  
  
    > [!NOTE]
    >  Vous pouvez également rechercher un élément de la base de données spécifique, comme décrit dans la procédure précédente.  
  
6.  Dans le **catégories et opérations disponibles** zone, sélectionnez les opérations qui se rapportent à l’élément de base de données que vous avez sélectionné à l’étape précédente, puis cliquez sur **ajouter**. Opérations sélectionnées sont répertoriées dans le **ajouté des catégories et opérations** boîte.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], qui répertorie les opérations sélectionnées.  
  
     ![Récupérer les métadonnées d’une base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/media/d3950566-8720-4c15-8a16-4ade14bf6221.gif "d3950566-8720-4c15-8a16-4ade14bf6221")  
  
     Si vous souhaitez générer le schéma pour plusieurs opérations, il est possible des définitions d’élément en double parmi ces schémas peut provoquer un échec de la compilation du projet BizTalk. Par exemple, considérez un scénario où vous générez le schéma pour une opération « Op1 ». Le schéma de « Op1 » contient un paramètre de type de données complexe « CT1 ». Après avoir généré le schéma pour « Op1 » que vous fermez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et rouvrez-le pour générer le schéma d’une autre opération « Op2 ». Supposons que « Op2 » contient également un paramètre de type de données complexe « CT1 ». Après avoir quitté le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et compilez le projet, vous obtenez des erreurs de compilation, car le type de données complexe « CT1 » est défini à deux reprises dans différents fichiers XSD. Dans ce cas, nous recommandons ce qui suit :  
  
    -   Génération du schéma pour toutes les opérations en une seule exécution de [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Cela garantit que le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ne génère qu’une seule définition pour le type de données complexe « CT1 ».  
  
    -   Si vous souhaitez générer le schéma pour plusieurs opérations entre les différentes exécutions de [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], veillez à sélectionner le **générer des types de schéma unique** case à cocher pour que les fichiers XSD générés contiennent des espaces de noms uniques pour le complexe type de données « CT1 ».  
  
7.  Cliquez sur **OK**. Le fichier de schéma est enregistré avec une extension .xsd dans le même emplacement que le projet BizTalk.  
  
     Par défaut, les fichiers sont créés avec la convention d’affectation de noms « OracleDBBindingSchema\<n\>.xsd », où « n » peut être 1, 2 et ainsi de suite, en fonction du nombre de fichiers de schéma créé. Ou bien, vous pouvez fournir un nom personnalisé pour les fichiers de schéma en entrant un nom dans la **préfixe de nom de fichier** zone de texte. Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] maintenant crée des fichiers de schéma avec la convention d’affectation de noms \<préfixe du nom de fichier\>schéma\<n\>.xsd.  
  
    > [!NOTE]
    >  Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] crée également un fichier de liaison (un fichier XML) qui contient les propriétés de liaison que vous avez spécifié quand générer le schéma pour une opération et l’action SOAP pour appeler l’opération. Vous pouvez importer ce fichier de liaison dans la console Administration de BizTalk Server pour créer un port personnalisé WCF avec l’URI, les propriétés de liaison de connexion et l’action SOAP définie. Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).  
  
    > [!IMPORTANT]
    >  À l’aide de la [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] ne génère pas un fichier de liaison.  
  
8.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="generating-a-wcf-client-or-wcf-service-contract-using-the-add-adapter-service-reference-plug-in"></a>Génération d’un Client WCF ou le contrat de Service WCF à l’aide de l’ajouter une référence de Service d’adaptateur plug-in  
 Vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer le code du client WCF pour les opérations sortantes ou code de service WCF pour les opérations entrantes.  
  
#### <a name="to-retrieve-metadata-from-an-oracle-database"></a>Pour récupérer des métadonnées à partir d’une base de données Oracle  
  
1.  Dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], à partir de la **type de contrat Select** liste déroulante, sélectionnez le type de contrat, selon que vous allez effectuer entrant (POLLINGSTMT) ou des opérations sortantes.  
  
2.  Parcourir ou rechercher des catégories (par exemple, une table de base de données Oracle) ou des opérations spécifiques pour lesquels vous voulez générer un client WCF (ou le contrat de service WCF).   
    Par exemple, pour rechercher les opérations de SCOTT. Table EMP, dans le **sélectionner une catégorie** zone :  
  
    1.  Développez le nœud racine (**/**) pour afficher les schémas signalées pour la base de données Oracle.  
  
    2.  Sous le nœud racine, développez le **SCOTT** nœud pour afficher les catégories exposées pour le schéma SCOTT.  
  
    3.  Sous le **SCOTT** nœud, développez le **Table** nœud pour afficher les tables signalées pour le schéma SCOTT.  
  
    4.  Sous le **Table** nœud sélectionner le **EMP** nœud. Les opérations exposées en surface pour la table EMP sont répertoriées dans le **catégories et opérations disponibles** boîte.  
  
3.  Dans le **catégories et opérations disponibles** , sélectionnez les opérations ou les catégories pour lequel vous souhaitez générer un client WCF (ou le contrat de service WCF), puis cliquez sur **ajouter**. Opérations sélectionnées sont répertoriées dans le **ajouté des catégories et opérations** boîte.  
  
     L’illustration suivante montre la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] avec les opérations Insert et Update pour SCOTT. Table EMP sélectionnée.  
  
     ![Les opérations Select et Update sont sélectionnées. ] (../../adapters-and-accelerators/adapter-oracle-database/media/4c41ac7b-784a-494c-ac82-c007e22a4fdf.gif "4c41ac7b-784a-494c-ac82-c007e22a4fdf")  
  
    > [!IMPORTANT]
    >  Selon les opérations sortantes (ou catégories) que vous sélectionnez, plus de WCF d’une classe de client peut être générée. Pour plus d’informations, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md).  
  
4.  La plupart des scénarios, les options de sérialisation par défaut sont suffisantes ; Toutefois, si nécessaire, vous pouvez contrôler plusieurs aspects sur le code qui est généré et le type de sérialiseur utilisé. Pour définir ces options :  
  
    1.  Cliquez sur **Options avancées** pour ouvrir le **Options avancées** boîte.  
  
    2.  Dans le **Options avancées** sous **choisir les options pour le proxy généré**, sélectionnez les options souhaitées. Par exemple, vous pouvez choisir les méthodes asynchrones sont générés pour le client WCF ou désactiver la génération d’un fichier de configuration.  
  
    3.  Sous **sérialiseur** sélectionner le sérialiseur doit être utilisé.  
  
     L’illustration suivante montre le **Options avancées** zone avec les sélections par défaut (**automatique** est sélectionné pour le sérialiseur et aucune autre option est sélectionnées).  
  
     ![Les Options avancées zone des paramètres par défaut](../../adapters-and-accelerators/adapter-oracle-database/media/r2-net-adapters-oracle-msb-advanced-options.gif "R2_NET_Adapters_Oracle_MSB_Advanced_Options")  
  
     Les options que vous pouvez configurer dans le **Options avancées** zone sont équivalentes à certaines des options disponibles lorsque vous utilisez le service Model Metadata Utility Tool (svcutil.exe). Pour plus d’informations sur ces options, consultez [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx).
  
5.  Cliquez sur **OK**. Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] enregistre la classe de client WCF (ou l’interface de service WCF) et le code d’assistance pour les opérations et les catégories que vous avez sélectionnées dans votre répertoire de projet. Par défaut, un fichier de configuration est également enregistré. Légèrement différents fichiers sont générés pour les opérations entrantes et sortantes ; Pour plus d’informations, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md).  
  
 Vous pouvez sélectionner n’importe quel nœud qui est répertorié dans le **catégories et opérations disponibles** boîte. Si vous sélectionnez un nœud de catégorie toutes les opérations disponibles sous ce nœud et ses sous-nœuds seront sélectionnés. Par exemple, pour générer un client WCF pour toutes les opérations exposées en surface pour la table EMP, vous pouvez sélectionner le nœud EMP ; pour générer des clients WCF pour toutes les tables dans le schéma SCOTT, vous pouvez sélectionner le nœud de la Table ; et ainsi de suite.  
  
## <a name="see-also"></a>Voir aussi  
[Obtenir les métadonnées pour les opérations de base de données Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)