---
title: "Comment configurer la forme étendue | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Scope shape [Orchestration Designer], about Scope shape
- Scope shape [Orchestration Designer], configuring
- Scope shape [Orchestration Designer], variables
- Scope shape [Orchestration Designer]
- configuring [Orchestration Designer], Scope shape
- Scope shape [Orchestration Designer], transactions
ms.assetid: 3c518db0-d68c-4f72-9d5c-48540811e289
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef17f5d1ab94875af118d17551da4334525535fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-scope-shape"></a>Configuration de la forme Étendue
Le **étendue** forme fournit une infrastructure contextuelle de son contenu. Le premier bloc d’un **étendue** forme est le bloc de contexte ou le corps, dans lequel les actions de base de l’étendue lieu ; elle est analogue au bloc try d’une instruction try/catch. Outre le corps, le **étendue** forme peut-être également inclure un ou plusieurs blocs de gestionnaire d’exceptions et d’un bloc de compensation.  
  
> [!NOTE]
>  Dans un environnement à plusieurs ordinateurs où [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et SQL Server sont situés sur des ordinateurs différents, si le temps universel coordonné (UTC) est différent sur les deux ordinateurs le **délai d’attente** propriété que vous configurez pour la  **Étendue** forme peut obtenir déclenchée plus tôt que prévu en raison de l’heure UTC sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et ordinateurs SQL Server n’est pas synchronisé. Notez qu'il ne s'agit pas ici d'un problème de fuseaux horaires, car ces derniers ne concernent pas l'heure UTC.  
  
### <a name="to-configure-a-scope-shape-as-a-transaction-boundary"></a>Pour configurer une forme Étendue en tant que limite de transaction  
  
1.  Dans la fenêtre Propriétés, définissez la **Type de Transaction** propriété **atomique** ou **Long terme**.  
  
    > [!NOTE]
    >  L'orchestration doit elle-même être une transaction longue pour que vous puissiez définir le type de transaction sur Atomique ou À long terme.  
  
2.  Si le **Type de Transaction** a la valeur **atomique**, puis, dans la fenêtre Propriétés, spécifiez les propriétés suivantes :  
  
    |Propriété| Description|  
    |--------------|-----------------|  
    |Traitement|Valeur booléenne qui détermine si la transaction peut être effectuée avec d'autres transactions sur plusieurs instances de l'orchestration. Cette propriété n'est jamais utilisée dans BizTalk Server, car BizTalk Server ne prend pas en charge le traitement par lot des transactions atomiques sur plusieurs instances d'orchestration. Elle sera supprimée dans la prochaine version.|  
    |Niveau d'isolement|Détermine le niveau auquel les données sont accessibles parmi les transactions simultanées :<br /><br /> -Read Committed : pour empêcher la transaction sélectionnée d’accéder aux modifications de données dans les transactions simultanées jusqu'à ce qu’elles sont validées. Il s'agit du paramètre par défaut de Microsoft SQL Server.<br />-Repeatable Read, pour exiger des verrous de lecture jusqu'à la fin de la transaction sélectionnée.<br />-Sérialisable : pour empêcher les transactions simultanées d’apporter des modifications de données jusqu'à ce que la transaction sélectionnée est terminée. Cette option constitue le niveau d'isolation le plus élevé.|  
    |Réessayer|Valeur booléenne qui détermine si la transaction doit être retentée lorsqu'une erreur survient. La valeur par défaut est **True**. **Remarque :** une transaction atomique sera retentée si vous levez une exception Microsoft.XLANG.BaseTypes.RetryTransactionException, ou si le moteur d’orchestration ne peut pas stocker son état ou de valider la transaction.|  
    |Délai d'expiration|Détermine le délai (en secondes) après lequel la transaction est considérée comme ayant échoué pour cause d'inactivité. Pour ne pas utiliser le délai d'attente, définissez la valeur de cette propriété sur 0. **Remarque :** est un délai DTC, il n’est pas appliquée par le moteur d’orchestration. Dans le cas des transactions atomiques, le moteur n'interrompt pas la transaction. Il continue le traitement normalement jusqu'à validation. La validation échoue uniquement s'il participe à une transaction DTC via l'un des objets contenus dans la transaction.|  
  
3.  Si le **Type de Transaction** a la valeur **Long terme**, puis, dans la fenêtre Propriétés, définissez la propriété suivante :  
  
    |Propriété| Description|  
    |--------------|-----------------|  
    |Délai d'expiration|Détermine le délai (en secondes) avant que la transaction n'expire et ne soit considérée comme un échec. Pour ne pas utiliser le délai d'attente, définissez la valeur de cette propriété sur 0.|  
  
### <a name="to-configure-a-scope-shape-to-contain-local-variables"></a>Pour configurer une forme Étendue de manière qu'elle contienne des variables locales  
  
1.  Double-cliquez sur l’étendue dans la fenêtre Vue Orchestration.  
  
2.  Cliquez sur le dossier Variables sous l’étendue, puis sur **nouvelle Variable**.  
  
3.  Passez à l’étape 2 dans « Pour ajouter une variable » dans [comment ajouter des Variables d’Orchestration](../core/how-to-add-orchestration-variables.md).