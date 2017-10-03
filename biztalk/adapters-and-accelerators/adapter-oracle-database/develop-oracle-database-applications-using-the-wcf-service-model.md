---
title: "Développer des applications de base de données Oracle à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performing operations, by using the WCF service model
- developing applications, by using the WCF service model
- WCF service model, using to develop applications
ms.assetid: 3f2c60b2-4835-492d-8c3c-ed35d3e4c517
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 548ca256d4395aefd67681229e9669ef2afcc2f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-oracle-database-applications-using-the-wcf-service-model"></a>Développer des applications de base de données Oracle à l’aide du modèle de Service WCF
Niveau le plus bas, la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] présente un modèle de programmation dans lequel les clients pour appeler les opérations sur un service en échangeant des messages SOAP sur un canal établi entre les points de terminaison de client et le service. Ce modèle, appelé le modèle de canal WCF, expose les types de données et des méthodes qui permettent d’agir directement sur l’architecture de canal WCF. Le modèle de canal WCF vous offre un contrôle direct sur le contenu des messages SOAP que vous créez et de façon à la fois votre application et le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] consommer ; Toutefois, en créant des messages SOAP correct à envoyer via un canal et en validant le les messages de réponse retournés peuvent être une tâche détaillée et précises.  
  
 Pour cette raison, [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] fournit un autre modèle de programmation appelé le modèle de service WCF. Le modèle de service WCF implique l’utilisation des classes proxy pour appeler des opérations sur un service cible ou de recevoir des opérations à partir d’un client.  
  
-   La classe proxy utilisée pour appeler des opérations sur un service cible est appelée une classe de client WCF. Cette classe modélise les opérations exposées par un service en tant que méthodes .NET avec des paramètres fortement typés. À l’aide du modèle de service WCF, vous pouvez appeler les opérations exposées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] en tant que méthodes .NET sur le client WCF. Pour plus d’informations sur les clients WCF, consultez « Présentation de Client WCF » à [http://go.microsoft.com/fwlink/?LinkId=91458](http://go.microsoft.com/fwlink/?LinkId=91458).  
  
-   Dans le modèle de service WCF, le contrat de service exposé par un service est représenté par une interface. Cette représentation sous forme de code managé du contrat de service est appelé un contrat de service WCF. Le contrat de service WCF modélise les opérations en tant que méthodes avec des paramètres fortement typés. Pour une opération de réception à partir d’un client, vous implémentez une classe, le service WCF, à partir de cette interface. Vous pouvez héberger ensuite une instance de cette classe dans un **System.ServiceModel.ServiceHost** pour permettre à un client d’appeler l’opération sur votre code. En utilisant le modèle de service WCF et un contrat de service WCF ciblé à l’opération POLLINGSTMT, vous pouvez recevoir les résultats d’une opération d’interrogation sur la base de données Oracle à l’aide [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
 Vous utilisez des outils pour générer une classe de client WCF ou un contrat de service WCF et code d’assistance à partir des métadonnées de service associé qui le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose. Vous pouvez utiliser un des outils suivants :  
  
-   Le service Model Metadata Utility Tool (svcutil.exe), qui est fourni avec WCF  
  
-   Le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], qui est fourni avec le[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]  
  
 Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] est intégré à la [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] l’expérience de conception et présente un Microsoft Windows standard de l’interface qui fournit puissants de parcourir et de recherche avancées sur les opérations exposées par l’adaptateur. Pour plus d’informations sur la façon de générer un client WCF ou un contrat de service WCF, consultez [générer un Client WCF ou un contrat de Service WCF pour les artefacts de Solution de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md).  
  
 Car il présente un modèle qui est familier aux programmeurs .NET et qui masque la complexité sous-jacente d’échange de messages SOAP sur un canal, le modèle de service WCF est souvent le meilleur choix pour développer des solutions de programmation pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Toutefois, il existe des scénarios dans lesquels le modèle de canal WCF peut être un meilleur choix. Par exemple, le modèle de service WCF ne prend en charge pour l’opération ReadLOB de diffusion en continu. C’est parce que la sérialisation et désérialisation entre la représentation XML d’objets dans un message SOAP et les types .NET utilisés pour représenter dans le modèle de service implique la lecture de la totalité du message en mémoire. (Le résultat d’une opération ReadLOB est une exception à cette règle.)  
  
 Le modèle de canal WCF prend en charge la diffusion en continu au niveau du nœud XML sur toutes les opérations et le niveau de données de diffusion en continu sur les opérations ReadLOB et UpdateLOB. Si vous êtes confronté à des requêtes qui retournent des jeux de résultats volumineux ou essayez de mettre à jour un champ LOB dans une table, le modèle de canal WCF peut être un meilleur choix. Pour plus d’informations sur l’utilisation du modèle de canal WCF, consultez [développer des Applications de base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md).  
  
 Les rubriques de cette section contiennent des informations, des procédures et des exemples pour vous aider à créer et utiliser le modèle de service WCF pour développer des applications à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Vue d’ensemble du modèle de Service WCF avec l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md)  
  
-   [Métadonnées et le modèle de Service WCF avec la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/metadata-and-the-wcf-service-model-with-oracle-database.md)  
  
-   [Générer un Client WCF ou un contrat de Service WCF pour les artefacts de Solution de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)  
  
-   [Configurer une liaison de Client pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-a-client-binding-for-the-oracle-database.md)  
  
-   [Exécution de base Insert, Update, Delete et opérations de sélection en utilisant le modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-select-operations-in-oracle-db-using-a-wcf-service.md)  
  
-   [Effectuer des opérations sur les Tables avec des types de données de grande taille dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-large-data-types-in-oracle-db-using-a-wcf-service.md)  
  
-   [Appel des fonctions et les procédures de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)  
  
-   [Exécution d’opérations à l’aide de REF CURSOR dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md)  
  
-   [Exécution d’opérations à l’aide des Types d’enregistrements dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md)  
  
-   [Une opération SQLEXECUTE dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md)  
  
-   [Réception de Messages de modification de données reposant sur l’interrogation de la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-service.md)  
  
-   [Recevoir des Notifications de modification de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-the-wcf-service-model1.md)