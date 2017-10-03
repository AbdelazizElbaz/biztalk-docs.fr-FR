---
title: "Générer un Client WCF ou le contrat de Service WCF pour les artefacts SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5fa7d8c0-8ee4-41e7-9394-d22e87e09391
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f961c3648e153847f5ac259c9902da5589b1486d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts"></a>Générer un Client WCF ou le contrat de Service WCF pour les artefacts SQL Server
Vous pouvez utiliser la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer une classe de client WCF ciblé sur les opérations sélectionnées sur les artefacts de SQL Server. Vous pouvez également utiliser le service Model Metadata Utility Tool (svcutil.exe) pour générer la classe de client WCF ; Toutefois, le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] expose les fonctionnalités de l’utilitaire de métadonnées ServiceModel via une interface de Microsoft Windows standard. Il fournit également des fonctionnalités de navigation et de recherche qui ne sont pas disponibles avec l’outil svcutil.exe et génère un fichier de configuration basé sur les propriétés de liaison que vous sélectionnez lorsque vous vous connectez à la base de données SQL Server.  
  
## <a name="generating-a-wcf-client-class-by-using-the-add-adapter-service-reference-plug-in"></a>Génération d’une classe de Client WCF à l’aide de l’ajouter une référence de Service d’adaptateur plug-in  
 Procédez comme suit pour générer une classe de client WCF à l’aide de la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, cliquez sur votre projet, puis cliquez sur **ajouter une référence de Service de carte**.  
  
2.  Après le **ajouter une référence de Service de carte** boîte de dialogue s’ouvre, suivez les étapes de [obtenir les métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md) pour se connecter à SQL Server et de rechercher et pour les opérations de recherche. Pour créer une classe de client WCF pour les opérations que vous sélectionnez, assurez-vous que **Client (Outbound operations)** est sélectionné dans le **type de contrat Select** liste déroulante. (Il s’agit de la valeur par défaut).  
  
3.  Après avoir sélectionné toutes les opérations que vous souhaitez cibler, cliquez sur **OK** pour générer la classe de client WCF.  
  
 Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ajoute deux fichiers à votre projet :  
  
-   **Le fichier de code du client WCF**. Ce fichier contient le WCF client classe et assistance code généré pour les opérations que vous avez sélectionné. La première fois que vous exécutez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], il génère ce fichier avec le nom par défaut **SQLAdapterBindingClient.cs**. Si vous l’exécutez à nouveau, le fichier suivant, il génère sera appelé **SQLAdapterBindingClient1.cs**.  Le suffixe du numéro augmente de 1 pour chaque nouveau fichier que vous générez.  Vous pouvez également modifier le préfixe par défaut **SQLBinding** en entrant un préfixe différent dans le **préfixe de nom de fichier** champ le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] avant de sélectionner **OK** à générer le fichier.  
  
-   **App.config**. Ce fichier contient une configuration de liaison et les configurations de point de terminaison client qui sont basées sur les sélections effectuées lors de la configuration de la connexion pour le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
    > [!IMPORTANT]
    >  Lors de l’utilisation du [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], si vous ne spécifiez pas une valeur pour une propriété de liaison de type chaîne et dont la valeur par défaut a la valeur null puis que la liaison de propriété sera pas disponible dans le fichier app.config. Vous devez ajouter manuellement la propriété de liaison et sa valeur dans le fichier app.config, si nécessaire.  
  
## <a name="generating-a-wcf-service-contract-by-using-the-add-adapter-service-reference-plug-in"></a>Génération d’un contrat de Service WCF à l’aide de l’ajouter une référence de Service d’adaptateur plug-in  
 Pour les opérations entrantes telles que l’interrogation de la base de données SQL Server ou de recevoir des notifications de la base de données, la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] enregistre une requête avec SQL Server (en cas d’ou exécute une requête spécifiée par l’application cliente (en cas d’interrogation) notification). Dans les deux scénarios, l’adaptateur envoie le message entrant à partir de la base de données SQL Server pour la consommation. Dans ce cas, l’application consommatrice agit comme un service et la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] joue le rôle du client. Vous devez, par conséquent, implémenter un service WCF qui peut recevoir des opérations entrantes à partir de l’adaptateur. Pour ce faire, vous utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer une interface .NET qui représente le contrat de service qui est visible par l’adaptateur pour les opérations entrantes. Cette interface .NET est également appelée un contrat de service WCF. Puis, vous implémentez cette interface pour créer le service WCF que vous pouvez utiliser pour recevoir les opérations entrantes.  
  
 Procédez comme suit pour générer un contrat de service WCF à l’aide de la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### <a name="to-generate-a-wcf-service-contract-for-inbound-operations"></a>Pour générer un contrat de service WCF pour les opérations entrantes  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, cliquez sur votre projet, puis cliquez sur **ajouter une référence de Service de carte**.  
  
2.  Après le **ajouter une référence de Service de carte** boîte de dialogue s’ouvre, suivez les étapes de [se connecter à SQL Server dans Visual Studio à l’aide d’Ajouter adaptateur Service référence un plug-in](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-add-adapter-service-reference.md) pour se connecter à la base de données SQL Server.  
  
    > [!IMPORTANT]
    >  Si vous générez du contrat de service WCF pour **TypedPolling** opération entrante, vous devez spécifier le **InboundID** dans le cadre de l’URI de connexion et **PollingStatement** propriété de liaison.  
  
3.  Après vous être connecté à la base de données SQL Server, sélectionnez **Service (opérations entrantes)** à partir de la **type de contrat Select** liste déroulante.  
  
4.  Dans le **sélectionner une catégorie** , cliquez sur le nœud racine (**/**), sélectionnez l’opération entrante à partir de la **catégories et opérations disponibles** , boîte de, puis Cliquez sur **ajouter**.  
  
5.  Pour générer le contrat de service WCF pour l’opération entrante, cliquez sur **OK**.  
  
 Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ajoute trois fichiers à votre projet :  
  
-   **SqlAdapterBindingInterface.cs**. Ce fichier contient le WCF généré contrat (interface) et le code d’application d’assistance pour l’opération entrante de service.  
  
-   **SqlAdapterBindingService.cs**. Ce fichier contient une classe qui implémente l’interface définie dans SqlAdapterBindingInterface.cs. Vous pouvez implémenter la logique métier qui traite les enregistrements retournés par l’opération entrante.  
  
-   **App.config**. Ce fichier contient une configuration de liaison, des comportements de point de terminaison et configuration de point de terminaison de service qui sont basées sur les sélections effectuées lors de la configuration de la liaison et la connexion pour le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
    > [!IMPORTANT]
    >  Lors de l’utilisation du [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], si vous ne spécifiez pas une valeur pour une propriété de liaison de type chaîne et dont la valeur par défaut a la valeur null puis que la liaison de propriété sera pas disponible dans le fichier app.config. Vous devez ajouter manuellement la propriété de liaison et sa valeur dans le fichier app.config, si nécessaire.  
  
## <a name="generating-a-wcf-client-class-by-using-svcutilexe"></a>Génération d’une classe de Client WCF à l’aide de svcutil.exe  
 Vous pouvez utiliser svcutil.exe pour générer une classe de client WCF pour votre application. Vous devez configurer svcutil.exe pour l’utiliser avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
 SvcUtil.exe génère la classe de client WCF dans un fichier de sortie avec un nom de fichier par défaut de **output.cs**. Vous devez inclure manuellement ce fichier dans votre [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] projet. Pour plus d’informations sur svcutil.exe, consultez [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx).
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications SQL à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)