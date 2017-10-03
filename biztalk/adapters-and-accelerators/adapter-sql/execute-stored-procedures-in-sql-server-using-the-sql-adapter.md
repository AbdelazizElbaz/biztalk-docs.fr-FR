---
title: "Exécuter des procédures stockées dans SQL Server à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 245626a7-f546-4aca-90df-c0579139a872
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65a475d8de1fc30df2e06923ad14bcba0897159e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="execute-stored-procedures-in-sql-server-using-the-sql-adapter"></a>Exécuter des procédures stockées dans SQL Server à l’aide de l’adaptateur SQL
Les procédures stockées CLR dans SQL Server Transact-SQL sont signalées en tant qu’opérations dans [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] sous le **procédures** nœud lors de l’utilisation la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Les noms des opérations exposées par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sont les mêmes que le nom de la procédure stockée dans SQL Server. Tous les paramètres dans la procédure stockée sont exposés dans l’opération correspondante. Le paramètre de sortie contient la valeur de retour de la procédure stockée. Le jeu de résultats de la procédure stockée est un tableau du jeu de données. Pour plus d’informations sur le jeu de données, consultez [http://go.microsoft.com/fwlink/?LinkId=196853](http://go.microsoft.com/fwlink/?LinkId=196853). Les informations de schéma de l’objet cible sont obtenues en tant que partie du message de réponse en cours d’exécution.  
  
 Toutefois, si vous souhaitez obtenir les informations de schéma de l’objet cible au moment du design, vous devez générer les schémas pour les procédures sous le **fortement typée procédures** nœud dans le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Notez que les mêmes procédures stockées sont signalées sous le **procédures** et **fortement typée procédures** nœud. La valeur de retour de la procédure stockée est fortement typé et pas seulement un tableau du jeu de données. Comme les informations de schéma sont disponibles au moment du design, vous pouvez l’utiliser pour mapper le schéma de la procédure stockée à un autre schéma pour une autre opération. Par exemple, vous pouvez mapper le schéma généré pour une procédure fortement typé pour le schéma généré pour l’opération d’insertion sur une table de base de données.  
  
> [!NOTE]
>  Vous ne serez pas en mesure d’afficher les informations de schéma au moment du design pour une procédure stockée fortement typé si :  
>   
>  -   Vous utilisez un curseur, ce qui correspond à une valeur de retour d’une autre procédure stockée, le paramètre d’entrée pour la procédure stockée fortement typée.  
> -   Il s’agit d’une procédure stockée CLR qui effectue certaines opérations sur une table.  
  
## <a name="support-for-stored-procedures-with-for-xml-clause"></a>Prise en charge des procédures stockées avec la Clause FOR XML  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] vous permet également d’exécuter des procédures stockées qui ont une instruction SELECT avec une clause FOR XML. Une clause FOR XML est utilisée dans une instruction SELECT pour retourner les résultats au format XML au lieu d’un ensemble de lignes. Pour plus d’informations sur la clause FOR XML, consultez [http://go.microsoft.com/fwlink/?LinkId=131402](http://go.microsoft.com/fwlink/?LinkId=131402).  
  
> [!NOTE]
>  Le « native » [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] disponible avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] prend en charge uniquement les procédures stockées qui renvoient des données XML, autrement dit, comportent la clause FOR XML dans l’instruction SELECT. Avec la prise en charge pour les procédures stockées avec la clause FOR XML, vous pouvez exécuter ces procédures stockées à l’aide de la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sans apporter de modifications à la définition de procédure stockée.  
  
## <a name="support-for-stored-procedures-with-temporary-tables"></a>Prise en charge des procédures stockées avec les Tables temporaires  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] vous permet de générer des métadonnées pour les procédures stockées qui contiennent des tables temporaires dans leurs définitions. Toutefois, pour ces procédures stockées vous devez générer des métadonnées en sélectionnant les procédures stockées uniquement à partir de la **procédures** nœud, tout en utilisant le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. L’adaptateur ne prend pas en charge les générer des métadonnées pour ces procédures stockées sous la **fortement typée procédures** nœud.  
  
## <a name="support-for-result-sets-containing-columns-without-names-or-with-same-names"></a>Prise en charge des jeux de résultats contenant des colonnes sans nom ou avec le même nom  
 Le tableau suivant répertorie comment les [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] gère les colonnes sans les noms et même dans les jeux de résultats des procédures stockées et des procédures stockées fortement typée.  
  
|Jeu de résultats contient...|Procédure stockée|Fortement typée de procédure stockée|  
|--------------------------|----------------------|--------------------------------------|  
|**Colonnes sans nom**|Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] génère un nom pour la colonne de la façon suivante : un ID unique (GUID) est généré pour la colonne sans «- » (tiret), et ensuite la chaîne GUID préfixée par « C », car le GUID généré peut commencer par un chiffre, mais un nom de balise XML ne peut pas.|Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] génère le nom suivant pour la colonne : « UnNamedColumn [column_index] », où column_index commence à partir de '0'.|  
|**Colonnes avec les mêmes noms**|Les noms des colonnes que la première sont complétés par « _ » (trait de soulignement) suivi d’un GUID aléatoire sans «- » (tiret). Par exemple : «\_[GUID] ».|Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ne prend pas en charge les colonnes avec les mêmes noms dans les jeux de résultats et lève une exception. **Important :** vous devez vous assurer que les noms de colonnes dans un jeu de résultats ont des noms uniques.|  
  
> [!NOTE]
>  En général, il est recommandé que toutes les colonnes dans un résultat défini pour les procédures stockées et fortement typée de procédures stockées doivent être nommés et ont des noms uniques.  
  
 Pour plus d’informations sur :  
  
-   Comment exécuter des procédures stockées, consultez [exécuter des procédures stockées dans SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-biztalk-server.md).  
  
-   Comment exécuter des procédures stockées ayant une clause FOR XML, consultez [exécuter des procédures stockées ayant une clause FOR XML dans SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-having-a-for-xml-clause-in-sql-server-using-biztalk.md).  
  
-   Pour les procédures stockées, les schémas de message, consultez [des schémas de Message pour les procédures et fonctions](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Se connecter à un système SAP à l’aide de l’adaptateur](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)