---
title: Informations de configuration | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Call Rules shape [Orchestration Designer], planning
- Call Rules shape [Orchestration Designer], configuring
ms.assetid: aa4924c6-4270-473b-aa0a-6d8b18375a39
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9a35767815eaf7406a7baae5d9dccb833492287
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuration-information"></a>Informations de configuration
Cette rubrique explique comment configurer le **appeler règles** forme.  
  
## <a name="orchestration-variables-and-fact-types"></a>Variables d'orchestration et types de faits  
 Dans l’orchestration où le **appeler règles** forme se trouve, vous devez avoir des variables qui correspondent aux types utilisés dans la stratégie. Si vous ne disposez pas des types de variables corrects, vous ne pouvez pas fournir les paramètres corrects à la stratégie. Supposons que vous ayez un **appeler règles** forme dans une orchestration, CallMyRules et que vous utilisez CallMyRules pour appeler MyPolicy. Si une classe .NET, MyClass, est utilisée dans MyPolicy, vous devez créer une variable de type MyAssembly.MyClass dans l'orchestration. De même, si MyPolicy a **DataConnection** liaisons, vous devez créer une variable d’un **Microsoft.RuleEngine.DataConnection** type dans l’orchestration.  
  
 En plus des variables dans l'orchestration, vous devez créer des instances pour ces variables. Vous pouvez le faire, ajoutez un **Expression** forme à votre orchestration. À l’aide de l’exemple précédent, vous devez instancier une instance MyAssembly.MyClass et une **DataConnection** instance. Pour instancier le **DataConnection** instance, vous procédez comme suit :  
  
-   Créer un **SqlConnection** de l’instance et l’assigner à MySqlCon.  
  
-   Créer un **DataConnection** de l’instance et l’assigner à dataConnection (variable de **DataConnection** type), comme illustré dans le fragment de code suivant :  
  
    ```  
    dataConnection = new Microsoft.RuleEngine.DataConnection("NameOfSqlDatabaseHere", "NameOfYourTableHere", MySqlCon);  
    ```  
  
> [!NOTE]
>  Si vous n’avez pas de variables correspondant aux types de faits, ces types n’apparaissent pas en tant que paramètres dans le **spécifier les paramètres de stratégie** zone de liste dans le **configuration de la stratégie RèglesAppel** boîte de dialogue.  
  
> [!NOTE]
>  Le moteur d’orchestration convertit automatiquement les variables de message que vous spécifiez en tant que paramètres à une stratégie BRE dans **TypedXmlDocument** objets et les déclare dans la mémoire de travail du moteur de règles avant l’exécution de la stratégie. Ainsi, vous ne devez pas déclarer les variables du type TypedXmlDocument comme vous le faisiez pour .NET et les faits de base de données.  
  
## <a name="message-type-and-document-type"></a>Type de message et type de document  
 Vous devez vous assurer que le **DocumentType** propriété pour les nœuds XML utilisés dans votre règle d’entreprise (que vous implémentez dans l’éditeur des règles d’entreprise) est le même que le **MessageType** pour les nœuds XML définis dans le orchestration : elle doit correspondre à la **MessageType** du message ou partie du message qui sera transmis au moteur de règles dans le **appeler règles** forme.  
  
 Par exemple, si vous définissez un schéma XML de bon de commande (PO) dans un projet BizTalk, le **MessageType** défini pour ce schéma est **BTSProject.PO** (si **BTSProject** est le espace de noms ou le nom du projet à l’aide de l’espace de noms par défaut).  
  
 Dans le cas de la **PO\Amount** élément, avant de le déposer dans une définition de règle, vous devez modifier son **DocumentType**propriété **BTSProject.PO** dans la fenêtre Propriétés . Vous pouvez accéder à la fenêtre Propriétés lorsque n’importe quel nœud dans le schéma est sélectionné dans le **schémas XML** onglet dans l’Explorateur de faits. Cette modification est appliquée à tous les éléments du schéma mais n'est pas conservée avec le schéma. Elle doit être réinitialisée lorsque l'Éditeur des règles d'entreprise est lancé ou quand le schéma est rechargé. Cela est nécessaire pour les définitions de vocabulaire basées sur des schémas XML ou sur des règles créées directement à partir des schémas XML. Si vous ne le faites pas, vous pouvez exécuter la stratégie, mais la **appeler règles** forme ne fonctionnera pas correctement et le type de message n’apparaît pas dans le **spécifier les paramètres de stratégie** zone de liste dans le  **Configuration de la stratégie RèglesAppel** boîte de dialogue.