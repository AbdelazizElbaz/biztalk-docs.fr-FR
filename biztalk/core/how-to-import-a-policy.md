---
title: "Comment importer une stratégie | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, requirements
- importing, policies
- policies, importing
- managing [policies], importing
ms.assetid: 92f6ef18-279f-416d-b13e-8b9642539d27
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac21ad1348dbc934c81d87f3c477977eeecd2ccf
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-import-a-policy"></a>Comment importer une stratégie
Cette rubrique explique comment importer une stratégie dans un groupe BizTalk ou dans une application BizTalk à l'aide respectivement de la console Administration de BizTalk Server ou de l'outil de ligne de commande BTSTask.  
  
 Vous pouvez créer une stratégie à l’aide de l’éditeur des règles d’entreprise, comme décrit dans [création des règles d’entreprise à l’aide de l’éditeur des règles d’entreprise](../core/creating-business-rules-using-the-business-rule-composer.md), puis l’importez directement, ou vous pouvez exporter une stratégie à partir d’un autre groupe BizTalk, comme décrit dans [Comment exporter une stratégie](../core/how-to-export-a-policy.md) , puis l’importer.  
  
 L'importation d'une stratégie l'enregistre dans la base de données du moteur de règles du groupe BizTalk. Une fois la stratégie importée, vous pouvez l'afficher dans la console Administration de BizTalk Server. Si vous utilisez la console Administration de BizTalk Server pour importer une stratégie, elle s’affichera dans le \<tous les artefacts\> nœud pour le groupe BizTalk. Vous pouvez ensuite le publier pour le rendre disponible pour l’ajouter à une application BizTalk, comme décrit dans [comment publier une stratégie](../core/how-to-publish-a-policy.md). Si vous utilisez l'outil de ligne de commande BTSTask pour importer une stratégie, celle-ci sera automatiquement publiée et s'affichera dans le dossier Stratégies de l'application dans laquelle vous l'avez importée.  
  
 Lorsque vous importez une stratégie, gardez les points importants suivants à l'esprit :  
  
-   Même si vous spécifiez l'option permettant de remplacer une stratégie existante par une autre importée, vous ne pouvez pas en importer une qui existe déjà dans la base de données du moteur de règles du groupe et qui a été déployée. L'opération d'importation échouera.  
  
-   Même si la stratégie était déployée lors de son exportation à partir d'un autre groupe BizTalk group, elle ne le sera pas une fois importée.  
  
-   BTSTask ne fournit pas de commande spécifique d'importation de stratégies ; toutefois, vous pouvez utiliser la commande ExportApp de BTSTask pour exporter de manière sélective uniquement les stratégies d'une application souhaitées, sans les autres artefacts de l'application. Vous pouvez ensuite utiliser la commande ImportApp pour importer le fichier .msi dans une application d'un autre groupe BizTalk. Cette approche est décrite dans cette rubrique. Lorsque vous adoptez cette approche, la stratégie est automatiquement importée et publiée dans le groupe BizTalk, puis elle est ajoutée à l'application spécifiée.  
  
 Pour plus d’informations sur l’utilisation des stratégies, consultez [gestion des stratégies de](../core/managing-policies.md). Pour les meilleures pratiques sur l’ajout de stratégies aux applications, consultez [meilleures pratiques pour déployer une Application BizTalk](../core/best-practices-for-deploying-a-biztalk-application.md).  
  
> [!NOTE]
>  Le développeur de solutions peut créer des stratégies, puis les importer dans la base de données du moteur de règles pour le groupe d’à l’aide de l’Assistant Déploiement du moteur de règles, comme décrit dans [comment déployer et annuler le déploiement de stratégies et vocabulaires](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 La configuration suivante est requise pour exécuter les procédures décrites dans cette rubrique :  
  
-   Vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
-   Le moteur des règles d'entreprise doit être installé. Pour plus d’informations, consultez [vue d’ensemble de l’Installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5).  
  
-   Pour importer une stratégie à l'aide de la console Administration de BizTalk Server, vous devez disposer d'un fichier .xml contenant la stratégie à importer. Vous pouvez générer un fichier .xml de ce type en exportant une stratégie à partir d’un autre groupe BizTalk ou application, comme décrit dans [comment exporter une stratégie](../core/how-to-export-a-policy.md), ou à l’aide de l’éditeur des règles d’entreprise, comme décrit dans [comment importer et exporter Stratégies et vocabulaires](../core/how-to-import-and-export-policies-and-vocabularies.md).  
  
-   Pour importer une stratégie à l'aide de BTSTask, vous devez disposer d'un fichier .msi contenant la stratégie à importer. Pour obtenir des instructions, consultez [comment exporter une stratégie](../core/how-to-export-a-policy.md).  
  
## <a name="to-import-a-policy"></a>Pour importer une stratégie  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk dans lequel vous souhaitez importer la stratégie, développez **Applications**, puis développez  **\<tous les artefacts\>** .  
  
3.  Avec le bouton droit **stratégies**, puis cliquez sur **importation**.  
  
4.  Recherchez le fichier .xml contenant la stratégie et cliquez sur **ouvrir**.  
  
     La stratégie est importée dans le groupe et s’affiche dans le **stratégies** dossier de  **\<tous les artefacts\>**.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **ImportApp /Package de BTSTask :** *valeur* [**« ApplicationName » :***valeur*] [**/overwrite**] [ **/ Server :***valeur*] [**/Database :***valeur*]  
  
     Exemple :  
  
     **/Package ImportApp de BTSTask : « C:\MSI Files\MyApplication.msi » /Environment:Test /ApplicationName:MyApplication de remplacement**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**/ Package**|Chemin d'accès complet au fichier .msi contenant la stratégie à importer. Si le chemin d’accès comprend des espaces, vous devez le placer entre guillemets («).|  
    |**/ ApplicationName**|Nom de l'application BizTalk dans laquelle importer la stratégie. Si ce nom n'est pas spécifié, le nom d'application spécifié lors de l'exportation du fichier .msi est utilisé. Si l’application spécifiée n’existe pas, il sera créé. Les noms d'application incluant des espaces doivent être placés entre guillemets doubles (").|  
    |**/ Remplacer**|Option permettant de remplacer les stratégies de l'application par les artefacts du fichier .msi ayant le même nom et numéro de version. Si cette option n'est pas spécifiée et qu'une ou plusieurs stratégies de l'application ont le même nom et numéro de version que les celles du fichier .msi, l'importation échoue. Vous pouvez afficher le nom et numéro de version des stratégies dans une application à l’aide de la [commande ListApp](../core/listapp-command.md).|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
## <a name="see-also"></a>Voir aussi  
 [L’importation de stratégies, les liaisons et les Applications BizTalk](../core/importing-biztalk-applications-bindings-and-policies.md)   
 [Exportation de stratégies, les liaisons et les Applications BizTalk](../core/exporting-biztalk-applications-bindings-and-policies.md)   
 [Gestion des stratégies](../core/managing-policies.md)