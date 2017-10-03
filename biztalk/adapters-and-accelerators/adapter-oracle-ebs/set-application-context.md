---
title: "Définir le contexte application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9697155-70c0-4173-80d2-d02d103c397b
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88db982be92123a13084892bfc396cb1d89c46ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="set-application-context"></a>Définir le contexte application
Dans [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)], contexte d’application de paramètre est obligatoire pour certains artefacts d’Oracle E-Business Suite (interface tables, vues de l’interface, des programmes simultanés et demande définit) avant de pouvoir effectuer des opérations sur les. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne vous permet pas d’effectuer des opérations sur ces artefacts jusqu'à ce que vous avez défini le contexte d’application. Toutefois, pour les artefacts dans la base de données Oracle, c’est à l’utilisateur s’il souhaite définir le contexte d’application ou non.  
  
## <a name="what-is-application-context"></a>Qu’est le contexte de l’application  
 Contexte de l’application est un ensemble d’éléments associés à un artefact dans Oracle E-Business Suite qui implémente les préférences de l’utilisateur et le contrôle d’accès sur l’artefact. Contexte de l’application se compose des éléments suivants :  
  
-   **Nom d’utilisateur**: un utilisateur peut se connecter à Oracle E-Business Suite.  
  
-   **Responsabilité**: une responsabilité est un niveau d’accès dans Oracle E-Business Suite qui permet aux utilisateurs d’accéder uniquement les données et les fonctions qui sont appropriées à leurs rôles dans une organisation. Responsabilités peuvent autoriser l’accès à une application spécifique, unités, ensemble de livres et une liste restreinte des fenêtres, des fonctions et des autres responsabilités de fonctionnement. En vertu de l’affectation des responsabilités à un utilisateur, vous pouvez accorder/restreindre l’accès de l’utilisateur dans Oracle E-Business Suite.  
  
-   **ID d’organisation**: Oracle E-Business Suite prend en charge le paramètre configuration de plusieurs organisations. Ces différentes organisations sont spécifiquement identifiées par une valeur ID de l’organisation, dans la colonne Org_ID de la table dans Oracle E-Business Suite qui stocke des informations sur ces organisations. En vertu d’affectation d’une responsabilité à l’organisation ou en sélectionnant une organisation explicitement, vous pouvez accorder/restreindre l’accès d’un utilisateur à l’organisation.  
  
 Pour plus d’informations sur la responsabilité, plusieurs organisations et l’ID d’organisation dans Oracle E-Business Suite, recherchez le [centre d’aide Oracle](http://docs.oracle.com).  
  
## <a name="setting-application-context"></a>Contexte de l’application de paramètre  
 Comme le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] se connecte à la base de données sous-jacente dans Oracle E-Business Suite, contexte d’application pour les artefacts d’Oracle E-Business Suite ne sont pas établies ou initialisés dans l’adaptateur. Vous pouvez initialiser ou définir le contexte de l’application de ces artefacts dans le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] à l’aide d’une des opérations suivantes :  
  
-   **Propriétés de liaison**: le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose les propriétés de liaison suivantes pour définir le contexte de l’application : **OracleEBSOrganizationId**, **OracleUserName**,  **OraclePassword**, **OracleEBSResponsibilityKey**, **OracleEBSResponsibilityName**, et **ApplicationShortName**. Vous n’avez pas besoin de spécifier des valeurs pour toutes ces propriétés de liaison définir le contexte d’application pour les divers artefacts. Pour plus d’informations sur les propriétés de liaison requis pour le contexte d’application de paramètre pour un artefact, voir [propriétés de liaison de paramètre de contexte pour différents artefacts de l’Application](#Binding) plus loin dans cette rubrique.  
  
-   **Les propriétés de contexte du message**: le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose les propriétés de contexte de message suivantes pour définir le contexte de l’application : **ApplicationShortName**, **OrganizationID**, **ResponsibilityKey**, et **ResponsibilityName**. Pour spécifier le nom d’utilisateur et un mot de passe, vous devez utiliser les propriétés de liaison. Pour plus d’informations sur la façon de définir le contexte de l’application à l’aide des propriétés de contexte de message, consultez [configurer les propriétés de contexte de Message à l’aide de Application contexte](../../adapters-and-accelerators/adapter-oracle-ebs/configure-application-context-using-message-context-properties-in-oracle-ebs.md).  
  
> [!IMPORTANT]
>  La valeur spécifiée pour le **OracleEBSResponsibilityKey** propriété de liaison remplace la valeur de la **OracleEBSResponsibilityName** propriété de liaison. De même, la valeur spécifiée pour le **ResponsibilityKey** propriété de contexte de message remplace la valeur spécifiée pour le **ResponsibilityName** propriété de contexte de message.  
  
### <a name="precedence-order-binding-properties-vs-message-context-properties"></a>Ordre de priorité (propriétés de liaison et les propriétés de contexte de message)  
 Si vous définissez le contexte d’application à l’aide des propriétés de liaison et les propriétés de contexte de message, les valeurs spécifiées pour les propriétés de contexte de message est prioritaire et remplace les valeurs spécifiées pour les propriétés de liaison. Mais, par exemple, si vous spécifiez le nom court de l’application comme une propriété de contexte de message et les autres en tant que propriétés de liaison, seule la valeur pour le nom court de l’application provient de la propriété de contexte de message et le reste sont récupérées à partir de la liaison appropriées Propriétés.  
  
 **Ordre de priorité pour le nom court de l’Application**  
  
 Lors de la définition du contexte d’application, le nom court de l’application est utilisé dans l’ordre de priorité suivant (le plus élevé au plus bas) :  
  
-   Le nom court d’application spécifié dans le **ApplicationShortName** propriété de contexte de message.  
  
-   Nom court d’application spécifié dans l’action SOAP (pour les tables d’interface, les vues de l’interface, les programmes simultanés et demande définit uniquement).  
  
-   Le nom court d’application spécifié dans le **ApplicationShortName** propriété de liaison.  
  
 Cependant, pour les tables d’interface, vues de l’interface, des programmes simultanés et ensembles de requêtes, l’ordre de priorité est uniquement applicable lors de la définition du contexte d’application. Pour identifier les tables d’interface, les vues de l’interface, des programmes simultanés et demande définit, l’application nom court de l’action SOAP est utilisé.  
  
 **Ordre de priorité pour la clé de responsabilité et le nom de la responsabilité**  
  
 Lors de la définition du contexte d’application, la clé de responsabilité et le nom de responsabilité sont utilisés dans l’ordre de priorité suivant (le plus élevé au plus bas) :  
  
-   La clé de responsabilité spécifiée dans le **ResponsibilityKey** propriété de contexte de message.  
  
-   Le nom de la responsabilité spécifié dans le **ResponsibilityName** propriété de contexte de message.  
  
-   La clé de responsabilité spécifiée dans le **OracleEBSResponsibilityKey** propriété de liaison.  
  
-   Le nom de la responsabilité spécifié dans le **OracleEBSResponsibilityName** propriété de liaison.  
  
> [!TIP]
>  **Pourquoi utiliser des propriétés de contexte de message sur la liaison des propriétés pour définir le contexte de l’application ?** Si vous définissez le contexte d’application à l’aide des propriétés de liaison, WCF-Custom port d’envoi pour le Oracle E-Business adaptateur peut être utilisé uniquement pour l’ID d’organisation spécifique, la responsabilité et application que vous avez spécifié pour les propriétés de liaison. En revanche, si vous utilisez la propriété de contexte de message vous pouvez configurer un port d’envoi WCF-Custom « générique » et définir le contexte d’application au niveau du message.  
  
### <a name="setting-application-context-for-interface-tables-interface-views-concurrent-programs-and-request-sets-mandatory"></a>Définition du contexte de l’Application pour les Tables d’Interface, les vues de l’Interface, les programmes simultanés et demande définit (obligatoire)  
 Vous devez définir le contexte de l’application avant d’effectuer des opérations sur les tables d’interface, les vues de l’interface, les programmes simultanés et demande définit [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Pour ce faire, vous devez fournir les valeurs appropriées pour les propriétés de liaison ou les propriétés de contexte de message comme indiqué précédemment.  
  
> [!IMPORTANT]
>  Vous ne pouvez pas effectuer des opérations sur les tables de l’interface, vues de l’interface, des programmes simultanés et demande définit, sauf si vous avez défini les valeurs appropriées pour les propriétés de liaison requis ou le message de propriétés de contexte.  
  
### <a name="setting-application-context-for-plsql-apis-procedures-functions-tables-and-views"></a>Définition du contexte de l’Application pour les vues, procédures, fonctions, Tables et les API PL/SQL  
  
-   **Les API PL/SQL**: le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose les API PL/SQL associé à la base de données Oracle, ainsi que l’application Oracle E-Business Suite. S’il est facultatif définir le contexte d’application pour les API PL/SQL associé à la base de données Oracle, il est obligatoire de définir le contexte d’application pour les API PL/SQL associé à l’application Oracle E-Business Suite.  
  
-   **Fonctions et procédures**: il n’est pas obligatoire de définir le contexte d’application pour effectuer des opérations sur les procédures et fonctions dans la base de données Oracle.  
  
-   **Tables et vues**: il n’est pas obligatoire de définir le contexte d’application pour effectuer des opérations sur les tables et vues dans la base de données Oracle. Toutefois, pour l’application personnalisée Oracle E-Business Suite, les utilisateurs peuvent ou ne peuvent pas enregistrer les tables de base de données en tant que tables de l’interface. Si une table de base de données n’est pas enregistrée comme un tableau d’interface, il sera affiché en même temps que les tables de base de données dans le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Étant donné que ces tables sont associées à une application Oracle E-Business, pour toute opération sur ces tables, vous devez définir le contexte d’application.  
  
 Pour définir le contexte d’application de ces artefacts, vous devez fournir les valeurs appropriées pour les propriétés de liaison ou les propriétés de contexte de message comme indiqué précédemment.  
  
### <a name="setting-application-context-for-poll-executenonquery-executereader-executescalar-and-composite-operations"></a>Définition du contexte de l’Application pour l’interrogation, ExecuteNonQuery, ExecuteReader, ExecuteScalar et des opérations composites  
 Outre les artefacts, vous pouvez également définir le contexte d’application pour différentes opérations sont effectuées sur ces artefacts.  
  
-   Pour définir le contexte d’application pour l’opération d’interrogation, vous pouvez uniquement utiliser les propriétés de liaison comme indiqué précédemment. Pour le contexte de l’application de paramètre, vous devez fournir les valeurs appropriées pour les propriétés de liaison qui s’applique à l’objet sur lequel l’opération d’interrogation est effectuée. Par exemple, si l’opération d’interrogation est effectuée sur une table d’interface vous devez spécifier les valeurs pour les propriétés de liaison pour la table d’interface.  
  
-   Pour définir le contexte d’application pour les opérations ExecuteNonQuery, ExecuteReader et ExecuteScalar, vous devez fournir les valeurs appropriées pour les propriétés de liaison ou le message comme indiqué précédemment, les propriétés de contexte. Pour le contexte de l’application de paramètre pour ces opérations, vous devez fournir les valeurs appropriées pour les propriétés de liaison ou le message des propriétés de contexte qui s’applique à l’objet sur lequel les opérations sont effectuées.  
  
-   Pour définir le contexte d’application pour des opérations composites, vous devez fournir les valeurs appropriées pour les propriétés de liaison ou les propriétés de contexte de message comme indiqué précédemment. Pour le contexte de l’application de paramètre pour des opérations composites, vous devez fournir les valeurs appropriées pour les propriétés de liaison ou le message des propriétés de contexte qui sont applicables pour les opérations individuelles. Par exemple, si une opération composite contient deux opérations : une sur la table d’interface et l’autre sur la base de données de table, puis vous devez spécifier des valeurs pour les propriétés de liaison ou les propriétés de contexte de message pour la table d’interface, ainsi que la liaison propriétés ou les propriétés de contexte de message pour la table de base de données.  
  
    > [!IMPORTANT]
    >  Pour toutes ces opérations, il est obligatoire de définir le contexte d’application si l’opération est effectuée sur un artefact dans Oracle E-Business Suite (table d’interface, vue de l’interface, des programmes simultanés ou ensembles de requêtes). Si l’opération est effectuée sur un artefact dans la base de données sous-jacente, il n’est pas obligatoire de définir le contexte d’application. Par exemple, si vous effectuez l’opération d’interrogation sur une table d’interface, il est obligatoire de définir le contexte d’application, tandis que si l’opération d’interrogation est effectuée sur une table, il n’est pas obligatoire de définir le contexte d’application.  
  
## <a name="setting-the-language-for-performing-operations"></a>Définition de la langue pour effectuer des opérations  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge la fonctionnalité de prise en charge multilingue (MLS) d’Oracle E-Business Suite, et vous permet de spécifier une langue lors de l’exécution des opérations. Expose de l’adaptateur le **langage** liaison de la propriété sous la **MlsSettings** propriété de liaison et la **langage** propriété de contexte pour spécifier une langue pour exécution d’opérations.  
  
 La valeur spécifiée pour le **langage** propriété de contexte de message remplace la valeur de la **langage** liaison de la propriété sous la **MlsSettings** propriété de liaison. Pour plus d’informations sur la **MlsSettings** liaison de propriété, consultez [en savoir plus sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
##  <a name="Binding"></a>Propriétés de liaison pour définir le contexte de l’Application pour les divers artefacts  
 Le tableau suivant fournit des informations sur les propriétés de liaison pour laquelle vous devez spécifier les valeurs appropriées pour définir le contexte d’application pour les divers artefacts :  
  
|Artefacts|OracleEBSOrganizationId|OracleUserName|OraclePassword|OracleEBSResponsibilityKey<br />ou<br />OracleEBSResponsibilityName|ApplicationShortName|  
|---|---|---|---|---|---|  
|Tables d’interface et les vues de l’Interface|√*|√|√|√||  
|Programmes simultanés|√*|√|√|√||  
|Ensembles de requêtes|√*|√|√|√||  
|API PL/SQL|√*|√|√|√|√|  
|Procédures et fonctions|√*|√|√|√|√|  
|Tables et vues|√*|√|√|√|√|  
  
 **√\* = facultatif**  
  
> [!IMPORTANT]
>  -   La valeur par défaut de la **OracleEBSOrganizationId** (facultative) de la propriété de liaison a la valeur null. Si vous spécifiez une valeur pour le **OracleEBSOrganizationId** liaison de propriété, le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] définit le ORG_ID de la session à cette valeur lors de la définition du contexte d’application.  
> -   La valeur spécifiée pour le **OracleEBSResponsibilityKey** liaison de propriété substitue à la valeur spécifiée pour le **OracleEBSResponsibilityName** propriété de liaison.  
  
 Pour obtenir des informations détaillées sur chacune de ces propriétés, consultez [en savoir plus sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)