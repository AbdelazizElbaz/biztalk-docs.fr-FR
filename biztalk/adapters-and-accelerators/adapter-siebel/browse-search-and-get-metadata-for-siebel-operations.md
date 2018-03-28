---
title: Parcourir, rechercher et obtenir des métadonnées pour les opérations Siebel | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- metadata, retrieving
- how to, browse metadata
- how to, retrieve metadata
- retrieving, metadata
- metadata, browsing
- browsing, metadata
- metadata, searching
- how to, seach metadata
- searching, metadata
ms.assetid: 7e474d8e-b030-47ea-b1b6-8048cddbba8a
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68e7d8dc1b067096f118eb1145554edf0b11f605
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="browse-search-and-get-metadata-for-siebel-operations"></a>Parcourir, rechercher et obtenir des métadonnées pour les opérations Siebel
Cette section fournit des informations sur l’utilisation de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]et le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]. À l’aide de ces [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] composants, vous pouvez :  
  
-   Rechercher des opérations pour lequel récupérer les métadonnées.  
  
-   Rechercher des opérations pour lequel récupérer les métadonnées.  
  
-   Ajouter des schémas de message pour les opérations sélectionnées et les fichiers de configuration de liaison pour le port un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] de projet lorsque vous utilisez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
-   Ajouter une classe de client WCF ou un contrat de service WCF (interface) pour les opérations sélectionnées et un fichier de configuration (app.config) à un projet de programmation non-BizTalk en utilisant le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
> [!NOTE]
>  Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] présentes essentiellement la même interface lors de la navigation et de la recherche pour les opérations, afin des trois composants sont traités dans les rubriques mêmes.  
  
## <a name="prerequisites"></a>Configuration requise  
 Vous devez vous connecter à un système Siebel avant de pouvoir parcourir, rechercher ou récupérer les métadonnées pour les opérations de la cible. Pour plus d’informations sur la façon de se connecter à un système Siebel lorsque vous utilisez la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [se connecter au système Siebel dans Visual Studio](../../adapters-and-accelerators/adapter-siebel/connect-to-the-siebel-system-in-visual-studio.md).  
  
## <a name="browsing-metadata"></a>Exploration des métadonnées  
 Lors de l’exploration des métadonnées à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces :  
  
-   Les opérations qui peuvent être effectuées sur les composants d’entreprise Siebel comme insérer, interrogent, mettre à jour et supprimer.  
  
-   Méthodes de service métier qui peuvent être appelées par les clients de la carte.  
  
> [!NOTE]
>  À l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], vous pouvez parcourir les nœuds de catégorie et l’opération à l’aide d’une interface Windows.  
  
 Pour plus d’informations sur la consultation des métadonnées Siebel, consultez [Parcourir, rechercher et obtenir les métadonnées Siebel](../../adapters-and-accelerators/adapter-siebel/browse-search-and-get-siebel-metadata.md) 
  
 Les étapes suivantes pour parcourir les métadonnées d’un système Siebel à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### <a name="to-browse-metadata-in-a-siebel-system"></a>Pour rechercher des métadonnées dans un système Siebel  
  
1.  Se connecter à un système Siebel à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Consultez [se connecter au système Siebel dans Visual Studio](../../adapters-and-accelerators/adapter-siebel/connect-to-the-siebel-system-in-visual-studio.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** liste déroulante, sélectionnez le type de contrat, selon que vous allez effectuer les opérations entrantes et sortantes, à l’aide de l’adaptateur.  
  
3.  Le **sélectionner une catégorie** zone répertorie le **des objets métier** et **Services professionnels** nœuds. Cliquez sur le **des objets métier** nœud pour afficher la liste d’objets métier dans les **catégories et opérations disponibles** boîte. Vous pouvez également voir la liste d’objets métier en développant le **des objets métier** nœud.  
  
    > [!TIP]
    >  Vous pouvez directement accéder à la catégorie « exécution » ou plusieurs nœuds de sous-catégorie dans l’arborescence, en tapant le nom de l’artefact dans tandis que le focus est sur l’arborescence dans le **sélectionner une catégorie** boîte. Par exemple, pour accéder à la **compte** objet métier, conserver le focus sur le **des objets métier** nœud, puis tapez `Account`.  
  
4.  Cliquez sur les objets métier pour afficher la liste des composants d’entreprise pour un objet métier spécifique. Ou bien, vous pouvez consulter la liste de composants d’entreprise en développant un objet métier.  
  
5.  Cliquez sur les composants de gestion pour afficher la liste des opérations prises en charge pour le composant d’entreprise spécifique.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], qui répertorie l’objet métier, les composants d’entreprise et les opérations prises en charge.  
  
     ![Parcourir les composants d’entreprise Siebel](../../adapters-and-accelerators/adapter-siebel/media/11c63383-4269-4ba0-909b-e2cbec7eae04.gif "11c63383-4269-4ba0-909b-e2cbec7eae04")  
  
6.  Cliquez sur le **Services professionnels** nœud pour afficher la liste des services professionnels dans le **catégories et opérations disponibles** boîte. Ou bien, vous pouvez voir la liste des tables en développant le **Services professionnels** nœud.  
  
7.  Cliquez sur les services d’entreprise pour afficher la liste des méthodes de service business correspondantes.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], qui répertorie les services d’entreprise et les méthodes de service d’entreprise correspondant.  
  
     ![Parcourir les services d’entreprise Siebel](../../adapters-and-accelerators/adapter-siebel/media/60405c18-6035-42a5-851f-a0ed6d0570d6.gif "60405c18-6035-42a5-851f-a0ed6d0570d6")  
  
## <a name="searching-metadata"></a>Recherche de métadonnées  
 Lors de la recherche à l’aide des métadonnées Siebel [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]:  
  
-   Prend en charge les caractères génériques et d’échappement.  
  
-   Permet la recherche immédiatement sous le nœud à partir duquel l’opération de recherche est effectuée. Par exemple, pour rechercher un service d’entreprise, vous devez rechercher dans sous \Business Services.  
  
 Le tableau suivant répertorie les caractères spéciaux qui peuvent être utilisés pour la recherche et de leur interprétation par le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
|Caractère spécial|Interpretation|  
|-----------------------|--------------------|  
|? (point d’interrogation)|Correspond à exactement un caractère<br /><br /> Par exemple, un ? correspond à AB, CA, Active Directory.|  
|* (astérisque)|Correspond à zéro ou plusieurs caractères.<br /><br /> Par exemple, A * correspond à un, AB, ABC.|  
  
 Les étapes suivantes pour rechercher des métadonnées dans un système Siebel à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### <a name="to-search-metadata-in-a-siebel-system"></a>Pour rechercher des métadonnées dans un système Siebel  
  
1.  Se connecter à un système Siebel à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Consultez [se connecter au système Siebel dans Visual Studio](../../adapters-and-accelerators/adapter-siebel/connect-to-the-siebel-system-in-visual-studio.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** la liste déroulante, sélectionnez le **Client (Outbound operations)** contrat.  
  
3.  Dans le **sélectionner une catégorie** , cliquez sur le **objet métier** nœud.  
  
4.  Pour rechercher un objet métier particulier, cliquez sur le **des objets métier** nœud dans le **recherche dans la catégorie** texte zone, puis entrez une expression de recherche. Par exemple, pour rechercher des objets métier qui ont des noms commençant par « Compte », tapez **compte\***  dans la zone de texte.  
  
5.  Cliquez sur le bouton avec l’icône de flèche droite pour démarrer la recherche. Une fois la recherche terminée, le **catégories et opérations disponibles** zone répertorie les objets métier qui répondent aux critères de recherche.  
  
6.  Rechercher pour un composant d’entreprise spécifique sous un objet métier, cliquez sur un objet métier et dans le **recherche dans la catégorie** , saisissez une expression de recherche. Par exemple, pour rechercher des composants d’entreprise qui ont des noms commençant par « Compte », tapez **compte\***  dans la zone de texte.  
  
7.  Cliquez sur le bouton avec l’icône de flèche droite pour démarrer la recherche. Une fois la recherche terminée, le **catégories et opérations disponibles** zone répertorie les composants d’entreprise qui répondent aux critères de recherche.  
  
8.  Pour rechercher des opérations particulières pour un composant d’entreprise, cliquez sur un composant d’entreprise et dans le **recherche dans la catégorie** , saisissez une expression de recherche. Par exemple, pour rechercher les opérations ayant des noms commençant par « Requête », tapez **requête\***  dans la zone de texte.  
  
9. Cliquez sur le bouton avec l’icône de flèche droite pour démarrer la recherche. Une fois la recherche terminée, le **catégories et opérations disponibles** zone répertorie les composants d’entreprise qui répondent aux critères de recherche.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], qui répertorie les résultats de la recherche.  
  
     ![Rechercher des composants d’entreprise](../../adapters-and-accelerators/adapter-siebel/media/siebel-adpt-lesson1-step3-04-search.gif "SIEBEL-ADPT-Lesson1-Step3-04-search")  
  
     Exécuter une procédure similaire pour effectuer une recherche sous la **Service métier** nœud.  
  
## <a name="generating-schema-for-biztalk-projects"></a>Génération de schéma pour les projets BizTalk  
 Vous pouvez utiliser la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer le schéma pour les artefacts Siebel sélectionnés. Une fois que vous avez parcouru et rechercher les artefacts que vous voulez appeler, vous pouvez générer le schéma pour ces artefacts et envoyer des messages, conforme au schéma, pour Siebel.  
  
> [!NOTE]
>  Vous pouvez sélectionner des nœuds de catégorie pour retourner toutes les opérations de cette catégorie sub-Tree, par exemple, vous pouvez sélectionner un composant d’entreprise (pour la génération du schéma pour toutes les opérations dans le composant d’entreprise) ou une sélection des opérations spécifiques sur un composant d’entreprise (pour exemple, Insert et Delete) pour générer le schéma pour seulement ces opérations. Pour plus d’informations sur les nœuds, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md).  
  
#### <a name="to-generate-schema-for-siebel-artifacts"></a>Pour générer le schéma pour les artefacts de Siebel  
  
1.  Se connecter à un système Siebel à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. Consultez [se connecter au système Siebel dans Visual Studio](../../adapters-and-accelerators/adapter-siebel/connect-to-the-siebel-system-in-visual-studio.md) pour obtenir des instructions.  
  
2.  À partir de la **type de contrat Select** la liste déroulante, sélectionnez le **Client (Outbound operations)** contrat.  
  
3.  Dans le **sélectionner une catégorie** , développez l’objet métier ou un nœud de service d’entreprise.  
  
4.  Dans le **catégories et opérations disponibles** , sélectionnez les composants d’entreprise ou les services ou les opérations correspondantes pour lequel vous souhaitez générer des métadonnées, puis cliquez sur **ajouter**. Les zones fonctionnelles sélectionnés ou les opérations sont répertoriées dans le **ajouté des catégories et opérations** boîte.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], qui répertorie les opérations sélectionnées.  
  
     ![Récupérer des métadonnées pour l’objet métier](../../adapters-and-accelerators/adapter-siebel/media/siebel-adpt-lesson1-step3-05-get.gif "SIEBEL-ADPT-Lesson1-Step3-05-get")  
  
     Si vous souhaitez générer le schéma pour plusieurs opérations, il est possible des définitions d’élément en double parmi ces schémas peut provoquer un échec de la compilation du projet BizTalk. Par exemple, considérez un scénario où vous générez le schéma pour une opération « Op1 ». Le schéma de « Op1 » contient un paramètre de type de données complexe « CT1 ». Après avoir généré le schéma pour « Op1 » que vous fermez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et rouvrez-le pour générer le schéma d’une autre opération « Op2 ». Supposons que « Op2 » contient également un paramètre de type de données complexe « CT1 ». Après avoir quitté le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et compilez le projet, vous obtenez des erreurs de compilation, car le type de données complexe « CT1 » est défini à deux reprises dans différents fichiers XSD. Dans ce cas, nous recommandons ce qui suit :  
  
    -   Génération du schéma pour toutes les opérations en une seule exécution de [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Cela garantit que le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ne génère qu’une seule définition pour le type de données complexe « CT1 ».  
  
    -   Si vous souhaitez générer le schéma pour plusieurs opérations entre les différentes exécutions de [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], veillez à sélectionner le **générer des types de schéma unique** case à cocher pour que les fichiers XSD générés contiennent des espaces de noms uniques pour le complexe type de données « CT1 ».  
  
5.  Cliquez sur **OK**. Le fichier de schéma est enregistré avec une extension .xsd dans le même emplacement que le projet BizTalk.  
  
     Par défaut, les fichiers sont créés avec la convention d’affectation de noms « SiebelBindingSchema\<n\>.xsd », où « n » peut être 1, 2 et ainsi de suite, en fonction du nombre de fichiers de schéma créé. Ou bien, vous pouvez fournir un nom personnalisé pour les fichiers de schéma en entrant un nom dans la **préfixe de nom de fichier** zone de texte. Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] maintenant crée des fichiers de schéma avec la convention d’affectation de noms \<préfixe du nom de fichier\>schéma\<n\>.xsd.  
  
    > [!NOTE]
    >  Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] crée également un fichier de liaison (un fichier XML) qui contient les propriétés de liaison que vous avez spécifié quand générer le schéma pour une opération et l’action SOAP pour appeler l’opération. Vous pouvez importer ce fichier de liaison dans la console Administration de BizTalk Server pour créer un port personnalisé WCF avec l’URI, les propriétés de liaison de connexion et l’action SOAP définie. Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-physical-port-binding-using-a-port-binding-file-to-siebel.md).  
  
6.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="generating-a-wcf-client-using-the-add-adapter-service-reference-plug-in"></a>Génération d’un Client WCF à l’aide de l’ajouter une référence de Service d’adaptateur plug-in  
 Vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer le code du client WCF pour les opérations sortantes sur un système Siebel.  
  
#### <a name="to-generate-a-wcf-client"></a>Pour générer un client WCF  
  
1.  Dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], à partir de la **type de contrat Select** la liste déroulante, sélectionnez **Client (Outbound operations)**.  
  
2.  Dans le **sélectionner une catégorie** , développez l’objet métier ou un nœud de service d’entreprise.  
  
3.  Dans le **catégories et opérations disponibles** , sélectionnez les composants d’entreprise, les services ou les opérations correspondantes pour lequel vous souhaitez générer un client WCF, puis cliquez sur **ajouter**. Les zones fonctionnelles sélectionnés ou les opérations sont répertoriées dans le **ajouté des catégories et opérations** boîte. Vous pouvez sélectionner n’importe quel nœud qui est répertorié dans le **catégories et opérations disponibles** boîte. Si vous sélectionnez un nœud de catégorie, toutes les opérations disponibles sous ce nœud et ses sous-nœuds seront sélectionnés.  
  
    > [!IMPORTANT]
    >  Selon les catégories et les opérations que vous sélectionnez, plus d’une classe de client WCF peut être générée. Pour plus d’informations, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Siebel](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md).  
  
4.  La plupart des scénarios, les options de sérialisation par défaut sont suffisantes ; Toutefois, si nécessaire, vous pouvez contrôler plusieurs aspects sur le code qui est généré et le type de sérialiseur utilisé. Pour définir ces options :  
  
    1.  Pour ouvrir la **Options avancées** , cliquez sur **Options avancées**.  
  
    2.  Dans le **Options avancées** sous **choisir les options pour le proxy généré**, sélectionnez les options souhaitées. Par exemple, vous pouvez choisir les méthodes asynchrones sont générées pour le client WCF, ou vous pouvez désactiver la génération d’un fichier de configuration.  
  
    3.  Sous **sérialiseur**, sélectionnez le sérialiseur doit être utilisé.  
  
     L’illustration suivante montre le **Options avancées** zone avec les sélections par défaut (**automatique** est sélectionné pour le sérialiseur et aucune autre option est sélectionnées).  
  
     ![Les Options avancées zone des paramètres par défaut](../../adapters-and-accelerators/adapter-oracle-database/media/r2-net-adapters-oracle-msb-advanced-options.gif "R2_NET_Adapters_Oracle_MSB_Advanced_Options")  
  
     Les options que vous pouvez configurer dans le **Options avancées** zone sont équivalentes à certaines des options disponibles lorsque vous utilisez le service Model Metadata Utility Tool (svcutil.exe). Pour plus d’informations sur ces options, consultez [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx).
  
5.  Cliquez sur **OK**. Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] enregistre le client WCF code de classe et d’assistance pour les opérations et les catégories que vous avez sélectionnées dans votre répertoire de projet. Par défaut, un fichier de configuration est également enregistré. Pour plus d’informations, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Siebel](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Obtenir les métadonnées pour les opérations Siebel dans Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)