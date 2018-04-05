---
title: Comment modifier les paramètres de CLR .NET | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Bts10.settings.HostInstanceCLR
ms.assetid: 085743d8-27a6-4d8b-98c7-bb5b5c75848c
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d134faf06aebbb24cafd716722d63172a5ceb68b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-net-clr-settings"></a>Modification des paramètres de CLR .NET
Pour mettre à jour le nombre de threads Windows disponibles dans le pool de threads .NET associé à une instance d’hôte BizTalk, vous pouvez modifier les valeurs d’hébergement CLR appropriées à l’aide du Panneau de configuration de BizTalk. Cette rubrique contient une procédure pas à pas permettant de modifier ces paramètres.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs BizTalk Server.  
  
### <a name="to-modify-the-net-clr-settings-of-a-host-instance"></a>Pour modifier les paramètres .NET CLR d'une instance d'hôte  
  
1.  Dans le **Console d’Administration de BizTalk Server**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], avec le bouton droit **groupe BizTalk**, puis cliquez sur **paramètres**.  
  
2.  Dans le **Panneau de configuration BizTalk** boîte de dialogue le **Instance d’hôte** , cliquez sur le **.NET CLR** onglet.  
  
3.  Procédez comme suit, puis cliquez sur **appliquer** pour appliquer les modifications et passer à un autre onglet. Ou cliquez sur **OK** pour appliquer les modifications et quitter le panneau de configuration.  
  
    |Utiliser|Pour effectuer cette opération|Valeurs limites|Valeur par défaut|Mise à jour de la logique|  
    |--------------|----------------|---------------------|-------------------|-------------------|  
    |**Instance de l’hôte**|Dans la zone déroulante, sélectionnez l'instance en cours d'exécution d'un hôte sur l'ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Runtime.|-|-|-|  
  
     **Paramètres de Threading**  
  
    |Utiliser|Pour effectuer cette opération|Valeurs limites|Valeur par défaut|Mise à jour de la logique|  
    |--------------|----------------|---------------------|-------------------|-------------------|  
    |**Max. threads de travail**|Spécifiez le nombre maximum de threads de travail CLR .NET.|[Nombre minimum de threads de travail, 500]|25|Faites migrer les paramètres du Registre de l'instance de l'hôte vers les paramètres de l'instance de l'hôte, ignorez Version, Flavor, Flags et MinCompletionPortThreads|  
    |**Nombre minimal de threads de travail**|Spécifiez le nombre minimum de threads de travail CLR .NET.|[0, 500]|5|Faites migrer les paramètres du Registre de l'instance de l'hôte vers les paramètres de l'instance de l'hôte, ignorez Version, Flavor, Flags et MinCompletionPortThreads|  
    |**Max. Threads d’e/s**|Spécifiez le nombre maximum de threads E/S.|[Nombre minimum de threads E/S, 1000]|250|Faites migrer les paramètres du Registre de l'instance de l'hôte vers les paramètres de l'instance de l'hôte, ignorez Version, Flavor, Flags et MinCompletionPortThreads|  
    |**Min. Threads d’e/s**|Spécifiez le nombre minimum de threads E/S.|[0, 1000]|25|Faites migrer les paramètres du Registre de l'instance de l'hôte vers les paramètres de l'instance de l'hôte, ignorez Version, Flavor, Flags et MinCompletionPortThreads|  
  
     Les paramètres de CLR .NET sont par noyau de processeur.  
  
    > [!NOTE]
    >  Pour restaurer les paramètres par défaut, cliquez sur **restaurer les valeurs par défaut**.  
  
    > [!NOTE]
    >  **Threads de travail** sont utilisés pour traiter les éléments de travail en file d’attente et **les threads d’e/s** sont des threads de rappel dédiés associés à un port de terminaison d’e/s pour traiter une demande d’e/s asynchrone terminée.  
  
    > [!NOTE]
    >  Si BizTalk est mis à niveau à partir d’une version précédente, les valeurs dans le HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc$*nom d’hôte*\CLR clé de Registre d’hébergement est défini dans le panneau de configuration.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment modifier les paramètres de l’Instance hôte](../core/how-to-modify-host-instance-settings.md)