---
title: "Créer l’URI de connexion Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91eb49fa-2a69-470b-b96d-dc3a6ffafef6
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3f6e3be6604e8786ff9481ab463f27a31bf1e5b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-the-oracle-e-business-suite-connection-uri"></a>Créer l’URI de connexion Oracle E-Business Suite
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] URI de connexion contient des propriétés de l’adaptateur utilise pour établir une connexion à Oracle E-Business Suite et essentiellement la base de données Oracle sous-jacente. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge deux manières de se connecter à la base de données Oracle : à l’aide de tnsnames.ora et sans utiliser de tnsnames.ora. Selon le type de connectivité, le format de l’URI de connexion est également différent. Cette rubrique fournit des informations sur l’URI de connexion Oracle et fournit également des liens vers d’autres rubriques qui expliquent comment spécifier un URI dans différents scénarios de programmation.  
  
 Oracle E-Business Suite est une couche d’application qui interagit avec une base de données Oracle sous-jacente et est classée dans différentes applications tels que Finances et ressources humaines, en fonction des besoins différents au sein d’une organisation. Chacune de ces applications fournit divers « types » permettant aux utilisateurs d’entrer des données dans la base de données Oracle. Accès à ces écrans est restreint par association d’utilisateurs à un contexte d’application qui comprend l’ID d’organisation à laquelle un utilisateur appartient, « responsable » associé à l’utilisateur et le nom de l’application Oracle E-Business Suite que l’utilisateur souhaite appeler. Même si l’adaptateur se connecte directement à la base de données sous-jacente et n’utilise pas de formulaires pour interagir avec Oracle E-Business Suite, la définition du contexte de l’application est obligatoire lorsque vous effectuez des opérations sur les artefacts d’Oracle E-Business Suite. Par conséquent, pour se connecter à la suite Oracle E-Business et le sous-jacent de la base de données Oracle, à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], vous devez :  
  
-   Spécifiez un URI de connexion pour se connecter à Oracle E-Business Suite et de la base de données Oracle. Lors de l’établissement d’une connexion, vous pouvez choisir de spécifier les informations d’identification pour Oracle E-Business Suite ou de la base de données Oracle.  
  
-   Définissez le contexte d’application pour l’utilisateur. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose certaines propriétés de liaison qui acceptent les informations d’identification de la responsabilité. Pour plus d’informations sur ces propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md). Pour plus d’informations sur la définition du contexte d’application, consultez [définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
 Cette section fournit des informations sur la façon de spécifier l’URI de connexion pour se connecter à la base de données sous-jacente à l’aide de tnsnames.ora et sans utiliser de tnsnames.ora. Il fournit également des informations sur l’utilisation de l’URI de connexion pour se connecter à Oracle E-Business Suite.  
  
## <a name="connect-using-tnsnamesora"></a>Connectez-vous à l’aide de tnsnames.ora  
  
> [!IMPORTANT]
>  -   Pour cette approche, vous devez ajouter l’entrée de nom de service réseau dans le fichier tnsnames.ora sur l’ordinateur avec le client de l’adaptateur installé. Pour plus d’informations sur l’entrée de nom de service réseau, consultez [configurer le client Oracle pour l’adaptateur de E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-oracle-client-for-the-e-business-suite-adapter.md).  
> -   En raison d’une limitation du Client Oracle, le **DataSourceName** paramètre (nom de service réseau) dans l’URI de connexion ne peut pas contenir plus de 39 caractères si vous effectuez des opérations dans une transaction. Par conséquent, assurez-vous que la valeur spécifiée pour le **DataSourceName** paramètre est inférieur ou égal à 39 caractères si vous allez effectuer les opérations dans une transaction.  
  
 La connexion de l’URI peut contenir un nom de service réseau Oracle qui est utilisé pour identifier le service Oracle E-Business Suite avec lequel vous souhaitez vous connecter. Le client Oracle résout le nom de service réseau Oracle que vous fournissez dans l’URI de connexion aux informations de connexion pour un service Oracle E-Business Suite, en fonction d’une hiérarchie de méthodes d’affectation de noms Oracle que vous configurez pour utiliser. Une méthode d’affectation de noms commune est appelée d’affectation de noms locale. Dans l’attribution de noms local, le client Oracle utilise un fichier appelé tnsnames.ora pour résoudre le nom de service réseau Oracle.  
  
 Un point de terminaison standard adresse URI dans [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] est représenté en tant que : `scheme://userauthparams@hostinfoparams`, où :  
  
-   schéma est le nom du schéma.  
  
-   userauthparams est une collection nom-valeur des paramètres requis pour l’authentification utilisateur par le point de terminaison.  
  
-   hostinfoparams est informations requises pour établir la connexion à l’hôte ; par exemple, un nom de service réseau.  
  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] connexion URI conforme au format de base et est implémentée comme suit :  
  
```  
oracleebs://User=[USER_NAME];Password=[PASSWORD]@[NET_SERVICE_NAME]  
```  
  
 Le tableau suivant décrit les propriétés contenues dans l’URI de connexion.  
  
|Propriété URI de connexion|Catégorie| Description|  
|-----------------------------|--------------|-----------------|  
|[NOM_UTILISATEUR]|userauthparams|Le nom d’utilisateur à utiliser pour l’authentification. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose un **ClientCredentialType** liaison de la propriété qui spécifie le type d’informations d’identification du client Oracle le client spécifie pour établir une connexion. Les valeurs possibles pour le **ClientCredentialType** propriété de liaison sont **base de données** et **EBusiness**. Selon la valeur de cette propriété de liaison, vous devez spécifier les informations d’identification appropriées. Pour plus d’informations, consultez [l’URI de connexion et les informations d’identification Oracle](#BKMK_OraCreds). **Remarque :** vous devez définir le **AcceptCredentialsInUri** liaison de propriété **true** pour spécifier le nom d’utilisateur et un mot de passe dans l’URI de connexion. **Remarque :** le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne conserve pas le cas de la valeur que vous entrez le nom d’utilisateur lorsqu’il se connecte à Oracle E-Business Suite. Le nom d’utilisateur est passé pour Oracle E-Business Suite à l’aide de règles standard de SQL * Plus. Toutefois, si vous souhaitez que la casse du nom d’utilisateur doivent être conservés ou si vous souhaitez entrer un nom d’utilisateur contenant des caractères spéciaux, vous devez spécifier la valeur entre guillemets doubles.|  
|[MOT DE PASSE]|userauthparams|Le mot de passe à utiliser pour l’authentification. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose un **ClientCredentialType** liaison de la propriété qui spécifie le type d’informations d’identification du client Oracle le client spécifie pour établir une connexion. Si le **ClientCredentialType** est définie sur **base de données**, les clients doivent spécifier le mot de passe pour un utilisateur de base de données Oracle. Si le **ClientCredentialType** est définie sur **EBusiness**, les clients doivent spécifier le mot de passe pour un utilisateur Oracle E-Business Suite. **Remarque :** le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne conserve pas la casse de la valeur que vous entrez le mot de passe lorsqu’il se connecte à Oracle E-Business Suite. Le nom d’utilisateur est passé pour Oracle E-Business Suite à l’aide de règles standard de SQL * Plus. Toutefois, si vous souhaitez que le cas du mot de passe doivent être conservés ou si vous souhaitez entrer un mot de passe contenant des caractères spéciaux, vous devez spécifier la valeur entre guillemets doubles.|  
|[NET_SERVICE_NAME]|hostinfoparams|Un nom de service réseau qui est spécifié dans le fichier tnsnames.ora sur l’ordinateur où le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] est installé. Pour plus d’informations sur les noms de service réseau et tnsnames.ora, consultez [configurer le client Oracle pour l’adaptateur de E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-oracle-client-for-the-e-business-suite-adapter.md).|  
  
## <a name="connect-without-using-tnsnamesora"></a>Se connecter sans utiliser de tnsnames.ora  
  
> [!IMPORTANT]
>  -   Pour cette approche, vous devez pas l’entrée de nom de service réseau dans le tnsnames.ora. En outre, il est même inutile pour que le fichier tnsnames.ora sur l’ordinateur avec le client de l’adaptateur installé.  
> -   Ce mode de connectivité n’est pas pris en charge si vous effectuez des opérations dans une transaction. Il s’agit d’une limitation du Client Oracle.  
  
 Un point de terminaison standard adresse URI dans [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] est représenté en tant que : `scheme://userauthparams@hostinfoparams`, où :  
  
-   schéma est le nom du schéma.  
  
-   userauthparams est une collection nom-valeur des paramètres requis pour l’authentification utilisateur par le point de terminaison.  
  
-   hostinfoparams est informations requises pour établir la connexion à l’hôte ; par exemple, nom du serveur, numéro de port, etc.  
  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] connexion URI conforme au format de base et est implémentée comme suit :  
  
```  
oracleebs://User=[USER_NAME];Password=[PASSWORD]@[SERVER_NAME]:[PORT_NUMBER]/[SERVICE_NAME]/[SERVICE_TYPE]   
```  
  
 Le tableau suivant décrit les propriétés contenues dans l’URI de connexion.  
  
|Propriété URI de connexion|Catégorie| Description|  
|-----------------------------|--------------|-----------------|  
|[NOM_UTILISATEUR]|userauthparams|Le nom d’utilisateur à utiliser pour l’authentification. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose un **ClientCredentialType** liaison de la propriété qui spécifie le type d’informations d’identification du client Oracle le client spécifie pour établir une connexion. Les valeurs possibles pour le **ClientCredentialType** propriété de liaison sont **base de données** et **EBusiness**. Selon la valeur de cette propriété de liaison, vous devez spécifier les informations d’identification appropriées. Pour plus d’informations, consultez [l’URI de connexion et les informations d’identification Oracle](#BKMK_OraCreds). **Remarque :** vous devez définir le **AcceptCredentialsInUri** liaison de propriété **true** pour spécifier le nom d’utilisateur et un mot de passe dans l’URI de connexion. **Remarque :** le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne conserve pas le cas de la valeur que vous entrez le nom d’utilisateur lorsqu’il se connecte à Oracle E-Business Suite. Le nom d’utilisateur est passé pour Oracle E-Business Suite à l’aide de règles standard de SQL * Plus. Toutefois, si vous souhaitez que la casse du nom d’utilisateur doivent être conservés ou si vous souhaitez entrer un nom d’utilisateur contenant des caractères spéciaux, vous devez spécifier la valeur entre guillemets doubles.|  
|[MOT DE PASSE]|userauthparams|Le mot de passe à utiliser pour l’authentification. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose un **ClientCredentialType** liaison de la propriété qui spécifie le type d’informations d’identification du client Oracle le client spécifie pour établir une connexion. Si le **ClientCredentialType** est définie sur **base de données**, les clients doivent spécifier le mot de passe pour un utilisateur de base de données Oracle. Si le **ClientCredentialType** est définie sur **EBusiness**, les clients doivent spécifier le mot de passe pour un utilisateur Oracle E-Business Suite. **Remarque :** le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne conserve pas la casse de la valeur que vous entrez le mot de passe lorsqu’il se connecte à Oracle E-Business Suite. Le nom d’utilisateur est passé pour Oracle E-Business Suite à l’aide de règles standard de SQL * Plus. Toutefois, si vous souhaitez que le cas du mot de passe doivent être conservés ou si vous souhaitez entrer un mot de passe contenant des caractères spéciaux, vous devez spécifier la valeur entre guillemets doubles.|  
|[NOM_SERVEUR]|hostinfoparams|Nom du serveur sur lequel s’exécute Oracle E-Business Suite. Ce champ est obligatoire.|  
|[NUMÉRO_PORT]|hostinfoparams|Le port d’écoute de réseau Oracle. La valeur par défaut 1521.|  
|[NOM_SERVICE]|hostinfoparams|Le nom du service de base de données Oracle. Ce champ est obligatoire.|  
|[SERVICE_TYPE]|hostinfoparams|Le type de service Oracle. Les valeurs possibles sont **dédié** ou **partagé**. Un service dédié utilise un processus serveur dédié pour servir les processus qu’un seul utilisateur. Un service partagé utilise un processus serveur partagé qui peut servir à plusieurs processus utilisateur. Valeur par défaut est **dédié**.|  
  
##  <a name="BKMK_OraCreds"></a>L’URI de connexion et les informations d’identification Oracle  
 Par défaut, le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] lève une exception lorsque les informations d’identification Oracle sont spécifiées dans l’URI de connexion. Il s’agit, car ces informations d’identification sont représentées sous forme de texte brut dans l’URI de connexion, et ceci pose un risque de sécurité. Vous pouvez définir le **AcceptCredentialsInUri** liaison de propriété contrôle si l’URI de connexion peut contenir des informations d’identification pour la base de données Oracle. Si le **AcceptCredentialsInUri** propriété **false**, qui est la valeur par défaut, le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] lève une exception si l’URI de connexion contient des informations d’identification Oracle ; si la propriété est **true**, aucune exception n’est levée.  
  
> [!IMPORTANT]
>  En raison des risques de sécurité générés en passant les informations d’identification dans les chaînes en tant que texte brut, vous devez éviter de spécifier des informations d’identification de connexion de base de données Oracle dans l’URI de connexion. Pour plus d’informations sur la façon de fournir en toute sécurité les informations d’identification pour la base de données Oracle, consultez [sécuriser vos applications Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/secure-your-oracle-ebs-applications.md).  
  
 Vous pouvez également choisir de spécifier les informations d’identification de base de données ou les informations d’identification Oracle E-Business Suite pour établir une connexion à Oracle E-Business Suite. L’adaptateur expose trois propriétés de liaison pour activer ce comportement : **ClientCredentialType**, **OracleUserName**, **OraclePassword**.  
  
 Les valeurs possibles pour le **ClientCredentialType** propriété de liaison sont **base de données** et **EBusiness**.  
  
-   Si le **ClientCredentialType** est définie sur **base de données**, les clients doivent spécifier les informations d’identification de base de données.  
  
-   Si le **ClientCredentialType** est définie sur **EBusiness**, les clients doivent spécifier les informations d’identification Oracle E-Business Suite. Dans ce cas, les clients de l’adaptateur doivent spécifier également les informations d’identification de base de données pour le **OracleUserName** et **OraclePassword** propriétés de liaison.  
  
> [!IMPORTANT]
>  Dans les scénarios où les clients de l’adaptateur spécifient les informations d’identification de base de données pour se connecter à Oracle E-Business Suite en définissant le **ClientCredentialType** liaison de propriété **base de données**, mais appelle Oracle Artefact de E-Business Suite, les valeurs spécifiées pour **OracleUserName** et **OraclePassword** propriétés de liaison sont utilisées pour définir le contexte de l’application. Définition du contexte de l’application est obligatoire pour l’appel d’artefacts dans Oracle E-Business Suite. Pour plus d’informations sur la définition du contexte d’application, consultez [définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
## <a name="using-reserved-characters-in-the-connection-uri"></a>À l’aide de caractères réservés dans l’URI de connexion  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne prend pas en charge la spécification d’une URI qui comporte des caractères spéciaux pour une des valeurs de paramètre de connexion. Si les valeurs de paramètre de connexion contiennent des caractères spéciaux, assurez-vous que vous effectuez l’une des opérations suivantes :  
  
-   Si vous spécifiez l’URI dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] à l’aide de [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], vous devez les spécifier en tant que-est dans le **propriétés URI** onglet, autrement dit, sans utiliser de caractères d’échappement. Si vous spécifiez l’URI directement dans le **configurer un URI** champ et les paramètres de connexion contiennent des caractères réservés, vous devez spécifier les paramètres de connexion à l’aide de caractères d’échappement corrects.  
  
-   Si vous spécifiez l’URI lors de la création d’un envoi ou port de réception [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration et les paramètres de connexion contiennent des caractères réservés, vous devez spécifier les paramètres de connexion à l’aide de caractères d’échappement corrects.  
  
## <a name="using-the-connection-uri-to-connect-to-oracle-e-business-suite"></a>À l’aide de l’URI de connexion pour se connecter à Oracle E-Business Suite  
 Voici un exemple d’URI de connexion pour [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] à l’aide de tnsnames.ora.  
  
```  
oracleebs://ADAPTER  
```  
  
 Dans cet exemple, l’adaptateur est un nom de service réseau associé avec les informations de nom de SERVICE et de connexion pour la base de données Oracle dans tnsnames.ora.  
  
 Voici un exemple d’URI de connexion pour [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] sans utiliser de tnsnames.ora.  
  
```  
oracleebs://yourOracleServer:1521/yourOracleDatabaseServiceName/Dedicated  
```  
  
 Dans cet exemple, le nom du serveur est « yourOracleServer » et le nom du service est « yourOracleDatabaseServiceName ».  
  
 Pour plus d’informations sur la façon d’établir une connexion à Oracle E-Business Suite lorsque vous :  
  
-   Utilisez le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], consultez [se connecter à Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md).  
  
-   Configurer un port d’envoi ou de réception du port (emplacement) dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution, consultez [configurer manuellement une liaison de port physique à l’adaptateur Oracle E-Business](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer le client Oracle pour l’adaptateur de E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-oracle-client-for-the-e-business-suite-adapter.md)   
 [Se connecter à Oracle E-Business Suite à l’aide de l’authentification Windows](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)  
 [Créer une connexion à Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md)