---
title: "Modifier les propriétés de l’Instance hôte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a35ca0c8-89b3-483a-b2fc-c8f43a8864d1
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 859170362ce804db6eff5b0e928998f008d0c2c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="update-host-instance-properties"></a>Mettre à jour les propriétés de l’Instance hôte

## <a name="overview"></a>Vue d'ensemble
Vous pouvez utiliser la console Administration de BizTalk Server ou Windows Management Instrumentation (WMI) pour modifier des instances d'hôte. Vous pouvez modifier le compte de service qui exécute une instance d'hôte. Vous pouvez également désactiver une instance d'hôte. Par exemple, si vous voulez conserver les paramètres d'une instance d'hôte et que vous ne voulez pas que cette instance démarre, désactivez-la. Pour plus d’informations sur les instances d’hôte, consultez [Instances d’hôte](../core/host-instances.md).  
  
 Vous ne pouvez pas utiliser les mêmes comptes de service pour les instances d'hôtes approuvés et celles d'hôtes non approuvés. Pour modifier le paramètre d'approbation d'une instance d'hôte lorsque cette instance utilise un compte de service également associé à d'autres instances d'hôte, effectuez l'une des opérations suivantes :  
  
-   Remplacez le compte de service de l'instance d'hôte dont vous voulez modifier les paramètres d'approbation par un nouveau compte de service.  
  
-   Remplacez le compte de service de l'instance d'hôte par un compte de service existant, utilisé par d'autres instances d'hôte dont le paramètre d'approbation est identique.  
  
-   Supprimez l'instance d'hôte et recréez-la avec un paramètre d'approbation et un compte de service différents.  
  
> [!CAUTION]
>  Vous devez modifier les informations d'identification d'une instance d'hôte en mettant à jour les propriétés de cette instance. Si vous modifiez les informations d'identification du service correspondant, le compte de service que vous spécifiez pour l'instance de l'hôte doit être membre du groupe sur l'hôte. N'utilisez pas le composant logiciel enfichable Services ni la console Gestion de l'ordinateur pour modifier les informations d'identification de l'instance d'hôte, cette dernière risquerait de ne pas fonctionner correctement.  
  
> [!CAUTION]
>  Si vous modifiez les informations d'identification d'une instance d'hôte, vous devez également modifier les informations d'identification SQL Server correspondantes. Sinon, l'instance d'hôte ne fonctionnera pas correctement.  
  
 Pour plus d’informations sur l’utilisation de WMI pour modifier une instance d’hôte, consultez **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez avoir ouvert une session en tant que membre du groupe des administrateurs BizTalk Server ou du groupe des administrateurs Windows.  
  
 Vous devez également être un membre du rôle de la base de données SQL Server db_securityadmin et du rôle SQL Server securityadmin sur les serveurs sur lesquels se trouvent les bases de données suivantes :  
  
-   importation principale BAM (BAMPrimaryImport).  
  
-   gestion BizTalk (BizTalkMgmtDb) ;  
  
-   MessageBox BizTalk (BizTalkMsgBoxDb) (tout) ;  
  
-   suivis BizTalk (BizTalkDTADb) ;  
  
-   moteur des règles (BizTalkRuleEngineDb) ;  
  
> [!CAUTION]
>  Nous vous recommandons de mettre à jour les informations de compte des instances d'hôte à l'aide de la console Administration de BizTalk Server ou d'un script WMI (Windows Management Instrumentation). De cette manière, BizTalk Server peut mettre à jour les informations de compte dans les bases de données BizTalk Server et peut synchroniser la configuration de sécurité entre les bases de données et l'instance d'hôte.  
  
## <a name="steps"></a>Étapes
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, cliquez sur **paramètres de plateforme**, puis cliquez sur **Instances d’hôte**.  
  
3.  Dans le volet de détails, cliquez sur l’instance d’hôte que vous souhaitez modifier, puis cliquez sur **propriétés**.  
  
4.  Dans le **propriétés de l’Instance hôte** boîte de dialogue, cliquez sur **configurer** pour modifier les informations de compte de service.  
  
5.  Dans le **informations d’identification d’ouverture de session** boîte de dialogue, entrez le nom de compte et le mot de passe du compte sous lequel l’instance d’hôte s’exécuter, puis cliquez sur **OK**.  
  
6.  Dans le **propriétés de l’Instance hôte** boîte de dialogue, procédez comme suit, puis cliquez sur **OK**:  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom d’hôte**|Afficher le nom de l'hôte associé au serveur sélectionné.|  
    |**Server**|Afficher le serveur associé à l'hôte sélectionné.|  
    |**Ouverture de session**|Afficher le nom de compte du nouveau service sous lequel l'instance de l'hôte doit s'exécuter.|  
    |**Configurer**|Cliquez pour afficher les **informations d’identification d’ouverture de session** boîte de dialogue, dans lequel vous pouvez entrer le nom de compte et le mot de passe du compte sous lequel s’exécute l’instance d’hôte.|  
    |**Désactiver l’instance de l’hôte de démarrer**|Activer cette case à cocher pour faire passer l'état de l'hôte sélectionné de « Activé » à « Désactivé ». La désactivation d'une instance de l'hôte est utile lorsque vous ne souhaitez pas que l'instance démarre, mais que vous voulez tout de même conserver sa configuration.|  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des hôtes BizTalk et les Instances d’hôte](../core/managing-biztalk-hosts-and-host-instances.md)   
 [Ajouter une Instance d’hôte](../core/how-to-add-a-host-instance.md)   
 [Démarrer une Instance d’hôte](../core/how-to-start-a-host-instance.md)   
 [Arrêter une Instance d’hôte](../core/how-to-stop-a-host-instance.md)   
 [Supprimer une Instance d’hôte](../core/how-to-delete-a-host-instance.md)