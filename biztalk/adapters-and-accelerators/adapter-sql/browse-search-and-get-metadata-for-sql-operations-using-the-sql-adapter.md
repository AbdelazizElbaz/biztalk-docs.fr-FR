---
title: "Parcourir, rechercher et obtenir des métadonnées pour les opérations SQL à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdd5ca6f-30ff-4d32-a656-bbd54b9d072e
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a8d82a69b342c278e7cb17de8759d4986a71cd6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="browse-search-and-get-metadata-for-sql-operations-using-the-sql-adapter"></a>Parcourir, rechercher et obtenir des métadonnées pour les opérations SQL à l’aide de l’adaptateur SQL
Cette section fournit des informations sur l’utilisation de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]et le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]. À l’aide de ces [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] composants, vous pouvez :  
  
-   Rechercher des opérations pour lequel récupérer les métadonnées.  
  
-   Rechercher des opérations pour lequel récupérer les métadonnées.  
  
-   Ajouter des schémas de message pour les opérations sélectionnées et les fichiers de configuration de liaison pour le port un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] de projet lorsque vous utilisez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
-   Ajouter une classe de client WCF ou un contrat de service WCF (interface) pour les opérations sélectionnées et un fichier de configuration (app.config) à un projet de programmation non-BizTalk en utilisant le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
> [!NOTE]
>  Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] présentes essentiellement la même interface lors de la navigation et de la recherche pour les opérations, afin des trois composants sont traités dans les rubriques mêmes.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez vous connecter à SQL Server avant de pouvoir parcourir, rechercher ou récupérer les métadonnées pour les opérations de la cible. Pour plus d’informations sur la façon de se connecter à SQL Server lorsque vous utilisez la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [se connecter à SQL Server dans Visual Studio à l’aide de la macro complémentaire Consume Adapter Service](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md).  
  
## <a name="browsing-for-operations"></a>Recherche d’opérations  
 Vous pouvez utiliser la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour parcourir les opérations entrantes et sortantes qui peuvent être effectuées sur SQL Server à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
### <a name="outbound-operations"></a>Opérations sortantes  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] permet aux clients d’effectuer les opérations sortantes suivantes.  
  
-   INSERT, Select, Update et opérations Delete sur les tables et les vues.  
  
-   Opérations de jeu < nom_colonne > sur les tables et vues. Cette opération est exposée sur les tables qui possèdent des colonnes de varchar (max), nvarchar (max) ou varbinary (max). Ces opérations permettent de diffusion en continu d’objets volumineux.  
  
-   Procédures stockées, faiblement et fortement typée en tant qu’opérations.  
  
-   Scalaires et table table des fonctions en tant qu’opérations.  
  
 L’adaptateur expose également les opérations sortantes génériques tel que **ExecuteReader**, **ExecuteScalar**, et **ExecuteNonQuery** au niveau racine.  
  
### <a name="inbound-operations"></a>Opérations entrantes  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] permet aux clients d’effectuer les opérations suivantes de trafic entrantes.  
  
-   **L’interrogation** opération pour recevoir des messages de modification de données reposant sur l’interrogation de SQL Server. Les messages reçus pour cette opération ne sont pas fortement typées.  
  
-   **TypedPolling** opération pour recevoir des messages de modification de données reposant sur l’interrogation de SQL Server. Les messages reçus pour cette opération sont fortement typées.  
  
-   **Notification** opération pour recevoir des notifications de requête à partir de SQL Server.  
  
> [!NOTE]
>  L’adaptateur prend également en charge une **XmlPolling** opération pour activer l’interrogation sur la base de données SQL Server à l’aide des instructions SELECT et les procédures stockées qui contiennent une clause FOR XML entrante. Toutefois, l’adaptateur n’expose pas une opération entrante spécifique pour ce. Pour plus d’informations sur XmlPolling, consultez [recevoir des messages d’interrogation à l’aide des instructions SELECT avec la Clause FOR XML à partir de SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-using-select-with-for-xml-clause-with-the-sql-adapter.md).  
  
 Pour plus d’informations sur ces opérations, consultez [se connecter à un système SAP à l’aide de l’adaptateur](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md).  
  
> [!NOTE]
>  À l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], vous pouvez parcourir les nœuds de catégorie et l’opération à l’aide d’une interface Windows.  
  
 Pour plus d’informations sur les métadonnées de navigation, consultez [obtenir les métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md).  
  
##### <a name="to-browse-outbound-operations-on-sql-server"></a>Pour parcourir des opérations sortantes sur SQL Server  
  
1.  Se connecter à SQL Server à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Consultez [se connecter à SQL Server dans Visual Studio à l’aide de la macro complémentaire Consume Adapter Service](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** répertorier, pour les opérations sortantes sélectionnez **Client (Outbound operations)**.  
  
3.  Le **sélectionner une catégorie** zone répertorie les artefacts disponibles dans la base de données SQL Server que vous vous connectez à. Cliquez sur un artefact pour afficher les opérations disponibles pour cet artefact dans le **catégories et opérations disponibles** boîte.  
  
    > [!TIP]
    >  Vous pouvez directement accéder à la catégorie « exécution » ou plusieurs nœuds de sous-catégorie dans l’arborescence, en tapant le nom de l’artefact, tandis que le focus est sur l’arborescence dans le **sélectionner une catégorie** boîte. Par exemple, pour accéder à la **employé** nœud de la table, conserver le focus sur le **Tables** nœud, puis tapez `Employee`.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Le nœud racine (/) est sélectionné, et les nœuds de catégorie générale disponibles sous le nœud racine sont répertoriées dans le **catégories et opérations disponibles** boîte.  
  
     ![Opérations et catégories disponibles au niveau de racine](../../adapters-and-accelerators/adapter-sql/media/3eef7b99-da8e-4b98-8b14-8e48fd7b3801.gif "3eef7b99-da8e-4b98-8b14-8e48fd7b3801")  
  
    > [!NOTE]
    >  Les opérations standard de SQL Server comme ExecuteReader, ExecuteScalar et ExecuteNonQuery sont également disponibles au niveau racine. Pour plus d’informations sur ces opérations, consultez [prise en charge de ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).  
  
4.  Pour afficher les procédures disponibles dans la base de données SQL Server, cliquez sur le **procédures** nœud. Dans l’illustration suivante, le **procédures** nœud est sélectionné dans le **sélectionner une catégorie** zone et les procédures correspondantes sont répertoriés dans le **catégories et opérations disponibles zone**.  
  
     ![Parcourir les procédures de SQL Server](../../adapters-and-accelerators/adapter-sql/media/e3b1a070-4077-4e4d-bfc7-558df9b8b9d5.gif "e3b1a070-4077-4e4d-bfc7-558df9b8b9d5")  
  
    > [!NOTE]
    >  Le même ensemble de procédures qui sont répertoriés sous la **procédures** nœud sont également disponibles dans le **fortement typée procédures** nœud. La différence réside dans le mode de génération de schéma. Pour une procédure sous la **procédure** nœud, le schéma est faiblement typé. Toutefois, pour une procédure sous la **fortement typée procédure** nœud, le schéma est fortement typé. Schéma fortement typé est utile si vous souhaitez mapper le schéma d’une opération à une autre opération à l’aide du Mappeur BizTalk, car le schéma n’est disponible au moment du design lors de la création du projet BizTalk. Pour connaître les procédures faiblement typée, le schéma de la procédure est reçu au moment de l’exécution en tant que partie du message de réponse.  
  
5.  Pour afficher les tables dans la base de données SQL Server, cliquez sur le **Tables** nœud. Vous pouvez également développer le **Tables** nœud.  
  
6.  Pour afficher les opérations prises en charge sur la table, cliquez sur un nom de table.  
  
     L’illustration suivante montre une liste de tables dans le **sélectionner une catégorie** boîte. Le **catégories et opérations disponibles** zone répertorie les opérations prises en charge pour une table sélectionnée.  
  
     ![Parcourir les tables dans une base de données SQL Server](../../adapters-and-accelerators/adapter-sql/media/3966f3b9-85a0-4354-8ed4-da5ae74c9885.gif "3966f3b9-85a0-4354-8ed4-da5ae74c9885")  
  
    > [!NOTE]
    >  Si une table SQL Server contient des colonnes de type varchar (max), nvarchar (max) et varbinary (max), l’adaptateur expose également une opération spécifique pour mettre à jour les données de cette colonne. Le nom de cette opération est défini à < nom_colonne >. Par exemple, si la table possède une colonne « Job_Description » de type varchar (max), le nom de l’opération est « SetJob_Description ».  
  
7.  Pour afficher les vues dans la base de données SQL Server, cliquez sur le **vues** nœud. Vous pouvez également développer le **vues** nœud.  
  
8.  Pour afficher les opérations prises en charge sur la vue, cliquez sur un nom de la vue.  
  
     L’illustration suivante montre une liste des vues dans le **sélectionner une catégorie** boîte. Le **catégories et opérations disponibles** zone répertorie les opérations prises en charge pour une vue sélectionnée.  
  
     ![Parcourir les vues dans une base de données SQL Server](../../adapters-and-accelerators/adapter-sql/media/67362fb2-35fb-4afb-8ff6-e519b26bd187.gif "67362fb2-35fb-4afb-8ff6-e519b26bd187")  
  
    > [!NOTE]
    >  Si une vue contient des colonnes de type varchar (max), nvarchar (max) et varbinary (max), l’adaptateur expose également une opération spécifique pour mettre à jour les données de cette colonne. Le nom de cette opération est défini à < nom_colonne >. Par exemple, si la table possède une colonne « Job_Description » de type varchar (max), le nom de l’opération est « SetJob_Description ».  
  
9. Pour afficher la liste des fonctions scalaires définies dans la base de données SQL Server dans le **catégories et opérations disponibles** , cliquez sur le **fonctions scalaires** nœud.  
  
     Dans l’illustration suivante, le **fonctions scalaires** nœud est sélectionné dans le **sélectionner une catégorie** zone et les fonctions correspondantes sont répertoriés dans le **catégories et opérations disponibles**  boîte.  
  
     ![Parcourir les fonctions scalaires dans SQL Server](../../adapters-and-accelerators/adapter-sql/media/78b9f720-2cb2-44a8-b8cc-49e4fb608a1f.gif "78b9f720-2cb2-44a8-b8cc-49e4fb608a1f")  
  
10. Pour afficher la liste de table valued fonctions définies dans la base de données SQL Server dans le **catégories et opérations disponibles** , cliquez sur le **fonctions table** nœud.  
  
     Dans l’illustration suivante, le **fonctions table** nœud est sélectionné dans le **sélectionner une catégorie** zone et les fonctions correspondantes sont répertoriés dans le **catégories disponibles et opérations** boîte.  
  
     ![Parcourir les fonctions table dans SQL Server](../../adapters-and-accelerators/adapter-sql/media/b007059f-280e-40d7-9553-eca4216296f4.gif "b007059f-280e-40d7-9553-eca4216296f4")  
  
##### <a name="to-browse-inbound-operations-on-sql-server"></a>Pour parcourir les opérations entrantes sur SQL Server  
  
1.  Se connecter à SQL Server à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Consultez [se connecter à SQL Server dans Visual Studio à l’aide de la macro complémentaire Consume Adapter Service](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** pour les opérations entrantes, la liste, sélectionnez **Service (opérations entrantes)**.  
  
3.  Toutes les opérations entrantes prises en charge par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sont disponibles sur le nœud racine. Cliquez sur le nœud racine (/) pour afficher les opérations d’entrée disponibles.  
  
     ![Opérations prises en charge par l’adaptateur entrantes](../../adapters-and-accelerators/adapter-sql/media/133732c0-ca8f-4e57-8a70-ba4fb561a37b.gif "133732c0-ca8f-4e57-8a70-ba4fb561a37b")  
  
## <a name="searching-for-operations"></a>Recherche d’opérations  
 Vous pouvez utiliser la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour rechercher les artefacts dans la base de données SQL Server. Lors de la recherche de métadonnées de SQL Server, le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:  
  
-   Prend en charge les caractères génériques et d’échappement dans l’expression de recherche.  
  
-   Permet la recherche immédiatement sous le nœud à partir duquel l’opération de recherche est effectuée. Par exemple, pour rechercher une table, vous devez être recherche sous \Table. Recherche de plusieurs niveaux n’est pas pris en charge.  
  
 Le tableau suivant répertorie les caractères spéciaux qui peuvent être utilisés pour la recherche d’artefacts et leur interprétation par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
|Caractère spécial|Interprétation|Exemple|  
|-----------------------|--------------------|-------------|  
|_ (souligné)|Correspond à exactement un caractère|« A_ » correspond à AB, CA, Active Directory.|  
|%|Correspond à zéro ou plusieurs caractères|« Un % » correspond à un, AB, CA.|  
|[ ]|-Une signification spéciale % et _ d’échappement<br />-Spécifie une plage ou un jeu de caractères à être présents|-% [%] correspond à tous les noms qui incluent un symbole %.<br />-[a-f] correspond à tous les noms contenant des caractères entre (et notamment) 'a' et 'f'.<br />-[abc] correspond à tous les noms contenant des caractères « a », « b » et « c ».|  
|[^]|Spécifie une plage ou un ensemble de caractères ne devant ne pas être présents|-[^ a-f] correspond à tous les noms qui n’ont pas de caractères entre (et notamment) 'a' et 'f'.<br />-[^ abc] correspond à tous les noms qui n’ont pas de caractères « a », « b » et « c ».|  
  
> [!NOTE]
>  Caractère d’échappement est un caractère placé devant un caractère générique pour indiquer que le caractère générique doit être interprété comme un caractère normal et non comme un caractère générique.  
  
 Pour plus d’informations, consultez [obtenir les métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md).  
  
 Pour rechercher des métadonnées dans SQL Server à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], procédez comme suit.  
  
#### <a name="to-search-metadata-in-sql-server"></a>Pour rechercher des métadonnées dans SQL Server  
  
1.  Se connecter à SQL Server à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Consultez [se connecter à SQL Server dans Visual Studio à l’aide de la macro complémentaire Consume Adapter Service](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** , sélectionnez le type de contrat selon si vous recherchez des opérations entrantes et sortantes.  
  
3.  Dans le **sélectionner une catégorie** , cliquez sur le nœud de catégorie sous lequel vous souhaitez rechercher un objet spécifique. Par exemple, pour rechercher une table, cliquez sur le **Tables** nœud.  
  
4.  Dans le **recherche dans la catégorie** , tapez une expression de recherche pour rechercher un objet spécifique. Par exemple, pour rechercher des tables qui ont « Client » dans leur nom, tapez `%Customer%`.  
  
    > [!NOTE]
    >  La chaîne de recherche respecte la casse.  
  
5.  Pour démarrer la recherche, cliquez sur le bouton avec l’icône de flèche droite. Une fois la recherche terminée, le **catégories et opérations disponibles** zone répertorie les artefacts qui répondent aux critères de recherche.  
  
     La figure suivante illustre les tables de SQL Server qui contiennent « Client » dans leur nom.  
  
     ![Rechercher des métadonnées dans SQL Server](../../adapters-and-accelerators/adapter-sql/media/62c24ed3-f4e5-47de-8e8d-35af96e6c5ec.gif "62c24ed3-f4e5-47de-8e8d-35af96e6c5ec")  
  
## <a name="generating-schema-for-biztalk-projects"></a>Génération de schéma pour les projets BizTalk  
 Vous pouvez utiliser la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer le schéma pour les artefacts sélectionnés de SQL Server. Une fois que vous avez parcouru et rechercher les artefacts que vous voulez appeler, vous pouvez générer le schéma pour ces artefacts et envoyer des messages, conforme au schéma, pour SQL Server.  
  
> [!NOTE]
>  Vous pouvez sélectionner des nœuds de catégorie pour retourner toutes les opérations de cette catégorie sub-Tree, par exemple, vous pouvez sélectionner une table entière (à la génération du schéma pour toutes les opérations dans la table) ou une sélection des opérations spécifiques sur une table (par exemple, Insert et Delete) à génération du schéma pour seulement les opérations sur une table. Pour plus d’informations sur les nœuds, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-sql/metadata-node-ids2.md).  
  
#### <a name="to-generate-schema-for-sql-server-artifacts"></a>Pour générer le schéma pour les artefacts de SQL Server  
  
1.  Se connecter à SQL Server à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. Consultez [se connecter à SQL Server dans Visual Studio à l’aide de la macro complémentaire Consume Adapter Service](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md) pour obtenir des instructions.  
  
    > [!IMPORTANT]
    >  Pour générer le schéma pour effectuer des opérations à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] vous devez définir le **EnableBizTalkCompatibilityMode** liaison de propriété **True**. Vous devez définir cette propriété de liaison lors de l’établissement d’une connexion à la base de données SQL Server.  
  
2.  À partir de la **type de contrat Select** , sélectionnez le type de contrat selon si vous générez le schéma pour les opérations entrantes ou sortantes.  
  
3.  Cliquez sur le nœud de catégorie pour laquelle vous souhaitez générer des métadonnées. Par exemple, si vous souhaitez générer des métadonnées pour une table, cliquez sur **Tables**.  
  
4.  Développez le nœud de catégorie et sélectionnez l’élément spécifique au sein de ce nœud pour lequel vous souhaitez générer des métadonnées. Par exemple, pour générer des métadonnées pour les opérations sur la table « CustomerTable », développez le **Tables** nœud, puis cliquez sur **CustomerTable**.  
  
5.  Dans le **catégories et opérations disponibles** , sélectionnez les opérations que vous souhaitez effectuer sur SQL Server, puis cliquez sur **ajouter**. Opérations sélectionnées sont répertoriées dans le **ajouté des catégories et opérations** boîte. Par exemple, pour effectuer des opérations d’insertion et Select sur la table « CustomerTable », cliquez sur le nom de l’opération, puis cliquez sur **ajouter**.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], qui répertorie les opérations sélectionnées.  
  
     ![Récupérer les métadonnées à partir de SQL Server](../../adapters-and-accelerators/adapter-sql/media/a6a95291-f6ed-46d1-bacc-2dfc27638117.gif "a6a95291-f6ed-46d1-bacc-2dfc27638117")  
  
     Si vous souhaitez générer le schéma pour plusieurs opérations, il est possible des définitions d’élément en double parmi ces schémas peut provoquer un échec de la compilation du projet BizTalk. Par exemple, considérez un scénario où vous générez le schéma pour une opération « Op1 ». Le schéma de « Op1 » contient un paramètre de type de données « CT1 ». Après avoir généré le schéma pour « Op1 » que vous fermez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et rouvrez-le pour générer le schéma d’une autre opération « Op2 ». Supposons que « Op2 » contient également un paramètre de type de données « CT1 ». Après avoir quitté le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et compilez le projet, vous obtenez des erreurs de compilation, car le type de données complexe « CT1 » est défini à deux reprises dans différents fichiers XSD. Dans ce cas, nous recommandons ce qui suit :  
  
    -   Génération du schéma pour toutes les opérations en une seule exécution de [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Cela garantit que le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ne génère qu’une seule définition pour le type de données complexe « CT1 ».  
  
    -   Si vous souhaitez générer le schéma pour plusieurs opérations entre les différentes exécutions de [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], veillez à sélectionner le **générer des types de schéma unique** case, afin que les fichiers XSD générés contiennent des espaces de noms uniques pour le « CT1 » de type de données complexes.  
  
6.  Cliquez sur **OK**. Le fichier de schéma est enregistré avec une extension .xsd dans le même emplacement que le projet BizTalk.  
  
    > [!NOTE]
    >  Si vous utilisez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer des métadonnées pour les artefacts de SQL Server, par défaut, les fichiers sont créés avec une convention d’affectation de noms spécifique. Le fichier WSDL généré contient un **fileNameHint** balise annotation qui inclut le nom qui doit être affecté au fichier XSD. Par exemple, un indicateur de nom de fichier pour un fichier de schéma pour l’opération de table suit la convention TableOperation. \<schéma >. \<tablename >. Si vous souhaitez personnaliser le nom du fichier XSD généré, vous pouvez fournir un préfixe dans le **préfixe de nom de fichier** boîte. Enfin, le nom d’un fichier XSD est arrivé à en tant que préfixe du nom de fichier + fileNameHint + entier unique (si nécessaire, pour vous assurer que le nom de fichier est unique).  
  
    > [!NOTE]
    >  Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] crée également un fichier de liaison (un fichier XML) qui contient les propriétés de liaison que vous avez spécifié quand générer le schéma pour une opération et l’action SOAP pour appeler l’opération. Vous pouvez importer ce fichier de liaison dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] set de la console d’Administration pour créer un port personnalisé WCF ou BizTalk SQL port de l’adaptateur avec l’URI de connexion, les propriétés de liaison et l’action SOAP. Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à utiliser l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).
  
     Vous avez correctement généré les métadonnées pour les artefacts de SQL Server. Vous pouvez utiliser les métadonnées pour envoyer des messages à SQL Server pour effectuer des opérations spécifiques. Consultez [BizTalk de développer les applications à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md) pour plus d’informations sur la façon d’effectuer ces opérations.  
  
## <a name="generating-a-wcf-client-or-wcf-service-contract-using-the-add-adapter-service-reference-plug-in"></a>Génération d’un Client WCF ou le contrat de Service WCF à l’aide de l’ajouter une référence de Service d’adaptateur plug-in  
 Vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer le code du client WCF pour les opérations sortantes ou code de service WCF pour les opérations entrantes.  
  
#### <a name="to-generate-wcf-client-class-or-service-contract-for-sql-server-operations"></a>Pour générer le contrat de service ou une classe de client pour les opérations de SQL Server WCF  
  
1.  Dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], à partir de la **type de contrat Select** liste déroulante, sélectionnez le type de contrat, selon que vous allez effectuer les opérations entrantes et sortantes.  
  
2.  Parcourir ou rechercher des catégories (par exemple, une table de base de données) ou pour des opérations spécifiques pour lesquels vous voulez générer un client WCF (ou le contrat de service WCF).   
    Par exemple, pour rechercher les opérations dans la table Employee, dans le **sélectionner une catégorie** zone :  
  
    1.  Développez le nœud racine (**/**) pour afficher les catégories dans lesquelles les opérations sont signalées pour une base de données SQL Server.  
  
    2.  Sous le nœud racine, développez le **Tables** nœud pour afficher les tables disponibles.  
  
3.  Cliquez sur le **employé** nœud de la table, puis, dans le **catégories et opérations disponibles** , sélectionnez les opérations ou les catégories pour lequel vous voulez générer un client WCF (ou le contrat de service WCF), puis Cliquez sur **ajouter**. Opérations sélectionnées sont répertoriées dans le **ajouté des catégories et opérations** boîte.  
  
     L’illustration suivante montre la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] avec les opérations d’insertion et sélectionnez pour la table Employee sélectionné.  
  
     ![Générer le contrat de service ou client WCF](../../adapters-and-accelerators/adapter-sql/media/sql-adap-add-adap-serv-ref.gif "sql_adap_add_adap_serv_ref")  
  
    > [!IMPORTANT]
    >  Selon les opérations sortantes (ou catégories) que vous sélectionnez, plus de WCF d’une classe de client peut être générée. Pour plus d’informations, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).  
  
4.  La plupart des scénarios, les options de sérialisation par défaut sont suffisantes ; Toutefois, si nécessaire, vous pouvez contrôler plusieurs aspects sur le code qui est généré et le type de sérialiseur utilisé. Pour définir ces options :  
  
    1.  Cliquez sur **Options avancées** pour ouvrir le **Options avancées** boîte.  
  
    2.  Dans le **Options avancées** sous **choisir les options pour le proxy généré**, sélectionnez les options souhaitées. Par exemple, vous pouvez choisir les méthodes asynchrones sont générés pour le client WCF ou désactiver la génération d’un fichier de configuration.  
  
    3.  Sous **sérialiseur** sélectionner le sérialiseur doit être utilisé.  
  
     L’illustration suivante montre le **Options avancées** zone avec les sélections par défaut (**automatique** est sélectionné pour le sérialiseur et aucune autre option est sélectionnées).  
  
     ![Les Options avancées zone des paramètres par défaut](../../adapters-and-accelerators/adapter-oracle-database/media/r2-net-adapters-oracle-msb-advanced-options.gif "R2_NET_Adapters_Oracle_MSB_Advanced_Options")  
  
     Les options que vous pouvez configurer dans le **Options avancées** zone sont équivalentes à certaines des options disponibles lorsque vous utilisez le service Model Metadata Utility Tool (svcutil.exe). Pour plus d’informations sur ces options, consultez [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx). 
  
5.  Cliquez sur **OK**. Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] enregistre la classe de client WCF (ou l’interface de service WCF) et le code d’assistance pour les opérations et les catégories que vous avez sélectionnées dans votre répertoire de projet. Par défaut, un fichier de configuration est également enregistré. Légèrement différents fichiers sont générés pour les opérations entrantes et sortantes ; Pour plus d’informations, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).  
  
 Vous pouvez sélectionner n’importe quel nœud qui est répertorié dans le **catégories et opérations disponibles** boîte. Si vous sélectionnez un nœud de catégorie toutes les opérations disponibles sous ce nœud et ses sous-nœuds seront sélectionnés. Par exemple, pour générer un client WCF pour toutes les opérations exposées en surface pour la table Employee, vous pouvez sélectionner le nœud de l’employé.  
  
## <a name="see-also"></a>Voir aussi  
 [Obtenir les métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)