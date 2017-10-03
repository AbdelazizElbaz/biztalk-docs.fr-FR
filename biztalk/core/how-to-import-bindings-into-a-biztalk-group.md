---
title: Comment importer des liaisons dans un groupe BizTalk | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- groups, importing
- importing, bindings
- groups, bindings
- bindings, groups
ms.assetid: 38da14fb-3522-4274-a633-2ff24e4bd574
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1cfc20fea950c737d59e6b325744a02ee67bb63f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-import-bindings-into-a-biztalk-group"></a>Importation des liaisons dans un groupe BizTalk
Cette rubrique décrit comment importer des liaisons dans un groupe BizTalk à partir d'un fichier .xml à l'aide de la console Administration de BizTalk Server ou de l'invite de commandes. Pour obtenir des instructions sur l’exportation des liaisons dans un fichier .xml que vous pouvez importer à partir d’un groupe BizTalk, consultez [comment exporter les liaisons pour un groupe BizTalk](../core/how-to-export-bindings-for-a-biztalk-group.md).  
  
 Vous pouvez également importer des liaisons dans une application BizTalk, comme décrit dans [comment importer les liaisons dans une Application BizTalk](../core/how-to-import-bindings-into-a-biztalk-application.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="to-import-bindings-into-a-biztalk-group"></a>Pour importer des liaisons dans un groupe BizTalk  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, le groupe BizTalk, puis cliquez sur **Applications**.  
  
3.  Pointez sur **importation**, puis cliquez sur **liaisons**.  
  
4.  Cliquez sur le fichier de liaison et cliquez sur **ouvrir**.  
  
     Les artefacts du fichier de liaison sont écrits dans le groupe. Elles s’affichent dans les dossiers appropriés de le \<tous les artefacts > nœud.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **BTSTask ImportBindings /Source :** *valeur* **paramètre « GroupLevel »** [**/Server :***valeur*] [**/ Base de données :***valeur*]  
  
     La commande suivante permet d'importer des liaisons dans le groupe défini dans la base de données de gestion BizTalk qui s'exécute sur une instance de SQL Server appelée MyServer.  
  
     **BTSTask ImportBindings GroupLevel /Server:MyServer Server /Source:C:\Bindings\Binding1.xml**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**/ Source**|Chemin d'accès complet du fichier de liaison à importer, nom du fichier inclus. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets (").|  
    |**/ GroupLevel**|Option permettant d'importer le fichier de liaison dans le groupe actuel.|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [L’importation de stratégies, les liaisons et les Applications BizTalk](../core/importing-biztalk-applications-bindings-and-policies.md)   
 [Commande ImportBindings](../core/importbindings-command.md)