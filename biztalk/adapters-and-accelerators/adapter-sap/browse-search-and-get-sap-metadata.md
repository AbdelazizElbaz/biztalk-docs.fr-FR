---
title: "Parcourir, rechercher et obtenir les métadonnées SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metadata
- adapters, surfacing metadata
- TRFC
- RFC
- metadata, browsing, searching, retrieving
- adapters, operations
- BAPI
- IDOC
ms.assetid: 5f0d7c1f-d6e1-4c56-8d8e-1f5d537aa3ce
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40cc1bd6592b38dbda9c9bff3ad01d6cdaf8a707
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="browse-search-and-get-sap-metadata"></a>Parcourir, rechercher et obtenir les métadonnées SAP
Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces des métadonnées à partir du système SAP. Ces métadonnées décrivent la structure du message pour la communication avec un système SAP à l’aide de l’adaptateur. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge deux interfaces de récupération des métadonnées.  
  
-   **MetadataExchange** fournie par [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]. WCF fournit un point de terminaison d’échange de métadonnées pour toutes les liaisons WCF, ce qui permet aux clients d’obtenir les métadonnées à partir du système SAP.  
  
-   **IMetadataRetrievalContract** fournie par le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], qui prend en charge les métadonnées de parcourir et rechercher des fonctions de l’adaptateur.  
  
 Un des objectifs de la [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] consiste à exposer le système SAP comme un service WCF. L’adaptateur met en évidence les artefacts SAP (RFC, BAPI et IDOC) en tant qu’opérations que les clients de l’adaptateur peuvent appeler. L’adaptateur met également en évidence certaines des opérations spécifiques qui peuvent être utilisées pour envoyer ou recevoir des IDOC à partir d’un système SAP. Ces opérations sont répertoriées plus loin dans cette rubrique.  
  
 Il est possible de parcourir, rechercher et récupérer des métadonnées à l’aide du modèle de service WCF, à l’aide du modèle de canal WCF ou en créant un BizTalk de projet dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
 Lorsque vous utilisez le modèle de service WCF, vous devez utiliser le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer les classes proxy pour effectuer des opérations sur le système SAP. Lorsque vous utilisez un projet BizTalk, vous devez utiliser le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] ou [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour générer des métadonnées pour les opérations que vous souhaitez exécuter sur le système SAP.  
  
 Pour plus d’informations sur la navigation, la recherche et la récupération de métadonnées à l’aide [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], consultez [obtenir les métadonnées pour les opérations de SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md).  
  
## <a name="browsing-metadata"></a>Exploration des métadonnées  
 Le[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] permet aux clients d’adaptateur parcourir le RFC tRFCs, BAPI et IDOC exposées par le système SAP. Dans le cadre de l’opération de parcourir des métadonnées, l’adaptateur met en évidence les RFC et les interfaces BAPI en tant qu’opérations. Des IDOC, l’adaptateur met en évidence des opérations pour envoyer et recevoir des IDOC. Ces opérations sont disponibles à partir de [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Les métadonnées SAP sont classée sous les nœuds suivants :  
  
-   **RFC**. Ce nœud contient les documents RFC exposées par le système SAP et représente un module de fonction dans SAP. L’adaptateur catégorise les RFC dans plusieurs niveaux logiques et expose une vue hiérarchique pour les clients de la carte. Une demande de changement est au niveau plus bas de cette hiérarchie et est exposée en tant qu’opération qui peut être appelée par une application externe. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise le SDK de RFC pour générer des métadonnées pour les documents RFC. L’adaptateur peut appeler uniquement ces documents RFC pour lequel il peut générer des métadonnées.  
  
     Autre que de surfaces des RFC en tant qu’opérations, l’adaptateur met également en évidence certaines des opérations spécifiques telles que **RfcGetAttributes**. Pour plus d’informations sur ces opérations, consultez [opérations sur les documents RFC dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md).  
  
-   **TRFC**. Ce nœud contient le tRFCs exposée par le système SAP. tRFCs ne sont pas un artefact classique dans un système SAP, mais plutôt un mécanisme pour appeler les documents RFC. tRFCs sont classés sous un nœud distinct, car leurs caractéristiques des métadonnées sont différentes de RFC. Plus précisément, les documents RFC incluent également des paramètres d’exportation. L’adaptateur de la catégorie du tRFCs dans plusieurs niveaux logiques et expose une vue hiérarchique pour les clients de la carte. Un tRFC est le niveau le plus bas de cette hiérarchie et est exposée en tant qu’opération qui peut être appelée par une application externe.  
  
     Autre que de surfaces le tRFCs en tant qu’opérations, l’adaptateur met également en évidence certaines des opérations spécifiques telles que **RfcConfirmTransID**. Pour plus d’informations sur ces opérations, consultez [opérations sur tRFCs dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).  
  
-   **BAPI**. Ce nœud contient les interfaces BAPI exposées par le système SAP. L’adaptateur catégorise les BAPI dans plusieurs niveaux logiques et expose une vue hiérarchique pour les clients de la carte. Un BAPI est le niveau le plus bas de cette hiérarchie et est exposé en tant qu’opération qui peut être appelée par une application externe.  
  
-   **IDOC**. Ce nœud contient les IDOC exposées par un système SAP. L’adaptateur de la catégorie de l’IDOC dans plusieurs niveaux logiques et expose une vue hiérarchique pour les clients de la carte. Les opérations qui expose de l’adaptateur pour l’IDOC sont :  
  
    -   **Envoyer** et **réception**. Les clients de l’adaptateur peuvent d’effectuer ces opérations envoyer et recevoir des IDOC à partir d’un système SAP à l’aide d’un schéma fortement typé.  
  
    -   **SendIdoc** et **ReceiveIdoc**. Les clients de l’adaptateur peuvent d’effectuer ces opérations envoyer et recevoir des IDOC à partir d’un système SAP à l’aide d’un schéma faiblement typée.  
  
     Pour plus d’informations sur ces opérations, consultez [opérations sur IDOC dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md).  
  
 Pour plus d’informations sur la façon dont les métadonnées sont catégorisée, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).  
  
## <a name="searching-metadata"></a>Recherche de métadonnées  
 Dans le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], les clients de l’adaptateur peuvent rechercher des métadonnées dans un système SAP en utilisant des expressions de recherche qui sont dépendantes des RFC sous-jacent qui le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise. Le tableau suivant répertorie les artefacts SAP et la hiérarchie de métadonnées sous lequel les clients de l’adaptateur peuvent rechercher.  
  
|Artefact|Recherches sous le nœud dans l’interface graphique utilisateur|  
|--------------|------------------------------------|  
|RFC|-/RFC<br />-/RFC/ [application groupe]|  
|tRFC|-/TRFC<br />-/TRFC/ [application groupe]|  
|BAPI|-/BAPI|  
|IDOC|-/IDOC|  
  
 Le tableau suivant répertorie les caractères spéciaux qui peuvent être utilisés pour la recherche et de leur interprétation par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
|Caractère spécial|Interprétation|  
|-----------------------|--------------------|  
|+ (plus)|Correspond à exactement un caractère.<br /><br /> Par exemple, A + correspond à AB, CA, Active Directory|  
|* (astérisque)|Correspond à zéro ou plusieurs caractères.<br /><br /> Par exemple, A * correspond à un, AB, ABC.|  
  
## <a name="retrieving-metadata"></a>Récupération de métadonnées  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] permet aux clients d’adaptateur récupérer des métadonnées pour le système SAP, y compris les caractéristiques des métadonnées détaillées :  
  
-   Pour une demande de changement, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] récupère le nom de la RFC, ainsi que l’importation, exportation, modification et les paramètres de table. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] également extrait les types de données pour les paramètres, la longueur de champ des paramètres, en plus des paramètres obligatoires et facultatifs.  
  
-   Pour un tRFC, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] récupère des informations similaires à la RFC, à l’exception des paramètres d’exportation. Étant donné que les appels tRFC sont asynchrones, aucun paramètre de sortie n’est récupérés.  
  
-   Pour un BAPI, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] récupère le nom d’objet métier, le nom de méthode d’objet métier et d’autres informations spécifiques similaires à RFC.  
  
-   Pour un IDOC, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] récupère le type IDOC, le numéro de version, la version, les enregistrements de contrôle IDOC, les enregistrements de données IDOC et autres informations de segment IDOC.  
  
    > [!NOTE]
    >  Si les métadonnées pour IDOC contient des valeurs supérieure et inférieure (plage) pour un type de données, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] qui expose sous forme de chaîne. Si les métadonnées contiennent uniquement des valeurs faibles, les [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] qui expose un enum.  
  
> [!NOTE]
>  Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] expose les paramètres de fonction SAP dans un ordre alphabétique, quelle que soit la façon dont les paramètres sont classés dans la définition de fonction SAP. Voici les raisons suivantes :  
>   
>  -   Différentes versions du Kit de développement logiciel SAP RFC retournent les paramètres de la fonction SAP dans des ordres différents. Par conséquent, afin de fournir une expérience cohérente pour les utilisateurs de la carte, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] expose les paramètres dans l’ordre alphabétique.  
> -   Mêmes RFC sur différents serveurs SAP peut avoir un ordre différent d’exposer les paramètres de fonction. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] rend cette différence transparent pour les utilisateurs en exposant les paramètres dans un ordre alphabétique cohérent.  
  
> [!NOTE]
>  Lors de la récupération des données du système SAP en utilisant le [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] modèle de service, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ne désérialise pas les messages comportant plus de 65 536 nœuds. Vérifiez que le message de réponse a des nœuds est inférieur ou égal à 65 536. Vous pouvez contourner cette limitation en modifiant le fichier app.config de votre application. Pour obtenir des instructions, consultez [dépanner les problèmes opérationnels](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-operational-issues-with-the-oracle-database-adapter.md).  
  
 Pour plus d’informations sur la navigation, la recherche et la récupération des métadonnées, consultez [obtenir les métadonnées pour les opérations de SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de l’architecture de l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md)