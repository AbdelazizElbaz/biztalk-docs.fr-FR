---
title: "Comment supprimer une stratégie à partir d’une Application et le groupe BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting, policies
- managing [policies], applications
- managing [policies], deleting
- groups, policies
- managing [policies], groups
- applications, policies
ms.assetid: e9882cb3-8808-4258-a107-a24905290288
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4bb4b162d90811a4eddaa513556ecb1f6c6cd8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-policy-from-an-application-and-the-biztalk-group"></a>Suppression d'une stratégie d'une application et du groupe BizTalk.
Cette rubrique explique comment utiliser la console Administration de BizTalk Server ou la ligne de commande pour supprimer une stratégie d'une application et de la base de données du moteur de règles du groupe BizTalk.  
  
 Avant de supprimer une stratégie, gardez les points importants suivants à l'esprit :  
  
-   Vous ne pouvez pas supprimer une stratégie déployée. Vous devez tout d’abord annuler le déploiement la stratégie, comme décrit dans [comment déployer ou annuler le déploiement d’une stratégie](../core/how-to-deploy-or-undeploy-a-policy.md). L'annulation du déploiement d'une stratégie la rend inactive et celle-ci ne fonctionne donc plus dans les applications qui l'utilisent dans le groupe BizTalk.  
  
-   Le fait de supprimer une stratégie supprime également celle-ci de la base de données du moteur de règles. Si vous souhaitez pouvoir la réutiliser, vous devez l'exporter dans un fichier .xml avant de la supprimer. Pour obtenir des instructions, consultez [comment exporter une stratégie](../core/how-to-export-a-policy.md).  
  
-   Si la stratégie est utilisée par d'autres applications, elle ne pourra plus l'être par la suite. Vérifiez que vous n'avez plus besoin de la stratégie avec d'autres applications qui lui font référence avant de la supprimer.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="to-remove-a-policy"></a>Pour supprimer une stratégie  
  
#### <a name="using-the-biztalk-server-administration-console"></a>Utilisation de la console Administration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk contenant la stratégie à supprimer, puis développez l’application contenant la stratégie  
  
3.  Cliquez sur **stratégies**, avec le bouton droit de la stratégie, puis cliquez sur **supprimer**.  
  
#### <a name="using-the-command-line"></a>À l’aide de la ligne de commande  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.  
  
2.  Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :  
  
     **BTSTask RemoveResource** [**« ApplicationName » :***valeur*] **ApplicationName :***valeur* [  **/Server :**  *valeur*] [**/Database :***valeur*]  
  
     Exemple :  
  
     **BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"Rule/Policy1/1.0 »**  
  
    |Paramètre| Description|  
    |---------------|-----------------|  
    |**/ ApplicationName**|Nom de l'application BizTalk contenant la stratégie à supprimer. L'application par défaut est utilisée si ce paramètre n'est pas spécifié.|  
    |**/ Luid**|Identificateur unique local (LUID) de la stratégie. Vous pouvez obtenir l’identificateur LUID à l’aide de la **ListApp** de commande, comme décrit dans [commande ListApp](../core/listapp-command.md).|  
    |**/ Serveur**|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk. Obligatoire si vous spécifiez le paramètre Database. Si les paramètres Database et Server ne sont pas spécifiés, la base de données de gestion BizTalk du groupe par défaut est utilisée.|  
    |**/ Base de données**|Nom de la base de données de gestion BizTalk. Obligatoire si vous spécifiez le paramètre Server. Si les paramètres Database et Server ne sont pas spécifiés, la base de données de gestion BizTalk du groupe par défaut est utilisée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des stratégies](../core/managing-policies.md)