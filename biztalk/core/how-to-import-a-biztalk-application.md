---
title: Comment importer une Application BizTalk | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, planning
- planning, importing
- importing, applications
- applications, planning
- planning, deploying
- applications, importing
- importing, planning
ms.assetid: 51169f35-d572-4612-9104-a59908e24874
caps.latest.revision: "70"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e640a11c709b25336b2a1625c42ce40b49926982
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-import-a-biztalk-application"></a>Comment importer une Application BizTalk
Cette rubrique décrit l'importation d'une application BizTalk dans un groupe BizTalk à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou de l'invite de commandes. Importer une application BizTalk inscrit les artefacts dans la base de données de gestion BizTalk et écrit les données des artefacts dans les bases de données BizTalk appropriées. Pour plus d’informations, consultez [que se passe-t-il lorsque artefacts sont importés](../core/what-happens-when-artifacts-are-imported.md). Le fait d'importer une application n'installe pas l'application. Vous devez installer une application incluant des artefacts basés sur un fichier pour qu'elle puisse s'exécuter.  
  
 Lorsque vous importez une application à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], l'emplacement à partir duquel vous lancez l'Assistant MSI d'importation détermine si vous pouvez créer ou non une application pendant que vous importez les artefacts. Si vous démarrez l'Assistant en cliquant avec le bouton droit sur le groupe BizTalk, vous devez fournir un nom d'application. Si une application du groupe BizTalk porte déjà le nom que vous spécifiez, les artefacts du fichier sont importés dans cette application. Dans le cas contraire, une nouvelle application portant le nom spécifié est créée et les artefacts sont importés dans cette application. Si vous lancez l'Assistant en cliquant avec le bouton droit sur une application, vous ne pouvez pas spécifier de nom d'application et les artefacts sont importés dans l'application actuelle.  
  
 Lorsque vous utilisez l'outil de ligne de commande BTSTask pour importer un fichier .msi, il n'est pas obligatoire de spécifier un nom d'application. Si vous ne spécifiez pas de nom, les artefacts du fichier sont importés dans l'application par défaut.  
  
 Après avoir importé les artefacts, vous pouvez les afficher dans le dossier approprié figurant dans le dossier de l'application dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez également afficher une liste des artefacts dans l’application à l’aide de BTSTask, comme décrit dans [commande ListApp](../core/listapp-command.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour importer une application BizTalk, vous devez ouvrir une session à l'aide d'un compte membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour installer une application BizTalk, vous devez également disposer d'autorisations en écriture sur le système de fichiers local. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="considerations-for-importing-applications"></a>Considérations relatives à l'importation d'applications  
 Lors de l'importation d'une application, tenez compte des éléments suivants :  
  
-   **L’importation d’applications à partir de versions précédentes de BizTalk Server**. Si vous importez des applications depuis BizTalk Server 2006 R2 ou BizTalk Server 2009 et que celles-ci contiennent des données de tiers EDI/AS2, l'importation peut échouer car le modèle de gestion des partenaires commerciaux a été considérablement modifié dans [!INCLUDE[prague](../includes/prague-md.md)]. Vous devez plutôt utiliser l'outil de migration de tiers pour migrer les données de tiers depuis les versions précédentes de BizTalk Server. Pour plus d’informations sur l’outil, consultez [migration des artefacts EDI à partir d’une Version précédente de BizTalk Server](http://msdn.microsoft.com/library/b956a97e-03d0-47ea-a2ce-c07a339c0f2c).  
  
-   **Les liaisons existantes sont toujours remplacées par les liaisons importées.** Lorsque vous importez un fichier .msi contenant des liaisons dans une application existante, les liaisons existantes sont remplacées par celles importées portant le même nom, et ce même si vous n'avez pas sélectionné l'option de remplacement des artefacts existants lors de l'importation du fichier .msi. Pour éviter que les liaisons de l'application exportée ne remplacent les liaisons de l'application dans laquelle vous importez le fichier .msi, ne sélectionnez pas le fichier de liaison en tant que ressource à exporter pendant l'opération d'exportation. Pour plus d’informations, consultez [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md).  
  
     À mesure que des liaisons sont appliquées au cours du processus d'importation, les liaisons déjà appliquées sont remplacées par de nouvelles liaisons qui portent le même nom. Autrement dit, la liaison d'un nom donné la plus récente est celle qui est effectivement appliquée. Lorsque vous importez une application, les liaisons sont appliquées dans l'ordre suivant :  
  
    1.  Liaisons d'application générées par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], n'ayant pas été explicitement ajoutées à l'application au moyen d'un fichier de liaison, mais ayant été sélectionnées par l'utilisateur pour leur exportation dans le fichier .msi de l'application.  
  
    2.  Fichiers de liaison ajoutés de manière explicite mais pour lesquels aucun environnement de déploiement cible n'a été défini. À l'intérieur de cet ensemble, l'application des liaisons ne respecte pas d'ordre particulier.  
  
    3.  Liaisons ajoutées de manière explicite auxquelles est associé un environnement de déploiement cible correspondant à l'environnement de déploiement sélectionné pour l'importation de l'application. À l'intérieur de cet ensemble, l'application des liaisons ne respecte pas d'ordre particulier.  
  
-   **L’hôte doit exister dans le groupe.** Un hôte correspondant à l'hôte spécifié dans les liaisons d'application contenues dans le fichier .msi doit déjà exister dans le groupe BizTalk, sans quoi l'opération d'importation échoue. En outre, le niveau de confiance de l'hôte doit correspondre.  
  
-   **Vous devrez peut-être ajouter une référence à une autre application.** Si l'application que vous importez est dépendante d'un artefact présent dans une autre application, vous devez ajouter une référence à cette application. L'application et l'artefact requis doivent déjà exister dans le groupe. L'Assistant Importation fournit cette option. Si vous utilisez la commande ImportApp de BTSTask, toutefois, vous devez ajouter la référence à l’application après l’importation, comme décrit dans [comment ajouter une référence à une autre Application](../core/how-to-add-a-reference-to-another-application.md). Pour plus d’informations, consultez [des dépendances et déploiement d’applications](../core/dependencies-and-application-deployment.md). L'Assistant Importation établit des correspondances entre les références et les applications existantes du groupe et vous permet d'ajouter ou de modifier une référence. Effectuez l'étape supplémentaire permettant de vérifier que l'application référencée contient l'artefact requis.  
  
-   **Si une opération d’importation expire, fractionnez l’application en fichiers .msi supplémentaires.** Une opération d'importation expire si elle dépasse 3 600 secondes. Si vous essayez d'importer un fichier .msi et que l'opération arrive à expiration, vous devez diviser le contenu de l'application en plusieurs fichiers .msi en réexportant l'application et en sélectionnant un sous-ensemble d'artefacts à exporter. Pour plus d’informations, consultez [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md).  
  
> [!IMPORTANT]
>  Pour des raisons de sécurité, pendant l'exportation d'une application, les mots de passe sont supprimés des liaisons d'application. Néanmoins, ils ne sont pas supprimés des fichiers de liaison ajoutés à l'application. Après avoir importé l'application, vous devez reconfigurer les mots de passe afin que l'application fonctionne correctement. Pour ce faire, modifiez le fichier de liaison ou utilisez la console Administration. Pour plus d’informations sur la modification d’un fichier de liaison, consultez [personnalisation des fichiers de liaison](../core/customizing-binding-files.md). Pour plus d’informations sur la configuration de la sécurité pour les adaptateurs, consultez [à l’aide des adaptateurs](../core/using-adapters.md).  
  
> [!NOTE]
>  Si une importation échoue, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] annule toutes les opérations d'importation sauf pour les actions effectuées par des scripts personnalisés.  
  
> [!NOTE]
>  Si vous créez un filtre pour un port d'envoi dans une application qui utilise un schéma de propriété d'une autre application et que vous importiez ensuite la première application dans un nouveau groupe BizTalk, vous ne recevrez pas de message vous avertissant de l'absence de schéma et le filtrage ne fonctionnera pas une fois l'application installée et démarrée. Vous pouvez corriger ce problème en important l'application qui contient le schéma avant d'installer l'application sans schéma.  
  
## <a name="to-import-a-biztalk-application"></a>Pour importer une application BizTalk  
  
#### <a name="using-the-biztalk-server-administration-console"></a>À l’aide de la Console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] et le groupe BizTalk, puis effectuez l'une des opérations suivantes :  
  
    -   Pour importer l’application et les artefacts contenus dans le fichier .msi dans le groupe BizTalk, cliquez sur **Applications**, pointez sur **importer**, puis cliquez sur **fichier MSI**.  
  
    -   Pour importer les artefacts contenus dans le fichier .msi dans une application existante, développez **Applications**, cliquez sur l’application, pointez sur **importer**, puis cliquez sur **le fichier MSI**.  
  
3.  Sur la page d’accueil de l’Assistant MSI d’importation, dans **fichier MSI à importer**, tapez le chemin d’accès du fichier .msi, puis cliquez sur **suivant**. Si nécessaire, vous pouvez rechercher le fichier .msi en cliquant sur le **...** .  
  
4.  Dans la page Paramètres de l’Application, dans le **nom de l’Application** liste déroulante, sélectionnez la nom de l’application si elle est disponible. Cette liste apparaît si vous importez l'application dans le groupe BizTalk.  
  
    > [!NOTE]
    >  Elle comprend le nom de toutes les applications actuellement présentes dans le groupe BizTalk, ainsi que le nom de l'application à partir de laquelle le fichier .msi a été exporté. Si vous sélectionnez ce dernier et que l'application n'existe pas déjà dans ce groupe BizTalk, l'Assistant Importation crée une application. Si vous sélectionnez une application existant déjà dans le groupe, l'Assistant Importation importe les artefacts du fichier .msi dans l'application existante.  
  
5.  Dans **applications disponibles auxquelles ajouter des références aux**, sélectionnez les applications auxquelles ajouter des références, éventuellement, puis cliquez sur **suivant**.  
  
6.  Si vous importez le fichier .msi dans une application existante et que vous souhaitez remplacer les artefacts dans l’application existante, sélectionnez **remplacer les ressources**.  
  
    > [!NOTE]
    >  Si vous ne sélectionnez pas cette option et que le fichier .msi contient un artefact existant déjà dans l'application, l'opération d'importation échoue et est annulée. Certains types d'artefact d'une application ou d'un groupe BizTalk doivent être uniques. Si vous ajoutez un artefact existant déjà dans le groupe BizTalk mais pas dans l'application actuelle, l'opération d'importation échoue, même si vous avez activé l'option de remplacement. Pour plus d’informations sur les artefacts doivent être uniques et de quelle manière ils doivent être uniques, consultez [artefacts que doit être Unique dans une Application ou d’un groupe](../core/artifacts-that-must-be-unique-in-an-application-or-group.md).  
  
7.  Dans la page Paramètres d’environnement cible Application, dans le **environnement intermédiaire cible** la liste déroulante, sélectionnez l’environnement cible pour cette application, puis cliquez sur **suivant**. Cette liste comprend tous les environnements spécifiés pour les fichiers de liaison ajoutés à cette application. Sélectionnez \<par défaut > Si vous souhaitez appliquer toutes les liaisons dans l’application à l’exception de celles qui ont un environnement cible spécifié. Si le fichier .msi ne contient pas un fichier de liaison que vous souhaitez appliquer explicitement, vous pouvez laisser \<par défaut > sélectionnée.  
  
    > [!NOTE]
    >  Vous spécifiez l'environnement cible des liaisons lorsque vous ajoutez un fichier de liaison à une application. Pour plus d’informations, consultez [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md). Pour obtenir des instructions sur l’ajout de fichiers de liaison, consultez [l’ajout d’un fichier de liaison à une Application](../core/how-to-add-a-binding-file-to-an-application2.md).  
  
8.  Dans la page Résumé d’importation, vérifiez que les informations de résumé sont correctes, puis cliquez sur **importation**.  
  
9. Dans la page Importation réussie, si vous souhaitez installer l’application sur l’ordinateur local, sélectionnez le **exécuter l’Assistant Installation de Application pour installer l’application sur l’ordinateur local** case à cocher.  
  
    > [!NOTE]
    >  Il n'est pas nécessaire d'installer l'application, sauf si vous devez l'exécuter telle qu'elle est actuellement configurée sur l'ordinateur local. Cependant, si l'application comprend des artefacts basés sur un fichier, vous devez l'installer sur tous les ordinateurs allant l'exécuter pour qu'elle fonctionne, car importer l'application l'ajoute simplement à la base de données de gestion BizTalk.  
  
10. Cliquez sur **Terminer**.  
  
> [!NOTE]
>  Si l'installation échoue (par exemple, parce que vous ne disposez pas des autorisations en écriture sur le système de fichiers local), elle est annulée mais pas l'opération d'importation.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **ImportApp /Package de BTSTask :** *valeur* [**/Environment :***valeur*] [**« ApplicationName » :**  *valeur*] [**/overwrite**] [**/Server :***valeur*] [**/Database :***valeur*]  
  
     Exemple :  
  
     **/Package ImportApp de BTSTask : « C:\MSI Files\MyApplication.msi » /Environment:Test /ApplicationName:MyApplication de remplacement**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**/ Package**|Chemin d'accès complet du fichier .msi. Si le chemin d’accès comprend des espaces, vous devez le placer entre guillemets («).|  
    |**/ Environnement**|L'environnement cible de déploiement du fichier de liaison à appliquer, tel que Test. Il s'agit de la valeur spécifiée pour l'environnement cible de déploiement lors de l'ajout du fichier de liaison à l'application.|  
    |**/ ApplicationName**|Nom de l'application BizTalk dans laquelle les artefacts du fichier .msi sont importés. Si ce nom n'est pas spécifié, le nom d'application spécifié lors de l'exportation du fichier .msi est utilisé. Si l’application spécifiée n’existe pas, il sera créé. Les noms d'application incluant des espaces doivent être placés entre guillemets doubles (").|  
    |**/ Remplacer**|Option permettant d'écraser les artefacts de l'application avec ceux du fichier .msi dotés du même identificateur local unique (LUID). Si cette option n'est pas spécifiée et qu'un ou plusieurs artefacts dans l'application possèdent le même LUID que des artefacts du fichier .msi, l'importation échoue. Vous pouvez afficher la liste des LUID des artefacts dans une application à l’aide de la [commande ListApp](../core/listapp-command.md).|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [L’importation de stratégies, les liaisons et les Applications BizTalk](../core/importing-biztalk-applications-bindings-and-policies.md)   
 [Commande ImportApp](../core/importapp-command.md)