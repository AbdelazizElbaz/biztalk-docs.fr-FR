---
title: Adaptateur de messagerie Service Bus | Documents Microsoft
description: "Envoyer et recevoir des messages à l’aide de l’adaptateur Azure SB-Messaging dans BizTalk Server"
ms.custom: 
ms.date: 11/21/2017
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
ms.openlocfilehash: 1775606a911d8ce23fd2999ad367053c4f8f72de
ms.sourcegitcommit: f65e8ed2b8c18cded26b9d60868fb6a56bcc1205
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sb-messaging-adapter"></a>Adaptateur SB-Messaging
Le Bus de Service (**SB-Messaging**) carte est utilisée pour recevoir et envoyer des entités Service Bus, comme les files d’attente, rubriques et les relais. Vous pouvez utiliser la **SB-Messaging** adaptateur pour se connecter à votre site [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vers Azure.

**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 2**, Service Bus Premium est prise en charge. Lorsque vous configurez un port d’envoi à l’aide de cette carte, vous pouvez envoyer des messages vers des rubriques et files d’attente partitionnées. 

## <a name="authenticating-with-service-bus"></a>L’authentification avec Service Bus
Service Bus fournit deux méthodes d’authentification : 

- Service de contrôle d’accès (ACS) 
- Signature d’accès partagé (SAS)

Nous vous recommandons de s’authentifier auprès de Service Bus à l’aide de la Signature d’accès partagé (SAS). La valeur de clé d’accès partagé est répertoriée dans le [portail Azure](https://portal.azure.com).

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

Consultez [New-AzureSBNamespace](https://docs.microsoft.com/powershell/module/Azure/New-AzureSBNamespace) pour obtenir des conseils.

## <a name="receive-messages-from-service-bus"></a>Recevoir des messages de Service Bus
  
1. Dans la console Administration de BizTalk Server, développez **groupe BizTalk**, développez **Applications**, puis développez votre application. 

2. Avec le bouton droit **Ports de réception**, sélectionnez **nouveau**, puis sélectionnez **unidirectionnel port de réception**. 

3. Donnez-lui un nom, puis sélectionnez **emplacements de réception**. 

4. Sélectionnez **nouveau**, lui donner un **nom**. Dans le **Transport** section, sélectionnez **SB-Messaging** à partir de la **Type** liste déroulante et sélectionnez **configurer**.  
  
5. Configurer le **général** propriétés :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**URL de file d’attente ou d’un abonnement**|Spécifier l’URL où la file d’attente Service Bus est déployée. En règle générale, l’URL est au format suivant :<br /><br /> `sb://<namespace>.servicebus.windows.net/<queue_name>`|  
    |**Open Timeout**|Spécifie une valeur de période indiquant le temps nécessaire pour qu’une opération d’ouverture de canal soit réalisée.<br /><br /> **Valeur par défaut :** 1 minute|  
    |**Fermer le délai d’attente**|Spécifie une valeur de période indiquant le temps nécessaire pour qu’une opération de fermeture soit réalisée.<br /><br /> **Valeur par défaut :** 1 minute|  
    |**Délai de réception**|Spécifie une valeur de période indiquant le temps nécessaire pour qu’une opération de réception soit réalisée.<br /><br /> **Valeur par défaut :** 10 minutes|  
    |**Nombre de prérécupérations**|Spécifie le nombre de messages reçus simultanément en provenance de la file d’attente Service Bus ou d’une rubrique. Le préchargement permet au client de la file d’attente ou de l’abonnement de charger des messages supplémentaires à partir du service lorsque celui-ci effectue une opération de réception. Le client stocke ces messages dans un cache local. La taille du cache est déterminée par la valeur spécifiée ici pour la propriété Nombre de préchargements.<br /><br /> Pour plus d’informations, reportez-vous à la section « Préchargement » à [https://azure.microsoft.com/documentation/articles/service-bus-performance-improvements/](https://azure.microsoft.com/documentation/articles/service-bus-performance-improvements/)<br /><br /> **Valeur par défaut :** -1|  
    |**Utiliser la Session**|Activer cette case à cocher pour utiliser une session Service Bus afin de recevoir des messages en provenance d’une file d’attente ou d’un abonnement.|  
  
6.  Configurer le **authentification** propriétés :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Service de contrôle d’accès**|Sélectionnez cette option afin d'utiliser ACS pour l'authentification et fournir les valeurs suivantes :<br /><br /> -Entrez l’URI STS du Service de contrôle Service Bus accès. En règle générale, l’URI est au format suivant :<br /><br /> `https://<namespace>-sb.accesscontrol.windows.net/`<br /><br /> -Entrez le nom de l’émetteur pour l’espace de noms Service Bus.<br /><br /> -Entrez la clé de l’émetteur pour l’espace de noms Service Bus.|  
    |**Signature d’accès partagé** (new compter [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)])|Sélectionnez cette option pour utiliser la signature d'accès partagé (SAP) pour l'authentification, et fournissez la valeur de clé et le nom de clé SAS.|  
  
7.  Dans le **propriétés** sous l’onglet du **Namespace pour les propriétés du Message réparti**, entrez l’espace de noms que l’adaptateur utilise pour écrire les propriétés de message réparti en tant que propriétés de contexte de message sur le message reçu par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Si vous souhaitez promouvoir les propriétés de message réparti, sélectionnez le **promouvoir les propriétés de Message réparti** case à cocher.  
  
8.  Sélectionnez **OK**.  
  
9. Sélectionnez votre **Gestionnaire de réception**et le **pipeline de réception**. Sélectionnez **OK** pour enregistrer vos modifications. [Créer un emplacement de réception](../core/how-to-create-a-receive-location.md) fournit quelques conseils.  
  
## <a name="send-messages-to-service-bus"></a>Envoyer des messages à Service Bus
  
1.  Dans la console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, sélectionnez **nouveau**, puis sélectionnez **port d’envoi unidirectionnel statique**.

    [Créer un Port d’envoi](../core/how-to-create-a-send-port2.md) fournit quelques conseils.

2. Entrez un **nom**. Dans **Transport**, définissez le **Type** à **SB-Messaging**, puis sélectionnez **configurer**. 
  
3.  Configurer le **général** propriétés :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**URL de destination**|Entrez l’URL où la file d’attente du Bus de Service est déployé. En règle générale, l’URL est au format suivant :<br /><br /> `sb://<namespace>.servicebus.windows.net/<queue_name>`|  
    |**Intervalle de vidage de lot**|Spécifie une valeur de période indiquant l’intervalle dans lequel les lots de messages envoyés vers une file d’attente ou une rubrique sont vidés. La valeur par défaut est 20 millisecondes.<br /><br /> Pour plus d’informations sur le traitement par lots en ce qui concerne les rubriques et files d’attente du Bus de Service, consultez le **le traitement par lots côté Client** section à [https://azure.microsoft.com/documentation/articles/service-bus-performance-improvements](https://azure.microsoft.com/documentation/articles/service-bus-performance-improvements).|  
    |**Open Timeout**|Spécifie une valeur de période indiquant le temps nécessaire pour qu’une opération d’ouverture de canal soit réalisée.<br /><br /> **Valeur par défaut :** 1 minute|  
    |**Un délai d’envoi**|Spécifie une valeur de période indiquant le temps nécessaire pour qu’une opération d’envoi soit réalisée.<br /><br /> **Valeur par défaut :** 1 minute|  
    |**Fermer le délai d’attente**|Spécifie une valeur de période indiquant le temps nécessaire pour qu’une opération de fermeture soit réalisée.<br /><br /> **Valeur par défaut :** 1 minute|  
  
4.  Configurer le **authentification** propriétés : 
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Service de contrôle d’accès**|Sélectionnez cette option afin d'utiliser ACS pour l'authentification et fournir les valeurs suivantes :<br /><br /> -Entrez l’URI STS du Service de contrôle Service Bus accès. En règle générale, l’URI est au format suivant :<br /><br /> `https://<namespace>-sb.accesscontrol.windows.net/`<br /><br /> -Entrez le nom de l’émetteur pour l’espace de noms Service Bus.<br /><br /> -Entrez la clé de l’émetteur pour l’espace de noms Service Bus.|  
    |**Signature d’accès partagé** (new compter [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)])|Sélectionnez cette option pour utiliser la signature d'accès partagé (SAP) pour l'authentification, et fournissez la valeur de clé et le nom de clé SAS.|  
  
5.  Dans le **propriétés** , entrez la **Namespace de l’utilisateur défini les propriétés du Message réparti** qui contient les propriétés de contexte de message BizTalk que vous souhaitez écrire sur le message sortant vers Bus de service. Toutes les propriétés de l’espace de noms sont écrites dans le message en tant que propriétés de Message réparti définies par l’utilisateur. L’adaptateur ignore l’espace de noms lors de l’écriture des propriétés comme propriétés de message réparti. Il utilise l’espace de noms uniquement pour déterminer quelles propriétés écrire.  
  
     Vous pouvez également entrer les valeurs pour les propriétés BrokeredMessage. Ces propriétés sont décrites sur [propriétés BrokeredMessage](https://docs.microsoft.com/dotnet/api/microsoft.servicebus.messaging.brokeredmessage), y compris le **clé de Partition**.
  
6.  Sélectionnez **OK** pour enregistrer vos modifications.  
  
## <a name="see-also"></a>Voir aussi
[À l’aide des adaptateurs](../core/using-adapters.md)