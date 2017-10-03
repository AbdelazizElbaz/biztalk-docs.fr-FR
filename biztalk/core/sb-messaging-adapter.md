---
title: Adaptateur SB-Messaging | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c06c4934-45b2-4f6f-9d19-3ebd937c32ae
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fb2eb8f532d72708dfca199f0eef794afdf77df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sb-messaging-adapter"></a>Adaptateur SB-Messaging
Le Bus de Service (**SB-Messaging**) carte est utilisée pour recevoir et envoyer des entités Service Bus, comme les files d’attente, rubriques et les relais. Vous pouvez utiliser la **SB-Messaging** pour établir la connectivité entre les cartes [!INCLUDE[winazure](../includes/winazure-md.md)] et locales [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ce qui permettant aux utilisateurs de créer une application hybride typique. Les rubriques de cette section fournissent des instructions sur la façon de configurer un **SB-Messaging** emplacement de réception et un port d’envoi pour recevoir et envoyer des messages à partir des entités Service Bus.  

## <a name="before-you-get-started"></a>Avant de commencer
Service Bus fournit deux méthodes d’authentification : Service de contrôle d’accès (ACS) et la Signature d’accès partagé (SAS). Notre recommandation est d’utiliser la Signature d’accès partagé (SAS) lors de l’authentification avec Service Bus. La valeur de clé d’accès partagé est répertoriée dans le [portail Azure](https://portal.azure.com).

Lorsque vous créez un espace de noms Service Bus, l’espace de noms Access Control (ACS) n’est pas créé automatiquement. Pour utiliser le contrôle d’accès, vous devez les valeurs de nom de l’émetteur et la clé de l’émetteur de cet espace de noms. Ces valeurs sont disponibles lorsque vous créez un nouvel espace de noms ACS à l’aide de Windows PowerShell. Ces valeurs ne sont pas répertoriées dans le portail Azure.

Pour utiliser des services ACS pour l’authentification et obtenir les valeurs de nom de l’émetteur et la clé de l’émetteur, les étapes générales sont les suivantes :

1. Installer le [applets de commande Azure Powershell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/).
2. Ajoutez votre compte Azure :`Add-AzureAccount`
3. Retourne le nom de votre abonnement :`get-azuresubscription`
4. Sélectionnez votre abonnement :`select-azuresubscription <name of your subscription>` 
5. Créer un nouvel espace de noms :`new-azuresbnamespace <name for the service bus> "Location" -CreateACSNamespace $true -NamespaceType Messaging`

    Exemple :`new-azuresbnamespace biztalksbnamespace "South Central US" -CreateACSNamespace $true -NamespaceType Messaging`
      
5. Lorsque l’espace de noms ACS est créé (ce qui peut prendre plusieurs minutes), les valeurs IssuerName et IssuerKey sont répertoriés dans la chaîne de connexion : 

    ```
    Name                  : biztalksbnamespace
    Region                : South Central US
    DefaultKey            : abcdefghijklmnopqrstuvwxyz
    Status                : Active
    CreatedAt             : 10/18/2016 9:36:30 PM
    AcsManagementEndpoint : https://biztalksbnamespace-sb.accesscontrol.windows.net/
    ServiceBusEndpoint    : https://biztalksbnamespace.servicebus.windows.net/
    ConnectionString      : Endpoint=sb://biztalksbnamespace.servicebus.windows.net/;SharedSecretIssuer=owner;SharedSecretValue=abcdefghijklmnopqrstuvwxyz
    NamespaceType         : Messaging
    ```
[Nouveau-AzureSBNamespace](https://msdn.microsoft.com/library/dn495165.aspx)

## <a name="receive-messages-from-service-bus"></a>Recevoir des messages de Service Bus
  
Cette section fournit des informations sur la façon de configurer un **SB-Messaging** à l’aide de l’emplacement de réception le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration.  
  
> [!NOTE]
>  Avant d’exécuter la procédure suivante, vous devez avoir déjà ajouté un unidirectionnel port de réception. Consultez [la création d’un port de réception](../core/how-to-create-a-receive-port.md).  

 
1.  Dans la console Administration de BizTalk Server, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**, puis développez l’application sous laquelle créer un emplacement de réception.  
  
2.  Dans le volet gauche, cliquez sur le nœud **Ports de réception** . Dans le volet droit, cliquez avec le bouton droit sur le port de réception auquel vous souhaitez associer le nouvel emplacement de réception, puis cliquez sur **Propriétés**.  
  
3.  Dans le volet gauche de la boîte de dialogue **Propriétés des ports de réception** , sélectionnez **Emplacements de réception**, puis dans le volet droit, cliquez sur **Nouveau** pour créer un emplacement de réception.  
  
4.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Transport** section, sélectionnez **SB-Messaging** à partir de la **Type** liste déroulante , puis cliquez sur **configurer** pour configurer les propriétés de transport pour l’emplacement de réception.  
  
5.  Dans le **propriétés du Transport SB-Messaging** boîte de dialogue le **général** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**URL de file d’attente ou d’un abonnement**|Spécifier l’URL où la file d’attente Service Bus est déployée. En règle générale, l’URL est au format suivant :<br /><br /> `sb://<namespace>.servicebus.windows.net/<queue_name>`|  
    |**Open Timeout**|Spécifie une valeur de période indiquant le temps nécessaire pour qu’une opération d’ouverture de canal soit réalisée.<br /><br /> **Valeur par défaut :** 1 minute|  
    |**Fermer le délai d’attente**|Spécifie une valeur de période indiquant le temps nécessaire pour qu’une opération de fermeture soit réalisée.<br /><br /> **Valeur par défaut :** 1 minute|  
    |**Délai de réception**|Spécifie une valeur de période indiquant le temps nécessaire pour qu’une opération de réception soit réalisée.<br /><br /> **Valeur par défaut :** 10 minutes|  
    |**Nombre de prérécupérations**|Spécifie le nombre de messages reçus simultanément en provenance de la file d’attente Service Bus ou d’une rubrique. Le préchargement permet au client de la file d’attente ou de l’abonnement de charger des messages supplémentaires à partir du service lorsque celui-ci effectue une opération de réception. Le client stocke ces messages dans un cache local. La taille du cache est déterminée par la valeur spécifiée ici pour la propriété Nombre de préchargements.<br /><br /> Pour plus d’informations, reportez-vous à la section « Préchargement » à [https://azure.microsoft.com/documentation/articles/service-bus-performance-improvements/](https://azure.microsoft.com/documentation/articles/service-bus-performance-improvements/)<br /><br /> **Valeur par défaut :** -1|  
    |**Utiliser la Session**|Activer cette case à cocher pour utiliser une session Service Bus afin de recevoir des messages en provenance d’une file d’attente ou d’un abonnement.|  
  
6.  Dans le **authentification** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Service de contrôle d’accès**|Sélectionnez cette option afin d'utiliser ACS pour l'authentification et fournir les valeurs suivantes :<br /><br /> -Entrez l’URI STS du Service de contrôle Service Bus accès. En règle générale, l’URI est au format suivant :<br /><br /> `https://<namespace>-sb.accesscontrol.windows.net/`<br /><br /> -Entrez le nom de l’émetteur pour l’espace de noms Service Bus.<br /><br /> -Entrez la clé de l’émetteur pour l’espace de noms Service Bus.|  
    |**Signature d’accès partagé** (new compter [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)])|Sélectionnez cette option pour utiliser la signature d'accès partagé (SAP) pour l'authentification, et fournissez la valeur de clé et le nom de clé SAS.|  
  
7.  Dans le **propriétés** sous l’onglet du **Namespace pour les propriétés du Message réparti** Indiquez l’espace de noms que l’adaptateur utilise pour écrire les propriétés de message réparti en tant que propriétés de contexte de message sur le message reçu par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. En outre, si vous souhaitez promouvoir les propriétés de message réparti, sélectionnez le **promouvoir les propriétés de Message réparti** case à cocher.  
  
8.  Cliquez sur **OK**.  
  
9. Entrez les valeurs appropriées dans la boîte de dialogue **Propriétés de l'emplacement de réception** pour terminer la configuration de l'emplacement de réception, puis cliquez sur **OK** pour enregistrer les paramètres. Pour plus d’informations sur la **propriétés des emplacements de réception** boîte de dialogue, consultez [la création d’un emplacement de réception](../core/how-to-create-a-receive-location.md).  
  
## <a name="send-messages-to-service-bus"></a>Envoyer des messages à Service Bus
Cette section fournit des informations sur la façon de configurer un **SB-Messaging** port d’envoi utilisant le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration.  
  
1.  Dans la console Administration de BizTalk Server, créez un port d’envoi ou double-cliquez sur un port d’envoi existant pour le modifier. Pour plus d’informations, consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md). Configurez toutes les options de port d’envoi et spécifiez **SB-Messaging** pour le **Type** option dans le **Transport** section de la **général** onglet.  
  
2.  Sur le **général** sous l’onglet du **Transport** , cliquez sur le **configurer** bouton.  
  
3.  Dans le **propriétés du Transport SB-Messaging** boîte de dialogue le **général** onglet, spécifiez les éléments suivants :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**URL de destination**|Entrez l’URL où la file d’attente du Bus de Service est déployé. En règle générale, l’URL est au format suivant :<br /><br /> `sb://<namespace>.servicebus.windows.net/<queue_name>`|  
    |**Intervalle de vidage de lot**|Spécifie une valeur de période indiquant l’intervalle dans lequel les lots de messages envoyés vers une file d’attente ou une rubrique sont vidés. La valeur par défaut est 20 millisecondes.<br /><br /> Pour plus d’informations sur le traitement par lots en ce qui concerne les rubriques et files d’attente du Bus de Service, consultez le **le traitement par lots côté Client** section à [https://azure.microsoft.com/documentation/articles/service-bus-performance-improvements](https://azure.microsoft.com/documentation/articles/service-bus-performance-improvements).|  
    |**Open Timeout**|Spécifie une valeur de période indiquant le temps nécessaire pour qu’une opération d’ouverture de canal soit réalisée.<br /><br /> **Valeur par défaut :** 1 minute|  
    |**Un délai d’envoi**|Spécifie une valeur de période indiquant le temps nécessaire pour qu’une opération d’envoi soit réalisée.<br /><br /> **Valeur par défaut :** 1 minute|  
    |**Fermer le délai d’attente**|Spécifie une valeur de période indiquant le temps nécessaire pour qu’une opération de fermeture soit réalisée.<br /><br /> **Valeur par défaut :** 1 minute|  
  
4.  Dans le **authentification** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Service de contrôle d’accès**|Sélectionnez cette option afin d'utiliser ACS pour l'authentification et fournir les valeurs suivantes :<br /><br /> -Entrez l’URI STS du Service de contrôle Service Bus accès. En règle générale, l’URI est au format suivant :<br /><br /> `https://<namespace>-sb.accesscontrol.windows.net/`<br /><br /> -Entrez le nom de l’émetteur pour l’espace de noms Service Bus.<br /><br /> -Entrez la clé de l’émetteur pour l’espace de noms Service Bus.|  
    |**Signature d’accès partagé** (new compter [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)])|Sélectionnez cette option pour utiliser la signature d'accès partagé (SAP) pour l'authentification, et fournissez la valeur de clé et le nom de clé SAS.|  
  
5.  Dans le **propriétés** sous l’onglet du **Namespace de l’utilisateur défini les propriétés du Message réparti** Indiquez l’espace de noms qui contient les propriétés de contexte de message BizTalk que vous souhaitez écrire en tant que propriétés de Message réparti définies par l’utilisateur sur le message sortant envoyé à la file d’attente du Bus de Service. Toutes les propriétés appartenant à l’espace de noms sont écrites dans le message comme propriétés de message réparti définies par l’utilisateur. L’adaptateur ignore l’espace de noms lors de l’écriture des propriétés comme propriétés de message réparti. Il utilise l’espace de noms uniquement pour déterminer quelles propriétés écrire.  
  
     Vous pouvez également spécifier les valeurs pour les propriétés BrokeredMessage. Pour plus d’informations sur les propriétés, consultez [propriétés BrokeredMessage](https://msdn.microsoft.com/library/azure/microsoft.servicebus.messaging.brokeredmessage_properties.aspx).  
  
6.  Cliquez sur **OK** et **OK** pour enregistrer les paramètres.  
  
## <a name="see-also"></a>Voir aussi
[À l’aide des adaptateurs](../core/using-adapters.md)