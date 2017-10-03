---
title: "Comment supprimer un Script de pré-traitement ou de post-traitement à partir d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [scripts], deleting
- deleting, scripts
- managing [applications], scripts
- scripts, deleting
- applications, scripts
ms.assetid: 7911f098-97f2-4a5d-87fe-20b55231113e
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25d60bdec2857d9d84042e184f0bbfbb2307806a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-pre--or-post-processing-script-from-an-application"></a>Suppression d'un script de pré-traitement ou de post-traitement d'une application
Cette rubrique décrit comment supprimer un script de prétraitement ou de post-traitement dans une application à l'aide de la console Administration de BizTalk Server ou de la ligne de commande. Cette opération supprime le script de la base de données de gestion BizTalk, afin qu'il ne soit pas exporté dans le fichier .msi de l'application. Elle ne supprime pas le script du système de fichiers local, le cas échéant.  
  
 Si l'application contenant le script a été installé sur le système de fichiers local et que le script a été conçu de manière à s'exécuter lors de la désinstallation, vous devez supprimer le script du système de fichiers pour éviter qu'il ne s'exécute lors de la désinstallation de l'application.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="to-remove-a-script-from-an-application"></a>Pour supprimer un script d'une application  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez successivement [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], le groupe BizTalk contenant le script à supprimer, puis l'application contenant le script.  
  
3.  Cliquez sur le **ressources** dossier, cliquez sur le script, puis cliquez sur **supprimer**.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **BTSTask RemoveResource** [**« ApplicationName » :***valeur*] **ApplicationName :***valeur* [  **/Server :**  *valeur*] [**/Database :***valeur*]  
  
     Exemple :  
  
     **BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyApplication:MyScript.vbs »**  
  
    |Paramètre| Description|  
    |---------------|-----------------|  
    |**/ ApplicationName**|Nom de l'application BizTalk contenant le script BizTalk à supprimer. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles ("). L'application par défaut est utilisée si ce paramètre n'est pas spécifié.|  
    |**/ Luid**|Identificateur unique local (LUID) du script. Vous pouvez obtenir l’identificateur LUID à l’aide de la [commande ListApp](../core/listapp-command.md).|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des Scripts de pré-traitement et post-traitement](../core/managing-pre-and-post-processing-scripts.md)   
 [Commande RemoveResource](../core/removeresource-command.md)