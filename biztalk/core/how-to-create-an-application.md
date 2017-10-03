---
title: "Comment créer une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, creating
- creating, applications
ms.assetid: 6a8682a7-3bef-4978-996f-5a9c5154ce62
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6078e292673a1d9dbe3634ea9c0c4e79ab9c2cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-an-application"></a>Création d'une application
Trois méthodes permettent de créer une application BizTalk :  
  
-   Vous pouvez créer l'application BizTalk en utilisant la commande Nouvelle application de la console Administration de BizTalk Server ou la commande AddApp de l'outil de ligne de commande BTSTask. Ces procédures sont décrites ultérieurement dans cette rubrique.  
  
-   Vous pouvez importer un fichier .msi exporté d'une autre application. Si l'application n'existe pas déjà dans le groupe BizTalk actuel, l'application et ses artefacts sont automatiquement créés dans le groupe BizTalk. Pour plus d’informations, consultez [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md).  
  
-   Vous pouvez déployer des assemblys BizTalk à partir de Visual Studio dans une application BizTalk. Si l'application spécifiée dans Visual Studio n'existe pas déjà dans le groupe BizTalk actuel, elle y est automatiquement créée. Pour plus d’informations, consultez [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).  
  
 Avant de créer une nouvelle application, vous devez réfléchir à la configuration des options suivantes :  
  
-   **Le nom de la nouvelle application.** Chaque application du groupe BizTalk doit avoir un nom unique.  
  
-   **Si vous devez ajouter des références à d’autres applications.** Vous devez ajoutez une référence de cette application vers toute application contenant des artefacts que vous souhaitez réutiliser dans cette application. Ceci a pour effet de créer une dépendance entre les applications, qui conditionne leur mode de déploiement. Pour plus d’informations, consultez [des dépendances et déploiement d’applications](../core/dependencies-and-application-deployment.md) et [comment ajouter une référence à une autre Application](../core/how-to-add-a-reference-to-another-application.md).  
  
-   **Si vous devez créer plusieurs applications.** Vous pouvez avoir besoin de déployer certains artefacts dans des applications distinctes. Par exemple, les artefacts partagés doivent être déployés dans leur propre application. Pour plus d’informations, consultez [meilleures pratiques pour déployer une Application BizTalk](../core/best-practices-for-deploying-a-biztalk-application.md).  
  
 Une fois que vous avez créé une application, vous pouvez ajouter des artefacts et apporter d’autres modifications, comme décrit dans les autres rubriques de cette section ([création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md)).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="to-create-a-biztalk-application"></a>Pour créer une application BizTalk  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], cliquez sur le groupe BizTalk dans lequel vous souhaitez créer la nouvelle application, pointez sur **nouveau**, puis cliquez sur **Application**.  
  
3.  Dans **nom**, tapez le nom de l’application. Le nom doit être unique dans le groupe BizTalk.  
  
4.  Si vous souhaitez transformer en application par défaut pour le groupe BizTalk, sélectionnez le **transformer en application par défaut** case à cocher.  
  
5.  Dans **Description**, tapez une description de l’application.  
  
6.  Si cette application doit réutiliser les artefacts à partir d’une autre application, cliquez sur **références** et suivez les étapes restantes. Sinon, cliquez sur **OK** et sans aller plus loin.  
  
7.  Cliquez sur **ajouter**, sélectionnez l’application qui contient les artefacts que vous souhaitez réutiliser dans cette application, puis cliquez sur **OK**. Répétez cette étape pour toutes les autres applications pour lesquelles vous souhaitez ajouter des références.  
  
8.  Si vous souhaitez supprimer une application de la liste, sélectionnez l’application et cliquez sur **supprimer**.  
  
9. Lorsque vous avez terminé, cliquez sur **OK**.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **« ApplicationName » BTSTask AddApp :** *valeur* [**/par défaut**] [**/Description :***valeur*] [**/ Serveur :***valeur*] [**/Database :***valeur*]  
  
     Exemple :  
  
     **BTSTask AddApp MonApplication / Description : « Mon application préférée » /Server:MySQLServer Server**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**/ ApplicationName**|Nom de l'application à créer. Les noms comportant des espaces doivent être placés entre guillemets (").|  
    |**/ Par défaut**|Lorsque ce paramètre est spécifié, la nouvelle application devient l'application par défaut pour le groupe BizTalk.|  
    |**/ Description**|Description de l'application. Les descriptions comportant des espaces doivent être placées entre guillemets (").|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [Création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md)   
 [Commande AddApp](../core/addapp-command.md)