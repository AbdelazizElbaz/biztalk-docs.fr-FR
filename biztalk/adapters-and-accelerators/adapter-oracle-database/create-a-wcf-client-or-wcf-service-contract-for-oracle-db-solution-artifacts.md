---
title: "Générer un client WCF ou un contrat de service WCF pour les artefacts de solution de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model programming, creating a proxy
- how to, create a proxy
- creating a proxy
- proxy programming, creating a proxy
ms.assetid: 3e832ae9-e253-4476-9f25-8cf0de12f469
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e729adec26aca98df80ecc7917ab0558faa6632e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="generate-a-wcf-client-or-a-wcf-service-contract-for-oracle-database-solution-artifacts"></a>Générer un client WCF ou un contrat de service WCF pour les artefacts de solution de base de données Oracle
Vous pouvez utiliser la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer une classe de client WCF ou un contrat de service WCF (interface) ciblé sur les opérations sélectionnées sur les objets de base de données Oracle. Vous pouvez également utiliser le service Model Metadata Utility Tool (svcutil.exe) pour générer la classe de client WCF ou le contrat de service WCF ; Toutefois, le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] expose les fonctionnalités de l’utilitaire de métadonnées ServiceModel via une interface de Microsoft Windows standard. Il fournit également des fonctionnalités de navigation et de recherche qui ne sont pas disponibles avec l’outil svcutil.exe, et génère un fichier de configuration basé sur les propriétés de liaison que vous sélectionnez lorsque vous vous connectez à la base de données Oracle.  
  
## <a name="generating-a-client-class-by-using-the-add-adapter-service-reference-plug-in"></a>Génération d’une classe de Client à l’aide de l’ajouter une référence de Service d’adaptateur plug-in  
 Procédez comme suit pour générer une classe de client WCF à l’aide de la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### <a name="to-generate-a-wcf-client-class"></a>Pour générer une classe de client WCF  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, cliquez sur votre projet, puis cliquez sur **ajouter une référence de Service de carte**.  
  
2.  Après le **ajouter une référence de Service de carte** boîte de dialogue s’ouvre, suivez les étapes de [de récupérer les métadonnées pour des opérations Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md) pour se connecter à la base de données Oracle et Parcourir, rechercher opérations. Pour créer une classe de client WCF pour les opérations que vous sélectionnez, assurez-vous que **Client (Outbound operations)** est sélectionné dans le **type de contrat Select** liste déroulante (il s’agit de la valeur par défaut).  
  
3.  Après avoir sélectionné toutes les opérations que vous souhaitez cibler, cliquez sur **OK** pour générer la classe de client WCF.  
  
 Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ajoute deux fichiers à votre projet :  
  
-   **OracleDBBindingClient.cs**. Ce fichier contient le WCF client classe et assistance code généré pour les opérations que vous avez sélectionné.  
  
-   **App.config**. Ce fichier contient une configuration de liaison et les configurations de point de terminaison de client. Ces configurations sont basées sur les sélections effectuées lors de la configuration de la liaison et la connexion pour le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
    > [!IMPORTANT]
    >  Lors de l’utilisation du [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], si vous ne spécifiez pas une valeur pour une propriété de liaison de type chaîne et dont la valeur par défaut a la valeur null puis que la liaison de propriété sera pas disponible dans le fichier app.config. Vous devez ajouter manuellement la propriété de liaison et sa valeur dans le fichier app.config, si nécessaire.  
  
## <a name="generating-a-wcf-service-contract-by-using-the-add-adapter-service-reference-plug-in"></a>Génération d’un contrat de Service WCF à l’aide de l’ajouter une référence de Service d’adaptateur plug-in  
 L’adaptateur expose les opérations entrantes pour activer la base de données Oracle envoyer des messages à un client de carte. Pour ces opérations, vous devez générer un contrat de service WCF. Par exemple, l’adaptateur expose une opération POLLINGSTMT entrante pour interroger la base de données Oracle. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exécute la requête spécifiée par la **PollingStatement** liaison de propriété et envoie le jeu de résultats à l’application consommateur dans un message POLLINGSTMT. Dans ce scénario, l’application consommatrice agit comme un service et la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] joue le rôle du client. Vous devez, par conséquent, implémenter un service WCF qui peut recevoir l’opération POLLINGSTMT à partir de l’adaptateur. Pour ce faire, vous utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer une interface .NET qui représente le contrat de service qui est visible par l’adaptateur pour l’opération POLLINGSTMT. Cette interface .NET est également appelée un contrat de service WCF. Puis, vous implémentez cette interface pour créer le service WCF que vous pouvez utiliser pour l’opération POLLINGSTMT de réception.  
  
 Cette section fournit des informations sur la façon de générer un contrat de service WCF à l’aide du [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour les opérations entrantes exposées par l’adaptateur.  
  
#### <a name="to-generate-a-wcf-service-contract-for-inbound-operations"></a>Pour générer un contrat de service WCF pour les opérations entrantes  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, cliquez sur votre projet, puis cliquez sur **ajouter une référence de Service de carte**.  
  
2.  Après le **ajouter une référence de Service de carte** boîte de dialogue s’ouvre, suivez les étapes de [de récupérer les métadonnées pour des opérations Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md) pour se connecter à la base de données Oracle. Il existe plusieurs propriétés de liaison et une propriété URI que vous pouvez définir lorsque vous vous connectez à la base de données Oracle pour les opérations entrantes. Par exemple, pour l’opération d’interrogation entrants (**POLLINGSTMT**), vous devez spécifier le **PollingStatement** propriété de liaison lorsque vous configurez la connexion à la base de données Oracle. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise l’instruction SQL SELECT spécifiée dans cette propriété pour générer la classe qui représente le jeu de résultats retourné par l’opération POLLINGSTMT.  
  
3.  Après vous être connecté à la base de données Oracle, sélectionnez **Service (opérations entrantes)** à partir de la **type de contrat Select** liste déroulante.  
  
4.  Dans le **sélectionner une catégorie** , cliquez sur le nœud racine (**/**), puis accédez à l’opération pour laquelle vous souhaitez générer le contrat de service. Par exemple, pour l’opération d’interrogation, sélectionnez **POLLINGSTMT** à partir de la **catégories et opérations disponibles** zone, puis cliquez sur **ajouter**.  
  
5.  Pour générer le contrat de service WCF pour l’opération POLLINGSTMT, cliquez sur **OK**.  
  
 Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ajoute trois fichiers à votre projet :  
  
-   **OracleDBBindingInterface.cs**. Ce fichier contient le WCF généré contrat (interface) et le code d’application d’assistance pour l’opération POLLINGSTMT de service.  
  
-   **OracleDBBindingService.cs**. Ce fichier contient une classe qui implémente l’interface définie dans OracleDBBindingInterface.cs. Vous pouvez implémenter la logique métier qui traite les enregistrements retournés par la requête d’interrogation dans la méthode POLLINGSTMT de cette classe.  
  
-   **App.config**. Ce fichier contient une configuration de liaison, des comportements de point de terminaison et configuration de point de terminaison de service qui sont basées sur les sélections effectuées lors de la configuration de la liaison et la connexion pour le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
    > [!IMPORTANT]
    >  Lors de l’utilisation du [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], si vous ne spécifiez pas une valeur pour une propriété de liaison de type chaîne et dont la valeur par défaut a la valeur null puis que la liaison de propriété sera pas disponible dans le fichier app.config. Vous devez ajouter manuellement la propriété de liaison et sa valeur dans le fichier app.config, si nécessaire.  
  
## <a name="using-svcutilexe-to-generate-a-wcf-client-class-or-a-wcf-service-contract"></a>À l’aide de svcutil.exe pour générer une classe de Client WCF ou un contrat de Service WCF  
 Vous pouvez utiliser svcutil.exe pour générer une classe de client WCF ou une interface de service WCF pour votre application. Vous devez configurer svcutil.exe pour l’utiliser avec le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Pour plus d’informations sur la configuration et l’utilisation de svcutil.exe avec la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [utilisant le service Model Metadata Utility Tool avec l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/use-the-servicemodel-metadata-utility-with-the-oracle-db-adapter-in-biztalk.md).  
  
 SvcUtil.exe génère la classe de client WCF ou le contrat de service WCF dans un fichier de sortie. Le nom de fichier par défaut est output.cs. Vous devez inclure manuellement ce fichier dans votre [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des Applications de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)   
 [Exécution de base Insert, Update, Delete et opérations Select dans SQL à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/insert-update-delete-or-select-operations-in-sql-using-the-wcf-service-model.md)