---
title: "Comment exporter des liaisons d’un groupe BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bindings, exporting
- groups, bindings
- groups, exporting
ms.assetid: 51955266-f87f-41c9-992c-93036b40f663
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df08f99a9e37bf1a4d4a794c17d483fdc381f463
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-export-bindings-for-a-biztalk-group"></a>Exportation des liaisons d'un groupe BizTalk
Cette rubrique décrit comment exporter des liaisons pour un groupe BizTalk vers un fichier .xml à l'aide de la console Administration de BizTalk Server ou de l'invite de commandes. Vous pouvez ensuite importer ces liaisons dans un groupe BizTalk ou d’une application, comme décrit dans [comment importer les liaisons dans un groupe BizTalk](../core/how-to-import-bindings-into-a-biztalk-group.md) et [comment importer les liaisons dans une Application BizTalk](../core/how-to-import-bindings-into-a-biztalk-application.md). Pour plus d’informations sur l’utilisation de fichiers de liaison, consultez [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md).  
  
> [!NOTE]
>  L'exportation de liaisons pour un groupe entraîne toujours l'exportation des informations du tiers global, que cette option soit spécifiée ou non.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server ou opérateurs BizTalk. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="to-export-bindings-for-a-biztalk-group"></a>Exportation des liaisons pour un groupe BizTalk  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, cliquez sur **Applications**, pointez sur **exporter**, puis cliquez sur **liaisons**.  
  
3.  Dans la page Exporter les liaisons, dans **exportation vers le fichier**, tapez le chemin d’accès absolu du fichier .xml vers lequel exporter les liaisons.  
  
     Exemple : C:\Bindings\Group1Bindings_Staging1.xml  
  
4.  Vérifiez que **exporter toutes les liaisons du groupe actif** est sélectionné, puis cliquez sur **OK**.  
  
     Les liaisons sont exportées vers un fichier .xml à l'emplacement spécifié.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **Facultatif /Destination de BTSTask ExportBindings :** *valeur* **paramètre « GroupLevel »** [**/GlobalParties**] [**/Server :**  *valeur*] [**/Database :***valeur*]  
  
     Exemple :  
  
     **Facultatif /Destination de BTSTask ExportBindings : « C:\Binding Files\MyBindings.xml » GroupLevel /Server:MyDatabaseServer Server**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**Et de destination**|Chemin d'accès complet du fichier de liaison à créer, nom du fichier inclus. Si un fichier de liaison doté du même chemin d'accès existe déjà, il est remplacé. Si le chemin d’accès contient des espaces, vous devez le placer entre guillemets doubles («).|  
    |**/ GroupLevel**|Lorsque ce paramètre est défini, toutes les liaisons du groupe BizTalk actif sont exportées.|  
    |**/ GlobalParties**|Si spécifié, exporte les informations du tiers global pour le groupe.|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [L’exportation des liaisons](../core/exporting-bindings6.md)   
 [Commande ExportBindings](../core/exportbindings-command.md)   
 [L’importation de stratégies, les liaisons et les Applications BizTalk](../core/importing-biztalk-applications-bindings-and-policies.md)