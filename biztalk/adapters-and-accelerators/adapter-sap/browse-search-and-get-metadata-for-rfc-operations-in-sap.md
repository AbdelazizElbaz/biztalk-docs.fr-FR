---
title: "Parcourir, rechercher et obtenir des métadonnées pour les opérations de RFC dans SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- browsing, RFCs
- RFCs, searching
- RFCs, browsing
- RFC operations, generating schema
- RFC operations
- searching, RFCs
- WCF client, generating a
ms.assetid: 68d9e7b2-b8ab-47f5-afda-2811f68e834b
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3aae3cb0963b4ccbc5c3e891af70706587f8e4b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="browse-search-and-get-metadata-for-rfc-operations-in-sap"></a>Parcourir, rechercher et obtenir des métadonnées pour les opérations de RFC dans SAP
Cette section fournit des instructions sur la façon de parcourir, rechercher et récupérer les métadonnées à partir de SAP pour les opérations de RFC à l’aide de [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. La plupart des instructions est les même pour toute l’interface utilisateur de trois. Là où les procédures d’applicables, distinctes sont fournies pour l’interface utilisateur approprié.  
  
 Avant d’effectuer les étapes décrites dans les sections suivantes, vous devez avoir :  
  
-   Créé un [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] projet.  
  
-   Le système SAP en utilisant le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Pour obtenir des instructions, consultez [se connecter au système SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md).  
  
## <a name="browsing-rfcs-in-an-sap-system"></a>Recherche de RFC dans un système SAP  
 Lors de l’exploration à l’aide de métadonnées [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces :  
  
-   RFC en tant qu’opérations pouvant être appelées sur le système SAP.  
  
-   Opération RfcGetAttributes, ce qui permet aux clients d’adaptateur obtenir des informations sur les paramètres de connexion RFC.  
  
 Pour plus d’informations sur la consultation des métadonnées SAP, consultez la rubrique [exposent les paramètres de la carte sous la forme d’une propriété de liaison à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/expose-adapter-settings-as-a-binding-property-using-the-wcf-lob-adapter-sdk.md).
  
 Les étapes suivantes pour rechercher les RFC dans un système SAP à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### <a name="to-browse-rfcs-in-an-sap-system"></a>Pour rechercher les RFC dans un système SAP  
  
1.  Se connecter à un serveur SAP à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Consultez [se connecter au système SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** liste déroulante, sélectionnez le type de contrat, selon que vous allez effectuer les opérations entrantes et sortantes, à l’aide de l’adaptateur.  
  
3.  Dans le **sélectionner une catégorie** , cliquez sur le nœud RFC pour afficher les groupes fonctionnels RFC le **catégories et opérations disponibles** boîte. Ou bien, vous pouvez également voir les groupes fonctionnels RFC en développant le nœud RFC.  
  
    > [!TIP]
    >  Vous pouvez directement accéder à la catégorie « exécution » ou plusieurs nœuds de sous-catégorie dans l’arborescence, en tapant le nom de l’artefact dans tandis que le focus est sur l’arborescence dans le **sélectionner une catégorie** boîte. Par exemple, pour accéder à la **base** groupe fonctionnel RFC, conserver le focus sur le **RFC** nœud, puis tapez `Basis`.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] qui répertorie les groupes fonctionnels RFC.  
  
     ![Exploration des groupes fonctionnels RFC](../../adapters-and-accelerators/adapter-sap/media/958cba26-1644-4700-a647-9eeb0273ebd1.gif "958cba26-1644-4700-a647-9eeb0273ebd1")  
  
4.  Cliquez sur les groupes fonctionnels RFC pour voir les documents RFC appropriées. L’illustration suivante montre la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] avec les RFC dans un groupe fonctionnel RFC particulier.  
  
     ![Recherche de RFC dans un groupe fonctionnel](../../adapters-and-accelerators/adapter-sap/media/bf725aa9-a547-4f20-8246-d9c8fedadb40.gif "bf725aa9-a547-4f20-8246-d9c8fedadb40")  
  
## <a name="searching-rfcs-in-an-sap-system"></a>Rechercher les RFC dans un système SAP  
 Lors de la recherche de métadonnées pour les RFC dans un système SAP à l’aide [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]:  
  
-   Prend en charge les caractères génériques dans l’expression de recherche.  
  
-   Permet la recherche immédiatement sous le nœud à partir duquel l’opération de recherche est effectuée.  
  
 Le tableau suivant répertorie les caractères spéciaux qui peuvent être utilisés pour la recherche et de leur interprétation par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
|Caractère spécial|Interprétation|  
|-----------------------|--------------------|  
|+ (plus)|Correspond à exactement un caractère.<br /><br /> Par exemple, A + correspond à AB, CA, Active Directory|  
|* (astérisque)|Correspond à zéro ou plusieurs caractères.<br /><br /> Par exemple, A * correspond à un, AB, ABC.|  
  
 Pour plus d’informations sur les caractères spéciaux pris en charge par l’adaptateur, consultez [exposent les paramètres de la carte sous la forme d’une propriété de liaison à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/expose-adapter-settings-as-a-binding-property-using-the-wcf-lob-adapter-sdk.md).
  
 Les étapes suivantes pour rechercher les RFC dans un système SAP à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### <a name="to-search-rfcs-in-an-sap-system"></a>Pour rechercher les RFC dans un système SAP  
  
1.  Se connecter à un serveur SAP à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Consultez [se connecter au système SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** liste déroulante, sélectionnez le type de contrat selon si vous recherchent pour les opérations entrantes ou sortantes, à l’aide de l’adaptateur.  
  
3.  Dans le **sélectionner une catégorie** , cliquez sur le groupe fonctionnel RFC contenant le document RFC que vous souhaitez rechercher. Si vous n’êtes pas sûr de savoir quel groupe fonctionnel pour effectuer la recherche, cliquez sur le nœud racine du document RFC.  
  
4.  Dans le **recherche dans la catégorie** texte, entrez une expression de recherche pour rechercher une demande de changement spécifique. Par exemple, pour rechercher les RFC qui ont « RFC_CUST » dans leur nom, tapez * RFC_CUST\* dans la zone de texte.  
  
5.  Cliquez sur le bouton avec l’icône de flèche droite pour démarrer la recherche. Une fois la recherche terminée, le **catégories et opérations disponibles** zone répertorie les documents RFC qui répondent aux critères de recherche.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] répertoriant le RFC résultat de la recherche.  
  
     ![Rechercher les RFC dans un système SAP](../../adapters-and-accelerators/adapter-sap/media/2cf0b262-bbc7-4d0f-a9cf-5b090fb744b6.gif "2cf0b262-bbc7-4d0f-a9cf-5b090fb744b6")  
  
## <a name="generating-schema-for-biztalk-projects"></a>Génération de schéma pour les projets BizTalk  
 Vous pouvez utiliser la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer le schéma pour les artefacts SAP sélectionnés. Une fois que vous avez parcouru et rechercher les artefacts que vous voulez appeler, vous pouvez générer le schéma pour ces artefacts et envoyer des messages, conforme au schéma, pour le système SAP.  
  
> [!NOTE]
>  Vous pouvez sélectionner des nœuds de catégorie pour retourner toutes les opérations de cette catégorie sub-Tree, par exemple, vous pouvez sélectionner un groupe fonctionnel RFC (pour générer le schéma pour tous les documents RFC dans ce groupe) ou sélectionnez RFC spécifiques pour générer le schéma pour uniquement ces documents RFC. Pour plus d’informations sur les nœuds, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).  
  
#### <a name="to-retrieve-metadata-for-rfcs"></a>Pour récupérer des métadonnées pour RFC  
  
1.  Se connecter à un serveur SAP à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. Consultez [se connecter au système SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** liste déroulante, sélectionnez le type de contrat, selon que vous allez effectuer les opérations entrantes et sortantes, à l’aide de l’adaptateur.  
  
3.  Dans le **sélectionner une catégorie** , cliquez sur le groupe fonctionnel RFC contenant le document RFC pour lequel vous souhaitez générer des métadonnées.  
  
     Vous pouvez également rechercher les RFC spécifiques. Par exemple, pour rechercher les RFC qui contiennent « RFC_CUST » dans leur nom, cliquez sur le nœud RFC et dans le **recherche dans la catégorie** type zone de texte \*RFC_CUST\*. Cliquez sur le bouton avec l’icône de flèche droite pour démarrer la recherche. Le **catégories et opérations disponibles** zone répertorie tous les documents RFC qui ont « RFC_CUST » dans leur nom.  
  
4.  Dans le **catégories et opérations disponibles** , sélectionnez les documents RFC pour lequel vous souhaitez générer des métadonnées, cliquez sur **ajouter**. Les documents RFC sélectionnés sont répertoriés dans le **ajouté des catégories et opérations** boîte.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] répertoriant les RFC sélectionnés.  
  
     ![Récupérer des métadonnées pour RFC](../../adapters-and-accelerators/adapter-sap/media/f7c89882-e2d7-409b-af2e-e35c7268c137.gif "f7c89882-e2d7-409b-af2e-e35c7268c137")  
  
     Si vous souhaitez générer le schéma pour plusieurs opérations, il est possible des définitions d’élément en double parmi ces schémas peut provoquer un échec de la compilation du projet BizTalk. Par exemple, considérez un scénario où vous générez le schéma pour une opération « Op1 ». Le schéma de « Op1 » contient un paramètre de type de données complexe « CT1 ». Après avoir généré le schéma pour « Op1 » que vous fermez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et rouvrez-le pour générer le schéma d’une autre opération « Op2 ». Supposons que « Op2 » contient également un paramètre de type de données complexe « CT1 ». Après avoir quitté le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et compilez le projet, vous obtenez des erreurs de compilation, car le type de données complexe « CT1 » est défini à deux reprises dans différents fichiers XSD. Dans ce cas, nous recommandons ce qui suit :  
  
    -   Génération du schéma pour toutes les opérations en une seule exécution de [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Cela garantit que le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ne génère qu’une seule définition pour le type de données complexe « CT1 ».  
  
    -   Si vous souhaitez générer le schéma pour plusieurs opérations entre les différentes exécutions de [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], veillez à sélectionner le **générer des types de schéma unique** case à cocher pour que les fichiers XSD générés contiennent des espaces de noms uniques pour le complexe type de données « CT1 ».  
  
5.  Cliquez sur **OK**. Le fichier de schéma est enregistré avec une extension .xsd dans le même emplacement que le projet BizTalk.  
  
    > [!NOTE]
    >  Si vous utilisez [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], par défaut, les fichiers sont créés avec la convention d’affectation de noms « SAPBinding\<n > .xsd », où « n » peut être de 1, 2, etc. selon le nombre de fichiers de schéma créés. Ou bien, vous pouvez fournir un nom personnalisé pour les fichiers de schéma en entrant un nom dans la **préfixe de nom de fichier** zone de texte. Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] maintenant crée des fichiers de schéma avec la convention d’affectation de noms \<préfixe de nom de fichier >\<n > .xsd.  
  
    > [!NOTE]
    >  Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] crée également un fichier de liaison (un fichier XML) qui contient les propriétés de liaison que vous avez spécifié lors de la génération du schéma pour une opération et l’action SOAP pour appeler l’opération. Vous pouvez importer ce fichier de liaison dans la console Administration de BizTalk Server pour créer un port personnalisé WCF avec l’URI, les propriétés de liaison de connexion et l’action SOAP définie. Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md).
  
6.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="generating-a-wcf-client-for-rfc-operations-using-the-add-adapter-service-reference-plug-in"></a>Génération d’un Client WCF pour les opérations de RFC à l’aide de l’ajouter une référence de Service d’adaptateur plug-in  
 Vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer un code de client WCF pour envoyer des documents RFC pour SAP du système ou un service WCF service contrat et le code pour recevoir les documents RFC (serveur RFC) à partir du système SAP.  
  
#### <a name="to-generate-a-wcf-client-or-a-wcf-service-contract-for-rfcs"></a>Pour générer un client WCF ou un contrat de service WCF pour les RFC  
  
1.  Dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], à partir de la **type de contrat Select** liste déroulante, sélectionnez le type de contrat, selon que vous exécutez (RFC serveur entrant) ou des opérations sortantes.  
  
2.  Dans le **sélectionner une catégorie** , développez le **RFC** nœud, puis cliquez sur le groupe fonctionnel RFC qui contient le document RFC pour lequel vous souhaitez générer un client WCF ou le contrat de service WCF.  
  
     Vous pouvez également rechercher les RFC. Par exemple, pour rechercher les RFC qui contiennent « RFC_CUST » dans leur nom, cliquez sur le **RFC** nœud et dans le **recherche dans la catégorie** type zone de texte \*RFC_CUST\*. Cliquez sur le bouton avec l’icône de flèche droite pour démarrer la recherche. Le **catégories et opérations disponibles** zone répertorie tous les documents RFC qui ont « RFC_CUST » dans leur nom.  
  
3.  Dans le **catégories et opérations disponibles** , sélectionnez les opérations ou les catégories (des groupes fonctionnels RFC) pour lequel vous souhaitez générer un client WCF (ou le contrat de service WCF), puis cliquez sur **ajouter**. Opérations sélectionnées sont répertoriées dans le **ajouté des catégories et opérations** boîte. Vous pouvez sélectionner n’importe quel nœud qui est répertorié dans le **catégories et opérations disponibles** boîte. Si vous sélectionnez un nœud de catégorie, puis toutes les opérations disponibles sous ce nœud et ses sous-nœuds seront ajoutés.  
  
4.  La plupart des scénarios, les options de sérialisation par défaut sont suffisantes ; Toutefois, si nécessaire, vous pouvez contrôler plusieurs aspects sur le code qui est généré et le type de sérialiseur utilisé. Pour définir ces options :  
  
    1.  Cliquez sur **Options avancées** pour ouvrir le **Options avancées** boîte.  
  
    2.  Dans le **Options avancées** sous **choisir les options pour le proxy généré**, sélectionnez les options souhaitées. Par exemple, vous pouvez choisir les méthodes asynchrones sont générés pour le client WCF ou désactiver la génération d’un fichier de configuration.  
  
    3.  Sous **sérialiseur** sélectionner le sérialiseur doit être utilisé.  
  
     L’illustration suivante montre le **Options avancées** zone avec les sélections par défaut (**automatique** est sélectionné pour le sérialiseur et aucune autre option est sélectionnées).  
  
     ![Les Options avancées zone des paramètres par défaut](../../adapters-and-accelerators/adapter-oracle-database/media/r2-net-adapters-oracle-msb-advanced-options.gif "R2_NET_Adapters_Oracle_MSB_Advanced_Options")  
  
     Les options que vous pouvez configurer dans le **Options avancées** zone sont équivalentes à certaines des options disponibles lorsque vous utilisez le service Model Metadata Utility Tool (svcutil.exe). Pour plus d’informations sur ces options, consultez [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx).
  
5.  Cliquez sur **OK**. Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] enregistre la classe de client WCF (ou l’interface de service WCF) et le code d’assistance pour les opérations et les catégories que vous avez sélectionnées dans votre répertoire de projet. Par défaut, un fichier de configuration est également enregistré. Légèrement différents fichiers sont générés pour les opérations entrantes et sortantes ; Pour plus d’informations, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Obtenir les métadonnées pour les opérations de SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)