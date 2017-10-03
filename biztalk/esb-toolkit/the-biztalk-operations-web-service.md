---
title: "Les opérations de BizTalk de Service Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af38815f-f643-4598-9148-6499071d12e4
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d09fb2cdcca83e8a9f2e4e7704178d40a915065
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-biztalk-operations-web-service"></a>Le Service Web d’opérations BizTalk
Le service Web de Microsoft BizTalk opérations expose des informations sur les objets et les messages dans BizTalk Server. Le nom du service est **ESB.BizTalkOperationsService**, et le service expose un large éventail de méthodes qui retournent des éléments, telles qu’une liste des ordinateurs hôtes, des orchestrations, des applications et l’état de l’application BizTalk.  
  
 Les méthodes suivantes sont disponibles :  
  
-   **Applications**. Cette méthode ne prend aucun paramètre et retourne le nom et la description de toutes les applications BizTalk installées comme une collection de **BTApplication** objets.  
  
-   **ApplicationStatus**. Cette méthode prend comme paramètre le nom de l’application, et il retourne des informations sur l’application BizTalk spécifiée comme un **BTSysStatus** instance. Ces informations comprennent des orchestrations, ports d’envoi, emplacements de réception et détails de l’hôte.  
  
-   **GetLiveMessageBody**. Cette méthode prend comme paramètres un ID de message et un ID d’instance, et elle retourne le corps du message à partir de l’environnement d’exploitation comme un **BTMsgBody** instance.  
  
-   **GetMessageInstances**. Cette méthode prend comme paramètre, le type de message et retourne comme une collection de tous les messages correspondants **BTMsgInstance** objets.  
  
-   **GetOrchestrationInstances**. Cette méthode prend comme paramètres le nom d’une orchestration, et il retourne une collection de **BTOrchestrationInstance** l’objet qui contient les détails des orchestrations correspondantes.  
  
-   **GetTrackedMessageBody**. Cette méthode prend comme paramètre un GUID du message et retourne le corps du message en tant qu’un **BTMsgBody** de l’instance après son traitement dans BizTalk Server.  
  
-   **Hôtes**. Cette méthode prend comme paramètre le nom d’un ordinateur hôte, et il retourne des informations sur l’instance d’hôte spécifié comme une collection de **BTHost** instances. Utilisez une chaîne vide pour le paramètre de nom d’hôte pour retourner des informations sur toutes les instances d’hôte.  
  
-   **MessageFlowTree**. Cette méthode prend comme paramètre un ID d’instance, et il renvoie des informations sur le flux de messages pour le message en tant qu’un **RouteTreeNode** instance.  
  
-   **Orchestrations**. Cette méthode prend comme paramètre le nom d’une orchestration, et il retourne toutes les informations de cette orchestration comme une **BTSysStatus** instance. Une chaîne vide pour le paramètre de nom d’orchestration permet de retourner des informations sur toutes les orchestrations.  
  
-   **ReceiveLocations**. Cette méthode prend comme paramètre le nom d’un emplacement de réception, et il retourne toutes les informations pour la correspondance des emplacements en tant qu’un **BTSysStatus** instance. Utilisez une chaîne vide pour le paramètre de nom des emplacements de réception à retourner des informations sur tous les emplacements.  
  
-   **ReceiveLocationsByDescription**. Cette méthode prend comme paramètre, la description d’un emplacement de réception, et il retourne toutes les informations pour la correspondance des emplacements en tant qu’un **BTSysStatus** instance. Utilisez une chaîne vide pour le paramètre description pour retourner des informations sur tous les emplacements.  
  
-   **Ports d’envoi**. Cette méthode prend comme paramètre le nom d’un port d’envoi, et elle retourne toutes les informations pour la correspondance des ports comme un **BTSysStatus** instance. Utilisez une chaîne vide pour le paramètre de nom de port envoi pour renvoyer des informations sur tous les ports.  
  
-   **SendPortsByDescription**. Cette méthode prend comme paramètre, la description d’un port d’envoi, et elle retourne toutes les informations pour la correspondance des ports comme un **BTSysStatus** instance. Utilisez une chaîne vide pour le paramètre description pour retourner des informations sur tous les ports.  
  
-   **StatusChanged**. Cette méthode prend comme paramètre un horodatage, et il renvoie des informations sur les objets BizTalk (par exemple, les ports, les hôtes et les orchestrations) modifiées depuis la date spécifiée en tant qu’un **BTSysStatus** instance.  
  
-   **SystemStatus**. Cette méthode ne prend aucun paramètre et retourne des informations complètes sur l’état du système BizTalk en tant qu’un **BTSysStatus** instance.  
  
-   **UpdateReceiveLocationDescription**. Cette méthode met à jour la description d’un emplacement de réception spécifié à l’aide des valeurs de paramètre qui contient le nom de l’application, le nom de port de réception, le nom d’emplacement de réception et description de l’emplacement de réception. Il retourne une chaîne qui indique le résultat de l’opération. Notez que l’application cliente de test lit ces informations à partir de son fichier App.config.  
  
-   **UpdateSendPortDescription**. Cette méthode met à jour la description d’un port d’envoi spécifié à l’aide des valeurs de paramètre qui contient le nom de port d’envoi et la description de port d’envoi. Il retourne une chaîne qui indique le résultat de l’opération. Notez que l’application cliente de test lit ces informations à partir de son fichier App.config.  
  
## <a name="configuring-the-biztalk-operations-web-service"></a>Configuration du Service Web d’opérations BizTalk  
 Le service Web d’opérations BizTalk soit communique directement avec les bases de données de gestion BizTalk Server à l’aide de Windows Management Instrumentation (WMI) ou qu’il utilise les opérations de BizTalk et les API de l’Explorateur pour obtenir les informations que nécessaires. Par conséquent, il se peut que vous devez vous assurer que votre système répond aux conditions suivantes et que vous configurez les paramètres d’autorisation de sécurité suivants :  
  
-   Définir le **allowOverride** attribut dans le fichier Web.config de niveau de l’ordinateur pour **false** pour vous assurer que les développeurs ne peut pas modifier le niveau de confiance de leurs applications.  
  
-   Par défaut, le service Web d’opérations BizTalk n’est pas configuré pour exiger SSL Secure Sockets Layer () lors de l’accès par les clients. Vous devez configurer le service afin qu’il exige SSL pour l’accès client et protéger la connexion entre l’ordinateur hôte du service Web des Internet Information Services (IIS) et l’ordinateur exécutant SQL Server qui héberge la base de données BizTalkMgmtDb à l’aide au niveau du réseau IPSec et les autorisations de liste (ACL) de contrôle de l’accès approprié au niveau du fichier.  
  
-   Les utilisateurs l’accès au service Web d’opérations BizTalk doivent être membres du groupe Administrateurs de BizTalk Server par défaut pour certaines méthodes et les membres du groupe d’utilisateurs d’applications BizTalk par défaut pour les autres méthodes.  
  
-   Il se peut que vous devez vous assurer que le service Web d’opérations BizTalk réside dans un répertoire virtuel IIS nommé ESB.BizTalkOperationsService qui a l’accès anonyme est désactivé.  
  
-   Les utilisateurs doivent avoir **sélectionnez** autorisation dans SQL Server pour plusieurs tables se trouve dans la base de données BizTalkMgmtDb et la base de données BizTalkMsgBoxDb. SQL Server Management Studio permet de définir les autorisations suivantes :  
  
    -   Dans la base de données BizTalkMgmtDb, configurer le rôle de base de données BTS_ADMIN_USERS avec **sélectionnez** autorisation sur les tables suivantes :  
  
        -   adm_Server2HostMapping  
  
        -   adm_Server  
  
        -   adm_hostInstance  
  
    -   Dans la base de données BizTalkMsgBoxDb, configurer le rôle de base de données BTS_ADMIN_USER avec **sélectionnez** autorisation sur la table ProcessHeartbeats.  
  
 Dans SQL Server Management Studio, vous pouvez configurer les autorisations requises. Pour ce faire, développez **sécurité** dans l’arborescence du volet gauche de l’Explorateur d’objets, développez **rôles**, développez **DatabaseRoles**, sélectionnez le rôle BTS_ADMIN_USERS, puis modifiez le propriétés de ce rôle, comme illustré dans la Figure 1.  
  
 ![SQL Server Management Studio](../esb-toolkit/media/ch4-sqlservermgmtstudio.gif "SQLServerMgmtStudio de chapitre 4")  
  
 **Figure 1**  
  
 **Modifiez les autorisations pour le rôle de base de données BTS_ADMIN_USERS dans Microsoft SQL Server Management Studio**  
  
> [!NOTE]
>  Vous devez configurer ce service pour utiliser la sécurité intégrée de Windows et s’exécuter sous le compte SERVICE réseau intégré. Vous devez également activer l’authentification Kerberos sur votre serveur Web IIS pour qu’il envoie l’en-tête **Negotiate, NTLM** au client. Pour plus d’informations, consultez [comment configurer IIS pour prendre en charge le protocole Kerberos et le protocole NTLM pour l’authentification réseau](http://go.microsoft.com/fwlink/?LinkId=186430)([http://go.microsoft.com/fwlink/?LinkId=186430](http://go.microsoft.com/fwlink/?LinkId=186430)).  
>   
>  Par défaut, le service Web d’opérations BizTalk n’est pas configuré pour exiger le protocole SSL lors de l’accès par les clients. Vous devez configurer le service afin qu’il exige SSL pour l’accès client et la protection de la connexion entre l’ordinateur hôte du service Web IIS et le serveur qui héberge le service UDDI à l’aide au niveau du réseau IPSec et les autorisations de liste ACL appropriées au niveau des fichiers.