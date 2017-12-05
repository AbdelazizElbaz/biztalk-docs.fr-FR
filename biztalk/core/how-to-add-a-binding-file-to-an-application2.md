---
title: "L’ajout d’un fichier de liaison à une Application2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [applications], binding files
- applications, binding files
- binding files, applications
ms.assetid: 1543ee5f-9ae4-4683-b6fe-ee84028c381d
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a1c7f0a73f811a6b339428e62a93916d9301edf
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-add-a-binding-file-to-an-application"></a>Ajout d'un fichier de liaison à une application
Cette rubrique décrit comment ajouter un fichier de liaison à une application BizTalk à l'aide de la console Administration de BizTalk Server ou de la ligne de commande. Vous pouvez souhaiter procéder ainsi pour faciliter les déploiement d’application ou l’assembly, comme décrit dans [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md).  
  
 Vous pouvez exporter des liaisons dans un fichier .xml à partir d’un assembly, une application ou un groupe, une application BizTalk, comme décrit dans [exportation des liaisons](../core/exporting-bindings6.md), puis utilisez une des procédures de cette rubrique pour ajouter le fichier de liaison à une application.  
  
 Dans ce cas, le fichier de liaison est ajouté à base de données de gestion BizTalk et s'affiche dans la console Administration de BizTalk Server, dans le dossier Ressources de l'application. Contrairement à l'importation d'un fichier de liaison, l'ajout d'un tel fichier ne s'applique pas immédiatement aux liaisons existantes. Au lieu de cela, les liaisons sont appliquées lorsque l'application est importée dans un autre groupe BizTalk.  
  
> [!IMPORTANT]
>  Pour des raisons de sécurité, lorsque vous exportez des liaisons, BizTalk Server ne conserve pas les mots de passe des liaisons du fichier. Une fois les liaisons importées, vous devez reconfigurer les mots de passe des ports d'envoi et des emplacements de réception pour qu'ils fonctionnent. Vous configurez ces mots de passe dans la boîte de dialogue Propriétés du transport de la console Administration de BizTalk Server pour le port d'envoi ou l'emplacement de réception. Pour obtenir des instructions, consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md). Voir aussi [la création d’un emplacement de réception](../core/how-to-create-a-receive-location.md).  
  
> [!NOTE]
>  Lorsque vous utilisez un fichier de liaison qui a été généré dans [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)], veillez à ce que le niveau de confiance de l'hôte ne soit pas conservé dans le fichier de liaison. Lorsque les liaisons sont appliquées pendant l'importation de la liaison ou de l'application, les artefacts sont liés aux hôtes, en fonction du nom de l'hôte uniquement Pensez à vérifier que les artefacts ont été liés à l'hôte correct et que le niveau de confiance est adéquat.  
  
 Lorsque vous ajoutez un fichier de liaison à une application, vous pouvez spécifier une valeur pour l'environnement de déploiement cible avec une chaîne qui représente l'environnement, telle que Test ou Production. Vous pouvez utiliser la chaîne de votre choix pour cette valeur. Ensuite, lorsque vous importez l'application, vous pouvez sélectionner le fichier de liaison à appliquer, en fournissant la valeur spécifiée pour son environnement de déploiement cible. Ce faisant, les liaisons sont appliquées depuis le fichier de liaison. Toutes les liaisons existant dans l'application, portant le même nom que les liaisons du fichier, sont automatiquement remplacées.  
  
 Lorsque vous importez une application, les liaisons sont appliquées dans l'ordre suivant. À mesure que des liaisons sont appliquées au cours du processus d'importation, les liaisons déjà appliquées sont remplacées par de nouvelles liaisons qui portent le même nom. Autrement dit, la liaison d'un nom donné la plus récente est celle qui est effectivement appliquée.  
  
1.  Liaisons d'application générées par BizTalk Server, n'ayant pas été explicitement ajoutées à l'application au moyen d'un fichier de liaison, mais ayant été sélectionnées par l'utilisateur pour leur exportation dans le fichier .msi de l'application.  
  
2.  Fichiers de liaison ajoutés de manière explicite mais pour lesquels aucun environnement de déploiement cible n'a été défini. À l'intérieur de cet ensemble, l'application des liaisons ne respecte pas d'ordre particulier.  
  
3.  Liaisons ajoutées de manière explicite auxquelles est associé un environnement de déploiement cible correspondant à l'environnement de déploiement sélectionné pour l'importation de l'application. À l'intérieur de cet ensemble, l'application des liaisons ne respecte pas d'ordre particulier.  
  
 Pour plus d’informations sur l’importation d’applications et l’application des liaisons, consultez [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="to-add-a-binding-file-to-an-application"></a>Pour ajouter un fichier de liaison à une application  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez Administration de BizTalk Server et le groupe BizTalk contenant l’application à laquelle vous souhaitez ajouter un fichier de liaison.  
  
3.  Développez Applications et cliquez avec le bouton droit sur l'application à laquelle vous souhaitez ajouter le fichier de liaison.  
  
4.  Pointez sur **ajouter**, puis cliquez sur **ressources**.  
  
5.  Cliquez sur **ajouter**, sélectionnez le fichier à ajouter, puis cliquez sur **ouvrir**.  
  
6.  Pour remplacer un fichier de liaison existant dans cette application qui a le même nom de fichier, sélectionnez le **remplacer tous les** case à cocher. Si vous ne spécifiez pas cette option et qu'un fichier du même nom existe déjà dans l'application, l'opération d'ajout échouera.  
  
7.  Dans le **type de fichier** la liste déroulante, sélectionnez **System.BizTalk : biztalkbinding**.  
  
8.  Dans **environnement cible**, tapez une chaîne représentant l’environnement de déploiement cible où vous souhaitez les liaisons de ce fichier à être appliquées, tel que Test, puis cliquez sur **OK**.  
  
    > [!IMPORTANT]
    >  Si vous laissez ce champ vierge, les liaisons de ce fichier seront appliquées à l'importation de l'application.  
  
     Le fichier de liaison est ajouté et s'affiche dans le dossier Ressources de l'application.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **BTSTask AddResource** [**« ApplicationName » : «***valeur***»**] **/Type:System.BizTalk:BizTalkBinding** [ **/Overwrite**] **/Source :***valeur***/Property:TargetEnvironment = «***valeur* **»** [**/Server :***valeur*] [**/Database :***valeur*]  
  
     Exemple :  
  
     **« ApplicationName » BTSTask AddResource : « My Application », /Type:System.BizTalk:BizTalkBinding/source : « C:\Binding Files\MyBinding.xml » /Property:TargetEnvironment = « Production » /Server:MyDatabaseServer Server**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**/ ApplicationName**|Nom de l'application BizTalk à laquelle ajouter le fichier de liaison. Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («).|  
    |**Type**|**System.BizTalk : biztalkbinding** (cette valeur ne respecte pas la casse).|  
    |**/ Remplacer**|Option permettant de mettre à jour un fichier de liaison existant. Si ce n’est pas spécifié, liaison et le fichier existe déjà dans l’application qui a le même nom que le fichier ajouté, l’opération AddResource échoue.|  
    |**/ Source**|Chemin d'accès complet du fichier de liaison, nom du fichier inclus. Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets doubles (").|  
    |**/Property:TargetEnvironment =**|Chaîne indiquant l'environnement de déploiement cible. Vous pouvez la chaîne de votre choix (ex. : Production). Exemple : **/Property:TargetEnvironment = « Production »**<br /><br /> Si non spécifié, la valeur \<par défaut\> est appliqué automatiquement. La valeur respecte la casse. Si elle comprend des espaces, vous devez la placer entre guillemets doubles ("). La longueur maximale de cette valeur ne doit pas dépasser 128 caractères.|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des assemblys .NET, certificats et autres ressources](../core/managing-net-assemblies-certificates-and-other-resources.md)   
 [Commande AddResource : Liaison de BizTalk](../core/addresource-command-biztalk-binding.md)   
 [Création et modification des applications BizTalk](../core/creating-and-modifying-biztalk-applications.md)