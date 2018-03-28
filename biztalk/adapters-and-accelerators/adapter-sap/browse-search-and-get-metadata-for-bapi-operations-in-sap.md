---
title: Parcourir, rechercher et d’obtenir des métadonnées pour des opérations BAPI dans SAP | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAPI operations
- WCF client, generating for BAPI operations
- BAPIs, browsing
- searching, BAPIs
- browsing, BAPIs
- BAPIs, searching
- BAPI operations, generating schema
ms.assetid: 2884215a-ddba-40c7-bf9f-bfc7831f90bb
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aaf2145bd288d844a3ad02e222a8d8193f32b7de
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="browse-search-and-get-metadata-for-bapi-operations-in-sap"></a>Parcourir, rechercher et d’obtenir des métadonnées pour des opérations BAPI dans SAP
Cette section fournit des instructions sur la façon de parcourir, rechercher et récupérer les métadonnées à partir de SAP pour à l’aide des opérations BAPI [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. La plupart des instructions est les même pour toute l’interface utilisateur de trois. Là où les procédures d’applicables, distinctes sont fournies pour l’interface utilisateur approprié.  
  
 Avant d’effectuer les étapes décrites dans les sections suivantes, vous devez avoir :  
  
-   Créé un [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] projet.  
  
-   Le système SAP en utilisant le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Pour obtenir des instructions, consultez [se connecter au système SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md).  
  
## <a name="browsing-bapis-in-an-sap-system"></a>Navigation BAPI dans un système SAP  
 Lors de l’exploration à l’aide de métadonnées [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] met en évidence des interfaces BAPI en tant qu’objets d’entreprise et en tant que documents RFC. Navigation BAPI en tant que RFC est similaire à la navigation d’une commande RFC dans un système SAP. Dans ce cas, les interfaces BAPI sont disponibles en tant que RFC sous le **RFC**. Pour plus d’informations sur la recherche de RFC, consultez [Parcourir, rechercher et obtenir des métadonnées pour les opérations de RFC dans SAP](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md).  
  
 Cette section fournit des informations sur la navigation BAPI en tant qu’objets d’entreprise. Pour plus d’informations sur la consultation des métadonnées SAP, consultez la rubrique [en quoi les métadonnées de SAP de Surface de carte ?](https://msdn.microsoft.com/library/dd788039.aspx)  
  
 Les étapes suivantes pour rechercher les BAPI dans un système SAP à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
 
  
#### <a name="to-browse-bapis-in-an-sap-system"></a>Pour rechercher les BAPI dans un système SAP  
  
1.  Se connecter à un serveur SAP à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Consultez [se connecter au système SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** liste déroulante, sélectionnez le type de contrat, selon que vous allez effectuer les opérations entrantes et sortantes, à l’aide de l’adaptateur.  
  
3.  Dans le **sélectionner une catégorie** , cliquez sur le nœud BAPI pour voir les zones fonctionnelles BAPI dans le **catégories et opérations disponibles** boîte. Ou bien, vous pouvez également voir les zones fonctionnelles BAPI en développant le nœud BAPI.  
  
    > [!TIP]
    >  Vous pouvez directement accéder à la catégorie « exécution » ou plusieurs nœuds de sous-catégorie dans l’arborescence, en tapant le nom de l’artefact dans tandis que le focus est sur l’arborescence dans le **sélectionner une catégorie** boîte. Par exemple, pour accéder à la **contrôle** zone fonctionnelle de BAPI, conserver le focus sur le **BAPI** nœud, puis tapez `Controlling`.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] répertoriant les zones fonctionnelles BAPI.  
  
     ![Recherche de zones fonctionnelles dans un BAPI](../../adapters-and-accelerators/adapter-sap/media/d4b03725-44d2-449d-a035-491cd7415139.gif "d4b03725-44d2-449d-a035-491cd7415139")  
  
4.  Cliquez sur la zone fonctionnelle de BAPI pour afficher les catégorisations supplémentaires de la zone fonctionnelle de BAPI.  
  
5.  Cliquez sur la zone fonctionnelle de BAPI pour voir les opérations pertinentes pris en charge pour cette zone fonctionnelle. L’illustration suivante montre la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] avec les opérations prises en charge pour un domaine fonctionnel spécifique.  
  
     ![Parcourir des opérations pour un BAPI](../../adapters-and-accelerators/adapter-sap/media/1a9be42e-1f9e-4cf6-a555-c4e755fcc0ea.gif "1a9be42e-1f9e-4cf6-a555-c4e755fcc0ea")  
  
## <a name="searching-bapis-in-an-sap-system"></a>Rechercher les BAPI dans un système SAP  
 Lors de la recherche de métadonnées pour les BAPI dans un système SAP à l’aide [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]:  
  
-   Prend en charge les caractères génériques dans l’expression de recherche.  
  
-   Permet la recherche immédiatement sous le nœud à partir duquel l’opération de recherche est effectuée.  
  
 Le tableau suivant répertorie les caractères spéciaux qui peuvent être utilisés pour la recherche et de leur interprétation par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
|Caractère spécial|Interpretation|  
|-----------------------|--------------------|  
|+ (plus)|Correspond à exactement un caractère.<br /><br /> Par exemple, A + correspond à AB, CA, Active Directory|  
|* (astérisque)|Correspond à zéro ou plusieurs caractères.<br /><br /> Par exemple, A * correspond à un, AB, ABC.|  
  
 Pour plus d’informations sur les caractères spéciaux pris en charge par l’adaptateur, consultez [en quoi les métadonnées de SAP de Surface de carte ?](https://msdn.microsoft.com/library/dd788039.aspx)  
  
 Les étapes suivantes pour rechercher les BAPI dans un système SAP à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### <a name="to-search-bapis-in-an-sap-system"></a>Pour rechercher les BAPI dans un système SAP  
  
1.  Se connecter à un serveur SAP à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Consultez [se connecter au système SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** liste déroulante, sélectionnez le type de contrat selon si vous recherchent pour les opérations entrantes ou sortantes, à l’aide de l’adaptateur.  
  
3.  Dans le **sélectionner une catégorie** , cliquez sur la zone fonctionnelle BAPI contenant BAPI à rechercher.  
  
    > [!NOTE]
    >  Vous pouvez rechercher les BAPI uniquement au niveau racine.  
  
4.  Dans le **recherche dans la catégorie** texte, entrez une expression de recherche pour rechercher un BAPI spécifique. Par exemple, pour rechercher les BAPI qui ont « Compte » dans leur nom, tapez * compte\* dans la zone de texte.  
  
5.  Cliquez sur le bouton avec l’icône de flèche droite pour démarrer la recherche. Une fois la recherche terminée, le **catégories et opérations disponibles** zone répertorie les interfaces BAPI qui répondent aux critères de recherche.  
  
6.  L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] liste BAPI résultat de la recherche.  
  
     ![Rechercher les BAPI dans un système SAP](../../adapters-and-accelerators/adapter-sap/media/82771a47-b656-473e-a96d-998bced38b35.gif "82771a47-b656-473e-a96d-998bced38b35")  
  
## <a name="generating-schema-for-biztalk-projects"></a>Génération de schéma pour les projets BizTalk  
 Vous pouvez utiliser la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer le schéma pour les artefacts SAP sélectionnés. Une fois que vous avez parcouru et rechercher les artefacts que vous voulez appeler, vous pouvez générer le schéma pour ces artefacts et envoyer des messages, conforme au schéma, pour le système SAP.  
  
> [!NOTE]
>  Vous pouvez sélectionner des nœuds de catégorie pour retourner toutes les opérations de cette catégorie sub-Tree, par exemple, vous pouvez sélectionner l’intégralité d’un BAPI fonctionnel inférieur sont (pour générer un schéma pour toutes les interfaces BAPI dans ce groupe) ou sélectionnez BAPI spécifiques pour générer le schéma pour seulement ces interfaces BAPI. Pour plus d’informations sur les nœuds, consultez [IDs4 de nœud de métadonnées](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).  
  
#### <a name="to-retrieve-metadata-for-bapis"></a>Pour récupérer des métadonnées pour les interfaces BAPI  
  
1.  Se connecter à un serveur SAP à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. Consultez [se connecter au système SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** liste déroulante, sélectionnez le type de contrat, selon que vous allez effectuer les opérations entrantes et sortantes, à l’aide de l’adaptateur.  
  
3.  Dans le **sélectionner une catégorie** , cliquez sur le groupe fonctionnel BAPI contenant BAPI pour lequel vous souhaitez générer des métadonnées.  
  
4.  Dans le **catégories et opérations disponibles** , sélectionnez les zones fonctionnelles ou pour lequel vous souhaitez générer des métadonnées, cliquez sur les opérations **ajouter**. Les zones fonctionnelles sélectionnés ou les opérations sont répertoriées dans le **ajouté des catégories et opérations** boîte.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] qui répertorie les interfaces BAPI sélectionnés.  
  
     ![Récupérer des métadonnées pour un BAPI](../../adapters-and-accelerators/adapter-sap/media/74170978-aef0-46c9-a6e2-36d6e9c2aefc.gif "74170978-aef0-46c9-a6e2-36d6e9c2aefc")  
  
     Si vous souhaitez générer le schéma pour plusieurs opérations, il est possible des définitions d’élément en double parmi ces schémas peut provoquer un échec de la compilation du projet BizTalk. Par exemple, considérez un scénario où vous générez le schéma pour une opération « Op1 ». Le schéma de « Op1 » contient un paramètre de type de données complexe « CT1 ». Après avoir généré le schéma pour « Op1 » que vous fermez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et rouvrez-le pour générer le schéma d’une autre opération « Op2 ». Supposons que « Op2 » contient également un paramètre de type de données complexe « CT1 ». Après avoir quitté le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et compilez le projet, vous obtenez des erreurs de compilation, car le type de données complexe « CT1 » est défini à deux reprises dans différents fichiers XSD. Dans ce cas, nous recommandons ce qui suit :  
  
    -   Génération du schéma pour toutes les opérations en une seule exécution de [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Cela garantit que le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ne génère qu’une seule définition pour le type de données complexe « CT1 ».  
  
    -   Si vous souhaitez générer le schéma pour plusieurs opérations entre les différentes exécutions de [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], veillez à sélectionner le **générer des types de schéma unique** case à cocher pour que les fichiers XSD générés contiennent des espaces de noms uniques pour le complexe type de données « CT1 ».  
  
5.  Cliquez sur **OK**. Le fichier de schéma est enregistré avec une extension .xsd dans le même emplacement que le projet BizTalk.  
  
    > [!NOTE]
    >  Si vous utilisez [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], par défaut, les fichiers sont créés avec la convention d’affectation de noms « SAPBinding\<n\>.xsd », où « n » peut être de 1, 2, etc. selon le nombre de fichiers de schéma créés. Ou bien, vous pouvez fournir un nom personnalisé pour les fichiers de schéma en entrant un nom dans la **préfixe de nom de fichier** zone de texte. Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] maintenant crée des fichiers de schéma avec la convention d’affectation de noms \<préfixe de nom de fichier\>\<n\>.xsd.  
  
    > [!NOTE]
    >  Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] crée également un fichier de liaison (un fichier XML) qui contient les propriétés de liaison que vous avez spécifié lors de la génération du schéma pour une opération et l’action SOAP pour appeler l’opération. Vous pouvez importer ce fichier de liaison dans la console Administration de BizTalk Server pour créer un port personnalisé WCF avec l’URI, les propriétés de liaison de connexion et l’action SOAP définie. Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md).
  
6.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="generating-a-wcf-client-for-bapi-operations-using-the-add-adapter-service-reference-plug-in"></a>Génération d’un Client WCF pour les opérations BAPI à l’aide de l’ajouter une référence de Service d’adaptateur plug-in  
 Vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer le code du client WCF pour les opérations BAPI (les opérations entrantes ne sont pas pris en charge pour les interfaces BAPI).  
  
#### <a name="to-generate-a-wcf-client-for-bapis"></a>Pour générer un client WCF pour les interfaces BAPI  
  
1.  Dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], à partir de la **type de contrat Select** la liste déroulante, sélectionnez **Client (Outbound operations)**.  
  
2.  Dans le **sélectionner une catégorie** , développez le **BAPI** nœud, puis parcourir ou rechercher les catégories BAPI ou les opérations pour lesquelles vous voulez générer un client WCF.  
  
3.  Dans le **catégories et opérations disponibles** , sélectionnez les opérations ou les catégories (groupes fonctionnels BAPI) pour lequel vous souhaitez générer un client WCF, puis cliquez sur **ajouter**. Opérations sélectionnées sont répertoriées dans le **ajouté des catégories et opérations** boîte. Vous pouvez sélectionner n’importe quel nœud qui est répertorié dans le **catégories et opérations disponibles** boîte. Si vous sélectionnez un nœud de catégorie, toutes les opérations disponibles sous ce nœud et ses sous-nœuds seront sélectionnés.  
  
    > [!IMPORTANT]
    >  Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère une classe de client WCF unique pour chaque objet de l’entreprise. Selon les catégories et les opérations que vous sélectionnez, plus d’une classe de client WCF peut être générée. Pour plus d’informations, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
4.  La plupart des scénarios, les options de sérialisation par défaut sont suffisantes ; Toutefois, si nécessaire, vous pouvez contrôler plusieurs aspects sur le code qui est généré et le type de sérialiseur utilisé. Pour définir ces options :  
  
    1.  Cliquez sur **Options avancées** pour ouvrir le **Options avancées** boîte.  
  
    2.  Dans le **Options avancées** sous **choisir les options pour le proxy généré**, sélectionnez les options souhaitées. Par exemple, vous pouvez choisir les méthodes asynchrones sont générés pour le client WCF ou désactiver la génération d’un fichier de configuration.  
  
    3.  Sous **sérialiseur** sélectionner le sérialiseur doit être utilisé.  
  
     L’illustration suivante montre le **Options avancées** zone avec les sélections par défaut (**automatique** est sélectionné pour le sérialiseur et aucune autre option est sélectionnées).  
  
     ![Les Options avancées zone des paramètres par défaut](../../adapters-and-accelerators/adapter-oracle-database/media/r2-net-adapters-oracle-msb-advanced-options.gif "R2_NET_Adapters_Oracle_MSB_Advanced_Options")  
  
     Les options que vous pouvez configurer dans le **Options avancées** zone sont équivalentes à certaines des options disponibles lorsque vous utilisez le service Model Metadata Utility Tool (svcutil.exe). Pour plus d’informations sur ces options, consultez [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx). 
  
5.  Cliquez sur **OK**. Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] enregistre le client WCF à code de classe et d’assistance dans votre répertoire de projet pour les catégories et opérations sélectionnées. Par défaut, un fichier de configuration est également enregistré. Pour plus d’informations, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Obtenir les métadonnées pour les opérations SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)