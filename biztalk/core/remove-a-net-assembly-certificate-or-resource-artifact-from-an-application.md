---
title: "Comment supprimer un Assembly .NET, certificat ou autre artefact de ressource à partir d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- virtual directories, deleting
- managing [.NET assemblies], deleting
- managing [applications], COM components
- managing [applications], deleting artifcats
- managing [certificates], deleting
- deleting, binding files
- binding files, deleting
- managing, COM components
- COM components, deleting
- managing [artifacts], deleting
- .NET assemblies, deleting
- deleting, virtual directories
- deleting, definitions [BAM]
- applications, .NET assemblies
- certificates, deleting
- deleting, .NET assemblies
- deleting, artifacts
- deleting, certificates
ms.assetid: b84eebac-261d-495f-80cd-ddda5bb08bef
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a82ffc63ff041aec1e9151e8198e2a7c3e74b3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-net-assembly-certificate-or-other-resource-artifact-from-an-application"></a>Suppression d'un assembly .NET, d'un certificat ou d'un autre artefact de ressource d'une application
Cette rubrique explique comment supprimer les artefacts de ressource suivants d'une application BizTalk à l'aide de la console Administration de BizTalk Server ou de la ligne de commande. L'utilisation des procédures de cette rubrique supprime l'artefact de la base de données de gestion BizTalk. Elle ne supprime pas l'artefact du système de fichiers, du magasin de certificats, des services IIS (Internet Information Services) ou du registre Windows s'il existe à ces emplacements. Par ailleurs, si vous supprimez un fichier de liaison, les liaisons restantes ne sont pas modifiées : seul le fichier de liaison est supprimé.  
  
-   assemblys .NET  
  
-   composants des services COM  
  
-   Certificats  
  
-   Fichiers ad hoc  
  
-   définitions BAM  
  
-   Fichiers de liaison  
  
-   Répertoires virtuels  
  
 Si un répertoire virtuel est ajouté de manière explicite à une application, en étant importé ou ajouté, vous pouvez le supprimer à l'aide des procédures de cette rubrique. S'il n'a pas été ajouté de manière explicite, mais par référence lors de la configuration d'un emplacement de réception, vous ne pouvez pas le supprimer à l'aide de ces procédures. Cela est dû au fait qu'il n'est pas stocké dans la base de données de gestion BizTalk. Si vous exportez le fichier .msi de l'application, le répertoire virtuel sera obtenu à partir de IIS et sera ajouté au fichier .msi. Si vous exportez le fichier .msi, le répertoire virtuel sera ajouté à la base de gestion BizTalk Management de ce groupe.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="to-remove-a-resource-artifact-from-an-application"></a>Pour supprimer un artefact de ressource d'une application  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez successivement Administration de [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], le groupe BizTalk contenant l'artefact de ressource à supprimer, puis l'application contenant l'artefact.  
  
3.  Cliquez sur le **ressources** dossier, cliquez sur l’artefact, puis cliquez sur **supprimer**.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **BTSTask RemoveResource** [**« ApplicationName » :***valeur*] **ApplicationName :***valeur* [  **/Server :**  *valeur*] [**/Database :***valeur*]  
  
     Exemple :  
  
     **BTSTask RemoveResource /ApplicationName:MyApplication ApplicationName : « MyAssembly, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 0123456789ABCDEF »**  
  
    |Paramètre| Description|  
    |---------------|-----------------|  
    |**/ ApplicationName**|Nom de l'application BizTalk contenant l'artefact à supprimer. Si cette valeur n'est pas définie, l'application par défaut est utilisée. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («).|  
    |**/ Luid**|Identificateur unique local (LUID) de l'artefact. Vous pouvez obtenir l’identificateur LUID à l’aide de la **ListApp** de commande, comme décrit dans [commande ListApp](../core/listapp-command.md).|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des assemblys .NET, certificats et autres ressources](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [Commande RemoveResource](../core/removeresource-command.md)