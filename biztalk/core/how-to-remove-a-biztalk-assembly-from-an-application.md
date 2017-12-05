---
title: "Comment supprimer un Assembly BizTalk à partir d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [applications], assemblies
- assemblies, deleting
- deleting, assemblies
- applications, assemblies
- managing [assemblies], deleting
ms.assetid: 0691c3b6-476d-4e01-b50b-47d7c0b299bf
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89e46b8610114149e8618811361090d8644f82aa
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-remove-a-biztalk-assembly-from-an-application"></a>Suppression d'un assembly BizTalk d'une application
Cette rubrique explique comment supprimer un assembly BizTalk d'une application BizTalk à l'aide de la console Administration de BizTalk Server ou de l'invite de commande. Lorsque vous effectuez cette opération, l'assembly et les artefacts qu'il contient, comme les orchestrations, schémas et pipelines, sont supprimés de la base de données de gestion BizTalk et de l'application.  
  
 Avant de supprimer un assembly BizTalk, gardez les points importants suivants à l'esprit :  
  
-   Lorsque vous supprimez un assembly BizTalk, le fichier de l'assembly n'est pas supprimé automatiquement du Global Assembly Cache (GAC) ou du système de fichiers local, s'il existe dans ces emplacements. Vous devez le supprimer manuellement. Pour obtenir des instructions, consultez [comment désinstaller un Assembly du GAC](http://msdn.microsoft.com/library/464706a8-f902-4d05-a724-19169facd2b4) et [comment supprimer d’autres fichiers et les paramètres d’une Application BizTalk](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).  
  
-   Si vous supprimez un assembly BizTalk contenant un pipeline, tous les ports d'envoi de l'application qui utilisent ce pipeline seront réinitialisés pour utiliser le pipeline par défaut, PassThruTransmit.  
  
-   Il est impossible de supprimer un assembly BizTalk dont d'autres artefacts dépendent. Vous devez commencer par supprimer les artefacts dépendants. Vous pouvez ensuite supprimer l'assembly BizTalk.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="to-remove-a-biztalk-assembly-from-an-application"></a>Pour supprimer un assembly BizTalk à partir d’une application  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez Administration de BizTalk Server, développez le groupe BizTalk contenant l’assembly BizTalk à supprimer, puis développez l’application contenant l’assembly BizTalk.  
  
3.  Cliquez sur le **ressources** dossier, cliquez sur l’assembly BizTalk, puis cliquez sur **supprimer**.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **BTSTask RemoveResource** [**« ApplicationName » :***valeur*] **ApplicationName :***valeur* [  **/Server :**  *valeur*] [**/Database :***valeur*]  
  
     Exemple :  
  
     **BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyApp.Orchestrations, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 0123456789ABCDEF »**  
  
    |Paramètre| Description|  
    |---------------|-----------------|  
    |**/ ApplicationName**|Nom de l'application BizTalk contenant l'assembly BizTalk à supprimer. L'application par défaut est utilisée si ce paramètre n'est pas spécifié. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («).|  
    |**/ Luid**|Identificateur unique local (LUID) de l'assembly BizTalk. Vous pouvez obtenir l’identificateur LUID à l’aide de la **ListApp** de commande, comme décrit dans [commande ListApp](../core/listapp-command.md).|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des assemblys BizTalk](../core/managing-biztalk-assemblies.md)   
 [Commande RemoveResource](../core/removeresource-command.md)