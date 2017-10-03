---
title: "Créer l’URI de connexion de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection URI, basic format of
- connection URI, database credentials and
- connection URI, connecting to the Oracle database
- connection URI
ms.assetid: 17d0a6d3-1b0c-43d6-a705-402c09a78ee0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45f7b0fcc0c83bd4a844ac1a83488e1a3e8d9a65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-the-oracle-database-connection-uri"></a>Créer l’URI de connexion de base de données Oracle
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] URI de connexion contient des propriétés de l’adaptateur utilise pour établir une connexion à la base de données Oracle. Cette rubrique fournit des informations sur la façon de spécifier l’URI de connexion pour se connecter à la base de données Oracle à l’aide de tnsnames.ora et sans utiliser de tnsnames.ora. Il fournit également des informations sur l’utilisation de l’URI de connexion pour se connecter à la base de données Oracle.  
  
## <a name="connection-uri-to-connect-to-the-oracle-database-using-tnsnamesora"></a>URI de connexion pour se connecter à la base de données Oracle à l’aide de tnsnames.ora  
  
> [!IMPORTANT]
>  -   Pour cette approche, vous devez ajouter l’entrée de nom de service réseau dans le fichier tnsnames.ora sur l’ordinateur avec le client de l’adaptateur installé. Pour plus d’informations sur l’entrée de nom de service réseau, consultez [configurer le Client Oracle pour l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md).  
> -   En raison d’une limitation du Client Oracle, le **DataSourceName** paramètre (nom de service réseau) dans l’URI de connexion ne peut pas contenir plus de 39 caractères si vous effectuez des opérations dans une transaction. Par conséquent, assurez-vous que la valeur spécifiée pour le **DataSourceName** paramètre est inférieur ou égal à 39 caractères si vous allez effectuer les opérations dans une transaction.  
  
 Un point de terminaison standard adresse URI dans [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] est représenté en tant que : `scheme://userauthparams@hostinfoparams?query_string`, où :  
  
-   schéma est le nom du schéma.  
  
-   userauthparams est une collection nom-valeur des paramètres requis pour l’authentification utilisateur par le point de terminaison.  
  
-   hostinfoparams est informations requises pour établir la connexion à l’hôte ; par exemple, un chemin d’accès.  
  
-   QUERY_STRING est une collection nom-valeur facultative de paramètres délimités par un point d’interrogation ( ?).  
  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] connexion URI conforme au format de base et est implémentée comme suit :  
  
```  
oracledb://User=[USER_NAME];Password=[PASSWORD]@[NET_SERVICE_NAME]?PollingId=[POLLING_ID]  
```  
  
 Le tableau suivant décrit les propriétés contenues dans l’URI de connexion.  
  
|Propriété URI de connexion|Catégorie| Description|  
|-----------------------------|--------------|-----------------|  
|[NOM_UTILISATEUR]|userauthparams|Le nom d’utilisateur à utiliser pour l’authentification sur la base de données Oracle ; par exemple, SCOTT. Vous devez définir le **AcceptCredentialsInUri** liaison de propriété **true** pour spécifier le nom d’utilisateur et un mot de passe dans l’URI de connexion.<br /><br /> **Remarque** le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] préserve la casse de la valeur que vous entrez le nom d’utilisateur lorsqu’il ouvre une connexion sur la base de données Oracle. Noms d’utilisateur sur la base de données Oracle respectent la casse. Vous devez vous assurer que vous fournissez des noms d’utilisateur Oracle pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] dans le cas attendu par votre base de données Oracle. En règle générale, cela signifie que le nom d’utilisateur dans les informations d’identification SCOTT/TIGER doit être en majuscule : « SCOTT ».|  
|[MOT DE PASSE]|userauthparams|Le mot de passe à utiliser pour l’authentification sur la base de données Oracle ; par exemple, TIGER. Vous devez définir le **AcceptCredentialsInUri** liaison de propriété **true** pour spécifier le nom d’utilisateur et un mot de passe dans l’URI de connexion.<br /><br /> **Remarque** le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] préserve la casse de la valeur que vous entrez le mot de passe lorsqu’il ouvre une connexion sur la base de données Oracle. Pour la version 10g et versions antérieures, les mots de passe sur le système Oracle ne respectent pas la casse.|  
|[NET_SERVICE_NAME]|hostinfoparams|Un nom de service réseau qui est spécifié dans le fichier tnsnames.ora sur l’ordinateur où le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est installé. Pour plus d’informations sur les noms de service réseau et tnsnames.ora, consultez [configurer le Client Oracle pour l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md).|  
|[POLLING_ID]|QUERY_STRING|Chaîne facultative qui doit être ajoutée par l’adaptateur pour l’espace de noms standard de l’opération POLLINGSTMT. Cela vous permet de spécifier un espace de noms unique pour chaque opération d’interrogation lorsqu’un projet contient plusieurs opérations d’interrogation. Il est inutile de spécifier une chaîne PollingId si votre projet contient une seule opération POLLINGSTMT.|  
  
> [!NOTE]
>  Paramètres de requête sont également utilisées dans l’URI de connexion lorsqu’une adresse de point de terminaison est spécifiée pour un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client de l’échange de métadonnées.  
  
## <a name="connection-uri-to-connect-to-the-oracle-database-without-using-tnsnamesora"></a>URI de connexion pour se connecter à la base de données Oracle sans l’aide de tnsnames.ora  
  
> [!IMPORTANT]
>  -   Pour cette approche, le nom de service réseau dans le fichier tnsnames.ora ou le fichier tnsnames.ora réel lui-même n’a pas besoin d’être présents sur l’ordinateur client.  
> -   Ce mode de connectivité n’est pas pris en charge si vous effectuez des opérations dans une transaction. Il s’agit d’une limitation du Client Oracle.  
  
 Un point de terminaison standard adresse URI dans [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] est représenté en tant que : `scheme://userauthparams@hostinfoparams?query_string`, où :  
  
-   schéma est le nom du schéma.  
  
-   userauthparams est une collection nom-valeur des paramètres requis pour l’authentification utilisateur par le point de terminaison.  
  
-   hostinfoparams est informations requises pour établir la connexion à l’hôte ; par exemple, nom du serveur, numéro de port, etc.  
  
-   QUERY_STRING est une collection nom-valeur facultative de paramètres délimités par un point d’interrogation ( ?).  
  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] connexion URI conforme au format de base et est implémentée comme suit :  
  
```  
oracledb://User=[USER_NAME];Password=[PASSWORD]@[SERVER_NAME]:[PORT_NUMBER]/[SERVICE_NAME]/SERVICE_TYPE]?PollingId=[POLLING_ID]  
```  
  
 Le tableau suivant décrit les propriétés contenues dans l’URI de connexion.  
  
|Propriété URI de connexion|Catégorie| Description|  
|-----------------------------|--------------|-----------------|  
|[NOM_UTILISATEUR]|userauthparams|Le nom d’utilisateur à utiliser pour l’authentification sur la base de données Oracle ; par exemple, SCOTT. Vous devez définir le **AcceptCredentialsInUri** liaison de propriété **true** pour spécifier le nom d’utilisateur et un mot de passe dans l’URI de connexion.<br /><br /> **Remarque** le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] préserve la casse de la valeur que vous entrez le nom d’utilisateur lorsqu’il ouvre une connexion sur la base de données Oracle. Noms d’utilisateur sur la base de données Oracle respectent la casse. Vous devez vous assurer que vous fournissez des noms d’utilisateur Oracle pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] dans le cas attendu par votre base de données Oracle. En règle générale, cela signifie que le nom d’utilisateur dans les informations d’identification SCOTT/TIGER doit être en majuscule : « SCOTT ».|  
|[MOT DE PASSE]|userauthparams|Le mot de passe à utiliser pour l’authentification sur la base de données Oracle ; par exemple, TIGER. Vous devez définir le **AcceptCredentialsInUri** liaison de propriété **true** pour spécifier le nom d’utilisateur et un mot de passe dans l’URI de connexion.<br /><br /> **Remarque** le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] préserve la casse de la valeur que vous entrez le mot de passe lorsqu’il ouvre une connexion sur la base de données Oracle. Pour la version 10g et versions antérieures, les mots de passe sur le système Oracle ne respectent pas la casse.|  
|[NOM_SERVEUR]|hostinfoparams|Nom du serveur sur lequel la base de données Oracle est en cours d’exécution. Ce champ est obligatoire.|  
|[NUMÉRO_PORT]|hostinfoparams|Le port d’écoute de réseau Oracle. Si aucune valeur n’est spécifiée, l’adaptateur prend la valeur par défaut 1521.|  
|[NOM_SERVICE]|hostinfoparams|Le nom du service de base de données Oracle. Ce champ est obligatoire.|  
|[SERVICE_TYPE]|hostinfoparams|Le type de service Oracle. Les valeurs possibles sont **dédié** ou **partagé**. Un service dédié utilise un processus serveur dédié pour servir les processus qu’un seul utilisateur. Un service partagé utilise un processus serveur partagé qui peut répondre à plusieurs processus utilisateur. Valeur par défaut est **dédié**.|  
|[POLLING_ID]|QUERY_STRING|Chaîne facultative qui doit être ajoutée par l’adaptateur pour l’espace de noms standard de l’opération POLLINGSTMT. Cela vous permet de spécifier un espace de noms unique pour chaque opération d’interrogation lorsqu’un projet contient plusieurs opérations d’interrogation. Il est inutile de spécifier une chaîne PollingId si votre projet contient une seule opération POLLINGSTMT.|  
  
> [!NOTE]
>  Paramètres de requête sont également utilisées dans l’URI de connexion lorsqu’une adresse de point de terminaison est spécifiée pour un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client de l’échange de métadonnées.  
  
## <a name="oracle-database-credentials-and-the-connection-uri"></a>Informations d’identification de la base de données Oracle et l’URI de connexion  
 Par défaut, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] lève une exception lorsque les informations d’identification de la base de données Oracle sont spécifiées dans l’URI de connexion. Il s’agit, car ces informations d’identification sont représentées sous forme de texte brut dans l’URI de connexion, et ceci pose un risque de sécurité. Vous pouvez définir le **AcceptCredentialsInUri** liaison de propriété contrôle si l’URI de connexion peut contenir des informations d’identification pour la base de données Oracle. Si le **AcceptCredentialsInUri** propriété est **false**, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] lève une exception si l’URI de connexion contient des informations d’identification de la base de données Oracle ; si la propriété **true** , aucune exception n’est levée. Il existe quelques scénarios limités dans lequel il est nécessaire de spécifier des informations d’identification dans la connexion URI ; par exemple, pour recevoir le trafic entrant POLLINGSTMT opération lorsque vous utilisez WCF service modèle ou le modèle de canal WCF. Toutefois, pour la plupart des cas, vous devez éviter en fournissant des informations d’identification dans l’URI de connexion. Pour plus d’informations sur la façon de fournir en toute sécurité les informations d’identification pour la base de données Oracle, consultez [sécuriser vos applications de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md).  
  
> [!IMPORTANT]
>  En raison des risques de sécurité générés en passant les informations d’identification dans les chaînes en tant que texte brut, vous devez éviter de spécifier des informations d’identification de connexion de base de données Oracle dans l’URI de connexion.  
  
## <a name="using-reserved-characters-in-the-connection-uri"></a>À l’aide de caractères réservés dans l’URI de connexion  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne prend pas en charge la spécification d’une URI qui comporte des caractères spéciaux pour une des valeurs de paramètre de connexion. Si les valeurs de paramètre de connexion contiennent des caractères spéciaux, assurez-vous que vous effectuez l’une des opérations suivantes :  
  
-   Si vous spécifiez l’URI dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] à l’aide de [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], vous devez les spécifier en tant que-est dans le **propriétés URI** onglet, autrement dit, sans utiliser de caractères d’échappement. Si vous spécifiez l’URI directement dans le **configurer un URI** champ et les paramètres de connexion contiennent des caractères réservés, vous devez spécifier les paramètres de connexion à l’aide de caractères d’échappement corrects.  
  
-   Si vous spécifiez l’URI lors de la création d’un envoi ou port de réception [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration et les paramètres de connexion contiennent des caractères réservés, vous devez spécifier les paramètres de connexion à l’aide de caractères d’échappement corrects.  
  
## <a name="using-the-connection-uri-to-connect-to-the-oracle-database"></a>À l’aide de l’URI de connexion pour se connecter à la base de données Oracle  
 Voici un exemple d’URI de connexion pour [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
|À l’aide de tnsnames.ora|Sans utiliser de tnsnames.ora|  
|------------------------|--------------------------------|  
|`oracledb://ADAPTER`<br /><br /> Dans cet exemple, l’adaptateur est un nom de service réseau associé avec les informations de nom de SERVICE et de connexion pour la base de données Oracle dans tnsnames.ora.|`oracledb://yourOracleServer:1521/yourOracleDatabaseServiceName/Dedicated`<br /><br /> Dans cet exemple, le nom du serveur est « yourOracleServer » et le nom du service est « yourOracleDatabaseServiceName ».|  
  
 Voici un exemple d’URI de connexion pour une opération POLLINGSTMT. Cet URI inclut un paramètre PollingId pour modifier l’espace de noms de l’opération POLLINGSTMT.  
  
|À l’aide de tnsnames.ora|Sans utiliser de tnsnames.ora|  
|------------------------|--------------------------------|  
|`oracledb://ADAPTER?PollingId=MyPollingNotification1`|`oracledb://yourOracleServer:1521/yourOracleDatabaseServiceName/Dedicated? PollingId=MyPollingNotification1`|  
  
 Pour la connexion ci-dessus URI, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] crée l’espace de noms suivant pour l’opération POLLINGSTMT.  
  
```  
http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTMyPollingNotification1  
```  
  
 Pour plus d’informations sur la façon d’établir une connexion à Oracle de base de données lorsque vous :  
  
-   Utilisez le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], consultez [se connecter à la base de données Oracle dans Visual Studio à l’aide de Consume Adapter Service](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md).  
  
-   Configurer un port d’envoi ou de réception du port (emplacement) dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution, consultez [configurer manuellement une liaison de port physique à l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md).  
  
-   Utilisez le modèle de canal WCF dans une solution de programmation, consultez [créer un canal à l’aide de la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md).  
  
-   Utilisez le modèle de service WCF dans une solution de programmation, consultez [configurer un client de liaison pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-a-client-binding-for-the-oracle-database.md).  
  
-   Utilisez WCF Service Model Metadata Utility Tool (svcutil.exe), voir [utilisant le service Model Metadata Utility Tool avec l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/use-the-servicemodel-metadata-utility-with-the-oracle-db-adapter-in-biztalk.md).  
  
## <a name="see-also"></a>Voir aussi  
[Créer une connexion à la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)   
 [Configurer le Client Oracle pour l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md)