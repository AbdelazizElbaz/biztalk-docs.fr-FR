---
title: Comment modifier les paramètres de limitation d’Orchestration | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Bts10.settings.HostOrchestration
ms.assetid: 30086994-cb55-4ff7-9940-df197e5e35ce
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f868c0b6d686871211410e8861acbdec118ac302
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-orchestration-throttling-settings"></a>Modification des paramètres de limitation des orchestrations
Le panneau de configuration permet de modifier les paramètres de configuration de la limitation des orchestrations d'un hôte donné à l'intérieur du groupe BizTalk. Ces paramètres s'appliquent à toutes les instances d'hôte affectées à l'hôte donné. Cette rubrique contient une procédure pas à pas permettant de modifier ces paramètres.  
  
 L’orchestration spécifiées dans les paramètres de limitation du **btsntsvc.exe.config** de fichiers, empêcher une orchestration d’utiliser trop de mémoire en limitant le nombre de messages en attente, il peut avoir. Tous les messages continuent d’être envoyés vers la MessageBox ; Toutefois, les messages en file d’attente ne sont pas remis à l’orchestration jusqu'à ce qu’il traite certains de ses messages en attente.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs BizTalk Server.  
  
### <a name="to-modify-the-orchestrations-throttling-settings-of-a-host"></a>Pour modifier les paramètres de la limitation des orchestrations d'un hôte  
  
1.  Dans le **Console d’Administration de BizTalk Server**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], avec le bouton droit **groupe BizTalk**, puis cliquez sur **paramètres**.  
  
2.  Dans le **Panneau de configuration BizTalk** boîte de dialogue le **hôtes** , cliquez sur le **limitation des Orchestrations** onglet.  
  
3.  Procédez comme suit, puis cliquez sur **appliquer** pour appliquer les modifications et passer à un autre onglet. Ou cliquez sur **OK** pour appliquer les modifications et quitter le panneau de configuration.  
  
    |Utiliser|Pour effectuer cette opération|Valeurs limites|Valeur par défaut|Mise à jour de la logique|  
    |--------------|----------------|---------------------|-------------------|-------------------|  
    |**Hôte**|Dans la liste déroulante, sélectionnez l'hôte représentant les instances d'exécution de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|-|-|-|  
    |**Comportement de mise en attente**|Sélectionnez le comportement de mise en attente du moteur d'orchestration (XLANG). Notez que les autres paramètres XLANG sont uniquement modifiables si vous sélectionnez l'option « Personnalisée ».<br /><br /> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise les propriétés de mise en attente pour décider du moment où il convient de mettre en attente ou de réalimenter les orchestrations. Dans des conditions de charge normales, les valeurs de mise en attente par défaut sont suffisantes, mais si le système fonctionne avec de lourdes charges et que vous souhaitez modifier les caractéristiques de performances, vous devez procéder à un réglage des valeurs. Le comportement de mise en attente de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dépend entièrement de la quantité de mémoire disponible et de la quantité de mémoire utilisée.|Always<br /><br /> Never<br /><br /> Custom|Custom|-|  
  
     **Temps en fonction**  
  
    |Utiliser|Pour effectuer cette opération|Valeurs limites|Valeur par défaut|Mise à jour de la logique|  
    |--------------|----------------|---------------------|-------------------|-------------------|  
    |**Seuil maximal**|Spécifiez le délai d'inactivité maximal pendant lequel une instance d'orchestration peut être bloquée avant d'être mise en attente.|(Seuil min. – Valeur maximale de type entier)|1 800 s|-|  
    |**Seuil minimal**|Spécifiez le délai d'inactivité minimal pendant lequel une instance d'orchestration peut être bloquée avant d'être mise en attente.|[Valeur 1 – valeur maximale de type entier)|1 seconde|-|  
    |**Abonnements**|Sélectionnez cette option pour définir manuellement les valeurs de suspension et de reprise pour un abonnement. Par défaut, le système se charge des abonnements lors de l'exécution.|Activé, désactivé|Inactif|-|  
    |**Suspendre à**|Spécifiez le nombre maximal de messages qu'un abonnement peut stocker.<br /><br /> Lorsque le nombre de messages d'un abonnement en attente d'être utilisés est supérieur ou égal au nombre spécifié, les messages ne sont pas remis à l'instance d'abonnement. Le nombre minimal de messages doit correspondre à la valeur de reprise.<br /><br /> Par exemple, si vous définissez **suspendre à** valeur à 100, cela signifie une orchestration possède 100 messages en attente et de la MessageBox cesse d’envoyer des messages supplémentaires.|(Valeur de l'option « Suspendre à  » – Valeur maximale de type entier).<br /><br /> Sauf lorsque les deux valeurs sont définies sur 0.|Inactif|-|  
    |**Reprendre à**|Spécifiez le nombre de messages à partir duquel la base de données MessageBox reprend l'envoi des messages à l'abonnement.<br /><br /> Par exemple, définissez la **reprendre à** valeur 50. Lorsque le nombre de messages en attente est 50, il spécifie que MessageBox peut reprendre l’envoi des messages.|(0 – Valeur maximale de type entier)|Inactif|-|  
  
    > [!NOTE]
    >  Pour restaurer les paramètres par défaut, cliquez sur **restaurer les valeurs par défaut**.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment modifier les paramètres de l’hôte](../core/how-to-modify-host-settings.md)