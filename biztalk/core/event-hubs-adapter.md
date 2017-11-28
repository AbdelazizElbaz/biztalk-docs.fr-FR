---
title: "Utilisation de l’adaptateur de concentrateurs d’événements | Documents Microsoft"
description: "Envoyer et recevoir des messages à l’aide de l’adaptateur Azure Event Hubs dans BizTalk Server"
ms.custom: 
ms.date: 11/16/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: MandiOhlinger
ms.author: plarsen
manager: anneta
ms.openlocfilehash: f394665a40b0a786ef6411b68ff8871e1a683614
ms.sourcegitcommit: f65e8ed2b8c18cded26b9d60868fb6a56bcc1205
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="event-hub-adapter-in-biztalk"></a>Adaptateur de concentrateur d’événements dans BizTalk Server

## <a name="overview"></a>Vue d'ensemble
**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 2**, vous pouvez envoyer et recevoir des messages entre BizTalk Server et Azure Event Hubs. 

Concentrateurs d’événements Azure est une plateforme, de diffusion en continu de données hautement évolutives et peut recevoir et traiter des millions d’événements par seconde. [Quel est le service Event Hubs ? ](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs) fournit plus de détails.

## <a name="prerequisites"></a>Conditions préalables

* Créer un [espace de noms Azure événement concentrateurs et concentrateur d’événements](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-create)
* Créer un [compte de stockage d’objets blob Azure avec un conteneur](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account)
* Installer [Feature Pack 2](https://aka.ms/bts2016fp2) sur votre serveur BizTalk Server

Votre concentrateur d’événements est créée, et que les chaînes de connexion que vous avez besoin pour envoyer et recevoir des événements.

## <a name="send-messages-to-event-hubs"></a>Envoyer des messages à des concentrateurs d’événements

1.  Dans la console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, sélectionnez **nouveau**, puis sélectionnez **port d’envoi unidirectionnel statique**.

    [Créer un Port d’envoi](../core/how-to-create-a-send-port2.md) fournit quelques conseils.

2. Entrez un **nom**. Dans **Transport**, définissez le **Type** à **EventHub**, puis sélectionnez **configurer**. 

3. Configurer le **compte Azure** propriétés : 

    |Utiliser|Pour effectuer cette opération|  
    |---|---|  
    | **Ouverture de session** | Connectez-vous à votre compte Azure |
    | **Abonnement** | Sélectionnez l’abonnement qui a votre espace de noms EventHubs |
    | **Groupe de ressources** | Sélectionnez votre groupe de ressources dont votre espace de noms EventHubs |

4. Configurer le **point de terminaison** propriétés : 

    |Utiliser|Pour effectuer cette opération|  
    |---|---|  
    | **Espace de noms** | Sélectionnez votre espace de noms de concentrateurs d’événements, qui ressemble à sb : / /*youreventhubnamespace*.servicebus.windows.net/ |
    | **Nom** | Sélectionnez le nom de votre Hub d’événements (qui a été créé dans votre espace de noms de concentrateurs d’événements) |
    | **Clé de Partition par défaut** | Ce paramètre est facultatif. [Guide de programmation de concentrateurs d’événements](https://docs.microsoft.com/azure/event-hubs/event-hubs-programming-guide) fournit plus de détails sur cette clé. |
    | **Authentification** | **Signature d’accès Namespace** est la valeur par défaut et utilise automatiquement le RootManageSharedAccessKey qui est créé lorsque vous créez un espace de noms de concentrateurs d’événements.<br/><br/>**Signature d’accès entité** est la stratégie SAP que vous pouvez créer à l’événement Hub niveau (pas les concentrateurs d’événements espace de noms). <br/><br/>[Vue d’ensemble des fonctionnalités de concentrateurs événements](https://docs.microsoft.com/azure/event-hubs/event-hubs-features) explique plus. |

    Lorsque vous avez terminé, les propriétés ressembler à ce qui suit : 

    ![Propriétés du point de terminaison](../core/media/event-hub-endpoint-properties.png)


5. Ce paramètre est facultatif. Configurer le **Message** propriétés. Le **Namespace pour les propriétés de Message définies par l’utilisateur** valeur représente un schéma de message BizTalk mappé à des propriétés de message de concentrateurs d’événements.

6. Sélectionnez **Ok** pour enregistrer vos modifications. 


### <a name="test-your-send-port"></a>Tester votre port d’envoi

Vous pouvez utiliser un simple fichier port de réception et emplacement pour envoyer des messages à votre concentrateur d’événements Azure. 

1. Créer un port de réception à l’aide de l’adaptateur File. Au sein de votre emplacement de réception, définissez la **dossier de réception** à **C:\Temp\In\**et le masque de fichier  **\*.xml**.
2. Propriétés du port d’envoi dans votre concentrateur d’événements, définissez la **filtres** à `BTS.ReceivePortName == FileReceivePort`.
3. Collez le texte suivant dans un éditeur de texte et enregistrez le fichier sous **EventHubMessage.xml**. Il s’agit de votre exemple de message. 

    ```xml
    <Data>
      <DataID>DataID_0</DataID>
      <DataDetails>DataDetails_0</DataDetails>
    </Data>
    ```

4. Démarrer le fichier emplacement de réception et le port d’envoi de concentrateur d’événements.
5. Copie **EventHubMessage.xml** exemple de message dans le dossier de réception (C:\Temp\In\). Le port d’envoi envoie le fichier XML au concentrateur d’événements.

## <a name="receive-messages-from-event-hubs"></a>Recevoir des messages de concentrateurs d’événements

1. Dans la console Administration de BizTalk Server, cliquez sur **Ports de réception**, sélectionnez **nouveau**, puis sélectionnez **unidirectionnel port de réception**. 

    [Créer un port de réception](../core/how-to-create-a-receive-port.md) fournit quelques conseils.

2. Entrez un nom, puis sélectionnez **emplacements de réception**. 

3. Sélectionnez **nouveau**, et **nom** l’emplacement de réception. Dans **Transport**, sélectionnez **EventHub** à partir de la **Type** liste déroulante et sélectionnez **configurer**. 

4. Configurer le **compte Azure** propriétés : 

    |Utiliser|Pour effectuer cette opération|  
    |---|---|  
    | **Ouverture de session** | Connectez-vous à votre compte Azure |
    | **Abonnement** | Sélectionnez l’abonnement qui a votre espace de noms EventHubs |
    | **Groupe de ressources** | Sélectionnez votre groupe de ressources dont votre espace de noms EventHubs |

4. Configurer le **point de terminaison** propriétés : 

    |Utiliser|Pour effectuer cette opération|  
    |---|---|  
    | **Espace de noms** | Sélectionnez votre espace de noms de concentrateurs d’événements, qui ressemble à sb : / /*youreventhubnamespace*.servicebus.windows.net/ |
    | **Nom** | Sélectionnez le nom de votre Hub d’événements (qui a été créé dans votre espace de noms de concentrateurs d’événements) |
    | **Groupe de consommateurs** | Sélectionnez le groupe de consommateurs au sein de votre Hub d’événements. Un groupe par défaut est créé automatiquement. <br/><br/>[Vue d’ensemble des fonctionnalités de concentrateurs événements](https://docs.microsoft.com/azure/event-hubs/event-hubs-features) fournit plus de détails. |
    | **Authentification** | **Signature d’accès Namespace** est la valeur par défaut et utilise automatiquement le RootManageSharedAccessKey qui est créé lorsque vous créez un espace de noms de concentrateurs d’événements.<br/><br/>**Signature d’accès entité** est la stratégie SAP que vous pouvez créer à l’événement Hub niveau (pas les concentrateurs d’événements espace de noms). <br/><br/>[Vue d’ensemble des fonctionnalités de concentrateurs événements](https://docs.microsoft.com/azure/event-hubs/event-hubs-features) explique plus. |

    Lorsque vous avez terminé, les propriétés ressembler à ce qui suit : 

    ![Propriétés du point de terminaison](../core/media/event-hub-endpoint-receive-properties.png)

5. Configurer le **point de contrôle** propriétés. Cet adaptateur utilise un compte de stockage d’objets blob Azure pour lire les événements à l’aide d’un point de contrôle et de manière fiable reprendre à partir d’un redémarrage. 

    **Authentification du stockage**   
    Sélectionnez une méthode d’authentification. En règle générale, il est recommandé d’utiliser une Signature d’accès partagé. Les liens suivants constituent de bonnes ressources pour vous aider à déterminer celle qui convient pour votre scénario :<br/><br/>[À propos des comptes de stockage Azure](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account)<br/>[À l’aide de signatures d’accès partagé (SAS)](https://docs.microsoft.com/azure/storage/common/storage-dotnet-shared-access-signature-part-1)

    Lorsque vous avez terminé, les propriétés ressembler à ce qui suit : 

    ![Propriétés du point de contrôle](../core/media/event-hub-receive-checkpoint.png)

6. Configurer le **Message** propriétés : 

    |Utiliser|Pour effectuer cette opération|  
    |---|---|  
    | **Namespace pour l’utilisateur défini les propriétés de Message** | http://schemas.Microsoft.com/BizTalk/EventHubAdapter/EventData/User est le schéma par défaut, mais vous pouvez entrer un autre schéma. Cette valeur représente un schéma de message BizTalk mappé à des propriétés de message de concentrateurs d’événements. |
    | **Promouvoir les propriétés définies par l’utilisateur** | Ce paramètre est facultatif. Vous pouvez promouvoir ces propriétés si vous préférez. <br/><br/>**REMARQUE**<br/>Les propriétés qui doivent être promues doivent avoir un schéma porperty déployé *avant* recevoir des événements.|

7. Sélectionnez **Ok** pour enregistrer vos modifications. 

### <a name="test-your-receive-settings"></a>Test de vos paramètres de réception

Vous pouvez utiliser un port d’envoi de fichier simple pour recevoir des messages à partir de votre concentrateur d’événements Azure. 

1. Créer un port d’envoi à l’aide de l’adaptateur File. Dans vos propriétés de port d’envoi, définissez la **dossier de Destination** à **C:\Temp\Out\**et définissez l’et **nom de fichier** à **%MessageID%.xml** .
2. Dans votre fichier de propriétés du port d’envoi, définissez la **filtres** à `BTS.ReceivePortName == EHReceivePort`.
3. Démarrer le concentrateur d’événements emplacement de réception et le port d’envoi de fichier.
4. Recherchez les messages dans le dossier de destination (c:\temp\out).

## <a name="do-more"></a>Faire plus
Concentrateurs d’événements est considérée comme la « porte d’entrée » à un grand nombre d’autres services Azure, y compris Azure Data Lake, HD Insight et bien plus encore. Il est conçu pour traiter un grand nombre de messages et les traiter plus rapide. En savoir plus sur les concentrateurs d’événements et ses fonctionnalités : 

[Vue d’ensemble des fonctionnalités de concentrateurs événements](https://docs.microsoft.com/azure/event-hubs/event-hubs-features)  
[Quel est le service Event Hubs ?](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)