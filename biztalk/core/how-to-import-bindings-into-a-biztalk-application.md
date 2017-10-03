---
title: Comment importer des liaisons dans une Application BizTalk | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bindings, applications
- applications, importing
- applications, bindings
- bindings, importing
ms.assetid: 89841b23-4e1b-46ff-8f00-cdad65d6216d
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b07e2c7cb5e63ee3e03ac69ad591d7939b22d5d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-import-bindings-into-a-biztalk-application"></a>Importation des liaisons dans une application BizTalk
Cette rubrique explique comment importer des liaisons dans un groupe BizTalk à partir d'un fichier .xml à l'aide de la console Administration de BizTalk Server ou de la ligne de commande. Vous pouvez également importer des liaisons dans un groupe BizTalk, comme décrit dans [comment importer les liaisons dans un groupe BizTalk](../core/how-to-import-bindings-into-a-biztalk-group.md).  
  
 Vous pouvez importer des liaisons qui ont été exportées depuis un assembly, une application ou un groupe. Si vous importez des liaisons de groupe, seules celles d'une application portant le même nom sont appliquées à l'application dans laquelle vous les importez. Vous pouvez également importer des liaisons à partir d'une application portant un nom différent. Pour obtenir des instructions sur l’exportation des liaisons, consultez [exportation des liaisons](../core/exporting-bindings6.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="to-import-bindings-into-a-biztalk-application"></a>Pour importer des liaisons dans une application BizTalk  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez successivement [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], le groupe BizTalk, puis Applications.  
  
3.  Cliquez sur l’application dans laquelle vous souhaitez importer des liaisons, pointez sur **importer**, puis cliquez sur **liaisons**.  
  
4.  Cliquez sur le fichier de liaison et cliquez sur **ouvrir**.  
  
     Les artefacts du fichier de liaison sont écrits dans l'application. Ils s'affichent dans les dossiers appropriés de l'application.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **BTSTask ImportBindings /Source :** *valeur* [**« ApplicationName » :***valeur*] [**/Server :**  *valeur*] [**/Database :***valeur*]  
  
     Par exemple, la commande suivante permet d'importer des liaisons dans l'application appelée MyApplication du groupe BizTalk par défaut.  
  
     **BTSTask ImportBindings /ApplicationName:MyApplication** /**Source:C:\Bindings\Binding1.xml**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**/ Source**|Chemin d'accès complet du fichier de liaison à importer, nom du fichier inclus. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets (").|  
    |**/ ApplicationName**|Nom de l'application BizTalk où les liaisons doivent être importées. L'application doit exister, faute de quoi, l'opération d'importation échoue. L'application BizTalk par défaut est utilisée si ce paramètre n'est pas spécifié. Les noms d'application incluant des espaces doivent être placés entre guillemets (").|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [L’importation de stratégies, les liaisons et les Applications BizTalk](../core/importing-biztalk-applications-bindings-and-policies.md)   
 [Commande ImportBindings](../core/importbindings-command.md)