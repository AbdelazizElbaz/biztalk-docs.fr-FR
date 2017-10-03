---
title: "Se connecter à SQL Server dans Visual Studio en utilisant Ajouter une référence de Service de carte Plug-in | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fc3b824-d20b-4531-81f3-89b4a1ff3216
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 506d0cc1d4f4fca94b71aef3e6d4855a2afb845b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-sql-server-in-visual-studio-using-add-adapter-service-reference-plug-in"></a>Se connecter à SQL Server dans Visual Studio en utilisant Ajouter une référence de Service de carte Plug-in
Pour se connecter à SQL Server à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] dans une solution de programmation .NET, vous devez utiliser le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]. Cette rubrique fournit des instructions sur l’utilisation de la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
## <a name="connecting-to-sql-server-using-add-adapter-service-reference-plug-in"></a>Connexion à SQL Server à l’aide d’ajouter une référence de Service de carte Plug-in  
 Les étapes suivantes pour vous connecter à SQL Server à l’aide du [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### <a name="to-connect-to-sql-server"></a>Pour se connecter à SQL Server  
  
1.  Pour se connecter à l’aide de le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] dans une solution de programmation :  
  
    1.  Créez un projet dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
    2.  Cliquez sur le projet dans l’Explorateur de solutions, puis cliquez sur **ajouter une référence de Service de carte**. Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] s’ouvre.  
  
2.  À partir de la **sélectionner une liaison** la liste déroulante, sélectionnez **sqlBinding**, puis cliquez sur **configurer**.  
  
3.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet et à partir de la **type d’informations d’identification du Client** liste déroulante, effectuez l’une des opérations suivantes :  
  
    > [!NOTE]
    >  Si vous vous connectez à SQL Server à l’aide de l’authentification Windows, l’utilisateur Windows avec lequel vous êtes connecté doit être ajouté à SQL Server, comme décrit dans [se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).  
  
    |Cliquez sur ce bouton|Pour effectuer cette opération|  
    |----------------|----------------|  
    |**Aucun**|Se connecter à SQL Server à l’aide de l’authentification Windows.|  
    |**Windows**|Se connecter à SQL Server à l’aide de l’authentification Windows.|  
    |**Nom d’utilisateur**|Spécifier le nom d’utilisateur et le mot de passe pour vous connecter à SQL Server en spécifiant des informations d’identification pour un utilisateur défini dans une base de données SQL Server. Notez que le nom d’utilisateur et le mot de passe respectent la casse. **Remarque :** si vous laissez le **nom d’utilisateur** et **mot de passe** champs, l’adaptateur se connecte à SQL Server à l’aide de l’authentification Windows.|  
  
4.  Cliquez sur le **propriétés URI** onglet et spécifiez des valeurs pour les paramètres de connexion. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], consultez [créer l’URI de connexion SQL Server](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).  
  
    > [!NOTE]
    >  Si les paramètres de connexion contiennent des caractères réservés, vous devez les spécifier en tant que-est dans le **propriétés URI** onglet, autrement dit, sans utiliser de caractères d’échappement. Toutefois, si vous spécifiez l’URI directement dans le **configurer un URI** champ et les paramètres de connexion contiennent des caractères réservés, vous devez spécifier les paramètres de connexion à l’aide de caractères d’échappement corrects.  
  
    > [!NOTE]
    >  Si vous ne spécifiez aucune valeur sous l’onglet Propriété de l’URI, le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] utilise l’URI `mssql://.//`. Dans ce cas, l’adaptateur se connecte à la base de données par défaut et à l’instance de base de données par défaut sur l’ordinateur local.  
  
5.  Cliquez sur le **propriétés de liaison** onglet et spécifiez des valeurs pour les propriétés de liaison, si elle existe, requis par les opérations que vous souhaitez cibler.  
  
6.  Cliquez sur **OK**.  
  
7.  Cliquez sur **Se connecter**. Une fois la connexion est établie, l’état de connexion s’affiche en tant que **connecté**.  
  
     L’illustration suivante montre le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] immédiatement après la connexion est établie. L’interface utilisateur graphique est identique pour les [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
     ![Se connecter à SQL Server](../../adapters-and-accelerators/adapter-sql/media/661adb8a-5050-44d5-8db8-fdf0fe530b40.gif "661adb8a-5050-44d5-8db8-fdf0fe530b40")  
  
     Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] affiche les différents nœuds contenant plusieurs opérations qui peuvent être effectuées sur SQL Server. Par exemple, le **procédures** nœud contient toutes les procédures disponibles pour vous connecté à la base de données. De même, la **Tables** nœud contient toutes les tables dans la base de données vous connecté et les opérations qui peuvent être effectuées sur une table. Pour plus d’informations sur ces nœuds, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-sql/metadata-node-ids2.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Se connecter à SQL Server dans Visual Studio à l’aide de la macro complémentaire Consume Adapter Service](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md)