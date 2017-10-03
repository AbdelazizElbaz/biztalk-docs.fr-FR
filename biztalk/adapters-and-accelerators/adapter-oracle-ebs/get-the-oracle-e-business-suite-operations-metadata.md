---
title: "Obtenir les métadonnées des opérations Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 566ae086-183a-47db-8f93-12b5903c85c3
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f49bda367f9929d3ab320ac7bbaeee6ed49de2a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="get-the-oracle-e-business-suite-operations-metadata"></a>Obtenir les métadonnées des opérations Oracle E-Business Suite
Vous pouvez utiliser la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer le schéma pour les artefacts d’Oracle E-Business Suite sélectionnés. Après avoir parcouru et rechercher les artefacts que vous voulez appeler, vous pouvez générer le schéma pour ces artefacts et envoyer des messages, conforme au schéma, pour Oracle E-Business Suite.  
  
> [!NOTE]
>  Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] présentes essentiellement la même interface lors de la navigation et de la recherche pour les opérations, afin des deux composants sont traités dans les rubriques mêmes.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez vous connecter à Oracle E-Business Suite avant d’extraire les métadonnées pour les opérations de la cible. Pour plus d’informations sur la façon de se connecter à Oracle de base de données lorsque vous utilisez la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [se connecter à Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md).  
  
## <a name="generating-schema-using-the-consume-adapter-service-add-in"></a>Génération de schéma à l’aide du Consume Adapter Service Add-in  
  
> [!NOTE]
>  Vous pouvez sélectionner des nœuds de catégorie pour retourner toutes les opérations de cette catégorie sub-Tree, par exemple, vous pouvez sélectionner le **programmes simultanés** nœud (pour la génération du schéma pour tous les programmes simultanés pour une application Oracle), ou vous pouvez Sélectionnez un programme simultané spécifique. Pour plus d’informations sur les nœuds, consultez l’ID de nœud de métadonnées.  
  
#### <a name="to-generate-schema-for-oracle-e-business-suite-artifacts"></a>Pour générer le schéma pour les artefacts d’Oracle E-Business Suite  
  
1.  Se connecter à Oracle E-Business Suite à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Consultez [se connecter à Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md) pour obtenir des instructions.  
  
    > [!IMPORTANT]
    >  Pour générer le schéma pour effectuer des opérations à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] vous devez définir le **EnableBizTalkCompatibilityMode** liaison de propriété **True**. Vous devez définir cette propriété de liaison lors de l’établissement d’une connexion à Oracle E-Business Suite.  
  
2.  À partir de la **type de contrat Select** , sélectionnez le type de contrat selon si vous générez le schéma pour les opérations entrantes ou sortantes.  
  
3.  Cliquez sur le nœud de catégorie pour laquelle vous souhaitez générer des métadonnées. Par exemple, si vous souhaitez générer des métadonnées pour un programme simultanée dans une application Oracle, cliquez sur **programmes simultanés**.  
  
4.  Développez le nœud de catégorie et sélectionnez l’élément spécifique au sein de ce nœud pour lequel vous souhaitez générer des métadonnées. Par exemple, pour générer des métadonnées pour les programmes simultanés pour l’application « Bancaire Center », développez le **programmes simultanés** nœud, puis cliquez sur **bancaire Center**.  
  
5.  Dans le **catégories et opérations disponibles** , sélectionnez les opérations que vous souhaitez appeler, puis cliquez sur **ajouter**. Opérations sélectionnées sont répertoriées dans le **ajouté des catégories et opérations** boîte. Par exemple, pour appeler « purger FTP bancaires » et « Get_Status » des programmes simultanés, cliquez sur le nom de l’opération, puis cliquez sur **ajouter**.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], qui répertorie les opérations sélectionnées.  
  
     ![Récupérer les métadonnées à partir d’Oracle E &#45; Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/media/df7de132-9177-4de7-a620-59dbd561efe5.gif "df7de132-9177-4de7-a620-59dbd561efe5")  
  
     Si vous souhaitez générer le schéma pour plusieurs opérations, il est possible des définitions d’élément en double parmi ces schémas peut provoquer un échec de la compilation du projet BizTalk. Par exemple, considérez un scénario où vous générez le schéma pour une opération « Op1 ». Le schéma de « Op1 » contient un paramètre de type de données « CT1 ». Après avoir généré le schéma pour « Op1 » que vous fermez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et rouvrez-le pour générer le schéma d’une autre opération « Op2 ». Supposons que « Op2 » contient également un paramètre de type de données « CT1 ». Après avoir quitté le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et compilez le projet, vous obtenez des erreurs de compilation, car le type de données complexe « CT1 » est défini à deux reprises dans différents fichiers XSD. Dans ce cas, nous recommandons ce qui suit :  
  
    -   Génération du schéma pour toutes les opérations en une seule exécution de [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Cela garantit que le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ne génère qu’une seule définition pour le type de données complexe « CT1 ».  
  
    -   Si vous souhaitez générer le schéma pour plusieurs opérations entre les différentes exécutions de [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], veillez à sélectionner le **générer des types de schéma unique** case, afin que les fichiers XSD générés contiennent des espaces de noms uniques pour le « CT1 » de type de données complexes.  
  
6.  Cliquez sur **OK**. Le fichier de schéma est enregistré avec une extension .xsd dans le même emplacement que le projet BizTalk.  
  
    > [!NOTE]
    >  Si vous utilisez le module additionnel Consume Adapter Service pour générer des métadonnées pour les opérations sur les artefacts d’Oracle, par défaut, les fichiers sont créés avec une convention d’affectation de noms spécifique : le nom de fichier XSD généré a les trois éléments suivants :  
    >   
    >  -   « OracleEBSBinding » ou le préfixe fourni dans le **préfixe de nom de fichier** boîte.  
    > -   Le nom inclus dans le **fileNameHint** balise d’annotation dans le fichier WSDL généré. Pour les opérations, l’indicateur de nom de fichier est le même que le groupe de l’opération. Pour les types complexes, l’indicateur de nom de fichier est l’espace de noms sans le préfixe « http://schemas.microsoft.com/OracleEBS/2008/05/ ». Par exemple, l’indicateur de nom de fichier pour une opération de table d’interface suit la convention \<InterfaceTables > + < app_short_name > + < interface_table_name >.  
    > -   (Facultatif) Nombre entier pour vous assurer que le nom de fichier est unique.  
    >   
    >  Enfin, le nom d’un fichier XSD est arrivé à en tant que < file_name_prefix > +\<fileNameHint > + n, où « n » est un entier unique.  
  
    > [!NOTE]
    >  Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] crée également un fichier de liaison (un fichier XML) qui contient les propriétés de liaison que vous avez spécifié quand générer le schéma pour une opération et l’action SOAP pour appeler l’opération. Vous pouvez importer ce fichier de liaison dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] set de la console d’Administration pour créer un port personnalisé WCF avec l’URI de connexion, les propriétés de liaison et l’action SOAP. Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).  
  
     Vous avez correctement généré les métadonnées pour les artefacts d’Oracle E-Business Suite. Vous pouvez utiliser les métadonnées pour envoyer des messages pour Oracle E-Business Suite pour effectuer des opérations spécifiques. Consultez [BizTalk de développer les applications à l’aide de l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md) pour plus d’informations sur la façon d’effectuer ces opérations.  
  
## <a name="generating-a-wcf-client-or-wcf-service-contract-using-the-add-adapter-service-reference-plug-in"></a>Génération d’un Client WCF ou le contrat de Service WCF à l’aide de l’ajouter une référence de Service d’adaptateur plug-in  
 Vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer le code du client WCF pour les opérations sortantes ou code de service WCF pour les opérations entrantes.  
  
#### <a name="to-generate-wcf-client-class-or-service-contract-for-oracle-e-business-suite-operations"></a>Pour générer le contrat de service ou une classe de client pour des opérations Oracle E-Business Suite WCF  
  
1.  Dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], à partir de la **type de contrat Select** liste déroulante, sélectionnez le type de contrat, selon que vous allez effectuer les opérations entrantes et sortantes.  
  
2.  Parcourir ou rechercher des catégories (par exemple, une table d’interface) ou pour des opérations spécifiques pour lesquels vous voulez générer un client WCF (ou le contrat de service WCF).   
    Par exemple, pour rechercher les opérations sur la table d’interface AR_ARCHIVE_PURGE_INTERIM, dans le **sélectionner une catégorie** zone :  
  
    1.  Développez le nœud racine (**/**) pour afficher les catégories dans lesquelles les opérations sont signalées pour Oracle E-Business Suite. La même table d’interface peut être disponible sous les **vue basée sur l’Application** nœud, ainsi que les **vue basée sur un artefact** nœud. Dans cet exemple, vous générez la classe de client WCF à partir de la **vue basée sur l’Application** nœud.  
  
    2.  Sous le nœud racine, développez le **vue basée sur l’Application** nœud pour afficher les applications disponibles dans Oracle E-Business Suite.  
  
    3.  Développez le nœud pour le **des comptes clients** application, puis développez le **Tables d’Interface** nœud.  
  
    4.  Cliquez sur le **AR_ARCHIVE_PURGE_INTERIM** nœud de table d’interface, puis, dans le **catégories et opérations disponibles** , sélectionnez les opérations pour lesquelles vous voulez générer un client WCF (ou un service WCF contrat), puis cliquez sur **ajouter**. Opérations sélectionnées sont répertoriées dans le **ajouté des catégories et opérations** boîte.  
  
         L’illustration suivante montre la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] avec les opérations Insert et Select de la table AR_ARCHIVE_PURGE_INTERIM sélectionnée.  
  
         ![Générer un contrat de service ou client WCF](../../adapters-and-accelerators/adapter-oracle-ebs/media/oraebs-adap-add-adap-serv-refs.gif "oraebs_adap_add_adap_serv_refs")  
  
        > [!IMPORTANT]
        >  Selon les opérations sortantes (ou catégories) que vous sélectionnez, plus de WCF d’une classe de client peut être générée. Pour plus d’informations, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).  
  
3.  La plupart des scénarios, les options de sérialisation par défaut sont suffisantes ; Toutefois, si nécessaire, vous pouvez contrôler plusieurs aspects sur le code qui est généré et le type de sérialiseur utilisé. Pour définir ces options :  
  
    1.  Cliquez sur **Options avancées** pour ouvrir le **Options avancées** boîte.  
  
    2.  Dans le **Options avancées** sous **choisir les options pour le proxy généré**, sélectionnez les options souhaitées. Par exemple, vous pouvez choisir les méthodes asynchrones sont générés pour le client WCF ou désactiver la génération d’un fichier de configuration.  
  
    3.  Sous **sérialiseur** sélectionner le sérialiseur doit être utilisé.  
  
     L’illustration suivante montre le **Options avancées** zone avec les sélections par défaut (**automatique** est sélectionné pour le sérialiseur et aucune autre option est sélectionnées).  
  
     ![Les Options avancées zone des paramètres par défaut](../../adapters-and-accelerators/adapter-oracle-database/media/r2-net-adapters-oracle-msb-advanced-options.gif "R2_NET_Adapters_Oracle_MSB_Advanced_Options")  
  
     Les options que vous pouvez configurer dans le **Options avancées** zone sont équivalentes à certaines des options disponibles lorsque vous utilisez le service Model Metadata Utility Tool (svcutil.exe). Pour plus d’informations sur ces options, consultez [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx).
  
4.  Cliquez sur **OK**. Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] enregistre la classe de client WCF (ou l’interface de service WCF) et le code d’assistance pour les opérations et les catégories que vous avez sélectionnées dans votre répertoire de projet. Par défaut, un fichier de configuration est également enregistré. Légèrement différents fichiers sont générés pour les opérations entrantes et sortantes ; Pour plus d’informations, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).  
  
 Vous pouvez sélectionner n’importe quel nœud qui est répertorié dans le **catégories et opérations disponibles** boîte. Si vous sélectionnez un nœud de catégorie toutes les opérations disponibles sous ce nœud et ses sous-nœuds seront sélectionnés. Par exemple, pour générer un client WCF pour toutes les opérations exposées en surface pour la table AR_ARCHIVE_PURGE_INTERIM, vous pouvez sélectionner le **AR_ARCHIVE_PURGE_INTERIM** nœud.  
  
## <a name="see-also"></a>Voir aussi  
 [Parcourir, rechercher et d’obtenir des métadonnées pour des opérations Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)