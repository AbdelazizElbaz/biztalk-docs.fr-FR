---
title: "Créer l’URI de connexion système Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection URI
- connecting to Siebel, using the connection URI
- how to, connect using connection URI
- connecting using connection URI
ms.assetid: 8cc78149-1c20-40db-aece-aab520ee04e7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9370ba739c9edc0fc80c6fa3dcfdfc9d8349c75e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-the-siebel-system-connection-uri"></a>Créer l’URI de connexion système Siebel
Le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] URI de connexion contient des propriétés de l’adaptateur utilise pour établir une connexion au système Siebel.  
  
 Cette rubrique fournit des informations sur l’URI de connexion Siebel et fournit également des liens vers d’autres rubriques qui expliquent comment spécifier un URI de connexion dans différents scénarios de programmation.  
  
## <a name="connection-uri-for-the-siebel-adapter"></a>URI de connexion pour l’adaptateur Siebel  
 Un type [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] adresse de point de terminaison URI est représenté comme suit :  
  
```  
scheme://userinfoparams@hostinfoparams?query_string  
```  
  
 L’URI d’adresse de point de terminaison contient les composants suivants :  
  
-   schéma est le nom du schéma.  
  
-   userinfoparams est une collection nom-valeur des paramètres requis pour l’authentification utilisateur par le point de terminaison.  
  
-   hostinfoparams est informations requises pour établir la connexion à l’hôte ; par exemple, un chemin d’accès.  
  
-   QUERY_STRING est une collection nom-valeur facultative de paramètres délimités par un point d’interrogation ( ?).  
  
 L’URI de connexion Siebel respecte le format général et est implémentée comme suit :  
  
```  
siebel://Username=[USER_NAME];Password=[PASSWORD]@[SERVER]:[PORT]?SiebelObjectManager=[SIEBEL_OBJECT_MANAGER_NAME]&SiebelEnterpriseServer=[SERVER_NAME]&Language=[LANGUAGE]&Transport=[TRANSPORT]&Encryption=[ENCRYPTION]&Compression=[COMPRESSION]&SiebelServer=[SIEBEL_SERVER_NAME]&SiebelRepository=[SIEBEL_REPOSITORY_NAME]  
```  
  
 Les sections suivantes décrivent les propriétés implémentées pour chaque composant de l’URI de connexion Siebel.  
  
### <a name="the-scheme-for-the-siebel-connection-uri"></a>Le schéma pour l’URI de connexion Siebel  
 Le schéma de l’URI de connexion Siebel est « siebel ».  
  
### <a name="user-information-in-the-siebel-connection-uri"></a>Informations utilisateur dans l’URI de connexion Siebel  
 Par défaut, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] lève une exception lorsque les informations d’identification du système Siebel sont spécifiées dans l’URI de connexion. Il s’agit, car ces informations d’identification sont représentées sous forme de texte brut, ce qui constitue un risque de sécurité inhérent. Vous pouvez définir le **AcceptCredentialsInUri** liaison de propriété contrôle si l’URI de connexion peut contenir des informations d’identification. Si le **AcceptCredentialsInUri** propriété **false**, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] lève une exception si l’URI de connexion contient des informations d’identification ; si la propriété est **true**, aucune exception n’est levée.  
  
> [!IMPORTANT]
>  En raison des risques de sécurité posés en passant les informations d’identification dans les chaînes en tant que texte brut, il est préférable de ne pas spécifier des informations d’identification du système Siebel dans l’URI de connexion.  
  
 Il existe plusieurs façons pour fournir des informations d’identification du système Siebel sans les spécifier dans l’URI de connexion.  
  
-   Dans le code, vous pouvez définir le **ClientCredentials** propriété sur l’objet approprié.  
  
-   Lorsque vous utilisez la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], vous pouvez entrer les informations d’identification en sélectionnant le **sécurité** onglet de la **configurer l’adaptateur** boîte de dialogue.  
  
-   Lorsque vous spécifiez un port d’envoi ou réception de liaison de l’emplacement dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution, vous pouvez entrer les informations d’identification en sélectionnant le **sécurité** onglet de la boîte de dialogue appropriée.  
  
 Les informations d’utilisateur (userinfoparams) dans la connexion Siebel QU'URI est représenté comme une collection nom-valeur des paramètres requis pour l’authentification utilisateur. Le tableau suivant décrit ces paramètres.  
  
|Propriété| Description|  
|--------------|-----------------|  
|Utilisateur|Le nom d’utilisateur sur le système Siebel. Cette valeur respecte la casse. Vous devez définir le **AcceptCredentialsInUri** liaison de propriété **true** pour spécifier le nom d’utilisateur et un mot de passe dans l’URI de connexion. **Remarque :** le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] préserve la casse de la valeur que vous entrez le nom d’utilisateur lorsqu’il ouvre une connexion sur le système Siebel.|  
|Mot de passe|Le mot de passe pour l’utilisateur sur le système Siebel. Cette valeur respecte la casse. Vous devez définir le **AcceptCredentialsInUri** liaison de propriété **true** pour spécifier le nom d’utilisateur et un mot de passe dans l’URI de connexion. **Remarque :** le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] préserve la casse de la valeur que vous entrez le mot de passe lorsqu’il ouvre une connexion sur le système Siebel.|  
  
### <a name="host-information-in-the-siebel-connection-uri"></a>Informations sur l’hôte dans l’URI de connexion Siebel  
 Les informations d’hôte Siebel (hostinfoparams) spécifient l’adresse du système Siebel dans le format suivant : [serveur] : [PORT]. Selon la version de serveur Siebel, les informations d’hôte Siebel accepte des valeurs différentes :  
  
-   **Pour Siebel version 7.5 et versions antérieure**, le paramètre informations d’hôte prend le nom de l’ordinateur sur le serveur de passerelle Siebel est installé et le numéro de port de passerelle Siebel.  
  
-   **Pour Siebel 7.7 et versions ultérieures**, le paramètre informations d’hôte prend le nom de l’ordinateur sur lequel le Siebel server est installé et la connexion Siebel numéro de port service broker.  
  
    > [!IMPORTANT]
    >  Lorsque vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour vous connecter à un système Siebel, les informations d’hôte doivent être fournies pour la propriété de connexion « SiebelGateway ».  
  
### <a name="query-information-in-the-siebel-connection-uri"></a>Informations de requête dans l’URI de connexion Siebel  
 Les informations de requête (query_string) dans l’URI de connexion Siebel permet de spécifier les propriétés de connexion supplémentaires.  
  
|Propriété| Description|  
|--------------|-----------------|  
|SiebelObjectManager|Nom du Gestionnaire d’objets Siebel sur le serveur d’entreprise. Ce paramètre est obligatoire.|  
|SiebelEnterpriseServer|Le nom de serveur de l’entreprise Siebel. Ce paramètre est obligatoire.|  
|Langage|La langue du Gestionnaire d’objets. Ce paramètre est facultatif. S’il n’est pas spécifié, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] fournit une valeur par défaut (FRA).|  
|Transport|Le transport ; seul tcpip est pris en charge. Ce paramètre est facultatif. S’il n’est pas spécifié, le système Siebel fournit une valeur par défaut (TCP/IP).|  
|Chiffrement|Le type de chiffrement à utiliser entre le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] et le système Siebel. Valeurs prises en charge sont none, mscrypto, ou rsa. Ce paramètre est facultatif. S’il n’est pas spécifié, le système Siebel fournit une valeur par défaut (aucun).|  
|Compression|L’algorithme de compression à utiliser entre le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] et le système Siebel. Valeurs prises en charge sont none ou zlib. Ce paramètre est facultatif. S’il n’est pas spécifié, le système Siebel fournit une valeur par défaut (zlib).|  
|SiebelServer|Le serveur Siebel. Requis pour toutes les connexions de serveur Siebel 7.5 (7.5.2, 7.5.3, etc..) ; dans le cas contraire, ne définissez pas ce paramètre.|  
|SiebelRepository|Le référentiel Siebel. Requis si plusieurs référentiels existe sur le serveur ; Sinon, facultatif. **Remarque :** s’il existe plusieurs référentiels sur le serveur, vous devez spécifier un référentiel cible dans le paramètre SiebelRepository.|  
  
 Pour plus d’informations sur les paramètres de Siebel qui sont définies dans les informations de requête, consultez votre documentation Siebel.  
  
## <a name="using-reserved-characters-in-the-connection-uri"></a>À l’aide de caractères réservés dans l’URI de connexion  
 Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] ne prend pas en charge la spécification d’une URI qui comporte des caractères spéciaux pour une des valeurs de paramètre de connexion. Si les valeurs de paramètre de connexion contiennent des caractères spéciaux, assurez-vous que vous effectuez l’une des opérations suivantes :  
  
-   Si vous spécifiez l’URI dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] à l’aide de [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], vous devez les spécifier en tant que-est dans le **propriétés URI** onglet, autrement dit, sans utiliser de caractères d’échappement. Si vous spécifiez l’URI directement dans le **configurer un URI** champ et les paramètres de connexion contiennent des caractères réservés, vous devez spécifier les paramètres de connexion à l’aide de caractères d’échappement corrects.  
  
-   Si vous spécifiez l’URI lors de la création d’un envoi ou port de réception [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration et les paramètres de connexion contiennent des caractères réservés, vous devez spécifier les paramètres de connexion à l’aide de caractères d’échappement corrects.  
  
## <a name="using-the-connection-uri-to-connect-to-the-siebel-system"></a>À l’aide de l’URI de connexion pour se connecter au système Siebel  
 Voici un exemple Siebel URI de connexion.  
  
```  
siebel://Username=YourUserName;Password=YourPassword@Siebel_server:1234?SiebelObjectManager=obj_mgr&SiebelEnterpriseServer=entserver&Language=enu  
```  
  
> [!NOTE]
>  Cet exemple d’URI contient les informations d’identification du système Siebel ; Vous devez définir le **AcceptCredentialsInUri** liaison de propriété **true** à utiliser une URI qui contient les informations d’identification de connexion.  
  
 Pour plus d’informations sur la façon d’établir une connexion au système Siebel (y compris la définition des propriétés de connexion) lorsque vous :  
  
-   Utilisez le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], consultez [obtenir les métadonnées pour les opérations Siebel dans Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md).  
  
-   Configurer un port d’envoi ou de réception du port (emplacement) dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution, consultez [configurer manuellement une liaison de port physique à l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/manually-configure-a-physical-port-binding-to-the-siebel-adapter.md).
  
-   Utilisez le modèle de canal WCF dans une solution de programmation, consultez [créer un canal à l’aide de Siebel](../../adapters-and-accelerators/adapter-siebel/create-a-channel-using-siebel.md).  
  
-   Utilisez le modèle de service WCF dans une solution de programmation, consultez [configurer un Client WCF pour un système Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md).  
  
-   Utilisez WCF Service Model Metadata Utility Tool (svcutil.exe), voir [à l’aide de l’utilitaire de métadonnées ServiceModel avec l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/use-the-servicemodel-metadata-utility-with-the-siebel-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une connexion au système Siebel](../../adapters-and-accelerators/adapter-siebel/create-a-connection-to-the-siebel-system.md)   
[Développer vos applications Siebel](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)   
 [Développer des Applications Siebel à l’aide de la modèle3 de canal WCF](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-channel-model3.md)   
 [Développer des applications SQL à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)