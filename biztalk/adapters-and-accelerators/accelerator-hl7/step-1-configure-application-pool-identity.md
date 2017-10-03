---
title: "Étape 1 : Configurer l’identité du Pool d’applications | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, application pools
- application pools
ms.assetid: 66286327-8580-4378-89ee-ddd7204b03c6
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e61ee2994e81c3fdd352506d6a9757cde557fbb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-configure-application-pool-identity"></a>Étape 1 : Configurer l’identité du Pool d’applications
Dans ce didacticiel, vous utilisez un pool d’applications dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Internet Information Services (IIS) pour traiter l’orchestration, vous publiez en tant qu’un service Web. Un pool d’applications est un regroupement d’une ou plusieurs URL servies par un processus de travail.  
  
 L’identité d’un pool d’applications est le nom du compte de service sous lequel s’exécute le processus de travail du pool d’applications. Par défaut, les pools d’applications fonctionnent sous le compte d’utilisateur Service réseau dispose de droits d’accès utilisateur bas niveau et ne suffit pas pour ce didacticiel pour la fonction. Pour des raisons de sécurité, vous souhaitez configurer l’identité du pool d’application pour un compte d’utilisateur avec les autorisations minimales, mais au moins d’autorisations pour écrire dans la base de données MessageBox (BizTalkMsgBoxDb) et la base de données (également appelé BizTalk Base de données de gestion, ou BizTalkMgmtDb).  
  
### <a name="to-change-the-service-account-under-which-an-application-pool-runs"></a>Pour modifier le compte de service sous lequel s’exécute un pool d’applications  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
2.  Dans le Gestionnaire des Services Internet (IIS), développez l’ordinateur local, puis **Pools d’applications**.  
  
3.  Cliquez sur le pool d’applications que vous souhaitez configurer (par défaut, ce didacticiel s’exécute sous le **DefaultAppPool**), puis cliquez sur **propriétés**.  
  
4.  Dans la boîte de dialogue Propriétés de DefaultAppPool sur le **identité** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Prédéfinis**|Désélectionnez **prédéfinies**. **Prédéfinies** fait référence à des comptes de service standard, tels que les éléments suivants :<br /><br /> -   **Service réseau** (la valeur par défaut), qui a des droits d’accès utilisateur de niveau inférieur qui peuvent être utilisés pour accéder aux ressources sur des ordinateurs distants.<br />-   **Service local**, ce qui a des droits d’accès de bas niveau. Vous utilisez ce paramètre pour les situations qui ne nécessitent pas d’accès aux ressources sur des ordinateurs distants.<br />-   **Système local**, qui est un compte avec des droits d’utilisateur plus que le compte Service réseau ou Service Local.|  
    |**Configurable**|Sélectionnez **Configurable**. **Configurable** fait référence aux noms d’utilisateur inscrit.|  
    |**Nom d'utilisateur**|Tapez le nom d’utilisateur du compte sous lequel le processus de travail de fonctionner.|  
    |**Mot de passe**|Tapez le mot de passe.|  
  
5.  Cliquez sur **OK**.  
  
    > [!NOTE]
    >  Ou bien, pour une sécurité accrue, vous pouvez créer un nouveau pool d’applications qui s’exécute sous une identité personnalisée que vous créez avec des autorisations personnalisées pour ce didacticiel.  
  
 Passez à [étape 2 : créer un nouveau projet](../../adapters-and-accelerators/accelerator-hl7/step-2-create-a-new-project.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel d’enrichissement de message](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)