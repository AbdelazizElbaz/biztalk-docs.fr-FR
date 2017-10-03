---
title: "Opérations sur les composants d’entreprise Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business components, operations on
- operations, on business components
- operations, on business components with picklist fields
ms.assetid: 5430a8bd-88eb-4851-92e3-676ca83780c9
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc634d48d4a39e610247edbab98104bc3c6da379
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-business-components-in-siebel"></a>Opérations sur les composants d’entreprise Siebel
Un composant d’entreprise Siebel est une entité logique qui associe les colonnes à partir d’une ou plusieurs tables de base de données dans une structure unique. Les clients de l’adaptateur peuvent effectuer les opérations suivantes sur les composants d’entreprise Siebel à l’aide de l’adaptateur :  
  
-   **Insérer**. Clients de l’adaptateur peuvent insérer un ou plusieurs enregistrements dans un composant d’entreprise.  
  
-   **Requête**. Les clients de l’adaptateur peuvent interroger un ou plusieurs enregistrements à partir d’un composant d’entreprise. Cette opération accepte les paramètres suivants comme entrée :  
  
    -   SearchExpr : Contient une expression de recherche. Tous les enregistrements sous un composant métier spécifiée sont comparées par rapport à cette expression de recherche, et les enregistrements correspondants sont retournés au client de carte.  
  
    -   SortSpec : S’il existe plusieurs enregistrements qui correspondent à l’expression de recherche, cette spécification détermine l’ordre dans lequel les enregistrements sont retournés. Ce paramètre est facultatif.  
  
    -   ChampsRequête : Permet aux clients de l’adaptateur récupérer des valeurs pour uniquement un sous-ensemble des champs dans les enregistrements retournés. Ce paramètre est facultatif.  
  
        > [!NOTE]
        >  Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] prend en charge l’utilisation de noms d’origine dans le paramètre QueryField dans l’opération de requête sur le composant de gestion  
  
-   **Mise à jour**. Les clients de l’adaptateur peuvent mettre à jour un ou plusieurs enregistrements dans un composant d’entreprise.  
  
-   **Supprimer**. Les clients de l’adaptateur peuvent supprimer un ou plusieurs enregistrements dans un composant métier en spécifiant un jeu d’ID ou en fournissant une expression de recherche.  
  
    > [!NOTE]
    >  En plus des autres paramètres, les opérations de requête, Update et Delete prennent également un paramètre ViewMode. Ce paramètre accepte un entier qui détermine les autorisations d’accès de l’utilisateur. Pour plus d’informations sur le paramètre ViewMode et les autres paramètres pour ces opérations, consultez le message de demande de composant d’activité sous [des schémas de Message pour des opérations de composant Business](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md).  
  
 Pour plus d’informations sur :  
  
-   Exécution d’opérations sur les composants d’entreprise à l’aide de BizTalk Server, consultez [exécuter des opérations sur les composants de métier à l’aide de BizTalk Server et de l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-using-the-siebel-adapter-in-biztalk.md).  
  
-   Exécution d’opérations sur les composants d’entreprise à l’aide du modèle de service WCF, consultez [exécuter des opérations sur les composants d’entreprise avec l’adaptateur Siebel à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-with-the-siebel-adapter-using-wcf-service.md).  
  
-   Exécution d’opérations sur les composants d’entreprise à l’aide du modèle de canal WCF, consultez [exécuter des opérations sur les composants d’entreprise avec l’adaptateur Siebel à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-with-the-siebel-adapter-using-wcf-service.md).  
  
-   Exécution d’opérations sur les composants d’entreprise à l’aide de structures de message et les actions de SOAP, consultez [des schémas de Message pour des opérations de composant Business](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md).  
  
## <a name="operations-on-business-components-with-mvg-fields"></a>Opérations sur les composants d’entreprise avec des champs de groupe à valeurs multiples  
 Un composant d’entreprise Siebel peut également récupérer des champs à partir d’autres composants d’entreprise à l’aide de jointures ou des groupes à valeurs multiples (multiples). Outre les opérations Insert, requête, Update et Delete qui sont signalées pour tous les composants de l’entreprise, les clients de l’adaptateur peuvent effectuer les opérations suivantes sur les composants d’entreprise Siebel à l’aide de l’adaptateur :  
  
-   **Associer**. Les clients de l’adaptateur peuvent associer des enregistrements en spécifiant les expressions de recherche pour le parent et enfant. Cela s’applique uniquement aux composants d’entreprise avec des champs de groupe à valeurs multiples. Les expressions de recherche doivent filtrer un seul enregistrement de composants d’entreprise à la fois parent et enfant.  
  
-   **Dissocier**. Les clients de l’adaptateur peuvent dissocier les enregistrements en spécifiant les expressions de recherche pour le parent et enfant. Cela s’applique uniquement aux composants d’entreprise avec des champs de groupe à valeurs multiples. Les expressions de recherche doivent filtrer un seul enregistrement de composants d’entreprise à la fois parent et enfant.  
  
-   **Query_ [MVG_Child_Business_Comp]**. Les clients de l’adaptateur peuvent interroger les enregistrements enfants qui sont associés à un enregistrement parent en spécifiant l’enregistrement parent et le nom de champ de groupe à valeurs multiples. Cela s’applique uniquement aux composants d’entreprise avec des champs de groupe à valeurs multiples.  
  
    > [!NOTE]
    >  En plus des autres paramètres, ces opérations prennent également un paramètre de ViewMode. Ce paramètre accepte un entier qui détermine les autorisations d’accès de l’utilisateur. Pour plus d’informations sur le paramètre ViewMode et les autres paramètres pour ces opérations, consultez le message de demande de composant d’activité sous [des schémas de Message pour des opérations de composant Business](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md).  
  
 Pour plus d’informations sur :  
  
-   Ces opérations sur les composants d’entreprise à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [exécuter des opérations sur les composants d’entreprise avec l’adaptateur Siebel et les champs de groupe à valeurs multiples à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-with-mvg-fields-using-the-siebel-adapter.md).  
  
-   Ces opérations sur les composants d’entreprise à l’aide du modèle de service WCF, consultez [exécuter des opérations sur les composants d’entreprise avec des champs de groupe à valeurs multiples avec l’adaptateur Siebel à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-siebel/work-with-mvp-fields-using-the-siebel-adapter-and-the-wcf-service-model.md).  
  
-   Message des structures et des actions SOAP pour ces opérations, consultez [des schémas de Message pour des opérations de composant Business](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md).  
  
## <a name="operations-on-business-components-with-picklist-fields"></a>Opérations sur les composants d’entreprise avec des champs de la liste de choix  
 Types de champ de liste de choix dans les composants d’entreprise constituent une collection de valeurs à partir de laquelle les utilisateurs peuvent récupérer des valeurs spécifiques à transmettre au système Siebel. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] prend en charge les opérations sur un composant d’entreprise avec des champs de la liste de choix. Les opérations sur les composants d’entreprise contenant des champs de la liste de choix sont les mêmes que les opérations sur tout autre composant de l’entreprise, comme décrit dans le paragraphe précédent. Toutefois, en fonction du type de liste de sélection, les valeurs d’entrée pour le composant de gestion peuvent varier. Pour plus d’informations sur les listes de choix et leurs types, reportez-vous à la documentation de Siebel.  
  
 Un des types de liste de choix, listes déroulantes délimitées statiques, sont signalées par les adaptateurs comme une liste de choix énumérée type dans les métadonnées générées par l’adaptateur au moment du design. Contient un ensemble statique de valeurs qui doivent être spécifiés pour le type de liste déroulante au moment de l’exécution.  Lors de la spécifier une valeur pour une liste de choix limitée statique, vous devez toujours spécifier une valeur qui appartient au jeu.  
  
 La structure du message pour effectuer des opérations sur les composants d’entreprise avec des champs de la liste de choix est similaire aux structures de message pour les opérations sur tout autre composant de l’entreprise, comme décrit dans [des schémas de Message pour les opérations de composant d’entreprise](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md).  
  
 Pour plus d’informations sur :  
  
-   Structures des composants d’entreprise contenant des champs de la liste de choix de message, consultez [schéma de Message pour les opérations de liste de choix](../../adapters-and-accelerators/adapter-siebel/message-schema-for-picklist-operations.md).  
  
-   Exécution d’opérations sur un composant d’entreprise qui contient des champs de la liste de choix, consultez [exécuter des opérations sur les composants d’entreprise avec les champs de liste de choix à l’aide de BizTalk Server et de l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/run-tasks-on-business-components-with-picklist-fields-using-the-siebel-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)