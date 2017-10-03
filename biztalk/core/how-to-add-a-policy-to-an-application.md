---
title: "Comment ajouter une stratégie à une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [policies], adding to applications
- policies, applications
- applications, policies
- policies, adding to applications
ms.assetid: 93b3ce5e-8c63-4c64-9bdc-1747541ba9a8
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ad9eaf1e2f14e51e60ad3f18e31cdaa72fa906a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-policy-to-an-application"></a>Ajout d'une stratégie à une application
Cette rubrique explique comment ajouter une stratégie à une application BizTalk à l'aide de la console Administration de BizTalk Server ou de la ligne de commande. La console d'administration vous permet d'ajouter plusieurs stratégies à la fois. L'ajout d'une stratégie à une application permet à celle-ci et à toutes les autres y faisant référence de l'utiliser.  
  
 Lorsque vous ajoutez une stratégie à une application, gardez les points importants suivants à l'esprit :  
  
-   Avant que vous pouvez ajouter une stratégie à une application, la stratégie doit exister dans la base de données du moteur de règles pour le groupe BizTalk, et il doit être publié, comme décrit dans [comment importer une stratégie](../core/how-to-import-a-policy.md).  
  
    > [!NOTE]
    >  Si vous supprimez une stratégie de la base de données du moteur de règles à l'aide de l'Assistant Déploiement du moteur de règles, elle s'affichera toujours dans la console d'administration, mais vous ne pourrez pas la publier. Pour plus d’informations sur l’Assistant Déploiement du moteur de règles, consultez [comment déployer et annuler le déploiement de stratégies et vocabulaires](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md).  
  
-   La stratégie ne doit pas déjà exister dans une autre application du groupe BizTalk.  
  
    > [!IMPORTANT]
    >  Si une stratégie est partagée entre plusieurs applications, vous devez créer une application distincte qui la contiendra, puis créer des références des applications qui l'utiliseront vers cette application. En effet, si vous arrêtez une application contenant une stratégie, le déploiement de celle-ci est automatiquement annulé et elle ne fonctionne plus pour aucune des applications qui l'utilisent. Pour obtenir des instructions sur l’ajout d’une référence, consultez [comment ajouter une référence à une autre Application](../core/how-to-add-a-reference-to-another-application.md).  
  
-   Pour que la stratégie soit prise en compte et commence à fonctionner, elle doit être déployée. Les stratégies sont déployées automatiquement lorsque l’application démarre, ou vous pouvez les déployer manuellement comme décrit dans [comment déployer ou annuler le déploiement d’une stratégie](../core/how-to-deploy-or-undeploy-a-policy.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="to-add-a-policy-to-an-application"></a>Pour ajouter une stratégie à une application  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez successivement [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis le groupe BizTalk.  
  
3.  Développez Applications, l’application à laquelle vous souhaitez ajouter une stratégie, puis avec le bouton droit **stratégies**.  
  
4.  Pointez sur **ajouter** et cliquez sur **stratégie**.  
  
5.  Activez la case à cocher de chaque stratégie et la version à ajouter, puis cliquez sur **OK**.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **BTSTask AddResource** [**« ApplicationName » :***valeur*] **/Type:System.BizTalk:Rules** [**remplacer**] **/Nom :***valeur***/version :***valeur* [**/Server :***valeur* ] [**/Database :***valeur*]  
  
    > [!NOTE]
    >  Les valeurs de paramètre respectent la casse. Quant aux noms de paramètres, ils ne respectent pas la casse. Par ailleurs, lorsque vous ajoutez une stratégie à une application à l'aide de cette commande, tous les vocabulaires utilisés par la stratégie sont automatiquement ajoutés.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
     Exemple :  
  
     **BTSTask AddResource /ApplicationName:MyApplication /Type:System.BizTalk:Rules /overwrite /Name:MyPolicy /Version:1.0 /Server:MyDatabaseServer Server**  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |**/ ApplicationName**|Nom de l'application BizTalk à laquelle ajouter la stratégie. Si le nom de l'application n'est pas spécifié, l'application utilisée est l'application BizTalk définie par défaut pour le groupe. Les noms qui incluent des espaces doivent être placés entre guillemets doubles («).|  
    |**Type**|**System.BizTalk : Rules**|  
    |**/ Remplacer**|Option permettant de mettre à jour une stratégie. Si cette option n'est pas spécifiée et qu'une stratégie, dont le nom est le même que celui de la stratégie à ajouter, existe déjà dans l'application, l'opération AddResource échoue.|  
    |**/ Nom**|Nom de la stratégie.|  
    |**/ Version**|Numéro de version de la stratégie.|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk. Obligatoire si vous spécifiez le paramètre Database. Si les paramètres Database et Server ne sont pas spécifiés, la base de données de gestion BizTalk du groupe par défaut est utilisée.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Obligatoire si vous spécifiez le paramètre Server. Si les paramètres Database et Server ne sont pas spécifiés, la base de données de gestion BizTalk du groupe par défaut est utilisée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des stratégies](../core/managing-policies.md)   
 [Création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md)   
 [Commande AddResource : stratégie](../core/addresource-command-policy.md)