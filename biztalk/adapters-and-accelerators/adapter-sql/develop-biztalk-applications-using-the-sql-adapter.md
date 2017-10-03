---
title: "Développer des applications BizTalk à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5471f28e-bce1-4295-b56d-954690e60749
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9963764a298246c5a236d10b6010feee8497278f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-biztalk-applications-using-the-sql-adapter"></a>Développer des applications BizTalk à l’aide de l’adaptateur SQL
Développement d’applications BizTalk implique la création d’un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et à l’aide de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer le schéma XML. Une fois que vous avez généré le schéma, vous pouvez utiliser le routage basé sur le contenu (CBR) ou créer des orchestrations BizTalk pour envoyer et recevoir des messages conformes au schéma généré.  
  
 CBR peut être utilisé dans les scénarios où les messages envoyés à SQL Server nécessitent un traitement intensif. Par exemple, si vous savez que le port de réception reçoit les messages uniquement d’un certain type, vous pouvez ajouter un filtre au port d’envoi pour router les messages qui correspondent à l’expression de filtre pour le port d’envoi.  
  
 Dans les orchestrations BizTalk, vous créez envoi et ports de réception pour envoyer et recevoir des messages vers et depuis le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], qui à son tour envoie des messages à [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Cette section fournit des informations sur l’utilisation des orchestrations BizTalk pour effectuer des opérations sur l’utilisation de SQL Server le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] à son tour utilise le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], ce qui peut interagir avec une liaison WCF.  
  
> [!IMPORTANT]
>  Pour utiliser le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous devez toujours définir la **EnableBizTalkCompatibilityMode** liaison de propriété **True**. Pour plus d’informations sur la définition des propriétés de liaison, consultez [configurer les propriétés de liaison de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Conditions préalables pour créer des applications SQL à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md) 
  
-   [Blocs de construction pour développer des applications BizTalk à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md) 
  
-   [INSERT, Update, Delete et sélectionnez les opérations sur les Tables et vues à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/insert-update-delete-and-select-on-tables-and-views-with-the-sql-adapter.md)  
  
-   [Exécuter des opérations sur les Tables et vues avec des Types de données volumineux à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/run-operations-on-tables-and-views-with-large-data-types-using-the-sql-adapter.md)  
  
-   [Exécuter des procédures stockées dans SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-biztalk-server.md)  
  
-   [Exécuter des procédures stockées avec un paramètre unique](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-with-a-single-xml-parameter-in-sql-using-biztalk.md)  
  
-   [Exécutez ayant de procédures stockées une clause FOR XML Clause dans SQL Server à l’aide de BizTalk server](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-having-a-for-xml-clause-in-sql-server-using-biztalk.md)  
  
-   [Exécuter des opérations composites sur SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/run-composite-operations-on-sql-server-using-biztalk-server.md)  
  
-   [Appeler des fonctions scalaires dans SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/invoke-scalar-functions-in-sql-server-using-biztalk-server.md)  
  
-   [Appeler des fonctions table dans SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/invoke-table-valued-functions-in-sql-server-using-biztalk-server.md) 
  
-   [Réalisation d’opérations ExecuteReader, ExecuteScalar ou ExecuteNonQuery opérations à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md)  
  
-   [Recherche de serveur SQL Server à l’aide de l’adaptateur SQL avec BizTalk Server](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)  
  
-   [Recevoir des Notifications de requête SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)  
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications SQL](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)