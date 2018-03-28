---
title: Parcourir, rechercher et d’obtenir des métadonnées pour des opérations IDOC dans SAP | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF client, generating for IDOC operations
- IDOCs, searching
- searching, IDOCs
- IDOCs, browsing
- browsing, IDOCs
- IDOC operations, generating schema for
- IDOC operations
ms.assetid: 44d05129-ce06-4a10-bf28-9d3519a02a7a
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b4c82ecf945e85c8e4c9b5f365c808598fcbbf3a
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="browse-search-and-get-metadata-for-idoc-operations-in-sap"></a>Parcourir, rechercher et d’obtenir des métadonnées pour des opérations IDOC dans SAP
Cette section fournit des instructions sur la façon de parcourir, rechercher et récupérer les métadonnées à partir de SAP pour à l’aide des opérations IDOC [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. La plupart des instructions est les même pour toute l’interface utilisateur de trois. Là où les procédures d’applicables, distinctes sont fournies pour l’interface utilisateur approprié.  
  
 Avant d’effectuer les étapes décrites dans les sections suivantes, vous devez avoir :  
  
-   Créé un [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] projet.  
  
-   Le système SAP en utilisant le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Pour obtenir des instructions, consultez [se connecter au système SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md) Notez que, avant de se connecter à un système SAP pour générer le schéma ou un client WCF pour IDOC, vous devez définir certaines propriétés de liaison.  
  
    -   GenerateFlatFileCompatibleIdocSchema  
  
    -   ReceiveIdocFormat  
  
    -   FlatFileSegmentIndicator  
  
     Ces propriétés déterminent la façon dont les métadonnées pour l’IDOC sont récupérées à partir d’un système SAP. Pour plus d’informations sur ces propriétés, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md). Pour obtenir des instructions sur la façon de définir les propriétés de liaison, consultez [configurer les propriétés de liaison de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md).  
  
## <a name="browsing-idocs-in-an-sap-system"></a>Navigation IDOC dans un système SAP  
 Lors de l’exploration à l’aide de métadonnées [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces séparer des opérations pour envoyer et recevoir des IDOC à partir d’un système SAP.  
  
-   **Envoyer** et **réception**. Les clients de l’adaptateur peuvent d’effectuer ces opérations envoyer et recevoir des IDOC à partir d’un système SAP à l’aide d’un schéma fortement typé. L’adaptateur met en évidence ces opérations séparément pour chaque IDOC et sont disponible sous le nœud IDOC respectif.  
  
-   **SendIdoc** et **ReceiveIdoc**. Les clients de l’adaptateur peuvent d’effectuer ces opérations envoyer et recevoir des IDOC à partir d’un système SAP à l’aide d’un schéma faiblement typée. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uniquement met en évidence une **SendIdoc** et **ReceiveIdoc** opération pour toutes les IDOC. Ces opérations sont accessibles directement sous le **IDOC** nœud.  
  
 Les étapes suivantes pour rechercher les IDOCs dans un système SAP à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### <a name="to-browse-idocs-in-an-sap-system"></a>Pour rechercher les IDOCs dans un système SAP  
  
1.  Se connecter à un serveur SAP à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Consultez [connexion au système SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** liste déroulante, sélectionnez le type de contrat, selon que vous allez effectuer les opérations entrantes et sortantes, à l’aide de l’adaptateur.  
  
3.  Dans le **sélectionner une catégorie** , cliquez sur le nœud IDOC pour voir les types de message IDOC dans le **catégories et opérations disponibles** boîte. Ou bien, vous pouvez également voir les types de messages IDOC en développant le nœud IDOC.  
  
    > [!TIP]
    >  Vous pouvez directement accéder à la catégorie « exécution » ou plusieurs nœuds de sous-catégorie dans l’arborescence, en tapant le nom de l’artefact dans tandis que le focus est sur l’arborescence dans le **sélectionner une catégorie** boîte. Par exemple, pour accéder à la **ACC_BILLING** IDOC type de message, conserver le focus sur le **IDOC** nœud, puis tapez `ACC_BILLING`.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] l’IDOC affichage de la liste des types de messages. Le nœud racine du IDOC met également en évidence un **SendIdoc** possibilité d’envoyer des IDOC de faiblement typé au système SAP.  
  
     ![Exploration des types de messages dans un IDOC](../../adapters-and-accelerators/adapter-sap/media/3b8701c2-0530-4577-817c-92af0cd9a770.gif "3b8701c2-0530-4577-817c-92af0cd9a770")  
  
    > [!NOTE]
    >  Pour obtenir un scénario entrant, les surfaces de nœud racine IDOC un **ReceiveIdoc** opération de réception faiblement typée IDOC.  
  
4.  Cliquez sur les types de messages IDOC pour voir le type IDOC pertinentes. L’illustration suivante montre la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] avec le type IDOC sous un IDOC notamment le type de message.  
  
     ![Recherche des types IDOC](../../adapters-and-accelerators/adapter-sap/media/fee70ed2-74c1-4c91-b2fd-3d281a335145.gif "fee70ed2-74c1-4c91-b2fd-3d281a335145")  
  
5.  Cliquez sur les types IDOC pour voir les différentes versions pour un type IDOC. L’illustration suivante montre la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] avec les versions d’un type IDOC particulier.  
  
     ![Recherche des versions d’un type IDOC](../../adapters-and-accelerators/adapter-sap/media/35603fac-ff48-40b1-bb51-bd0548715cd3.gif "35603fac-ff48-40b1-bb51-bd0548715cd3")  
  
6.  Cliquez sur la version d’un type IDOC pour voir les opérations prises en charge sur ce type IDOC. L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] avec l’opération prise en charge pour une version de type IDOC particulière.  
  
     ![Parcourir des opérations pour un type IDOC](../../adapters-and-accelerators/adapter-sap/media/f37624b4-f1f2-4d44-8708-01eb51a2d2a7.gif "f37624b4-f1f2-4d44-8708-01eb51a2d2a7")  
  
## <a name="searching-idocs-in-an-sap-system"></a>Rechercher les IDOCs dans un système SAP  
 Lors de la recherche dans un système SAP à l’aide de métadonnées des IDOC [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]:  
  
-   Prend en charge les caractères génériques dans l’expression de recherche.  
  
-   Permet la recherche immédiatement sous le nœud à partir duquel l’opération de recherche est effectuée.  
  
 Le tableau suivant répertorie les caractères spéciaux qui peuvent être utilisés pour la recherche et de leur interprétation par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
|Caractère spécial|Interpretation|  
|-----------------------|--------------------|  
|+ (plus)|Correspond à exactement un caractère.<br /><br /> Par exemple, A + correspond à AB, CA, Active Directory|  
|* (astérisque)|Correspond à zéro ou plusieurs caractères.<br /><br /> Par exemple, A * correspond à un, AB, ABC.|  
  
 Pour plus d’informations sur les caractères spéciaux pris en charge par l’adaptateur, consultez [exposent les paramètres de la carte sous la forme d’une propriété de liaison à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/expose-adapter-settings-as-a-binding-property-using-the-wcf-lob-adapter-sdk.md).
  
 Les étapes suivantes pour rechercher les IDOCs dans un système SAP à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### <a name="to-search-idocs-in-an-sap-system"></a>Pour rechercher les IDOCs dans un système SAP  
  
1.  Se connecter à un serveur SAP à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Consultez [se connecter au système SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** liste déroulante, sélectionnez le type de contrat selon si vous recherchent pour les opérations entrantes ou sortantes, à l’aide de l’adaptateur.  
  
3.  Dans le **sélectionner une catégorie** , cliquez sur le nœud IDOC.  
  
    > [!IMPORTANT]
    >  Vous pouvez rechercher des IDOC uniquement au niveau racine.  
  
4.  Dans le **recherche dans la catégorie** texte, entrez une expression de recherche pour rechercher un type de message IDOC spécifique. Par exemple, pour rechercher des IDOC qui ont « MATMAS » dans leur nom, tapez * MATMAS\* dans la zone de texte.  
  
5.  Cliquez sur le bouton avec l’icône de flèche droite pour démarrer la recherche. Une fois la recherche terminée, le **catégories et opérations disponibles** zone répertorie l’IDOC qui répondent aux critères de recherche.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] répertoriant l’IDOC le résultat de la recherche.  
  
     ![Rechercher les IDOCs dans un système SAP](../../adapters-and-accelerators/adapter-sap/media/tut1-lesson3-step3-idocsearch.gif "Tut1-Lesson3-Step3-IDOCSearch")  
  
## <a name="generating-schema-for-biztalk-projects"></a>Génération de schéma pour les projets BizTalk  
 Vous pouvez utiliser la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer le schéma pour les artefacts SAP sélectionnés. Une fois que vous avez parcouru et rechercher les artefacts que vous voulez appeler, vous pouvez générer le schéma pour ces artefacts et envoyer des messages, conforme au schéma, pour le système SAP.  
  
> [!NOTE]
>  Vous pouvez sélectionner des nœuds de catégorie pour retourner toutes les opérations de cette catégorie sub-Tree, par exemple, vous pouvez sélectionner un type IDOC (pour générer le schéma pour toutes les versions d’IDOC dans ce groupe) ou sélectionnez une version spécifique d’IDOC pour générer le schéma pour que cette version des IDOC. Pour plus d’informations sur les nœuds, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).  
  
#### <a name="to-retrieve-metadata-for-idocs"></a>Pour récupérer des métadonnées des IDOC  
  
1.  Se connecter à un serveur SAP à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. Consultez [se connecter au système SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** liste déroulante, sélectionnez le type de contrat, selon que vous allez effectuer les opérations entrantes et sortantes, à l’aide de l’adaptateur.  
  
3.  Dans le **sélectionner une catégorie** , cliquez sur le type de message IDOC ou le type IDOC pour lequel vous souhaitez générer des métadonnées.  
  
4.  Dans le **catégories et opérations disponibles** , sélectionnez le type IDOC ou les opérations prises en charge pour lequel vous souhaitez générer des métadonnées, cliquez sur **ajouter**. Les types IDOC sélectionnés ou les opérations sont répertoriées dans le **ajouté des catégories et opérations** boîte.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] répertoriant les IDOCs sélectionnés.  
  
     ![Récupérer les métadonnées des IDOC](../../adapters-and-accelerators/adapter-sap/media/d9765c62-68b2-4313-9292-9265ab095e2e.gif "d9765c62-68b2-4313-9292-9265ab095e2e")  
  
     Si vous souhaitez générer le schéma pour plusieurs opérations, il est possible des définitions d’élément en double parmi ces schémas peut provoquer un échec de la compilation du projet BizTalk. Par exemple, considérez un scénario où vous générez le schéma pour une opération « Op1 ». Le schéma de « Op1 » contient un paramètre de type de données complexe « CT1 ». Après avoir généré le schéma pour « Op1 » que vous fermez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et rouvrez-le pour générer le schéma d’une autre opération « Op2 ». Supposons que « Op2 » contient également un paramètre de type de données complexe « CT1 ». Après avoir quitté le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et compilez le projet, vous obtenez des erreurs de compilation, car le type de données complexe « CT1 » est défini à deux reprises dans différents fichiers XSD. Dans ce cas, nous recommandons ce qui suit :  
  
    -   Génération du schéma pour toutes les opérations en une seule exécution de [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Cela garantit que le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ne génère qu’une seule définition pour le type de données complexe « CT1 ».  
  
    -   Si vous souhaitez générer le schéma pour plusieurs opérations entre les différentes exécutions de [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], veillez à sélectionner le **générer des types de schéma unique** case à cocher pour que les fichiers XSD générés contiennent des espaces de noms uniques pour le complexe type de données « CT1 ».  
  
5.  Cliquez sur **OK**. Le fichier de schéma est enregistré avec une extension .xsd dans le même emplacement que le projet IDOC.  
  
    > [!NOTE]
    >  Si vous utilisez [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], par défaut, les fichiers sont créés avec la convention d’affectation de noms « SAPBinding\<n\>.xsd », où « n » peut être de 1, 2, etc. selon le nombre de fichiers de schéma créés. Ou bien, vous pouvez fournir un nom personnalisé pour les fichiers de schéma en entrant un nom dans la **préfixe de nom de fichier** zone de texte. Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] maintenant crée des fichiers de schéma avec la convention d’affectation de noms \<préfixe de nom de fichier\>\<n\>.xsd.  
  
    > [!NOTE]
    >  Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] crée également un fichier de liaison (un fichier XML) qui contient les propriétés de liaison que vous avez spécifié lors de la génération du schéma pour une opération et l’action SOAP pour appeler l’opération. Vous pouvez importer ce fichier de liaison dans la console Administration de BizTalk Server pour créer un port personnalisé WCF avec l’URI, les propriétés de liaison de connexion et l’action SOAP définie. Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md).  
  
6.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="generating-a-wcf-client-for-idoc-operations-using-the-add-adapter-service-reference-plug-in"></a>Génération d’un Client WCF pour les opérations IDOC à l’aide de l’ajouter une référence de Service d’adaptateur plug-in  
 Vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer le code du client WCF pour envoyer des IDOC à un système SAP ou un contrat de service WCF pour recevoir des IDOC à partir d’un système SAP.  
  
#### <a name="to-generate-a-wcf-client-or-a-wcf-service-contract-for-idocs"></a>Pour générer un client WCF ou un contrat de service WCF pour IDOC  
  
1.  Dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], à partir de la **type de contrat Select** liste déroulante, sélectionnez le type de contrat, selon que vous allez effectuer entrants (réception IDOC) ou des opérations sortantes (envoi IDOC).  
  
2.  Dans le **sélectionner une catégorie** , développez le **IDOC** nœud, puis parcourir ou rechercher le type de message IDOC ou le type IDOC que vous souhaitez envoyer ou recevoir.  
  
3.  Dans le **catégories et opérations disponibles** , sélectionnez le type IDOC ou les opérations prises en charge pour lequel vous souhaitez générer un client WCF (ou le contrat de service WCF), puis cliquez sur **ajouter**. Opérations sélectionnées sont répertoriées dans le **ajouté des catégories et opérations** boîte. Vous pouvez sélectionner n’importe quel nœud qui est répertorié dans le **catégories et opérations disponibles** boîte. Si vous sélectionnez un nœud de catégorie, puis toutes les opérations disponibles sous ce nœud et ses sous-nœuds seront ajoutés.  
  
    > [!IMPORTANT]
    >  Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère une classe de client WCF unique (ou le contrat de service WCF) pour chaque type IDOC. Selon les catégories et les opérations que vous sélectionnez, plus d’une classe de client WCF peut être générée. Pour plus d’informations, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
4.  La plupart des scénarios, les options de sérialisation par défaut sont suffisantes ; Toutefois, si nécessaire, vous pouvez contrôler plusieurs aspects sur le code qui est généré et le type de sérialiseur utilisé. Pour définir ces options :  
  
    1.  Cliquez sur **Options avancées** pour ouvrir le **Options avancées** boîte.  
  
    2.  Dans le **Options avancées** sous **choisir les options pour le proxy généré**, sélectionnez les options souhaitées. Par exemple, vous pouvez choisir les méthodes asynchrones sont générés pour le client WCF ou désactiver la génération d’un fichier de configuration.  
  
    3.  Sous **sérialiseur** sélectionner le sérialiseur doit être utilisé.  
  
     L’illustration suivante montre le **Options avancées** zone avec les sélections par défaut (**automatique** est sélectionné pour le sérialiseur et aucune autre option est sélectionnées).  
  
     ![Les Options avancées zone des paramètres par défaut](../../adapters-and-accelerators/adapter-oracle-database/media/r2-net-adapters-oracle-msb-advanced-options.gif "R2_NET_Adapters_Oracle_MSB_Advanced_Options")  
  
     Les options que vous pouvez configurer dans le **Options avancées** zone sont équivalentes à certaines des options disponibles lorsque vous utilisez le service Model Metadata Utility Tool (svcutil.exe). Pour plus d’informations sur ces options, consultez [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx).
  
5.  Cliquez sur **OK**. Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] enregistre la classe de client WCF (ou l’interface de service WCF) et le code d’assistance pour les opérations et les catégories que vous avez sélectionnées dans votre répertoire de projet. Par défaut, un fichier de configuration est également enregistré. Légèrement différents fichiers sont générés pour les opérations entrantes et sortantes ; Pour plus d’informations, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Obtenir les métadonnées pour les opérations SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)