---
title: "Créer l’URI de connexion SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 688e2215-a4d8-4f55-a37c-7d91c3de080f
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f31b6d6919924d3bb4bb1ac6c817c3f3b3d77dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-the-sql-server-connection-uri"></a>Créer l’URI de connexion SQL Server
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] URI de connexion contient des propriétés de l’adaptateur utilise pour établir une connexion à la base de données SQL Server. Cette rubrique fournit des informations sur l’URI de connexion SQL Server et fournit des liens vers d’autres rubriques qui expliquent comment spécifier un URI dans différents scénarios de programmation.  
  
##  <a name="FailoverPartner"></a>L’URI de connexion de l’adaptateur SQL  
 Une adresse de point de terminaison standard URI dans WCF est représentée en tant que : `scheme://hostinfoparams?query_string`, où :  
  
-   schéma est le nom du schéma.  
  
-   hostinfoparams est informations requises pour établir la connexion à l’hôte ; par exemple, un nom de serveur.  
  
-   QUERY_STRING est une collection nom-valeur facultative de paramètres délimités par un point d’interrogation ( ?).  
  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] connexion URI conforme au format de base et est implémentée comme suit :  
  
```  
  
mssql://[Server_Name[:Portno]]/[Database_Instance_Name]/[Database_Name]?FailoverPartner=[Partner_Server_Name]&InboundId=[Inbound_ID]  
```  
  
 WHERE, `mssql` est le schéma pour l’URI de connexion SQL Server.  
  
 Le tableau suivant décrit les propriétés contenues dans l’URI de connexion.  
  
|Propriété URI de connexion|Catégorie| Description|  
|-----------------------------|--------------|-----------------|  
|[NOM_SERVEUR]|hostinfoparams|Nom du serveur sur lequel SQL Server est installé. Si vous ne spécifiez pas une valeur, l’adaptateur suppose que le nom du serveur en tant que « localhost » et établit une connexion avec la base de données SQL Server sur le serveur local.|  
|[NUMÉRO_PORT]|hostinfoparams|Le numéro de port sur lequel la connexion est établie. Si vous ne spécifiez pas une valeur, l’adaptateur se connecte via le port par défaut.|  
|[DATABASE_INSTANCE_NAME]|hostinfoparams|Nom de l’instance de SQL Server pour se connecter à. Si vous ne spécifiez pas une valeur, l’adaptateur se connecte à l’instance de base de données par défaut.|  
|[DATABASE_NAME]|hostinfoparams|Nom de la base de données pour se connecter à. Si vous ne spécifiez pas une valeur, l’adaptateur se connecte à la base de données par défaut.|  
|[PARTNER_SERVER_NAME]|QUERY_STRING|Nom de la base de données de basculement SQL Server pour se connecter à if de la base de données SQL Server principal n’est pas disponible. Pour plus d’informations sur la haute disponibilité par rapport à SQL Server, consultez [mise en miroir de base de données dans SQL Server](https://msdn.microsoft.com/library/5h52hef8.aspx).|  
|[INBOUND_ID]|QUERY_STRING|Un identificateur que vous ajoutez à l’URI pour le rendre unique de connexion. Vous devez fournir ce paramètre de connexion si vous souhaitez générer des métadonnées pour le **TypedPolling** opération entrante. En outre, dans une application BizTalk, si vous disposez de plusieurs d’interrogation de la même base de données, des emplacements de réception entrant ID établit la connexion URI unique, ce qui permet à des clients de l’adaptateur recevoir des messages de l’interrogation de la même base de données sur différents emplacements de réception. Pour plus d’informations, consultez [de réception d’interrogation Messages entre plusieurs Ports réception à partir de SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md).|  
  
> [!NOTE]
>  Pour plus d’informations sur ces propriétés de chaîne de connexion, consultez [propriété SqlConnection.ConnectionString](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectionstring.aspx).
  
## <a name="sql-server-credentials-and-the-connection-uri"></a>Informations d’identification SQL Server et l’URI de connexion  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ne prend pas en charge les informations d’identification en spécifiant l’URI de connexion. Pour plus d’informations sur la spécification des informations d’identification dans les applications qui utilisent la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], consultez [sécuriser vos applications SQL](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md).  
  
## <a name="using-special-characters-in-the-connection-uri"></a>À l’aide de caractères spéciaux dans l’URI de connexion  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ne prend pas en charge la spécification d’une URI qui comporte des caractères spéciaux pour une des valeurs de paramètre de connexion. Si les valeurs de paramètre de connexion contiennent des caractères spéciaux, assurez-vous que vous effectuez l’une des opérations suivantes :  
  
-   Si vous spécifiez l’URI dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] à l’aide de [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], vous devez les spécifier en tant que-est dans le **propriétés URI** onglet, autrement dit, sans utiliser de caractères d’échappement. Si vous spécifiez l’URI directement dans le **configurer un URI** champ et les paramètres de connexion contiennent des caractères spéciaux, vous devez spécifier les paramètres de connexion à l’aide de caractères d’échappement corrects.  
  
     Par exemple, si l’URI de connexion a un paramètre portant le nom `sql server`, vous devez le spécifier en tant que `sql%20server`.  
  
-   Si vous spécifiez l’URI lors de la création d’un envoi ou port de réception [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration et les paramètres de connexion contiennent des caractères spéciaux, vous devez spécifier les paramètres de connexion à l’aide de caractères d’échappement corrects.  
  
## <a name="using-the-connection-uri-to-connect-to-the-sql-server-database"></a>À l’aide de l’URI de connexion pour se connecter à la base de données SQL Server  
 Ce qui suit est un URI de connexion exemple pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
```  
mssql://sql_server/sql_server_instance//  
```  
  
 Dans l’exemple précédent, « sql_server » est le nom de l’ordinateur sur lequel SQL Server est installé, alors que « sql_server_instance » est le nom de l’instance de base de données pour se connecter à. Car aucun nom de base de données est spécifié, l’adaptateur se connecte à la base de données par défaut.  
  
 Voici un exemple d’une connexion URI où la base de données SQL Server est installé sur le même ordinateur que le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Dans cet exemple, l’adaptateur se connecte à la base de données « ma_base_de_données » pour l’instance de base de données « sql_server_instance » sur l’ordinateur local.  
  
```  
mssql://localhost/sql_server_instance/my_database/  
```  
  
 Dans cet exemple, l’adaptateur se connecte à la base de données par défaut pour l’instance par défaut en cours d’exécution sur l’ordinateur local.  
  
```  
mssql://localhost///  
```  
  
 Pour plus d’informations sur la façon de spécifier une connexion à SQL Server de base de données lorsque vous :  
  
-   Utilisez le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], consultez [se connecter à SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-sql-adapter.md).  
  
-   Configurer un port d’envoi ou réception de port (emplacement) dans une solution BizTalk Server, consultez [configurer manuellement une liaison de port physique à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md).
  
-   Utilisez le modèle de canal WCF dans une solution de programmation, consultez [créer un canal à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/create-a-channel-using-the-sql-adapter.md).  
  
-   Utilisez le modèle de service WCF dans une solution de programmation, consultez [configurer une liaison de Client de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications SQL](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)