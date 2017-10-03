---
title: "Comment exporter une stratégie | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [policies], exporting
- policies, exporting
- exporting, policies
ms.assetid: 2e46d96a-7762-479b-be20-bd590b2a4f0a
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 752336e0642c42418f6c68ddefb719d02051d937
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-export-a-policy"></a>Exportation d'une stratégie
Cette rubrique décrit comment exporter une ou plusieurs stratégies et les vocabulaires qui leur sont associés à l'aide de la console Administration de BizTalk Server ou de l'invite de commandes.  
  
 Lorsque vous exportez une stratégie, gardez les points importants suivants à l'esprit :  
  
-   À l'aide de la console Administration de BizTalk Server, vous pouvez exporter des stratégies à partir d’un groupe BizTalk ou d’une application BizTalk ainsi que les vocabulaires à exporter. Avec BTSTask, vous pouvez exporter des stratégies à partir d’une application et tous les vocabulaires associés seront exportés également. Vous ne pouvez pas sélectionner les vocabulaires à exporter.  
  
    > [!IMPORTANT]
    >  Lorsque vous utilisez la console d’administration, vous pouvez sélectionner les vocabulaires à exporter. Nous vous conseillons de sélectionner tous les vocabulaires associés à une stratégie pour les exporter. Ainsi, vous êtes certain que les vocabulaires nécessaires figurent dans l’environnement de destination. Même si les vocabulaires requis ont été précédemment déployés vers l'environnement de destination, si leur stratégie associée a été supprimée, ils ont également été supprimés. En effet, lorsque vous supprimez une stratégie, tous les vocabulaires qui lui sont associés et qui ne sont pas utilisés par une autre stratégie sont supprimés.  
  
-   Vous pouvez ensuite importer l’ou les stratégies dans un autre groupe BizTalk ou d’une application dans un autre groupe BizTalk, comme décrit dans [comment importer une stratégie](../core/how-to-import-a-policy.md).  
  
-   Pour que vous puissiez exporter une stratégie, elle doit exister dans la base de données du moteur de règles pour le groupe BizTalk. Il existe plusieurs façons d’importer une stratégie dans la base de données du moteur de règles, comme décrit dans [comment importer une stratégie](../core/how-to-import-a-policy.md).  
  
    > [!NOTE]
    >  Lorsque vous supprimez une stratégie de la base de données du moteur de règles à l'aide de l'Assistant Déploiement du moteur de règles, elle s’affiche toujours dans la console d'administration, mais vous ne pouvez pas l'exporter. Pour plus d’informations sur l’Assistant Déploiement du moteur de règles, consultez [comment déployer et annuler le déploiement de stratégies et vocabulaires](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md).  
  
-   Lorsque vous utilisez la console d’administration pour l’exportation, les stratégies et vocabulaires sont exportés dans un fichier .xml. Lorsque vous utilisez l’outil de ligne de commande BTSTask pour l’exportation, les stratégies et vocabulaires sont exportés dans un fichier .msi.  
  
-   BTSTask ne fournit pas de commande spécifique pour l'exportation de stratégies ; toutefois, vous pouvez utiliser la commande ExportApp de BTSTask pour exporter de manière sélective uniquement les stratégies que vous voulez, sans les autres artefacts. Cette opération génère un fichier .msi d’application contenant les stratégies. Vous pouvez ensuite utiliser la commande ImportApp pour importer le fichier .msi dans un groupe BizTalk différent.  
  
## <a name="prerequisites"></a>Conditions préalables  
 La configuration suivante est requise pour exécuter les procédures décrites dans cette rubrique :  
  
-   Vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
-   Le moteur des règles d'entreprise doit être installé. Pour plus d’informations, consultez [vue d’ensemble de l’Installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5).  
  
-   La stratégie que vous voulez exporter doit exister dans la base de données du moteur de règles pour le groupe BizTalk. Si vous voulez exporter la stratégie à partir d’une application, elle doit avoir été ajoutée à l’application également.  
  
## <a name="to-export-a-policy"></a>Pour exporter une stratégie  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server** et développez le groupe BizTalk.  
  
3.  Si vous souhaitez sélectionner les stratégies à exporter à partir de toutes les stratégies dans un droit du groupe BizTalk les **Applications** dossier, cliquez sur **exporter**, puis cliquez sur **stratégies**.  
  
     ou  
  
     Si vous souhaitez exporter les stratégies dans une application particulière, développez le dossier Applications, cliquez sur l’application, cliquez sur **exporter**, puis cliquez sur **stratégies**.  
  
     ou  
  
     Si vous souhaitez exporter uniquement une stratégie particulière, cliquez sur le dossier stratégies qui contient la stratégie, avec le bouton droit de la stratégie, puis cliquez sur **exporter**.  
  
4.  Dans la page Exporter les stratégies, dans **stratégies à exporter**, sélectionnez les stratégies à exporter.  
  
5.  Dans **vocabulaires à exporter**, activez les cases à cocher des vocabulaires à exporter et désactivez les cases à cocher de tous les vocabulaires que vous ne voulez pas exporter. Les vocabulaires utilisés par cette stratégie sont automatiquement sélectionnés.  
  
6.  Dans **fichier à exporter** , entrez le chemin d’accès du fichier XML vers lequel exporter l’ou les stratégies, puis cliquez sur **OK**.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Utilisez la commande BTSTask ListApp avec l’option /ResourceSpec pour générer un fichier XML qui répertorie les artefacts de l’application BizTalk à partir de laquelle vous voulez exporter une stratégie, comme décrit dans [commande ListApp](../core/listapp-command.md).  
  
2.  Modifiez le fichier XML généré à l’étape précédente en supprimant tous les artefacts à l’exception de la ou des stratégies que vous voulez exporter.  
  
3.  Utilisez la commande BTSTask ExportApp et spécifiez le fichier XML modifié pour le paramètre /ResourceSpec. Pour plus d’informations, consultez [commande ExportApp](../core/exportapp-command.md).  
  
     BTSTask exporte les stratégies spécifiées ainsi que tous les vocabulaires qui leur sont associés dans un fichier .msi d'application.  
  
## <a name="see-also"></a>Voir aussi  
 [Exportation de stratégies, les liaisons et les Applications BizTalk](../core/exporting-biztalk-applications-bindings-and-policies.md)   
 [Gestion des stratégies](../core/managing-policies.md)