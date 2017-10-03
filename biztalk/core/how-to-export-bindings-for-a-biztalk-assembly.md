---
title: "Comment exporter des liaisons d’un Assembly BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies, bindings
- assemblies, exporting
- exporting, assemblies
ms.assetid: 7e37348d-5fa5-43cc-b3c0-2d8cb6a8f394
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64086cc8e54d89180d3c95268c78bc53e5ec9f55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-export-bindings-for-a-biztalk-assembly"></a>Exportation des liaisons d'un assembly BizTalk
Cette rubrique décrit comment exporter des liaisons pour un assembly BizTalk vers un fichier .xml à l'aide de la console Administration de BizTalk Server ou de l'invite de commandes. Vous pourrez ensuite importer ces liaisons dans une application BizTalk, ce qui aura pour effet de remplacer les liaisons existantes par les liaisons importées du même nom. Vous pouvez exporter les liaisons pour un assembly avant de le mettre à jour, afin de pouvoir importer les liaisons après la mise à jour afin de les réappliquer. Pour plus d’informations sur la mise à jour des applications et des assemblys, consultez [mise à jour des Applications BizTalk](../core/updating-biztalk-applications.md). Pour plus d’informations sur l’utilisation de fichiers de liaison, consultez [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter les procédures de cette rubrique, vous devez avoir ouvert une session en tant que membre du groupe des opérateurs de BizTalk Server ou du groupe d'administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="to-export-bindings-for-a-biztalk-assembly"></a>Pour exporter les liaisons pour un assembly BizTalk  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez successivement [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], le groupe BizTalk, puis Applications.  
  
3.  Cliquez sur l’application contenant l’assembly, pointez sur **exporter**, puis cliquez sur **liaisons**.  
  
4.  Dans la page Exporter les liaisons, dans **exportation vers le fichier**, tapez le chemin d’accès absolu du fichier .xml vers lequel exporter les liaisons.  
  
     Exemple : **C:\Bindings\MyAssemblyBindings_Staging1.xml**  
  
5.  Dans la page Exporter les liaisons, cliquez sur **exporter les liaisons de l’assembly sélectionné**, puis dans **Assembly**, cliquez sur l’assembly.  
  
6.  Si vous voulez exporter toutes les informations du tiers dans le groupe, sélectionnez **exporter les informations du tiers Global**.  
  
     Les liaisons sont exportées vers un fichier .xml à l'emplacement spécifié.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **Facultatif /Destination de BTSTask ExportBindings :** *valeur* **/AssemblyName :** *valeur* [**/GlobalParties**] [**/Server :***valeur*] [**/Database :***valeur*]  
  
     Exemple :  
  
     **Facultatif /Destination de BTSTask ExportBindings : « C:\Binding Files\MyBindings.xml » /AssemblyName:"ErrorHandling.ErrorHandler, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 11e921d58826420e « /Server:MyDatabaseServer Server**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**Et de destination**|Chemin d'accès complet du fichier de liaison à créer, nom du fichier inclus. Si un fichier de liaison doté du même chemin d'accès existe déjà, il est remplacé. Si le chemin d’accès contient des espaces, vous devez le placer entre guillemets doubles («).|  
    |**/ AssemblyName**|Identificateur unique local (LUID) de l'assembly à partir duquel les liaisons sont exportées. Vous pouvez obtenir une liste des LUID pour les artefacts dans une application à l’aide de la [commande ListApp](../core/listapp-command.md).|  
    |**/ GlobalParties**|Si spécifié, exporte les informations de global suffit pour le groupe.|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [L’exportation des liaisons](../core/exporting-bindings6.md)   
 [Commande ExportBindings](../core/exportbindings-command.md)   
 [L’importation de stratégies, les liaisons et les Applications BizTalk](../core/importing-biztalk-applications-bindings-and-policies.md)