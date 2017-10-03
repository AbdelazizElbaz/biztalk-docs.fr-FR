---
title: "Comment modifier les paramètres de limitation des orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Bts10.settings.HostInstanceOrchestration
ms.assetid: f6953c68-7809-4518-87ec-e75c98884af3
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c48f1ec5e74ae577a7c1d130e22f3b4a1b53874c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-orchestration-memory-throttling-settings"></a>Modification des paramètres de limitation de mémoire d'orchestration
Le mécanisme de limitation des instances d'hôte de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] recherche en permanence la présence d'une condition de limitation, calcule la gravité de la condition de limitation et applique la limitation progressivement en fonction de la gravité calculée. Cette rubrique contient une procédure pas à pas permettant de modifier ces paramètres à l'aide du panneau de configuration.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs BizTalk Server.  
  
### <a name="to-modify-the-orchestration-memory-throttling-settings-of-a-host-instance"></a>Pour modifier les paramètres de la limitation des orchestrations d'une instance d'hôte  
  
1.  Dans le **Console d’Administration de BizTalk Server**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], avec le bouton droit **groupe BizTalk**, puis cliquez sur **paramètres**.  
  
2.  Dans le **Panneau de configuration BizTalk** boîte de dialogue le **Instances d’hôte** , cliquez sur le **la limitation de mémoire d’Orchestration** onglet.  
  
3.  Procédez comme suit, puis cliquez sur **appliquer** pour appliquer les modifications et passer à un autre onglet. Ou cliquez sur **OK** pour appliquer les modifications et quitter le panneau de configuration.  
  
    |Utiliser|Pour effectuer cette opération|Valeurs limites|Valeur par défaut|  
    |--------------|----------------|---------------------|-------------------|  
    |**Instance de l’hôte**|Dans la zone déroulante, sélectionnez l'instance en cours d'exécution d'un hôte sur l'ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Runtime.|-|-|  
  
     **Physique**  
  
    |Utiliser|Pour effectuer cette opération|Valeurs limites|Valeur par défaut|  
    |--------------|----------------|---------------------|-------------------|  
    |**Utilisation optimale**|Spécifiez le pourcentage d'utilisation de la mémoire physique auquel la limitation de mise en attente prend effet. Il s'agit du pourcentage optimal de mémoire physique à utiliser pour les instances d'hôte.|[0 – 100]|70|  
    |**Utilisation maximale**|Spécifiez le pourcentage d'utilisation de la mémoire physique auquel la limitation de mise en attente est maximale. Il s'agit du pourcentage maximal de mémoire physique à utiliser pour les instances d'hôte<br /><br /> La valeur minimale de **utilisation maximale** doit être **utilisation optimale**.|(Utilisation optimale – 100]<br /><br /> Sauf lorsque les deux valeurs sont 0 ou 100.|85 %|  
  
     **Virtuel**  
  
    |Utiliser|Pour effectuer cette opération|Valeurs limites|Valeur par défaut|  
    |--------------|----------------|---------------------|-------------------|  
    |**Utilisation optimale**|Spécifiez le pourcentage d'utilisation de la mémoire virtuelle auquel la limitation de mise en attente prend effet.<br /><br /> À ce stade, **TestThreshold** a la valeur **MaxThreshold** et toute utilisation de mémoire supérieure à **OptimalUsage** entraîne **TestThreshold**soit inférieure à **MaxThreshold**.|[0 – 100]|65|  
    |**Utilisation maximale**|Spécifiez le pourcentage d'utilisation de la mémoire virtuelle auquel la limitation de mise en attente est maximale.<br /><br /> À ce stade, **TestThreshold** a la valeur **MinThreshold** et toute utilisation de mémoire inférieure à **MaximalUsage** entraîne **TestThreshold** est supérieure à **MinThreshold**.|(Utilisation optimale – 100]<br /><br /> Sauf lorsque les deux valeurs sont 0 ou 100.|85 %|  
  
    > [!NOTE]
    >  Pour restaurer les paramètres par défaut, cliquez sur **restaurer les valeurs par défaut**.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment modifier les paramètres de l’Instance hôte](../core/how-to-modify-host-instance-settings.md)